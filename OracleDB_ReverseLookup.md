# Oracle Reverse Lookup
## Setting
### OracleDBの一覧
- "/etc/oratab"に記述がある。
  手動でCREATE DATABASEを作った場合は、反映されていない場合がある。
## Status
### 接続インスタンスの状態
- select * from v$instance;
#### インスタンスの状態確認
- 
  以下のコマンドで確認する。
  select STATUS from v$instance;
  ⇒
  shutdown : エラー(ORA-01034: ORACLE not available)
  nomount  : STARTED
  mount    : MOUNTED
  open     : open

- 
  [[http://ooltcloud.expressweb.jp/201212/article_18230921.html][【Oracle】データベースの状態の変更と確認方法 - オールトの雲]]
### アーカイブログ設定
- モード切替(mount状態で)
  - alter database archivelog;
  - alter database noarchivelog;
- モード確認
  select log_mode from v$database;
  archive log list
- 出力先の確認
  show parameter log_archive_dest
### 初期化パラメータの確認
- 現在使用中のすべてのパラメータ
  SHOW PARAMETERS
- 現在使用している特定のパラメータ
  SHOW PARAMETERS [parameter name]
- 動的パフォーマンスビューからの表示
  select * from v$parameter;
  select * from v$parameter2; --行出力
  select * from gv$parameter;
- http://www.atmarkit.co.jp/fdb/ref/ref_oracle/param.html
## SQL
### 制約
#### 制約の追加
- ALTER TABLE table_name ADD CONSTRAINT const_name constraint(column_name);
#### 制約の削除
- ALETR TABLE table_name DROP CONSTRAINT const_name;
#### 制約の有効/無効
- ALTER TABLE table_name [ENABLE|DISABLE] CONSTRAINT const_name;
#### NULL制約の変更
- ALTER TABLE table_name MODIFY (column_name {NOT} NULL)
### 日時
#### 現在日時の取得
- TIMESTAMP WITH ZONE
  - CURRENT_TIMESTAMP
  - SYSDATETIME
- TIMESTAMP
  - LOCALTIME
- DATE
  - CURRENT_DATE
  - SYSDATE

- 違い
  - OSの現在日時
    - SYSDATETIME, SYSDATE
  - セッションのタイムゾーン
    - CURRENT_TIMESTAMP, LOCALTIME, CURRENT_DATE

#### リテラル表記
- TIMESTAMP
  TIMESTAMP 'YYYY-MM-DD HH:MM:DD.xx(max:9)'
- DATE
  DATE 'YYYY-MM-DD'
- INTERVAL
  
### キャッシュクリア
- 共有プール(SHARED POOL)
  ALTER SYSTEM FLUSH SHARED_POOL;
  - SGAの「共有プール」上のすべてのデータをフラッシュする。
    - 対象
      - データディクショナリ
      - SHARED SQL AREA
      - SHARED PL/SQL AREA
      - ストアド・サブプログラム
      - トリガー
      - （実行中のキャッシュは削除されない）
- バッファキャッシュ(10g以降)
  ALTER SYSTEM FLUSH BUFFER_CACHE;
### コンパイル
- 単体
  ALETR PROCEDURE procedure_name COMPILE;
  ALTER PACKAGE package_name COMPILE [PACKAGE/BODY];
- 全体 （スキーマ名を省略すると全スキーマを対象にINVALIDなオブジェクトをコンパイルする）
  CALL UTL.RECOMP.RECOMP_SERIAL('schema_name');
  or
  EXECUTE UTL.RECOMP.RECOMP_SERIAL('schema_name');
  or
  EXECUTE DBMS_UTILITY.COMPILE_SCHEMA('schema_name');
### 実行履歴の確認
- V$SQLのSQL_TEXT列を確認する。SQL_TEXTに入っているのは最初の1000文字で、CLOB型のSQL_FULLTEXTには全テキストが入っている。
- V$SQLTEXTのSQL_TEXTを確認する。VARCHAR2(64)で、テキストの一部分。
### コメントの削除
- 削除コマンドは存在しないので、空文字で上書きすることとなる。
  COMMENT ON COLUMN table.column is '';
### PLUSTRACEロール
- PLUSTRACEロールの作成方法
  @$ORACLE_HOME/sqlplus/admin/plustrce.sql
### テーブル一覧の表示
- 古い方法（非推奨）
  SELECT TNAME FROM TAB;
- 普通の方法
  SELECT TABLE_NAME FROM USER_TABLES;
### ユーザパスワード
- 状態確認
  select * from DBA_USERS;
  (account_status列)

- ロック解除
  ALTER USER <username> ACCOUNT UNLOCK;

- パスワード再設定
  ALTER USER <username> IDENTIFIED BY <password>;

## Failure 障害
### ログ確認
#### ログパスの確認
- select * from v$diag_info;
  - アラートログ : Diag Alert
  - トレースログ : Diag Trace
  - インシデントログ : Diag Incident

- リスナーログ
  - "# lsnrctl status"
    (select * from v$diag_info;
     ⇒<ADR Base>/diag/tnslsnr/<hostname>/listener/trace/listener.log)

- スタートアップ
  <$ORACLE_HOME>/startup.log

#### 監査ログ
### リスナー
#### 状態確認
- # lsnrctl status
- # lsnrctl services
- # tnsping localhost
### データベース
- Status
  - select STATUS from v$instance;
  - 10, 15
### Link
- [[http://www.atmarkit.co.jp/ait/series/2416/][Oracleバックアップ/リカバリ講座 - @IT]]
- [[http://www.atmarkit.co.jp/ait/articles/0806/30/news118.html][Oracleトラブル対策の基礎知識 - @IT]]
- [[http://www.atmarkit.co.jp/ait/articles/0406/25/news101.html][Oracleパフォーマンス障害の克服 - @IT]]
- [[http://www.shift-the-oracle.com/oerrs/][Oracle エラーの代表的な原因と具体的な対応方法 - SHIFT the ORacle]]
## Performance
### 統計情報の取得
- set autotrace on [explain|statistics]
  (or set autotrace traceonly)
- set autotrace off
## IO
### 結果の出力
- SPOOL filename
- SPOOL OFF
## Query
### テーブルに関連したインデックスを確認する
- 
  select INDEX_NAME, TABLE_NAME form dba_ind_columns;

### テーブルスペースのサイズを確認する
- 
  set linesize 200
  set pagesize 1000
  set colsep ‘|’
  
  col TABLESPACE_NAME for a20
  col TOTAL(GB)       for 999,990.9
  col USED(GB)        for 999,990.9
  col USED(%)         for 990.9
  
  select TABLESPACE_NAME,
         TABLESPACE_SIZE/1024/1024/1024 “TOTAL(GB)”,
         USED_SPACE/1024/1024/1024 “USED(GB)”,
         USED_PERCENT “USED(%)”
  from DBA_TABLESPACE_USAGE_METRICS
### テーブルスペースに属するオブジェクトを確認する
- 
  select segment_name, segment_type, tablespace_name
    from dba_segments
   where tablespace_name like 'ABCDE%'
  ;

- 種類を調べる
  select segment_type, count(*)
    from dba_segments
   where tablespace_name like 'ABCDE%'
   group by segment_type
  ;

### ファイルとテーブルスペースの関係を調べる
- 
  SELECT FILE_NAME, TABLESPACE_NAME FROM DBA_DATA_FILES;
  (WHEREでFILE_NAMEやTABLESPACE_NAMEを絞り込む)
### ブロックサイズを確認する
