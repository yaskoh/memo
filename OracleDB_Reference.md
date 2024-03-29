# OracleDB Reference
## Reference
### 初期化パラメータ
#### AUDIT_FILE_DEST
- Type:文字列
  AUDIT_TRAIL初期化パラメータがos, xmlまたはxml,extendedに指定されている場合に監査証跡が書き込まれるOSディレクトリを指定する。
#### AUDIT_TRAIL
- Type:文字列, Default:none
  データベースの監査を使用可能または使用禁止にする
- value
  - none
    標準監査を使用禁止にする。
  - os
    すべての監査レコードをOSファイルに書き込む。
  - db
    OSの監査証跡に常に書き込まれるレコードを除いて、監査レコードをデータベース監査証跡(SYS.AUD$表内)に書き込む。
  - db, extended
    dbのすべてのアクションを実行し、SYS.AUD$表が利用できる場合はこの表のSQLBINDおよびSQLTEXT CLOB列にデータを移入する。
  - xml
    XML形式でOS監査レコードファイルに書き込む。
  - xml, extended
    xmlのすべてのアクションを実行し、監査証跡にSQLテキストおよびSQLバインド情報が含まれる。
#### BACKGROUND_DUMP_DEST
- ALERTログおよびバックグラウンド・トレースの格納場所
  バックグラウンド・プロセス(LGWR, DBWnなど)のデバッグ・トレース・ファイルが書き込まれるパス名を指定する。
#### COMPATIBLE
- Type:文字列, 変更不可
  Oracleとの互換性を保つ必要があるリリースを指定する。
n**** CONTROLL_FILES
- 制御ファイル名のリスト
#### DB_BLOCK_BUFFERS
- 
  DB_CACHE_SIZEより古くから使われていたパラメータ。
  特に事情がなければDB_CACHE_SIZEを使う。
   
#### DB_BLOCK_SIZE
- 標準ブロックサイズの確認
#### DB_CACHE_SIZE
- バッファキャッシュのサイズを設定するパラメータ。
#### DB_DOMAIN
- Type:文字列, 変更不可
  分散システムまたはその一部の場合、この値を設定する必要がある。
#### DB_NAME
- データベース名
#### DDL_LOCK_TIMEOUT
- DDLの対象がロックされていた場合の待ち時間を指定する。

#### DIAGNOSTIC_DEST
- Type:文字列, 変更:ALTER SYSTEM
  各インスタンスの診断が専用のディレクトリに配置され、専用ディレクトリはDIAGNOSTIC_DESTの初期化パラメータによって指定する。
  ディレクトリ構造は、<diagnostic_dest>/diag/rdbms/<dbname>/<instance>
  上記は自動診断リポジトリ(ADR)ホームと呼ばれ、以下のファイルが配置される。
  - トレース・ファイル : <adr-home>/trace配下に配置
  - アラート・ログ : <adr-home>/alert配下に配置
  - コア・ファイル : <adr-home>/cdump配下に配置
  - インシデント・ファイル : <adr-home>/incident/<incdir#>に配置。各重大エラーが発生した場合。
#### DISPATCHERS
- Type:文字列
  共有サーバ・アーキテクチャ内のディスパッチャ・プロセスを構成する。
#### FIXED_DATE
- システム日時を一時的に変更する際に設定する
#### INSTANCE_NAME
- インスタンス名
#### JAVA_POOL_SIZE
#### LARGE_POOL_SIZE
#### LOCAL_LISTENER
- Type:文字列, Default:(ADDRESS = (PROTOCOL=TCP)(HOST=hostname)(PORT=1521))
#### NLS_LANGUAGE
- Type:文字列, Default:OSのNLS_LANGから導出される
  データベースのデフォルト言語を指定する。
  メッセージ、曜日名、月名、AD、BC、a.m.、p.m.の記号およびデフォルトのソート・メカニズムに使用される。
#### NLS_LENGTH_SEMANTICS
#### NLS_TERRITORY
- Type:文字列, Default:OS依存
  日と週の順序付けについて地域別規則に従う場合のその地域の名前を指定する。
#### OPEN_CURSORS
- Type:整数, Default:50, Range:0-65535
  1つのセッションで同時にオープンできるカーソルの最大数。
#### OPTIMIZER_MODE
- Type:文字列, Default:all_rows
  インスタンスの最適化方法を選択するためのデフォルトの動作を確立する。
- Value
  - first_rows_n
    最短の応答時間で最初のn行(n=1,10,100,1000)を戻すために最適化する。
  - first_rows
    コストと発見的方法を組み合わせて使用し、最初の数行を迅速に配信するための最適な計画を判断する
  - all_rows
    セッション内のすべてのSQL文に対してコストベース方法を使用し、最高のスループットを得るために最適化する。
#### PGA_AGGREGAET_TARGET
- Type:大整数, Default:10MBもしくはSGAサイズの20%の大きい方, Range:10MB - 4096GB-1
  インスタンスに接続されたすべてのサーバー・プロセスが使用できるターゲット集計PGAメモリーを指定する。
#### PROCESSES
- Type:整数, Default:100, Range:6以上
  Oracleに同時に接続できるOSのユーザー・プロセスの最大数を指定する。
#### REMOTE_LOGIN_PASSWORDFILE
- Type:文字列, Defaut:exclusive
  Oracleがパスワードファイルを確認するかどうかを指定する。
- Value
  - shared
    1つ以上のデータベースがパスワードファイルを使用可能。
  - exclusive
    1つのデータベースのみがパスワードファイルを使用可能。
  - none
    パスワードファイルは無視される。
