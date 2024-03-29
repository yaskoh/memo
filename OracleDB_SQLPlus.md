# Oracle SQL*Plus
## About
- 入力
  次の3タイプのコマンドが入力可能。
  - SQLコマンド
  - PL/SQLブロック
  - SQL*Plusコマンド
  
## Syntax
- SQLPLUS [ [Options] [Logon|/NOLOG] [Start] ]
### Options
- - H[ELP] | -V[ERSION] | 
  [[-C[OMPATIBILITY] [x.y[.z]] [-L[OGON]] [-M[ARKUP] markup_option] [-R[ESTRICT] {1|2|3}] [-S[ILENT]] ]
#### HELP
#### VERSION
#### COMPATIBILITY
#### LOGON
#### MARKUP
#### RESTRICT
#### SILENT
### Logon
- {username[/password][@connect_identifier]| / } [AS {SYSOPER|SYSDBA|SYSASM}] [edition=value]
### /NOLOG
- データベースに接続せず、SQL*Plusを起動できる。
### Start
- @{url|file_name[.ext]} [arg ...]
## SQLコマンドの終了
- 
  - セミコロン(;)を入力する
  - 1行にスラッシュ(/)のみを1つ入力する
  - 空白行を入力する
## Scriptの使用
### Variables 変数
#### 置換変数
##### 定義
- DEFINE varname
- ACCEPT ~
- 削除
  UNDEFINE varname
##### 利用
###### &置換変数
- &VARNAME、で指定の値に置き換えられ、SQL実行される。
  例: where deptno = &deptno
- VERIFY変数
  OFFにすると、置換変数の置き換え前後の値が表示されなくなる。
  例: SET VERIFY OFF
  
###### &&置換変数
- &&変数は、SQL実行後も値が保持される。
  対して、&置換変数で置き換えられた値はSQL実行後に破棄される。
  DEFINEコマンドで確認し、UNDEFINEコマンドで破棄する。

###### 無効化
- 置換変数を無効にする
  SET DEFINE OFF
- 置換変数を他の文字に変更することなども可能(SET ESCAPE c)。
##### 種類
###### ユーザー定義変数
###### 事前定義変数
####### _CONNECT_IDENTIFIER
- 可能な宛先への接続に使用される接続識別子
####### _DATE
- 動的変数としての現在の日付、またはユーザー定義の固定文字列が含まれる。
####### _EDITOR
- EDITコマンドで使用されるエディタを指定
####### _O_VERSION
- インストールされたOracle Databaseの現行のバージョン
####### _O_RELEASE
- インストールされたOracle Databaseの完全なリリース番号
####### _PRIVILEGE
- 現在の接続での権限レベル。次のいずれかの値となる。
  - AS SYSASM
  - AS SYSBACKUP
  - AS SYSDBA
  - AS SYSDG
  - AS SYSOPER
  - 空文字(通常のユーザー接続)
####### _SQLPLUS_RELEASE
- インストールされたSQL*Plusコンポーネントの完全なリリース番号
####### _USER
- 接続に使用されるユーザー名
#### バインド変数
- 
  SQL*PlusとPL/SQLの双方で参照できる変数。
  PL/SQLに値を渡したり、結果を受け取ったりできる。
  "var[iable] 変数名 型"で宣言する。
  
- PL/SQL
  変数名の前に:(コロン)を付けて参照したり値を格納できる。
  :count:=3;
  
- SQL*Plus
  PRINTコマンドで出力可能。

## Variables
- SQL*Plusに影響するパラメータ・環境変数
### LD_LIBRARY_PATH
### LOCAL
### NLS_LANG
- グローバリゼーション機能を指定する環境変数。
  NLSはNational Language Supportの略。
  "language_territory.charset"を指定する。
  例: JAPANESE_JAPAN.UTF8, AMERICAN_AMERICA.UTF8

### ORACLE_HOME
### ORACLE_PATH
### ORACLE_SID
### PATH
### SQLPATH
## Commands
### @
- 指定したスクリプトのSQL*Plus文を実行する。
### /
- 最後に実行されたSQLコマンドまたはSQLバッファに格納されているPL/SQLブロックを実行する。
### ;
- バッファの内容を表示する。L(IST)と同様。
### !
- unix系でのHO[ST]コマンド実行の短縮形。
### ACCEPT
- 構文
  ACC[EPT] variable 
    [NUM[BER] | CHAR | DATE | BINARY_FLOAT | BINARY_DOUBLE]
    [FOR[MAT] foramt]
    [DEF[AULT] default]
    [PROMPT text|NOPR[OMPT]]
    [HIDE]

- 項
  - variable
    値を格納する変数の名前を指定する。variableを指定しない場合、SQL*Plusによって変数が指定される。

  - Type
    - NUM[BER]
      variableがNUMBERデータ型に設定される。
    - CHAR
      variableがCHARデータ型に設定される。

  - Prompt
    - PROMPT text
      variableの値を受け入れる前に、画面にテキストtextを表示する。
    - NOPROMPT
      - プロンプトを表示せずに入力を待つ

  - HIDE
    - 入力された応答が表示されない。

### APPEND
- A[PPEND] text
  textで指定したテキストをSQLバッファ内のカレント行の終わりに追加する。
### ARCHIVE LOG
- ARCIVE LOG LIST
  REDOログファイルに関する情報を表示する
### ATTRIBUTE
### BREAK
### BTITLE
### CHANGE
- C[HANGE] sephcar old [sepchar [new [sepchar]]]
  バッファ内のカレント行で最初に一致した文字列を変更する。
### CLEAR
- CL[EAR] option...
- 指定したオプションの現行の値または設定をリセットまたは消去する
#### options
##### BRE[AKS]
- ブレーク定義が取り消される。
##### BUFF[ER]
- バッファからテキストが消去される。複数バッファを使用しない場合はCLEAR SQLと同じ。
##### COL[UMNS]
- すべての列について、COLUMNコマンドで設定した列表示属性がデフォルトにリセットされる。
##### COMP[UTES]
- COMPETE定義が取り消される。
##### SCR[EEN]
- 画面が消去される
##### SQL
- SQLバッファからテキストが消去される。複数バッファを使用しない限り、CLEAR BUFFERと同じ動きとなる。
### COLUMN
- COL[UMN] [{column | expr} [option ...]]
#### options
##### ALI[AS] alias
##### CLE{AR}
##### ENTMAP {ON|OFF}
##### FOLD_A[FTER]
##### FOLD_B[EFORE]
##### FOR[MAT] format
- format
  - aNNN : 桁数を指定する（バイト数）
  - ex)
    col column1 for a20
    col column2 for 999,990.9
