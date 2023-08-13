# Oracle Utilities
- [[https://docs.oracle.com/cd/E16338_01/server.112/b56303/toc.htm][Oracle® Databaseユーティリティ 11gリリース2 (11.2)]]
## 第Ⅰ部 Oracle Data Pump
### 1 Oracle Data Pumpの概要
### 2 データ・ポンプ・エクスポート
#### エクスポート・ユーティリティのコマンドライン・モードでの使用可能なパラメータ
##### CLUSTER
- データポンプでOracle RACを使用できるかどうか、ワーカーを他のRACインスタンス上で開始できるかどうかを決定する。
- デフォルト: YES
##### CONTENT
- エクスポート・ユーティリティでアンロードする内容を、データのみ、メタデータのみ（あるいはその両方）でフィルタ処理できる。
- デフォルト: ALL
- CONTENT = [ALL | DATA_ONLY | METADATA_ONLY]
##### DIRECTORY
- エクスポート・ユーティリティによるダンプ・ファイル・セットおよびログ・ファイルのデフォルトの書込み先を指定
- デフォルト: DATA_PUMP_DIR
##### DUMPFILE
- 名前を指定する
- デフォルト: expdat.dmp
##### FILESIZE
- 各ダンプ・ファイルの最大サイズを指定する。
- デフォルト: 0(最大サイズの16TB)
##### FULL
- 全体データベース・モード・エクスポートの実行を指定する。
- FULL = [YES | NO]
- 注意:
  全体モード・エクスポートによって作成されたダンプ・ファイルを後でインポートする場合、SYSアカウントのパスワードをソース・データベースからコピーしようとするが、失敗する場合がある。
  失敗した場合はインポートの完了後に、ターゲット・データベース上のSYSアカウントのパスワードを任意のパスワードに設定すル必要がある。
##### LOGFILE
- エクスポート・ジョブのログ・ファイルの名前を指定する。
- デフォルト: export.log
##### PARALLEL
- エクスポート・ジョブのために動作するアクティブな実行プロセスの最大数を指定する。
- デフォルト: 1
##### SCHEMAS
- スキーマ・モード・エクスポートの実行を指定する。
### 3 データ・ポンプ・インポート
#### インポート・ユーティリティのコマンドライン・モードでの使用可能なパラメータ
##### CLUSTER
##### CONTENT
##### DIRECTORY
##### DUMPFILE
##### EXCLUDE
##### INCLUDE
##### LOGFILE
##### PARALLEL
##### SCHEMAS
- スキーマ・モード・インポートの実行を指定する
- 構文
  SCHEMAS=schema_name
##### REMAP_SCHEMA
- ソース・スキーマにあるすべてにあるすべてのオブジェクトをターゲット・スキーマにロードする。
- 構文
  REMAP_SCHEMA=source_schema:target_schema
##### REMAP_TABLESPACE
- インポート操作中に、表の名前を変更できる。
- 構文
  REMAP_TABLESPACE=source_tablespace:target_tablespace
##### TABLE_EXISTS_ACTION
- インポート・ユーティリティに対して、作成しようとしている表がすでに存在している場合に行う操作を指定する。
- 構文
  TABLE_EXISTS_ACTION = [SKIP | APPEND | TRUNCATE | REPLACE]
### 4 データ・ポンプのレガシーモード
### 5 データ・ポンプ・ユーティリティのパフォーマンス
### 6 データ・ポンプAPI
## 第Ⅱ部 SQL*Loaderの概要
## 第Ⅲ部 外部表
## 第Ⅳ部 その他のユーティリティ
### 16 ADRCI
### 17 DBVERIFY
### 18 DBNEWID
### 19 LogMiner
### 20 メタデータAPIの使用
### 21 オリジナルのエクスポート
### 21 オリジナルのインポート
