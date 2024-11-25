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
Implement best practices for non-fungible tokens to safeguard against vulnerabilities.

### S11.2.A 非代替性トークンのベストプラクティス (Best Practices for Non-Fungible Tokens)

| 参照コード   | 要件                                                                        | L1 | L2 | L3 | SWE |
| ------------ | --------------------------------------------------------------------------- | -- | -- | -- | --- |
| S11.2.A1     | Implement standards and best practices for NFT creation, management, and transfer to prevent common vulnerabilities. |    | ✓  | ✓  |     |
| S11.2.A2     | Ensure proper metadata integrity and prevent unauthorized minting or transfers. |    | ✓  | ✓  |     |
| S11.2.A3     | Safeguard against potential exploits related to royalty payments or token burns. |    | ✓  | ✓  |     |


## S11.3 保管室 (Vaults)

### 管理目標
Ensure secure asset storage and management within vault systems.

### S11.3.A 安全な資産保管と管理 (Secure Asset Storage and Management)

| 参照コード   | 要件                                                                        | L1 | L2 | L3 | SWE |
| ------------ | --------------------------------------------------------------------------- | -- | -- | -- | --- |
| S11.3.A1     | Address potential overhead issues associated with withdrawing stETH or wstETH, including queue times and withdrawal limits, to ensure smooth operations. |    | ✓  | ✓  |     |
| S11.3.A2     | Handle conversions between stETH and wstETH carefully to avoid potential issues due to the rebasing nature of stETH. |    | ✓  | ✓  |     |


## S11.4 流動的ステーキング (Liquid Staking)

### 管理目標
Ensure secure staking mechanisms to protect users' assets.

### S11.4.A 安全なステーキングメカニズム (Secure Staking Mechanisms)

| 参照コード   | 要件                                                                        | L1 | L2 | L3 | SWE |
| ------------ | --------------------------------------------------------------------------- | -- | -- | -- | --- |
| S11.4.A1     | Verify that mechanisms for detaching sfrxETH from frxETH are robust to prevent discrepancies and ensure accurate reward transfers, particularly when controlled by centralized entities. |    | ✓  | ✓  |     |
| S11.4.A2     | Monitor potential future changes in the sfrxETH/ETH rate and ensure users are adequately forewarned to mitigate risks associated with rate fluctuations. |    | ✓  | ✓  |     |


## S11.5 流動性プール (AMM) (Liquidity Pools (AMMs))

### 管理目標
Establish security measures in automated market makers.

### S11.5.A 自動マーケットメーカーのセキュリティ (Security in Automated Market Makers)

| 参照コード   | 要件                                                                        | L1 | L2 | L3 | SWE |
| ------------ | --------------------------------------------------------------------------- | -- | -- | -- | --- |
| S11.5.A1     | [WIP/Will be removed]                                                     |    |    |    |     |



## S11.6 Uniswap V4 フック (Uniswap V4 Hook)

### 管理目標
Ensure secure integration and customization of Uniswap components.

### S11.6.A 安全な統合とカスタマイズ (Secure Integration and Customization)

| 参照コード   | 要件                                                                        | L1 | L2 | L3 | SWE |
| ------------ | --------------------------------------------------------------------------- | -- | -- | -- | --- |
| S11.6.A1     | Verify the correct usage of Uniswap’s TickMath and FullMath libraries to ensure proper handling of unchecked arithmetic operations, adhering to version-specific Solidity considerations. |    | ✓  | ✓  |     |
