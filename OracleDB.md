# Oracle Database
## About
- 
  オブジェクトおよびXML機能を使用するリレーショナルデータベース。

- 構成
  - ホストコンピュータ上のOracleソフトウェア
  - 物理ファイルの集合であるデータベース
  - Oracleインスタンス
    - バックグラウンド・プロセス
    - 共有メモリ―領域
  - サーバープロセス
  - Oracle Net / Oracle Netリスナー

## History/Version
### Oracle V2(1979)
- 
  トランザクションの概念はないが、SQLを使用できた。
  Version1が存在しないのは、洗練されたDBであることを印象付けるための営業戦略と言われる。

### Oracle version 3(1983)
### Oracle 4(1984)
### Oracle 5.0(1985)
### Oracle 6.0(1988)
### Oracle7 7.0(1992)
- 
  最終バージョンは7.3.4。
  パラレルクエリー、完全制約性、ストアドプロシージャ、データベーストリガ、
  テータベースリンク、レプリケーションなどがサポート。

### Oracle8 8.0(1997)
- 
  オブジェクト指向やマルチメディアに対応。
  パーティショニング機能とカラム型LOB(BLOB型、CLOB型)がサポート。
  ROWIDの仕様変更により大容量のデータをサポート。
  最終バージョンは8.1.7。
  

#### Oracle 8i(R8.1.5～)(1999)
- 
  Java仮想マシンなどを組み込む。
  iはinternetの略。

### Oracle 9i Database(2001)
- 
  RAC(Real Application Clusters)が目玉。
  最終バージョンは9.2.0.8。
  XMLの入出力など、400もの新しい特徴を有す。

### Oracle Database 10g(2003)
- 
  グリッド・コンピューティングを目指し、グリッド技術を応用。
  gはGridの略とされる。

### Oracle Database 11g(2007)
### Oracle Database 12c(2013)
- 
  cはCloudの略とされる。

## Architecture
- [[file:OracleDB_Architecture.org][OracleDB Architecture]]
## Setting
### files
#### parameter file
##### PFILE, SPFILE
- PFILE
  初期化パラメータファイル
  テキストファイル。設定内容を手動で変更可能。
  ALTER SYSTEMコマンドで変更した場合、起動中のインスタンスのみに変更が適用されるため、変更した値はインスタンス再起動により失われる。
- SPFILE
  サーバー・パラメータファイル
  バイナリファイル。alter sysetmコマンドで編集し、効果は永続する。9iから導入された。
##### initSID.ora
- 初期化パラメータファイル。PFILE
- 下記のコマンドで設定値を確認可能。
  SQL> show parameter
##### spfileSID.ora
- サーバー・パラメータファイル。SPFILE。
  select * from v$spparameterなどで確認が可能
##### Default path
- UNIX : $ORACLE_HOME/dbs/init$ORACLE_SID.ora
- Windows : ORACLE_HOME\database\initORCL.ora
##### 優先順
- 
  1. 起動時に指定したpfile (startup pfile='filename')
  2. spfileSID.ora
  3. spfile.ora
  4. initSID.ora
  5. init.ora

##### 確認方法
- show parameter spfile
  →spfileが使われていればpathが表示される。pfileの場合は表示されない。
- select count(*) from v$spparameter where value is not null;
  →pfileが使われていれば0件、spfileが使われていれば数件引っかかる。
- http://at-j.co.jp/blog/?p=5468
##### 作成方法
- pfileの作成
  - from Memory
    create pfile='/home/oracle/initdb01.ora' from memory;
  - from spfile
    create pfile='/home/oracle/initdb01.ora' from spfile;
- spfileの作成
  - from pfile
    create spfile from pfile = '$ORACLE_HOME/work/initdb01.ora';
