# Testing
## Standard
### ISO/IEC 29119
- 2013 Software and systems engineering -Software testing-
- Its purpose is to define an internationally agreed set of standards to support software testing.
  This standards replace a number of existing software testing standards:
  - IEEE 829 Test Documentation
  - IEEE 1008 Unit Testing
  - BS 7925-1 Vocabulary of Terms in Software Testing
  - BS 7925-2 Software Component Testing Standard
#### ISO/IEC/IEEE 29119-1:Consepts & Definitions
#### ISO/IEC/IEEE 29119-2:Test Processes
#### ISO/IEC/IEEE 29119-3:Test Documentation
#### ISO/IEC/IEEE 29119-4:Test Techniques
#### ISO/IEC/IEEE 29119-5:Keyword Driven Testing
#### Link
- [[http://www.softwaretestingstandard.org/][The International Software Testing Standard - ISO/IEC/IEEE 29119 Software Testing]]
### IEEE 829-2008
#### Test Plan Outline テスト計画書
##### Test Plan Identifier 識別番号
##### Referencens 参考資料
##### Introduction はじめに
##### Test Items テストアイテム
##### Features To Be Tested テスト対象機能
##### Features Not To Be Tested 非テスト対象機能
##### Approach アプローチ
##### Item Pass/Fail Criteria テスト合否判定基準
##### Suspension Criteria and Resumption Requirements テスト中止再開基準
##### Test Deliverables テスト成果物
##### Testing Tasks テスト作業タスクと担当
##### Environmental Needs テスト環境
##### Responsibilities 責任範囲
##### Staffing And Training Needs 人員計画、トレーニング
##### Schedule スケジュール
##### Risks And Contingencies リスクと対策
##### Approvals 承認
#### Test Documents
##### Master Test Plan(MTP) マスターテスト計画
- Providing an overall test planning and test management document for muliple levels of test
###### 目次例
- マスターテスト計画
  - 1. 概要
    - 1.1. 文書識別番号
    - 1.2. 対象範囲
    - 1.3. 参考資料
    - 1.4. システム要旨と重要な特徴
    - 1.5. テスト要旨
      - 1.5.1. 組織編成
      - 1.5.2. テスト全体日程
      - 1.5.3. 整合性レベル概要
      - 1.5.4. リソースサマリ
      - 1.5.5. 責任
      - 1.5.6. ツール、技術、方法、メトリクス
  - 2. 全体テスト計画詳細
    - 2.1. テストレベルの定義を含むテストプロセス
      - 2.1.1. プロセス：管理
        - 2.1.1.1 アクティビティ：テスト作業の管理
      - 2.1.2 プロセス：収集
        - 2.1.2.1 アクティビティ：取得支援テスト
      - 2.1.3 プロセス：供給
        - 2.1.3.1 アクティビティ：テストの計画
      - 2.1.4 プロセス：開発
        - 2.1.4.1 アクティビティ：コンセプト
        - 2.1.4.2 アクティビティ：要件
        - 2.1.4.3 アクティビティ：設計
        - 2.1.4.4 アクティビティ：実装
        - 2.1.4.5 アクティビティ：テスト
        - 2.1.4.6 アクティビティ：インストール／点検
      - 2.1.5 プロセス：運用
        - 2.1.5.1 アクティビティ：運用テスト
      - 2.1.6 プロセス：保守
        - 2.1.6.1 アクティビティ：保守テスト
    - 2.2. テスト文書要件
    - 2.3. テスト管理要件
    - 2.4. テスト報告要件
  - 3 一般
    - 3.1. 用語集
    - 3.2. 改訂履歴
##### Level Test Plan(LTP) レベルテスト計画
- For each LTP the scope, approach, resources, and schedule of the testing activities for its specified level of testing need to be described.
  The item being tested, the features to be tested, the testing tasks to be performed, the personnel responsible for each task, and the associated risk(s) need to be identified.
- テストに関するスコープ、アプローチ、リソース、スケジュールを記述。
###### 目次例
- レベルテスト計画
  - 1 概要
    - 1.1 文書識別番号
    - 1.2 対象範囲
    - 1.3 参考資料
    - 1.4 レベルテスト全体像
    - 1.5 テストクラスと全体テスト条件
  - 2 レベルテスト計画詳細
    - 2.1 テスト項目と識別子
    - 2.2 テスト追跡表
    - 2.3 テスト対象機能
    - 2.4 テスト非対象機能
    - 2.5 アプローチ
    - 2.6 合否基準
    - 2.7 一時停止基準と再開要件
    - 2.8 テスト成果物
  - 3 テスト管理
    - 3.1 計画されたアクティビティとタスク；テストの流れ
    - 3.2 環境／設備
    - 3.3 責任と権限
    - 3.4 関係者間のコミュニケーション
    - 3.5 リソース配分
    - 3.6 トレーニング
    - 3.7 スケジュール・見積り・コスト
    - 3.8 リスクと対応策
  - 4 一般
    - 4.1 品質保証の手順
    - 4.2 メトリクス
    - 4.3 テストカバレッジ
    - 4.4 用語集
    - 4.5 改訂履歴
##### Level Test Design(LTD) レベルテスト設計
-
###### 目次例
- レベルテスト設計
  - 1 概要
    - 1.1. 文書識別番号
    - 1.2. 対象範囲
    - 1.3. 参考資料
  - 2 レベルテスト設計詳細
    - 2.1. テスト対象機能
    - 2.2. アプローチの具体化
    - 2.3. テスト識別子
    - 2.4. 合否基準
    - 2.5 テスト成果物
  - 3 一般
    - 3.1. 用語集
    - 3.2. 改訂履歴
##### Level Test Case(LTC) レベルテストケース
- テストケース設計仕様書に列挙された書くテストケースの詳細
###### 目次例
- レベルテストケース
  - 1 概要
    - 1.1. 文書識別番号
    - 1.2. 対象範囲
    - 1.3. 参考資料
    - 1.4. その他事項
    - 1.5. テストケース構成図
  - 2 詳細
    - 2.1. テストケース識別子
    - 2.2. テスト目的
    - 2.3. 入力
    - 2.4. 期待される結果
    - 2.5. 環境要件
    - 2.6. 手順に関する特記事項
    - 2.7. テストケース間の相互関係
  - 3 全体
    - 3.1. 用語集
    - 3.2. 改訂履歴
##### Level Test Procedure(LTCr) レベルテスト手順
- テストケースを実施する手順と、ソフトウェアがテストに合格したのかそれとも不合格なのかを判定するプロセスを示すこと
##### Level Test Log(LTL) レベルテストログ
- テスト実行中に観察された何かしら意義ある詳細情報を時系列に記録として残す
##### Anomaly Report(AR) 異常報告
- テストの途中で観察されたさらなる調査を必要とする事象を文書化する
##### Level Interim Test Status Report(LITSR) レベルテスト中間状況報告
##### Level Test Report(LTR) レベルテスト報告
##### Master Test Report(MTR) マスターテスト報告
#### Link
- [[http://www.fit.vutbr.cz/study/courses/ITS/public/ieee829.html][TEST PLAN OUTLINE (IEEE 829 Format)]]
- [[https://www.qbook.jp/qptemplate/testieee829][テストドキュメントテンプレート - Qbook]]
- [[http://h50146.www5.hpe.com/products/software/hpsoftware/bto/pdfs/alm1_6.pdf][テストマネジメント虎の巻 第六回]]
- [[http://kazu5.exblog.jp/3014629/][IEEE829標準規格のドキュメント - 和子の毎日ヘロヘロ記録]]
## Level
### UnitTest / UT / 単体試験
#### 自動テスト
- [[file://UnitTest.org][UnitTest.org]]
#### Link
- [[http://code.tutsplus.com/articles/the-beginners-guide-to-unit-testing-what-is-unit-testing--wp-25728][The Beginner’s Guide to Unit Testing: What Is Unit Testing? - envatotuts+]]
- [[https://appkitbox.com/knowledge/test/20130228-130][ユニットテストを学ぶための推薦図書 - Developers AppKit Box]]
### Integration Test / IT / 結合試験
- 

### System Test  / ST / システム試験
- 
#### Functional Test / FT / 機能試験
-
#### Performance Test / 性能テスト
### Regression Test
##### Link
- [[https://www.slideshare.net/taruhachi/201611-69516073][クラウドファーストにおけるWEBアプリケーション負荷試験実践入門 - SlideShare]]
#### 不可テスト
#### リグレッションテスト
#### Penetration Test
- A software attack on a computer system that looks for security weaknesses, potentially gaining access to the computer's features and data.
## 品質特性
### 機能性
### 信頼性
### 使用性
### 効率性
### 保守性
### 移植性
## JSTQB
### テキスト
#### テストの基礎
##### テストの必要性
##### テストとはなにか
##### テストの７原則
##### 基本的なテストプロセス
##### テストの心理学
##### 行動規範
#### ソフトウェアサイクルを通じてのテスト
##### ソフトウェア開発モデル
##### テストレベル
##### テストタイプ
##### 保守テスト
#### 静的技法
##### 静的技法とテストプロセス
##### レビュープロセス
##### ツールによる静的解析
#### テスト設計技法
##### テスト開発プロセス
##### テスト設計技法のカテゴリ
##### 仕様ベース、ブラックボックスのテスト技法
##### 構造ベース、ホワイトボックスのテスト技法
##### 経験ベースのテスト技法
##### テスト技法の選択
#### テストのマネジメント
##### テスト組織
##### テスト計画作業と見積もり
##### テスト進捗のモニタリングとコントロール
##### 構成管理
##### リスクとテスト
##### インシデント管理
#### テスト支援ツール
##### テストツールの種類
##### ツールの効果的な使い方:利点とリスク
##### 組織へのツール導入

### 用語

## Glossary
### 探索的テスト
## Memo
### 検討事項
- [[http://h50146.www5.hpe.com/products/software/hpsoftware/bto/pdfs/alm1_6.pdf][テストマネジメント虎の巻 第六回]]
#### テスト範囲
#### テスト環境
#### テストのやり方
### ダミーデータ
#### ドメイン
##### トップレベルドメイン
- .example
- .test
##### セカンドレベルドメイン
- RFC2606で例示用として示されたもの
  (https://tools.ietf.org/html/rfc2606)
  - example.com
  - example.net
  - example.org
- JPドメインは以下
  (https://jprs.jp/faq/use/)
  - "example"を用いたもの
    - example.jp
    - example.co.jp
    - example.ne.jp
  - "example"の後に数字1桁がつくもの
    - example1.jp
    - example2.co.jp
    - 他...
#### Link
- https://blog.ko31.com/201304/sample-domain-example/
- https://www.find-job.net/startup/dummy-2013
### Pairwise ペアワイズ法
- すべての因子の組み合わせでなく、全てのペアの組み合わせにテストを制限する。
  テストケースを組み合わせる場合、直交させて組み合わせるとすぐに値が大きくなってしまうため、
  ペアに制限することで増加率を抑える。
- [[https://github.com/Microsoft/pict/blob/master/doc/pict.md][Microsoft/pict - Github]]
- [[https://msdn.microsoft.com/en-us/library/cc150619.aspx][Pairwise Testing in the Real World: Practical Extensions to Test-Case Scenarios - Microsoft Developer Network]]
## Link
- [[https://www.qbook.jp/qptop][Qbook]]
