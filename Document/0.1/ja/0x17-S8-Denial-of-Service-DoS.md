# S8. サービス拒否 (Denial of Service (DoS))

## 管理目標
プラクティスとメカニズムを確立して、コントラクトの機能とか要請を妨げる可能性のあるサービス拒否 (DoS) 攻撃を防ぎます。


## S8.1 ガス制限 (Gas Limits)

### 管理目標
コントラクト設計と機能実装がガス使用に効率的であり、out-of-gas エラーや関連する脆弱性に関連するリスクを軽減することを確認します。

### S8.1.A 効率的なループと関数の設計 (Efficient Loop and Function Design)

| 参照コード   | 要件                                                                        | L1 | L2 | L3 | SWE |
| ------------ | --------------------------------------------------------------------------- | -- | -- | -- | --- |
| S8.1.A1      | 重要な機能のガス消費を慎重に管理することで、コントラクトが不十分なガスのグリーフィング攻撃から保護されていることを確認します。 |    | ✓  | ✓  |     |
| S8.1.A2      | RocketDepositPool コントラクトのようなシステムが burn() のような関数の失敗を適切に処理することを確認します。 |    | ✓  | ✓  |     |
| S8.1.A3      | 関数とループのガス使用が効率的であり、out-of-gas エラーを回避することを検証します。 |    | ✓  | ✓  |     |
| S8.1.A4      | ブロックガス制限によるサービス拒否攻撃を防ぐメカニズムを実装して、トランザクションや操作がガス制限の制約を超えないことを確保します。 |    | ✓  | ✓  |     |

### S8.1.B フォールバックメカニズム (Fallback Mechanisms)

| 参照コード   | 要件                                                                        | L1 | L2 | L3 | SWE |
| ------------ | --------------------------------------------------------------------------- | -- | -- | -- | --- |
| S8.1.B1      | try/catch ブロックには十分なガスが提供され、エラー時の失敗や予期しない動作を回避することを確認します。 |    | ✓  | ✓  |     |


## S8.2 資源枯渇に対する耐性 (Resilience Against Resource Exhaustion)

### 管理目標
Implement strategies to protect contracts from resource exhaustion attacks that can lead to DoS scenarios.

### S8.2.A レート制限 (Rate Limiting)

| 参照コード   | 要件                                                                        | L1 | L2 | L3 | SWE |
| ------------ | --------------------------------------------------------------------------- | -- | -- | -- | --- |
| S8.2.A1      | Avoid using blocking mechanisms that could lead to a Denial-of-Service (DoS) attack. |    | ✓  | ✓  |     |
| S8.2.A2      | Protect against potential DoS in functions like supportsERC165InterfaceUnchecked() by handling excessive data queries efficiently. |    | ✓  | ✓  |     |
| S8.2.A3      | Ensure that assertions do not lead to denial of service or unexpected contract reverts, especially in scenarios where conditions are not met. |    | ✓  | ✓  |     |
| S8.2.A4      | Verify that return values from external function calls are checked to prevent issues related to unchecked return values, which could lead to unexpected behavior. |    | ✓  | ✓  |     |
| S8.2.A5      | Ensure that contract functions are protected against denial of service due to unexpected reverts by handling all possible error conditions appropriately. |    | ✓  | ✓  |     |
| S8.2.A6      | Ensure that functions such as supportsERC165InterfaceUnchecked() in ERC165Checker.sol handle large data queries efficiently to avoid excessive resource consumption. |    | ✓  | ✓  |     |
