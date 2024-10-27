# S11. コンポーネント固有のセキュリティ (Component-Specific Security)

## 管理目標
Establish security practices and standards for various blockchain components to mitigate specific vulnerabilities associated with tokens, NFTs, vaults, and liquidity pools.

---

## S11.1 トークン (ERC20, ERC721, ERC1155) (Tokens (ERC20, ERC721, ERC1155))

### 管理目標
Ensure secure implementation and management of token standards to prevent vulnerabilities.

### S11.1.A 安全な実装と管理 (Secure Implementation and Management)

| 参照コード   | 要件                                                                        | L1 | L2 | L3 | SWE |
| ------------ | --------------------------------------------------------------------------- | -- | -- | -- | --- |
| S11.1.A1     | Verify that the totalSupply value is consistent during token minting operations, ensuring that callbacks do not result in incorrect values. |    | ✓  | ✓  |     |
| S11.1.A2     | Some tokens have multiple addresses associated with them, which can introduce vulnerabilities. Ensure all token addresses are managed and verified securely to avoid related risks. |    | ✓  | ✓  |     |
| S11.1.A3     | Verify that tokens handle zero amount transfers properly to prevent issues in integrations and operations. |    | ✓  | ✓  |     |
| S11.1.A4     | Verify that tokens handle zero amount transfers properly to prevent issues in integrations and operations. |    | ✓  | ✓  |     |
| S11.1.A5     | Some tokens revert on the transfer of a zero amount, which can cause issues in certain integrations and operations. Ensure compatibility with such tokens to avoid integration problems. |    | ✓  | ✓  |     |
| S11.1.A6     | Not all ERC20 tokens comply with the EIP20 standard; some may not return a boolean flag or revert on failure. Verify compliance with the ERC20 standard to avoid compatibility issues. |    | ✓  | ✓  |     |

---

## S11.2 NFT セキュリティ (NFT Security)

### 管理目標
Implement best practices for non-fungible tokens to safeguard against vulnerabilities.

### S11.2.A 非代替性トークンのベストプラクティス (Best Practices for Non-Fungible Tokens)

| 参照コード   | 要件                                                                        | L1 | L2 | L3 | SWE |
| ------------ | --------------------------------------------------------------------------- | -- | -- | -- | --- |
| S11.2.A1     | Implement standards and best practices for NFT creation, management, and transfer to prevent common vulnerabilities. |    | ✓  | ✓  |     |
| S11.2.A2     | Ensure proper metadata integrity and prevent unauthorized minting or transfers. |    | ✓  | ✓  |     |
| S11.2.A3     | Safeguard against potential exploits related to royalty payments or token burns. |    | ✓  | ✓  |     |

---

## S11.3 保管室 (Vaults)

### 管理目標
Ensure secure asset storage and management within vault systems.

### S11.3.A 安全な資産保管と管理 (Secure Asset Storage and Management)

| 参照コード   | 要件                                                                        | L1 | L2 | L3 | SWE |
| ------------ | --------------------------------------------------------------------------- | -- | -- | -- | --- |
| S11.3.A1     | Address potential overhead issues associated with withdrawing stETH or wstETH, including queue times and withdrawal limits, to ensure smooth operations. |    | ✓  | ✓  |     |
| S11.3.A2     | Handle conversions between stETH and wstETH carefully to avoid potential issues due to the rebasing nature of stETH. |    | ✓  | ✓  |     |

---

## S11.4 流動的ステーキング (Liquid Staking)

### 管理目標
Ensure secure staking mechanisms to protect users' assets.

### S11.4.A 安全なステーキングメカニズム (Secure Staking Mechanisms)

| 参照コード   | 要件                                                                        | L1 | L2 | L3 | SWE |
| ------------ | --------------------------------------------------------------------------- | -- | -- | -- | --- |
| S11.4.A1     | Verify that mechanisms for detaching sfrxETH from frxETH are robust to prevent discrepancies and ensure accurate reward transfers, particularly when controlled by centralized entities. |    | ✓  | ✓  |     |
| S11.4.A2     | Monitor potential future changes in the sfrxETH/ETH rate and ensure users are adequately forewarned to mitigate risks associated with rate fluctuations. |    | ✓  | ✓  |     |

---

## S11.5 流動性プール (AMM) (Liquidity Pools (AMMs))

### 管理目標
Establish security measures in automated market makers.

### S11.5.A 自動マーケットメーカーのセキュリティ (Security in Automated Market Makers)

| 参照コード   | 要件                                                                        | L1 | L2 | L3 | SWE |
| ------------ | --------------------------------------------------------------------------- | -- | -- | -- | --- |
| S11.5.A1     | [WIP/Will be removed]                                                     |    |    |    |     |

---

## S11.6 Uniswap V4 フック (Uniswap V4 Hook)

### 管理目標
Ensure secure integration and customization of Uniswap components.

### S11.6.A 安全な統合とカスタマイズ (Secure Integration and Customization)

| 参照コード   | 要件                                                                        | L1 | L2 | L3 | SWE |
| ------------ | --------------------------------------------------------------------------- | -- | -- | -- | --- |
| S11.6.A1     | Verify the correct usage of Uniswap’s TickMath and FullMath libraries to ensure proper handling of unchecked arithmetic operations, adhering to version-specific Solidity considerations. |    | ✓  | ✓  |     |
