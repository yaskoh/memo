# PostgerSQL Documentation
- [[https://www.postgresql.org/docs/9.6/static/][PostgreSQL 9.6.10 Documentation]]
- [[https://www.postgresql.jp/document/9.6/html/index.html][PostgreSQL 9.6.5文書]]
## I:   Tutorial
### Getting Started
#### Installation
#### Architectural Fundamentals
#### Creating a Database
- $ createdb mydb (or /usr/local/pgsql/bin/createdb mydb , and so on)
- $ dropdb mydb
#### Accessing a Database
- $ psql mydb
### The SQL Language
### Advanced Features
## II:  The SQL Language / SQL言語
### 4. SQL Syntax / SQLの構文
#### 4.1. 字句の構造
##### 4.1.2.
###### 4.1.2.4 ドル記号で引用符付けされた文字列定数
##### 4.1.4. 特殊文字
#### 4.2. 評価式
#### 4.3. 関数呼び出し
#### 語彙の構成
- SQL
  SQLは一続きのコマンド。
- コマンド
  コマンドはトークンがつながったもので、セミコロンで終わる。
  トークンは通常空白(スペース、タブ、改行)で区切られるが、曖昧さがなければ必要ない。
- トークン
  キーワード、識別子、引用符で囲まれた識別子、リテラル（若しくは定数）、特別な文字シンボル。

##### キーワード
- 
  SQL言語で決まった意味を持つ単語。
  [[https://www.postgresql.jp/document/9.3/html/sql-keywords-appendix.html][付録C. SQLキーワード]]

##### 識別子
- 
  識別子とキーワードは同じ語彙構造を持つため、キーワードでないものが識別子。
  識別子（とキーワード）は、文字、アンダースコアで始まり、
  続く文字は、文字、アンダースコア、数字、あるいはドル記号$を使用できる。
  標準識別子ではドル記号$は識別子内では使用できない。
  
  NAMEDATALEN-1バイトより長い識別子は使えない。長い名前を書くことはできるが区切られてしまう。
  デフォルトではNAMEDATALENは64。src/include/pg_config_manual.hを編集することで変更可能。
  
  任意の文字の連なりを二重引用符(")で囲んだ区切り識別子も使用できる。
  バックスラッシュでないエスケープ文字を使用したい場合、文字列の後にUESCAPE句を使用して指定する。

##### 定数
- 暗黙に型付けされる定数
  文字列、ビット文字列、数字

###### 文字列定数
- 
  単一引用符(')でくくられた任意の文字の並び。
  2つの文字列定数が、改行を含む空白で区切られている場合、連結され1つの定数として処理される。
  ex) SELECT 'foo'
      'bar';
      ⇒ SELECT 'foobar';

####### C形式エスケープ
- 
  単一引用符の前にEを記述する。
  文字列内でバックスラッシュ文字によりC言語のようなバックスラッシュシーケンスが開始される。
  
  |---------------------------+---------------------------------------|
  | Backslash Escape Sequence | 解釈                                  |
  |---------------------------+---------------------------------------|
  | \b                        | 後退                                  |
  | \f                        | 改ページ                              |
  | \n                        | 改行                                  |
  | \r                        | 復帰                                  |
  | \t                        | タブ                                  |
  | \o, \oo, \ooo (o=0-7)     | 8進数バイト値                         |
  | xh, \xhh (h=              | 16進数バイト値                        |
  | \uxxxx, \Uxxxxxxxx        | 16もしくは32ビットの16進Unicode文字列 |
  |---------------------------+---------------------------------------|

####### Unicodeエスケープ
- 
  U&で始まる。
  バックスラッシュ以外のエスケープ文字を使いたい場合、
  UESCAPE句を使用して指定することが可能。

####### ドル引用符
- ex)
  $$Dianne's horse$$
  $tag$Dianne's horse$tag$

###### ビット文字列定数
- 
  BやXを前置して、ビット文字列を表現できる。小文字でもよい。
  Xだと16進の表記となる。
  ex) B'1001', X'1FF'

###### 数値定数
- 
  以下の形式がある。
  - digits
  - digits.[digits][e[+-]digits]
  - [digits].digits[e[+-]digits]
  - digitse[+-]digits

  ex) 42, 3.5, 4., .001, 5e2, 1.925e-3

###### 他の型の定数
- 
  type 'string'
  'string'::type
  CAST ('string' AS type)

##### 演算子
- 
  NAMEDATALEN-1までの長さの、以下に示すリストに含まれる文字の並び。
    + - * / < > = ~ ! @ # % ^ & | ` ?
  
  --, /*は使用できない。
  複数文字の演算子名は、下記の文字を含まない限り、+や-で終わることができない。
    ~ ! @ # ^ & | ` ?

  曖昧さを回避するため、隣り合った演算子を空白で区切る必要がある。
    X*@Y -> X* @Y

###### 優先順位
- 
  |--------------------+--------+------------------------------------------------|
  | 演算子/要素        | 結合性 | 説明                                           |
  |--------------------+--------+------------------------------------------------|
  | .                  | 左     | テーブル/列名の区切り文字                      |
  | ::                 | 左     | PostgreSQL方式の型キャスト                     |
  | [ ]                | 左     | 配列要素選択                                   |
  | + -                | 右     | 単項可算、単項減算                             |
  | ^                  | 左     | 累乗                                           |
  | * / %              | 左     | 掛け算、割り算、剰余                           |
  | + -                | 左     | 加算、減算                                     |
  | IS                 |        | IS TRUE, IS FALSE, IS NULL, その他             |
  | ISNULL             |        | NULLかどうかを試す                             |
  | NOTNULL            |        | 非NULLかどうかを試す                           |
  | (その他)           | 左     | その他全ての組み込み、あるいはユーザ定義演算子 |
  | IN                 |        | メンバシップを設定する                         |
  | BETWEEN            |        | 範囲内に含有                                   |
  | OVERLAPS           |        | 時間間隔の重複                                 |
  | LIKE ILIKE SIMILAR |        | 文字パターンの一致                             |
  | < >                |        | 小なり、大なり                                 |
  | =                  | 右     | 等しい、代入                                   |
  | NOT                | 右     | 論理否定                                       |
  | AND                | 左     | 論理積                                         |
  | OR                 | 左     | 論理和                                         |
  |--------------------+--------+------------------------------------------------|

##### 特殊文字
- 
  直後に数字が続くドル記号($)は、関数定義の本体またはプリペアド文中の位置パラメータを表すために使われる。
  括弧()は、式をまとめる。
  大括弧[]は、配列要素を選択するために使う。
  カンマ,は、リストの要素を区切るために構文的構造体で使われることがある。
  セミコロン;は、SQLコマンドの終わりを意味する。
  コロン:は、配列から"一部分"を取り出すために使う。
  アスタリスク*は、すべてのフィールドを表現するために使われる
  ピリオド.は数値定数の中で使われる。

##### コメント
- 
  一行コメント --
  ブロックコメント /* */

#### 評価式
- 
  評価式は以下のいずれか。
  - 定数またはリテラル値
  - 列の参照
  - 関数宣言の本体やプリペアド文における位置パラメータ参照
  - 添え字付の式
  - フィールド選択式
  - 演算子の呼び出し
  - 関数呼び出し
  - 集約式
  - ウィンドウ関数呼び出し
  - 型キャスト
  - 照合順序式
  - スカラ副問い合わせ
  - 配列コンストラクタ
  - 行コンストラクタ
  - 括弧で囲まれた別の評価式

#### 関数と演算子

##### 関数呼び出し
- 
  関数呼び出し時の引数は、位置表記、名前付け表記、混在表記が可能。

### 5. Data Definition / データ定義
#### デフォルト値
##### DEFAULT
- 
  列データ型の後に列挙して設定する。

##### SERIAL
- 
  連続した値を生成する

#### 制約
- 
  列に対して制約をつける列制約と、
  テーブルに対して制約をつけるテーブル制約がある。

##### CHECK
- 
  制約を付ける。
  ex) price numeric CHECK (price > 0)

##### COSTRAINT
- 
  制約に個別に名前を付けることが出来る。
  ex) price numeric CONSTRAINT positive_price CHECK (price > 0)

##### NOT NULL
- 
  非NULL制約。

##### UNIQUE
- 
  一意性制約

##### PRIMARY KEY
- 
  単純に一意性制約と非NULL制約を組み合わせたもの。

##### REFERENCES
- 
  外部キー制約。
  列リストを省略した場合、参照先の主キーを対象とする。

##### FOREIGN KEY

##### EXCLUDE
- 
  排他制約

#### システム列

##### oid
- 
  オブジェクト識別子。

##### tableoid
- 
  行を含むテーブルのOID。

##### xmin
- 
  行バージョンの挿入トランザクションの識別情報。
  行バージョンとは、行の個別の状態。

##### cmin
- 
  挿入トランザクション内のコマンド識別子。

##### xmax
- 
  削除トランザクションの識別情報。

##### cmax
- 
  削除トランザクション内のコマンド識別子。

##### ctid
- 
  行バージョンの物理的位置。

#### テーブルの変更
##### 列の追加
- 
  ex) ALTER TABLE products ADD COLUMN descrition text CHECK (description <> '');

##### 列の削除
- 
  ex) ALTER TABLE products DROP COLUMN description;

##### 制約の追加
- 
  ex) ALTER TABLE products ADD CHECK (name <> '');
      ALTER TABLE products ADD CONSTRAINT some_name UNIQUE (product_no);
      ALTER TABLE products ADD FOREIGN KEY (product_group_id) REFERENCES product_groups;
      ALTER TABLE products ALTER COLUMN products_no SET NOT NULL;

