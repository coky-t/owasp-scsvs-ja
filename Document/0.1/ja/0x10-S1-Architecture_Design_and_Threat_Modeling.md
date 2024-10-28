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
| S1.1.B1      | さまざまな機能が個別のコントラクトやモジュールに分離されていることを検証します。 |    | ✓  | ✓  |     |
| S1.1.B2      | 各モジュールが単一の責任を持ち、他のモジュールへの依存関係が最小限であることを確認します。 |    | ✓  | ✓  |     |
| S1.1.B3      | セキュリティリスクにつながる可能性のある、モジュール間の依存関係についてチェックします。 |    | ✓  | ✓  |     |
| S1.1.B4      | さまざまなエッジケースを考慮して、権限移譲時にプロトコルが一貫性と信頼性の高い動作を維持することを確認します。 |    |    | ✓  |     |
| S1.1.B5      | プロキシコンストラクトが `initializer` の代わりに `onlyInitializing` 修飾子を使用して、適切な初期化を確保していることを検証します。 |    |    | ✓  |     |
| S1.1.B6      | コントラクトバージョン間のストレージレイアウトが一貫しており、データの破損や予期しない動作を防いでいることを検証します。 |    |    | ✓  |     |
| S1.1.B7      | プロキシアップグレード時に実装間で不変変数が一貫していることを確認します。 |    |    | ✓  |     |
| S1.1.B8      | コントラクトのさまざまな部分にまたがる同じロジックの実装が一貫しており、エラーや脆弱性の発生を避けていることを検証します。 |    |    | ✓  |     |
| S1.1.B9      | 適切なチェックで ETH と WETH が個別に処理されており、排他性に関する正しくない想定によるエラーを回避していることを確認します。 |    |    | ✓  |     |
| S1.1.B10     | プロキシのセットアップでコンストラクタを有するコントラクトが使用されておらず、代わりに初期化ロジックが使用されていることを検証します。 |    |    | ✓  |     |

## S1.2 プロキシパターン (Proxy Patterns)

### 管理目標
プロキシパターンとアップグレードメカニズムが安全に実装され、適切に管理されており、コントラクトアップグレード、廃止、コントラクトバージョン間の移行時のリスクを軽減していることを確認します。
### セキュリティ検証要件
### S1.2.A アップグレードメカニズム (Upgrade Mechanisms)

| 参照コード   | 要件                                                                        | L1 | L2 | L3 | SWE |
| ------------ | --------------------------------------------------------------------------- | -- | -- | -- | --- |
| S1.2.A1      | コントラクトにアップグレードメカニズム (プロキシパターンなど) が実装されていることを検証します。 |    | ✓  | ✓  |     |
| S1.2.A2      | アップグレードプロセスには認可されていないアップグレードに対するセーフガードを含んでいることを確認します。 |    | ✓  | ✓  |     |
| S1.2.A3      | アップグレードメカニズムは文書化され、セキュリティがレビューされていることをチェックします。 |    | ✓  | ✓  |     |
| S1.2.A4      | プロキシのアップグレード時に実装間で不変変数が一貫しており、誤用を防いでいることを検証します。 |    |    | ✓  |     |
| S1.2.A5      | プロキシのセットアップで実装コントラクトの `selfdestruct` および `delegatecall` が脆弱性や予期しない動作をもたらさないことを検証します。 |    |    | ✓  |     |
| S1.2.A6      | UUPSUpgradeable コントラクトが初期化されていない実装コントラクトに影響を及ぼす可能性のある脆弱性から保護され、安全なアップグレードメカニズムを確保していることを検証します。 |    |    | ✓  |     |

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