##### HEA[DING] text
##### JUS[TIFY] {L[EFT] | C[ENTER] | R[IGHT]}
##### LIKE {expr | alias}
##### NEWL[INE]
##### NEW_V[ALUE] variable
##### NOPRI[NT] | PRI[NT]
##### NUL[L] text
##### OLD_V[ALUE] variable
##### ON | OFF
##### WRA[PPED]
##### WOR[D_WRAPPED]
##### TRU[NCATED]
### COMPUTE
### CONNECT
- 
  指定したユーザ-名でOracle Databaseに接続する。

- 構文
  CONN[ECT] [{logon|/|proxy} [AS {SYSOPER|SYSDBA|SYSASM}] [edition=value]
  - logon : 
    username[/password]@connect_identifier
  - proxy :
    proxyuser[ username][/password][@connect_identifier]
  
- 項
  - /
    デフォルト・ログオンを表す。

  - AS {SYSOPER|SYSDBA|SYSASM}
    AS句を使用すると、SYSOPER、SYSDBA、またはSYSASMシステム権限が付与されているユーザーによる特権付接続が可能。

### COPY
### DEFINE
- DEF[INE] [variable] | [variable = text]
  ユーザ変数または事前定義変数を指定し、その変数にCHAR値を割り当てたり、1つまたはすべての変数の値および変数型を表示する。

#### 事前定義変数
##### _CONNECT_INDENTIFIER
##### _DATE
##### _EDITOR
- EDITコマンドで使用されるエディタを指定する。
##### _O_VERSION
##### _O_RELEASE
##### _PRIVILEGE
##### _SQLPLUS_RELEASE
##### _USER
### DEL
### DESCRIBE
- DESC[RIBE] objectx
  表、ビュー、ファンクション、プロシージャの定義を表示する。

### DISCONNECT
### EDIT
- ED[IT] [file_name[.ext]]
  file_name[.ext]に指定したファイルの内容又はバッファの内容を対象として、OSのテキストエディタを起動する。
### EXECUTE
### EXIT
- {EXIT | QUIT} [SUCCESS | FAILURE | WARNING | n | variable | :BndVariable] [COMMIT | ROLLBACK]
- 保留中のすべての変更をコミットまたはロールバック、OracleをログアウトしてSQL*Plusを終了し、OSに制御を戻す。
### GET
### HELP
- HELP | ? [topic]
  topicには、COLUMなどのSQL*Plusのヘルプトピックを指定する。
### HOST
- HO[ST]
  続けてOSのコマンドを入力することで、OSのコマンドを実行可能。

- 短縮形
  - !
    Unix系での短縮形。直後にスペースは不要で、続けて入力可能。
  - $
    Windows系での短縮形。

### INPUT
- I[NPUT] [text]
  textの内容をバッファ内のカレント行の後に1行以上の新規コメントを追加する。
  
### LIST
- L[IST] [n|n m|n*|n LAST|*|* n|* LAST|LAST]
  SQLバッファの1つ以上の行を表示する。
  ";"でも同様。
### PASSWORD
### PAUSE
### PRINT
### PROMPT
- PRO[MPT] [text]
  textを画面上表示する
  
### RECOVER
- RECOVER {general | managed | BEGIN BACKUP | END BACKUP}
#### general
- [AUTOMATIC] [FROM location]{ {full_database_recovery | partial_database_recovery | LOGFILE filename}[ {TEST | ALLOW integer CORRUPTION | parallel_clause} [TEST | ALLOW integer CORRUPTION | parallel_clause]...]| CONTINUE [DEFAULT] | CANCEL}
#### full_database_recovery
- [STANDBY] DATABASE [{UNTIL {CANCEL | TIME date | CHANGE integer} | USING BACKUP CONTROLFILE} [UNTIL {CANCEL | TIME date | CHANGE integer} | USING BACKUP CONTROLFILE]...]
#### managed
- MANAGED STANDBY DATABASE recover_clause | cancel_clause | finish_clause
### REMARK
### REPFOOTER
### REPHEADER
### RUN
- R[UN]
  現在SQLバッファに格納されているSQLコマンドまたはPL/SQLブロックを表示して実行する。
### SAVE
- SAV[E] [FILE] file_name[.ext] [CRE[ATE]] | REP[LACE] | APP[END]]
  SQLバッファの内容を、OSのスクリプトに保存する。
