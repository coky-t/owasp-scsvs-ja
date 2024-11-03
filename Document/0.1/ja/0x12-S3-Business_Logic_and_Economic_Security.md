# S3. ビジネスロジックと経済のセキュリティ (Business Logic and Economic Security)

## 管理目標
スマートコントラクトのビジネスロジックと経済のセキュリティが、インセンティブ構造、トークノミクス、ロジックの脆弱性に関連する脅威に対して耐性があることを確認します。コントラクトは、安全な経済モデル、トークン処理、トランザクションの完全性を実装することで、不正使用、誤動作、予期しない動作を防ぐ必要があります。


## S3.1 経済モデル (Economic Models)

### 管理目標
インセンティブ構造やトークノミクスを含む経済モデルが、エコシステム内で価値を確保し、適切な行動にインセンティブを与えるように設計され、実装されていることを確認します。コントラクトはトークン価値の変動に対応し、悪用の機会を作らないようにする必要があります。

### S3.1.A インセンティブ構造 (Incentive Structures)

| 参照コード   | 要件                                                                        | L1 | L2 | L3 | SWE |
| ------------ | --------------------------------------------------------------------------- | -- | -- | -- | --- |
| S3.1.A1      | 会計を追跡し、ユーザーが支払いを引き出せるように、払い戻しプロセスがプッシュベースではなくプルベースのアプローチを導入していることを確認します。 | ✓  | ✓  | ✓  |     |
| S3.1.A2      | cbETH から ETH へのレートが低下する可能性があり、cbETH を保有またはやり取りするユーザーに影響を及ぼします。変換レートの変動に対応するためのメカニズムがあることを確認します。 |    | ✓  | ✓  |     |
| S3.1.A3      | Ethereum 2.0 Beacon Chain のバリデータは、不正行為によってペナルティを受けたり削減される可能性があり、rETH の価値に影響を及ぼす可能性があります。価値評価ややり取りにおいて、これらのダイナミクスが考慮されていることを確認します。 |    | ✓  | ✓  |     |
| S3.1.A4      | ETH と rETH との間の変換レートはステーキングから得られる報酬に基づいて時間の経過とともに変化する可能性があります。これらの変動が適切に管理され、捕捉されていることを確認します。 |    | ✓  | ✓  |     |


## S3.2 トークノミクス (Tokenomics)

### 管理目標
Ensure that tokens used within the smart contract ecosystem are securely implemented, including aspects such as value management, rebasing mechanisms, and reward systems. Contracts should prevent token vulnerabilities like double-spending, incorrect rewards, and improper fee handling.

### S3.2.A トークンの経済的セキュリティとそのユースケース (Economic Security of Tokens and Their Use Cases)

| 参照コード   | 要件                                                                        | L1 | L2 | L3 | SWE |
| ------------ | --------------------------------------------------------------------------- | -- | -- | -- | --- |
| S3.2.A1      | Ensure that Merkle trees do not contain duplicate proofs, as this can lead to vulnerabilities like double-spending. |    | ✓  | ✓  |     |
| S3.2.A2      | Verify that DeFi protocols account for tokens with negative rebase mechanisms, ensuring that value changes and potential miscalculations are properly handled and mitigated. |    | ✓  | ✓  |     |
| S3.2.A3      | Verify that reward claims are correctly implemented to ensure users receive their correct rewards. |    | ✓  | ✓  |     |
| S3.2.A4      | Verify that tokens do not have vulnerabilities such as incorrect fee application or unexpected behavior due to token transfer issues. |    | ✓  | ✓  |     |
| S3.2.A5      | Verify that all claimable addresses are included in the hashing process for Merkle tree leaves to prevent attackers from claiming funds they should not. |    | ✓  | ✓  |     |


## S3.3 再入可能性とロジックの欠陥の防止 (Preventing Reentrancy and Logic Flaws)

### 管理目標
Ensure the smart contract's transaction flow and logic integrity are protected from reentrancy attacks and logic flaws. Contracts should implement robust control structures and security patterns to prevent reentrancy, handle complex flows, and ensure that state transitions are secure and symmetrical.

### S3.3.A トランザクションフローのセキュリティ (Transaction Flow Security)

| 参照コード   | 要件                                                                        | L1 | L2 | L3 | SWE |
| ------------ | --------------------------------------------------------------------------- | -- | -- | -- | --- |
| S3.3.A1      | Check for edge cases in loop control structures to prevent unexpected behaviors due to break or continue statements. |    | ✓  | ✓  |     |
| S3.3.A2      | Ensure that scenarios where sender and recipient are the same are considered to prevent unintended issues in smart contracts. |    | ✓  | ✓  |     |
| S3.3.A3      | Ensure that the `NonReentrant` modifier is applied before other modifiers in functions to prevent reentrancy attacks. |    | ✓  | ✓  |     |
| S3.3.A4      | Verify that the check-effect-interaction pattern is implemented to prevent reentrancy attacks. |    | ✓  | ✓  |     |
| S3.3.A5      | Ensure that function calls with arbitrary user input and low-level calls are handled securely to avoid introducing risks. |    | ✓  | ✓  |     |

### S3.3.B 機能の完全性 (Function Integrity)

| 参照コード   | 要件                                                                        | L1 | L2 | L3 | SWE |
| ------------ | --------------------------------------------------------------------------- | -- | -- | -- | --- |
| S3.3.B1      | Ensure that functions intended to be unique per parameter set are not callable multiple times to prevent potential issues. |    | ✓  | ✓  |     |
| S3.3.B2      | Verify that state changes in functions, such as withdraw and deposit, are symmetrically handled to avoid undesired behavior due to inconsistencies. |    | ✓  | ✓  |     |
