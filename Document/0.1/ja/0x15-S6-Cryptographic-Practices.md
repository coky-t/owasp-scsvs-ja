# S6. 暗号化の実践 (Cryptographic Practices)

## 管理目標
鍵の管理、署名の検証、乱数の生成のための安全な暗号プラクティスを確立して、スマートコントラクト内のトランザクションとデータの完全性と真正性を保護します。

## S6.1 鍵管理 (Key Management)

### 管理目標
秘密鍵の安全な取り扱いと保管を確保し、堅牢な署名検証プロセスを実装して、認可されていないアクセスやアクションを防ぎます。

### S6.1.A 秘密鍵の安全な処理と保管 (Secure Handling and Storage of Private Keys)

| 参照コード   | 要件                                                                        | L1 | L2 | L3 | SWE |
| ------------ | --------------------------------------------------------------------------- | -- | -- | -- | --- |
| S6.1.A1      | ecrecover() 関数が不正な入力を正しく処理し、無効なデータを返さないことを検証します。 |    | ✓  | ✓  |     |
| S6.1.A2      | 特に、署名自体にのみ依存するのではなく、ノンスやハッシュ化されたメッセージを使用することで、署名検証メカニズムが署名の可変性やリプレイ攻撃に対して堅牢であることを確認します。 |    | ✓  | ✓  |     |
| S6.1.A3      | Solidity 0.8 で導入された ABI デコードの問題を考慮して、SignatureChecker.isValidSignatureNow がエッジケースを適切に処理し、予期せず元に戻らないことを検証します。 |    | ✓  | ✓  |     |
| S6.1.A4      | すべての署名が徹底的にチェックされ、脆弱または不適切に管理された署名バリデーションによる認可されていないトランザクションやアクションを防いでいることを確認します。 |    | ✓  | ✓  |     |
| S6.1.A5      | 古いライブラリやプラクティスを避けることで、署名保護メカニズムが最新であり、署名可変性攻撃に対する耐性があることを検証します。 |    | ✓  | ✓  |     |

### S6.1.B マルチ署名ウォレット (Multi-Signature Wallets)

| 参照コード   | 要件                                                                        | L1 | L2 | L3 | SWE |
| ------------ | --------------------------------------------------------------------------- | -- | -- | -- | --- |
| S6.1.B1      | Verify that multi-signature wallets require a predefined number of signatures before executing any transaction. |    | ✓  | ✓  |     |
| S6.1.B2      | Ensure that the multi-signature wallet logic is resistant to replay attacks. |    | ✓  | ✓  |     |
| S6.1.B3      | Verify that the process of adding or removing signatories from the multi-signature wallet is secure and controlled. |    | ✓  | ✓  |     |


## S6.2 署名検証 (Signature Verification)

### 管理目標
Implement cryptographic techniques that ensure the secure verification of signatures and compliance with standards to maintain the integrity of authenticated transactions.

### S6.2.A 認証のための暗号技法 (Cryptographic Techniques for Authentication)

| 参照コード   | 要件                                                                        | L1 | L2 | L3 | SWE |
| ------------ | --------------------------------------------------------------------------- | -- | -- | -- | --- |
| S6.2.A1      | Ensure that cryptographic algorithms used for signature verification are secure and follow best practices. |    | ✓  | ✓  |     |

### S6.2.B 標準準拠 (例, EIP-712) (Standard Compliance (e.g., EIP-712))

| 参照コード   | 要件                                                                        | L1 | L2 | L3 | SWE |
| ------------ | --------------------------------------------------------------------------- | -- | -- | -- | --- |
| S6.2.B1      | Verify that ECDSA signature handling functions, such as ECDSA.recover and ECDSA.tryRecover, properly manage signature formats to prevent signature malleability, especially when handling both traditional 65-byte and EIP-2098 compact signatures. |    | ✓  | ✓  |     |

## S6.3 安全な乱数生成 (Secure Random Number Generation)

### 管理目標
Implement best practices for secure random number generation to ensure unpredictability and resistance against manipulation.

### S6.3.A ランダム性のベストプラクティス (Best Practices for Randomness)

| 参照コード   | 要件                                                                        | L1 | L2 | L3 | SWE |
| ------------ | --------------------------------------------------------------------------- | -- | -- | -- | --- |
| S6.3.A1      | Ensure that random number generation follows best practices and uses secure sources of entropy. |    | ✓  | ✓  |     |
| S6.3.A2      | Verify that any random number generation is resistant to manipulation and prediction. |    | ✓  | ✓  |     |