- [[https://docs.oracle.com/cd/E16338_01/server.112/b56299/statements_6016.htm][CREATE SPFILE - Oracle® Database SQL言語リファレンス 11gリリース2]]
- [[http://it-memo.info/?p=1227][pfileとspfileを作成する方法　（spfileからとメモリから） - オラエーリックスマンの呟き]]
#### network(folder)
##### admin
###### sqlnet.ora
- プロファイル構成ファイル
###### listener.ora
- listenerの情報を記載する。
###### tnsnames.ora
- 接続識別子の情報を記載する。
#### oratab
- 自動起動するインスタンスの選択
- Location
  - Solaris以外
    /etc/oratab
    
- Format
  $ORACLE_SID:$ORACLE_HOME:[Y|N]
  最後の値が"Y"のものが自動起動する。
### sql script
#### rdbms/
##### admin/
###### データディクショナリの作成
####### catalog.sql
- データ・ディクショナリおよびその多数のビューに対するパブリック・シノニムを作成し、PUBLICアクセス権限を与える。
####### catproc.sql
- PL/SQLに必須のスクリプトまたはPL/SQLで使用するスクリプトをすべて実行する。
####### catclust.sql
###### その他のデータ・ディクショナリ構造体の作成
####### catblock.sql
- パフォーマンス管理・SYS
  ロック関連のグラフを動的に表示するビューを作成する。
###### NOスクリプト
####### catnoadt.sql
- オブジェクト型に関連するディクショナリ・メタデータのビューおよびシノニムを削除する。
####### catnoavd.sql
- 監査メタデータのビューおよびシノニムを削除する
####### catnohs.sql
- 異機種間サービス・ディクショナリ・メタデータを削除する
####### catnoprt.sql
- パーティション表および索引に関連するディクショナリ・メタデータのビューおよびシノニムを削除する。
####### catnosvm.sql
- Oracle7 Server Managerのビューおよびシノニムを削除する
####### catnsnmp.sql
- DBSNMPユーザーおよびSNMPAGENTロールを削除する
###### アップグレード・ダウングレード
###### JavaScript
###### AWR
####### awrrpt.sql
- AWRレポートの作成
###### パッチ適用
####### catbundleapply.sql
- Call catbundle.sql to apply the Patch Set Update (PSU)
#### sqlplus
##### admin
###### glogin.sql
- サイト・プロファイル設定ファイル。
  SQL*Plusを起動すると、最初に実行される。
  次にユーザー・プロファイル設定ファイルlogin.sqlが実行される。
###### login.sql
- ユーザー・プロファイル設定ファイル
  現行のディレクトリを検索し、環境変数SQLPATHで指定したディレクトリを検索してファイルを検出する。
  glogin.sqlファイルの設定よりも優先される。
###### plustrce.sql
- 
###### pupbld.sql
- PRODUCT_USER_PROFILE表を再作成する。
###### help
####### helpbld.sql
- 新しいヘルプ表の削除および作成。SYSTEMスキーマにコマンドライン・ヘルプを手動でインストールする。
  内部的にはhlpbld.sqlを呼ぶだけ。
####### helpdrop.sql
- コマンドライン・ヘルプの表を削除する。
####### helpus.sql
- ヘルプ・データへのヘルプ表の移入。hlpbldの引数に渡す。
####### hlpbld.sql
- ヘルプ表を作成する。helpusを引数に取って実行する。
### set
#### shmsys:~
- 
  shmから始まるものが共有メモリの設定
  
#### semsys:~
- 
  semから始まるものがセマフォの設定。

### variables
#### ORACLE_BASE
- 
  ex) /u01/app/oracle(UNIX)
#### ORACLE_HOME
- 必須項目
  インストールされているディレクトリを指定
  ex) ORACLE_BASE/product/11.2.0/db_1
#### ORACLE_SID
- 必須項目
  初期化パラメータのファイル名に、この関数で指定されている名前が含まれる
#### PATH
- 必須項目
  ex) $ORACLE_HOME
#### Link
- [[http://www.shift-the-oracle.com/config/oracle-environment-variable.html][NLS_LANG、ORACLE_HOME、ORACLE_SID などの設定 - SHIFT the Oracle]]
## Command
### bin/
#### emctl
- 
#### dbca
- 
  dbcaを起動する。

#### expdp
- Data Pump。
#### impdp
#### lsnrctr
- start
  デフォルトのリスナーを起動する
- status
- stop
- help
- reload
- save_config
- exit
#### orapwd
- パスワードファイルを作成する。
  
- Usage
  opapwd file=<fname> entries=<users> force=<y/n> ignorecase=<y/n> nosysdba=<y/n>
  - file : name of password file (required)
  - password : password for SYS will be prompted if not specified at command line
  - entries : maximum number of distinct DBA (optional)
  - force : whether to overwrite existing file (optional)
  - ignorecase : passwords are case-insensitive (optional)
  - nosysdba : whether to shut out the SSYDBA logon (optional Database Vault only)
#### rman
- Recovery Manager。データベースでバックアップおよびリカバリ・タスクを実行し、バックアップ計画の管理を自動化するOracle Databaseクライアントのこと。
#### sqlplus
- /nolog
  ログオンを行わずにsqlplusを起動

#### tnsping
- tns用のping。
### rdbms/
#### admin/
##### awrddrpt.sql
- 選択された2つの期間の詳細なパフォーマンス属性および構成設定を比較する、HTMLまたはテキストのレポートが生成される。
##### awrddrpi.sql
- 特定のデータベースおよびインスタンスにおける選択された2つの基幹の詳細なパフォーマンス属性および構成設定を比較する、HTMLまたはテキストのレポートが生成される。
##### awrrpt.sql
- 一定範囲のスナップショットIDの統計を表示する、HTMLまたはテキストのレポートが生成される。
##### awrrpti.sql
- 指定されたデータベースおよびインスタンスの一定範囲のスナップショットIDの統計を表示する、HTMLまたはテキストのレポートが生成される。
##### awrsqlpi.sql
- 指定されたデータベース及びインスタンスにおける一定範囲のスナップショットIDに対する特定のSQL文の統計を表示する、HTMLまたはテキストのレポートが生成される。
##### awrsqrpt.sql
- 一定範囲のスナップショットIDに対する特定のSQL文の統計を表示する、HTMLまたはテキストのレポートが生成される。
## SQL言語
- [[file:OracleDB_SQLLang.org][OracleDB_SQLLang.org]]
## PL/SQL
- [[file:OracleDB_PLSQL.org][OracleDB_PLSQL.org]]
## SQL*Plus
- [[file:OracleDB_SQLPlus.org][SQL*Plus.org]]
## Interface
### SQL*Plus
- SQLを実行するためのインターフェイスユーティリティ。
  アプリケーションから呼ぶことはほとんどなく、人手によるデータベースの管理をするために使う。
### JDBC
- Java Database Connectivity
### ODBC
- Java Database Connectivity
### OO4O
- Oracle Object For Ole
### Pro*C
- Oracle向けC言語コンパイラ。

## Manage
### ユーザ分類
#### データベース管理者
##### タスク
###### データベース・サーバ・ハードウェアの評価
###### Oracle Databaseソフトウェアのインストール
###### データベースの計画
###### データベースの作成とオープン
###### データベースのバックアップ
###### システムユーザの登録
###### データベース設計の実装
###### 実行データベースのバックアップ
###### データベースのパフォーマンス・チューニング
###### パッチのダウンロードとインストール
###### 追加ホストのロール・アウト
#### セキュリティ管理者
#### ネットワーク管理者
#### アプリケーション管理者
#### データベースユーザ
### 管理ロードマップ
#### インスタンスの起動
#### ネットワーク環境構成
#### 記憶域構造の核にｎ
#### メモリー管理
#### ユーザ管理
#### スキーマ・オブジェクトの管理
#### バックアップ・リカバリの実行
#### リカバリ設定の構成
#### データベースの監視およびチューニング
#### 問題の調査、報告、解決
#### ソフトウェアの管理
### SQLの発行
- SQL*Plus
- Oracle Enterprise Manager
- SQL Developer

## Performance
- [[file:OracleDB_Performance.org][OracleDB_Performance.org]]
## Security
### 事前定義ユーザ
#### 事前定義された管理アカウント
##### ANONYMOUS
- Oracle XML DBへおHTTPアクセスを許可するアカウント。
  EPG(Embedded PL/SQL Gateway)をデータベースにインストールするときに、APEX_PUBLIC_USERアカウントの代わりに使用される。
##### CTXSYS
- Oracle Textを管理するためのアカウント。
##### DBSNMP
- データベースの監視及び管理を行うためにOracle Enterprize ManagerのManagement Agentのコンポーネントによって使用されるアカウント。
##### EXFSYS
- Rules Manager機能およびExpression Filter機能と関連頭消されるEXFSYSスキーマにアクセスするために内部で使用されるアカウント。
  (どちらの機能も12cで終了)
##### LBACSYS
- Oracle Label Security(OLS)を管理するためのアカウント。Label Securityオプションをインストールするときのみ作成される。
##### MDSYS
- Oracle SpatialおよびOracle Multimedia Locator管理者アカウント。
##### MGMT_VIEW
- Oracle Enterprise Manager Database Controlで使用されるアカウント。
  
##### OLAPSYS
- OLAPカタログ(CWMLite)を所有するアカウント。非推奨だが下位互換のために保持されている。
##### ORDDATA
- Oracle Multimedia DICOMのデータモデルが含まれている。
##### OWBSYS
##### ORDPLUGINS
- Oracle Multimediaユーザ。Oracleおよびサード・パーティに提供されたプラグインはこのスキーマにインストールされている。
##### ORDSYS
- Oracle Multimedia管理者アカウント。
##### OUTLN
##### SI_INFORMTN_SCHEMA
- SQL/MM Still Image Standard向けの情報ビューを保持しているアカウント。
  
##### SYS
- データベース管理タスクの実行に使用されるアカウント。
##### SYSMAN
- Oracle Enterprise Managerデータベースの管理タスクの実行に使用するアカウント。
  SYSおよびSYSTEMでもこれらのタスクを実行できる。
##### SYSTEM
- Oracle Databaseのデフォルトの汎用データベース管理者アカウント。
  本番環境ではSYSTEMを使用せず、個々のデータベース管理者アカウントを作成するべき。
##### WK_TEST
##### WKSYS
##### WKPROXY
##### WMSYS
- Oracle Workspace Managerのメタデータ情報の格納に使用されるアカウント。
##### XDB
- Oracle XML DBデータおよびメタデータの保存に使用されるアカウント。
#### 事前定義された非管理アカウント
##### APEX_PUBLIC_USER
- Oracle Database Application Expressのアカウント。
  データベース・アクセス記述子(DAD)でデータベースに接続するために使用するOracleのスキーマの指定に使用する。
##### DIP
- 
  Oracle Directory Integration and Provisioning(DIP)のアカウント。
  
##### FLOWS_040100
##### FLOWS_FILES
##### MDDATA
##### ORACLE_OCM
- Oracle Configuration Managerと使用するアカウント。
  現在のインスタンスの構成情報をMy Oracle Supportと関連付けることができる。
##### SPATIAL_CSW_ADMIN_USR
##### SPATIAL_WFS_ADMIN_USR
##### XS$NULL
- セッション内にユーザーが存在しないことを表す内部アカウント。
  ユーザーでないため、Oracle Databaseインスタンスによってのみアクセスできる。権限はない。
#### 事前定義されたサンプル・スキーマ・ユーザアカウント
##### BI
- サンプルスキーマに含まれるBI(Business Intelligence)スキーマを所有するアカウント。
##### HR
- HR(Human Resources)スキーマを管理するためのアカウント。
  企業の従業員や施設に関する情報。
##### OE
- OE(Order Entry)スキーマを管理するためのアカウント。
  製品のインベントリや様々なチャネルによる製品の売り上げ
##### PM
- PM(Product Media)スキーマを管理するためのアカウント。
  企業が販売した各製品の説明と詳細情報
##### IX
- IX(Information Exchange)スキーマを管理するためのアカウント。
  B2Bアプrケーションを介した発送を管理
##### SH
- SH(Sales)スキーマを管理するためのアカウント。
  ビジネス上の決断を容易にするビジネス戦略を格納
#### その他
##### APPQOSSYS
- Oracle Quality of Service Managementで必要なすべてのデータおよびメタデータの格納および管理に使用される。
  
##### TSMSYS
- 透過的なセッション移行(Transparent Session Migration: TSM)に使用されるアカウント。
##### PERFSTAT
- Oracle Statspackに関するユーザ。
#### 旧資料参照
##### DMSYS
- データマイニングアカウント。
  10gまでは存在したが、11gには存在せず、代わりにSYSを使うこととなる。
  [[http://docs.oracle.com/cd/E18283_01/datamine.112/e16807/upgrade_odm.htm][6 Upgrading Oracle Data Mining - Oracle® Data Mining Administrator's Guide 11g Release 2 (11.2)]]

#### Link
- [[https://docs.oracle.com/cd/E16338_01/server.112/b56296/tdpsg_user_accounts.htm#BABGEGFI][Oracle Databaseから提供される事前定義されるユーザー・アカウント - Oracle® Database 2日でセキュリティ・ガイド 11g リリース2(11.2)]]

## Installation
### Class
#### Desktop Class
- ラップトップコンピュータ用。
#### Server Class
- 拡張構成オプションにアクセスする必要がある場合、このクラスを選択する。
### Install Type
#### Enterprise Edition
- 完全な機能。
  ミッションクリティカル、OLTP、データウェアハウス環境。
#### Standard Edition
- ワークグループや部門レベル、もしくは中小企業用。
#### Standard One Edition
- ワークグループ、部門、もしくはWebアプリケーションに最適。
#### Personal Edition
- Windowsのみ。
  Enterprise Editionと同様のソフトウェアだが、シングル環境のユーザ開発環境とデプロイメントkン今日のみサポート。
### 拡張インストール
#### 製品の言語
- ソフトウェアで使用する言語
#### データベース構成タイプ
- 以下のいずれかを選択可能。
  - 汎用目的/トランザクション処理
  - データ・ウェアハウス
#### データベース構成オプション
#### データベース管理オプション
- Oracle Enterprise Managerを使用して、集中管理するかローカル管理するかを指定する。
  - 集中管理
    複数のターゲットを単一のインターフェースで管理できる。
    各ホスト・各コンピュータにOracle Enterprise Management Agentを1つずつ配置する必要がある。
  - ローカル管理
#### リカバリ・オプション
#### スキーマ・パスワード
#### オペレーティング・システム・グループ

### DB作成
#### CREATE DATABASE
##### 1.インスタンス識別子(SID)の指定
##### 2.必要な環境変数が設定されていることの確認
##### 3.認証方式の選択
##### 4.初期化パラメータファイルの作成
##### 5.(Windows)インスタンスの作成
##### 6.インスタンスへの接続
##### 7.サーバー・パラメータ・ファイルの作成
##### 8.インスタンスの起動
##### 9.CREATE DATABASE文の発酵
##### 10.追加の表領域の作成
##### 11.スクリプトの実行によるデータ・ディクショナリ・ビューの作成
### Silent install
#### Link
- [[https://docs.oracle.com/cd/E16338_01/install.112/b56273/app_nonint.htm#BABFEECI][A レスポンス・ファイルを使用したOracle Databaseのインストールおよび構成 - Oracle® Databaseインストレーション・ガイド 11gリリース2 (11.2) for Linux]]
- [[http://www.lovebug.jp/index.php?Oracle%2F11g%2F%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%AB%EF%BC%88%E3%83%AC%E3%82%B9%E3%83%9D%E3%83%B3%E3%82%B9%E3%83%95%E3%82%A1%E3%82%A4%E3%83%AB%E3%82%92%E5%88%A9%E7%94%A8%E3%81%97%E3%81%9FCUI%E3%81%A7%E3%81%AE%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%AB%EF%BC%89][Oracle 11g Release 2のインストール（レスポンスファイルを利用したCUIでのインストール）]]
### Install Log
#### 2016/6/11 11c
- http://docs.oracle.com/cd/E16338_01/install.112/b56277/toc.htm
  
- 6 カーネルパラメータの値が結構違う。とりあえずスルーします。
  /etc/sysctl.confを編集する、とのこと。
  ⇒結局10で怒られたので編集した。

- 7 DISPLAYの設定をして、xhostが利用できるようにしたが、
  今回は色々変更した後で、別に変更しなければ接続できたことに気付いた。
  ⇒oracleでxhost localhost、でOK?
  ⇒違う。rootでxhost local:userを設定。
  oracleユーザでDISPLAYを規定値":0.0"に戻した後、runinstallerを実行。

- 10 
  - emailは入力せず。クリティカルイッシューでメールよこさんぞ、と言われる。
  - Skip software updateとしてしまう。
  - Createする
  - Server Classを選択
  - RACにしようとしたら怒られる。Singleに。
  - Typical Installを行う。
  - 詳細
    - Oracle base : /oracle/app/oracle
    - Software location : /oracle/app/oracle/product/11.2.0/dbhome_1
    - Storage Type : File System
      - Database file location : /oracle/app/oracle/oradata
    - Database edition : Enterprise Edition
    - OSDBA Group : dba
    - Global database name : orcl.localdomain
    - Password : yasutake
  - Inventory
    - Directory : /home/oracle/app/oraInventory
    - Group : oinstall
  - Prerequisite Check
    - Passせず。
      - Phisical Memory
      - OS Kernel Parameters
        - semmsl
        - semmns
        - semmni
        - shmmni
        - ip_local_port_range
      - Package
        - elfutils-libelf-devel-0.97
        - gcc-c++-3.4.5(x86_64)
        - libstdc++-devel-3.4.6(x86_64)
        - pdksh-5.2.14
    - 以下についてIgnore
      - Checks
        - Hard Limit maximum open file descriptors : 65536 -> 4096
        - Hard Limit maximum user processes : 16384 -> 5110
        - Soft Limit maximum user processes : 2047 -> 1024
        - Package : pdksh-5.2.14
  - rootで以下を実行しろ、とのこと。
    - /home/oracle/app/oracInventory/orainstRoot.sh
    - /home/oracle/app/oracle/product/11.2.0/dbhome_1/root.sh
  - current home is not registered in the central inventory on this system. OK? -> Yes
#### 2016/6/14
- パスが/home/oracleになっていたため再作成。
  - デフォルトのユーザはSYSTEM、だった。
##### DBCA
- General
- test.local_domain
- local management
- すべて自分のユーザ(SYS, SYSTEM, DBSNMP, SYSMAN)
## Backup/Recovery
### Glossary
#### Backup
##### Logical Backup 論理バックアップ
##### Physical Backup 物理バックアップ
#### Resotre リストア
- 
#### Recovery リカバリ
- アーカイブログ、REDOログを用いて状態を復元すること
### Memo
#### リカバリ
##### 完全リカバリ
- 障害が発生した直前までリカバリする方法。
- バックアップ、アーカイブログ、REDOログファイルを使い障害が発生した時点の状態に戻す。
  コミットデータは失われない。
###### 手順(RMAN上)
- 
  sql "ALTER TABLESPACE 表領域名 offline immediate";
  RESTORE TABLESPACE 表領域名;
  RECOVER TABLESPACE 表領域名;
  sql "ALTER TABLESPACE 表領域名 online";

##### 不完全リカバリ
- 特定の時点までリカバリする方法。
  アーカイブログを適用できる限りの時点までリカバリが可能。
- 過去の特定の状態に戻すこと全体を「Point In Time Recovery (PITR)」と呼ぶ。

###### 手順
- 
  1. データベースの停止
  2. データベースをマウント
  3. どの時点に復旧したいか決める
  4. RMANコマンドを実行する
- コマンドの実行が完了したら、RESETLOGSオプションでデータベースをオープンする。
## Tools
### Automatic Workload Repository(AWR)
#### 概要
- 自動ワークロード・リポジトリ
  Oracle Databaseの稼働状況とワークロード情報のスナップショットを自動的に収集/管理する。
  AWRの情報は、MMONによってSGAから直接、定期的(11gのデフォルトは60分毎)に取得され、データベース内に一定期間(11gのデフォルトは8に置換)保存される。
- 10gより提供された、Statspackを進化させたもの。
  Statspackの取得データに加えて、稼働統計やワークロード情報のスナップショットなど実際の使用履歴そのものを動的に取得している。
- StatspackはDB作成時にインストールが必要だったが、AWRはSYSAUX表領域にデフォルトでインストールされている。

#### 収集レベル
- STATISTICS_LEVEL 初期化パラメータで設定する。
  デフォルトはTYPICAL。より低いBASIC、より高いALLへの設定変更も可能。
  TYPICALはStatspcakのi_snap_level7相当。
#### レポート
- 任意の2時点のスナップショットに基づき、統計をレポート形式で出力したもの。
  利用にはOracle Diagnostics Packが必要(有償)。
- レポート作成
  - EM
    EM上でGUI操作による作成が可能。
  - コマンドライン
    SYSTEMユーザやSSYDBA権限ユーザで"awrrpt.sql"を実行することで作成可能。
#### Snapshot
##### 生成
- exec dbms_workload_repository.create_snapshot();
##### 削除
- exec dbms_workload_repository.drop_snapshot();
##### 設定変更
- exec dbms_workload_repository.modify_snapshot_settings(...);
##### 確認
- select * from dba_hist_snapshot;
#### Baseline
- パフォーマンス上の問題が発生したときに比較するために保持された特定の基幹のパフォーマンスデータが含まれる。
- 自動AWR消去プロセス対象からは除去され、無期限に保存される。
#### Memo
##### しばちょう先生
###### 第39回 AWRレポートを読むステップ1
- [[http://www.oracle.com/technetwork/jp/database/articles/shibacho/index-2547807-ja.html][しばちょう先生の試して納得！DBAへの道 第39回 AWRレポートを読むステップ1.バッファキャッシュ関連の待機イベントと統計情報]]

- まず確認すべき項目
  - Top, 最上段
    - HW増強の確認
      - Release - バージョン情報
      - RAC - RACか否か
      - CPUs, Cores, Sockets - CPUコア数
      - Memory(GB) - 物理メモリ容量
        - Report SummaryのCache SizesでSGAの設定を合わせて見る
    - Elapsed - レポートの期間、比較する他のAWRレポートの期間が異なる場合特に意識する必要あり。
  - Report Summary
    - Load Profile
      - どのようなWorkloadが流れているのかを理解するのにこのセクションが大事。
        このセクションは大事、すべて見る。
      - Redo size : Per Second - 秒間のRedo生成量。
        1MB/secだと更新が少ない、5-10MB/secはふつう、20MB/secで少し多い、40MB/secで多い。
    - Instance Efficency Precentage (Target 100%)
      - Buffer Hit % - ミスしたIOPSをディスクが捌けるか、が重要。%以外にI/O回数が重要。
    - Cache Sizes
###### 第40回 AWRレポートを読むステップ2
- [[http://www.oracle.com/technetwork/jp/database/articles/shibacho/index-2613471-ja.html][しばちょう先生の試して納得！DBAへの道 第40回 AWRレポートを読むステップ2：アクセス数が多い表領域とセグメント]]
###### 第51回 AWRレポートを読むステップ3
- [[http://www.oracle.com/technetwork/jp/database/articles/shibacho/index-3655144-ja.html][しばちょう先生の試して納得！DBAへの道 第51回 AWRレポートを読むステップ3: オンライン・トランザクションのスループット低下の原因特定]]
###### 第52回 AWRレポートを読むステップ4
- [[http://www.oracle.com/technetwork/jp/database/articles/shibacho/index-3682060-ja.html][しばちょう先生の試して納得！DBAへの道 第52回 AWRレポートを読むステップ4: 特定時間帯に発生する性能劣化の原因特定]]
#### Link
- tmp
  - http://docs.oracle.com/cd/E16338_01/server.112/b56312/autostat.htm#i27008
  - http://oracle-pub.wikidot.com/ocm-11g-awr
  - [[http://www.oracle.com/technetwork/jp/ondemand/database/db-new/120517-consultant-shinzui-part2-1641035-ja.pdf][オラクルコンサルタントが語る性能分析の真髄 Part2 - Oracle]]
  
### Automatic Database Diagnostic Monitor(ADDM)
- 自動データベース診断モニター
  ある程度のパフォーマンス分析を自動的に実施し、その分析結果をレポートとして提供する機能。

### Automatic Diagnostic Repository(ADR)
- Automatic Diagnostic Repository 自動診断レポジトリ
  ログファイルなどのデータベースの状況管理や診断に使用するデータを一括で管理する。11gより。
  ログファイルを含むすべての診断データを「ADR_BASE」と呼ばれる単一のディレクトリの配下に補完する。
  ADR_BASEとADR_HOMEの場所は「V$DIAG_INFO」ビューで確認できる。
- 
  [[http://www.atmarkit.co.jp/ait/articles/0808/08/news143.html][11gからの新管理機構「ADR」を理解しよう (1/4) - @IT]]
  [[http://cosol.jp/tech/detail/d3_adr_automatic_diagnostic_repository.shtml][Oracle Database 11gから導入されたADR ( 自動診断リポジトリ ) - 株式会社こーそる]]
#### ADRCI
- https://docs.oracle.com/cd/E60665_01/db112/SUTIL/adrci.htm
##### Command Reference
###### CREATE REPORT
###### ECHO
###### EXIT
###### HOST
###### IPS
###### PURGE
- 現在の削除ポリシーに従って、カレントADRホーム内の診断データを削除する。
####### フラグ
######## -i {id1 | start_id end_id}
######## -age mins
######## -type {ALERT | INCIDENT | TRACE | CDUMP | HM}
###### QUIT
###### RUN
###### SELECT
###### SET BASE
###### SET CONTROL
- 削除ポリシー属性を含む、ADRの各種属性を示す。
####### 削除ポリシー属性
######## SHORTP_POLICY
- 残存期間の短いADRの内容が削除可能になるまでの時間数。デフォルトは720(30日)。
  0を設定すると、全ての残存期間の短い内容を削除できる。
######## LONGP_PLICY
- 残存期間の長いADRの内容が削除可能になるまでの時間数。デフォルトは8760(365日)。
  0を設定すると、全ての内容を削除できる。
###### SET ECHO
###### SET EDITOR
###### SET HOMEPATH
###### SET TERMOUT
###### SHOW ALERT
###### SHOW BASE
###### SHOW CONTROL
###### SHOW HM RUN
###### SHOW HOMEPATH
###### SHOW HOMES
###### SHOW INCDIR
###### SHOW INCIDENT
###### SHOW PROBLEM
###### SHOW REPORT
###### SHOW TRACEFILE
###### SPOOL
### Database Upgrade Assistant
- 既存のDBを新しいリリースのDBへアップグレードする際に使うツール
### Net Configuration Assistant (NetCA)
- リスナーとネーミング・メソッドを構成する場合に使用するユーティリティ。
### Oracle Application Express
- Oracle APEX
  Oracle DatabaseのためのWebアプリケーション開発ツール。
  
### Oracle Automatic Storage Management(ASM)
- Oracleデータベース・ファイルのボリューム・マネージャ兼ファイルシステム。
- データベースファイルの配置とネーミングを自動的に管理する。
  多数のディスクを持つ環境では、管理が簡単になり、パフォーマンスが向上する。
- ファイル・レベルでソフトウェアのストライプ化とミラー化を行う。
  
- [[https://docs.oracle.com/cd/E16338_01/server.112/b61035/toc.htm][Oracle® Automatic Storage Management管理者ガイド 11gリリース2 (11.2)]]

#### Memo
##### [[http://output-place.blogspot.com/2013/07/oracle-asm.html][Oracle ASMの概念を簡単にまとめてみた - OUTPUT PLACE]]
- ASMの役割を三行で言ってしまうと
  1. 複数のストレージを一つのボリュームとして扱い、ディスクへのI/Oを分散する
  2. オンラインでのディスク追加を可能にする
  3. 冗長構成を実現する
##### [[http://www.nkjmkzk.net/?p=1018][今さらですが、「ASMとは？」をあらためて。 - nkjmkzk.net]]
- サーバ側にインストールするソフトウェアで、下記のことが可能になります。
  - 複数ストレージを連結して一つの大きなボリュームを構築する
  - 複数ストレージ間でデータを冗長化し、ストレージ装置の障害時にも完全なデータアクセスを可能にする
  - 需要に応じてオンラインでストレージを追加／削除できる
  - 追加・削除を行った際、ドライブ上のデータは新しい構成に応じて自動的に再配置される
  - 複数クライアントからのアクセスを同時に処理できる（つまり共有ボリュームとして利用できる）
  - ASMが提供するボリュームはデータベースの他、ファイルシステムでフォーマットしたりと汎用的に利用できる

- 現在ASMはDatabaseではなく「Grid Infrastructure」というパッケージに含まれるソフトウェアとなっており、Databaseとは独立してインストールして使用可能です。
- Grid Infrastructureはそれ自体にライセンス費用はかかりません。

### Oracle Configuration Manager
- クライアントの構成情報の収集と、この情報のOracleリポジトリへのアップロードに使用される。
### Oracle Data Mining(ODM)
- Oracleデータベースにデータ・マイニング機能を組み込む。
  
### Oracle Data Pump
#### About
- 
  10gより導入された。
  従来のエクスポート/インポート(exp/impコマンド)と目的は同じく論理バックアップの取得で、データベース間のデータ移動を可能とする。
  従来のexp/impは基本的にユーティリティ側で処理されるが、Data Pumpはデータベースサーバー側でジョブとして管理・処理され、
  「パフォーマンス向上」と「管理性の向上」が得られる。

#### Architecture
- 
  1) コマンドライン・クライアント expdp/impdp
  2) PL/SQLパッケージ DBMS_DATAPUMP (Data Pump API)
  3) PL/SQLパッケージ DBMS_METADATA (メタデータAPI)

#### 利用例
- 
  - 事前準備
    - Directoryの作成
      create or replace directory TEST_DIR as '/home/test';
    - Directoryの権限付与
      grant read, write on directory TEST_DIR to SCOTT;
  - EXPDP
    ex) expdp scott/tiger directory=test_dir tables=emp
  - IMPDP
    ex) impdp scott/tiger directory=test_dir dumpfile=exp.dmp tables=emp
        impdp scott/tiger directory=test_dir dumpfile=exp.dmp sqlfile=ddl.sql

#### Options
##### MODE
###### FULL 全体エクスポート・モード
- FULL=Yでデータベース全体を指定
###### SCHEMAS スキーマ・モード
- スキーマ名を指定
###### TABLESPACES 表領域モード
- 表領域名を指定
###### TABLES 表モード
- テーブル名を指定
###### TRANSPORT トランスポータブル表領域モード
##### FILTER
###### Data filter
- 
  Use "QUERY" or "SAMPLE" parameter.

###### Metadata filter
- 
  Use "EXCLUDE" or "INCLUDE" parameter.

##### Export
###### ESTIMATE_ONLY
- ESTIMATE_ONLY=yで、領域の見積もりのみ実施
##### Import
###### SQLFILE
- SQL DDLの書き込み先ファイルを指定する。import。
##### Both
###### CONTENT
- CONTENT=data_only
  表のデータのみ
- CONTENT=metadata_only
  表の定義のみ
- CONTENT=all(default)
  表のデータと定義の両方
###### DUMPFILE
- ダンプファイル名を指定する。デフォルトは"EXPDAT.DMP"
###### EXCLUDE
- default : null
  一部のオブジェクトを除く。

- object_type
  以下で有効な値を確認可能。
  - 全体モード : DATABASE_EXPORT_OBJECTS
  - スキーマモード : SCHEMA_EXPORT_OBJECTS
  - 表および表領域モード : TABLE_EXPORT_OBJECTS
  
###### INCLUDE
- default : 
###### LOGFILE
- ログファイル名を指定する。デフォルトは"export.log","import.log"
###### NOLOGFILE
- NOLOGFILE=yでログファイルの出力を行わない
#### Memo
##### 特殊文字の利用
- 'や"、()などを利用する際、シェル側で展開されてしまうので、バックスラッシュによるエスケープを行う必要がある。
#### Link
- 
  [[http://otndnld.oracle.co.jp/products/database/oracle11g/pdf/datapump11g2007_quickstart.pdf][Oracle Data Pump クイック・スタート - Oracle ホワイト・ペーパー]]
  [[https://blogs.oracle.com/oracle4engineer/entry/data_pumpexpdpimpdp][Data Pump(expdp/impdp)の使い方～エクスポート／インポート、データ移動、論理バックアップ - オラクルエンジニア通信]]
  [[http://docs.oracle.com/cd/E16338_01/server.112/b56303/part_dp.htm][Oracle Data Pump - Oracle® Databaseユーティリティ 11gリリース2 (11.2)]]
### Oracle Database Configuration Assistant(DBCA)
- テンプレートからデータベースを作成したり、独自のデータベースを作成するユーティリティ。
#### Create a Database / データベース作成
##### 起動
- shellより"dbca" ($ORACLE_HOME/bin)
##### Templates
- General, Data Warehouseなどから選択
- Template
  - General Purpose or Transaction Processing
  - Custom Database
  - Data Warehouse
##### Identification
- Global Database Nameを指定
##### Management Option
- Enterprise Managerで管理するか否か設定する。
  - Agentが存在する場合は"Register with Grid Control ~"にチェック
  - ローカルで管理する場合"Configure Database Control ~"にチェック
##### Credentials
- パスワードなどを指定する
##### File Locations
###### Storage Type
- File System
- ASM
###### Storage Locations
- テンプレートに設定されているディレクトリ情報を利用
- すべてデータベースファイルに対して共通の位置。指定が必要。
- Oracle Managed Files
  すべてのファイルに対して、「データベース領域」と呼ばれるデフォルトの場所を指定する。
  このオプションを選択すると、データベースファイルの管理を
##### Recovery Configuration
###### Specify Fast Recovery Area
- バックアップおよびリカバリ領域とそのディレクトリ位置・サイズを指定。
###### Enable Archiving
- アーカイブ有効化
##### Database Content
- Sample Schemas / サンプルスキーマ
- Custom Scripts / カスタムスクリプト
##### Initialization Parameters / 初期化パラメータ
###### Memory
- Typical / 標準
- Custom / カスタム
###### Sizing
- Block Size
- Processes / プロセス数
###### Character Sets
- Database Character Set
  - Default
  - Use Unicode
    - AL32UTF8は、Oracleで使用しているUTF-8エンコードの名前。
  - Choose from list
- National Character Set / 各国語キャラクタ・セット
  NVARCHAR2やNCHAR、NCLOBのデータ格納に使われるキャラクタっセット。
  基本はデフォルトのAL16UTF16を使用する。
- Default Language
- Default Territory
###### Connection Mode
- Dedicated Server Mode 専用サーバー・モード
  各ユーザ・プロセスで専用のサーバ・プロセスが使用できる。
  クライアント総数が50以下など、少ないと予想される場合にこのオプションを指定する。
- Shared Server Mode 共用サーバー・モード
  リソース・プールを複数のクライアント接続で共有できる。
##### Storage
- 記憶域構造が表示される。
##### Creation Options
- Create Database
  この時点でデータベースを作成する場合に選択
- Save as a database Template
  後で使用するテンプレートとしてDBの定義を保存する
- Generate atabase Creation Scripts
  後で実行可能なSQLデータベース作成スクリプトを生成する
#### Configure Database Options / DB構成変更
##### Database Content
##### Connection Mode
#### Delete a Database / DB削除
#### Manage Templates / テンプレート管理
##### タイプ
###### シード
- 
  拡張子：.dbc
  既存のデータベース（シード・データベース）の構造および物理データファイルの両方が含まれる。
  
###### 非シード
- .dbt
### Oracle Database Quality of Service Management
- Oracle Database QoS Management
  システム全体のワークロード・リクエストを監視する自動化されたポリシーベースの製品。
  アプリケーション間で共有されるリソースを監視し、システム構成を調整して、アプリケーションの実行をビジネスに必要なパフォーマンス・レベルに維持する。
### Oracle Directory Integration and Provisioning Server
- Oracle DIP
  
### Oracle Enterprise Manager(OEM)
- [[file:OracleDB_EnterpriseManager.org][OracleDB EnterpriseManager]]
### Oracle Expression Filter
- RUL
  Expression FilterとObject Relationalの機能を使用して、特殊な目的のルールエンジンの機能を提供する。
  12cでサポートが終了。
### Oracle Identity Management
- 
  アプリケーションとディレクトリ(サード・パーティのLDAPディレクトリを含む)をOracle Internet Directoryに統合して、管理作業にかかる時間とコストを削減できる。

### Oracle Internet Directory
- Oracleコンポーネントとサード・パーティのアプリケーションによって、ユーザIDおよび資格情報が格納され、アクセスされるリポジトリ。
### Oracle Label Security
- 
  データベース表に対して行レベルのセキュリティを提供する。
  データ行は、個々の行にラベルを付けることで保護される。
  ニーズに応じて行を様々なセキュリティ・レベルに割り当てることができる。

#### Components
##### Label
###### Level
###### Compartment
###### Group
##### Policy
### Oracle Locator
- Oracle Spatialで使用可能な主要な機能およびサービスを提供する。
  通常、インターネットおよびワイヤレス・サービス・ベースのアプリケーションおよびパートナ・ベースのGISソリューションをサポートする貯めに必要な、重要な機能を提供する。
### Oracle Multimedia
- イメージ、オーディオ、ビデオまたは疎オン他の異機種間メディアデータを、他の企業情報と統合したフォーマットで格納、管理および検索する機能。
### Oracle Multimedia DICOM
- Digital Imaging and Communications in Medicine(DICOM)は医用画像の標準規格。
  
### Oracle Net Services
#### 制御ユーティリティ
##### リスナー
##### Oracle Connection Manager
#### 構成パラメータ
##### 全体
##### sqlnet.ora
###### プロファイル・パラメータ
####### NAMES.DIRECTORY_PATH
- クライアントの名前解決に使用するネーミング・メソッドの順序を指定する。
- Default
  NAMES.DIRECTORY_PATH=(tnsnames, ldap, ezconnect)
- Value
  - tnsnames(ローカル・ネーミング・メソッド)
    クライアントのtnsnames.oraファイルによりネットサービス名を解決する場合に設定する
  - ldap(ディレクトリ・ネーミング・メソッド)
    データベース・サービス名、ネットサービス名またはネット・サービス別名をディレクトリ・サーバーにより解決する場合に設定する。
  - ezconnectまたはhostname(簡易接続ネーミング・メソッド)
    ホスト名、オプションのポートおよびサービス名で構成されるTCP/IP接続識別子をクライアントで使用できるようにする場合に選択する。
  - nis(外部ネーミング・メソッド)
    既存のNetwork Information Serviceでサービス情報を解決する場合に設定する。
###### ADR診断パラメータ
###### ADR以外の診断パラメータ
##### tnsnames.ora (ローカル・ネーミング)
###### 接続記述子
####### DESCRIPTION_LIST
####### DESCRIPTION
###### プロトコル・アドレス・セクション
####### ADDRESS_LIST
####### ADDRESS
###### アドレス・リストのオプション・パラメータ
####### ENABLE
######## About
- DESCRIPTIONパラメータの下に埋め込むことで、サポートされているTCP転送のキープアライブ機能をネット・サービス・クライアントに対して有効にできる。
######## Value
- BROKEN
######## Example
- 
  net_service_name
   (DESCRIPTION=
    (ENABLE=broken)
    (ADDRESS=(PROTOCOL=tcp)(HOST=sales1-svr)(PORT=1521))
    (ADDRESS=(PROTOCOL=tcp)(HOST=sales2-svr)(PORT=1521)))
    (CONNECT_DATA=(SERVICE_NAME=sales.us.example.com))
####### FAILOVER
####### LOAD_BALANCE
####### RECV_BUF_SIZE
####### SDU
####### SEND_BUF_SIZE
####### SOURCE_ROUTE
####### TYPE_OF_SERVICE
###### 接続データ・セクション
####### CONNECT_DATA
####### FAILOVER_MODE
####### GLOBAL_NAME
####### HS
####### INSTANCE_NAME
####### RDB_DATABASE
####### SERVER
####### SERVICE_NAME
###### セキュリティ・セクション
####### SECURITY
####### SSL_SERVER_CERT_DN
###### タイムアウト・パラメータ
####### CONNECT_TIMEOUT
####### RETRY_COUNT
####### TRANSPORT_CONNECT_TIMEOUT
##### listener.ora (Oracle Net Listener)
##### cman.ora (Oracle Connection Manager)
##### ldap.ora (ディレクトリ使用)
#### Link
- [[https://docs.oracle.com/cd/E16338_01/network.112/b56287/toc.htm][Oracle® Database Net Servicesリファレンス 11gリリース2 (11.2)]]
- [[https://docs.oracle.com/cd/E16338_01/network.112/b56288/toc.htm][Oracle® Database Net Services管理者ガイド 11gリリース2 (11.2)]]
### Oracle Rules Manager
- EXF
  アプリケーション開発者が条件式をリレーショナル表の1つ以上の列に格納し、索引を付けて評価できるようにするRules Managerのコンポーネント。
  12cでサポートが終了。
### Oracle Spatial
- Oracleのファンクションとプロシージャを統合した製品で、空間データの格納、アクセスおよび分析を短時間で効率的に処理することを目的としている。
### Oracle Statspack
- 
  パフォーマンス上の問題点を診断するツール。
  Oracle 8iから提供されている。
  10gでは自動ワークロードリポジトリ(AWR)が提供されたため、マニュアルから削除されているが、機能自体は存続している。
### Oracle Streams Advanced Queuing (AQ)
#### Link
- [[https://docs.oracle.com/cd/E16338_01/server.112/b61355/toc.htm][Oracle® Streamsアドバンスト・キューイング・ユーザーズ・ガイド - 11gリリース2 (11.2)]]
### Oracle SQL Developer
- GUIツール。
  $ORACLE_HOME/sqldeveloper中に、sqldeveloper.shがあるので起動。
  xが利用できる必要がある。
- 
  http://www.oracle.com/technetwork/jp/developer-tools/sql-developer/downloads/index.html

### Oracle Text
- 全文検索およびドキュメント分類のためのエンジン。
  検索対象の文書の「本文」そのものを検索対象とする。
- CTXSYSユーザの存在有無でOracle Textのインストール有無が確認可能。
  >select username from dba_users where username='CTXSYS';
#### Reference
- [[https://docs.oracle.com/cd/E16338_01/text.112/b61357/toc.htm][Oracle® Textリファレンス 11gリリース2(11.2)]]

##### Text索引付けの要素
###### データストア型
###### フィルタ型
###### レクサー型
###### ワードリスト型
###### 記憶域型
###### セクション・グループ型
###### 分類型
###### クラスタ型
###### ストップリスト
###### システム定義プリファレンス
####### データ記憶域
######## CTXSYS.DEFAULT_DATASTORE
######## CTXSYS.FILE_DATASTORE
######## CTXSYS.URL_DATASTORE
####### フィルタ
######## CTXSYS.NULL_FILTER
######## CTXSYS.AUTO_FILTER
####### レクサー
######## CTXSYS.DEFAULT_LEXER
######## CTXSYS.BASIC_LEXER
####### セクション・グループ
######## CTXSYS.NULL_SECTION_GROUP
######## CTXSYS.HTML_SECTION_GROUP
######## CTXSYS.AUTO_SECTION_GROUP
######## CTXSYS.PATH_SECTION_GROUP
####### ストップリスト
######## CTXSYS.DEFAULT_STOPLIST
######## CTXSYS.EMPTY_STOPLIST
####### 記憶域
######## CTXSYS.DEFAULT_STORAGE
####### ワードリスト
######## CTXSYS.DEFAULT_WORDLIST
##### CONTAINTS問合せ演算子
##### 問合せの特殊文字
##### パッケージ
###### CTX_ADM
###### CTX_CLS
###### CTX_DDL
###### CTX_DOC
###### CTX_OUTPUT
###### CTX_QUERY
###### CTQ_REPORT
###### CTX_THES
###### CTX_ULEXER
##### ユーティリティ
##### 代替スペル
### Oracle Universal Installer(OUI)
- Install用ユーティリティ
### Oracle Workspace Manager
- 作業領域を作成し、バージョンが異なる表の行の値を、異なる作業領域に簡単にグループ化できるインフラストラクチャを提供する。
  ユーザは、古いデータを保持しながら、更新するデータの新しいバージョンを作成することができる。
### Oracle XML DB
- XMLデータの格納、生成、アクセス、検索、検証、変換、拡張および索引付などの高パフォーマンスの処理に関連する一連のOracle Databaseテクノロジー。
  SQLとXMLの両方のデータ・モデルの相互運用を可能にすることで、ネイティブなXMLサポートを提供する。
### Recovery Manager / RMAN
- https://docs.oracle.com/cd/E16338_01/backup.112/b56269/toc.htm
#### Commands
##### BACKUP
- バックアップ実行
##### CONFIGURE
- 初期設定
##### CONNECT
##### EXIT
##### RECOVERY
- リカバリ
##### RESTORE
- リストア
##### RMAN
##### RUN
##### SHOW
- 設定表示
###### SHOW ALL
##### SPOOL
#### RMAN Sub Query
#### Recovery Catalog View
#### Link
- [[http://docs.oracle.com/cd/E16338_01/backup.112/b56270/toc.htm][Oracle® Databaseバックアップおよびリカバリ・リファレンス 11gリリース2(11.2)]]
### TKPROF
## Services
### dbconsole
## Error
### ORA-00942
- 該当の表またはビューが存在しない場合や、表やビューに対するアクセス権限が不足している場合に発生する。
### ORA-00972
- 識別子が長すぎる。
  列名、テーブル名は30文字までとのこと。
### ORA-01031
- 権限が不足している。
  ユーザの権限等を見直す必要がある。
### ORA-01659
- 十分な容量がありません。
### ORA-22868
- LOB列のセグメントがあるが、表セグメントは異なる表領域にある
  削除しようとした表領域には、表のLOB列のセグメントがあるが、表セグメントがない。
  表を削除してから、表領域の削除を再実行する必要がある。
### ORA-27101 : shared memory realm does not exist
- 共有にアクセス失敗した場合に発生する。
- 主な発生要因
  - インスタンスが起動していない
  - 環境変数が誤っている
## Reference
- [[file:OracleDB_Reference.org][OracleDB_Reference.org]]
## Glossary
### ASH
- Active Session History
  
### CRブロック
- Consistent Read Block、読み取り一貫性ブロック
  多くの場合、データ更新中のブロックに対して別ノードから参照要求があった場合に一部UNDOのデータ等を使用して作成されるブロック。
### DUAL表
- 
  1列しか存在しない特別な表。
  SYSDATEやUESRなど、表を適用せずとも値を返す演算に対してSELECTを行う場合に使われる。
  VARCHAR2(1)のDUMMYという列があり、レコード値は'X'となっている。

- 
  Oracle 10gでは、DUAL表そのものは存在しているものの、最適化により実際にはアクセスしないようになっている。

### データベース名
#### インスタンス関連
##### データベース識別子、DBID(Database Identifier)
- データベース内部の一意データ識別子。
- 確認方法
  SELECT DBID, NAME, DB_UNIQUE_NAME FROM V$DATABASE;
##### インスタンス識別子、システム識別子、SID(System Identifier)
- ホストサーバー内で有効で、ホストの共有メモリにアクセスするための識別子。
  ホスト外になるとSIDではアクセスできない。
  インスタンスを区別するために使用する一意の識別子。
##### インスタンス名、INSTANCE_NAME
- ホスト外部から、単一のインスタンスを識別するための名前。単独でユニークとは限らない。
  通常は個別に設定しないためSIDと同じ名前になっているが、SIDとINSTANCE_NAMEは役割が全く違う。
- 確認方法
  select instance_name from v$instance;
##### データベース名、DB_NAME
- DB_NAME初期化パラメータを表す。通常SIDと一致する。
  一致しない場合は起動しない。
- 確認方法
  show parameter db_name
###### ドメイン名
- 確認方法
  show parameter db_domain
##### グローバル・データベース名、GLOBAL_NAME
- DATABASE LINK作成に関係するパラメータ。
  GLOBAL_NAMES初期化パラメータと併用することでデータベースリンク名の補完が行われる。
  DB_NAME + DB_DOMAIN(database_name.database_domain)がデフォルト値。
  その他のデータベースと一意に識別されるデータベースの完全名。

##### SERVICE_NAME(S)、サービス名
- 1つのインスタンス、もしくは同じ機能を提供する複数インスタンスの集合体を特定する名称。
  インスタンス名とドメイン名を合わせた名前。
- 確認方法
  show parameter service_name
##### ネットサービス名、NET SERVICE NAME、TNSサービス名、接続識別子
- SERVICE_NAMEに繋ぐためのNet Service上での名前。
### SCN
- System Change Number
  システム変更番号
- 現在のSCMを確認する : select bdms_flashback.get_system_change_number from dual;
  
### Schema スキーマ
- 
  データの論理構造の集合。
  1ユーザは1スキーマを必ず所有し、デフォルトで自動的にユーザ名と同じスキーマ名が割り当てられる。
  ユーザなしのスキーマ、スキーマなしのユーザは作成できない。
  
### SYNONYM シノニム
### TNS
- Transparent Network Substrate
  データベースの接続や複数ノード間のメッセージのやり取りを単一の共通インターフェースで提供している技術。
  Oracle Net Foundationレイヤーに組み込まれている。
  
### Database Access Descriptor
- データベースアクセス記述子
  
### DIRECTORY ディレクトリ
- 
  コンピュータの物理的なディレクトリをSQLやPL/SQLに直接指定することがないように、Oracle城で別名を付けて管理する。
  物理ディレクトリを変更したくなった場合に、SQLやPL/SQLを変更しなくても済む。
  [[http://q.hatena.ne.jp/1093325780][Oracleのディレクトリオブジェクトは何のために存在していますか。どのようなときにどう使うと便利なのですか？ - 人力検索はてな]]

### 引用識別子/非引用識別子
- 
  非引用識別子は大/小文字が区別されず、すべて大文字として解析される。
  引用識別子は大/小文字が区別される。
  [[http://otndnld.oracle.co.jp/document/products/oracle11g/111/doc_dvd/server.111/E05750-03/sql_elements.htm#57456][スキーマオブジェクト名および修飾子 - Oracle Database SQL言語リファレンス 11g リリース1（11.1）]]
### RAC
- Oracle Real Application Clusters

### PSR, CPU, PSU, PSE
- PSR, Patch Set Release
  安定したパッチセットで、重要度の高いバグをフィックス可能。PSUやCPU適用の前提条件であることも多い。
- CPU, Critical Patch Update
  四半期ごとに提供される、セキュリティ修正を中心とした重要な修正の集積体。
- PSU, Patch Set Update
  CPUの修正を含み、かつ適用が推奨される重要な修正を含んだ集積パッチ。CPUと同様四半期ごとに提供される。
- PSE, Patch Set Exception
  別名個別パッチ。
  一つの不具合に対する修正パッチ。リリースタイミングは不定期。
  
### RMAN
- Recovery Managerのこと。Toolも参照
### PROFILE
- データベース・リソースの制限の集合。
  
### 自動化メンテナンス・タスク、AUTOTASK
- データベースのメンテナンス操作を実行するために、一定の間隔をおいて自動的に開始されるタスク。
  問い合わせオプティマイザのスキーマ・オブジェクトに関する統計を収集するタスクなどはその一例。
  
- 3種類の自動化メンテナンス・タスクが事前定義されている。
  - 自動オプティマイザ統計収集
  - 自動セグメント・アドバイザ
  - 自動SQLチューニング・アドバイザ
#### メンテナンス・ウィンドウ
- 自動化メンテナンス・タスクが実行される連続した時間間隔。
  MAINTENANCE_WINDOW_GROUPという名前のウィンドウ・グループに属するOracle Scheduleウィンドウ。
### コンポジット変数
- 
  コレクションとレコードという、2種類のコンポジット変数がある。
  - コレクション
    常に同じデータ型であり、"要素"と呼ばれる。
  - レコード
    データ型が異なる場合があり、"フィールド"と呼ばれる
### 行連鎖・行移行
- 無駄なブロックI/Oが多くなりパフォーマンスに影響する。
  [[http://www.insight-tec.com/mailmagazine/ora3/vol440.html][行移行・行連鎖に関する検証 その１ - InsightTechnology]]
#### 行移行
- 1つのデータ・ブロックに収まっていた行が更新されて、行全体の長さが増加したが、更新後の行を保持する十分な空き容量がない場合、
  行全体が新しいブロックに収まることを前提として、行全体が新しいデータ・ブロックに移動される。
  移行された行の元の行断片には、行の移行先の新しいブロックへのポインタまたは「転送先アドレス」が含まれる。そのためROWIDは変わらない。
#### 行連鎖
- 最初に行を挿入するとき、大きすぎて1つのデータ・ブロック内に収まらない場合、
  その行のデータは、セグメント用に確保された1つ以上のデータ・ブロックの連鎖に格納される。
### Flashback Query
- 誤って変更したデータをもとに戻す場合などに、UNDOデータを参照してデータを復活させることができる。
  http://output-place.blogspot.jp/2013/09/oracle.html
### Snapshot
- 現在"Materialized View"と呼ばれているものの、昔の呼び方。
  
### Restore/Recovery リストア/リカバリ
- Restore
  取得しておいたバックアップから、データを物理的に復元すること
- Recovery
  リストアしたデータに対して、その後の変更内容を反映させ最新の状態に復旧すること
### gc
- Global Cacheのこと。
### PARSE
#### SOFT PARSE
- パーサによってパースされる。
  次にパースされた文が、共有プールにすでにキャッシュされているかどうかをチェックする。
  共有プールにキャッシュされている場合、すぐにそのSQL文を実行できる。この流れをSOFT PARSEという。
#### HARD PARSE
- 共有プールにキャッシュがなかった場合、ハードパースが行われる。
  オプティマイザが利用されるのはハードパースの場合のみ。
  オプティマイザのアウトプットとして「問合せ実行計画(QEP:QueryExecutionPlan)」が作成される。
  その結果をソースジェネレータが受け取り、必要なデータ構造を生成する。
### Latch ラッチ
- SGAのメモリー構造を保護するためにOracleで使用される下位レベルの内部ブロック。
  サーバープロセスやバックグラウンドプロセスは、メモリー情報が変更されないように、非常に短い時間ラッチを獲得する。
  目的はロックと同じだが、ユーザーに見せるのがロック、ユーザーに見せないのがラッチ。
### Inventry インベントリ
- インストール用の領域。
  $ORACLE_HOMEに犬sトールされているソフトウェア情報、JREなどそれ以外のOracle製品情報などが含まれる。
  UNIX/Linuxではインストール時に指定。
  WindowsではC:\Program Files\Oracle\Inventory。
  %ORACLE_HOME\Inventory、というわけではないので注意。
  推奨インストール先は、$Oracle_base/../oraInventory。
## Memo
### 他システムとの違い
#### 空文字/Null
- 
  可変長文字列において空文字列とNULLを区別しない。
  （正確には空文字列がNULLとして扱われる）

#### 比較演算子
- 
  通常の演算子として認識されず、WHERE句の中でしか利用できない

#### FROM句
- 
  表を必要としないSQLでも、必ず何らかの表を参照するFROM句を書かなければならない。

#### マルチバイト文字
- 
  テーブル名や列名、その別名にマルチバイト文字を使用する場合必ず""で囲む必要がある。
  困難なため、実際には英数字および記号（_ $ #）のみを使用することが推奨される。
### インスタンス
- 
  Oracleでは、管理の単位として「インスタンス」という用語を用いる。
  意味は「バックグラウンドプロセス群＋共有メモリ」のこと。
  データベースを管理しているもの、というイメージであり、データベースそのものではない。
  通常インスタンスとデータベースは1:1で対応するが、RACを使用している場合は異なる。
### インスタンスリカバリ
- 
  abrotオプションでshutdownした場合には変更済みデータを書き込まず終了するが、
  REDOログファイルのデータを使用して、データを復旧させる。
  この作業を「インスタンスリカバリ」という。
  この作業は、起動時にOracleが勝手に行う。
  Oracleが異常終了した場合もインスタンスリカバリが行われる。
  ただし、キャッシュ上の変更済みデータが失われただけでなく、データファイルが存在しないなどのファイルに関する障害がある場合は、
  本格的な復旧作業が必要。
  
### rlwrap - sqlplusでヒストリ利用
- 
  "readline-devel"を入れて、rlwrapというツールを使ってwrapする。
  rlwrap_extを利用すれば補完も可能。
- 
  [[http://utopia.knoware.nl/~hlub/uck/rlwrap/][rlwrap]]
  [[http://d.hatena.ne.jp/yohei-a/20101021/1287677679][sqlplus で bash みたいにヒストリを呼び出したりできたらいいな - ablog]]
  [[http://www.intellilink.co.jp/article/column/oracle-yam05.html][第5回 SQL*Plusを使いやすくする - NTTデータ]]

### 実行スクリプトファイルを指定してSQL*Plusを起動
- 
  スペースを入れて、@xxx.sqlを指定する。
  スペースを入れない場合はネットサービス名となる。
  ex) sqlplus rivus/rivus_pass@orcl_net @go.sql
- 
  [[http://www.shift-the-oracle.com/sqlplus/tutorial/sqlplus-script.html][SQL*Plus を実行スクリプトファイルを指定して起動する - SHIFT the Oracle]]

### 結果の出力行数を抑制する
- 
  rownum擬似列を利用する。
  where rownum = 1とすると、1行のみ出力できる。行頭を見たい場合に利用している。
  where rownum < 11など、使い道
  
### 明示カーソルと暗黙カーソル、カーソルFOR LOOP
- [[http://www.shift-the-oracle.com/plsql/cursor-loop.html][明示カーソルと暗黙カーソル - SHIFT the Oracle]]
- [[http://www.istudy.ne.jp/training/serial/plsql/010.html][第10回 「カーソルFORループ文」 - PL/SQLを使ってみよう！ iStudy]]

### ProcedureとFunctionの違い
- 
  戻り値(RETURN句)の有無。
  ファンクションはプロシージャと異なり、SELECT expr FROM..のような形で含められる。

### デフォルトパスワード
- 
  SYS : CHANGE_ON_INSTALL
  SYSTEM : MANAGER

- 
  [[http://otndnld.oracle.co.jp/document/products/oracle11g/111/doc_dvd/server.111/E05760-03/dba.htm#403635][DBAのセキュリティと権限の概要 - Oracle Database 管理者ガイド 11gリリース1（11.1）]]

### Insert文の生成
- 
  DESCRIBEはsqlplusの文なので、pl/sqlから呼ぶことができないが、
  dba_tab_columnsなどに列情報が入っているので、その内容を元にクエリを構成可能。
### SQL実行計画・統計情報を取得するための準備(PLUSTRACEなど)
- PLUSTRACEロールの作成
  @$ORACLE_HOME/sqlplus/admin/plustrace.sql
- 実行ユーザの割り当て
  GRANT PLUSTRACE TO (USER)
- 
  [[http://www.sql-dbtips.com/performance-tuning/plustrace/][SQL実行計画・統計情報を取得するための準備 - Oracle使いのネタ帳]]

### Listerの接続関係
- 
  リスナーは、同一リスナーで複数SIDを設定できるし、逆に複数リスナーで一つのSIDを見るように設定することも可能。
  ポートとインスタンスを接続するために存在するのみ、比較的それぞれ自由で疎結合。
### 自動メンテナンスタスク
- 機能
  - 自動オプティマイザ機能
  - 自動セグメント・アドバイザ
  - 自動SQLチューニング・アドバイザ
### フラッシュバッククエリ
- 間違えて変更したものをUNDOデータから復活できる。
  http://output-place.blogspot.jp/2013/09/oracle.html
### トレースの取得
#### ALTER SESSION
#### ログオントリガー
#### ALTER SYSTEM
#### DBMS_MONITOR
- [[https://www.ashisuto.co.jp/db_blog/article/20160630_sqltrace.html][SQLトレースの取得方法まとめ（ケース別） - アシスト Database Support Blog]]
### Flashback Technology
- http://docs.oracle.com/cd/E16338_01/appdev.112/b56259/adfns_flashback.htm

#### About
#### Type
##### アプリケーション開発機能
###### Oracle Flashback Query
###### Oracle Flashback Version Query
###### Oracle Flashback Transaction Query
###### DBMS_FLASHBACKパッケージ
###### フラッシュバック・トランザクション
###### フラッシュバック・データ・アーカイブ(Oracle Total Recall)
##### データベース管理機能
###### Oracle Flashback Table
###### Orcale Flashback Drop
###### Oracle Flashback Database
#### Settings
### 外部表
- 外部のファイルを、あたかもテーブルが存在するかのようにアクセスすることができる。
  
- 
  - http://www.shift-the-oracle.com/table/external-table-practice.html
  - http://otn.oracle.co.jp/otn_pl/otn_tool/code_detail?n_code_id=203
  - http://d.hatena.ne.jp/replication/20130408/1366426828
### パラレル実行
#### 種類
- パラレル問い合わせ
- パラレルDML
- パラレルDLL
#### 動作条件
- PARALLEL句（テーブルの属性、索引の属性など）の指定
- PARALLELヒントを指定している場合
- ALTER SESSION FORCE PARALEL分で強制的にパラレル化することも可能
  ※DMLはデフォルトでDISABLE
  - ALTER SESSION {ENABLE|DISABLE|FORCE} PARALLEL {DML|DDL|QUERY} [PARALLEL <パラレル度>];
#### 動作
- パラレル・スレーブ・プロセス(PQプロセス)を使用して最大2セット(2つの処理)までを同時に行う。
- PQプロセスの最大起動数
  - 初期化パラメータ「PARALLEL_MAX_SERVERS」で設定
    初期値は「CPU_COUNT * PARALLEL_THREADS_PER_CPU * 10」
##### アクター
###### QS クエリー・スレーブ
- 処理を行うプロセス
###### TQ テーブル・キュー
- 前方のプロセス処理した値を格納して、順次後方のプロセスが拾い処理する。
- テーブル・キュー自体は抽象概念
  実際には各プロセスそれぞれがキューを持ち、そこに置かれたデータをキュー・リファレンスという番号を使ってリンク。
  読み取ったデータは各プロセスのPGAからPGAにコピーされる。
###### QC クエリーコーディネーター
##### 種類
###### パラレル問合せ
- FULL TABLE SCAN / 全表スキャン
- INDEX FAST FULL SCAN / 索引高速スキャン
- パラレル索引スキャン
- 結合
- ソート
- グループ関数の集計
###### パラレルDML
- SELECT以外のDML文(INSERT, DELETE, UPDATE, MERGE)が該当。
###### パラレルDDL
#### 問題点
##### データ分割の偏り
- 分割をするときに、データが偏らないようにする必要がある。
  ハッシュ、レンジ、ブロードキャストなどがある。
##### プロセス間通信（転送オーバーヘッド）
##### 同時通信（多重実行）
##### パラレル度
#### Link
- [[http://www.oracle.com/technetwork/jp/database/articles/tsushima/index-1741351-ja.html][第20回 パラレル実行について - 津島博士のパフォーマンス講座]]
- [[http://www.oracle.com/technetwork/jp/database/articles/tsushima/tsushima-hakushi-39-2254816-ja.html][第39回 パラレル実行について（2） - 津島博士のパフォーマンス講座]]
- [[http://www.oracle.com/webfolder/technetwork/jp/ondemand/ddd2013/A-4.pdf][シバタツ流！パラレル・クエリーの徹底活用とチューニングの極意 - ORACLE]]
### SDO_GEOR_DDL__TABLE$$, TO Locks
- temp
  sdo_geor_ddl__table$$ is global temporary tabel.
  Created by Oracle Spatial which has installed DDL triger which causes this operation.

- https://jonathanlewis.wordpress.com/2010/02/19/to-locks/
  This is a system which had been installed as a "default" database,
  and the person installing it had just accepted everything the DBCA had offered
  without bothering to eliminate all the options they don't want or need.
  So this system has Oracle Spatial installed, and Spatial has installed a DDL trigger
  that does a lot of stuff in the background when you drop a table
  – using global temporary table SDO_GEOR_DDL__TABLE$$ to keep track of what's going on.

- https://stackoverflow.com/questions/40779201/is-it-wrong-to-use-direct-path-load-hint-in-array-binding
  This is global temporary table.
  Created by Oracle Spatial which has installed DDL trigger which causes this operation.
  This happens we choose General Purpose database creation on DBCA.
  Actually we should use Custom database creation so that we always have option to select required components.

## News
### 2017/1/24 ライセンス体系
- AWS, Azureにおけるクラウド環境でのコア係数を変更。実質的に値上げ。
  マルチコアプロセッサ向けの適用係数から、他社クラウドサービスを外した。
  http://www.oracle.com/jp/store/cloud-lic-170290-ja.pdf
### 2016/3/1 SE1の廃止
- Standard Edition Oneを廃止し、Standard Editionの内容を変更したStandard Edition 2に一本化。
  実質的に値上げに。
## Link
### Oracle 11.2
- [[http://docs.oracle.com/cd/E16338_01/nav/portal_booklist.htm][Oracle® Databaseオンライン・ドキュメント・ライブラリ 11g リリース2 (11.2) すべてのドキュメント]]
#### Install
- [[http://docs.oracle.com/cd/E16338_01/install.112/b56277/toc.htm][Oracle® Databaseクイック・インストレーション・ガイド 11gリリース2 (11.2) for Linux x86-64]]
- [[http://docs.oracle.com/cd/E16338_01/install.112/b56273/rev_precon_db.htm#BGECJCJI][Oracle® Databaseインストレーション・ガイド 11gリリース2 (11.2) for Linux]]
#### 概要
- [[https://docs.oracle.com/cd/E16338_01/server.112/b56306/toc.htm][Oracle® Database概要 11gリリース2 (11.2)]]
#### Manage
- [[https://docs.oracle.com/cd/E16338_01/server.112/b56301/toc.htm][Oracle® Database管理者ガイド 11gリリース2 (11.2)]]
- [[https://docs.oracle.com/cd/E16338_01/backup.112/b56269/toc.htm][Oracle Databaseバックアップおよびリカバリ・ユーザーズ・ガイド11g リリース2(11.2)]]
- [[https://docs.oracle.com/cd/E16338_01/server.112/b61035/title.htm][Oracle® Automatic Storage Management管理者ガイド 11gリリース2 (11.2)]]
#### SQL言語
- [[https://docs.oracle.com/cd/E16338_01/server.112/b56299/toc.htm][Oracle® Database SQL言語リファレンス 11gリリース2]]
#### SQL*Plus
- [[https://docs.oracle.com/cd/E16338_01/server.112/b56314/toc.htm][SQL*Plus®ユーザーズ・ガイドおよびリファレンスリリース11.2]]
#### PL/SQL
- [[https://docs.oracle.com/cd/E16338_01/appdev.112/b56260/toc.htm][Oracle® Database PL/SQL言語リファレンス 11gリリース2 (11.2)]]
- [[https://docs.oracle.com/cd/E16338_01/appdev.112/b56262/toc.htm][Oracle® Database PL/SQLパッケージおよびタイプ・リファレンス 11g リリース2(11.2)]]
#### Backup/Recovery
- [[https://docs.oracle.com/cd/E16338_01/backup.112/b56269/toc.htm][Oracle Databaseバックアップおよびリカバリ・ユーザーズ・ガイド 11g リリース2(11.2)]]
- [[http://docs.oracle.com/cd/E16338_01/backup.112/b56270/toc.htm][Oracle® Databaseバックアップおよびリカバリ・リファレンス 11gリリース2(11.2)]]
#### Reference
- [[https://docs.oracle.com/cd/E16338_01/server.112/b56311/toc.htm][Oracle® Databaseリファレンス 11gリリース2 (11.2)]]
#### Performance
- [[https://docs.oracle.com/cd/E16338_01/server.112/b56312/toc.htm][Oracle® Databaseパフォーマンス・チューニング・ガイド 11gリリース2 (11.2)]]
#### Utilities
- [[https://docs.oracle.com/cd/E60665_01/db112/SUTIL/toc.htm][Oracle® Databaseユーティリティ 11gリリース2 (11.2)]]

#### Geo Spatial
- [[https://docs.oracle.com/cd/E16338_01/appdev.112/b72087/toc.htm][Oracle® Spatial開発者ガイド 11gリリース2 (11.2)]]
- [[https://docs.oracle.com/cd/E16338_01/appdev.112/b72086/toc.htm][Oracle® Spatial GeoRaster開発者ガイド 11gリリース2 (11.2)]]
#### 2日でシリーズ
- [[https://docs.oracle.com/cd/E16338_01/server.112/b56320/toc.htm][Oracle® Database 2日でデータベース管理者 11gリリース2(11.2)]]
- [[https://docs.oracle.com/cd/E16338_01/appdev.112/b56265/toc.htm][Oracle® Database 2日で開発者ガイド 11gリリース2 (11.2)]]
- [[https://docs.oracle.com/cd/E16338_01/server.112/b56313/tdppt_preface.htm#sthref2][Oracle® Database 2日でパフォーマンス・チューニング・ガイド 11gリリース2(11.2)]]
### Etc
- [[https://support.oracle.com/epmos/faces/Dashboard][my oracle support]]

- [[http://luna.gonna.jp/oracle/index.html][オラクル ちょこっとリファレンス]]
- [[http://kagamihoge.hatenablog.com/entry/2014/01/03/180049][どのようにOracleを勉強してきたか - kagamihogeの日記]]
- [[https://blogs.oracle.com/otnjp/entry/links_for_oracle_database_beginners][春からはじめる、春からやりなおす。これから学ぶOracle Database - Oracle Technology Network Japan Blog]]
- [[http://www.drk7.jp/MT/archives/001223.html][Oracle 運用術 ： これだけでほぼ十分。運用監視スクリプト - drk7.jp]]
- [[http://www.doppo1.net/index.html][Walking ALone]]
