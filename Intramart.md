# intra-mart
## Kind
### intra-mart Accel Platform
### intra-mart Accel Application
### Accel-Mart
### IM-BPM
### intra-mart WF
### Biz ∫
## IM-Juggling
- モジュールの管理、WARファイルのリモートデプロイを実行できる環境構築ツール。
### Structure
#### conf/
##### bis-config
##### forma-config.xml
##### solr-config.xml
- solr関連の設定
#### modules
#### schema
#### juggling.im
##### ベースモジュール
##### アプリケーション
##### ユーザモジュール
##### 設定ファイル
###### IM-BIS for Accel Platform
####### bis-config.xml
####### bis-tenant-config.xml
##### 履歴
#### resin-web.xml
### Memo
#### トピックス、ベースライン他が何も表示されない
- ネット接続の問題。プロキシを疑うか、そもそもネット接続されていないかなどの確認をする。
## Accel Platform
### Setup
#### Setup Middleware
##### JDK
- setup
##### Application Server
- Resin
##### Database
- postgres
  - add login roll
  - create database with the role above
##### JDBC Driver
- download JDBC 4 (4.1 is not verified)
- set it under C:/Resin/lib
##### Cassandra
##### Solr
- resinに追加
#### Make WAR file by IM-Juggling
#### Deploy WAR on Resin(Web Application Server)
- deploy前に、以下が必要
  - user/passwordを設定する
    - java -jar lib/resin.jar generate-password username password
      (resin generate-password username password)
    - 上記コマンドで出力されたuser, passwordをresin.propertiesに設定する。
  - resin.propertiesのremote_admin_enable : trueを有効にする。
- deploy
  - resin deploy --user username --password password imart.war
#### Access
- Tenant作成時にErrorが八歳する場合、tenantの名前が設定ファイルと異なっている可能性あり。
  "data-source-mapping-config.xml"に設定が入っている。
#### Uninstall
##### Undeploy
- (win)resin undeploy application-name
- Resinの停止
- webapp以下の該当ファイルを削除

- （現状不明）アプリケーションの削除
  - resin-data配下
  - webapps配下