#### SERVICE_NAME
#### SGA_MAX_SIZE
- 最大SGAメモリサイズ(BYTE)
#### SGA_TARGET
- Type:大整数, Syntax: SGA_TARGET = integer[K|M|G], Default:0, Range:64MB以上
  全てのSGAコンポーネントの合計サイズ(Byte)を指定する。
  この値が設定されると、次のメモリー・プールのサイズが自動的に設定される。
  - バッファキャッシュ(DB_CACHE_SIZE), 共有プール(SHARED_POOL_SIZE), ラージ・プール(LARGE_POOL_SIZE),
    Javaプール(JAVA_POOL_SIZE), Streamsプール(STREAMS_POOL_SIZE)
  
#### SHARED_POOL_SIZE
- システムグローバル領域(SGA)内の共有プールのサイズ(BYTE)
#### SPFILE
- サーバー・パラメータ・ファイルのパス
#### STREAMS_POOL_SIZE
- SGA_TARGET初期化パラメータに0以外の値を設定すると、Oracleの自動共有メモリ―管理機能によってStreamsプールのサイズが管理される。
  STREAMS_POOL_SIZE初期化パラメータにも0以外の値を設定した場合、この値は、Streamsプールの最小値として自動共有メモリ―管理によって使用される。
#### UNDO_TABLESPACE
- Type:文字列, Default:データベース内の最初に使用可能なUNDO表領域
  インスタンスの起動時に使用するUNDO表領域。
#### USER_DUMP_SIZE
- ユーザートレースの格納場所
#### hidden
#### Memo
##### 確認方法
- show parameter
- select * from v$parameter; (現在のセッション)
- select * from v$system_parameter (システム、新規セッションのデフォルト)
### 静的データ・ディクショナリ・ビュー
#### ALL
- 現在ユーザがアクセス可能な全て
##### ALL_CLUSTERS
- 現在のユーザがアクセスできるすべてのクラスタを示す。
##### ALL_CONS_COLUMNS
- 現行のユーザがアクセスでき、また制約に指定されている列を示す。
##### ALL_CONSTRAINTS
- 現行のユーザがアクセスできる表の制約定義を示す。
- CONSTRAINT_TYPE
  - C : Constraint 表でのチェック制約
  - P : Primary Key
  - U : Unique Key
  - R : 参照整合性
  - V : ビューでのチェック・オプション付
  - O : ビューで読み取り先勝
  - H : ハッシュ式
  - F : REF列を含む制約
  - S : サプリメンタル・ロギング
##### ALL_COL_COMMENTS
- 現行のユーザーがアクセスできる表およびビューの列についてのコメントを示す。
##### ALL_DB_LINKS
##### ALL_DIRECTORIES
- 現在のユーザがアクセスできるディレクトリをすべて示す。
##### ALL_INDEXES
- 現在のユーザがアクセスできる表の索引を示す。
##### ALL_IND_COLUMNS
##### ALL_IND_PARTITIONS
##### ALL_IND_STATISTICS
##### ALL_SEQUENCES
##### ALL_SOURCE
- 現行のユーザがアクセスできるストアド・オブジェクトのテキスト・ソースを示す。
##### ALL_TAB_COMMENTS
- 現行のユーザがアクセスできる表およびビューのコメントを示す。
#### DBA
- DB内全て
##### DBA_AUTOTASK_CLIENT
- 7日間および30日間の各自動メンテナンスタスクに対する統計データを示す。
##### DBA_AUTOTASK_OPERATION
- 各クライアントの自動メンテナンス・タスク操作をすべて示す。
##### DBA_AUTOTASK_TASK
- 現在および過去の自動メンテナンス・タスクに関する情報を示す。
##### DBA_AUTOTASK_WINDOW_CLIENTS
- MAINTENANCE_WINDOW_GROUPに属するウィンドウを、各メンテナンス・タスクのウィンドウのステータスEnabledまたはDisabledとともに示す。
##### DBA_CLUSTERS
##### DBA_COL_COMMENTS
- データベース内のすべての表及びビューについてのコメントを示す。
##### DBA_CONSTRAINTS
- データベース内の制約定義をすべて示す。
##### DBA_DATA_FILES
- データベース・ファイルを示す。
###### Columns
####### FILE_NAME
####### TABLESPACE_NAME
####### ONLINE_STATUS
- ファイルのオンライン状態。
  - SYSOFF
  - SYSTEM
  - OFFLINE
  - ONLINE
  - RECOVER
##### DBA_EXTENTS
- データベース内のすべての表領域内のセグメントを含むエクステントを示す。
###### Columns
####### OWNER
####### SEGMENT_NAME
####### TABLESPACE_NAME
####### EXTENT_ID
####### BLOCK_ID
####### BYTES
- バイト単位のエクステントのサイズ
####### BLOCKS
- Oracleブロック単位のエクステントのサイズ
##### DBA_HIST_SEG_STAT
- セグメント・レベルの履歴統計情報を示す。
  一連の基準に基づいた最上位セグメントおよびV$SEGSTATからの情報が取得される。
  合計値は、インスタンスの起動以降の統計の値で、デルタ値は、DBA_HIST_SNAPSHOTビューのBEGIN_INTERVAL_TIMEからEND_INTERVAL_TIMEまでの統計値。
