# PostgreSQL
## About 概要
### postgreSQLとは
- 
  カリフォルニア大学バークレイ校のCS学科で開発されたものがベース。
  Ingresの後継を意味する名前。
  
  C言語で書かれている。
  
  ライセンスは、"The PostgreSQL License"

### 構造的な基本事項
- 構成
  クライアント・サーバモデルを使用しており、以下で構成される。
    - サーバプロセス
    - クライアントアプリケーション

- スキーマ
  データベースオブジェクトの集合で、データベース内に論理的な区分を与えるのに使う。
  スキーマを利用して、同一のデータベース内に同名のテーブルを作成できる。

### 管理ツール
- psql
  付属のコマンドライン・プログラム。
  SQLを直接入力・ファイルから読み込んで入力できる他、
  スキーマ情報の表示などのメタコマンドを持つ。

- pgAdmin
  GUIの管理インターフェース。
  
- phpPgAdmin
  ウェブベースの管理ツール。PHPで作られておりGPLで配布されている。
  
### 機能
#### バックアップ、リカバリ、レプリケーション
- オンラインバックアップ
- PITR(Point In Time Recovery)
- レプリケーション
  
### 制限
- 
  |----------------------+--------------------------------------------------------------------------------------|
  | 項目                 | 制限                                                                                 |
  |----------------------+--------------------------------------------------------------------------------------|
  | データベースの大きさ | 無制限                                                                               |
  | テーブルの大きさ     | 最大32[Tbyte]                                                                        |
  | テーブルのレコード数 | 無制限。ただしテーブルの大きさは32[Tbyte]以内                                        |
  | テーブルのカラム数   | 最大1600。データ型に依存（全カラムのデータ型合計を8[Kbyte]のブロックに収める必要あり |
  | 1レコードの大きさ    | 通常8[Kbyte]、TOASTを使えば最大1.6[Gbyte]                                            |
  | インデックスの大きさ | 無制限                                                                               |
  |----------------------+--------------------------------------------------------------------------------------|

## Command
- See "Reference" on Manuals
  [[file:PostgreSQL_Documentation.org][PostgreSQL_Documentation.org]]