##### 制約の削除
- 
  制約を削除する場合、対象の制約名を知る必要がある。
  自分で設定していない場合、システムが生成した名前が割り当てられているため、
  それを探す必要がある。
  ex) ALTER TABLE products DROP CONSTRAINT some_name;

##### デフォルト値の変更
- 
  ex) ALTER TABLE products ALTER COLUMN price SET DEFAULT 7.77;
      ALTER TABLE products ALTER COLUMN price DROP DEFAULT;

##### 列のデータ型の変更
- 
  暗黙のキャストが変更する場合のみ、成功する。
  ex) ALTER TABLE products ALTER COLUMN price TYPE numeric(10,2);

##### 列名の変更
- 
  ex) ALTER TABLE products RENAME COLUMN product_no TO product_number;

##### テーブル名の変更
- 
  ex) ALTER TABLE products RENAME TO items;

#### 権限
- 
  オブジェクトを使用するには権限が必要。

- 権限の種類
  SELECT, INSERT, UPDATE, DELETE, TRUNCATE, REFERENCES, TRIGGER,
  CREATE, CONNECT, TEMPORARY, EXECUTE, USAGE

##### GRANT
- 
  権限を割り当てる。
  ex) GRANT UPDATE ON accounts TO joe;

##### REVOKE
- 
  権限を取り消す。
  ex) REVOKE ALL ON accounts FROM PUBLIC;

#### スキーマ
- 
  入れ子にできないOSのディレクトリのようなもの。
  名前空間を分離する。
  
- オブジェクトの作成
  スキーマ上にオブジェクトを作成するには、
    ex) CREATE TABLE myschema.mytable ( ...);
  のようにスキーマを指定した形式で書く。

- デフォルト
  デフォルトでは、publicスキーマにオブジェクトが作成される。

- スキーマ検索パス
  "SHOW search_path;"で現行の検索パスを表示できる。
  検索パス内で最初に存在するスキーマが新規オブジェクトが作成されるデフォルトの場所で、
  検索時は一致するオブジェクトが見つかるまで検索パス内で探索される。
  追加するには、"SET search_path TO myschema, public;"のようにする。

- システムカタログスキーマ
  pg_catalogスキーマが、publicおよびユーザ作成のスキーマのほかに各データベースに含まれる。
  pg_catalogは常に検索パスに含まれる。
  明示的にリストされていない場合、パスのスキーマを検索する前に暗黙的に検索される。

##### CREATE SCHEMA
- 
  スキーマに自由に名前をつける。

##### DROP SCHEMA
- 
  スキーマを削除する。
  オブジェクトを含むスキーマを削除するには、CASCADEをつける。

##### USAGE
- 
  スキーマを使用する権限。多分。

#### 継承
- 
  親テーブルの検査制約と非NULL制約は子テーブルに継承される。
  他の種類の制約は継承されない。
  
  複数の親から継承可能。
  複数の親が同じ名前の列を保持していたり、子テーブルが親テーブルと同じ列を保持している場合、
  統合され一つとなる。データ型が異なる場合はエラーとなる。
  全ての制約を受け継ぐ。

  子テーブルがいる場合親テーブルを削除できないが、
  CASCADEオプションを付けて子テーブルも全て削除することはできる。

##### INHERITS
- 
  テーブルで継承を行うためのヒント。

#### パーティショニング
- 概要
  - テーブルのサイズがデータベースサーバの物理メモリを超えないようにすることがポイントとなってくる。
  - 「範囲分割」、「リスト分割」が存在する。
  - 継承によりサポートしているため、1つの親テーブルの子テーブルとして作成する必要がある。

##### 実装
- 
  1. すべてのパーティションが継承する"マスタテーブル"を作成する。
  2. マスタテーブルから継承された"子テーブル"を作成する。
  3. 分割されたテーブルにテーブル制約を追加する
  4. 各テーブルにインデックスを作成
  5. マスタテーブルに、パーティションに中継するためのトリガ等を作成
  6. constraint.exclusion背亭パラメータがpostgresql.conf内で無効となっていないことの確認

### 6. Data Manipulation / データ操作
### 7. Queries / 問合せ
#### 7.6 LIMITとOFFSET
### 8. Data Type / データ型
#### 数値データ型
- 
  |------------------+-------+--------------+------------------|
  |                  |       |              |                  |
  |------------------+-------+--------------+------------------|
  | smallint         | 2byte | 狭範囲の整数 | -32768 ～ +32768 |
  | integer          |       |              |                  |
  | bigint           |       |              |                  |
  | decimal          |       |              |                  |
  | numeric          |       |              |                  |
  | real             |       |              |                  |
  | double precision |       |              |                  |
  | smallserial      |       |              |                  |
  | serial           |       |              |                  |
  | bigserial        |       |              |                  |
  |------------------+-------+--------------+------------------|

#### 通貨型
- 
  |-------+-------+----------+---|
  | 型名  | 格納サイズ | 説明     |   |
  |-------+-------+----------+---|
  | money | 8byte | 貨幣金額 |   |
  |-------+-------+----------+---|

#### 文字型
- 
  |----------------------------------+----------------|
  | 型名                             | 説明           |
  |----------------------------------+----------------|
  | character varying(n), varchar(n) | 上限付き可変長 |
  | character(n), char(n)            | 空白埋め固定長 |
  | text                             | 制限なし可変長 |
  |----------------------------------+----------------|

#### バイナリ列データ型
- 
  |-------+--------------------------+--------------------|
  | 型名  | 格納サイズ               | 説明               |
  |-------+--------------------------+--------------------|
  | bytea | (1 or 4) + binary length | 可変長のバイナリ列 |
  |-------+--------------------------+--------------------|