###### Columns
####### BUFFER_BUSY_WAITS_DELTA
- buffer busy waitsのデルタ値
##### DBA_HIST_SEG_STAT_OBJ
- ワークロード・リポジトリで取得されたセグメントのすべての名前を示す。
###### Columns
##### DBA_HIST_SNAPSHOT
- ワークロード・リポジトリ内のスナップショットに関する情報を示す。
###### Columns
####### SNAP_ID
- 一意のスナップショットID
##### DBA_HIST_SQLTEXT
- ワークロード・リポジトリで取得された共有SQLカーソルに属するSQL文のテキストを示す。
  V$SQLからの情報が取得され、DBA_HIST_SQLSTATビューとともに使用される。
##### DBA_HIST_SQLSTAT
- SQL統計情報の履歴情報を示す。
  このビューには、一連の基準に基づいた最上位SQL文およびV$SQLからの統計情報が取得される。
##### DBA_HIST_SYSTEM_EVENT
- 1つのイベントについての待機の合計の履歴情報。
  V$SYSTEM_EVENTのスナップショットが含まれる。
###### Columns
####### SNAP_ID
####### DBID
####### INSTANCE_NUMBER
####### EVENT_ID
####### EVENT_NAME
####### WAIT_CLASS_ID
####### WAIT_CLASS
####### TOTAL_WAITS
####### TOTAL_TIMEOUTS
####### TIME_WAITED_MICRO
####### TOTAL_WAITS_FG
####### TOTAL_TIMEOUTS_FG
####### TIME_WAITED_MICRO_FG
##### DBA_HIST_SYSMETRIC_HISTORY
- データベース内に保存されているデータ・セット全体についてのシステム・メトリック値の使用可能なすべての履歴を外部化する。
###### Columns
####### BEGIN_TIME
- 間隔の開始時間
####### METRIC_NAME
- メトリック名
####### VALUE
- メトリック値
##### DBA_DB_LINKS
- テータベース内のデータベース・リンクをすべて示す。
##### DBA_DIRECTORIES
- データベース内のディレクトリをすべて示す。
##### DBA_EXTENTS
- データベース内のすべての表領域内のセグメントを含むエクステントを示す。
##### DBA_FREE_SPACE
- データベース内のすべての表領域の使用可能エクステントを示す。
  tablespaceが表示されない場合は、使用可能エクステントがないということらしい。
  
##### DBA_INDEXES
- データベース内の索引をすべて示す。
##### DBA_IND_COLUMNS
- データベース内のすべての表の索引の列。
- テーブルに紐付くインデックスを調べるときなどに利用。
###### Columns
####### INDEX_NAME
####### TABLE_NAME
####### COLUMN_NAME
##### DBA_IND_PARTITIONS
- データベース内の索引パーティションをすべて示す。
##### DBA_IND_STATISTICS
- データベース内のすべての索引についてのオプティマイザ統計情報を示す。
##### DBA_ROLE_PRIVS
- データベース内のすべてのユーザおよびロールに付与されたロールを表示する
##### DBA_SEGMENTS
- データベース内のすべてのセグメントに割り当てられた記憶域を示す。
##### DBA_SEQUENCES
- データベース内の順序をすべて示す。
##### DBA_SOURCE
- データベース内のすべてのストアド・オブジェクトのテキスト・ソースを示す。
##### DBA_SYS_PRIVS
- ユーザ、またはロールに付与されたシステム権限。
##### DBA_TAB_COMMENTS
- データベース内のすべての表およびビューについてのコメントを示す。
##### DBA_TAB_COLUMNS
- データベース内すべての表、ビューおよびクラスタの列を示す。
  
##### DBA_TAB_COL_STATISTICS
##### DBA_TAB_HISTOGRAMS
##### DBA_TAB_PRIVS
##### DBA_TAB_STATISTICS
##### DBA_TABLES
- データベース内のリレーショナル表をすべて示す。
##### DBA_TABLESPACE_USAGE_METRICS
- 永続、一時、UNDOなどすべてのタイプの表領域についての表領域使用状況メトリックを示す。
###### Columns
####### TABLESPACE_NAME
####### USED_SPACE
####### TABLESPACE_SIZE
####### USED_PERCENT
##### DBA_TABLESPACES
- データベース内の表領域をすべて示す。
##### DBA_USERS
- データベース内のユーザーをすべて示す。
#### USER
- ユーザ所有
##### USER_CLUSTERS
- 現在のユーザが所有する全てのクラスタを示す
  OWNER列を表示しない
##### USER_COL_COMMENTS
##### USER_CONS_COLUMNS
- 現行のユーザが所有していて、また制約に指定されている列を示す。 
##### USER_CONSTRAINTS
- 現在のユーザが所有する表の制約定義をすべて示す。
##### USER_DB_LINKS
- 現在のユーザーが所有するデータベース・リンクを示す。
##### USER_EXTENTS
- DBA_EXTENTSと異なり、OWNER, FILE_ID, BLOCK_ID, RELATIVE_FNO列は存在しない。その他はDBA_EXTENTS列と同様。
##### USER_INDEXES
- 現行のユーザが所有する索引を示す
##### USER_ROLE_PRIVS
##### USER_SEGMENTS
##### USER_SEQUENCES
##### USER_SOURCE
##### USER_SYS_PRIVS
##### USER_TAB_COMMENTS
##### USER_TAB_PRIVS
##### USER_USERS
- 現行のユーザを説明する。
  現在ログインしているユーザを確認する場合などに便利。
#### SYNONYM
##### SYN
##### TABS
- USER_TABELSのシノニム
#### ETC
##### DATABASE_EXPORT_OBJECTS
##### SCHEMA_EXPORT_OBJECTS
##### TAB
- 互換性のために残している。非推奨
##### TABLE_EXPORT_OBJECTS
### Dynamic Performance View / 動的パフォーマンスビュー
#### About
- V$ビュー
  実際の動的パフォーマンスビューは接頭辞V_$であり、それらのビューのパブリックシノニムに接頭辞V$が付いている。
  基本的にV$のみにアクセスするようにする。
