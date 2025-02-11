# S7. 算術と論理のセキュリティ (Arithmetic and Logic Security)

## 管理目標
安全な算術と論理のプラクティスを確立して、オーバーフロー/アンダーフローなどの脆弱性を防ぎ、スマートコントラクト内の計算の完全性を確保します。


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
| S7.1.B1      | 固定小数点算術演算が安全に実行され、オーバーフロー、アンダーフロー、精度損失を防いでいることを検証します。 |    | ✓  | ✓  |     |


## S7.2 算術の完全性 (Arithmetic Integrity)

### 管理目標
スマートコントラクト内のすべての計算と論理演算が正しく実行され、データの完全性を維持して、操作を防いでいることを確認します。

### S7.2.A 安全な計算と論理 (Secure Calculations and Logic)

| 参照コード   | 要件                                                                        | L1 | L2 | L3 | SWE |
| ------------ | --------------------------------------------------------------------------- | -- | -- | -- | --- |
| S7.2.A1      | フラッシュローンや寄付などの攻撃ベクトルを考慮して、資産残高から導き出される価格やレートの計算が操作から保護されていることを確認します。 |    | ✓  | ✓  |     |
| S7.2.A2      | 構造体と配列の使用がストレージのエンコーディング問題によるデータ破損や不正確な値につながらないことを確認します。 |    | ✓  | ✓  |     |
| S7.2.A3      | 算術演算が正しく実行されるようにすることで、意図しないデータ型変換や精度損失につながる可能性のある演算を回避します。 |    | ✓  | ✓  |     |
| S7.2.A4      | 最小トランザクション金額を強制して、攻撃者がゼロ金額やダストトランザクションでネットワークを詰まらせることを防ぎます。 |    | ✓  | ✓  |     |
| S7.2.A5      | 金融演算が結合法則を尊重することを検証して、演算が集約的に実行されても反復的に実行されても一貫した結果を確保します。 |    | ✓  | ✓  |     |
| S7.2.A6      | 会計がユーザーシェアに依存する計算に対して適切な丸め方向を実装して、不正確さを回避します。 |    | ✓  | ✓  |     |
| S7.2.A7      | 不等式と比較が正しく実装され、エッジ値を適切に処理することを検証します。    |    | ✓  | ✓  |     |
| S7.2.A8      | abi.decode が型制限を準拠して、ターゲット型のオーバーフローによる差し戻しを回避することを確認します。 |    | ✓  | ✓  |     |
| S7.2.A9      | 特にテストカバレッジが制限される可能性がある場合は、`==`, `!=`, `&&`, `||`, `!` などの論理演算子が正しく使用されていることを確認します。 |  | ✓  | ✓  |  |


### S7.2.B 前提条件と事後条件のチェック (Precondition and Postcondition Checks)

| 参照コード   | 要件                                                                        | L1 | L2 | L3 | SWE |
| ------------ | --------------------------------------------------------------------------- | -- | -- | -- | --- |
| S7.2.B1      | 乗算が除算の前に実行され、計算の精度を維持していることを確認します。 |    | ✓  | ✓  |     |
| S7.2.B2      | リクエスト確認番号がチェーン再構成に伴うリスクを軽減するのに十分に高いことを確認します。 |    | ✓  | ✓  |     |
| S7.2.B3      | ループとイテレーションで off-by-one エラーが回避され、リストの長さとインデックスを正しく処理することを確保していることを検証します。 |    | ✓  | ✓  |     |
| S7.2.B4      | 符号なし整数が負の値を表すために使用されていないことを検証します。これは誤った動作につながる可能性があります。 |    | ✓  | ✓  |     |
| S7.2.B5      | 複数の項を持つ計算が最小値/最大値のすべての可能なエッジケースを処理して、エラーを回避することを検証します。 |    | ✓  | ✓  |     |
