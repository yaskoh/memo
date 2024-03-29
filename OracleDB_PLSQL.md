# OracleDB PL/SQL
## PL/SQL
### Architecture
#### PL/SQL Engine
#### PL/SQL Unit
##### PL/SQL Unit
- 次のいずれか
  - PL/SQLの無名ブロック
  - FUNCTION
  - LIBRARY
  - PACKAGE
  - PACKAGE BODY
  - PROCEDURE
  - TRIGGER
  - TYPE
  - TYPE BODY
##### Compile Parameters
### 言語仕様
#### Fundamentals
##### Character Set
###### データベース・キャラクタ・セット
###### 各国語・キャラクタ・セット
##### Lexical Unit
##### 
##### Expression
#### データ型
##### スカラー
###### 数値
####### PLS_INTEGER, BINARY_INTEGER
- 
  32ビットであらわされる-2147483648~2147483647の範囲の符号付整数
######## NATURAL
######## NATURALN
######## POSITIVE
######## POSITIVEN
######## SIGNTYPE
######## SIMPLE_INTEGER
####### BINARY_FLOAT
######## Const
######### BINARY_FLOAT_NAN
######### BINARY_FLOAT_INFINITY
######### BINARY_FLOAT_MAX_NORMAL
######### BINARY_FLOAT_MIN_NORMAL
######### BINARY_FLOAT_MAX_SUBNORMAL
######### BINARY_FLOAT_MIN_SUBNORMAL
####### BINARY_DOUBLE
######## Const
######### BINARY_DOUBLE_NAN
######### BINARY_DOUBLE_INFINITY
######### BINARY_DOUBLE_MAX_NORMAL
######### BINARY_DOUBLE_MIN_NORMAL
######### BINARY_DOUBLE_MAX_SUBNORMAL
######### BINARY_DOUBLE_MIN_SUBNORMAL
####### NUMBER
###### 文字
####### CHAR
####### VARCHAR2
####### RAW
####### NCHAR
####### NVARCHAR2
####### LONG
####### LONG RAW
####### ROWID
####### UROWID
###### BOOLEAN
###### 日時
####### Field
######## YEAR
######## MONTH
######## DAY
######## HOUR
######## MINUTE
######## SECOND
######## TIMEZONE_HOUR
######## TIMEZONE_MINUTE
######## TIMEZONE_REGION
######## TIMEZONE_ABBR
###### 時間隔
##### コンポジット
##### 参照
##### ラージ・オブジェクト
#### 制御文
##### IF, CASE
##### LOOP, EXIT, CONTINUE
##### GOTO, NULL
#### コレクション・レコード
#### 静的SQL
#### 動的SQL
#### サブプログラム
- 
  繰り返し起動できる名前付きPL/SQLブロック。
  
##### サブプログラムの分類
###### ネストしたサブプログラム
- PL/SQLブロック内で作成される
###### パッケージ・サブプログラム
- パッケージ内で作成される
###### スタンドアロン・サブプログラム
- スキーマレベルで作成される。
#### トリガー
#### パッケージ
#### エラー処理
#### 言語要素
##### カーソルFOR LOOP文
- 指定されたカーソルが戻す行の型のレコード変数として暗黙的にループ索引を宣言し、カーソルをオープンする。
  反復される度に、結果セットから行をフェッチしてレコードに入れる。フェッチする行がなくなるとカーソルがクローズされる。
###### cursor_for_loop_statement
- FOR record IN ... LOOP statement END LOOP label;

##### EXECUTE IMMEDIATE文
- 動的SQLを一度の操作で作成して実行する。

##### SQLCODEファンクション
- 処理する例外の数値コードを戻す。
##### SQLERRMファンクション
- エラー・コードに関連付けられているエラー・メッセージを戻す。
## Link
### PL/SQL
- [[https://docs.oracle.com/cd/E16338_01/appdev.112/b56260/toc.htm][Oracle® Database PL/SQL言語リファレンス 11gリリース2 (11.2)]]
- [[https://docs.oracle.com/cd/E16338_01/appdev.112/b56262/toc.htm][Oracle® Database PL/SQLパッケージおよびタイプ・リファレンス 11g リリース2(11.2)]]
  