- GV$ビュー
  ほとんどすべてのV$ビューに対し、対応するGV$ビューがある。
#### V$ACTIVE_SESSION_HISTORY
- データベース内のサンプリングされたセッション・アクティビティを表示する。
  1秒に1回取得される、アクティブなデータベース・セッションのスナップショットが含まれる。
#### V$BH
- SGA内のバッファごとのpingの状態と数を示す。RACのビュー。
#### V$CONTROLFILE
- 制御ファイルの名前を示す
#### V$DATABASE
- 現在接続しているインスタンスのDBID、チェックポイントなどが取得できる。
#### V$DIAG_INFO
- NAME=VALUEペアを使用して自動診断リポジトリ(ADR)機能の状態を示す。

#### V$EVENT_NAME
- 待機イベントに関する情報を示す。
#### V$FIXED_TABLE
- データベース内のすべての固定表、動的パフォーマンスビューおよび導出表を示す。
  一部のV$表は実表を参照するため表示されない。
#### V$FIXED_VIEW_DEFINITION
- 全ての固定ビュー(V$で始まるビュー)の定義を示す。

#### V$INSTANCE
- 現行インスタンスの状態を表す。
##### Columns
###### INSTANEC_NAME
###### STATUS
- OPEN, MOUNTなどの状態
#### V$LATCHHOLDER
- 現行のラッチ保持プロセスの情報を示す。
#### V$METRIC
- AWRによって取得された一連のメトリックの最新統計値を示す。
#### V$OPTION
- オプション製品のインストール状況
#### V$PARAMETER
- セッションに現在有効になっている初期化パラメータの情報を示す。
#### V$PROCESS
- 現在アクティブなプロセスの情報を示す。
  バックグラウンドプロセスなどが表示される。
#### V$PWFILE_USERS
- パスワードファイル認証にエントリされている（SYSDBAまたはSYSOPERシステム権限がある）ユーザの一覧
#### V$RECOVERY_LOG
- メディア・リカバリの完了に必要なアーカイブ・ログの情報を示す。
  ログ履歴ビューV$LOG_HISTORYから導出される。
#### V$SESSION
- カレント・セッションごとのセッション情報を示す。
#### V$SESSION_WAIT
- 各セッションについて現行または前回の待機を示す。
#### V$SESSION_WAIT_CLASS
#### V$SESSION_WAIT_HISTORY
- 各アクティブ・セッションの最後の10待機イベントを示す。
#### V$SESSTAT
- ユーザー・セッションについての統計情報を示す。
#### V$SQL
- GROUP BY句のない共有SQL領域についての統計情報を示し、入力された元のSQLテキストの子ごとに1行ずつ実行する。
- V$SQLAREAとの違いは、こちらは「子」単位で集計、V$SQLAREAは親カーソル・SQL単位で統計情報を出力する部分。
#### V$SQL_BIND_CAPTURE
- SQLカーソルによって使用されたバインド変数に関する情報を示す。
  
#### V$SQL_PLAN
- ライブラリ・キャッシュにロードされる子カーソルごとの実行計画情報を示す。
#### V$SQL_SHARED_CURSOR
- 特定の子カーソルが既存の子カーソルと共有されない理由を示す。
  それぞれの列は、カーソルが共有されない具体的な理由を示す。
##### Columns
###### SQL_ID
###### ADDRESS
- 親カーソルのアドレス
###### CHILD_ADDERSS
- 子カーソルのアドレス
###### CHILD_NUMBER
- 子番号
###### U/UNBOUND_CURSOR
###### S/SQL_TYPE_MISMATCH
###### O/OPTIMIER_MISMATCH
###### O/OUTLINE_MISMATCH
###### S/STATS_ROW_MISMATCH
###### L/LITERAL_MISMATCH
###### E/
###### B
###### P
###### I
###### S
###### T
###### A
###### B
###### D
###### L
###### T
###### R
###### I
###### I
###### R
###### L
###### I
###### O
###### S
###### M
###### U
###### T
###### N
###### F
#### V$SQLAREA
- 共有SQL領域の統計情報を示し、SQL文字列毎に1行ずつ表示する。
- V$SQLとの違いは、こちらは親カーソル・SQL単位の統計情報、V$SQLは子カーソル単位の統計情報を示す、とのこと。
#### V$SQLTEXT
- SGA内の共有SQLカーソルに属するSQL文のテキストを示す。
#### V$STATNAME
- V$SESSTAT表及びV#SYSSTAT表で表示される統計情報のデコードされた統計名を示す。
#### V$SYSSTAT
- V$SESSTAT表およびV$SYSSTAT表で表示される統計情報のデコードされた統計名を示す。
#### V$SYSTEM_EVENT
- イベントの待機の合計の情報を示す。
#### V$SYSTEM_PARAMETER
- インスタンスに現在有効になっている初期化パラメータの情報。
  新しいセッションは本ビューで確認できるインスタンスの値を継承する。
#### V$SYSTEM_WAIT_CLASS
- 待機イベントクラス毎の待機回数と待機時間を調べられる
#### V$SYSMETRIC_HISTORY
- データベースで使用可能なすべてのシステム・メトリックの値を示す。
  長期(60s, 1hの履歴)および短期(15s, 1間隔の履歴)の両方のメトリックが表示される。