### SET
- SET system_variable value
  SQL*Plus環境を変更するシステム変数を設定する。
#### SET AUTOT[RACE] {ON|OFF|TRACE[ONLY]} [EXP[LAIN]] [STAT[ISTICS]]
- 正常に実行されたSQL DML分のレポートを表示する。
  レポートには実行統計および問合せ実行パスを含めることができる。
- Options
  - OFF : トレースレポートが表示されない
  - ON : トレースレポートが表示される
  - TRACEONLY : トレースレポートは表示される。問い合わせデータは存在しても表示しない。
  - EXPLAIN : 実行計画が実行され、問い合わせパスが実行される。
  - STATISTICS : 統計が表示される。

#### SET AUTORECOVERY [ON|OFF]
- ONを指定すると、リカバリ時に必要なREDOログ・ファイルのデフォルトのファイル名を自動的に適用するためにRECOVERコマンドが設定される。
#### SET COLSEP {|text}
- 列出力間のセパレータ文字を設定する。
  変数に空白または句読記号が含まれる場合、シングルクォートで囲む必要がある。
- ex
  - SET COLSEP '|'
#### SET DEF[INE] {&|c|ON|OFF}
- 置換変数の接頭辞として使用する文字を、cに設定する。
  ONまたはOFFによって、置換をするかどうかを設定する。ONを設定するとデフォルトの"&"へボトル。