- Storage領域の削除
- https://www.intra-mart.jp/download/product/iap/setup/iap_setup_guide/texts/uninstallation/index.html
#### Link
- [[http://www.intra-mart.jp/download/product/iap/setup/iap_quick_setup_guide/index.html#][intra-mart Accel Platform クイック セットアップガイド]]
- [[http://www.intra-mart.jp/download/product/iap/setup/iap_setup_guide/index.html][intra-mart Accel Platform セットアップガイド]]
### Tenant
#### Setup
- テナント環境セットアップは、モジュールやアプリケーションを新たに追加した場合に必要となるセットアップ処理の実行と、その実行履歴を管理する機能。
  実行履歴が管理されるため、同じセットアップが2度実行されることはない。
  機能追加や仕様変更のため、追加でセットアップ処理を行うことも可能。
##### Setup settings file / セットアップ設定ファイル
- Location : src/main/conf/products/import/basic/{ArtifactId (ProjectName)}/
  ex) src/main/conf/products/import/basic/my_project/
- File : import-{ArtifactId (ProjectName)}-config-1.xml
  ex) import-my_project-config-1.xml
  - "1"はテナント環境セットアップのバージョン管理のための番号（スキーマバージョン）。初回は必ず"1"とする。
##### built-in operations / 組み込み可能な処理
###### database / データベース系
- 拡張子.sql
####### create-file / DDL実行
- tag : <create-file>
  システムストレージからの相対パスを指定(拡張子sql)
####### insert-file / DML実行
- tag : <insert-file>
  システムストレージからの相対パスを指定(拡張子sql)
###### tenant-master / テナントマスタ系
- 拡張子.xml
####### role-file / ロール
####### account-file / アカウント
####### calendar-file / カレンダー:カレンダー
####### calendar-day-set-file / カレンダー:日付情報セット
####### calendar-day-file / カレンダー:日付情報
####### calendar-merge-file / カレンダー:カレンダーマージ
####### menu-group-category-file / メニュー:メニューカテゴリ
####### menu-group-file / メニュー:メニューグループ
####### authz-resource-group-file / 認可:リソースグループ
####### authz-resource-file / 認可:リソース
####### authz-subject-group-file / 認可:サブジェクト
####### authz-policy-file / 認可:ポリシー
####### job-scheduler-file / ジョブスケジューラ
###### 拡張処理
####### extends-import-class / 拡張インポート
######## Javaプログラム実行
- インターフェースjp.co.intra_mart.foundation.security.ExtendsImport実装クラスを、完全修飾クラス名で指定する。
  doImportが実行される。
  (上記interfaceはim_import_export_base-x.x.x-main.jarに入っている。x.x.xはバージョン番号。)
######## サーバサイドJavaScriptプログラム実行
- doImportメソッドを実装したサーバサイドJavaScriptを、ルートからの相対パスで拡張子.jsを付けて指定する。
  doImportが実行される。
#### Link
- [[http://www.intra-mart.jp/download/product/iap/im_import_export/tenant_environment_setup_specification/index.html][intra-mart Accel Platform テナント環境セットアップ 仕様書]]
- [[http://www.intra-mart.jp/download/product/iap/operation/tenant_administrator_guide/][intra-mart Accel Platform テナント管理者操作ガイド]]
### Middleware
#### JDK
#### Resin
#### DB
#### Apache Cassandra
#### Apache Solr
### Architecture
#### Load Balancer
#### Web Server
#### Web Application Server
#### intra-mart Accel Platform
- IM-Jugglingにより生成されたWRAファイルをデプロイする
#### RDB
#### Storage
- 添付ファイルや各種ドキュメントの電子ファイルの保存先として利用する。
#### Apache Cassandra
- IMBoxを利用する場合に必要となる。
#### Apache Solr
- IM-ContentsSearchを利用する場合に必要となる。
### im-BizAPI
#### 業務基盤ツール
##### IM-Workflow
###### About
- ワークフローの処理内容と処理順序を示す「フロー定義」に従い、その流れに応じて処理を行う「案件」を進める機能。
###### Edit
####### コンテンツ定義
######## 基本情報
######## 画面
######### 画面種別
######### パス種別
- スクリプト開発モデル
  - スクリプトパス
    スクリプト開発モデルプログラムのソースディレクトリからの相対パス形式を指定する。
    デフォルトではWEB-INF/jssp/srcからの相対パス形式。
- JavaEE開発モデル
  - アプリケーションID
  - サービスID
- JSP or Servlet
  - ページパス
######## ユーザプログラム
- ワークフローの処理時に実行するアプリケーションプログラム。
######### プラグイン種別
- 案件開始処理
  案件が開始される際に呼び出されるプログラム
- 案件終了処理
- アクション処理
  申請等の処理が起動された際に呼び出されるプログラム
- 到達処理
  ある処理によりノードに処理が進んだ際に呼び出されるプログラム
- 分岐処理
  分岐先を判定するプログラム
- 結合処理
  分岐終了ノードの次へ遷移してよいかを判定するプログラム

######### プラグイン種類
- スクリプト開発モデル
- JavaEE開発モデル
- LogicDesigner
######## メール
######## IMBox
######## ルール
####### ルート定義
- 申請から最終承認までの処理の流れを保持する。
  ルート定義を利用するフロー定義において、ルートに定義された各ノードの設定を使用することができる。
####### フロー定義
######## 基本情報
######## 参照者
######## コンテンツ詳細
######## ルート詳細
####### 案件プロパティ
- 案件処理中にユーザコンテンツ固有の業務データを保持する。
  以下の機能で使用可能。
  - 案件の一覧表示画面での表示
  - ルールが判定するパラメータとしての利用
  - メールテンプレートやIMBoxテンプレートの置換文字列としての利用
######## 型
- 文字列
- 数値
######## 仕様種別
- 一覧表示項目の項目
- メールの置換文字列
- IMBoxの置換文字列
- ルールの条件変数
####### ルール
####### メール定義
- ワークフローの処理時に送信するメールの送信先や内容のひな形を定義する。
####### IMBox定義
- ワークフローの処理時にIMBoxへ送信する内容のひな形を定義する。
###### Node
####### 開始ノード
####### 終了ノード
####### 申請ノード
####### 承認ノード
####### 動的承認ノード
####### システムノード
- Workflow外の別のプログラムで案件の処理を行うことを示すノード。
####### 確認ノード
####### 同期開始ノード
####### 同期終了ノード
####### 分岐開始ノード
####### 分岐終了ノード
####### 横配置ノード
####### 縦配置ノード
####### テンプレート置換ノード
####### テンプレート開始ノード
####### テンプレート終了ノード
####### コメント
####### スイムレーン
- ルート上のノードを分類、整理する際に枠線表示として使用する。処理に
###### Programming
####### Screen
####### User Program
######## 案件開始処理
- 案件が開始される際に、一度実行される処理。
######## 案件終了処理
- 案件が終了する際に、一度実行される処理。
######## アクション処理
- 下記のような行為を行った場合に実行される処理。
  - 申請 / apply
  - 再申請 / reapply
######## 到達処理
- ノードに到達した場合に実行される処理。
######## 分岐開始処理
- 分岐開始ノードで「ユーザプログラムで分岐する」を選択した場合に実行される処理。
######## 分岐終了処理
######## 案件終了処理（トランザクションなし）
####### Other Program
###### Link
- [[http://www.intra-mart.jp/document/library/iap/public/im_workflow/im_workflow_administrator_guide/index.html][intra-mart Accel Platform IM-Workflow 管理者操作ガイド]]
- [[http://www.intra-mart.jp/download/product/iap/im_workflow/im_workflow_user_guide/index.html][intra-mart Accel Platform IM-Workflow ユーザ操作ガイド]]
- [[http://www.intra-mart.jp/document/library/iap/public/im_workflow/im_workflow_specification/][intra-mart Accel Platform IM-Workflow 仕様書]]
- [[http://www.intra-mart.jp/document/library/iap/public/im_workflow/im_workflow_programming_guide/][intra-mart Accel Platform IM-Workflow プログラミングガイド]]

- [[https://www.intra-mart.jp/apidoc/iap/apilist-ssjs/doc/im_workflow/com/imwCodeList.html][IM-Workflow CodeList]]

##### Portal
##### IMBox
- 企業向けSNS機能。
##### ViewCreator
- intra-martの画面上からDBデータを使用して、表やグラフを作成するツール。
###### Data データ
####### Query クエリ
- データベース上のテーブルを使用して作成されるSQLクエリ
####### データ参照
- クエリの表示方法（表orグラフなど）の設定
  1つのクエリから複数の見せ方をさせることが可能。
######## リスト集計
######## クロス集計
######## グラフ集計
###### Memo
####### 対応するフィールドの型
- https://www.intra-mart.jp/download/product/iap/viewcreator/viewcreator_administrator_guide/texts/about/about.html
######## PostgreSQL
######### 文字列型
- varchar
- character
- text
######### 数値型
- smallint
- bigint
- decimal
- numeric
- real
######### 日付型
- date
######### タイムスタンプ型
- timestamp
######### バイナリ型
- bytea
######### 真偽値型
- boolean
####### 日付フォーマットパターン
- https://www.intra-mart.jp/download/product/iap/viewcreator/viewcreator_administrator_guide/texts/apply_guide/apply_guide_6.html
- フォーマットパターンは以下ファイルで設定している、追加も可能。
  - %コンテキストパス%/WEB-INF/conf/viewcreator-config.xml
- 設定例
  <date-format-list>
    <date-format>yyyy/MM/dd HH:mm:ss</date-format>
    <date-format>yyyy/MM/dd HH:mm</date-format>
    <date-format>yyyy/MM/dd</date-format>
    <date-format>yyyy/MM</date-format>
  </date-format-list>
##### TableMaintenance
- データベース上の既存のテーブルに対して、レコードの新規登録・更新・削除を行うことができる。
##### IM-Notice
- 通知受信クライアント
##### IM-LogicDesigner
- ビジネスロジックを簡単に作成するアプリケーション。
#### 基盤機能
##### 開発フレームワーク
###### スクリプト開発フレームワーク
- スクリプト開発モデル
  プレゼンテーション・ページ(HTML)とファンクションコンテナ(サーバサイドJavaScriptファイル)の2つのファイルを生成する。
  少人数システム開発における生産性がたかくなる傾向がある。
####### Contents
######## プレゼンテーション・ページ
- ユーザインターフェース部分に相当。拡張子は.html固定。
  HTMLファイルにIMARTタグを追加することで、JavaScriptと関連付けて呼び出すことが可能。
######## ファンクション・コンテナ
- ビジネスロジック部分に相当。拡張子は.js固定。
  ファンクションコンテナとプレゼンテーションページはワンセットのため、ファイルラベル名は同一となる。
######## ルーティングテーブル
####### Development
######## Basics 基本
####### 設定ファイル
######## source-config.xml
- プログラムリソースの読み込みや実行に関する制御を行う設定ファイル。
- Path
  - %CONTEXT_PATH%/WEB-INF/jssp/compatible/src/
  - %CONTEXT_PATH%/WEB-INF/jssp/platform/src/
  - %CONTEXT_PATH%/WEB-INF/jssp/product/src/
  - %CONTEXT_PATH%/WEB-INF/jssp/src/
####### Routing ルーティング
- スクリプト開発モデルでのルーティングファイルは、以下パスの配下に設置、が基本。
  %CONTEXT_PATH%/WEB-INF/conf/routing-jssp-config/
- file-mapping要素のpath属性に{[識別子]}と記述することで、URL途中の値がリクエスト・パラメータとして扱える。

####### Link
- [[http://www.intra-mart.jp/document/library/iap/public/development/script_programming_guide/index.html][intra-mart Accel Platform スクリプト開発モデル プログラミングガイド]]
###### IM-JavaEE Framework
- JavaEE開発モデル
  JSP、Servelt、ActionForm, DAOなどを利用して開発を行う。
  Seasar2(SAStruts+S2JDBC)を利用して効率化する。
  コンポーネント再利用や並行分散開発により、スクリプト開発モデルに比べ大規模システム開発において生産性を発揮する。
####### コンポーネント
- [[http://www.intra-mart.jp/download/product/iap/iap_introduction/texts/std_function/app_dev.html#id7][3.2.2.3. SAStrutsとS2JDBCによるアプリケーション開発 - intra-mart Accel Platform イントロダクション]]
######## Action
- クライアントからのリクエスト（フォーム）を受け取り、ビジネスロジックを実行
  ビジネスロジックはサービスとして切りだし、Actionから呼び出す
######## Form
- 画面入力情報を格納
  アクションでリクエストパラメータを受け取るためのオブジェクト。
  StrutsのActionFormクラスに相当。
######## JSP
- 画面
  アクションでの処理後にフォワードされ、ブラウザに返却するHTMLの生成を行う
######## DTO
- データオブジェクト
  FormやEntity以外のデータオブジェクトを格納
######## Logic
- 業務ロジック
  DTO(検索条件)を参照し、Service(DBアクセス)の呼び出し
######## Service
- 業務ロジック
  エンティティの操作。データベースアクセス処理を定義。
######## Entity
- データベースのテーブルとマッピングするオブジェクト
####### Link
- [[http://www.intra-mart.jp/document/library/iap/public/development/sastruts_s2jdbc_programming_guide/index.html][intra-mart Accel Platform SAStruts+S2JDBC プログラミングガイド]]
###### TERASOULNA Server Framework for Java (5.x)
- NTTデータが公開しているJava開発フレームワーク。
  Spring MVC 4.1 + SpringFramework4.1 + MyBatis3.2.8 + 共通ライブラリ群
- [[http://www.intra-mart.jp/download/product/iap/iap_introduction/texts/std_function/app_dev.html#common-terasoluna][3.2.2.4. TERASOLUNA Server Framework for Java (5.x) - intra-mart Accel Platform イントロダクション]]

####### Link
- [[http://terasolunaorg.github.io/guideline/][TERASOLUNA Server Framework for Java (5.x)]]
- [[http://www.intra-mart.jp/document/library/iap/public/development/tgfw_programming_guide/index.html][intra-mart Accel Platform TERASOLUNA Server Framework for Java (5.x) プログラミングガイド]]
###### SAStruts Framework on Accel Platform
###### Maskat Framework on Accel Platform
#### エクステンションシリーズ
##### intra-mart e Builder for Accel Platform
###### Structure
####### module.xml
- ユーザ定義モジュールを作成するために必要なファイル。
  編集する際に、専用のモジュール・エディタが開く。
####### src/
######## main/
######### conf/
########## routing-jssp-config
- ルーティング設定ファイルを配置する
###### Project
####### Partitioning
######## main
- モジュールの主たるコードやリソースを配置する
######## test
- テストを行うためのコード・リソースを配置する。
####### Directory
######## generated
- 対象例:*.java
- 配置先:WEB-INF/libのjarファイル内
- 自動生成されたJavaファイルを格納する。
######## java
- 対象例:*.java
- 配置先:WEB-INF/libのjarファイル内
######## resource
- 対象例:*.java
- 配置先:WEB-INF/libのjarファイル内
######## conf
- 対象例:*.properties, *.xml
- 配置先:WEB-INF/conf配下
######## jssp
- 対象例:*.properties, *.xml
- 配置先:WEB-INF/jssp配下
######## plugin
- 対象例:*.html, *.js
- 配置先:WEB-INF/plugin配下
######## public
- 対象例:*.html, *.css, *.swf等
- 配置先:WARを展開したフォルダ配下
######## schema
- 対象例:*.xsd
- 配置先:WEB-INF/schema配下
######## storage/public
- 対象例:*.*
- 配置先:%ストレージのパス%/storage/pubilc配下
######## storage/system
- 対象例:*.*
- 配置先:%ストレージのパス%/storage/system配下
######## webapp
- 対象例:*.jsp, WEB-INF/に配置するファイル(iconファイル等)
- 配置先:WARを展開したフォルダ配下
###### Settings
####### Workspace
- ウィンドウ->設定
######## 一般
######## e Bulider
######### license
- ライセンス・コード
######## Java
######### インストール済みのJRE
- 利用するJREバージョンの設定
######### コンパイラー
######### ビルド・パス
######## Maven
- Download repository index updates on startup
  Mavenを利用しない場合、本オプションを無効にする。
######## Web
######### CSSファイル
######### HTMLファイル
- エンコード
  エンコード設定。UTF-8を推奨。
####### Project
- プロジェクトを右クリック->プロパティ
######## e Builder
######### Module Assembly
- 連携するResin上のWARファイル（展開後）を設定する。
######## Javaコンパイラー
######## Javaのビルドパス
######### ソース
######### プロジェクト
######### ライブラリー
######### 順序およびエクスポート
#####
###### Developing Model
####### スクリプト開発モデル
######## HTMLエディター
####### im-JavaEEフレームワーク
######## JSPエディター
######## im-JavaEEフレームワークエディター
######### アプリケーション
######### サービス
######### イベント
######### DAO(モデル)
######### DAO
######### SQLビルダ
####### SAStruts+S2JDBCフレームワーク
####### 業務スケルトン
###### Link
- [[http://www.intra-mart.jp/document/library/ebuilder/public/e_builder_setup_guide/texts/all_in_one/index.html][intra-mart e Builder for Accel Platform セットアップガイド]]
- [[http://www.intra-mart.jp/document/library/ebuilder/public/e_builder_user_guide/index.html][intra-mart e Builder for Accel Platform アプリケーション開発ガイド]]
##### IM-BIS for Accel Platform
- BIS(Business Integration Suite)
###### Architecture
####### IM-BIS for Accel Platform
- 画面、BPM/WFなどを統合管理するツール
####### Forma
######## IM FormaDesigner for Accel Platform
- Web画面作成のためのGUIツール
####### DataMapper
######## DM Designer
- 画面項目とWebサービス、部品のパラメータを関連付け、データの変換等を行う
######## DM Executor
- イベント発生時に関連頭蹴られたWebサービスを起動し実行する
######## Web Service Register
- 利用するWebサービスを事前に登録する
####### BPM/Workflow
######## BPM Designer
- BPMの流れなどをGUIで定義
######## WF Designer
- WFの流れなどをGUIで定義
######## BPM/WF Engine
- BPM/WFを実行するエンジン
######## BAM
- BPM/WFの実行状況をロギングし、分析用の情報を管理する
###### Role
####### BIS管理者 / bis_manager
- 作成したフローの詳細設定やカスタマイズを行うことができる。
####### BIS業務管理者 / bis_business_manager
- ワークフローやBISフローのフローを作成することができるユーザ。
####### BIS監査者 / bis_auditor
- 監査を目的とした、履歴を参照できるユーザ。
####### BIS担当者 / bis_user
- 申請・承認・処理などを行うことができるユーザ。利用者。
###### Glossary
####### BPM
- Business Process Management ビジネスプロセス管理
###### Edition
####### 新規登録
- BISフロー
  - 一方通行を想定したプロセス。
- ワークフロー
  - 申請・承認を伴うワークフローで利用。避妊や差し戻しなど、柔軟にルートを作成可能。
####### ルート定義（Forma？）
- WFルートの定義
####### IM-BIS - フロー編集
- フロー
######## 遷移
- ダブルクリックで該当フローのフォーム編集へ。
- 右上からルート編集へ移動可能
######## 操作
- 右クリックで共有、貼り付け、でフォームを張り付ける
####### フォーム編集
- フローをダブルクリックして登録可能
######## 各種アイテム
######### 更新
- 編集内容の反映、保存
######### 画像アップロード
######### ラベル一覧
######### フィールド一覧
######### スマートフォン設定
######### グリッド
######### 枠線
######### 再利用
######### テンプレート
######### ヘッダーとフッター
######### アクション設定
######### ツールキット
########## 入力アイテム
########### 文字列 String
############ プロパティ
########### 複数行文字列 Multiline string
########### 日付 Date
########## ボタンアイテム
########### ボタン(登録) Register Button
########### ボタン(一覧に戻る) Back to list Button
########### ボタン(一時保存) Temporary save Button
########## 共通マスタアイテム
########## WFアイテム
########## 汎用アイテム
########## 表示アイテム
########## 互換性アイテム
######### アイテムコピー
###### Manual
####### IM-BIS ビギナーズガイド
- 
###### Link
- [[http://www.intra-mart.jp/document/library/bis/public/bis_setup_guide/index.html][IM-BIS for Accel Platform セットアップガイド]]
- [[http://www.intra-mart.jp/document/library/bis/public/bis_beginners_guide/][IM-BIS for Accel Platform IM-BIS ビギナーズガイド]]
- [[http://www.intra-mart.jp/document/library/bis/public/bis_administrator_guide/index.html][IM-BIS for Accel Platform システム管理者 操作ガイド]]
- [[http://www.intra-mart.jp/download/product/bis/manager_guide/index.html][IM-BIS for Accel Platform 業務管理者 操作ガイド]]
- [[http://www.intra-mart.jp/document/library/bis/public/bis_user_guide/index.html][IM-BIS for Accel Platform ユーザ 操作ガイド]]
##### IM-FormaDesigner
###### Setting
####### forma-config
###### Link
- [[http://www.intra-mart.jp/document/library/forma/public/forma_setup_guide/index.html][IM-FormaDesigner for Accel Platform セットアップガイド]]
##### IM-PDF Designer
##### View Creator
###### Link
- [[http://www.intra-mart.jp/document/library/iap/public/viewcreator/viewcreator_user_guide/index.html][intra-mart Accel Platform ViewCreator ユーザ操作ガイド]]
- [[http://www.intra-mart.jp/document/library/iap/public/viewcreator/viewcreator_administrator_guide/index.html][intra-mart Accel Platform ViewCreator 管理者操作ガイド]]
- [[http://www.intra-mart.jp/document/library/iap/public/im_workflow/im_workflow_viewcreator_guide/index.html][intra-mart Accel Platform ViewCreator for IM-Workflow 連携ガイド]]
### API Specification / Packages
#### jp.co.intra_mart.common.platform.atabase.util
##### Classes
###### DatabaseUtil
####### Methods
######## createDatabaseInfo()
- static Map<String,Number> createDatabaseInfo()
  DB名とDBタイプを返却する。
- 導入バージョン:8.0.14
#### jp.co.intra_mart.foundation.context
##### Classes
###### Contexts
####### Methods
######## get(Class<T> type)
- static <T extends Context> get (Class<T> type)
  引数にマッチするアクセスコンテキストを、アクセスコンテキストストアから取得して返却する。
###### ContextStatus
##### Exceptions
###### ContextNotFoundException
###### ContextPropertyException
#### jp.co.intra_mart.foundation.context.model
#### jp.co.intra_mart.foundation.context.model.job_scheduler
##### Interfaces
###### Job
###### JobSchedulerContext
- public interface JOBSchedulerContext extends Context
- ジョブスケジューラに関する情報を格納するコンテキストクラス。
  
####### Methods
######## getTaskId()
- String getTaskId()
  タスクIDを取得する。
###### JobSchedulerManager
##### Class
###### BaseJob
###### JobResult
###### JobSchedulerManagerFactory
##### Enums
#### jp.co.intra_mart.foundation.context.model.job_scheduler.exception
##### Exceptions
###### JobExecuteException
- ジョブスケジューラの例外クラス
#### jp.co.intra_mart.foundation.extension.spring.context
##### Classes
###### ApplicationContextProvider
####### Methods
######## getApplicationContext()
- static org.springframework.context.ApplicationContext getApplicationContext()
- ApplicationContextを返す。
#### jp.co.intra_mart.foundation.job_scheduler
##### Interfaces
###### Job
- ジョブスケジューラサービスから実行されるジョブ実装のためのインターフェース
###### JobSchedulerContext
- ジョブスケジューラに関する情報を格納するコンテキストクラス
##### Classes
###### JobResult
- ジョブの実行処理の結果を格納するクラス
#### jp.co.intra_mart.foundation.workflow.application.model
##### Classes
###### ApplyResultModel
- 申請結果情報 モデルクラス
####### Constructors
####### Methods
#### jp.co.intra_mart.foundation.workflow.application.model.param
##### Classes
###### ApplyParam
- 申請用パラメータ情報 モデルクラス
- pubilc class ApplyParam
  extends Object
####### Constructors
######## ApplyParam()
####### Methods
#### jp.co.intra_mart.foundation.workflow.application.process
##### Classes
###### ApplyManager
- 申請マネージャ
####### Constructors
######## ApplyManager(String localeId)
- 引数で指定したロケールIDで申請マネージャを新しく生成する。
####### Methods
######## apply(ApplyParam applyParam, Map<String,Object> userParam)
- ApplyResultModel apply(ApplyParam applyParam, Map<String,Object> userParam)
  申請処理を実行する。
#### jp.co.intra_mart.foundation.security.message
##### Classes
###### MessageManager
- メッセージを取得するためのクラス
####### Methods
######## getInstance()
- static MessageManager getInstance()
  メッセージマネージャのインスタンスを取得する
######## getMessage(String key, String arg)
- String getMessage(String key, String arg)
  メッセージを取得する
#### jp.co.intra_mart.framework.extension.spring.context
##### Classes
###### ApplicationContextProvider
####### Methods
######## getApplicationContext()
- static org.springframework.context.ApplicationContext getApplicationContext()
- ApplicationContextを返す。
### Structure(Deploy file)
#### wepapps/
##### (application)/
###### WEB-INF/
####### conf/
######## authz-resource-mappers/
- mapperの設定を行う。
######### im_authz.xml
######## log/
######### im_logger_database.xml
- DB_LOG
  level value : off | trace | ...?
  トレース情報
######## products/
######### import/
########## basic/
########### im_tenant/ (%ショートモジュールID%)
############ improt-im_tenant(%ショートモジュールID%)-config-n(%スキーマバージョン%).xml
######## routing-jssp-config/
- ルーティングテーブルを保持する。
######## bis-config.xml
######### rule-cache
- キャッシュ機能利用の有無設定。
  value : true/false
######### delete-bpm-link
- IM-BISを利用しない際はtrueとする。
  value : true/false
######### transaction-file-location
########## history
- value : 
  - db : BinaryデータとしてDBに保存する場合
  - storage : ファイル実体としてストレージに保存する場合
######## bis-tenant-config.xml
######## cassandra-config.xml
- Cassandraサーバ接続に関する設定情報
######## data-source-mapping-config.xml
######### Tags
########## system-data-source
- システムデータベースとして利用するデータソースを設定する
########## tenant-data-source
- テナントデータベースとして利用するデータソースを設定する。
########## resource-ref-name
- Web Application Serverに設定されているリソース参照名を指定する項目
########## tenant-id
- テナントのテナントIDを指定する
######### Link
- http://www.intra-mart.jp/download/product/iap/setup/im_configuration_reference/texts/im_database/data-source-mapping-config/index.html
######## forma-config.xml
######## network-agent-config.xml
- bind-port : Web Application Server間で通信を行う際に利用するポート番号
- port-range : bind-portで指定されたポート番号が既に使用されていた場合の代替えポート番号のレンジ。
######## solr-config
- Solrサーバへの接続設定情報を保持するファイル。
######## storage-config.xml
######### Tags
########## storage-info
########## root-path-name
- Storage領域のパスを設定
####### jssp/
######## compatible/
######### src/
########## source-config.xml
- スクリプト開発モデルのプログラムリソースの読み込みや実行に関する制御を行う設定ファイル。
  ../../src/source-config.xmlも参照のこと。
######## platform/
######### src/
########## source-config.xml
- スクリプト開発モデルのプログラムリソースの読み込みや実行に関する制御を行う設定ファイル。
  ../../src/source-config.xmlも参照のこと。
######## product/
######### src/
########## bis/
########### common/
############ user_program/
############# apply_process.js
############# bam_action_process.js
############# bam_end_process.js
############# web_service_execution_end.js
############# web_service_execution_start.js
########### imw/
############ view/
############# apply_view.js
############# approve_view.js
############# reference_view.js
############# retry_view.js
########## forma/
########### imw/
############ process/
############# apply_process.js
########## source-config.xml
- スクリプト開発モデルのプログラムリソースの読み込みや実行に関する制御を行う設定ファイル。
  ../../src/source-config.xmlも参照のこと。
######## src/
######### source-config.xml
- スクリプト開発モデルのプログラムリソースの読み込みや実行に関する制御を行う設定ファイル。
  ディレクトリに対して有効で、サブディレクトリに対しても再帰的に影響を及ぼす。
  
########## Tags
########### charset
- 文字エンコーディングの設定
########### javascript
- JavaScriptの設定
############ compiler
- JavaScriptコンパイラに関する設定
############ optimize
- JavaScriptコンパイラの最適化に関する設定
########### view
- スクリプト開発モデルのHTMLに関する設定
############ compiler
- Viewコンパイラに関する設定
####### modules/
####### log/
####### schema/
######## routing-jssp-config.xsd
- jssp用ルーティングファイルフォーマット
######## routing-service-config.xsd
######## routing-servlet-config.xsd
####### resin-web.xml
- databaseのコネクション設定などが存在
#### storage
- Pathはstorage-config.xmlで設定
##### public
###### storage
####### default
- 配下をテナント管理/ファイル操作、で利用できる。
##### system
- systemで利用すると思われる
### Screen
#### システム管理者
- http://localhost:8080/imart/system/login
##### システム環境構築
###### ライセンス管理
###### テナント管理
###### テナント環境セットアップ
####### テナント環境セットアップ
####### サンプルデータセットアップ
###### データソース設定
##### システム管理
#### テナント
- http://localhost:8080/imart/login
##### ホーム
- /home、基本的にはポータルとのこと。
##### ポータル/
###### ポータル /portal/desktop
###### ポータル管理/
####### ポートレット一覧
####### グループポータル管理
####### インポート・エクスポート
##### サイトマップ /menu/sitemap
##### 共通マスタ/
###### マスタメンテナンス/
####### ユーザ
####### パブリックグループ
####### 分類
####### 会社
####### 会社グループ
####### 組織
####### 法人・取引先
####### 法人グループ
####### 品目カテゴリ・品目
####### 通過
####### 組織分類
###### プライベートグループ
##### 個人設定/
###### パスワード
###### カレンダー
###### ロケール
###### 日付と時刻の形式
###### テーマ
###### プロファイル
###### マイメニュー
###### メッセージ通知
###### メニュー表示
###### 数値形式
##### テナント管理/
###### 認可
###### メニュー
###### ロール
###### カレンダーメンテナンス
###### テナント情報/
###### ジョブ管理/
###### ファイル操作
###### データベース操作
##### FileExchange
##### ワークフロー
##### IM-BIS/
###### システム管理者/
####### IM-BIS作成/
####### マスタ管理/
####### インポート/
####### エクスポート/
####### フロー運用管理/
###### 業務管理者/
####### IM-BIS作成/
####### フロー/
####### テンプレートカテゴリ定義/
###### ワークフロー/
####### 申請
####### 未処理
####### 処理済
####### 参照
####### 確認
###### BISフロー/
###### 過去案件
###### 印影設定
###### 代理設定/
###### 監査者/
##### LogicDesigner
##### ViewCreator
##### Accel Documents
##### Table Maintenance
###### テーブル一覧
###### テーブル・エクスポート
###### テーブル・インポート
###### テーブル・キャプション登録
###### テーブル一覧
##### Formaアプリ
##### Forma開発者
##### Forma管理画面
##### Forma全文検索管理画面
##### Contents Search
##### コラボレーション
### Setting Files
#### Resin
#### コアモジュール
##### ストレージ設定ファイル
###### storage-config.xml
####### storage-info
- /storage-config/storage-info
####### root-path-name
- /storage-config/storage-info/root-path-name
  ストレージルートとして利用するファイルシステム上のパスを指定する。
- 分散環境を構築する場合
  - Storageのルートディレクトリに指定するパスは全て同じ共有ディレクトリを参照する必要がある。
- 分散環境のサーバをWindowsサービスに登録する場合
  - パスはUNC形式で指定する。
    例:\\servername\drive\directory\file
####### permit-symlink
- シンボリックリンク等をストレージ配下に持つ場合にTrueとする必要がある。
#### テナント管理機能
##### ルーティングテーブル用 認可リソースマッパー定義設定
###### About
- Location : WEB-INF/conf/authz-resource-mappers/{filename}.xml
- Format : WEB-INF/schema/authz-resource-mappers.xsd
###### Tags
####### mapper
######## Attributes
######### name
- マッパー名。ここで設定した名前をルーティングテーブルで指定可能。
######### class
- マッパーの実装裏巣の完全修飾クラス名
##### スクリプト開発モデルルーティング設定
###### About
- Location : WEB-INF/conf/routing-jssp-config/{filename}.xml
- Format : WEB-INF/schema/routing-jssp-config.xsd
###### Tags
####### authz-default
- デフォルト認可設定
- authz-defaultタグを省略した場合、file-mapping, folder-mapping, authzタグを必ず指定する必要がある。
######## Attributes
- ui + action属性か、mapper属性の何れかの設定を行う必要がある。
######### uri
- 認可リソースURIを指定する
######### action
- 認可アクションを指定する
######### mapper
- 認可リソース真っパーを指定する。
  使用可能な値はauthz-resource-mapper設定で設定済みの値。
####### file-mapping
- URLとスクリプト開発モデルのプログラムのマッピングを行う。
######## Attributes
######### path
- マッピングを行うURLを指定する。
  値の末尾にワイルドカードを指定することが可能。
  値に{<識別子>}を記述することでURLの途中の値をリクエスト・パラメータとしてプログラム中で使用可能。
  例：/sample/view/{dataId}
######### page
- マッピングを行うスクリプト開発モデルのプログラムを指定する
######### action
- page属性に指定されたプログラウmの実行前に呼び出す関数を指定する。
  
######### from
- action属性で指定した関数を呼び出すプログラムを指定する。
######### client-type
- マッピングが有効となるクライアントタイプを指定する。
####### folder-mapping
######## Attributes
######### path-prefix
######### folder
######### client-type
####### authz
######## Attributes
######### uri
######### action
######### mapper
####### param
######## Attributes
######### key
######### value
##### パスワード履歴管理設定
###### About
- Location : WEB-INF/conf/password-history.xml
#### Link
- [[http://www.intra-mart.jp/download/product/iap/setup/im_configuration_reference/index.html][intra-mart Accel Platform 設定ファイルリファレンス]]
### Log 
- [[https://www.intra-mart.jp/support/information/texts/logfile/index.html][付録（ログファイル構造詳細） - intra-mart]]
### Glossary
#### tenant テナント
##### マルチテナント
- テナント毎にデータベースの接続先やストレージ領域などを個別に管理・運用可能。
###### バーチャルテナント機能の利用
- 1つのWARファイル内で、論理的にテナントを分割する。
###### WARファイルによるマルチテナント
- WARファイル単位で書くテナントを管理し、データベースの接続先もWARファイル単位で管理する。
####### Setting
- [[http://www.intra-mart.jp/download/product/iap/setup/iap_setup_guide/texts/multi_tenant/index.html][WARファイルによる複数テナント]]
######## Network
- クラスタリングID、クラスタリング用ポート番号、ポートレンジがテナント間で重複しないようにする。
- /conf/network-agent-config.xml
######## DataSource
- テナント毎にデータベース接続先をそれぞれ設定する必要がある
- resin-web.xml : コネクション
- /conf/data-source-mapping-config.xml : マッピング
######## Storage
- テナント毎に利用するStorage領域をそれぞれ設定する必要がある。
- /conf/storage-config.xml : Storageパス(root-path-name)
######## Casandra
- テナント毎にAppache Cassandraの接続先、またはkeyspaceをそれぞれ設定する必要がある
- cassandra-config.xml : 
######## Solr
- テナント毎にAppache Solrを設定する必要がある。
##### テナント環境セットアップ
- デプロイされた各モジュールが動作するための動作前提を構築する処理。
### Memo
#### 分散システムとして構築する場合
- 全てのサーバOSのシステム時計を合わせる必要がある
- 全てのサーバプロセスについてJDKのバージョン・リビジョンを統一する
- https://www.intra-mart.jp/download/product/iap/iap_release_note/texts/limitations/environment.html
### Link
- [[http://www.intra-mart.jp/apidoc/iap/javadoc/all-dev_apidocs/overview-summary.html][intra-mart Accel Platform API Specification]]

- [[http://www.intra-mart.jp/document/library/iap/public/first_step_guide/index.html][intra-mart Accel Platform ファーストステップガイド]]

- [[http://www.intra-mart.jp/download/product/iap/iap_introduction/index.html][intra-mart Accel Platform イントロダクション]]
## IM-Mail
## Accel Documents
### API Specification
### Link
- [[http://www.intra-mart.jp/download/product/iad/im_acceldocuments_setup_guide/index.html][intra-mart Accel Documents セットアップガイド]]
- [[http://www.intra-mart.jp/download/product/iad/im_acceldocuments_user_guide/][intra-mart Accel Documents ユーザ操作ガイド]]
- [[http://www.intra-mart.jp/download/product/iad/im_acceldocuments_repository_api_programming_guide/index.html][intra-mart Accel Documents プログラミングガイド]]
## Resin
- [[file:Resin.org][Resin.org]]
## Error
### デフォルトのテナント作成時に完了しない
- コンテナ名が間違っていると思われる。設定時に注意する。
### リソースグループが登録されていません
- メニューに残っているがアクセス権限がなくなった場合に出るエラー、と思われる。
  エラーメッセージに該当するルーティング設定をconfから探し出し、コメントアウト、再起動。
  ログイン、問題のメニューアイテムを削除し、ルーティング設定を戻した上で、再起動。
  http://imfaq.intra-mart.jp/imqa/faq/print.asp?Option=&NodeID=&DispNodeID=&CID=&Text=&Field=&KW=&KWAnd=&Attrs=&Bind=&SearchID=&FAQID=15&baID=1&strKind=
### データソースが確認できない
- resin-web.xmlなどのデータソース設定不足。
- data-source-mapping-config.xmlの設定不足。
### テナント再作成
## Table
### IM共通マスタ
#### imm_company
##### imm_company_post / 役職
#### imm_corporation
#### imm_currency
#### imm_customer
#### imm_department / 会社組織
##### imm_department
##### imm_department_ath
##### imm_department_ctg
#### imm_item
#### imm_private_grp
#### imm_public_grp / パブリックグループ
##### imm_public_grp_role / パブリックグループ役割
#### imm_unit
#### imm_user / ユーザ
### テナント管理
#### b_m / マスタか？
##### b_m_account
##### b_m_calendar
##### b_m_day_info
##### b_m_link
##### b_m_menu
##### b_m_my_menu
##### b_m_password
##### b_m_portal
##### b_m_portlet
##### b_m_role / ロール
##### b_m_rss
##### b_m_shortcut
##### b_m_sso
##### b_m_system
##### b_m_update
#### b_vc / ViewCreatorか
##### b_vc_data
##### b_vc_query
##### b_vc_search
##### b_vc_tm
#### 認可
- テーブルはimaz~、サブジェクトはim_authz~
##### imaz_company_post_sid
##### imaz_department_sid
##### imaz_ipv4_addr_patterns / IPv4アドレス
##### imaz_meta_subject / 認証
##### imaz_role_sid
##### imaz_subject
##### imaz_term / 期間
### improj_project / プロジェクトチーム機能
### BIS
#### ib_bis~
### フロー？
#### imfr~
### ジョブ
#### imjob
### ?
#### imld
### ワークフロー
#### IMBoxテンプレートテーブル
##### imw_m_imbox_template / IMBoxテンプレート
##### imw_m_imbox_template_classify / IMBoxテンプレート種類
#### コンテンツ定義関連テーブル
##### imw_m_contents / コンテンツ
##### imw_m_contents_detail / コンテンツ詳細
##### imw_m_contents_imbox_template / コンテンツIMBoxテンプレート
##### imw_m_contents_mail_template / コンテンツメールテンプレート
##### imw_m_contents_plugin / コンテンツプラグイン
##### imw_m_contents_rule / コンテンツルール
##### imw_m_page_path / コンテンツ画面パス
#### スレッド監視関連テーブル
##### imw_t_thread / スレッド実行情報
#### バッチ関連テーブル
##### imw_t_batch / バッチ起動日時
##### imw_w_sync_batch / 同期バッチ用ワークテーブル
#### フローグループ定義関連テーブル
##### imw_m_flow_group / フローグループ設定
##### imw_m_group / フローグループ
##### imw_m_group_inc / フローグループ内包
#### フロー定義関連テーブル
##### imw_m_branch_union_detail / 分岐結合条件詳細
##### imw_m_flow / フロー
##### imw_m_flow_cooperation / フロー連携
##### imw_m_flow_cooperation_detail / フロー連携詳細
##### imw_m_flow_default_orgz / フロー標準組織
##### imw_m_flow_detail / フロー詳細
##### imw_m_flow_handle_user / フロー操作権限者
##### imw_m_node_attr_cooperation / ノード属性連携
##### imw_m_node_cooperation / ノード連携
##### imw_m_node_cooperation_detail / ノード連携詳細
#### メールテンプレートテーブル
##### imw_m_mail_template / メールテンプレート
##### imw_m_mail_template_classify / メールテンプレート種類
#### ユーザデータ関連テーブル
##### imw_t_user_data / ユーザデータ
#### ルート定義関連テーブル
##### imw_m_route / ルート
##### imw_m_route_detail / ルート詳細
##### imw_m_route_plugin / ルートユーザ設定
#### ルールテーブル
##### imw_m_rule / ルール
##### imw_m_rule_detail / ルール詳細
#### 案件プロパティ関連テーブル
##### imw_m_matter_property / 案件プロパティ
#### 一時保存関連テーブル
##### imw_t_temporary_save / 一時保存案件
#### 一覧表示パターン関連テーブル
##### imw_m_column / 一覧表示カラム
##### imw_m_list_pattern / 一覧パターン
##### imw_m_selected_column_list / 一覧選択カラム
#### 一覧表示関連テーブル
##### imw_t_user_select_column_list / ユーザ選択一覧パターン
#### 印影設定関連テーブル
##### imw_t_stamp / 印影設定
##### imw_t_stamp_tag / 印影タグ設定
#### 過去案件関連テーブル
##### imw_ayyyymm_matter / 過去案件
##### imw_ayyyymm_matter_attach_b / 過去案件添付ファイルバイナリ
##### imw_ayyyymm_matter_attach_file / 過去案件添付ファイル
##### imw_ayyyymm_matter_auth_user / 過去案件操作権限者
##### imw_ayyyymm_matter_confirm / 過去案件確認処理履歴
##### imw_ayyyymm_matter_his / 過去案件履歴
##### imw_ayyyymm_matter_his_detail / 過去案件履歴詳細
##### imw_ayyyymm_matter_his_locale / 過去案件履歴ロケール
##### imw_ayyyymm_matter_locale / 過去案件ロケール
##### imw_ayyyymm_matter_task / 過去案件タスク
##### imw_ayyyymm_matter_task_stamp / 過去案件印影情報
##### imw_ayyyymm_matter_user_data / 過去案件ユーザデータ
##### imw_ayyyymm_xml_exe_user / 過去案件権限者XML
##### imw_ayyyymm_xml_flow / 過去案件フローXML
##### imw_ayyyymm_xml_history / 過去案件履歴XML
##### imw_ayyyymm_xml_master / 過去案件マスタXML
##### imw_ayyyymm_xml_operation / 過去案件操作履歴XML
##### imw_ayyyymm_xml_progress / 過去案件進捗XML
#### 完了案件関連テーブル
##### imw_t_cpl_matter / 完了案件
##### imw_t_cpl_matter_attach_b / 完了案件添付ファイルバイナリ
##### imw_t_cpl_matter_attach_file / 完了案件添付ファイル
##### imw_t_cpl_matter_confirm / 完了案件確認処理履歴
##### imw_t_cpl_matter_confirm_orgz / 完了案件確認処理権限者組織
##### imw_t_cpl_matter_confirm_user / 完了案件確認処理権限者
##### imw_t_cpl_matter_handle_user / 完了案件操作権限者
##### imw_t_cpl_matter_his / 完了案件履歴
##### imw_t_cpl_matter_his_detail / 完了案件履歴詳細
##### imw_t_cpl_matter_his_locale / 完了案件履歴ロケール
##### imw_t_cpl_matter_locale / 完了案件ロケール
##### imw_t_cpl_matter_task / 完了案件タスク
##### imw_t_cpl_matter_task_stamp / 完了案件印影情報
##### imw_t_cpl_matter_user / 完了案件タスク完了ユーザ
##### imw_t_cpl_matter_user_data / 完了案件ユーザデータ
##### imw_t_cpl_matter_user_target / 完了案件完了タスク処理対象種別
##### imw_t_cpl_xml_exe_user / 完了案件権限者XML
##### imw_t_cpl_xml_flow / 完了案件フローXML
##### imw_t_cpl_xml_history / 完了案件履歴XML
##### imw_t_cpl_xml_master / 完了案件マスタXML
##### imw_t_cpl_xml_operation / 完了案件操作履歴XML
##### imw_t_cpl_xml_progress / 完了案件進捗XML
#### 管理グループ定義関連テーブル
##### imw_m_administration_group / 管理グループ
##### imw_m_administration_orgz / 管理グループ標準組織
##### imw_m_administration_plugin / 管理グループ権限プラグイン
##### imw_m_administration_target / 管理グループ管理対象
#### 集計情報関連テーブル
##### imw_t_alert / アラート
##### imw_t_monitoring_flow / フロー別モニタリング
##### imw_t_monitoring_matter / 案件処理状況別モニタリング
#### 代理管理者関連テーブル
##### imw_m_act_administration / 代理管理者設定
#### 代理設定関連テーブル
##### imw_t_act / 代理設定
##### imw_t_act_temporary_expand / 代理設定一時展開
#### 非同期処理関連テーブル
##### imw_t_async_proc_status / 非同期処理状況
#### 未完了案件関連テーブル
##### imw_t_actv_executable_user / 未完了案件タスク処理対象者
##### imw_t_actv_matter / 未完了案件
##### imw_t_actv_matter_attach_b / 未完了案件添付ファイルバイナリ
##### imw_t_actv_matter_attach_file / 未完了案件添付ファイル
##### imw_t_actv_matter_handle_user / 未完了案件案件操作権限者
##### imw_t_actv_matter_his / 未完了案件履歴
##### imw_t_actv_matter_his_detail / 未完了案件履歴詳細
##### imw_t_actv_matter_his_locale / 未完了案件履歴ロケール
##### imw_t_actv_matter_locale / 未完了案件案件ロケール
##### imw_t_actv_task / 未完了案件未完了タスク
##### imw_t_actv_user_orgz / 未完了案件タスク権限者組織
##### imw_t_actv_user_target / 未完了案件タスク処理対象者種別
##### imw_t_actv_xml_exe_user / 未完了案件権限者XML
##### imw_t_actv_xml_flow / 未完了案件フローXML
##### imw_t_actv_xml_history / 未完了案件履歴XML
##### imw_t_actv_xml_master / 未完了案件マスタXML
##### imw_t_actv_xml_operation / 未完了案件操作履歴XML
##### imw_t_actv_xml_progress / 未完了案件進捗XML
##### imw_t_before_task / 未完了案件前処理タスク
##### imw_t_confirm / 未完了案件確認処理履歴
##### imw_t_confirm_orgz / 未完了案件確認処理権限者組織
##### imw_t_confirm_user / 未完了案件確認処理権限者
##### imw_t_cpl_task / 未完了案件完了タスク
##### imw_t_cpl_task_stamp / 未完了案件印影情報
##### imw_t_cpl_task_user_target / 未完了案件完了タスク処理対象種別
##### imw_t_cpl_user / 未完了案件タスク完了ユーザ
#### 利用者ノード設定関連テーブル
##### imw_t_user_node_config / 利用者ノード設定
##### imw_t_user_node_config_detail / 利用者ノード設定詳細
##### imw_t_user_node_config_node / 利用者ノード設定ノード
### DBBridge
#### odbb_env
#### odbb_history_detail
#### odbb_history_header
#### odbb_report_data
#### odbb_report_search
## Reverse Lookup
### スマートフォン版へ、の削除
- 認可でモバイルフレームワーク⇒スマートフォンリダイレクタ、を外す。
  http://www.earthlink.co.jp/info/1758/
### アカウントロック回数の設定
- サイトマップ⇒テナント管理⇒テナント情報⇒アカウントロックで設定。
  https://www.intra-mart.jp/download/product/iap/operation/tenant_administrator_guide/texts/basic_guide/basic_guide_9.html
### 認可が消滅した場合などの対処
- システム管理者でログインした状態で、
  直接認可設定やジョブネット設定のURLに飛ぶことで、該当ページにアクセス可能。
  http://www.earthlink.co.jp/info/2994/
### WARファイル単位での起動・停止
- resin web-app-start imart / resin web-app-stop imart
  http://imfaq.intra-mart.jp/imqa/faq/print.asp?Option=&NodeID=&DispNodeID=&CID=&Text=&Field=&KW=&KWAnd=&Attrs=&Bind=&SearchID=&FAQID=413&baID=1&strKind=5
### IMマスタの変更内容がWorkflowに反映されない
- 「処理対象者標準プラグイン結果キャッシュ設定」のため。
  "WEB-INF/conf/im-workflow-system-config.xml"に設定がある。
- キャッシュ削除方法としてジョブが存在する。
  「処理対象者標準プラグイン結果キャッシュ削除」
- https://www.intra-mart.jp/document/library/iap/public/im_workflow/im_workflow_specification/texts/setting_guide/setting_list/system_unit/setting_guide_1.html#set-plugin
- https://www.intra-mart.jp/download/product/iap/im_workflow/im_workflow_troubleshooting/texts/troubleshooting/target_user2.html
- https://www.intra-mart.jp/document/library/iap/public/im_workflow/im_workflow_specification/texts/job_guide/job_guide_1.html
### ヘルスチェック画面
- availability_check/index.jsp、を利用する
- https://www.intra-mart.jp/download/product/iap/setup/iap_setup_guide/texts/appendix/health_check.html
## Memo
### トレーニング
#### 環境
##### サービス
###### Task Service
  - 全てのAPサーバ上で稼働
  - 非同期系のメッセージを実行する
###### Job Scheduler Service
  - 全てのAPサーバ上で稼働
  - Job(バッチ)を実行する。

###### Server Manager
  - 1APサーバ上のみで稼働

#### スクリプト開発
- スクリプト開発では、init関数がまず実行される。
- ファンクションコンテナから、プレゼンテーションページに値を受け渡す。

### jsspRpc
- 
   - https://api.intra-mart.jp/iap/apilist-jssp-tagdoc/doc/imart_tag_api/jsspRpc/index.html

## Link
### About
- [[http://www.intra-mart.jp/document/library/index.html][intra-mart Accell Platform - intra-mart Accel Series ドキュメントライブラリ]]
- [[http://www.intra-mart.jp/apidoc/][API Documentation - intra-mart]]

- [[http://www.intra-mart.jp/apidoc/iap/index.html][intra-mart Accel Platform API Documentation]]
- [[http://www.intra-mart.jp/apidoc/iap/javadoc/all-dev_apidocs/overview-summary.html][intra-mart Accel Platform API Specification]]

- [[http://www.intra-mart.jp/document/library/iap/public/im_workflow/im_workflow_table_definition.xls][IM-Workflowテーブル定義書(Excelファイル)]]

### Docsまとめ
- Accel Platform
  - [[http://www.intra-mart.jp/download/product/iap/iap_introduction/index.html][intra-mart Accel Platform イントロダクション]]
  - [[http://www.intra-mart.jp/download/product/iap/setup/iap_quick_setup_guide/index.html#][intra-mart Accel Platform クイック セットアップガイド]]
  - [[http://www.intra-mart.jp/download/product/iap/setup/iap_setup_guide/index.html][intra-mart Accel Platform セットアップガイド]]
  - [[http://www.intra-mart.jp/document/library/iap/public/first_step_guide/index.html][intra-mart Accel Platform ファーストステップガイド]]
  - [[http://www.intra-mart.jp/download/product/iap/setup/im_configuration_reference/index.html][intra-mart Accel Platform 設定ファイルリファレンス]]
  - [[http://www.intra-mart.jp/download/product/iap/operation/system_administrator_guide/index.html][intra-mart Accel Platform システム管理者操作ガイド]]
  - [[http://www.intra-mart.jp/download/product/iap/im_import_export/tenant_environment_setup_specification/index.html][intra-mart Accel Platform テナント環境セットアップ 仕様書]]
  - [[http://www.intra-mart.jp/download/product/iap/operation/tenant_administrator_guide/][intra-mart Accel Platform テナント管理者操作ガイド]]
- Job
  - [[http://www.intra-mart.jp/document/library/iap/public/job-jobnet_reference/index.html][intra-mart Accel Platform ジョブ・ジョブネット リファレンス]]
  - [[http://www.intra-mart.jp/document/library/iap/public/im_job_scheduler/im_job_scheduler_specification/index.html][intra-mart Accel Platform ジョブスケジューラ仕様書]]
- Import/Export
  - [[http://www.intra-mart.jp/document/library/iap/public/im_master/im_master_import_export_specification/index.html][intra-mart Accel Platform IM-共通マスタ インポート・エクスポート仕様書]]
  - [[http://www.intra-mart.jp/document/library/iap/public/im_import_export/im_authz_import_export_specification/index.html][intra-mart Accel Platform IM-Authz（認可）インポート・エクスポート仕様書]]
  - [[http://www.intra-mart.jp/document/library/iap/public/im_import_export/im_admin_account_import_export_specification/index.html][intra-mart Accel Platform アカウント インポート・エクスポート仕様書]]
  - [[http://www.intra-mart.jp/document/library/iap/public/im_import_export/im_admin_role_import_export_specification/index.html][intra-mart Accel Platform ロール インポート・エクスポート仕様書]]
  - [[http://www.intra-mart.jp/document/library/iap/public/im_job_scheduler/im_job_scheduler_import_export_specification/index.html][intra-mart Accel Platform ジョブ インポート・エクスポート仕様書]]
  - [[http://www.intra-mart.jp/document/library/iap/public/im_import_export/im_menu_import_export_specification/index.html][intra-mart Accel Platform メニュー インポート・エクスポート仕様書]]
- Log
  - [[https://www.intra-mart.jp/download/product/iap/im_core/im_log_specification/index.html][intra-mart Accel Platform ログ仕様書]]
- 認可
  - [[https://www.intra-mart.jp/document/library/iap/public/im_authz/im_authz_specification/index.html][intra-mart Accel Platform 認可仕様書]]
- IM-BIS
  - [[https://www.intra-mart.jp/document/library/bis/public/bis_specification/index.html][IM-BIS for Accel Platform IM-BIS 仕様書]]
  - [[http://www.intra-mart.jp/document/library/bis/public/bis_setup_guide/index.html][IM-BIS for Accel Platform セットアップガイド]]
  - [[http://www.intra-mart.jp/document/library/bis/public/bis_beginners_guide/][IM-BIS for Accel Platform IM-BIS ビギナーズガイド]]
  - [[http://www.intra-mart.jp/download/product/bis/manager_guide/index.html][IM-BIS for Accel Platform 業務管理者 操作ガイド]]
  - [[https://www.intra-mart.jp/document/library/bis/public/bis_administrator_guide/index.html][IM-BIS for Accel Platform システム管理者 操作ガイド]]
- Design
  - [[https://www.intra-mart.jp/document/library/iap/public/im_ui/im_design_guideline_pc/index.html][intra-mart Accel Platform UIデザインガイドライン（PC版）]]
- 開発
  - [[http://www.intra-mart.jp/document/library/iap/public/development/script_programming_guide/index.html][intra-mart Accel Platform スクリプト開発モデル プログラミングガイド]]
  - [[http://www.intra-mart.jp/document/library/iap/public/development/sastruts_s2jdbc_programming_guide/index.html][intra-mart Accel Platform SAStruts+S2JDBC プログラミングガイド]]
  - [[http://www.intra-mart.jp/document/library/iap/public/development/tgfw_programming_guide/index.html][intra-mart Accel Platform TERASOLUNA Server Framework for Java (5.x) プログラミングガイド]]
  - [[http://www.intra-mart.jp/document/library/iap/public/development/usermodule_developers_guide/index.html][intra-mart Accel Platform ユーザモジュール開発ガイド]]
- ポータル・ポートレット
  - [[https://www.intra-mart.jp/download/product/iap/im_portal/im_portal_administrator_guide/index.html][intra-mart Accel Platform ポータル 管理者操作ガイド]]
  - [[https://www.intra-mart.jp/download/product/iap/im_portal/im_portlet_programming_guide/index.html][intra-mart Accel Platform ポートレット プログラミングガイド]]
- その他
  - [[http://www.intra-mart.jp/document/library/iap/public/im_import_export/im_language_additional_guide/index.html][intra-mart Accel Platform 言語追加ガイド]]

- IM-FormaDesigner
  - [[http://www.intra-mart.jp/document/library/forma/public/forma_setup_guide/index.html][IM-FormaDesigner for Accel Platform セットアップガイド]]
- IM-Workflow
  - [[http://www.intra-mart.jp/document/library/iap/public/im_workflow/im_workflow_administrator_guide/index.html][intra-mart Accel Platform IM-Workflow 管理者操作ガイド]]
  - [[http://www.intra-mart.jp/download/product/iap/im_workflow/im_workflow_user_guide/index.html][intra-mart Accel Platform IM-Workflow ユーザ操作ガイド]]
  - [[http://www.intra-mart.jp/document/library/iap/public/im_workflow/im_workflow_specification/][intra-mart Accel Platform IM-Workflow 仕様書]]
  - [[http://www.intra-mart.jp/document/library/iap/public/im_workflow/im_workflow_programming_guide/][intra-mart Accel Platform IM-Workflow プログラミングガイド]]
- Accel Documents
  - [[http://www.intra-mart.jp/download/product/iad/im_acceldocuments_setup_guide/index.html][intra-mart Accel Documents セットアップガイド]]
  - [[http://www.intra-mart.jp/download/product/iad/im_acceldocuments_user_guide/][intra-mart Accel Documents ユーザ操作ガイド]]
  - [[http://www.intra-mart.jp/download/product/iad/im_acceldocuments_repository_api_programming_guide/index.html][intra-mart Accel Documents プログラミングガイド]]
- View Creator
  - [[https://www.intra-mart.jp/document/library/iap/public/viewcreator/viewcreator_administrator_guide/index.html][intra-mart Accel Platform ViewCreator 管理者操作ガイド]]
  - [[https://www.intra-mart.jp/document/library/iap/public/viewcreator/viewcreator_user_guide/index.html][intra-mart Accel Platform ViewCreator ユーザ操作ガイド]]
  - [[https://www.intra-mart.jp/document/library/iap/public/im_workflow/im_workflow_viewcreator_guide/index.html][intra-mart Accel Platform ViewCreator for IM-Workflow 連携ガイド]]
    
- e Builder
  - [[http://www.intra-mart.jp/document/library/ebuilder/public/e_builder_setup_guide/texts/all_in_one/index.html][intra-mart e Builder for Accel Platform セットアップガイド]]
  - [[http://www.intra-mart.jp/document/library/ebuilder/public/e_builder_user_guide/index.html][intra-mart e Builder for Accel Platform アプリケーション開発ガイド]]
  - [[http://accel-archives.intra-mart.jp/2014-winter/document/ebuilder/public/e_builder_user_guide/index.html][intra-mart e Builder for Accel Platform / ユーザ操作ガイド]]
### 要件
- [[https://issue.intra-mart.jp/][intra-mart 要件情報公開サイト]]
### その他
- http://final.hateblo.jp/entry/2016/04/29/175815