##### Columns
###### GROUP_ID
- メトリック・グループID
###### METRIC_ID
- メトリックID
###### METRIC_NAME
- メトリック名
###### VALUE
- メトリック値
#### Memo(View)
##### 一覧取得方法
- select * from v$fixed_table where type = 'VIEW';
  GV$表も取得される。
### Fixed Table / 固定表, X表
- オラクルの内部表
#### X$BH
- Buffer Header
#### X$KSPPCV
- Kernel Services, Parameter, current value
#### X$KSPPI
- Kernel Services, Parameter, parameter info
##### Columns
###### ksppinm
- name
###### ksppdesc
- description
#### X$KSSPSV
- Kernel Services, Parameter
#### X$KSUPRLAT
#### Memo(Fixed Table)
##### 一覧取得方法
- select * from v$fixed_table where type = 'TABLE';
#### Link
- [[http://yong321.freeshell.org/computer/x$table.html][Oracle X$ Tables]]
- [[http://web.archive.org/web/20101124054809/http://www.fors.com/velpuri2/X$/List%20of%20X$%20Tables][List of X$ Tables and how the names are derived]]
### 待機イベント
#### Class
- 各待機イベントは待機イベントのクラスに属している。
##### About
- 11.2の状況
  select wait_class#, wait_class, count(wait_class) from v$event_name group by wait_class#, wait_class order by wait_class#;
  |-------------+----------------+-------------------|
  | WAIT_CLASS# | WAIT_CLASS     | COUNT(WAIT_CLASS) |
  |-------------+----------------+-------------------|
  |           0 | Other          |               958 |
  |           1 | Application    |                17 |
  |           2 | Configuration  |                24 |
  |           3 | Administrative |                55 |
  |           4 | Concurrency    |                33 |
  |           5 | Commit         |                 2 |
  |           6 | Idle           |                96 |
  |           7 | Network        |                35 |
  |           8 | User I/O       |                48 |
  |           9 | System I/O     |                32 |
  |          10 | Scheduler      |                 8 |
  |          11 | Cluster        |                50 |
  |          12 | Queueing       |                 9 |
  |-------------+----------------+-------------------|
  |         Sum |                |              1367 |
  |-------------+----------------+-------------------|

##### 00 Other
- 通常システムでは発生しない待機。
  wait for EMON to spawnなど
###### Events(Other)
####### check CPU wait times
####### ksxr poll remote instances
####### PX Deq: Signal ACK RSG
####### null event
####### reliable message
##### 01 Application
- ユーザーのアプリケーション・コードによる待機。
  行レベル・ロック、明示的ロックコマンドが原因のロック待機など。
###### Events(Application)
####### enq: TX - row lock contention
- Application
##### 02 Configuration
- データベースの構成またはインスタンスのリソースが十分でないことによる待機。
  ログ・ファイル・サイズ、共有プールサイズなどが小さい、など。
##### 03 Administrative
- ユーザーが待機する原因となるDBAコマンドによる待機。
  索引再作成など。
##### 04 Concurrency
- 内部データベース・リソースの待機
  ラッチなど
###### Events(Concurrency)
####### library cache pin
- Concurrency
- ライブラリ・キャッシュの同時実行性を管理する。
  オブジェクトを確保すると、ヒープがメモリーにロードされる。
####### row cache lock
##### 05 Commit
- 1つの待機イベントのみで構成される待機クラス
  コミット後のREDOログ書き込み確認用待機(log file sync)
###### Events(Commit)
####### log file sync
- Commit
- LGWRを転送してログ・バッファをREDOログ・ファイルに書き込む。
##### 06 Idle
- セッションがアクティブでない、すなわち作業の待機中であることを示す待機。
  SQL*Net message from clientなど。
##### 07 Network
- ネットワーク・メッセージに関連する待機。
  SQL*Net more data to dblinkなど。
##### 08 User I/O
- ユーザーI/Oの待機
  db file sequential readなど
###### Events(User I/O)
####### Archive Manager file transfer I/O
####### ASM Fixed Package I/O
####### ASM Staleness File I/O
####### BFILE read
####### buffer read retry
####### cell list of blocks physical read
####### cell multiblock physical read
####### cell single block physical read
####### cell smart file creation
####### cell smart index scan
####### cell smart table scan
####### cell statistics gather
####### Data file init write
####### Datapump dump file I/O
####### db file parallel read
- User I/O
- リカバリ時のイベント。リカバリ時に変更が必要となったデータベース・ブロックはデータベースからパラレルに読み込まれる。
####### db file scattered read
- User I/O
- db file sequential readと似ているが、セッションが複数のデータ・ブロックを読み込んでいる。
####### db file sequential read
- User I/O
- データベースからの順次読み取りが実行されている間待機する。
  制御ファイルの再構築、データベース・ファイル・ヘッダーのダンプ、データベース・ファイル・ヘッダーの取得にも使用する。
####### db file single write
####### db flash cache multiblock physical read
####### db flash cache single block physical read
####### db flash cache write
####### dbms_file_transfer I/O
####### dbverify reads
####### DG Broker configuration file I/O
####### direct path read
####### direct path read temp
####### direct path sync
####### direct path write
####### direct path write temp
####### Disk file I/O Calibration
####### Disk file Mirror Read
####### Disk file Mirror/Media Repair Write
####### Disk file operations I/O
####### external table misc IO
####### external table open
####### external table read
####### external table seek
####### external table write
####### flashback log file sync
####### local write wait
####### Log file init write
####### Parameter File I/O
####### read by other session
- User I/O
- セッションが別のセッションによって現在バッファ・キャッシュに読み込まれているバッファをリクエストする場合に発生する。
####### securefile direct-read completion
####### securefile direct-write completion
####### Shared IO Pool IO Completion
####### TEXT: File System I/O
####### utl_file I/O
##### 09 System I/O
- バックグラウンド・プロセスのI/Oの待機
  db file parallel writeのDBWR待機など
###### Event(System I/O)
####### control file sequential read
##### 10 Scheduler
- リソース・マネージャに関連する待機
  resmgr: become activeなど
##### 11 Cluster
- Real Application Clustersリソースに関連する待機。
  gc cr block busyなどのグローバル・キャッシュ・リソースなど
###### Events(Cluster)
####### gc buffer busy acquire
- Cluster
- 別のセッションが別のインスタンスのキャッシュからバッファを読み取り中であるため、バッファ・キャッシュ内でバッファを確保できない。
####### gc cr block 2-way
- Cluster
- ブロックの待機、確保またはログ・フラッシュなしでリモート・キャッシュ・ブロックがローカルインスタンスへ送信されたことを示す。
####### gc cr grant 2-way
- Cluster
- メッセージ関連待機イベント。
  インスタンスにブロックがキャッシュされなかったために、ブロックが受信されなかったことを示す。
####### gc current block 2-way
- Cluster
- ブロックの待機、確保またはログ・フラッシュなしでリモート・キャッシュ・ブロックがローカルインスタンスへ送信されたことを示す。
####### gc current block busy
- Cluster
- リモート・キャッシュまたはローカル・キャッシュがビジーなため、キャッシュ・データ・ブロックへのアクセスが遅延状態であることを示す。
####### gc current grant 2-way
- Cluster
- メッセージ関連待機イベント。
  インスタンスにブロックがキャッシュされなかったために、ブロックが受信されなかったことを示す。
##### 12 Queueing
- パイプライン化された環境における追加データ取得での遅延を示すイベントが含まれる。
  パイプラインに非効率性などの問題があることを示す。
#### Event parameters
##### block#
##### blocks
##### break?
##### class
##### dba
##### driver id
##### file#
##### id1
##### id2
##### le
##### mode
##### name, type
##### namespace
##### requests
##### session#
##### waited
#### Events
- 各クラスに割り振る。
- https://docs.oracle.com/cd/E16338_01/server.112/b56311/waitevents003.htm#BGGIBDJI
#### Memo(待機イベント)
- [[file:OracleDB_Performance.org][OracleDB_Performance.org]]
#### Link
- [[https://docs.oracle.com/cd/E16338_01/server.112/b56311/waitevents.htm][Oracle待機イベント - Oracle® Databaseリファレンス 11gリリース2 (11.2)]]
- [[http://www.doppo1.net/oracle/tuning/wait-event.html][待機イベント一覧 - WalkingAlone]]

### Enqueue / エンキュー名
### 統計情報
- https://docs.oracle.com/cd/E16338_01/server.112/b56311/stats002.htm
#### 統計クラス
- 
  |-----+---------------------------|
  |   1 | User                      |
  |   2 | Redo                      |
  |   4 | Enqueue                   |
  |   8 | Cache                     |
  |  16 | OS                        |
  |  32 | Real Application Clusters |
  |  64 | SQL                       |
  | 128 | Debug                     |
  |-----+---------------------------|
  
#### 統計情報説明
- 2つ以上のフラグが立つ場合があるので、クラスに分けず記載する。
##### About
- 以下コマンドで一覧を確認できる。
  select * from v$sysstat;
  11.2では計679。
##### application wait time
##### background checkpoints started
##### global cache cr block receive time (40)
- フォアグラウンド・プロセスがインターコネクト経由で送信されるCRブロックを待機した合計時間。
##### global cache cr block serve time (40)
- BSPプロセスが読み取り一貫性(CR)ブロックを構成するために必要とした時間。
##### global cache cr blocks received (40)
- 受信したブロックの合計数
##### parse count(hard)
- 解析コール(実解析)の合計数。
  ハード解析は、作業ヒープおよびその他のメモリー構造体を割り当てた後に解析ツリーを構築することを要求するため、
  メモリー使用の面から考えて、非常にコストが高い。
##### recursive calls (1)
- 実行時内部で発行されたrecursive call、再帰的コールの回数
##### db block gets
- DMLやSELECT FOR UPDATEを発行したときなどに発生するカレントモードで読み込まれたブロック数。
  ブロックの要求回数
##### consistent gets
- SELECTを発行したときなどに発生する読み取り一貫性モードで読み込まれたブロック数
  ブロックレベルの一貫性読み込み回数
##### physical reads
- ディスクアクセスによって読み込まれたブロック数
  物理読み込みの合計数(physical reads direct + physical reads cache)
##### redo size
- REDOログに書き込まれたサイズ
  生成されたREDOの合計（バイト)
##### bytes sent via SQL*Net to client
- クライアントへ送られた合計byte数
##### bytes received via SQL*Net from client
- クライアントから受信した合計byte数
##### SQL*Net roundtrips to/from client
- クライアントに送受信されたNetメッセージの合計数
  Oracle Netの送受信のやり取りの合計数
##### sorts (memory)
- メモリ内で実行されたソート回数
##### sorts (disk)
- ディスク書き込みを伴うソート回数
##### rows processed
- SQLが処理した件数
### Background processes / バックグラウンドプロセス
#### CJQ0 / ジョブ・キュー・コーディネーター・プロセス
- データディクショナリから実行する必要のあるジョブを選択し、ジョブを実行するジョブ・キュー・スレーブ・プロセス(Jnnn)を起動する。
#### CKPT / チェックポイント・プロセス
- チェックポイントでDBWnにシグナルを送り、データベースのすべてのデータ・ファイルと制御ファイルを更新して、最新のチェックポイントを示す
#### DBRM / データベース・リソース・マネージャ・プロセス
- リソース・プランを設定して、データベース・リソース・マネージャに関連するその他のタスクを実行する。
#### DBW0/ データベース・ライター・プロセス
- 変更されたブロックをデータベース・バッファ・キャッシュからデータ・ファイルに書き込む
#### DIA0 / 診断プロセス
- ハングおよびデッドロックを検出し解決する
#### DIAG / 診断取得プロセス
- 診断ダンプを実行する
#### Dnnn / ディスパッチャ・プロセス
- 共有サーバー・アーキテクチャでネットワーク通信を実行する
#### GEN0 / 一般タスク実行プロセス
- SQLとDMLを含む要求されたタスクを実行する
#### LGWR / ログ・ライター・プロセス
- オンラインREDOログにREDOエントリを書き込む
#### MMAN / メモリー・マネージャ・プロセス
- インスタンスのメモリー・マネージャとして機能する
#### MMNL / 管理性モニター・ライト・プロセス
- アクティブ・セッション履歴のサンプリング、メトリック計算など、管理性に関するタスクを実行する
#### MMON / 管理性モニタープロセス
- 管理性に関する多数のタスクを実行したり、そのスケジュールを設定する
#### PING / インターコネクト待機時間測定プロセス
- クラスタ・インスタンス・ペアごとに通信に伴う待機時間を評価する
#### PMON / プロセス・モニター
- 他のバックグラウンド・プロセスを監視し、サーバー・プロセスまたはディスパッチャ・プロセスが異常終了した場合にプロセスのリカバリを実行する
#### PSP0 / プロセス・スポーナ・プロセス
- 初期のインスタンス起動後にOracleバックグラウンド・プロセスを起動する。
#### QMNC / AQコーディネータ・プロセス
- AQを監視する
#### Qnnn / AQサーバー・クラス・プロセス
- QMNCのために様々なAQ関連のバックグラウンド・タスクを実行する
#### RECO / リカバリ・プロセス
- 分散データベースでのネットワークまたはシステムの障害によって保留にされている分散トランザクションを解決する
#### SMCO / 領域管理コーディネーター・プロセス
#### SMON / システム・モニター・プロセス
#### Snnn / 共有サーバー・プロセス
#### VKTM / 時間の仮想キーパー・プロセス
#### Wnnn / 領域管理スレーブ・プロセス
#### Memo(Background processes)
##### リスト取得方法
- おそらく不完全
- select * from v$process;

### PL/SQLパッケージ
#### DBMS_ADVISOR
- 
  データベース・サーバー・コンポーネントに関するパフォーマンス問題を特定および解決する一連のエキスパート・システムであるアドバイザのサーバー管理スイートに含まれる。
- 
  https://docs.oracle.com/cd/E57425_01/121/ARPLS/d_advis.htm#CIHIGAED
#### DBMS_ASSET
##### Subprograms
###### ENQUOTE_NAME
- 文字列リテラルを開始一重引用符と終了一重引用符で囲む。
###### SCHEMA_NAME
- 入力文字列が既存のスキーマ名であることを検証する。
#### DBMS_AUTO_TASK_ADMIN
- AUTOTASK機能へのインターフェースを提供する。
  
##### Subprograms
###### DISABLE
- AUTOTASKが、指定したクライアントまたは操作による要求を実行しないようにする。
###### ENABLE
- 以前に使用禁止にしたクライアント、操作、ターゲット・タイプまたは個々のターゲットをAUTOTASKコントロールの基で使用可能にする。
#### DBMS_FLASHBACK
-
##### Subprograms
###### DISABLE
- セッション全体においてフラッシュバックモードを無効化する。
###### ENABLE_AT_SYSTEM_CHANGE_NUMBER
###### ENABLE_AT_TIME
###### GET_SYSTEM_CHANGE_NUMBER
- 現在のSCNをOracleの数値タイプとして戻す。
###### TRANSACTION_BLOCKOUT
#### DBMS_METADATA
##### Subprograms
###### GET_xxx
- オブジェクトのメタデータを1回のコールでフェッチできる。
- Type
  - GET_XML
  - GET_DDL
  - GET_SXML
  - GET_DEPENDENT_XML
  - GET_DEPENDENT_DDL
  - GET_GRANTED_XML
  - GET_GRANTED_DDL
- Ex
  - select dbms_metadata.get_ddl('TABLESPACE','SYSTEM') from dual;
  - select dbms_metadata.get_ddl('TABLE','TableName','SchemaName') from dual;
    
- Memo
  - SET LONGを十分大きな値にし、PAGESIZEを0にしておくとよい。
#### DBMS_MONITOR
- PL/SQLを使用して統計情報収集とSQLトレースを制御するためのパッケージ。
##### Subprograms
###### CLIENT_ID_STAT_DISABLE
###### CLIENT_ID_STAT_ENABLE
###### CLIENT_ID_TRACE_DISABLE
###### CLIENT_ID_TRACE_ENABLE
###### DATABASE_TRACE_DISABLE
- データベース全体または特定のインスタンスに対するSQLトレースを無効にする。
###### DATABASE_TRACE_ENABLE
- データベース全体または特定のインスタンスに対するSQLトレースを有効にする。
###### SESSION_TRACE_DISABLE
- 指定されたデータベース・セッション識別子(SID)に対して有効にされたトレースをローカル・インスタンス上で無効にする。
###### SESSION_TRACE_ENABLE
- 指定されたデータベース・セッション識別子(SID)に対して有効にされたトレースをローカル・インスタンス上で有効にする。
#### DBMS_PROFILER
- 既存のPL/SQLアプリケーションをプロファイルし、パフォーマンスのボトルネックを識別するためのインターベースを提供する。
##### Subprograms
###### FLUSH_DATA
###### GET_VERSION
###### INTERNAL_VERSION_CHECK
###### PAUSE_PROFILER
###### RESUME_PROFILER
###### START_PROFILER
###### STOP_PROFILER
#### DBMS_SQLTUNE
- 
  オンデマンドでSQLをチューニングするためのインターフェース。

- 
  https://docs.oracle.com/cd/E57425_01/121/ARPLS/d_sqltun.htm#CHDGAJCI
#### DBMS_STATS
- データベース・オブジェクト用に収集したオプティマイザの統計情報を表示及び変更できる。
##### Constants 定数
###### AUTO_CASCADE
###### AUTO_DEGREE
###### AUTO_INVALIDATE
###### AUTO_SAMPLE_SIZE
##### Supprograms
###### オプティマイザ統計情報の収集
- 特定のクラスのオプティマイザ統計情報を収集し、ANALYZEコマンドの潜在的なパフォーマンスを向上させる。
####### GATHER_DICTIONARY_STATS
- ディクショナリのスキーマ('SYS', 'SYSTEM'およびRDBMSコンポーネントに関するスキーマ)に関する統計情報を集する。
####### GATHER_INDEX_STATS
- 索引の統計譲歩うを収集する。
  可能な限り多くの作業をパラレル化する。
######## Parameters
######### ownname
- 索引のスキーマ
######### indname
- 索引名
######### partname
- パーティション名
######### estimate_percent
- 推定する行のパーセント
######### stattab
######### degree
######### granularity
####### GATHER_SCHEMA_STATS
####### GATHER_TABLE_STATS
####### GENERATE_STATS
###### 統計情報の設定または取得
####### PREPARE_COLUMN_VALUES
####### SET_INDEX_STATS
####### SET_TABLE_STATS
####### GET_INDEX_STATS
####### GET_INDEX_STATS
###### 統計情報の削除
####### DELETE_DATABASE_STATS
####### DELETE_INDEX_STATS
####### DELETE_TABLE_STATS
###### 統計情報の転送
####### CREATE_STAT_TABLE
####### DROP_STAT_TABLE
####### EXPORT_DICTIONARY_STATS
####### EXPORT_INDEX_STATS
####### EXPORT_TABLE_STATS
####### IMPORT_DICTIONARY_STATS
####### IMPORT_INDEX_STATS
####### IMPORT_TABLE_STATS
###### 統計情報のロックまたはロック解除
####### LOCK_SCHEMA_STATS
####### LOCK_TABLE_STATS
####### UNLOCK_SCHEMA_STATS
####### UNLOCK_TABLE_STATS

###### 統計履歴のリストアおよびパージ
####### RESET_GLOBAL_PREF_DEFAULTS
####### RESTORE_DICTIONARY_STATS
####### RESTORE_SCHEMA_STATS
####### RESTORE_TABLE_STATS
#### DBMS_SYSTEM
- http://www.morganslibrary.org/reference/pkgs/dbms_system.html
##### Subprograms
###### SET_EV
###### SET_QSL_TRACE_IN_SESSION
- Turn tracing on or off in any session
#### DBMS_TRACE
- PL/SQLトレースを開始および停止するサブプログラムを提供する。
#### DBMS_ROWID
- ROWIDに関する情報を取得できる。
  https://docs.oracle.com/cd/E16338_01/appdev.112/b56262/d_rowid.htm
#### DBMS_XMLGEN
- SQL問合せの結果を標準的なXML形式に変化する。
##### Subprograms
###### GETXML
- XML文書を取得する。指定した最大行数まで行をフェッチする。
###### GETXMLTYPE
###### NEWCONTEXT
#### DBMS_XPLAN
- EXPLAIN PLANコマンドの出力を事前定義した複数の書式で表示する簡単な方法が提供される。
##### Supprograms
#### SDO_GEOM
- ジオメトリファンクション
#### SDO_GEOR
- Oracle Spatial GeoRaster機能に関するファンクションおよびプロシージャが含まれる。
#### TimesTen
##### UTL_RECOMP
- データベース内の無効なPL/SQLモジュール、無効なビュー、索引タイプおよび演算子を再コンパイルする。
###### RECOMP_PARALLELプロシージャ
- 
  特定のスキーマ内の無効なオブジェクトまたはデータベース内のすべての無効なオブジェクトを、パラレルに再コンパイルする。
  TimesTenでパラレル実行される再コンパイル・スレッドの数は常に1つなので、SERIALとの違いは事実上ない。
###### RECOMP_SERIALプロシージャ
- 
  特定のスキーマ内またはデータベース内の無効なオブジェクトを再コンパイルする。

## Link
### Reference
- [[https://docs.oracle.com/cd/E16338_01/server.112/b56311/toc.htm][Oracle® Databaseリファレンス 11gリリース2 (11.2)]]
- [[https://docs.oracle.com/cd/E16338_01/appdev.112/b56262/toc.htm][Oracle® Database PL/SQLパッケージおよびタイプ・リファレンス 11g リリース2(11.2)]]