#### SET ECHO {ON|OFF}
- @、@@またはSTARTを使用して実行するスクリプトでコマンドをエコー表示するかどうかを制御する。
  ONを指定すると、画面にコマンドが表示される。OFFを指定すると、非表示となる。
  対話方式で入力するコマンドまたはOSからリダイレクトするコマンドの表示には影響がない。
  
#### SET EMB[EDDED] {ON|OFF}
- ページのどこから各レポートが始まるかを制御する。
  OFFを指定すると、新しいページの一番上から始まる。
  ONを指定すると、新しいページのどこからでもレポートを開始できる。
- 異なるSQLを1つのページ中に含める/含めない、の制御とのこと。
#### SET ESC[APE] {\|c|ON|OFF}
- エスケープ文字として使用する文字を定義する。
  OFFを指定するとエスケープ文字の定義が解除される。ONを指定すると、使用可能となり、設定値はデフォルトの"\"に戻る。
  
#### SET FEED[BACK] {6|n|ON|OFF}
- スクリプトがn個以上のレコードを選択した場合に、スクリプトから戻されるレコード数を表示する。
  ON/OFFによりこの表示をON/OFFにできる。ONにした場合、nが1に設定される。0を設定する場合、OFFと同義。
  "n row selected."の部分の表示・非表示設定。
- "5行が選択されました"などのメッセージが表示される件数を設定する。
  また、DDLやPL/SQLの応答メッセージもON/OFFで制御される。
  "表が作成されました。"や"PL/SQLプロシージャが正常に完了しました。"など。
#### SET HEA[DING] {ON|OFF}
- レポートへの列ヘッダーの出力を制御する。
  ONを指定すると、列ヘッダーがレポートに出力される。
#### SET NEWP[AGE] {1|n|NONE}
- 各ページの最上部から上部タイトルまでの間に入れる空白行の数を設定。
#### SET LIN[ESIZE]
- 1行に表示する文字の合計数を設定する。
#### SET LONG {80|n}
- BLOB, BFILE, CLOB, lONG, NCLOB, XMLType値を表示、およびLONG値をコピーするため最大幅をバイト単位で設定する。
#### SET LONGC[HUNKSIZE] {80|n}
#### SET PAGES[IZE]
- 各出力ページの行数を設定する。
  0に設定すると、ヘッダ、ブレーク、タイトル、初期空白行およびその他の情報をすべて費用時にできる。
#### SET TERM[OUT] {ON|OFF}
- @、@@またはSTARTを使用して実行するスクリプトの出力表示を制御する。
  ONだと画面表示、OFFだと非表示となる。
#### SET TI[ME] {ON|OFF}
- 現在の時刻表示を制御する。
  プロンプト表示が、"SQL>"から"10:12:53 SQL>"のように変化する。
#### SET TIMI[NG] {ON|OFF}
- タイミング統計の表示を制御する。
  ONを指定すると、それぞれのSQLコマンドまたはPL/SQLブロックが実行される度に、そのタイミング統計が表示される。
  実行後、末尾に"Elapsed: 00:00:00.06"などと経過時間を表示する。
#### SET TRIM[OUT] {ON|OFF}
- それぞれの表示行の終わりに後続の空白を入れるかどうかを指定する。
  ONを指定すると、各行の終わりの空白を削除し、パフォーマンスが向上する。
  スプールには影響しない。
#### SET TRIMS[POOL] {ON|OFF}
- それぞれのスプール行の終わりに後続の空白を入れるかどうかを指定する。
  ONを指定すると、各行の終わりの空白が削除される。
#### SET UND[ERLINE] {-|c|ON|OFF}
- レポートの列ヘッダーに下線を付けるために使用する文字を設定する。
  "ON"を設定するとデフォルトの"-"となる。
