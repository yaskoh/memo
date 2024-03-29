# OracleDB SQL Lanugage
## SQL言語
### 擬似列
#### ROWNUM
- 
  問い合わせによって戻される各行について、表や結合処理された行の集合からOracleが行を選択する順序を示す番号を戻す。
  つまり、選択される最初の行のROWNUMは1、2番目の行のROWNUMは2、となる。
  
### 要素
#### データ型
##### 組み込み
###### CHAR
- 
  固定長の文字列を指定する。

###### NCHAR
###### NVARCHAR2
###### VARCHAR2
- 
  変長のデータ型。

###### VARCHAR
- 
  使用せず、VARCHAR2を使用する。
  現在はVARCHAR2と同様の動きをするが、今後異なる比較せマンティクスで比較される別の可変長文字列のデータ型に変更予定。

###### NUMBER
- NUMBER(p, s)
  固定小数点数。
  0と、絶対値が1.0×10^(-130)以上1.0×10^126未満の範囲にある正と負の値を格納する。

- p:精度(precision)
  最大有効桁数。

- s:位取り(scale)
  小数点から最下位有効桁までの桁数。

###### FLOAT
###### DATE
- 
  日付および時刻の情報を格納するために使用する。

###### TIMESTAMP
###### TIMESTAMP WITH TIME ZONE
###### TIMESTAMP WITH LOCAL TIME ZONE
###### INTERVAL YEAR TO MONTH
###### INTERVAL DAY TO SECOND
###### RAW, LONG RAW
- バイナリデータまたはバイト列。
  LONG RAW列はBLOBへ変換することを推奨。
###### BLOB
###### CLOB
##### ROWID
###### ROWID
###### UROWID
##### XML
##### Spatial
#### リテラル
##### テキスト・リテラル
##### 数値リテラル
###### 整数
###### NUMBER/浮動小数点
##### 日時リテラル
###### DATE 日付リテラル
- Format
  DATE 'YYYY-MM-DD'
  ex : DATE '2016-12-1'
###### TIMESTAMP
- Format
  TIMESTAMP 'YYYY-MM-DD HH:MM:DD.x(*9:max)
  
  ex : TIMESTAMP '2016-12-1 12:00:00.123456789'
###### TIMSETAMP WITH TIME ZONE
###### TIMSETAMP WITH LOCAL TIME ZONE
##### 期間リテラル
###### INTERVAL YEAR TO MONTH
###### INTERVAL DAY TO SECOND
#### NULL
#### コメント
##### ヒント
#### データベース・オブジェクト
##### スキーマ・オブジェクト
##### 非スキーマ・オブジェクト
### 演算子
#### SQL演算子
- 優先順位
  - +, -(単項演算子), PRIOR, CONNECT_BY_ROOT
  - *, /
  - +, -(バイナリ演算子), ||
#### 算術演算子
- +, -(単項演算子)
- +, -(バイナリ演算子)
- *, /(バイナリ演算子)
  
#### 連結演算子
- ||
  文字列およびCLOBデータを連結する
  
#### 階層問い合わせ演算子
- PRIOR
- CONNECT_BY_ROOT
#### 集合演算子
- UNION
- UNION ALL
- INTERSECT
- MINUS

#### MULTISET
### ファンクション
#### 単一行ファンクション
##### 数値ファンクション
###### ABS
###### CEIL
###### EXT
###### FLOOR
###### MOD
###### POWER
###### ROUND
###### SQRT
##### 文字値を戻す文字ファンクション
###### CHR
- nに等しい2進数を持つ文字を、VARCHAR2値として戻す。
####### Syntax
- CHAR ( n [ USING NCHAR_CS ] )
###### CONCAT
- 
  2つの引数を連結して返す。

###### REGEXP_REPLACE
- REGEXP_REPLACE ( source_char, pattern [, replace_string[, position[, occurrence[, match_param]]]])
  正規表現パターンで文字列を検索できるようにREPLACEの機能を拡張したもの。
###### REGEXP_SUBSTR
- REGEXP_SUBSTR ( source_char, pattern [, position[, occurrence[, match_param[, subexpr]]]])
  正規表現パターンで文字列を検索できるようにSUBSTRの機能を拡張したもの。
###### REPLACE
- REPLACE (char, search_string[, replacement_string] )
  replacement_stringを変換してcharを戻す。
