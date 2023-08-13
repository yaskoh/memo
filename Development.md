# Development
- システム開発に関することを入れる。分類が難しい場合も多いので、ひとまずここに記載する運用でよい。
## Software life cycle
### ISO/IEC/IEEE
#### System and software engineering 29148
- file:///C:/Users/yasutakk/Downloads/iso-iec-ieee-29148-2011.pdf
#### 
### IEEE
#### SQA - Software quality assurance IEEE 730
#### SCM - Software configuration management IEEE 828
#### STD - Software test documentation IEEE 829
#### SRS - Software requirements specification IEEE 830
#### V&V - Software verification and validation IEEE 1012
#### SDD - Software design description IEEE 1016
#### SPM - Software project management IEEE 1058
#### SUD - Software user documentation IEEE 1063
## SWEBOK
- [[https://www.computer.org/web/swebok/v3][SWEBOK V3]]
## Software metric
### NCSS
- Non Commenting Source Statement
### LOC
- line of code
### Link
- https://en.wikipedia.org/wiki/Software_metric
- https://ja.wikipedia.org/wiki/%E3%82%BD%E3%83%95%E3%83%88%E3%82%A6%E3%82%A7%E3%82%A2%E6%B8%AC%E5%AE%9A%E6%B3%95
## Backup
### 条件
- 復旧にどれだけの時間をかけられるか
- どの時点のデータにふっゆすればよいのか
### 要件例
- バックアップ対象とサイズ
- バックアップ取得時間
- バックアップ方法
- バックアップ世代数と取得媒体
- バックアップにかけられる費用

<<<<<<< HEAD:Development.org
** The Twelve-Factor App / 12FA
- [[https://12factor.net/][THE TWELVE-FACTOR APP]]
- [[https://aws.amazon.com/jp/builders-flash/202208/introductions-twelve-factors-app/?awsf.filter-name=*all][AWS アーキテクチャで学ぶ The Twelve Factors App 本格入門 - builders.flash]]
- [[https://kakakakakku.hatenablog.com/entry/2020/03/09/084833][「The Twelve-Factor App」を15項目に見直した「Beyond the Twelve-Factor App」を読んだ - kakakakakku blog]]

*** About
- Heroku の共同創設者である Adam Wiggins 氏が提唱した、優れたソフトウェアを開発するための方法論
*** Practices
**** 1. Codebase
- コードとアプリケーションは常に1:1の関係であるべき
**** 2. Dependencies
- アプリケーション内で利用されるライブラリ等の依存関係を明示的に宣言し、その定義を分離すべき
**** 3. Config
- 環境毎に異なるアプリケーションの設定値はコード上から分離すべき
**** 4. Backing services
- ネットワーク越しに利用するサービスは、アプリケーション上のリソースとして考えることでコードを変更することなく切り替えられるべき
**** 5. Build, release, run
- アプリケーションはコードベースから厳密に分離されたビルドステージ、リリースステージ、実行ステージを経て本番環境にデプロイされるべき
**** 6. Processes
- アプリケーションは 1 つもしくは複数のステートレスなプロセスとして実行すべき
**** 7. Port binding
- アプリケーション自体がポートをバインドして Web アプリケーションとして公開できるようにすべき
- ApacheやTomcatは利用せず、アプリケーション自信がポートを持っている状態とすべき
**** 8. Concurrency
- アプリケーションをプロセスとして扱い、プロセス単位で水平にスケール可能とするべき
**** 9. Disposability
- アプリケーション、プロセスに関する起動や終了時間を最小化するように努めるべき
**** 10. Dev/prod parity
- アプリケーションの継続的なデプロイが実現できるように、開発環境と本番環境の差を可能な限り小さく保つべき
**** 11. Logs
- ログをイベントストリームとして扱うべき
**** 12. Admin processes
- 管理タスクを 1 回限りのプロセスとして実行すべき
- 管理作業の自動化
*** Link

** Glossary
*** COCOMO
=======
## Glossary
### COCOMO
>>>>>>> da64b3e6149158f439ef4f2f452104987db5f3cf:Development.md
- constructive cost model
  ソフトウェア開発の工数、開発期間の見積もり手法の一つ。
  $y=ax^b$ として開発期間を求める。
### CMMI
- Capability Maturity Model Integration、 能力成熟度モデル統合
  組織が「プロセスをより適切に管理できるようになる」ことを目的として、遵守すべき方針を体系化したもの。
  
#### Level

##### 段階表現
- 5段階の成熟度レベル（レベル1からレベル5）
##### 連続表現
- 4段階の成熟度レベル（レベル0からレベル3, v1.2までは0-5までの6段階。）
  
#### CMM
- Capability Maturity Model 能力成熟度モデル

#### PCMM
- People Capability Maturity Model, People CMMI
## Personal Development
### Link
- [[https://www.google.com/search?q=%E5%80%8B%E4%BA%BA%E9%96%8B%E7%99%BA&oq=%E5%80%8B%E4%BA%BA%E9%96%8B%E7%99%BA&aqs=chrome..69i57j69i59j69i61j0j69i61l2.2892j0j7&sourceid=chrome&ie=UTF-8][個人開発 - Google]]
- [[https://www.google.com/search?q=%E5%80%8B%E4%BA%BA%E9%96%8B%E7%99%BA+%E3%83%9E%E3%83%8D%E3%82%BF%E3%82%A4%E3%82%BA&oq=%E5%80%8B%E4%BA%BA%E9%96%8B%E7%99%BA%E3%80%80&aqs=chrome.2.69i57j0l5.4285j0j7&sourceid=chrome&ie=UTF-8][個人開発 マネタイズ - Google]]

- [[https://qiita.com/kazukichi/items/aeba286c2a750081e5c0][WEBサービスで起業したい人に読んで欲しい２０のコト @kazukichi - Qiita]]
- [[https://qiita.com/curryperformer-kato/items/a7dc9a41200b6c9c1912][Webサービス個人開発するなら読みたい情報源12 @curryperformer-kato - Qiita]]
- [[https://qiita.com/jabba/items/1a49e860a09a613b09d4][開設後３週間で収益１０万円を得た個人開発サイトでやったことの全部を公開する @jabba - Qiita]]
- [[https://blog.sesere.net/entry/2017/10/27/183957][【7年かかった】19歳から7年、1人で30個のWebサービスを作り一発当ててもう働く必要がなくなったので振り返ってみる - 考えすぎてしまう人のブログ]]

- [[https://www.jabba.cloud/20190120-andrey-indie-maker/][個人開発者のAndreyは今、世界で最も熱い男。彼のブログから学ぶ個人開発のあり方 - ジャバ・ザ・ハットリ]]

## Book
- [[http://keens.github.io/blog/2016/01/17/dokugakudepuroguraminguwoyattekitanakadeyokattagijutsushowoageteiku/][独学でプログラミングをやってきた中で良かった技術書50選 - κeenのHappy Hacκing Blog]]
- [[http://rkx1209.hatenablog.com/entry/2016/12/25/141543][低レイヤーの歩き方 - るくすの日記 ~ Out_Of_Range]]
- [[http://yuseinishiyama.com/posts/2014/07/07/recently-read-books/][プログラマ歴2年の文系出身プログラマがこの1年で読んだ本 - だからといって、このままでいいはずがない。]]
## Memo
### 標準工期の計算
- 
  COCOMOモデルを元に、JUASが求めた標準工期。
  $D=2.4E^\frac{1}{3}$  (D:開発工期、E:工数)
  [[https://www.juas.or.jp/servey/library/pdf/08swm_pr_dev.pdf][ユーザ企業SWM2008調査報告（開発プロジェクト） - JUAS]]
  [[http://www.atmarkit.co.jp/news/200707/05/juas.html][最適な工期は「投入人月の立方根の2.4倍」、JUASが調査 - @IT]]

### 生産性
- [[http://blog.goo.ne.jp/xmldtp/e/513c525aa1b41929a7e8c49f66ba35b8][１人月あたり、何ステップ？１画面あたり、何人日でできる？の考え方 - ウィリアムのいたずらの開発日記]]
### Waterfall
#### 提案・営業
##### 評価
- 業務の理解
- 現行システムの理解
- 次期要件の理解

##### 解決案の作成
- 全体方針の作成
- アーキテクチャの検討

##### 見積もり
- 工数・金額の見積もり
  - 1人当たり100万程度？

##### 提案
- 提案
  
#### デリバリー
##### 管理
##### 構築
###### 要件定義
###### 外部設計
- 外部設計書
  - 着目点は？開発可能性（正確性）と保守性

###### 内部設計
- 詳細設計書
  - 着目点は？開発可能性（正確性）

###### 開発・単体テスト
###### コンポーネント間テスト
###### サブシステム間テスト
###### システムテスト

#### 保守
- 保守性
  保守・メンテナンス性の高いシステムを、構築時・アーキテクチャ

#### memo
##### 難しさは何か？
- 感覚としては規模の大きさ。
  小さなシステムであれば簡単な、単純な形のものが多い。
  ⇒すべてを一人の頭の中に入れることが難しい。
  - 相互に影響度の少ない、小さな部品をたくさん作る。
    インプット・アウトプットの正確な定義が必要
  - すべて頭に入れる。時間をかける？
  - 情報を共有・参照が容易となるようにする。
    wikiなどを使い、編集する。

#### link
- [[http://www.atmarkit.co.jp/ait/articles/0901/28/news151.html][現状のソフトウェア開発は間違っていないか？ - @IT]]
- 

### システムの種類
#### 概要
- バッチインプット
- 画面インプット
- DB
- バッチアウトプット
- 画面アウトプット

#### 精算

#### 参照

##### Webサイト

### ウォーターフォール型開発のドキュメント
- 
  |----------------------------+------------------------------------------------------------------------------|
  | フェイズ                   | ドキュメントの種類                                                           |
  |----------------------------+------------------------------------------------------------------------------|
  | 要件定義                   | 要件定義書                                                                   |
  | 基本設計                   | 基本設計書、機能仕様書、ネットワーク設計書、SW/HW（SoftWare/HardWare）構成書 |
  |                            | セキュリティ設計書、性能・信頼性設計書、データ構造定義書（ER図）             |
  |                            | テーブル定義書、画面定義書、画面遷移定義書、帳票定義書、開発標準書           |
  | 詳細設計                   | 詳細設計書、クラス設計書、構成管理定義書、インターフェイス設計書             |
  | 開発・単体テスト           | 単体テスト仕様書                                                             |
  | 結合テスト・システムテスト | テスト計画書、結合テスト仕様書、システム・テスト仕様書                       |
  | 本番／運用                 | 環境構築手順書、運用定義書、障害対応手順書、移行仕様書、移行手順書           |
  |----------------------------+------------------------------------------------------------------------------|

### アジャイルドキュメント(ドキュメント作成・保守の心構え)
- 
  - ドキュメントは必要十分でなければならない
  - ドキュメントは、ソース・コードと同じでシステムの一部である
  - チームの第2の作業は次の作業への備えである
  - ドキュメントを持つことによる利点は、ドキュメントを作成および保守するためのコストを上回らなければならない
  - ドキュメントを信用してはならない
  - システムごとにドキュメントに対するニーズは異なる
  - ドキュメントがなぜ必要かを尋ねるべきである
  - ドキュメントに投資するかどうかは、技術上の判断ではない
  - 必要なときだけドキュメントを作成するべきであり、ドキュメントのためのドキュメントを作成してはならない
  - ドキュメントが十分かどうかを決めるのは、開発者ではなく、顧客である

  [[http://www.atmarkit.co.jp/fdotnet/special/agiledocument01/agiledocument01_01.html][ツールを使ったドキュメント作成技法（前編） - @IT]]

### 価値あるドキュメントを作成するコツ
- ドキュメントを書く目的を意識する
- 読み手を意識する
- ドキュメントの構成を意識する
- ドキュメント間で整合性が取れている必要がある
  
## Link
- [[http://sysdev.sakura.ne.jp/category/development][システム開発の基礎 - エンジニア目線のシステム開発]]
