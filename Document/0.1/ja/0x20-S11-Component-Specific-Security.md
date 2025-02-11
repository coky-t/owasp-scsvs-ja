# S11. コンポーネント固有のセキュリティ (Component-Specific Security)

## 管理目標
さまざまなブロックチェーンコンポーネントのセキュリティプラクティスと標準を確立して、トークン、NFT、vault、流動性プールに関連する特定の脆弱性を軽減します。

## S11.1 トークン (ERC20, ERC721, ERC1155) (Tokens (ERC20, ERC721, ERC1155))

### 管理目標
トークン標準の安全な実装と管理を確保して、脆弱性を防ぎます。

### S11.1.A 安全な実装と管理 (Secure Implementation and Management)

| 参照コード   | 要件                                                                        | L1 | L2 | L3 | SWE |
| ------------ | --------------------------------------------------------------------------- | -- | -- | -- | --- |
| S11.1.A1     | トークンミント操作時に totalSupply 値が一貫しており、コールバックによって正しくない値につながらないことを確保します。 |    | ✓  | ✓  |     |
| S11.1.A2     | 一部のトークンには複数のアドレスが関連付けられており、脆弱性が生じる可能性があります。すべてのトークンアドレスが安全に管理および検証され、関連するリスクを回避していることを確認します。 |    | ✓  | ✓  |     |
| S11.1.A3     | トークンがゼロ金額の転送を適切に処理し、統合と操作での問題を防いでいることを検証します。 |    | ✓  | ✓  |     |
| S11.1.A4     | トークンがゼロ金額の転送を適切に処理し、統合と操作での問題を防いでいることを検証します。 |    | ✓  | ✓  |     |
| S11.1.A5     | 一部のトークンではゼロ金額の転送で差し戻し、特定の統合と操作で問題を生じる可能性があります。そのようなトークンとの互換性を確保し、統合の問題を回避します。 |    | ✓  | ✓  |     |
| S11.1.A6     | すべての ERC20 トークンが EIP20 標準に準拠しているわけではありません。一部はブールフラグを返さないか、失敗時に差し戻さない可能性があります。ERC20 標準に準拠していることを検証して、互換性問題を回避します。 |    | ✓  | ✓  |     |


## S11.2 NFT セキュリティ (NFT Security)

### 管理目標
非代替性トークンのベストプラクティスを実装して、脆弱性から保護します。

### S11.2.A 非代替性トークンのベストプラクティス (Best Practices for Non-Fungible Tokens)

| 参照コード   | 要件                                                                        | L1 | L2 | L3 | SWE |
| ------------ | --------------------------------------------------------------------------- | -- | -- | -- | --- |
| S11.2.A1     | NFT の作成、管理、転送に関する標準とベストプラクティスを実装して、一般的な脆弱性を防ぎます。 |    | ✓  | ✓  |     |
| S11.2.A2     | 適切なメタデータの完全性を確保して、認可されていないミントと転送を防ぎます。 |    | ✓  | ✓  |     |
| S11.2.A3     | ロイヤリティの支払いやトークンバーンに関連する潜在的な悪用から保護します。 |    | ✓  | ✓  |     |


## S11.3 保管室 (Vaults)

### 管理目標
vault システム内での安全な資産保管と管理を確保します。

### S11.3.A 安全な資産保管と管理 (Secure Asset Storage and Management)

| 参照コード   | 要件                                                                        | L1 | L2 | L3 | SWE |
| ------------ | --------------------------------------------------------------------------- | -- | -- | -- | --- |
| S11.3.A1     | キュー時間や引き出し制限など、stETH や wstETH の引き出しに関連する潜在的なオーバーヘッド問題に対処して、スムーズな操作を確保します。 |    | ✓  | ✓  |     |
| S11.3.A2     | stETH と wstETH 間の変換を慎重に処理して、stETH のリベース特性による潜在的な問題を回避します。 |    | ✓  | ✓  |     |


## S11.4 流動的ステーキング (Liquid Staking)

### 管理目標
安全なステーキングメカニズムを確保して、ユーザーの資産を保護します。

### S11.4.A 安全なステーキングメカニズム (Secure Staking Mechanisms)

| 参照コード   | 要件                                                                        | L1 | L2 | L3 | SWE |
| ------------ | --------------------------------------------------------------------------- | -- | -- | -- | --- |
| S11.4.A1     | 特に一元管理されたエンティティにより制御されている場合、sfrxETH を frxETH からデタッチするメカニズムが堅牢であり、不整合を防ぎ、正確な報酬の転送を確保していることを検証します。 |    | ✓  | ✓  |     |
| S11.4.A2     | sfrxETH/ETH レートの将来の潜在的な変化を監視して、ユーザーに十分な事前警告が届き、レート変動に関連するリスクを軽減することを確保します。 |    | ✓  | ✓  |     |


## S11.5 流動性プール (AMM) (Liquidity Pools (AMMs))

### 管理目標
自動マーケットメーカーにおけるセキュリティ対策を確立します。

### S11.5.A 自動マーケットメーカーのセキュリティ (Security in Automated Market Makers)

| 参照コード   | 要件                                                                        | L1 | L2 | L3 | SWE |
| ------------ | --------------------------------------------------------------------------- | -- | -- | -- | --- |
| S11.5.A1     | [WIP/Will be removed]                                                       |    |    |    |     |



## S11.6 Uniswap V4 フック (Uniswap V4 Hook)

### 管理目標
Uniswap コンポーネントの安全な統合とカスタマイズを確保します。

### S11.6.A 安全な統合とカスタマイズ (Secure Integration and Customization)

| 参照コード   | 要件                                                                        | L1 | L2 | L3 | SWE |
| ------------ | --------------------------------------------------------------------------- | -- | -- | -- | --- |
| S11.6.A1     | Uniswap の TickMath および FullMath ライブラリの正しい使用状況を検証して、バージョン固有の Solidity の考慮事項に従って、チェックされていない算術演算の適切な処理を確保していることを検証します。 |    | ✓  | ✓  |     |