###### SUBSTR
- {SUBSTR | SUBSTRB | SUBSTRC | SUBSTR2 | SUBSTR4} (char, position[, substring_length])
  charのpositionの文字からsubstring_length文字分の文字列を抜き出して戻す。
###### TRIM
##### 数値を戻す文字ファンクション
###### ASCII
- charの最初の文字の、データベース・キャラクタ・セットでの10進数表記を戻す。
####### Syntax
- ASCII ( char )
###### LENGTH
###### REGEXP_COUNT
##### キャラクタ・セット・ファンクション
##### 日時ファンクション
###### ADD_MONTHS
###### CURRENT_DATE
- DATE型を返す
###### CURRENT_TIMESTAMP
- DATETIME WITH ZONE型を返す
###### LAST_DAY
###### LOCALTIMESTAMP
###### NEXT_DAY
###### ROUND
###### SYSDATE
###### SYSTIMESTAMP
###### TO_TIMESTAMP
##### 一般的な比較ファンクション
###### GREATEST
###### LEAST
##### 変換ファンクション
###### CAST
###### SCN_TO_TIMESTAMP
- SCN_TO_TIMESTAMP ( number )
###### TIMESTAMP_TO_SCN
- TIMESTAMP_TO_SCN ( timestamp )
###### TO_CHAR
####### TO_CHAR(文字)
####### TO_CHAR(日時)
###### TO_TIMESTAMP
##### ラージオブジェクトファンクション
##### 階層ファンクション
##### データ・マイニング・ファンクション
##### XMLファンクション
###### EXTRACTVALUE
- 非推奨。下位互換のためにサポートされている。
  XMLTABLE, XMLCASTおよびXMLQUERYを使用する。
####### Syntax
  EXTRACTVALUE ( XMLType_instance , XPath_string [, namespace_string] )
###### XMLCAST
####### Syntax
- XMLCAST ( value_expression AS datatype )
###### XMLQUERY
- SQL文のXMLデータを問い合わせることができる。
  文字列リテラル、オプションのコンテキスト項目、および他のバインド変数としてXQuery式を取り、これらの入力値を使用してXQuery式の評価結果を戻す。
####### Syntax
- Syntax
  XMLQUERY ( XQuery_string [XML_passing_clause] RETURNING CONTENT [NULL ON EMPTY] )
- XML_passing_clause
  PASSING [BY VALUE] {expr [AS identifier]},+
###### XMLTABLE
- XQueryの評価結果をリレーショナル行および列にマップする。
####### Syntax
##### エンコーディングおよびデコーディング・ファンクション
##### NULL関連ファンクション
###### COALESCE
- COALESCE(expr1, ...)
  式リストの最初のNULLでないexprを戻す。2つ以上の指揮を指定する必要がある。
  全てのexprがNULLの場合はNULLを返す。
  
###### NVL
- NVL(expr1, expr2)
  expr1がNULLの場合、expr2を消す。
  expr1, expr2には任意のデータ型を持つことができる。

##### 環境ファンクションおよび識別子ファンクション
#### 集計ファンクション
##### RANK
###### Syntax
- RANK ( expr {,expr}* ) WITHIN GROUP ( ORDER BY expr [DESC|ASC] [NULLS {FIRST|LAST}] [,expr]* )
#### 分析ファンクション
- 行のグループに基づいて集計値を計算する。
  行のグループをウィンドウといい、aanlytic_clauseで定義される。
##### RANK
- 一連の値における値のランクを計算する。戻り値はNUMBER。
###### Syntax
- RANK ( ) OVER ( [query_partition_clause] order_by_clause )
### 式
### 条件
### SQL文
#### Object
##### CLUSTER
- クラスタとは、1つ以上の表データが含まれているスキーマ・オブジェクトのこと。
  結合処理のパフォーマンスを向上させるために使用されるデータ構造で、複数の表を結合した状態でデータベースに格納する。
###### ALTER
###### CREATE
###### DROP
###### TRUNCATE
##### CONTEXT
##### CONSTRAINT[S]
###### SET
##### DATABASE
###### ALTER
####### 構文
######## ALTER DATABASE [database] options
######## options
######### startup_clauses
- 
  データベースをマウントおよびオープンしてアクセス可能にする。


########## MOUNT [{STANDBY | CLONE} DATABASE]
########## OPEN {READ ONLY | [READ WRITE] [RESETLOGS|NORESETLOGS] [UPGRADE|DOWNGRADE]
- READ WRITE
  読み取り/書き込みモードでデータベースがオープンされ、REDOログを生成できるようになる。
