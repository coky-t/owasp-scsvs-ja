# S4. アクセス制御と認証 (Access Control and Authentication)

## 管理目標
堅牢なアクセス制御と認証メカニズムを確立し、認可されたエンティティのみがスマートコントラクト内での機密性の高い操作を実行できるようにします。これには、ロールベースのアクセス制御 (RBAC)、安全な認可メカニズム、分散型アイデンティティ管理の実装を含みます。

## S4.1 ロールベースのアクセス制御 (RBAC) (Role-Based Access Control (RBAC))

### 管理目標
ロールベースのアクセス制御を実装してパーミッションを管理し、認可されたユーザーのみが特定の機能にアクセスできるようにします。これには、アイデンティティの検証、最小権限の原則の適用、適切なアクセス制御の実施の確保などを含みます。

### S4.1.A マルチ署名スキーム (Multi-Signature Schemes)

| 参照コード   | 要件                                                                        | L1 | L2 | L3 | SWE |
| ------------ | --------------------------------------------------------------------------- | -- | -- | -- | --- |
| S4.1.A1      | すべての関数の visibility 修飾子が適切であり、内部関数の不必要な公開を防いでいることを確認します。 |    | ✓  | ✓  |     |

### S4.1.B アイデンティティ検証 (Identity Verification)

| 参照コード   | 要件                                                                        | L1 | L2 | L3 | SWE |
| ------------ | --------------------------------------------------------------------------- | -- | -- | -- | --- |
| S4.1.B1      | Validate that unexpected addresses do not result in unintended behaviors, particularly when these addresses refer to contracts within the same protocol. |    | ✓  | ✓  |     |
| S4.1.B2      | Verify that functions like ecrecover handle all potential null addresses properly to avoid vulnerabilities arising from unexpected ecrecover outputs. |    | ✓  | ✓  |     |

### S4.1.C 最小権限の原則 (Least Privilege Principle)

| 参照コード   | 要件                                                                        | L1 | L2 | L3 | SWE |
| ------------ | --------------------------------------------------------------------------- | -- | -- | -- | --- |
| S4.1.C1      | Use msg.sender instead of tx.origin for authorization to avoid potential abuse from malicious contracts; include checks like require(tx.origin == msg.sender) to ensure the sender is an EOA. |    | ✓  | ✓  |     |
| S4.1.C2      | Certain addresses might be blocked or restricted from receiving tokens (e.g., LUSD). Ensure that address restrictions are properly managed and verified. |    | ✓  | ✓  |     |
| S4.1.C3      | Ensure that Guard’s hooks (e.g., checkTransaction(), checkAfterExecution()) are executed to enforce critical security checks. |    | ✓  | ✓  |     |
| S4.1.C4      | Ensure that access controls are implemented correctly to determine who can use certain functions, and avoid unauthorized changes or withdrawals. |    | ✓  | ✓  |     |


## S4.2 認可メカニズム (Authorization Mechanisms)

### 管理目標
Implement secure authorization mechanisms to safeguard critical functions and sensitive operations, ensuring only authorized entities can perform these actions.

### S4.2.A 重要な機能への安全なアクセス (Secure Access to Critical Functions)

| 参照コード   | 要件                                                                        | L1 | L2 | L3 | SWE |
| ------------ | --------------------------------------------------------------------------- | -- | -- | -- | --- |
| S4.2.A1      | Verify that the contract uses msg.sender for authorization instead of tx.origin to avoid vulnerabilities related to contracts that forward calls from legitimate users. |    | ✓  | ✓  |     |
| S4.2.A2      | Implement and verify appropriate access controls for functions that modify contract state or perform sensitive operations to prevent unauthorized access. |    | ✓  | ✓  |     |

### S4.2.B 期限付きパーミッション (Timed Permissions)

| 参照コード   | 要件                                                                        | L1 | L2 | L3 | SWE |
| ------------ | --------------------------------------------------------------------------- | -- | -- | -- | --- |
| S4.2.B1      | Ensure that msg.sender validation is properly implemented when using Merkle trees to maintain security and prevent unauthorized access. |    | ✓  | ✓  |     |
| S4.2.B2      | Use whitelisting to restrict interactions to a specific set of addresses, providing additional security against malicious actors. |    | ✓  | ✓  |     |
| S4.2.B3      | Ensure that functions modifying the contract state or accessing sensitive operations have proper access controls implemented. |    | ✓  | ✓  |     |


## S4.3 分散型アイデンティティ (Decentralized Identity)

### 管理目標
Implement decentralized identity solutions to ensure secure and reliable identity verification and management while maintaining user privacy.

### S4.3.A 分散識別子 (DID) (Decentralized Identifiers (DIDs))

| 参照コード   | 要件                                                                        | L1 | L2 | L3 | SWE |
| ------------ | --------------------------------------------------------------------------- | -- | -- | -- | --- |
| S4.3.A1      | Verify that the smart contract for handling DIDs adheres to the latest standards and best practices for decentralized identity management. |    | ✓  | ✓  |     |
| S4.3.A2      | Ensure that the DID management contract includes mechanisms to prevent unauthorized modifications and ensure the integrity of DID records. |    | ✓  | ✓  |     |
| S4.3.A3      | Check that DID documents managed by the smart contract are securely stored and can be retrieved in a decentralized manner. |    | ✓  | ✓  |     |
| S4.3.A4      | Verify that the smart contract supports reliable DID resolution and includes mechanisms for handling conflicts and updates. |    | ✓  | ✓  |     |
| S4.3.A5      | Ensure that the smart contract maintains the privacy and confidentiality of DID-related information throughout its lifecycle. |    | ✓  | ✓  |     |

### S4.3.B 検証可能なクレデンシャル (Verifiable Credentials)

| 参照コード   | 要件                                                                        | L1 | L2 | L3 | SWE |
| ------------ | --------------------------------------------------------------------------- | -- | -- | -- | --- |
| S4.3.B1      | Verify that the smart contract manages verifiable credentials in a way that ensures their authenticity and integrity through cryptographic proofs. |    | ✓  | ✓  |     |
| S4.3.B2      | Ensure that the issuance process of verifiable credentials by the smart contract includes proper identity verification and validation procedures. |    | ✓  | ✓  |     |
| S4.3.B3      | Check that the smart contract supports cryptographic proofs to verify the validity of credentials without disclosing sensitive information. |    | ✓  | ✓  |     |
| S4.3.B4      | Verify that the smart contract includes a secure process for revoking verifiable credentials when necessary. |    | ✓  | ✓  |     |
| S4.3.B5      | Ensure that the smart contract’s handling of verifiable credentials complies with relevant standards and best practices for secure credential management. |    | ✓  | ✓  |     |
