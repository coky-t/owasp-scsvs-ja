# S2. ポリシー、手続き、コード管理 (Policies, Procedures, and Code Management)

## 管理目標
セキュアコーディングプラクティス、徹底したコードレビュー、包括的なテストを推進するために開発ポリシーと手続きが整備されていることを確認します。その目的は、脆弱性を防ぎ、スマートコントラクトコードの保守性と明確性を高めることです。

## S2.1 開発ポリシー (Development Policies)

### 管理目標
セキュアコーディング標準とレビュープロセスを確立して実施し、脆弱性を最小限に抑え、開発ライフサイクル全体を通じてベストプラクティスが遵守されるようにします。

### S2.1.A セキュアコーディング標準 (Secure Coding Standards)

| 参照コード   | 要件                                                                        | L1 | L2 | L3 | SWE |
| ------------ | --------------------------------------------------------------------------- | -- | -- | -- | --- |
| S2.1.A1      | 開発者が古いバージョンのコンパイラを使用しておらず、最新のコンパイラ推奨に準拠していることを確認します。 |    | ✓  | ✓  |     |
| S2.1.A2      | コード内で非推奨関数が使用されていないことを検証します。                    |    | ✓  | ✓  |     |

### S2.1.B コードレビュープロセス (Code Review Processes)

| 参照コード   | 要件                                                                        | L1 | L2 | L3 | SWE |
| ------------ | --------------------------------------------------------------------------- | -- | -- | -- | --- |
| S2.1.B1      | すべてのスマートコントラクトのコード変更が、メインブランチにマージする前に、スマートコントラクトセキュリティに精通した二人の独立した開発者によってレビューされていることを検証します。 |    | ✓  | ✓  |     |
| S2.1.B2      | スマートコントラクトのコードレビューには、スマートコントラクト専用に設計された自動静的解析ツールを使用し、フラグが立てられた問題はすべて、マージ前に対処されるか文書化されていることを確認します。 |    | ✓  | ✓  |     |
| S2.1.B3      | スマートコントラクトのコードレビュープロセスには、再入攻撃、整数オーバーフロー、不適切なアクセス制御などの脆弱性の徹底的な分析を含むことをチェックします。 |    | ✓  | ✓  |     |
| S2.1.B4      | コードレビューには、安全な数学ライブラリやセキュアデザインパターンの使用など、スマートコントラクト開発標準への準拠を含むことを検証します。 |    | ✓  | ✓  |     |
| S2.1.B5      | コードレビューには一般的なスマートコントラクトの脆弱性のチェックリストを組み込んでいること、およびコードが承認される前にそのリストの各項目が対処されていることを確認します。 |    | ✓  | ✓  |     |

## S2.2 コードの明確性 (Code Clarity)

### 管理目標
徹底した文書化、論理的な構造、一貫したコーディング標準の準拠を通じてコードの明確性と保守性を促進し、開発者の理解と修正を容易にします。

### S2.2.A 可読性と文書化 (Readability and Documentation)

| 参照コード   | 要件                                                                        | L1 | L2 | L3 | SWE |
| ------------ | --------------------------------------------------------------------------- | -- | -- | -- | --- |
| S2.2.A1      | スマートコントラクトのすべての機能と重要なコードブロックが、その目的とロジックを説明する明確なコメントとともに文書化されていることを確認します。 |    | ✓  | ✓  |     |
| S2.2.A2      | スマートコントラクトの構造が論理的で、他の開発者が理解しやすく修正しやすいように整理されていることを検証します。 |    | ✓  | ✓  |     |
| S2.2.A3      | スマートコントラクトのドキュメントには、その機能の高レベルの概要、使用方法、他のコントラクトやシステムとの依存関係を含むことをチェックします。 |    | ✓  | ✓  |     |
| S2.2.A4      | スマートコントラクトのコードが、変数、関数、コントラクト名の一貫した命名規則に従っていて、可読性と保守性を向上していることを確認します。 |    | ✓  | ✓  |     |

### S2.2.B コードリンティングとフォーマッティングツール (Code Linting and Formatting Tools)

| 参照コード   | 要件                                                                        | L1 | L2 | L3 | SWE |
| ------------ | --------------------------------------------------------------------------- | -- | -- | -- | --- |
| S2.2.B1      | Ensure that a code linting tool specific to smart contracts is integrated into the development workflow to enforce coding standards and style guidelines. |    | ✓  | ✓  |     |
| S2.2.B2      | Verify that all smart contract code passes linting checks without errors or warnings before being committed to the repository. |    | ✓  | ✓  |     |
| S2.2.B3      | Check that code formatting tools are applied to maintain consistent indentation, spacing, and line breaks in smart contract code. |    | ✓  | ✓  |     |
| S2.2.B4      | Ensure that the linting and formatting configurations are reviewed and updated regularly to reflect new best practices and emerging issues in smart contract development. |    | ✓  | ✓  |     |
| S2.2.B5      | Verify that the linting and formatting tools are compatible with the development environment and do not introduce unintended changes to the smart contract code. |    | ✓  | ✓  |     |


## S2.3 テストカバレッジ (Test Coverage)

### 管理目標
Ensure comprehensive test coverage for smart contracts, encompassing unit tests, integration tests, and security-specific tests, to identify vulnerabilities and maintain code quality throughout development.

### S2.3.A 単体テスト、統合テスト、自動テスト (Unit Tests, Integration Tests, Automated Testing)

| 参照コード   | 要件                                                                        | L1 | L2 | L3 | SWE |
| ------------ | --------------------------------------------------------------------------- | -- | -- | -- | --- |
| S2.3.A1      | Verify that all critical functions in the smart contract have comprehensive unit tests that cover both typical and edge cases. |    | ✓  | ✓  |     |
| S2.3.A2      | Ensure that integration tests are implemented to validate the interactions between the smart contract and other contracts or external systems. |    | ✓  | ✓  |     |
| S2.3.A3      | Check that automated tests are set up to run on each code commit to detect regressions and maintain continuous quality of the smart contract. |    | ✓  | ✓  |     |
| S2.3.A4      | Verify that test coverage tools are used to monitor and achieve a high percentage of coverage for the smart contract code. |    | ✓  | ✓  |     |
| S2.3.A5      | Ensure that the testing framework supports mocking and simulating external dependencies to effectively isolate and test specific functionalities of the smart contract. |    | ✓  | ✓  |     |

### S2.3.B セキュリティ特化テスト (Security-Specific Tests)

| 参照コード   | 要件                                                                        | L1 | L2 | L3 | SWE |
| ------------ | --------------------------------------------------------------------------- | -- | -- | -- | --- |
| S2.3.B1      | Verify that the test suite for the smart contract includes security-specific tests designed to identify vulnerabilities such as reentrancy, integer overflows, and improper access controls. |    | ✓  | ✓  |     |
| S2.3.B2      | Ensure that the security tests validate proper implementation of access controls and permissions within the smart contract. |    | ✓  | ✓  |     |
| S2.3.B3      | Check that fuzz testing is conducted to uncover unexpected behaviors and potential security issues under various input scenarios. |    | ✓  | ✓  |     |
| S2.3.B4      | Verify that the smart contract's response to invalid inputs and edge cases is thoroughly tested to ensure robust security measures are in place. |    | ✓  | ✓  |     |