- RESETLOGS | NORESETLOGS
  現行のログ順序番号を1にリセットし、アーカイブされていないログ(現行のログを含む)をアーカイブして、リカバリ時に適用されなかったREDO情報を今後適用されないように破棄するかどうかを指定する。
  RESETLOGが必要な次の場合を除き、NORESETLOGSを自動的に使用する。
  - RESETLOGSを指定する必要がある場合：
    - 不完全メディア・リカバリ、またはバックアップ制御ファイルを使用してメディアリカバリを実行した後
    - 前回の不完全なOPEN RESETLOGS操作後
    - FLASHBACK DATABASE処理後
  作成した制御ファイルをマウントした場合、オンライン・ログが失われた場合RESETLOGS、失われていない場合NORESETLOGSを指定する必要がある。
######### recovery_clauses
######### alter_datafile_clause
- DATAFILE
  - (filename | filenumber)
    - RESIZE size_clause

###### CREATE
- CREATE DATABASE
  汎用的なデータベースを作成する。
  この文を実行すると、指定した既存のデータファイル上のデータがすべて消去される。
  
####### 構文
######## CREATE DATABASE [database] options... ;
######## options
######### USER [SYS|SYSTEM] IDENTIFIED BY password
######### MAXDATAFILES integer
- CREATE DATABASEまたはCREATE CONTROLFILE実行時の、制御ファイルのデータファイル・セクションの初期サイズを指定する。
  
######### MAXINSTANCES integer
- データベースを同時にマウントおよびオープンできる最大値。
######### CHARACTER SET charset
- データベースにデータを格納するときのキャラクタ・セットを指定する。
  サポートされているキャラクタセットおよびこのパラメータのデフォルト値はOSによって異なる。
  AL16UTF16はデータベース・キャラクタ・セットとして指定できない。
######### NATIONAL CHARACTER SET charset
- データ型がNCHAR、NCLOBｍたはNVARCHAR2として定義された列にデータを格納する際に使用する各国語キャラクタ・セットを指定する。
  有効値はAL16UTF16及びUTF8。デフォルトはAL16UTF16。
######### database_logging_clauses
########## LOGFILE [GROUP integer] file_specification (, GROUP integer...)
########## MAXLOGFILES integer
- データベースに対し作成可能なREDOログファイルグループの最大数を指定する。
########## MAXLOGMEMBERS integer
- REDOログ・ファイル・グループのメンバー（コピー）の最大数を指定する。
  最小値は1。最大値およびデフォルトはOSにより異なる。
########## MAXLOGHISTORY integer
- 自動メディア・リカバリに使用するアーカイブREDOログ・ファイルの最大数を指定する。
  最小値は0。デフォルト値はMAXINSTANCES値の倍数で、OSによって異なる。最大値は制御ファイルの最大サイズ制限のみを受ける。
  有用なのはOracle RACでARCHIVELOGモードで使用している場合のみ。
########## ARCHIVELOG | NOARCHIVELOG
########## FORCE LOGGING
######### tablespace_clauses
########## EXTENT MANAGEMENT LOCAL
########## DATAFILE file_specification(, ...)
########## SYSAUX DATAFILE file_specification(, ...)
- SYSAUX表領域の1つ以上のデータファイルを指定する場合、この句を使用する。
########## DEFAULT TABLESPACE tablespace [DATAFILE datafile_tempfile_spec] [extent_management_clause]
########## [BIGFILE | SMALLFILE] DEFAULT TEMPORARY TABLESPACE tablespace [TEMPFILE file_specification(, ...)] [extent_management_clause]
########## [BIGFILE | SMALLFILE] UNDO TABLESPACE tablespace [DATAFILE file_specification(, ...)]
######### set_time_zone_clause
###### DROP
- ターゲット・データベースを削除する。RMANプロンプトのみで実行する。
  ターゲットデータベースが排他的にマウントされ、オープンされていない状態で、RESTRICTモードで起動されている必要がある。
####### 構文
######## DROPDATABASE [INCLUDING BACKUPS] [NOPROMPT];
####### 用例
- RMAN> CONNECT TARGET SYS@test1
  RMAN> STARTUP FORCE MOUNT
  RMAN> SQL 'ALTER SYSTEM ENABLE RESTRICTED SESSION';
  RMAN> DROP DATABASE INCLUDING BACKUPS NOPROMPT;
