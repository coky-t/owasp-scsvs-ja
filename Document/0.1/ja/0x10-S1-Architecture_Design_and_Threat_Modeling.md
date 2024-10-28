# S1. アーキテクチャ、設計、脅威モデリング (Architecture, Design, and Threat Modeling)

## S1.1 セキュアデザインパターン (Secure Design Patterns)

### 管理目標
スマートコントラクトがモジュール性、アップグレード可能性、関心の分離を考慮して設計され、安全な運用、アップグレード、保守が可能であることを確認します。コントラクトは、複雑なアップグレード、権限移譲、依存関係の不適切な管理に関するセキュリティリスクを最小限に抑えるように設計されるべきです。
### セキュリティ検証要件
### S1.1.A モジュール性とアップグレード可能性 (Modularity and Upgradability)

| 参照コード   | 要件                                                                        | L1 | L2 | L3 | SWE |
| ------------ | --------------------------------------------------------------------------- | -- | -- | -- | --- |
| S1.1.A1      | コントラクトがモジュラーコンポーネントやコントラクトに分割されていることを検証します。 |    | ✓  | ✓  |     |
| S1.1.A2      | アップグレードメカニズムが安全で制御されたアップデートを可能にするように設計されていることを確認します。 |    | ✓  | ✓  |     |
| S1.1.A3      | モジュール境界が明確に定義され、依存関係が管理されていることをチェックします。 |    | ✓  | ✓  |     |
| S1.1.A4      | コントラクトバージョン間でのストレージ変数の順序やタイプの変更が管理され、ストレージの衝突やデータの破損を避けていることを確認します。 |    | ✓  | ✓  |     |
| S1.1.A5      | 重要な権限移譲が二段階のプロセスで実施され、安全で信頼性の高い権限変更を確保していることを検証します。 |    |    | ✓  |     |
| S1.1.A6      | 仮想関数の呼び出し時に無効なコードが生成されないように、内部関数とパブリック関数をオーバーライドする際に、パラメータやリターン変数のデータ位置が正しく処理されていることを検証します。 |    |    | ✓  |     |

### S1.1.B 関心の分離 (Separation of Concerns)

| 参照コード   | 要件                                                                        | L1 | L2 | L3 | SWE |
| ------------ | --------------------------------------------------------------------------- | -- | -- | -- | --- |
| S1.1.B1      | Verify that different functionalities are separated into distinct contracts or modules. |    | ✓  | ✓  |     |
| S1.1.B2      | Ensure that each module has a single responsibility and minimal dependencies on other modules. |    | ✓  | ✓  |     |
| S1.1.B3      | Check for any cross-module dependencies that could lead to security risks.   |    | ✓  | ✓  |     |
| S1.1.B4      | Ensure that the protocol maintains consistent and reliable operation during the transfer of privileges, with considerations for various edge cases. |    |    | ✓  |     |
| S1.1.B5      | Verify that proxy contracts use the `onlyInitializing` modifier instead of `initializer` to ensure proper initialization. |    |    | ✓  |     |
| S1.1.B6      | Verify that storage layouts between contract versions are consistent to prevent data corruption and unpredictable behavior. |    |    | ✓  |     |
| S1.1.B7      | Ensure that immutable variables are consistent across implementations during proxy upgrades. |    |    | ✓  |     |
| S1.1.B8      | Verify that implementations of the same logic across different parts of the contract are consistent to avoid introducing errors or vulnerabilities. |    |    | ✓  |     |
| S1.1.B9      | Ensure that ETH and WETH are handled separately with appropriate checks to avoid errors due to incorrect assumptions about exclusivity. |    |    | ✓  |     |
| S1.1.B10     | Verify that contracts with constructors are not used in a proxy setup, and initializer logic is used instead. |    |    | ✓  |     |

## S1.2 プロキシパターン (Proxy Patterns)

### 管理目標
Ensure that proxy patterns and upgrade mechanisms are implemented securely and managed properly, to mitigate risks during contract upgrades, deprecations, and transitions between contract versions.
### セキュリティ検証要件
### S1.2.A アップグレードメカニズム (Upgrade Mechanisms)