#### SET VER[IFY] {ON|OFF}
- 置換変数を値と置き換える前後に、SQL文またはPL/SQLコマンドのテキストをリスト表示するかどうかを制御する。
### SHOW
- SHO[W] option
- SQL*Plusシステム変数の値または現行のSQL*Plus環境を表示する。
#### Options
##### system_variable
- SETで設定する変数を指定する。
##### ALL
##### BTI[TLE]
##### ERR[ORS]
- ERR[ORS] [{FUNCTION | PROCEDURE | PACKAGE | PACKAGEBODY | VIEW | TYPE | TYPE BODY | DIMENSION | JAVA CLASS} [schema.]name]
##### LNO
##### PARAMETERS [parameter_name]
- 1つ以上の初期化パラメータに対して、現行の値を表示する。
  parameter_nameなしで使用すると、すべての初期化パラメータが表示される。
  parameter_nameにより、マッチするパラメータのみ表示される
##### PNO
##### REL[EASE]
##### REPF[OOTER]
##### REPH[EADER]
##### SPOO[L]
##### SGA
##### SPARAMETERS [parameter_name]
##### SQLCODE
##### TTI[TLE]
##### USER
##### XQUERY
### SHUTDOWN
- 
  接続の終了を待つ。

- transactional
  トランザクションが終わるまで待つ。
  トランザクションが終わったら接続を切る。

- immediate
  接続終了をまたず、コミットされていないデータは失われる。
  変更済みデータはデータファイルに書き込まれる。

- abort
  接続終了をまたず、コミットされていないデータは失われる。
  変更済みデータはデータファイルに書き込まれない。
### SPOOL
- 構文
  SPO[OL] [file_name[.ext] [CRE[ATE] | REP[LACE] | APP[END]] | OFF | OUT]
- 項
  - CRE[ATE]
    指定した名前でファイルを新規作成する。
  - REP[LACE]
    デフォルトの動作。既存のファイルの内容を置換する。ファイルが存在しない場合、ファイルが作成される。
  - APP[END]
    指定したファイルの終わりに、バッファの内容を追加する
  - OFF
    スプールを停止する。
  - OUT
    スプールを停止して、ファイルをコンピュータの標準プリンタに送る。
  - (指定なし)
    現行のスプール状態を表示する。

### START
### STARTUP
- 
  SQL*Plusを起動する

- 構文
  - STARTUP options | upgrade_options
  - options :
    [FORCE] [RESTRICT] [PFILE=filename] [QUIET] [MOUNT [dbname] | [OPEN [open_options] [dbname]] | NOMOUNT ]
  - open_options :
    READ {ONLY | WRITE [RECOVER]} | RECOVER
  - upgrade_options :
    [PFILE=filename] {UPGRADE | DOWNGRADE} [QUIET]

- 項
  - FORCE
    再起動する前に現行のインスタンスをABORTモードのSHUTDOWNで停止しておく必要があり、現在のインスタンスが実行されている場合はエラーとなる。
    FORCEが指定されている場合は実行される。デバッグ中及び異常な環境下で有効なオプションで、通常は仕様を控えるべき。
  - PFILE=filename
    インスタンスの起動中に使用されるクライアント・パラメータ・ファイルを指定する。
    PFILEの指定を省略すると、デフォルトのサーバー・パラメータ・ファイル(spfile)にアクセスしようとする。spfileが見つからないとデフォルトのpfileにアクセスしようとする。
    デフォルトファイルはプラットフォーム固有でhとなる。
    例 : UNIX : $ORACLE_HOME/dbs/init$ORACLE_SID.ora、Windows : ORACLE_HOME\database\initORCL.ora
    
  - Mount
    - MOUNT dbname
      オープンしないでマウントする。
    - OPEN
      マウントおよびオープンする。
    - NOMOUNT
      停止状態からNOMOUNT状態になる。
      MOUNTまたはOPENと同時には指定できない。
      その後変更する場合は、alter database mount; alter database open;など。

### STORE
### TIMING
### TTITLE
### UNDEFINE
### VARIABLE
- VAR[IABLE] [variable [type]]
  引数なしでVARIABLEを指定すると、セッション内で宣言されているすべての変数が表示される。
  変数名のみを指定すると、その変数が表示される。
  
  ストアドプロシージャに対するパラメータとして使用される。また、無名PL/SQLブロックの中で直接参照できる。