###### FLASHBACK
##### DATABASE LINK
##### DIRECTORY
###### CREATE
###### DROP
####### 構文
- DROP DIRECTORY directory_name ;
##### DIMENSION
##### DISKGROUP
##### EDITION
##### FLASHBACK ARCHIVE
###### ALTER
###### CREATE
###### DROP
##### FUNCTION
- PL/SQL
###### CREATE
- CREATE (OR REPLACE) FUNCTION
  - (schema.) function name
    - RETURN datatype
      ファンクションの戻り値のデータ型を指定する。
####### parallel_enable_clause
- PARALLEL_ENABLE 
  - ( (PARITION argument BY ... ) )

- 
  パラレル問い合わせ操作のパラレル実行サーバーからファンクションを実行できることを示す。
  パッケージ変数などのセッション状態は使用しないようにする。
####### AGGREGATE USING
- AGGREGATE USING (schema.)implementation_type
  集計ファンクションまたは行のグループを評価して単一行を戻すファンクションとして使用する。
  
###### ALTER
###### DROP
##### INDEX
##### INDEXTYPE
##### LIBRARY
##### MATERIALIZED VIEW
##### OUTLINE
##### PACKAGE
- PL/SQL
###### CREATE
###### DROP
- DROP PACKAGEは、データベースから仕様と本体の両方を削除する。

###### ALTER
##### PACKAGE BODY
###### CREATE
###### DROP
- 本体のみを削除する。