#### 日付/時刻データ型
- 
  |---------------------------------+------------+--------------------------+------+------+------|
  | 型名                            | 格納サイズ | 説明                     | 過去 | 未来 | 精度 |
  |---------------------------------+------------+--------------------------+------+------+------|
  | timestamp [ without time zone ] | 8byte      | 日付と時刻（時間帯なし） |      |      |      |
  | timestamp with time zone        | 8byte      | 日付と時刻、時間帯付     |      |      |      |
  | data                            | 4byte      | 日付（時刻なし）         |      |      |      |
  | time [ without time zone ]      | 12byte     | 時刻（日付なし）         |      |      |      |
  | time with time zone             | 12byte     | その日の時刻のみ、時間帯付 |      |      |      |
  | interval                        | 12byte     | 時間間隔                       |      |      |      |
  |---------------------------------+------------+--------------------------+------+------+------|

#### 論理値データ型
- 
  |---------+------------+------------|
  | 型名    | 格納サイズ | 説明       |
  |---------+------------+------------|
  | boolean | 1byte      | 真または偽 |
  |---------+------------+------------|

#### 列挙型
#### 幾何データ型

### 9. Functions and Operators / 関数と演算子
#### 9.1. 論理演算子
#### 9.4. 文字列関数と演算子
##### SQL文字列関数と演算子
###### trim([leading | trailing | both] [characters] from string)
#### 9.8. データ型書式設定関数
#### 9.9. 日付/時刻関数と演算子
##### 日付/時刻演算子
##### 日付/時刻関数
- age(timestamp, timestamp)
- age(timestamp)
- current_date
- current_time
- current_timestamp
##### 9.9.1. EXTRACT, date_part
##### 9.9.2. date_trunc
##### 9.9.3. AT TIME ZONE
##### 9.9.4. Current Date/Time
##### 9.9.5. 遅延実行
#### 9.17. 条件式
##### 9.17.1. CASE
##### 9.17.2. COALESCE
- NULLでない自身の最初の引数を返す。全ての引数がNULLの場合のみNULLが返される。
##### 9.17.3. NULLIF
- NULLIF(value1, value2)
  value1がvalue2と等しい場合、NULL値を返す。その他の場合はvaleu1を返す。
##### 9.17.4. GREATESTおよびLEAST
#### 9.25. システム情報関数
#### 9.26. システム管理関数
##### 構成設定関数
##### サーバシグナル送信関数
#### tmp
##### version()
- 
  postgresのバージョンを表示する。

##### rank()

##### nextval()

### 10. Type Conversion / 型変換
### 11. Index / インデックス
#### 11.8. 部分インデックス
#### 11.9. 演算子クラスと演算子族
### 12. Full Text Search / 全文検索
### 13. Concurrency Control / 同時実行制御
### 14. Performance Tips / 性能に関するヒント
### 15. Parallel Query / パラレルクエリ
## III: Server Administration サーバの管理
### 運用管理概要