## Manuals
- [[file:PostgreSQL_Documentation.org][PostgreSQL_Documentation.org]]
## Architecture
- [[https://speakerdeck.com/soudai/postgresql-architecture-and-performance-monitoring?slide=19][PostgreSQL Architecture And Performance Monitoring - speakerdeck]]
- [[https://www.slideshare.net/uptimejp/postgresql-6872500][PostgreSQLアーキテクチャ入門 - SlideShare]] ※2011年時点の情報
- https://morizyun.github.io/database/postgresql-basic-architecture.html
### 構成要素
#### プロセス群
##### マスターサーバ
- 最初に起動される親プロセス
##### writer / ライタ
- ディスク（テーブルファイル、インデックスファイル）に共有バッファの内容を非同期に書き戻す。
##### wal writer / WALライタ
- WALバッファの内容をWALファイルに書き出す
##### チェックポインタ
- 全てのダーティーページをデータファイルに書き出す
##### 自動VACUUMランチャ
- 設定にしたがって自動VACUUMワーカを起動する
##### 自動VACUUMワーカ
- 自動VACUUMを実行する。複数起動することがある。
##### stat collector / 統計情報コレクタ
- データベースの活動状況に関する統計情報を収集する
##### バックエンドプロセス
- クライアントの接続要求ごとに起動し、要求に対して処理する
##### logger / ロガー
- PostgreSQLのログをファイルへ書き出す
##### archiver / アーカイバ
- WALログをアーカイブする
##### wal sender / WALセンダ
- レプリケーション時にWALをスレーブサーバから転送する
##### wal receiver / WALレシーバ
- レプリケーション時にWALをマスターサーバから受信する
##### Old
###### postmaster ⇒ postgres
- リスナープロセス。
  クライアントからの接続を受け認証処理を行い、Postgresプロセスを生成して処理を引き渡す。
###### postgres
- クライアントに対して1:1で存在。
  構文解析、最適化、実行、結果返却を行う。
#### メモリ群
##### shared_buffers / 共有バッファ
- テーブルやインデックスのデータをキャッシュする領域
##### wal_buffers / WALバッファ
- ディスクに書きこまれていないトランザクションログをキャッシュする領域
##### Visibility Map / 可視性マップ
- テーブルのデータが参照できるか否か管理する情報を扱う領域。
##### Free Scan Map / 空き容量マップ
- テーブル上の利用可能な領域を指し示す情報を扱う領域。
##### トランザクション制御情報
#### ファイル群
##### 設定ファイル
##### テーブルファイル
- 8kB単位のブロックで管理、ブロックの中に実データレコードを配置
- 基本的に追記のみ。
  削除したら削除マークをつけ、VACUUMで回収。
- テーブルのページヘッダは24byte固定
  アイテムポインタ(行ヘッダ)は28byte
##### INDEXファイル
- 8kB単位のブロックをノードとする論理的なツリー構造
##### WALファイル
- Write Ahead Logging, トランザクションログのこと。
- 更新情報が記載される。
  共有バッファのデータ更新「前」に記録
- 16MBずつのセグメントに分割されている
- pg_xlog/(pg10からはpg_wal)以下に配置され、リカバリ時に読み込まれる。
##### アーカイブログファイル
## Structure
### -9.6
#### InstalledDir
##### data
###### base/
- データ領域。データベースのデータを格納
####### nnnnn/
- データベース、テーブルスペース。
  紐付は以下で確認可能(oidがフォルダ名となる)。
  "select datname, oid from pg_database;"
######## nnnnn
- オブジェクト。以下でファイル名との紐付確認が可能。
  "select relname, relfilenode from pg_class;"
######## nnnnn_fsm
- free space map
######## nnnnn_vm
- visibility map
###### global/
- 
###### pg_clog/
###### pg_log/
- log
###### pg_multixact/
###### pg_notify/
###### pg_serial/
###### pg_snapshots/
###### pg_stat_tmp/
###### pg_tblspc/
###### pg_twophase/
###### pg_xlog/
- WALログ
###### pg_hba.conf
###### pg_ident.conf
###### PG_VERSION
###### postgresql.conf
###### postmaster.opts
## Performance
- [[https://taityo-diary.hatenablog.jp/entry/2017/09/10/091729][PostgreSQLの実行計画を読み解くための参考資料集 - ぱと隊長日誌]]
## Security
- [[https://www.slideshare.net/uptimejp/postgresql-54761353][PostgreSQLセキュリティ総復習 - SlideShare]]
## Tools
### pgtool-II
- サーバとクライアントの間で稼働するMW。
- 機能
  - コネクションプーリング
  - レプリケーション
  - ロードバランス
- [[http://www.pgpool.net/mediawiki/jp/index.php/%E3%83%A1%E3%82%A4%E3%83%B3%E3%83%9A%E3%83%BC%E3%82%B8][pgtool-II wiki]]
### pgBouncer
- Lightweight connection pooler
#### Link
- https://github.com/pgbouncer/pgbouncer
- https://pgbouncer.github.io/
- https://wiki.postgresql.org/wiki/PgBouncer
### pgAdmin
- Management Software
#### pgAdmin4
#### pgAdmin3
#### Link
- https://www.pgadmin.org/
## Etc
### current_date
- 変数だろう。ただし今欄がない。

### DISTINCT

### OVER
- 
  window関数で使われる。
  （そのうち項目をSQL Commandにでも移すかも。）

## Glossary
### Relation
- 狭義・もしくは一般にはテーブルのことだが、Postgresでは広義の意味で各種データ構造についても利用される。
- 
  |----------------------------|
  |                            |
  |----------------------------|
  | Relation Relation          |
  | Index Relation             |
  | Sequence Relation          |
  | Toast Relation             |
  | View Relation              |
  | Compositetype Relation     |
  | Foreign Table Relation     |
  | Materialized View Relation |
  |----------------------------|

- http://www.nminoru.jp/~nminoru/postgresql/pg-table-and-block-structure.html#relation
### Fork
- FSM, VISIBILITYMAP, INIT。
  http://www.nminoru.jp/~nminoru/postgresql/pg-table-and-block-structure.html#relation
### Tuple
- 行、Row、Recordのこと。
## Error
### psqlでencodingに関連するエラー
#### エラー内容: character with byte sequence 0xe3 0x82 0x94 in encoding has no ～
- UTF8の内容を別のエンコーディングへ変換する際、同じ表示項目が存在せずエラーとなる。
- 対応
  "\encoding"で現在の設定を確認。
  "\encoding utf8"とすることでエンコーディングをUTF8に変更可能。
- https://kenpg.bitbucket.io/blog/201601/12.html

#### エラー内容: character with byte sequence 0x81 in encoding "WIN1252" has no equivalent in encoding "UTF8"
- WIN1251の0x81に該当するコードが、UTF8にはありませんよ、というエラー。
  この場合クライアントがWIN1252、サーバがUTF8設定。
- 対応
  - 2: 0x81は、全角スペース？だったため、削除して再度実行。
  
#### 符号化方式"UTF8"で無効なバイトシーケンスです
- COPYコマンドでファイルの文字コードを指定すればよい。
  今回は、encoding 'UTF8'にずっとしていたが、ファイルはSJISだったため、encoding 'SJIS'として取り込むことで対応。
  https://kenpg.bitbucket.io/blog/201601/12.html
## Reverse lookup
### 設定値関連
#### 設定
- システム全体: alter system set (parameter) = (value)
- 実行時: set (parameter) = (value) ※実行時パラメータ
#### 確認
- show {name|ALL}
- select * from pg_settings; (view)
#### 反映
- GUI
  - "PostgreSQL X.X"を右クリックして"Reload Configuration"
- CUI
  - SIGHUPを投げるとリロードするとのこと。方法は色々ある。
    - pg_ctl reload [-D PGDATA]
    - pg_ctl kill HUP PID
  - select pg_reload_conf(); --システム管理関数
### データベースの複製
- コマンド:
  - createdb -T ORG_DB_NAME NEW_DB_NAME (createdb --template=template db)
  - https://qiita.com/tatataiki/items/e6208ab36d35356f1f55
- クエリ:
  - CREATE DATABASE 新DB名 TEMPLATE 複製元のDB名
  - https://whitemitt.com/2012/04/14-113046.htm
### データベースとフォルダ、テーブルとファイル名の関係を取得
- データベース、テーブルスペースの紐付は以下で確認可能(oidがフォルダ名)。
  "select datname, oid from pg_database;"
- オブジェクト。以下でファイル名との紐付確認が可能。
  "select relname, relfilenode from pg_class;"
### テーブル名等の一覧を取得
- information_schemaを利用
  →どのような情報が取得されるか不明。
    また、最新Verでの推奨法かも不明。
- pg_tablesなどを利用
### テーブル定義の取得
- information_schema.columnsを取得する。
  http://landhere.jp/blog/a169.html
### 各種定義を確認(psql)
- \d table_name (or index_name, etc...)
### テーブルの複製
- CREATE TABLE new_table AS SELECT * FROM present_table;
### テーブルスペースの確認
- select * from pg_tablespace;
- \db
### テーブルスペースが作成できない場合(Windows)
- Permission deniedの場合、WindowsではAuthenticated_Usersに権限をつける。
- https://www21.atwiki.jp/ohden/pages/628.html

### テーブルスペースの作成
- テーブルスペースの作成自体は、CREATE TABLESPACE tablespacename LOCATION 'directory';といったところ。
### テーブルスペースの変更
- テーブルの変更はALTER TABLE tablename SET TABLESPACE tablespacename;
### NASなどの利用
- レジストリで"HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\postgresql-9.1"(一例)以下のImagePathを変更する。
  例: "postgresql-91" -D "//isln-1/share/work/pgpsql/daat" -w
  initdbやテーブルスペースにはUNCは利用できないが、ベースディレクトリにはUNCが利用可能な模様。  
  https://ml.postgresql.jp/pipermail/pgsql-jp/2012-August/016156.html
### インデックスの一覧を表示
- SELECT tablename, indexname from pg_indexes;
- https://hacknote.jp/archives/2474/
### 実行クエリをログ取得したい場合
- ログに残す:
  postgresql.confのlog_statementを修正する。
### 接続中のセッションを調べる
- SELECT * from pg_stat_activity;
### セッションを切る
- SELECT pg_terminate_backend(processID);
### 制約を調べる
### メッセージを表示する(PL/pgSQL)
- RAISEを利用してメッセージを表示可能。
- https://db.just4fun.biz/?PL/pgSQL/%E3%82%BF%E3%83%BC%E3%83%9F%E3%83%8A%E3%83%AB%E3%81%AB%E3%83%A1%E3%83%83%E3%82%BB%E3%83%BC%E3%82%B8%E3%82%92%E8%A1%A8%E7%A4%BA%E3%81%99%E3%82%8B
### postgresql.confの設定値
- booleanはtrue/falseでなくon/offで設定する。
### psqlの接続時引数
- -h hostname : ホスト名
- -d dbname : 接続先DB
- -U username : 接続ユーザ

- -c command : コマンド実行
- -o filename : 出力ファイル
### psqlのバッチ設定
#### パスワードの入力を省略
- 環境変数"PGPASSWORD"を設定することで、デフォルトのパスワード名を設定可能。
- https://qiita.com/met_ganchan13/items/2af29ba1f6da87199de0
#### クライアント・psqlの文字化け対処
- 環境変数"PGCLIENTENCODING=sjis"を設定することで、cmdと同様のsjisを設定しておくことができる。
  https://qiita.com/hoxo_m/items/1ef8666ab939fd68ed72
- psqlにログインできる場合は、\encoding
### psqlで標準出力
- qechoを使う。echoではない。
### psqlでファイル出力
- psql -c "command" >> out.txtがよい。
- psql -o out.txt -c "command" だと、毎回新規に書き込みにいくので、複数回同じファイルでは不可。
  -cでなく、psql内で動作し続ける場合は可。
- psql > \o out.txt も、-oと同様の動き。
- https://stackoverflow.com/questions/19114346/export-from-postgresql-multiple-times-to-same-file
### psqlのよく使うコマンド
- https://dev.classmethod.jp/server-side/db/postgresql-organize-command/
### ArchiveLogの削除タイミング
- basebackupで作成したbackup_labelよりも古いものは不要。
  pg_archivecleanupも利用可能だが、結局walのバージョンは指定が必要。
### timeoutを設定
- SET statement_timeout TO 1000; (1000ms -> 1s)
- RESET statement_timeout
### TRIM
- trim, rtrim, ltrim, btrim
  https://www.postgresql.jp/document/9.6/html/functions-string.html
### Extension(拡張)関連
#### 現在設定中の拡張を調べる。
- \dx
- select * from pg_extension;
- https://stackoverflow.com/questions/21799956/using-psql-how-do-i-list-extensions-installed-in-a-database

- デフォルトではpl_pgsqlのみ設定されている。
#### 利用可能な拡張を調べる
- select * from pg_available_extensions;
#### 拡張の追加・削除
- CREATE / DROP EXTENSION extension_name;
### ロケールの確認
- pg_settingsから'lc%'を取得
  SELECT name, setting, context FROM pg_settings WHERE name LIKE 'lc%';
### エンコーディングを設定
- psql, client
  \encoding utf8
### 列の追加・削除
- 追加: ALTER TABLE tablename [ADD | DROP] COLUMN columnname type;
- 削除: ALTER TABLE tablename [ADD | DROP] COLUMN columnname {CASCADE};
### テーブルに設定したオプションを調べる
- テーブルごとに設定した"autovacuum_enabled=0"などを調べるには、"d+ tablename"を実行すると確認できる。
### Windows版・インストール後にデータの場所を変える
- https://kenpg.bitbucket.io/blog/201506/04.html
## Memo
### Uninstall(Windows)
- 
  1. [コントロールパネル]から削除
  2. フォルダを削除(C:\Program Files\PostgreSQLなど)
  3. 「postgres」ユーザアカウントを削除
     - net user postgres /delete
     - [コントロールパネル]->[ユーザアカウント]から。

### 冗長化
#### pgpool-II
- DBクラスタを抽象化する。
- 更新は両方に行う。
- 参照は
  一つで運用すると単一障害点となり得るが、pgtool-II自体を冗長化可能。

#### DRBD + Pacemaker
- DRBD : 分散
#### Replication + Pacemaker
- Replicatoin : 9.0以降で利用できる本体組み込みレプリケーション機能
  
#### WSFC
- https://ml.postgresql.jp/pipermail/pgsql-jp/2013-July/016400.html
#### Link
- [[http://www.slideshare.net/SoudaiSone/db-34069118][PostgreSQLの冗長化について - SlideShare]]
### Ubuntuでの設定
- aptで取得したdbのsuperuserはpostgres。下記のようにpostgresユーザとして接続が必要。
  sudo -u postgres psql postgres
- https://help.ubuntu.com/community/PostgreSQL
### 一部の行を取得する
- LIMIT、OFFSETを利用する。
  OFFSETは飛ばす数、LIMITは限度数。
  OFFSET 10は最初の10行を飛ばして他を返す。LIMIT 20は20行分返す。
### 文字列型の使い分け
- https://lets.postgresql.jp/documents/technical/text-processing/1
### 依存関係の確認
- CASCADEなしで実行した場合のエラーメッセージに、依存関係にあるオブジェクトが表示される。
  その後DROP ~ CASCADE;として、依存関係を確認したうえでオブジェクトを削除するのがよい。
  
### COPYコマンド
- メタコマンド: \COPY
  - 1行で書く必要あり。
  - 出力ファイルは絶対パス指定。
  - サーバが読み書き込みを行うのでなく、psqlがファイルの読み書きやシステム間データ送信をおこなう。
  - COPYに比べると効率が悪い。（すべてのデータをクライアント/サーバ接続を通じてやり取りするため）
- コマンド: COPY
  - 複数行で記述可能。
  - 出力ファイルは相対パス指定。
  - \COPYに比べて効率がよい。
### ベースバックアップの状態確認
- [[http://server-helper.doorblog.jp/archives/3202048.html][【PostgreSQL】ベースバックアップの状態確認について - インフラエンジニアのメモ]]
- ベースバックアップが実行中であるかの確認方法はあるのか。
  - /var/lib/pgsql/data/backup_ラベル という名前のファイルがある場合には、pg_start_backup のあと、pg_stop_backup が実行されていない状況ということになります。
  - Windowsで確認したところ、data配下にbackup_labelというファイルが作成され、中に情報が書かれていた。

## Link
- [[https://www.postgresql.org/docs/9.6/static/][PostgreSQL 9.6.10 Documentation]]
- [[https://www.postgresql.jp/document/9.6/html/index.html][PostgreSQL 9.6.5文書]]
- [[http://www.postgresql.org/][PostgreSQL]]
- [[https://wiki.postgresql.org/wiki/Main_Page][PostgreSQL Wiki]]

- [[http://lets.postgresql.jp/][Let's Postgres]]
- [[http://lets.postgresql.jp/documents/tutorial/centos/2][CentOSでPostgreSQLを使ってみよう!(2)]]

- [[https://thinkit.co.jp/series/4975][徹底比較!! Oracle & PostgreSQL 記事一覧 - Think IT]]

- [[http://pgtune.leopard.in.ua/][pgtune]]

- [[https://www.postgresqlinternals.org][PostgreSQL Internals]]
- [[https://www.slideshare.net/uptimejp/postgresql-6872500][PostgreSQLアーキテクチャ入門 - SlideShare]]

## EnterpriseDB
### 比較
 - 
   [[http://www.enterprisedb.co.jp/products-services-training/products/postgres-plus-advanced-server][PostgreSQLとPostgres Plus Advanced Serverの比較 - EDB]]

 - 主な違い
   PostgreSQLの全機能とアップデートに加え、以下が含まれる。
   - セキュリティ機能
   - パフォーマンス機能
   - 開発者向け機能
   - データベース管理者向け機能
   - Oracleとの互換性
   - 企業ツール

### Features
 - 
   [[http://www.enterprisedb.com/docs/en/9.4/eeguide/toc.html][Postgres Plus Enterprise Edition Guide v9.4 - EDB]]

#### Introduction

#### Database Administration

#### Enhanced SQL Features

#### Security

#### EDB Resource Manager

#### Database Utilities

#### Open Client Library

#### Performance Analysis and Tuning

#### Built-In Utility Packages

#### Expanded Catalog Views

#### System catalog Tables

#### Appendix
