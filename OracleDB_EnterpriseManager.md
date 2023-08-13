# Oracle Enterprise Manager
## Kind
### Database Control
- 
  Webベースのインターフェース。
  インストール、データベースを作成（アップグレード）してネットワークを構成すると使用可能に。
  1つのデータベースに対して1つ用意されるdbconsoleプロセスが管理を行う。

### Cloud Control
- OracleおよびOracle以外のテクノロジを実行するシステムを含むITインフラストラクチャ全体に対し、
  集中化された監視機能、管理機能およびライフ・サイクル管理機能を提供するシステム管理ソフトウェア。
  Grid Controlの後継製品。
  
#### Components

##### Oracle Management Agent
- 管理エージェント
  組み込まれたソフトウェア・コンポーネントで、Enterprise Managerシステムで管理対象外ホストを管理対処ホストに変換する。
  プラグインと連携することにより、管理対象ホスト上で実行されているターゲットを監視する。

##### Oracle Management Service
- OMC
  管理エージェントおよびプラグインと連携し、ターゲットを検出して、その監視及び管理を行い、
  将来の分析のために収集した情報をリポジトリ内に格納するWebベースのアプリケーション。
  
##### Oracle Management Repository
- 管理リポジトリ
  管理リポジトリは、管理エージェントが収集したすべての情報が保存される場所。
  
##### Plugins
##### Console
### Grid Control
-
#### Components
##### Oracle Management Agent
- 管理エージェント
##### Oracle Management Service
- OMS
##### Oracle Management Repository
- 管理リポジトリ
##### Console

## Operations
### Commands
#### emca
##### 
#### emctl
##### OMS
###### emctl start oms
- -admin_only
- -bip_only
###### emctl stop oms
- -all
- -force
- -bip_only
###### emctl secure oms
- OMSのSSL構成を設定する
##### 管理Agent
- 
###### emctl {start | stop} dbconsole
###### emctl {status | secure | setpasswd} dbconsole
###### emctl config dbconsole -heap_size <size_value> -max_perm_size <size_value>
###### emctl {start | stop} agent
###### emctl status agent
###### emctl resetTZ agent
- タイムゾーンのリセット
###### emctl getemhome
- ランタイムディレクトリの確認。
  ログ及びトレースファイルは以下に存在。
  <EMHOME>/sysman/log