- [[http://lets.postgresql.jp/map/operation][目的別ガイド：運用管理編 - Let's postgres]]

#### 運用管理作業の分類
##### メンテナンス
- 
  内部状態を要状態に保ち、一定のパフォーマンスを発揮させる。
  VACUUMやANALYZE

##### 監視
- 
  異常を事前に察知する、もしくは発生後に原因調査をする。

##### バックアップ・リストア
- 
  ディスクの故障や誤操作によるデータ消失に対処するため、バックアップを行う。

##### アップグレード・ダウングレード
- 
  マイナーリリースに柔軟に追随できるようにする。
  マイナーリリースでは、互換性が保たれたまま、
  主にバグやセキュリティ問題の修正が行われる。

#### 期間別作業
##### 運用前

###### ログ関連の設定

###### 稼働統計情報関連の設定

###### autovacuum
- 
  テーブルのじょうたいを監視して、しかるべきタイミングでVACUUMする機能。
  
##### 日単位

###### VACUUM
- 
  追記型アーキテクチャのため、更新や削除でガベージが発生する。
  ガベージを回収する作業がVACUUM。
  VACUUMを主導で行う場合、VERBOSEオプションを付与すると
  所要時間や回収したガベージ量が確認できるため便利。

###### ANALYZE
- 
  統計情報を最新のデータ状態をもとにリフレッシュするコマンド。
  autovacuum機能により自動で実行することもできる。

###### システムリソースの取得
- 
  CPU使用率やデバイス使用率、各プロセスの活動状態などの情報を記録する。

###### バックアップ
- 
  論理的なバックアップと、ファイルシステムのファイルとして取得する方法の2種類がある。

####### 論理バックアップ(pg_dump)
- 
  pg_dumpを使ってDBのデータをダンプする。
  一部のテーブルやDBのスキーマ、データ内容だけを取得することが可能。
  SQLの形でデータ取得を行い、主に小規模のDBやメジャーバージョン間の移行などに使用。
  
####### オンライン・バックアップ
- 
  DBクラスタをrsyncやcpコマンドを使い、ファイルとして取得する。
  DBやテーブル単位の指定はできず、DBクラスタ全体のバックアップとなる。
  アーカイブログを取得しておくことが必須。
  アーカイブログと合わせて、ダウン直前までのリカバリが可能なPITRが必要な際に使用する。

##### 月単位～

###### 月次メンテナンス
- REINDEX
  インデックスの再構築を行う。
- CLUSTER
  インデックス順に、テーブルデータを物理的に再編成する。
  テーブルの物理的な圧縮+再編成+REINDEXの効果がある。
  CLUSTERをオンラインで実行可能なpg_reorgというプロダクトもある。
- VACUUM FULL
  テーブルを物理的に圧縮する。DBが肥大化してディスクフル直前の場合に実施する。

###### アップグレード・アップデート
- アップグレード
  メジャーバージョン間のDBクラスタ互換性がないので、
  pg_updateにより変換するか、pg_dumpでデータを抽出し流し込む作業が必要。
  振る舞いが変わることがあるため、APのチェックやパラメータ再設計が必要。

- アップデート
  互換性があるため、基本的にバイナリの差し替えのみで済む。
  振る舞いは原則変わらない。

##### 不定期
###### 再起動
###### フェイルオーバ
### Installation from Source Code / ソースコードからインストール
### Installation from Source Code on Windows / Windowsにおけるソースコードからのインストール
### Server Setup and Operation / サーバの準備と運用
### 19. Server Configuration / サーバの設定
#### 設定ファイル
- postgresql.conf、pg_hba.conf、pg_ident.confという設定ファイルがある。
  インストールしたフォルダの"data"フォルダ配下に存在する。
##### postgresql.conf
- 最大接続数やログの保存方法など、基本的なPostgreSQLの設定を行う。

- 設定ファイル上では、booleanはtrue/falseでなくon/offで設定する。
##### pg_hba.conf
- 
  クライアントの認証に関する記述を行う。
  TYPE, DATABASE, USER, ADDRESS, METHODの5つの項目で1行の設定となる。
  
- TYPE
  
- DATABASE
  対象とするデータベース名

- USER
  対象とするPostgresのユーザー名

- ADDRESS
  クライアントのIPアドレス

- METHOD
  認証方式。以下が使用可能。
    trust / reject / md5 / crypt / password / krb5 / ident / pam
  
##### pg_ident.conf
- 
  認証方式で"ident"を使う場合に、identのユーザ名をPostgreSQLのユーザ名にマップするマップ名の記述を行う。
  MAPNAME, SYSTEM-USERNAME, PG-USERNAMEの3項目がある。

#### 19.1. Setting Parameters / パラメータの設定
##### パラメータ名とその値
- 
  - 論理型
  - 文字列型
  - 数値型
  - 単位付きの数値
  - 列挙型
##### 設定ファイルによるパラメータ操作
- postgresql.conf
  - 1つの行に1つのパラメータが設定される
  - 名前と値の間の等号は省略可能
  - ハッシュはその行の後ろがコメントであることを示す。
  - 単純でない識別子、または数値でないパラメータは単一引用符でくくられる。
- 再読み込み
  - SIGHUPシグナルを受け取るたびに再読み込み
    - pg_ctl reload (コマンドライン)
    - pg_reload_conf() (SQL関数)
- postgres.auto.conf
  - 決して手動で編集してはいけない
  - ALTER SYSTEMコマンドを使った設定値を保存する。
  - postgresql.confが読み込まれる度に常に自動で読み込まれ、postgresql.conf設定を上書きする。
- pg_file_settings（システムビュー）

##### SQLを通じたパラメータ操作
- 恒久的
  - ALTER SYSTEM
    - グローバルな設定値を変更する。postgresql.conf変更と等価。
  - ALTER DATABASE
    - データベース単位での変更。グローバル設定値を上書き。
  - ALTER ROLE
    - ユーザ固有の設定値。グローバル、データベース設定値を上書き。
- 一時的
  - SHOW : 現在の値を調べる。
    関数はcurrent_setting(setting_name text)
  - SET : ローカルに変更できるパラメータの値を変更する。
    関数はset_config(setting_name, new_value, is_local)
- 参照
  - pg_settings (system view)
    - SHOW ALLと同じだが、更に詳細な情報が提供される。
    - このビューのsetting列をupdateするのは、SETコマンドの実行と同等。
##### シェルによるパラメータ操作
##### 設定ファイルの内容の管理
#### 19.2. File Locations / ファイルの場所
- data_dirctory
  - データ格納に使用するディレクトリ
- config_file
  - メインサーバ設定ファイル。通例postgresql.conf
- hba_file
  - ホストベース認証(HBA)用のファイル。通例pg_hba.conf
- ident_file
  - ユーザ名マッピング設定ファイル。通例pg_ident.conf
- external_pid_file
  - PIDファイルの名前を指定。
#### 19.3. Connections and Authentication / 接続と認証
##### 接続設定
###### listen_address (string)
###### port (integer)
###### max_connections (integer)
###### superuser_reserved_connections (integer)
###### unix_socket_directories (string)
###### unix_socket_group (string)
###### unix_socket_permissions (integer)
###### bonjour (boolean)
###### bonjour_name (string)
###### tcp_keepalives_idle (integer)
###### tcp_keepalives_interval (integer)
###### tcp_keepalives_count (integer)
##### セキュリティと認証
###### authentication_timeout (integer)
###### ssl (boolean)
###### ssl_ca_file (string)
###### ssl_cert_file (string)
###### ssl_crl_file (string)
###### ssl_key_file (string)
###### ssL_ciphers (string)
###### ssl_prefer_server_ciphers (bool)
###### ssl_ecdh_curve (string)
###### password_encryption (boolean)
###### krb_server_keyfile (string)
###### krb_caseins_users (boolean)
###### db_user_namespace (boolean)
#### 19.4. Resource Consumption / 資源の消費
##### 19.4.1. メモリ
###### shared_buffers(integer)
- 1GB以上のRAMを載せた専用DBSの場合は、妥当な初期値は25%。OSのキャッシュにも依存するため、40%以上を割り当てても動作がよくなる見込みはない。
- shared_buffersを50%以上に設定するとカーネルのキャッシュがあふれスワップする
##### 19.4.2. ディスク
##### 19.4.3. カーネル資源使用
##### 19.4.4. コストに基づくVacuum遅延
##### 19.4.5. バックグラウンドライタ
##### 19.4.6. 非同期動作
#### Write Ahead Log / ログ先行書き込み(WAL)
##### 諸設定
###### wal_level (enum)
- VALUE: minimal, replica, logical
###### wal_buffers (integer)
##### チェックポイント
###### checkpoint_timeout (integer)
###### checkpoint_completion_target (floating point)
###### max_wal_size (integer)
- 自動WALチェックポイント尾間にWALが増加する最大サイズ。
  ソフトリミット。高負荷の場合などwal_max_sizeを超える場合がある。
###### min_wal_size (integer)
##### アーカイビング
###### archive_mode (enum)
###### archive_command (string)
###### archive_timeout (integer)
#### Replication / レプリケーション
#### Query Planning / 問合せ計画
##### プランナメソッド設定
##### プランナコスト定数
###### effective_cache_size (integer)
##### 遺伝的問合せオプティマイザ
##### その他のプランナオプション
#### Error Reporting and Logging / エラー報告とログ取得
##### Where To Log / ログの出力先
##### When To Log / いつログを取得するか
###### log_min_duration_statement (integer)
- 文の実行に少なくとも指定したミリ秒かかった場合に、文の実行に要した時間をログに記録する。
- -1(default)は無効とする。0にするとすべての分の実行時間が出力される。
##### What To Log / 何をログに
###### log_statement (enum)
- どのSQL文をログに記録するかを制御する。
- Values: none, ddl, mod, all
##### Using CSV-Format Log Output
##### Process Title
#### Run-time Statistics / 実行時統計情報
##### Query/Index Statistics Collector / 問い合わせおよびインデックスに関する統計情報コレクタ
###### track_functions (enum)
- 関数の呼び出し数と費やされた時間の追跡を有効にする。
#### Automatic Vacuuming / 自動Vacuum作業
#### 19.11. Client Connection Defaults / クライアント接続デフォルト
##### 19.11.3. 共有ライブラリのプリロード
###### local_preload_libraries (string)
- 接続時に事前読み込みされる、1つまたは複数の共有ライブラリを指定。
###### session_preload_libraries (string)
- 接続開始時にプリロードされる共有ライブラリを指定。
###### shared_preload_libraries (string)
- サーバ起動時にプリロードされる共有ライブラリを指定
#### Lock Management / ロック管理
#### Version and Platform Compatibility / バージョンとプラットフォーム互換性
#### Error Hadling
#### Preset Options
#### Customized Options
#### Developer Options
#### Short Options
### Client Authentication / クライアント認証
### Database Roles / データベースロール
### Managing Databases / データベース管理
### Localization / 多言語対応
### Routine Database Maintenance Tasks / 定常的なデータベース保守作業
### Backup and Restore / バックアップとリストア
#### SQLによるダンプ
- ダンプ
  データのダンプ方法は、以下の通り。
  - pg_dump dbname > outfile

- リストア
  通常のテキストファイルで作成されたファイルをリストアする場合は、
  psqlコマンドで読み込む。
  - psql dbname < infile

- pg_dumpall
  ロールやテーブル空間にうちても取得する場合に用いる。

- 大規模DBの扱い
  パイプを使って圧縮を行う等する。

#### ファイルシステムのバックアップ
- 
  データを保存しているファイルを直接コピーしバックアップする方法も可能。
  ただし、以下の二点の制約があり、あまり実用的でなく、pg_dumpに劣る。
  1. データベースサーバを必ず停止する必要がある。リストアする場合も同様。
  2. コミットログなしでは使えないため、個別テーブルをそれぞれ復元するなどの方法は取れない。
  
- 
  サイズ上は、インデックスの有無等の理由で概してダンプより大きくなる。
  ただし、ファイルシステムバックアップの方が高速である。

#### 継続的アーカイブとPITR
- 
  WALファイルとファイルシステムレベルのバックアップから復旧する方法。
  - WALはpg_xlog/ディレクトリは以下で管理している。
  - pg_dumpやpg_dumpallは論理的なバックアップであり、WALでのやり直し目的には使用できない。

##### WALアーカイブ設定
- 
  - WALの記録は、通常1つ16メガバイトのWALセグメントファイルに分割される。
  - 概念的なWALの並び内の位置を反映した、数字の名前が付与される。
  - 不要となったセグメントファイルの名前をより大きなセグメント番号に変更することで"再回収"する。
  
##### ベースバックアップの作成
- 
  pg_basebackupを実行するのが一番簡単。
  より柔軟性が求められる場合は、低レベルなAPIを使ってバックアップを作ることも可能。
  
  ベースバックアップの過程で、WALアーカイブ領域にバックアップ履歴ファイルが作成さえっる。
  
##### 復旧
- 
  1. 稼働している場合、サーバを停止する。
  2. 容量があるのであれば、クラスタデータディレクトリ全体とテーブル空間をすべて一時的な場所にコピーする。
     少なくともpg_xlog/は対比しておく。
  3. クラスタデータディレクトリ以下、および使用中のテーブル空間最上位ディレクトリ以下の、
     既存のすべてのサブディレクトリ、ファイルを削除する。
  4. ファイルシステムバックアップからデータベースファイルをリストアする。
     所有権が正しいことを確認し、テーブル空間を使用している場合は、pg_tblspc/内のシンボリックリンクが正しいことを確認する。
  5. pg_xlog/内のファイルをすべて削除する。
  6. 2.で対比した未アーカイブのWALセグメントファイルをpg_xlog/へコピーする。
  7. 復旧コマンドファイルrecovery.confをクラスタデータディレクトリに作成する。
     場合によってはpg_hba.confを編集し、一般ユーザが接続できないようにする。
  8. サーバを起動する。

###### recovery.conf
- 
  リカバリに使用する、リカバリのときのみ有効となるファイル。
  name = 'value'という書式取る。ハッシュ(#)は後続がコメントとなる。シングルクォートを使う場合は2つ重ねる。('')
  
  サンプルファイルのshare/recovery.conf.sampleが提供されている。
  
  リカバリが完了すると、"recovery.done"と拡張子が変わる。

####### Archive Recoverry Parameters
- restore_command(string)
  連続したWALファイルのアーカイブを取得するために実行するシェルコマンドを指定する。
  アーカイブリカバリには必須だが、ストリーミングレプリケーションの場合は必須ではない。
  %fはアーカイブから取得するファイル名に置換される。
  %pはコピー先のディレクトリ名に置換される。
  %rは有効な最後のリスタートポイントを含むWALファイルのファイル名に置換される。通常ウォームスタンバイ設定でのみ使用される。

  コマンドは、成功したときのみ終了コードゼロを返すことが重要。

- archive_cleanup_command(string)
- recovery_end_command(string)

####### Recovery Target Parameters
- recovery_target_name(string)
- recovery_target_time(string)
- recovery_target_xid(string)
- recovery_target_inclusive(boolean)
- recovery_target_timeline(string)
- pause_at_recovery_target(boolean)

####### Standby Server Parameters
- standby_mode(boolean)
- primary_conninfo(string)
- trigger_file(string)
### High Availability, Load Balancing, and Replication / 高可用性・負荷分散・レプリケーション
### Recovery Configuration / リカバリの設定
### 28. Monitoring Database Activity / データベース活動状況の監視
#### 28.1. 表運的なUnixツール
### Monitoring Disk Usage / ディスク使用量の監視
### Reliability and the Write-Ahead Log / 信頼性とログ先行書き込み
### Regression Tests / リグレッションテスト
### チューニング

- [[http://lets.postgresql.jp/map/tuning][目的別ガイド：チューニング編 - Let's postgres]]
- [[https://wiki.postgresql.org/wiki/Tuning_Your_PostgreSQL_Server/ja][Tuning Your PostgreSQL Server/ja]]

#### チューニングの流れ
- 情報収集と分析
- チューニングの実施
- 繰り返し or 完了の判断

#### ハードウェア構成の見直し

##### スケールアウト / スケールアップ

##### ストレージを重視

##### メモリ量を重視

##### CPU速度を重視

#### アプリケーション要求の見直し
- 
  アプリケーションやサービスの無謀な要求の確認。
  
  歯抜けのないIDを振る、正確な行数を表示する、など、
  パフォーマンスを犠牲にして非効率な処理を行う必要があるか確認する。

#### スキーマ・チューニング

##### テーブルの物理編成
- 正規型
  正規化が重要。
  1行のサイズが2KBを超えると、極端に性能が落ちる場合がある。

- データ型
  文字列型の使い分けなど、効率の良いデータ型を選ぶことも効果がある。

- パーティショニング
  1テーブルのサイズが大きすぎるとキャッシュ効率も落ちる。
  パーティショニングなどテーブル分割も検討されたし。

##### データの並び順を考慮
- 
  

##### 適切なインデックスを張る

##### 更新処理でHOTを働かせる
- 
  HOTを利用すると更新処理が速くなる、とのこと。

#### パラメータ・チューニング

##### 接続数

##### メモリ関連

##### WAL関連

#### クエリ・チューニング

##### SQL チューニング

##### 通信方式

##### Prepared Statement

##### 大量データ投入
### 物理的な格納
#### データベースファイルのレイアウト
- 
  制御ファイルとデータファイルは、クラスタのデータディレクトリ内に格納され、
  環境変数名にちなんでPGDATAとして参照される。
  通常位置は"/var/lib/pgsql/data"(WindowsではProgram Files配下などインストール先に存在)。

- 
  |----------------+-------------------------------------------------------------------------------------------------------|
  | 項目         | 説明                                                                                                  |
  |----------------+-------------------------------------------------------------------------------------------------------|
  | PG_VERSION     | 主バージョン番号を保有するファイル                                                                    |
  | base           | データベースごとのサブディレクトリを保有するサブディレクトリ                                          |
  | global         | pg_Databaseのようなクラスタで共有するテーブルを保有するサブディレクトリ                               |
  | pg_clog        | トランザクションのコミット状態のデータを保有するサブディレクトリ                                      |
  | pg_multixact   | マルチトランザクションの状態のデータを保有するサブディレクトリ（共有行ロックで使用される）            |
  | pg_notify      | LISTEN/NOTIFY状態データを保有するサブディレクトリ                                                     |
  | pg_serial      | コミットされたシリアライザブルトランザクションに関する情報を保有するサブディレクトリ                  |
  | pg_snapshots   | エキスポートされたスナップショットを保有するサブディレクトリ                                          |
  | pg_stat_tmp    | 統計用サブシステム用の一時ファイルを保有するサブディレクトリ                                          |
  | pg_subtrans    | サブトランザクションの状態のデータを保有するサブディレクトリ                                          |
  | pg_tblspc      | テーブル空間へのシンボリックリンクを保有するサブディレクトリ                                          |
  | pg_twophase    | プリペアドトランザクション用の状態ファイルを保有するサブディレクトリ                                  |
  | pg_xlog        | WALファイルを保有するサブディレクトリ                                                                 |
  | postmaster.org | 最後にサーバを起動したときのコマンドラインオプションを記録するファイル                                |
  | postmaster.pid | 現在のpostmasterプロセスID、クラスタのデータディレクトリパス、                                        |
  |                | postmaster起動時のタイムスタンプ、ポート番号、Unixドメインソケットのディレクトリパス(Windowsでは空)、 |
  |                | 有効な監視アドレスの一番目(IPアドレスまたは*、TCPを監視していない場合は空)                            |
  |                | および共有メモリのセグメントIDを記録するロックファイル(サーバが停止した後は存在しません）             |
  |----------------+-------------------------------------------------------------------------------------------------------|

#### base
-
  クラスタ内の各データベースに対して、PGDATA/base内にサブディレクトリが存在する。
  サブディレクトリ名はpg_database内の「データベースOID」となる。

##### base配下
- 
  各テーブルおよびインデックスは別個のファイルに格納される。
  通常のリレーションでは、これらのファイル名はテーブルまたはインデックスの「ファイルノード番号」となる。
  ファイルノード番号はpg_class.relfilenodeで見つけられる。

- 
  一時的なリレーションでは、ファイル名はtBBB_FFFという形となる。
  BBBはファイルを生成したバックエンドID、FFFはファイルノード番号。

- 
  どちらも主ファイル（主フォーク）に加え、空き領域情報である"空き領域マップ"を持つ。接尾辞_fsmがついた名前のファイルに格納される。
  テーブルは、どのページが不要な持っていない、と判断できるように追跡する可視性マップを持つ。接尾辞_vmがついたファイル。
  ログを取らないテーブルとインデックスは、初期化フォークという第3のフォークを持つ。フォークに接尾辞_initがつく。

- 
  テーブルのファイノード番号とOIDは多くの場合一致するが、常に一致するわけではないことに注意。

- 
  テーブルまたはインデックスが1GBを超えると、ギガバイト単位のセグメントに分割される。
  2つ目以降のセグメントについては、ノード番号.1、ノード番号.2、というファイル名となる。
  
## IV:  Client Interfaces クライアントインターフェース
### 32. libpq
#### 32.14. 環境変数
- 呼び出し側のプログラムで直接値を指定しなかった場合の接続パラメータのデフォルト値を設定可能。
##### PGHOST
##### PGPORT
##### PGDATABASE
##### PGPASSOWRD
- password接続パラメータと同様に動作する。
##### PGCLIENTENCODING
- client_encoding接続パラメータと同様に動作する。
### 33. ラージオブジェクト
### 34. ECPG - C言語による埋め込みSQL
#### 34.5. 動的SQL
##### 34.5.1. 
### 35. Information Schema / 情報スキーマ
- 現在のデータベースで定義されたオブジェクトについての情報を持つビューの集合。
  標準SQLで定義されており、移植性・安定性を保持できるものと期待される。
  （システムカタログはPostgreSQLに特化し、実装上の事項にならって作成される。）
  情報スキーマのビューにはPostgreSQL固有機能の情報がないため、確認にはシステムカタログやPostgreSQL固有ビューの問い合わせが必要。
  スキーマなので、information_schema.(tablename)という問い合わせが必要。
#### The Schema スキーマ
- 
  情報スキーマ自身は、information_schemaという名前のスキーマ。
  このスキーマは自動的にすべてのデータベース内に存在する。
  所有者は、クラスタ内の最初のデータベースユーザであり、
  スキーマの削除を含むスキーマについてのすべての権限を持つ。

  デフォルトでは、情報スキーマはスキーマの検索パスには含まれない。

#### Data Types データ型（情報スキーマ）
- 概要
  情報スキーマのビューの列では、情報スキーマ内で定義された特殊なデータ型を使用する。
  これらは通常の組み込み型の上位ドメインとして定義される。
  情報スキーマ内の列は、以下5つの型のいずれかを取る。
  
- cardinal_number
  非負の整数

- character_data
  最大文字長の指定がない文字列

- sql_identifier
  文字列。SQL識別子用に使用される。その他の任意のテキストデータには、character_dataを用いる。

- time_stamp
  timestamp with time zone型の上位ドメイン。

- yes_or_no
  YESかNOのいずれかを持つ文字列ドメイン。
  情報スキーマ内で論理（真/偽）データを表すために使用される。
  情報スキーマはboolean型が追加される前に考案されたため、この記法が必要。

#### Views
##### columns
##### tables
##### triggers
##### views
## V:   Server Programming サーバプログラミング
### 36. SQLの拡張
#### 36.15. 関連するオブジェクトを拡張としてパッケージ化
- まとまったパッケージを拡張と呼ぶ。
  少なくともSQLコマンドを含むスクリプトファイル、拡張自身の基本属性を指定する制御ファイルが必要。
- CREATE EXTENSIONでオブジェクトをDB内に読み込み、DROP EXTENSIONでオブジェクトを削除できる。
##### 36.15.1. 拡張のファイル
- .control / 制御ファイル
  拡張と同じ名前に.controlという拡張子を持つファイル名の制御ファイルが必要。
  SHAREDIR/extensionディレクトリに存在する必要がある。
  - extension.control / 主制御ファイル
  - extension--version.control
- extension--version.sql / SQLスクリプトファイル
### 37. トリガ
### 38. イベントトリガ
### 39. ルールシステム
### 40. 手続き言語
### 41. PL/pgSQL - SQL手続き言語
#### 41.1. 概要
##### 41.1.1.
##### 41.1.2.
#### 41.2. PL/pgSQLの構造
- 構造
  - CREATE FUNCTION somefunc(iteger, text) RETURNS integer
    AS 'function body text'
    LANGUAGE plpgsql;
  - 
#### 41.3. 宣言
- name [CONSTANT] type ~
##### 41.3.1. 関数引数の宣言
- 引数は$1, $2と識別子が付けられる。
  別名を宣言可能。
##### 41.3.6. PL/pgSQL変数の照合
#### 41.4. 式
#### 41.5. 基本的な文
##### 41.5.1. 代入
##### 41.5.3. 1行の結果を返す問い合わせの実行
#### 41.6. 制御構造
##### 41.6.2. 条件分岐
###### 41.6.2.1. IF-THEN
###### 41.6.2.1. IF-THEN-ELSE
###### 41.6.2.1. IF-THEN-ELSIF
###### 41.6.2.4. 単純なCASE
###### 41.6.2.5. 検索付きCASE
##### 41.6.3. 単純なループ
##### 41.6.4. 問い合わせ結果による繰り返し
#### 41.11. PL/pgSQLによる開発向けのヒント
##### 41.11.1. 引用符の扱い
- ドル引用符
## VI:  Reference リファレンス
### SQL Command
#### ABORT
#### ALTER ~
##### ALTER INDEX
- インデックス定義を変更する
###### 概要
- ALTER INDEX [ IF EXISTS ] name RENAME TO new_name
- ALTER INDEX [ IF EXISTS ] name SET TABLESPACE tablespace_name
##### ALTER TABLE
- ALTER TABLE
###### 概要
- ALTER TABLE [ IF EXISTS ] [ ONLY ] name [ * ] RENAME [ COLUMN ] column_name TO new_column_name
- ALTER TABLE [ IF EXISTS ] name RENAME TO new_name
#### BEGIN

#### COMMIT

#### COPY
- 
  平文テキストから入力する。
  ファイルとテーブルの間でデータをコピーする。
  ex) COPY weather FROM '/home/user/weacher.txt';

#### CREATE ~
##### tmp
- INHERITS
  指定されたテーブルのすべての列を自動的に継承する。
  新しい子テーブルと複数の親テーブルとの間に永続的な関連が作成される。

- LIKE
  テーブルのすべての列名、データ型、非NULL制約が新しいテーブルにコピーされる。
  INHERITSとの違いは、新テーブルと旧テーブルが完全に分離されること。

##### CREATE DATABES
###### Synopsis
- CREATE DATABASE name 
    [ [WITH]
      [ OWNER [=] user_name ]
      [ ENCODING [=] encoding ]
      [ IS_TEMPLATE [=] istemplate ]]
###### Parameters
####### OWNER [=] user_name
- role name
#######
##### CREATE EXTENSION
##### CREATE TABLE AS
- 問合せの結果によって新しいテーブルを作成する
###### 注釈
- SELECT INTOと同等の機能を持つが、SELECT INTO構文の他の使用例と混乱する可能性から、こちらの使用のほうがよい。
  機能もSELECT INTOのスーパーセットとなっている。
##### CREATE TABLESPACE
- CREATE TABLESPACE tablespace_name
  [ ... ]
  LOCATION 'directory'
  [ ... ]
##### CREATE ROLE
- define a new database role
###### Synopsis
###### Parameters
####### [ENCRYPTED | UNENCRYPTED] PASSWORD 'password'
- control whether the password is stored encrypted in the system catalog.
####### LOGIN | NOLOGIN
- determine whether a role is allowed to log in;
####### INHERIT | NOINHERIT
- determine whether a role "inherits" the privileges of roles it is a member of.
####### VALID UNTIL 'timestamp'
- it sets a data and time after which the role's password is no longer valid.
#### DELETE
- テーブルから行を削除する。
    ex) DELETE FROM weather WHERE city = 'Hayward';
  もし条件がない場合、テーブル内"全ての"データが削除される。
    ex) DELETE FROM weather;

##### 概要
- [WITH [RECURSIVE] with query [, ...] ]
  DELETE FROM [ONLY] table_name [*] [[AS] alias]
      [USING using_list]
      [WHERE condition | WHERE CURRENT OF cursor_name]
      [RETURNING * | output_expression [[AS] output_name] [, ...]]
#### DROP ~
##### DROP EXTENSION
#### EXPLAIN
- 
  問い合わせ文の実行結果を表示する。
  与えられた文に対して、PostgreSQLプランナが生成する実行計画を表示する。

#### INSERT
  
#### LOAD
- LOAD 'filename'
- 共有ライブラリファイルの読み込みを行う。
#### ROLLBACK

#### SAVEPOINT
- 
  現在のトランザクション内に新規にセーブポイントを定義する。

#### SELECT
- テーブルもしくはビューから行を検索する
#### SELECT INTO
- 問い合わせの結果からの新しいテーブルを定義する
##### 注釈
- 機能的にはSELECT INTOと同等。
  ECPGやPL/pgSQLではINTO句の解釈が異なるため、CREATE TABLE AS構文の利用を勧める。
  更に、SELECT INTOよりもCREATE TABLE ASの方が多くの機能がある。
#### UPDATE
##### 概要
- [ WITH [ RECURSIVE ] with_query [, ...] ] 
  UPDATE [ ONLY ] table_name [ * ] [[AS] alias]
     SET { column_name = { exression | DEFALUT } |
           ( 
#### Memo - Objects オブジェクト
##### AGGREGATE
##### CAST
##### COLLATION
##### CONVERSION
##### DATABASE
##### DOMAIN
##### EXTENSION
##### EVENT TRIGGER
##### FOREIGN TABLE
##### FUNCTION
##### GROUP
##### INDEX
##### LANGUAGE
##### OPERATOR
##### ROLE
##### RULE
##### SCHEMA
##### TABLE
##### TRIGGER
##### TYPE
##### USER
##### VIEW
### Client Application
#### clusterdb
- 
  PostgreSQLデータベースをクラスタ化する

#### createdb
- 新しいPostgreSQLデータベースを作成する
  createdb [connection-option...] [option...] [dbname [description]]
##### Options
###### -T template, --template=template
###### -V, --version
###### -?, --help
#### createlang
- 
  PostgreSQL手続き言語をインストールする。
  廃止予定。CREATE EXTENSIONを使う。

#### createuser
- 
  新しいPostgreSQLユーザアカウントを作成する。

#### dropdb
- 
  PostgreSQLデータベースを削除する。

#### droplang
- 
  手続き言語を削除する

#### dropuser
- 
  ユーザアカウントを削除する

#### ecpg
- 
  埋め込みSQL用Cプリプロセッサを使用する

#### pg_basebackup
- 
  クラスタのベースバックアップを取得。
  
  自動的にバックアップモードとし、自動的にバックアップモードから戻ることを確実に行ってくれる。
  バイナリコピーを作成する。
  
  常にデータベースクラスタ全体のバックアップを取る。
  個々のバックアップはできないため、必要であればpg_dumpなどを用いる。
  
  レプリケーションプロトコルを用いて作成するため、スーパーユーザまたはREPLICATION権限を持つユーザが確立する必要がある。
  また、pg_hba.confにおける明示的な権限が許されていなければいけない。
  サーバでmax_wal_sendersをバックアップ用に少なくとも1つのセッションを残すように十分高く設定する必要がある。

##### オプション・出力場所・書式
- -D directory, --pgdata=directory
  出力を書き出すディレクトリ。

- -F format, --format=format
  出力形式を選択する。
  - p, plain
    普通のファイルで、現在のデータディレクトリとテーブル空間と同じレイアウトで出力を書き出す。
    デフォルト書式。
  - t, tar
    指定したディレクトリ内にtarファイルとして出力を書き出す。

- -X method, --x log-method=method
  必要なトランザクションログファイル(WALファイル)をバックアップに含める。
  バックアップ中に生成されたトランザクションログもすべて含める。
  ログアーカイブを考慮することなく、展開したディレクトリ内でそのままpostmasterを起動できる。
  完全なスタンドアローンバックアップ。
  
  - f, fetch
    トランザクションファイルはバックアップの最後に収集される。
  - s, stream
    バックアップを作成するときにトランザクションログをストリームする。

##### オプション・バックアップ生成とプログラム実行制御
- -l label, --label=label
  バックアップのラベルを設定する。
  デフォルトでは"pg_basebackup base backup"

- -P, --progress
  進行状況報告を有効にする。

- -v, --verbose
  冗長モードを有効にする。
  
##### オプション・データベース接続パラメータ制御
- -h host, --host=host
  ホスト名を指定する。

- -p port, --port=port
  ポート番号を指定する。
  
- -U username, --username=username
  接続ユーザ名

- -W, --password
  強制的にパスワード入力を促す。

#### pg_config
- 
  インストールしたPostgreSQLバージョン情報を提供する

#### pg_dump
- Usage
  pg_dump [connection-option..] [option..] [dbname]

- PostgreSQLデータベースをスクリプトファイルまたは他のアーカイブファイルへ抽出する
  
  - スクリプト形式
    再構成するためのSQLコマンドが書かれた平文ファイル。
    リストアを行うにはpsqlコマンドを使う。

  - アーカイブ形式
    リストア時はpg_restoreを使う。
##### Options
###### 出力内容と形式の制御
####### -a, --data-only
- データのみダンプし、スキーマ（データ定義）はダンプしない。

####### -f file, --file=file
- 出力を指定のファイルへ送る。

####### -F format, --format=format
- 出力形式を選択する。以下のいずれかの値を取る。
  - p, plain
    平文のSQLスクリプトを出力する（デフォルト）
  - c, custom
    pg_restoreへの入力に適したカスタム形式アーカイブを出力する。
  - d, directory
    pg_restoreへの入力に適したディレクトリ形式のアーカイブを出力する。
  - t, tar
    pg_restoreへの入力に適したtar形式のアーカイブを出力する。
    個々のテーブルサイズに8GBという上限がある。

####### -s, --schema-only
- --data-onlyの逆。
###### 
#### pg_dumpall
- 
  データベースクラスタをスクリプトファイルへ抽出する。
  pg_dumpで取得できない、ロールやテーブル空間の情報を含むクラスタ全体にわたるデータを保存する。

#### pg_isready
- 
  サーバの接続状態を検査する

#### pg_receivexlog
- クラスタからトランザクションログをストリームする

#### pg_restore
- pg_dumpで作成されたアーカイブファイルから、データベースをリストアする

#### psql
- https://www.postgresql.jp/document/9.6/html/app-psql.html
##### About
- ;(セミコロン)で1文の終わりを表す。
  SQLコマンドの使用が可能。
  
  オプション等はClient Applicationを参照。

##### Options
###### -a, --echo-all
###### -A, --no-align
###### -b, --echo-errors
###### -c comand, --command=command
- psqlに対し、コマンド文字列を実行し終了するように指示する。

###### -d dbname, --dbname=dbname
- DB名を入力する。
  postgres。
  省略した場合は、ユーザ名と同じDB名が使われる模様。

###### -e, --echo-queries
###### -f filename, --file=filename
###### -h hostname
- ホスト名を入力する。
  lotalhost。
  デフォルトがlocalhostであれば省略可能。とのことだったが失敗する。

###### -l, --list
- データベースの一覧を表示する。

###### -L filename, --log-file=filename
###### -n, --no-readline
###### -o filename, --output=filename
- filenameに、問い合わせの出力を書き込む。

###### -p port, --port=port
###### -U username
- ユーザ名を入力する。
  postgres。
###### -V, --version
###### -w, --no-password
###### -W, --password
###### -0, --record-separator-zero
###### -?, --help
- コマンドオプションを表示する。

##### Meta-Commands メタコマンド
- psql内で入力されたコマンドのうち、バックスラッシュで始まり、引用符で囲まれていないものは、
  psql自身が実行するpsqlのメタコマンドとして扱われる。

###### \c, \connect
- 
  サーバへの接続を新規に確立する。

###### \C
- \C [ title ]
  テーブルタイトルの設定/解除を行う。
  "Caption"に由来。

###### \cd
- カレントディレクトリを変更する。
###### \conninfo
- 現在の接続情報を表示する
###### \d[+] [pattern]
- 接続されているDB内のテーブル一覧を表示
  \d+とすると、より多くの情報を表示する。

###### \db[+]
###### \du
- ユーザを確認できる

###### \e, \edit [ filename ] [ line_number ]

###### \echo text [ ... ]

###### \encoding [encoding]
- エンコーディングを表示、またはセット
###### \h
- 
  ヘルプを表示する

###### \i
- 
  ファイルを読み込んで実行する。

###### \l
- 
  存在するデータベースの一覧を表示する

###### \o | \out [filename]
###### \o | \out [| command]
###### \p
- 
  途中まで入力されたクエリの内容を確認する。

###### \q
- psqlを終了する。
  quit

###### \r
- 部分的に入力したクエリをキャンセルする。

###### \z
- テーブル一覧とアクセス権の表示
###### \! [command]
- 別のシェルを起動するか、もしくはUnixのcommandコマンドを実行する。
  引数はこれ以上解釈されず、そのままシェルに渡される。

###### \?
- バックスラッシュコマンドに関するヘルプ情報を表示する
#### reindexdb
- 
  インデックスを再作成する

#### vacuumdb
- 
  不要領域の回収と解析を行う。

### Server Application
#### initdb
- 
  データベースクラスタを新しく作成する

#### pg_archivecleanup
#### pg_controldata
- 
  クラスタの制御情報を表示する

#### pg_ctl
- サーバの初期化、起動、停止、制御
##### Commands
###### init[db]
###### start
###### stop
###### restart
###### reload [-s] [-D datadir]
- 単にpostgresにSIGHUPシグナルを送り、設定ファイルの再読み込みをさせる。
###### status
###### promote
###### kill
- 指定したプロセスにシグナルを送信できる
###### register
###### unregister
##### Options
#### pg_resetxlog
- 
  データベースクラスタの先行書き込みログやその他制御情報を初期化する

#### pg_test_fsync
#### pg_test_timing
#### pg_upgrade
#### postgres
- PostgreSQLデータベースサーバ。

#### postmaster
- 
  postgresの別名。廃止予定。
## VII: Internals 内部構造
### Overview of PostgreSQL Internals /  PostgreSQL内部の概要
### 50. System Catalogs / システムカタログ
- テーブルや列の情報などのスキーマメタデータと内部的な情報を格納する場所。
  PostgreSQLのシステムカタログは通常のテーブルのため、削除・再作成、列の追加、値の挿入や更新が可能だが、通常変更してはいけない。
  その代りにSQLコマンドを実行する。
#### Overview / 概要
#### System Catalogs
##### pg_aggregate
##### pg_am
##### pg_amop
##### pg_amproc
##### pg_attrdef
##### pg_attribute
##### pg_authid
##### pg_auth_members
##### pg_cast
##### pg_class
- テーブルやテーブルに似たもの全ての目録となっていｒ。う
##### pg_constraint
##### pg_colation
##### pg_conversion
##### pg_database
##### pg_depend
##### pg_db_role_setting
##### pg_default_acl
##### pg_enum
##### pg_index
##### pg_namespace
##### pg_statistic
##### pg_trigger
##### pg_type

#### System Views
- システムカタログに対する問い合わせに手近にアクセスできるようにしたり、
  サーバ内部状態へのアクセスを提供したりする。
  
  システムビューはPhostgres特有なのに対し、情報スキーマはSQL標準なので、
  情報スキーマが必要とする情報すべてを提供するのであれば、そちらを選ぶ方がよい。

##### pg_config
##### pg_cursors
##### pg_file_settings
- 設定ファイルの内容の要約を提供する。
  現在の内容であり、最後に適用した内容ではない。
##### pg_group
##### pg_indexes
##### pg_locks
###### 列
####### locktype
- 対象オブジェクトの種類
  - relation
  - extend
  - page
  - tuple
  - transactionid
  - virtualxid
  - object
  - userlock
  - advisory
####### mode
- ロックモードの名称。
####### granted
- boolean
  - true: ロック保持
  - false: ロック待ち
####### fastpath
- boolean
  - true: ファストパス経由でロックが獲得されている場合
  - false: メインロックテーブル経由の場合
##### pg_roles
##### pg_rules
##### pg_stats
##### pg_settings
- サーバの実行時パラメータへのアクセスを提供する。
  基本的にSHOWとSETコマンドの代わりとなるインターフェース。
##### pg_shadow
##### pg_stats
##### pg_tables
##### pg_user
##### pg_user_mappings
##### pg_views

### Frontend/Backend Protocol
### プロセスとメモリ構造
### データベースクラスタ/バックグラウンドライタ
### SQLの実行
### プラン処理
### バッファマネージャとバックグランドライタ
### トランザクションIDと同時実効制御
### VACUUM
### HOT(Heap Only Tuple)

## VIII:Appendixes
### A. PostgreSQLエラーコード
### F. 追加で提供されるモジュール
#### F.3. auto_explain
- 自動的に遅い文の実行計画をログ記録する手段を提供する。
#### F.24. pg_buffercache
- 追加: extension pg_buffercache;
- https://qiita.com/noborus/items/3b8b8cc9b8efb2f894d7
- http://pgsqldeepdive.blogspot.com/2012/12/pgbuffercache.html
##### pgpagecache
- Pythonスクリプト、OSのファイルシステムキャッシュの調査

- https://github.com/cnanakos/pgpagecache
- https://pypi.org/project/pgpagecache/0.1/#description
- http://tyawan080.hatenablog.com/entry/2017/12/31/004634
#### F.27. pg_prewarm
- 追加: extension pg_prewarm;
### G. 追加で提供されるプログラム
#### G.1. クライアントアプリケーション
##### oid2name
- OIDとpostgreSQLデータディレクトリ内のファイルノードを解決する
##### vacuumlo
- 虎児となったラージオブジェクトを削除する
#### G.2. サーバアプリケーション
##### pg_standby
- PostgreSQLウォームスタンバイサーバの作成をサポートする
### H. 外部プロジェクト
#### H.1. クライアントインタフェース
#### H.2. 管理ツール
#### H.3. 手続き言語
#### H.4. 拡張
### J. ドキュメント作成