##### PFILE, SPFILE
###### CREATE
- tmp
  - [[https://docs.oracle.com/cd/E16338_01/server.112/b56299/statements_6008.htm#i2072768][CREATE PFILE]]
  - [[https://docs.oracle.com/cd/E16338_01/server.112/b56299/statements_6016.htm#i2072626][CREATE SPFILE]]
##### PROCEDURE
- PL/SQL
###### CREATE
- CREATE (OR REPLACE) PROCEDURE plsql_source
###### ALTER
###### DROP

##### PROFILE
###### CREATE
####### 構文
######## CREATE PROFILE profile LIMIT (resource_parameters | password_parameters);
######## resource_parameters
######### SESSION_PER_USER [integer|UNLIMITED|DEFAULT]
- ユーザーを制限する同時セッションの数を指定する。
######### CPU_PER_SESSION [integer|UNLIMITED|DEFAULT]
- 1セッションあたりのCPU時間制限を指定する。100分の1秒単位。
######### CPU_PER_CALL [integer|UNLIMITED|DEFAULT]
- 1コールあたりのCPU時間制限を指定する。100分の1秒単位。
######### CONNECT_TIME [integer|UNLIMITED|DEFAULT]
- 1セッション辺りの合計経過時間制限を指定する。分単位。
######### IDLE_TIME [integer|UNLIMITED|DEFAULT]
- セッション中の連続的な日活動時間の長さを制限する。
######### LOGICAL_READS_PER_SESSION [integer|UNLIMITED|DEFAULT]
- メモリー及びディスクから読み込まれるブロックなど、1セッション中に読み込まれるデータ・ブロックの数の制限を指定する。
######### LOGICAL_READS_PER_CALL [integer|UNLIMITED|DEFAULT]
- SQL文を処理する1つのコールで読み込まれるデータ・ブロックの数の制限を指定する。
######### COMPOSITE_LIMIT [integer|UNLIMITED|DEFAULT]
- 1セッションあたりのリソースの総コストをサービス単位で指定する。
######### PRIVATE_SGA [size_clause|UNLIMITED|DEFAULT]
- 1つのセッションでシステム・グローバル領域(SGA)の共有プール内に割り当てることができるプライベート領域の大きさを指定する。
######## password_parameters
######### FAILED_LOGIN_ATTEMPTS [exr|UNLIMITED|DEFAULT]
- ユーザー・アカウントがロックされる前にそのアカウントへのログインに連続して失敗できる回数を指定する。
######### PASSWORD_LIFE_TIME [exr|UNLIMITED|DEFAULT]
- 同じパスワードを認証に使用できる日数を制限する。
######### PASSWORD_REUSE_TIME [exr|UNLIMITED|DEFAULT]
- パスワードを再利用できない日数を指定する。
  PASSWORD_REUSE_MAXと組み合わせて設定する必要がある。
######### PASSWORD_REUSE_MAX [exr|UNLIMITED|DEFAULT]
- 現行のパスワードを再利用する前に必要な、パスワードの変更回数を指定する。
  PASSWORD_REUSE_TIMEと組み合わせて設定する必要がある。
######### PASSWORD_LOCK_TIME [exr|UNLIMITED|DEFAULT]
- ログインが指定された回数連続して失敗した場合、アカウントがロックされる日数を指定する。
  デフォルトは1日。
######### PASSWORD_GRACE_TIME [exr|UNLIMITED|DEFAULT]
- ログインが許可される猶予期間の日数を指定する。7日がデフォルト。
######### PASSWORD_VERIFY_FUNCTION [function|UNLIMITED|DEFAULT]****** ALTER
- 
  プロファイルのリソース制限またはパスワード管理パラメータを追加、変更または削除できる。
  変更は現行のセッションのユーザーには影響せず、後続セッションのユーザーのみに影響する。

- パスワード検証スクリプトを引数として渡すことができる。
###### ALTER
####### 構文
######## ALTER PROFILE profile LIMIT (resource_parameters | password_parameters);
######## resource_parameters
######### SESSION_PER_USER [integer|UNLIMITED|DEFAULT]
######### CPU_PER_SESSION [integer|UNLIMITED|DEFAULT]
######### CPU_PER_CALL [integer|UNLIMITED|DEFAULT]
######### CONNECT_TIME [integer|UNLIMITED|DEFAULT]
######### IDLE_TIME [integer|UNLIMITED|DEFAULT]
######### LOGICAL_READS_PER_SESSION [integer|UNLIMITED|DEFAULT]
######### LOGICAL_READS_PER_CALL [integer|UNLIMITED|DEFAULT]
######### COMPOSITE_LIMIT [integer|UNLIMITED|DEFAULT]
######### PRIVATE_SGA [size_clause|UNLIMITED|DEFAULT]
######## password_parameters
######### FAILED_LOGIN_ATTEMPTS [exr|UNLIMITED|DEFAULT]
######### PASSWORD_LIFE_TIME [exr|UNLIMITED|DEFAULT]
######### PASSWORD_REUSE_TIME [exr|UNLIMITED|DEFAULT]
######### PASSWORD_REUSE_MAX [exr|UNLIMITED|DEFAULT]
######### PASSWORD_LOCK_TIME [exr|UNLIMITED|DEFAULT]
######### PASSWORD_GRACE_TIME [exr|UNLIMITED|DEFAULT]
######### PASSWORD_VERIFY_FUNCTION [function|UNLIMITED|DEFAULT]
###### DROP
##### RESTORE POINT
###### CREATE
###### DROP
##### ROLE
###### CREATE
###### SET
##### SEQUENCE
###### CREATE
- CREATE SEQUENCE (schema.) sequence
  
###### ALTER
###### DROP
##### SYNONYM
###### CREATE
- CREATE [OR REPLACE] [PUBLIC] SYNONYM syn_name FOR schema_name.object_name;
- OR REPLACE
  同名のシノニムが存在した場合でも構わず上書きする場合に指定する
- PUBLIC
  パブリックシノニムを作成する場合に指定

###### DROP
- DROP [PUBLIC] SYNONYM syn_name;

###### RENAME
- RENAME old_syn_name TO new_syn_name
- PUBLICはRENAME不可。
##### SYSTEM
###### ALTER
####### 構文
######## ALETR SYSTEM options;
######## options
######### archive_log_clause
######### CHECKPOINT [GLOBAL | LOCAL]
######### CHECK DATAFILES [GLOBAL | LOCAL]
######### [ENABLE | DISABLE] DISTRIBUTED RECOVERY
######### FLUSH {SHARED_POOL | GLOBAL CONTEXT | BUFFER_CACHE | REDO TO target_db_name [[NO] CONFIRM APPLY]}
######### end_session_clauses
########## DISCONNECT SESSION 'integer1, integer2' [POST TRANSACTION] IMMEDIATE
########## KILL SESSION 'integer1, integer2 [, @integer3]' IMMEDIATE
######### SWITCH LOGFILE
######### {SUSPEND | RESUME}
######### quiesce_clauses
########## QUISCE RESTRICTED
########## UNQUIESCE
######### rolling_migration_clauses
######### security_clauses
######### SHUTDOWN [IMMEDIATE] dispatcher_name
######### REGISTER
######### SET alter_system_set_clause
######### REEST alter_system_set_clause
##### TABLE
###### CREATE
####### 構文
######## CREATE [ GLOBAL TEMPORARY ] TABLE [ scehma ] . table { relational_table | object_table | XMLType_table } ;
######## relational_table
######### [ ( relational properties ) ] [ ON COMMIT { DELETE | PRESERVE } ROWS ] [ physical_properties ] [ table_properties ]
######## object_table
######## XMLType_table
######## segment_attributes_clause
- physical_attributes_clause
- TABLESPACE tablespace
  表領域を指定する。
- logging_clause
  表、および制約のために必要な索引、パーティションまたはLOBの記憶特性を、
  REDOログファイルに記録する(LOGGING)かしないか(NOLOGGING)を指定する。
  - LOGGING
  - NOLOGGING
  - FILESYSTEM_LIKE_LOGGING
######## physical_attributes_clause
- PCTFREE
  データブロックに、更新のために残しておく領域の割合。デフォルトは10。0から99の正の整数。
- PCTUSED
  デフォルトは40。0から99の正の整数。
- INITRANS
  各データブロックに割り当てられる、同時実行トランザクション・エントリの初期数。
  値の範囲は1から255で、デフォルトは1。通常は変更せずデフォルトで使用するようにする。
- MAXTRANS
  同時実行可能な同時実行更新トランザクションの最大数を決定する。以前のリリースのパラメータ。
  現在は非推奨。
######## storage_clause
- STORAGE
  - INITIAL
    オブジェクトの第1エクステントのサイズを指定する。
  - FREELISTS
    最小値（デフォルト）は1。
  - FLEELIST GROUPS
    最小値（デフォルト）は1。
  - BUFFER_POOL
    - KEEP
    - RECYCLE
    - DEFAULT
######## table_compression
- 概要
  ヒープ構成表に対してのみ有効。
  ディスク使用量を削減するためにデータ・セグメントを圧縮するかどうかを指定できる。
  COMPRESSを指定すると、表の圧縮が使用可能となる。
  NOCOMPRESSを指定すると、表の圧縮が使用禁止となる。デフォルトはNOCOMPRESS。

- COMPRESS
  - BASIC
  - FOR
    - OLTP
    - QUERY | ARCHIVE
      - LOW | HIGH
- NOCOMPRESS
###### ALTER
- ALTER TABLE [schema.]table options enable_disables;
####### options
######## alter_table_properties
######### RENAME TO new_table_name
######## column_clauses
######## constraint_clauses
######## alter_table_partitioning
######### modify_table_tefault_attrs
######### alter_interval_partitioning
######### set_subpartition_template
######### move_table_partition
########## About
- partitionを別のセグメントへ移動できる。
  
########## MOVE partition_extended_name [MAPPING TABLE] [table_partition_description] [update_index_clauses] [parallel_clause]
########### partition_extended_name
############ {PARTITION partition} | {PARTITION FOR "(" {partition_key_value},+ ")" }
######### move_table_subpartition
######## alter_external_table
######## move_table_clause
######### MOVE [ONLINE] [segment_attributes_clause] [table_compression] [index_org_table_clause] {[LOB_storage_clause] | [varray_col_properties]}* [parallel_clause]
####### enable_disables
######## enable_disable_clause
######## [ENABLE|DISABLE] [TABLE LOCK | ALL TRIGGERS]
####### memo
######## add
- 
  - PKの作成
    ADD [CONSTRAINT primary_key_name] PRIMARY KEY (col1, col2, ..) ;
    PK名を省略した場合、PK_tablenameとなる模様。
######## drop_constraint_clause
- PRIMARY KEY
- UNIQUE
- 
  - PKの削除
    - ALTER TABLE table_name DROP PRIMARY KEY;
    - ALTER TABLE table_name DROP CONSTRAINT primary_key_name;
######## log
- LOGGING
  REDOログ記録をONに変更する
- NOLOGGING
  REDOログ記録をOFFに変更する
###### FLASHBACK
###### LOCK
##### TABLESPACE
###### CREATE
####### permanent_tablespace
- BLOCKSIZE
  非標準ブロックサイズを指定する場合に使用する。
- ONLINE | OFFLINE
  表形式がオンラインまたはオフラインのいずれかであるかを決定できる。
  - ONLINE : 表領域にアクセス権限があるユーザに対し、作成直後の表領域を使用可能にする。デフォルト。
  - OFFLINE : 作成直後の表領域を使用禁止にできる。

####### temporary_tablespace
- 
  ローカル管理一時表領域を作成できる。
  一時表領域は、セッションの存続期間中にのみ保持される一時データを格納できるデータベース内の領域割り当て。
  一次データとは、一次表などのユーザ生成スキーマ・オブジェクト、またはハッシュ結合およびソート操作で一次領域などのシステム生成データ。

- TEMPORARY TABLESPACE tablespace
  ソート処理専用の一時表領域として作成する。

  - TEMPFILE file_specification

####### undo_tablespace
- UNDO TABLESPACE tablespace
  UNDO表領域を作成する。自動UNDO管理モードでデータベースを実行する場合、ロールバック・セグメントの代わりにUNDO表領域を使用してUNDO領域を管理する。
  
####### extent_management
- 構文
  EXTENT MANAGEMENT LOCAL [AUTOALLOCATE | UNIFORM [SIZE size_clause]]

- 項
  - AUTOALLOCATE
    表領域がシステム管理される。
  - UNIFORM
    表領域をSIZEバイトの均一のエクステントで管理できる。デフォルトは1MB。
    一次表領域のすべてのエクステントはサイズが均一であるため、このキーワードは一次表領域ではオプション扱い。
    ただし、SIZEを指定する場合はUNIFORMを指定する必要がある。
    UNDO領域に指定することはできない。
    - SIZE size_clause | 

####### segment_management
- SEGEMNT SPACE MANAGEMENT
  - AUTO
    ビットマップを使用して表領域のセグメントにある空き領域を管理できる。
  - MANUAL
    空きリストを使用して表領域のセグメントにある空き領域を管理できる。
    この設定は使用せず、AUTOを利用することを強く勧める。
####### file_specification
- datafile_tempfile_spec | redo_log_file_spec
######## datafile_tempfile_spec
- 構文
  ['(filename | ASM filename)'] [SIZE size_clause] [REUSE] [autoextend_clause]

- 項
  - SIZE句
    ファイルのサイズをバイト単位で指定する。K,M,G,Tを使用して単位の指定も可能。
  - REUSE
    既存ファイルの再利用を可能にする。filenameを指定しない限り、指定不可。
######## redo_log_file_spec
######## autoextend_clause
- AUTOEXTEND (OFF | ON [NEXT size_clause] [maxsize_clause])
###### ALTER
- 例
  - データファイルの追加
    ALTER TABLESPACE DAT01 ADD DATAFILE 'home/db/DAT01_02.dbf' size 2000M;

###### DROP
- DROP TABLESPACE tablespace
  - INCLUDING CONTENTS
    表領域の中のすべてのデータベース・オブジェクトを削除できる。
    表領域がから出ない場合にこの句を省略した場合、エラーがもどされ、表領域は削除されない。
    - AND DATAFILES
      関連するOSファイルも削除できる。
    - KEEP DATAFILES
      OSファイルはそのままにしておく。
    - CASCADE CONSTRAINTS
      tablespaceに含まれる表の主キーまたは一意キーを参照する、tablespace外のすべての参照整合性制約を削除する。
      
##### TRANSACTION
###### SET
##### TRIGGER
- PL/SQL
##### TYPE
- PL/SQL
##### USER
###### CREATE
-
####### 構文
######## CREATE USER user IDENTIFIED id_clause option_clause*
######## id_clause
######### BY password
######### EXTERNALLY [ AS ' { certificate_DN | kerberos_principal_name } ' ]
######### GLOBALLY [ AS ' [ directory_DN ] ' ]
######## option_clause
######### DEFAULT TABLESPACE tablespace
######### TEMPORARY TABLESPACE { tablespace | tablespace_group_name }
######### ( QUOTA { size_clause | UNLIMITED } ON tablespace ) *
######### PROFILE profile
######### PASSWORD EXPIRE
######### ACCOUNT { LOCK | UNLOCK }
######### ENABLE EDITIONS
###### ALTER
- DEFAULT ROLE
  ログイン時にデフォルトによってユーザに付与されるロールを指定する。
  GRANT文を使用してユーザに付与されているロール、またはCREATE ROLE権限を持つユーザが作成したロールのみ指定可能。

####### 構文

######## ALTER USER {user options | user[, ...] proxy_clause}
######## options
######### IDENTIFIED BY password []
######### IDENTIFIED EXTERNALLY []
######### IDENTIFIED GLOBBALY []
######### DEFAULT TABLESPACE tablespace
######### TEMPORARY TABLESPACE [tablespace | tablespace_group_name]
######### QUOTA []
######### PROFILE profile
######### DEFAULT ROLE {}
######### PASSWORD EXPIRE
######### ACCOUNT {LOCK | UNLOKC}
######### ENABLE EDITIONS [FORCE]
######## proxy_clause
###### DROP
- DROP USER user
  - CASCADE

##### VIEW
#### Etc
##### DELETE
##### GRANT
###### System Privileges
####### システム権限
######## アドバイザ・フレームワーク権限
######### ADVISOR
- PL/SQLパッケージ(DBMS_ADVISORやDBMSSQLTUNEなど)を介したアドバイザ・フレームワークへのアクセス。
######### ADMINISTER SQL TUNING SET
########## ADMINISTER SQL TUNING SET
- DBMS_SQLTUNEパッケージを介した、権限受領者が所有するSQLチューニング・セットの作成、削除、選択（読み取り）およびロード（書き込み）
########## ADMINISTER ANY SQL TUNING SET
######### SQL PROFILE
########## CREATE ANY SQL PROFILE 
########## ALTER ANY SQL PROFILE
########## DROP ANY SQL PROFILE
######## CLUSTER
######### CREATE CLUSTER
######### CREATE ANY CLUSTER
######### ALTER ANY CLUSTER
######### DROP ANY CLUSTER
######## CONTEXT
######### CREATE ANY CONTEXT
######### DROP ANY CONTEXT
######## DATA REDACTION
######### EXEMPT REDACTION POLICY
######## DATABASE
######### ALTER DATABASE
######### ALTER SYSTEM
######### AUDIT SYSTEM
######## DATABASE LINK
######### CREATE DATABASE LINK
######### CREATE PUBLIC DATABASE LINK
######### ALTER DATABASE LINK
######### ALTER PUBLIC DATABASE LINK
######### DROP PUBLIC DATABASE LINK
######## DEBUGGING
######### DEBUG CONNECT SESSION
######### DEBUG ANY PROCEDURE
######## DICTIONARIES
######### ANALYZE ANY DICTIONARY
######## DIMENSIONS
######### CREATE DIMENSION
######### CREATE ANY DIMENSION
######### ALTER ANY DIMENSION
######### DROP ANY DIMENSION
######## DICTIONARIES
######### CREATE ANY DICTIONARY
######### DROP ANY DICTIONARY
######## EDITIONS
######### CREATE ANY EDITION
######### DROP ANY EDITION
######## FLASHBACK DATA ARCHIVES
######## INDEXES
######## INDEXTYPES
######## JOB SCHEDULER OBJECTS
######## LIBRARIES
######## MATERIALIZED VIEWS
######## MINING MODEL
######## OLAP CUBE
######## OLAP CUBE MEASURE FOLDEL
######## その他
######### SELECT_CATALOG_ROLE
######### UNLIMITED TABLESPACE
###### Object Privileges
####### DIRECTORY
####### EDITION
####### INDEX
####### 
###### 構文
####### GRANT [ grant_system_privileges | grant_object_privileges ] ;

####### grant_system_privileges
######## { system_privilege | role | ALL PRIVILEGES } ,* TO grantee_clause [ WITH ADMIN OPTION ]
####### grant_object_privileges
######## ( { object_privilege | ALL [PRIVILEGES ] } [ ( column ,* ) ] ) ,* on_object_clause TO grantee_clause [ WITH HIERARCHY OPTION ] [ WITH GRANT OPTION ]
####### on_object_clause
####### grantee_clause
######## user [IDENTIFIED BY password]
######## role
######## PUBLIC
##### INSERT
##### MERGE
##### NOAUDIT
##### PURGE
##### RENAME
##### REVOKE
##### ROLLBACK
##### SAVEPOINT
##### SELECT
###### 構文
####### subquery [for_update_clause] ;
####### subquery
######## {query_block | subquery { UNION [ALL] | INTERSECT | MINUS } subquery | ( subquery ) } [order_by_clause]
####### query_block
######## [subquery_factoring_clause] SELECT [hint] [ { ALL | DISTINCT | UNIQUE } ] select_list FROM
####### flashback_query_clause
######## VERSIONS BETWEEN { SCN | TIMESTAMP } { expr | MINVALUE } AND { expr | MAXVALUE }
######## AS OF { SCN | TIMESTAMP } expr
- 特定のシステム変更番号(SCN)またはタイムスタンプでの問合せによって戻された行の
##### UPDATE
## Link
### SQL言語
- [[https://docs.oracle.com/cd/E16338_01/server.112/b56299/toc.htm][Oracle® Database SQL言語リファレンス 11gリリース2]]