##### セキュリティ
###### セキュリティ
###### セキュリティ診断
###### EMキー
##### HAConfig
##### Resync
##### コネクタ
##### パッチ・リポジトリ
##### Partool
##### プラグイン
### Files
#### 管理エージェントのログ・トレース
- emagent.log / Oracle Management Agent ログ・ファイル
- emagent.trc / Oracle Management Agent トレース・ファイル
- emagent.nohup / Oracle Management Agent 起動ログ・ファイル
#### tmp
##### bin
##### sysman
###### config
####### emd.properties
###### emd
####### agntstmp.txt
####### lastupid.xml
####### upload
###### log
### Access
#### URL
- https://<hostname(localhost)>:<port(1158)>/em
- "$ORACLE_HOME/host_sid/sysman/config/emd.properties"の"REOSITORY_URL"にポート番号の記載あり。
#### User
- sys/(password)でアクセス
### Functions/Screen
#### 11?
##### Database(local?)
###### Home
###### Performance
###### Availability
####### Backup/Recovery
######## Setup
######### Backup Settings
######### Recovery Settings
########## Instance Recovery
########## Media Recovery
########## Fast Recovery
######### Recovery Catalog Settings
######## Manage
######### Schedule Backup
######### Manage Current Backups
######### Backup Reports
######### Manage Restore Points
######### Perform Recovery
######### View and Manage Transactionsx
######## Oracle Secure Backup
######### Assign and Manage
###### Server
####### Storage
######## Control Files
######## Tablespaces
######## Temporary Tablespace Groups
######## Datafiles
######## Rollback Segmetns
######## Redo Log Groups
######## Archive Logs
######## Migrate to ASM
######## Make Tablespace Locally Managed
####### Database Configuration
######## Memory Advisors
- メモリ管理、割り当て状況の確認
######## Automatic Undo Management
######## Initialization Parameters
- 初期パラメータ
######## View Database Feature Usage
####### Oracle Scheduler
######## Jobs
######## Chains
######## Schedules
######## Programs
######## Job Classes
######## Windows
######## Window Groups
######## Global Attributes
######## Automated Maintenance Tasks
####### Statistics Management
######## Automatic Workload Repository
######## AWR Baselines
####### Resource Manager
######## Getting Started
######## Consumer Groups
######## Consumer Group Mappings
######## Plans
######## Settings
######## Statistics
######## Parallel Statement Queue
####### Security
######## Users
- ユーザ
######## Roles
######## Profiles
######## Audit Settings
######## Transparent Data Encryption
######## Virtual Private Database
######## Applcation Contexts
######## Enterprise User Security
####### Query Optimizer
####### Change Database
####### Enterprise Manager Administration
###### Schema
####### Database Objects
####### Programs
####### Materialized Views
####### Change Management
####### Data Making
####### User Defined Types
####### XML Database
####### Workspace Manager
####### Text Manager
###### Data Movement
####### Move Row Data
######## Export to Export Files
######## Import from Export Files
######## Import from Database
######## Load Data from User Files
######## Monitor Export and Import Jobs
####### Move Database Files
######## Clone Database
######## Trasport Tablespaces
####### Streams
######## Setup
######## Manage Replication
######## Manage Advanced Queues
####### Advanced Replication
######## Setup
######## Manage
###### Software and Support
####### Configuration
####### Database Software Patching
####### Real Application Testing
####### Deployment Procedure Manager
####### Support
##### Main(OEM 10g)
###### Home
###### Target
####### Host
######## (each host)
######### Home
######### Performance
######### Management
######### Target
######### 構成
####### Database
- データベース・インスタンス、クラスタ・データベースなどの情報が表示される
####### Middleware
####### Web Application
####### Service
####### System / システム
####### Group / グループ
####### All Targets / すべてのターゲット
- インスタンス等の選択
######## Type別
######### Claster
########## ホーム
########## パフォーマンス
########## ターゲット
########## インターコネクト
########## トポロジ
######### Claster Database / クラスタ・データベース
########## ホーム
########### 一般
########### ホストCPU
########### アクティブセッション
########### 診断サマリー
########### 領域サマリー
########### 高可用性
########## パフォーマンス
########### クラスタ・ホストのロード平均
########### グローバル・キャッシュ・ブロックのアクセス待機時間
########### 平均アクティブセッション
########### タグ
############ スループット
############ I/O
############ パラレル実行
############ サービス
############ インスタンス
########### その他の監視リンク
########### その他のインスタンス監視リンク
########## 可用性
########## サーバー
########## スキーマ
########### データベース・オブジェクト
########### プログラム
########### マテリアライズド・ビュー
########### ユーザー定義タイプ
########### XMLデータベース
########### Workspace Manager
########### Text Manager
########## データ移動
########## ソフトウェアとサポート
########## その他（リンク先等）
########### トップ・アクティビティ
- 過去1時間のアクティブなセッション数を、待機イベントクラス（待機状態の分類）毎に集計したグラフから構成されている。
############ 自ページ
############# トップ・アクティビティ
############## SQLの詳細
############### Self(SQLの詳細)
################ テキスト
################ 詳細
################# 統計
################# アクティビティ
################# プラン
################# 計画管理
################# チューニング履歴
################# SQL監視
############# 選択した5分間隔の詳細
############## 上位SQL
############### SQLチューニング・アドバイザのスケジュール
############### SQLチューニング・セットの作成
############## 右（上位～）
############### 上位セッション
############### 上位サービス
############### 上位モジュール
############### 上位アクション
############### 上位クライアント
############### 上位ファイル
############### 上位オブジェクト
############### 上位PL/SQL
############# その他のリンク
############ インスタンスごとのアクティブセッション
######### Database Instance / データベース・インスタンス
########## ホーム
########### Current
############ 一般
############ ホストCPU
############ アクティブ・セッション
############ SQLレスポンス時間
############ 診断サマリー
############ 領域サマリー
############ 高可用性
############ アラート
############ 関連アラート
############ ジョブアクティビティ
############ 関連リンク
############# すべてのメトリック
########## パフォーマンス
########### その他の監視リンク
############ SQLの検索
########## 可用性
########## 待機中アクティブ・セッション
########## サーバー
########## スキーマ
########## データ移動
########## ソフトウェアとサポート
########## その他
########### すべてのメトリック
############ Current
############# SQLレスポンス時間
############## ベースラインSQLレスポンス時間
############## 現行のSQLレスポンス時間
############## SQLレスポンス時間(%)
############### Current
################ 統計
################ メトリック値
################ アラート履歴
################ 関連リンク
################# ベースラインSQL
################# メトリックとポリシー設定
############### メトリック・アラート:SQLレスポンス時間(%)
########### SQLレスポンス時間の最新の収集
########### メトリックとポリシー設定
############ メトリックしきい値
############ ポリシー
######### Host
######### Agent
######### Listener
########## ホーム
########## パフォーマンス
########## データベース・サービス
###### Deploy
####### General
####### Provisioning
###### Alert
####### Stopped target
####### Critical
####### Warning
####### Error
####### Blackout
####### Unknown availability
###### Compliance
####### Policy
####### Policy group
####### Security list
###### Job
###### Report
##### Setup
##### Preferences
##### Help
##### Logout
#### Cloud Control 12c
##### データベース/インスタンス
###### パフォーマンス
####### トップ・アクティビティ
####### ASH分析
####### SQLモニタリング
####### SLQ
####### AWR
###### 可用性
###### セキュリティ
###### スキーマ
####### ユーザー
####### データベース・オブジェクト
####### プログラム
####### マテリアライズド・ビュー
###### 管理 / メンテナンス
####### 初期化パラメータ
####### 記憶域
######## 制御ファイル
######## データファイル
######## 表領域
######## ローカル管理表領域の作成
######## 一時表領域グループ
######## ロールバック・セグメント
######## セグメント・アドバイザ
######## 自動UNDO管理
######## REDOログ・グループ
######## アーカイブ・ログ
####### Oracle Scheduler
######## ホーム
######## ジョブ
######## ジョブ・クラス
######## チェーン
######## ...
####### レプリケーション
####### ASMに移行
##### Enterprise
###### サマリー
###### モニタリング
###### ジョブ
###### レポート
###### 構成
###### コンプライアンス
###### プロビジョニングとパッチ適用
###### クオリティ管理
###### My Oracle Support
##### ターゲット
###### グループ
###### システム
###### サービス
###### ホスト
###### データベース
- 1レベル上の"データベース"を参照。
###### ミドルウェア
##### お気に入り
##### 履歴
##### 設定
## Manual
### Cloud Control管理者ガイド
- [[https://docs.oracle.com/cd/E26854_01/doc.121/b65081/toc.htm][Oracle® Enterprise Manager Cloud Control管理者ガイド 12c リリース5 (12.1.0.5)]]
#### 第Ⅰ部
##### 1
##### 2 ターゲットの検出、昇格および追加
##### 3 インシデント管理の使用
#### 第Ⅱ部
### インストレーション・ガイド
- [[https://docs.oracle.com/cd/E26854_01/install.12105/b65084/toc.htm][Oracle® Enterprise Manager Cloud Control基本インストレーション・ガイド 12cリリース5 (12.1.0.5)]]
#### 第Ⅰ部 概要
##### 1 概要
###### 1.1 概要
###### 1.2 アーキテクチャ
- コンポーネント
  - Oracle Management Agent / 管理エージェント
  - Oracle Management Service / OMS
  - Oracle Management Repository / 管理リポジトリ
  - プログイン
  - Enterprise Manager Cloud Controlのコンソール
#### 第Ⅱ部 インストール前の要件
##### 2 ハードウェア要件
###### 2.1
###### 2.2
###### 2.3
##### 3 パッケージ、カーネル・パラメータ、ライブラリ要件
##### 4 OS、ユーザの作成
##### 5 Cygwin、SSHデーモン
#### 第Ⅲ部 インストール
##### 6 システムのインストール
###### 6.1 インストールの概要
####### 6.1.1 インストールタイプの概要
- 単純構成または詳細構成
- 簡易インストール、拡張インストール
##### 7 Agentのインストール
##### 8 Serviceの追加
##### 9 Application Dependency and Performanceのインストール
##### 10 JVM Diagnosticsのインストール
#### 第Ⅳ部 Cloud Controlの設定および使用
#### 第Ⅴ部 付録
## Glossary
### Blackout
- メンテナンス等のために、監視を計画停止できる。
## Memo
### (tmp)SQL Worksheet
- Related Links(画面下部)からリンクで移動できる。
### IP/hostnameの変更時
- アクセスできなくなるので、各種構築が必要。
### ERROR: NMO not setuid-root (Unix-only)が表示された場合
- $ORACLE_HOME/root.shを実行すると実行できた。
### Performance
#### Kind
##### Top Activity / トップアクティビティ
###### アクセス手順
- 11g
  ホーム、パフォーマンス、その他の監視リンクでトップ・アクティビティ
##### Avarage Active Sessions / 平均アクティブ・セッション
- データベースの負荷の平均。
##### Top Working SQL / 上位SQL
- アクティビティ(%)
- SQLハッシュ値
- SQLタイプ
- サービス
- インスタンス
##### Top Sessions / 上位セッション
- アクティビティ(%)
- セッションID
- ユーザー名
- プログラム
- サービス
#### その他有用なデータ
- トップアクティビティの時系列グラフ（パフォーマンス中のリンクより）
- 実行計画表示（SQLの詳細->プラン）
- スループット、I/Oの時系列グラフ（パフォーマンス画面下部）
- メモリアドバイザのアドバイザ画面
#### Link
- http://www.oracle.com/technetwork/jp/database/articles/pickup/index-1598196-ja.html
### Internal Server Error
## Link
- [[http://www.oracle.com/technetwork/jp/oem/enterprise-manager/documentation/index.html][Oracle Enterprise Manager ドキュメント - ORACLE]]
- [[https://docs.oracle.com/cd/E26854_01/doc.121/b65081/toc.htm][Oracle® Enterprise Manager Cloud Control管理者ガイド 12c リリース5 (12.1.0.5)]]
- [[https://docs.oracle.com/cd/E26854_01/install.12105/b65084/toc.htm][Oracle® Enterprise Manager Cloud Control基本インストレーション・ガイド 12cリリース5 (12.1.0.5)]]

- [[https://docs.oracle.com/cd/E17559_01/em.111/b61022/toc.htm][Oracle Enterprise Manager管理 11gリリース1（11.1.0.1）]]

- [[http://otndnld.oracle.co.jp/easy/oracle11gr1/windows/1st/][意外と簡単!? Oracle Database 11g Release 1]]