| 参照コード   | 要件                                                                        | L1 | L2 | L3 | SWE |
| ------------ | --------------------------------------------------------------------------- | -- | -- | -- | --- |
| S1.2.A1      | Verify that an upgrade mechanism (e.g., proxy pattern) is implemented for the contract. |    | ✓  | ✓  |     |
| S1.2.A2      | Ensure that the upgrade process includes safeguards against unauthorized upgrades. |    | ✓  | ✓  |     |
| S1.2.A3      | Check that the upgrade mechanism is documented and reviewed for security.    |    | ✓  | ✓  |     |
| S1.2.A4      | Verify that immutable variables are consistent across implementations during proxy upgrades to prevent misuse. |    |    | ✓  |     |
| S1.2.A5      | Verify that `selfdestruct` and `delegatecall` in implementation contracts do not introduce vulnerabilities or unexpected behaviors in a proxy setup. |    |    | ✓  |     |
| S1.2.A6      | Verify that UUPSUpgradeable contracts are protected against vulnerabilities that may affect uninitialized implementation contracts, ensuring secure upgrade mechanisms. |    |    | ✓  |     |

### S1.2.B 非推奨の管理 (Managing Deprecation)

| 参照コード   | 要件                                                                        | L1 | L2 | L3 | SWE |
| ------------ | --------------------------------------------------------------------------- | -- | -- | -- | --- |
| S1.2.B1      | Verify that deprecated contract versions are correctly marked and handled.   |    |    | ✓  |     |
| S1.2.B2      | Ensure that access to deprecated versions is restricted or disabled.         |    |    | ✓  |     |
| S1.2.B3      | Check that migration paths from deprecated versions to new versions are secure. |    |    | ✓  |     |

### S1.2.C 透過プロキシと不透過プロキシ (Transparent vs. Opaque Proxies)

| 参照コード   | 要件                                                                        | L1 | L2 | L3 | SWE |
| ------------ | --------------------------------------------------------------------------- | -- | -- | -- | --- |
| S1.2.C1      | Verify whether a transparent or opaque proxy pattern is used and its suitability for the contract. |    | ✓  | ✓  |     |
| S1.2.C2      | Ensure that the proxy pattern is correctly implemented and does not introduce vulnerabilities. |    | ✓  | ✓  |     |
| S1.2.C3      | Check that the proxy pattern’s choice is documented and justified.           |    | ✓  | ✓  |     |
| S1.2.C4      | Ensure that uninitialized contracts cannot be taken over by attackers and that initialization functions are secured with the correct modifiers. |    |    | ✓  |     |
| S1.2.C5      | Verify that `TransparentUpgradeableProxy` and similar proxy patterns handle selector clashes and non-decodable calldata correctly to maintain transparency. |    |    | ✓  |     |

## S1.3 脅威モデリング (Threat Modeling)

### 管理目標
Identify, assess, and mitigate security threats for smart contract systems by implementing a thorough threat modeling process, ensuring that risks are minimized and protections are in place for critical contract features.
### セキュリティ検証要件
### S1.3.A 脅威の特定 (Identifying Threats)

| 参照コード   | 要件                                                                        | L1 | L2 | L3 | SWE |
| ------------ | --------------------------------------------------------------------------- | -- | -- | -- | --- |
| S1.3.A1      | Verify that potential threats are identified and documented.                 | ✓  | ✓  | ✓  |     |
| S1.3.A2      | Ensure that the threat identification process includes input from security experts. |    | ✓  | ✓  |     |
| S1.3.A3      | Check that threats are categorized based on their impact and likelihood.     |    | ✓  | ✓  |     |
| S1.3.A4      | Implement protections against front-running in governor proposal creation to prevent attackers from blocking proposals or gaining undue advantages. |    |    | ✓  |     |

### S1.3.B リスクの評価 (Assessing Risks)

| 参照コード   | 要件                                                                        | L1 | L2 | L3 | SWE |
| ------------ | --------------------------------------------------------------------------- | -- | -- | -- | --- |
| S1.3.B1      | Verify that risk assessments are performed for identified threats.           |    | ✓  | ✓  |     |
| S1.3.B2      | Ensure that risks are prioritized based on their potential impact and likelihood. |    | ✓  | ✓  |     |
| S1.3.B3      | Check that risk assessment results are documented and reviewed.              |    | ✓  | ✓  |     |

### S1.3.C 緩和策の実施 (Implementing Mitigations)

| 参照コード   | 要件                                                                        | L1 | L2 | L3 | SWE |
| ------------ | --------------------------------------------------------------------------- | -- | -- | -- | --- |
| S1.3.C1      | Verify that mitigations are implemented for high-priority risks.             |    | ✓  | ✓  |     |
| S1.3.C2      | Ensure that mitigation strategies are documented and tested.                 |    | ✓  | ✓  |     |
| S1.3.C3      | Check that the effectiveness of implemented mitigations is reviewed and validated. |    | ✓  | ✓  |     |
