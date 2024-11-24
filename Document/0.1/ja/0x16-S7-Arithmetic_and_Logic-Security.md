# S7. 算術とロジックのセキュリティ (Arithmetic and Logic Security)

## 管理目標
安全な算術とロジックのプラクティスを確立して、オーバーフロー/アンダーフローなどの脆弱性を防ぎ、スマートコントラクト内の計算の完全性を確保します。


## S7.1 オーバーフロー/アンダーフローの防止 (Preventing Overflow/Underflow)

### 管理目標
安全な算術プラクティスを実装して、コントラクトの機能やセキュリティを脅かす可能性のあるオーバーフローやアンダーフローの脆弱性を防ぎます。

### S7.1.A 安全な数学ライブラリの使用 (Use of Safe Math Libraries)

| 参照コード   | 要件                                                                        | L1 | L2 | L3 | SWE |
| ------------ | --------------------------------------------------------------------------- | -- | -- | -- | --- |
| S7.1.A1      | 明示的な型キャストがオーバーフローやアンダーフローにつながらないことを検証します。 |    | ✓  | ✓  |     |
| S7.1.A2      | 整数算術演算がその境界を超えず、整数オーバーフローやアンダーフローの脆弱性を防いでいることを検証します。 |    | ✓  | ✓  |     |
| S7.1.A3      | 時間単位やその他の式を含む演算が潜在的なオーバーフローを正しく処理することを確認します。 |    | ✓  | ✓  |     |
| S7.1.A4      | ゼロによる除算が正しく処理され、トランザクションを元に戻して、予期しない動作を防いでいることを検証します。 |    | ✓  | ✓  |     |
| S7.1.A5      | 変数が境界内で管理され、制限を超えたことによる差し戻しを防いでいることを確認します。 |    | ✓  | ✓  |     |
| S7.1.A6      | unchecked{} ブロック内の算術演算は慎重に管理され、意図しないオーバーフローやアンダーフローを防いでいることを確認します。 |    | ✓  | ✓  |     |
| S7.1.A7      | インラインアセンブリ演算がゼロによる除算とオーバーフロー/アンダーフローを望ましい動作に従って処理して、適切に戻すことを確認します。 |    | ✓  | ✓  |     |
| S7.1.A8      | 演算によって意図しない精度の問題や丸め誤差につながるかもしれない場合に対処するためのチェックを実装します。 |    | ✓  | ✓  |     |

### S7.1.B 固定小数点算術 (Fixed-Point Arithmetic)

| 参照コード   | 要件                                                                        | L1 | L2 | L3 | SWE |
| ------------ | --------------------------------------------------------------------------- | -- | -- | -- | --- |
| S7.1.B1      | 固定小数点算術演算が安全に実行され、オーバーフロー、アンダーフロー、精度低下を防いでいることを検証します。 |    | ✓  | ✓  |     |


## S7.2 算術の完全性 (Arithmetic Integrity)

### 管理目標
Ensure that all calculations and logical operations within the smart contract are performed correctly to maintain data integrity and prevent manipulation.

### S7.2.A 安全な計算とロジック (Secure Calculations and Logic)

| 参照コード   | 要件                                                                        | L1 | L2 | L3 | SWE |
| ------------ | --------------------------------------------------------------------------- | -- | -- | -- | --- |
| S7.2.A1      | Ensure that price or rate calculations derived from asset balances are protected from manipulation, considering attack vectors like flash loans and donations. |    | ✓  | ✓  |     |
| S7.2.A2      | Ensure that the use of structs and arrays does not lead to data corruption or incorrect values due to storage encoding issues. |    | ✓  | ✓  |     |
| S7.2.A3      | Avoid operations that could lead to unintended data type conversions or precision loss by ensuring arithmetic operations are performed correctly. |    | ✓  | ✓  |     |
| S7.2.A4      | Enforce a minimum transaction amount to prevent attackers from clogging the network with zero amount or dust transactions. |    | ✓  | ✓  |     |
| S7.2.A5      | Validate that financial operations respect associative properties, ensuring consistent outcomes whether operations are performed in aggregate or iteratively. |    | ✓  | ✓  |     |
| S7.2.A6      | Implement proper rounding direction for calculations where accounting relies on user shares to avoid inaccuracies. |    | ✓  | ✓  |     |
| S7.2.A7      | Validate that inequalities and comparisons are correctly implemented to handle edge values appropriately. |    | ✓  | ✓  |     |
| S7.2.A8      | Ensure that abi.decode adheres to the type limits to avoid reverts due to overflow of target types. |    | ✓  | ✓  |     |
| S7.2.A9 | Ensure that logical operators such as `==`, `!=`, `&&`, `||`, and `!` are used correctly, especially when test coverage may be limited. |  | ✓  | ✓  |  |


### S7.2.B 前提条件と事後条件のチェック (Precondition and Postcondition Checks)

| 参照コード   | 要件                                                                        | L1 | L2 | L3 | SWE |
| ------------ | --------------------------------------------------------------------------- | -- | -- | -- | --- |
| S7.2.B1      | Ensure that multiplication is performed before division to maintain precision in calculations. |    | ✓  | ✓  |     |
| S7.2.B2      | Ensure that the request confirmation number is high enough to mitigate risks associated with chain re-orgs. |    | ✓  | ✓  |     |
| S7.2.B3      | Verify that off-by-one errors are avoided in loops and iterations, ensuring correct handling of list lengths and indexing. |    | ✓  | ✓  |     |
| S7.2.B4      | Verify that unsigned integers are not used to represent negative values, as this can lead to erroneous behavior. |    | ✓  | ✓  |     |
| S7.2.B5      | Verify that calculations with multiple terms handle all possible edge cases for min/max values to avoid errors. |    | ✓  | ✓  |     |