### WHENEVER OSERROR
- 
  OSのエラーが発生した場合に、指定した操作を実行する。
- 構文
  - WHENEVER OSERROR {EXIT [SUCCESS|FAILURE|n|variable|:BindVariable] [COMMIT|ROLLBACK] | CONTINUE [COMMIT|ROLLBACK|NONE]}
- 項
  - EXIT [SUCCESS|FAILURE|n|variable|:BindVariable]
    エラーが検出されたらすぐに終了するように指定する。
  - CONTINUE
    EXITオプションをオフにする。
  - 動作
    - COMMIT
      終了または継続する前にCOMMITを実行し、データベースに対する保留中の変更を保存するように指示する。
    - ROLLBACK
      終了前にROLLBACKを実行するようにする。
    - NONE
      何の操作もしない。
### WHENEVER SQLERROR
- SQLコマンドまたはPL/SQLブロックでエラーが発生した場合に、指定した操作を実行する。
- 構文
  WHENEVER SQLERROR {EXIT [SUCCESS|FAILURE|WARNING|n|visible|:BindVariable] [COMMIT|ROLLBACK] | CONTINUE [COMMIT|ROLLBACK|NONE]}
- 項
  - EXIT [SUCCESS|FAILURE|n|variable|:BindVariable]
    エラーが検出されたらすぐに終了するように指定する。
  - CONTINUE
    EXITオプションをオフにする。
  - 動作
    - COMMIT
      終了または継続する前にCOMMITを実行し、データベースに対する保留中の変更を保存するように指示する。
    - ROLLBACK
      終了前にROLLBACKを実行するようにする。
    - NONE
      何の操作もしない。
- ex)
  WHENEVER SQLERROR EXIT SQL.SQLCODE ROLLBACK
  sqlerrorが発生した場合、SQLCODEを戻してROLLBACK、終了する。
### XQUERY
## Restriction
- 
  |----------------------+------------|
  | 項目                 | 制限       |
  |----------------------+------------|
  | ユーザー名           | 30バイト   |
  | 置換変数名の長さ     | 30バイト   |
  | 置換変数値の長さ     | 240文字    |
  | コマンドラインの長さ | 2500文字   |
  | 最大PAGESIZE         | 50,000行   |
  | 合計行幅             | 32,767文字 |
  | 最大ページ数         | 99,999     |
  |----------------------+------------|

- 
  [[http://docs.oracle.com/cd/E16338_01/server.112/b56314/apa.htm][A SQL*Plusの制限 - SQL*Plus®ユーザーズ・ガイドおよびリファレンス リリース11.2]]

## Arguments
- 
  ファイル名の後にスペースを挟んで引数を列挙する。
  内部では&1, &2などの形で受け取れる。
  
- 
  [[http://www.shift-the-oracle.com/sqlplus/tutorial/sqlplus-script-parameter.html][SQL*Plus の実行スクリプトをパラメータ付きで起動する - SHIFT the Oracle]]

## Security
### PRODUCT_USER_PROFILE表
- PUP表
  GRANTとREVOKEコマンド、およびユーザー・ロールによるユーザー・レベルのセキュリティを補う。
  特定のSQLおよびSQL*Plusコマンドをユーザー単位で使用禁止にできる。
## Memo
### 接続
- [[http://itref.fc2web.com/oracle/sqlplus/][Oracle SQL*Plus - SE学院]]
#### ローカル接続
#### リモート接続
##### 簡易接続
##### ローカルネーミングパラメータによる接続
## Link
- [[https://docs.oracle.com/cd/E16338_01/server.112/b56314/toc.htm][目次 - SQL*Plusユーザーズ・ガイドおよびリファレンスリリース11.2]]
- [[https://docs.oracle.com/cd/E16338_01/server.112/b56314/ch_twelve001.htm#BACDBGBC][SQL*Plusコマンド一覧 - SQL*Plusユーザーズ・ガイドおよびリファレンスリリース11.2]]
