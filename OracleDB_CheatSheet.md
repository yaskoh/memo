# OracleDB Cheat Sheet
## /* sqlplus */
- sqlplus / as dba
- sqlplus username
### COLumn
- COLumn colname NEW_Value varname
  colnameの値をvarnameに格納する。
## /* INSTANCE */
- select instance_name from v$instance; -- 接続先確認
- show parameter instance_name -- 接続先確認
- select STATUS from v$instance;  -- (shutdown, nomount, mount, open)
## /* LOG */
- ALTER DATABASE [archivelog | noarchivelog];
- SELECT log_mode from v$database;
- SHOW PARAMETER log_archive_dest;
## /* PARAMETER */
- SHOW PARAMETERS -- 全てのパラメータの表示
- SHOW PARAMETERS parameterName -- 一部パラメータのみ
- 動的パフォーマンスビュー:
  - select * from v$parameter;
  - select * from v$parameter2;
  - select * from gv$parameter;

## /* USER, SCHEMA */
- DROP USER {username} CASCADE;
- SELECT owner, table_name from {dba_tables | all_tables};

## /* DEPENDENCY */
- SELECT * FROM DBA_DEPENDENCIES;

## /* DATAFILES */
- select data
## /* TABLESPACE */
- DROP TABLESPACE tablespacename INCLUDING CONTENTS AND DATAFILES CASCADE CONSTRAINTS;

- //check segments on the specific tablespace
  select segment_name, segment_type, tablespace_name
    from dba_segments
   where tablespace_name like 'ABCDE%'
  ;

## /* TABLE */
- SELECT * FROM USER_TABLES;
- CREATE TABLE tablename (columnname type, ...)

## /* INDEXES */
## /* CONSTRAINT */
- ALTER TABLE table_name ADD CONSTRAINT const_name constraint(column_name);
- ALETR TABLE table_name DROP CONSTRAINT const_name;
- ALTER TABLE table_name [ENABLE|DISABLE] CONSTRAINT const_name;
- ALTER TABLE table_name MODIFY (column_name {NOT} NULL)

## /* TRIGGER */
- CREATE TRIGGER triggername BEFORE INSERT ON tablename  -- 例
  BEGIN
    transactions;
  END
  ;
- CREATE TRIGGER triggername {BEFORE|AFTER|INSTEADOF} {INSERT|UPDATE|DELETE|(OR ...)+} ON tablename [FOR EACH ROW] transaction...; -- 定義の一部

-- トリガーのenable, disable
- ALTER TRIGGER triggername {DISABLE|ENABLE};
- ALTER TRIGGER tablename {DISABLE|ENABLE} ALL TRIGGERS;

- SELECT trigger_name, status from USER_TRIGGERS; -- 状態の確認
## /* SESSION */
- セッション確認
  select sid, serial#, username, logon_time, schemaname, program,  from v$session;
  [[https://docs.oracle.com/cd/E16338_01/server.112/b56311/dynviews_3016.htm][V$SESSION - Oracle® Databaseリファレンス 11gリリース2 (11.2)]]

- クエリ確認
  select SQL_TEXT from v$sql
  v$sessionとは"SQL_ID"で紐づける。

- プロセスIDの取得
  - select S.SID, S.SERIAL#, P.SPID from V$SESSION S, V$PROCESS P WHERE S.PADDR = P.ADDR

- 切断
  ALTER SYSTEM KILL SESSION 'sid, serialNo[@instanceNo]' [IMMEDIATE];
  orakill <sid> <processid> (※on Windows, cmd)
  
  - Memo
    - IMMEDIATEを付けないとあまりうまく動作しないらしい
    - 11gまではIMMEDIATEもなくうまく動作しなかったらしい、KILLEDマークがつくだけ。
    - DISCONNECTはKILLと大体同じ。
    - 
  - [[https://www.shift-the-oracle.com/alter-system/kill-session-or-disconnect-session.html]]      
  - [[https://qiita.com/RYO-4947123/items/e949f6b31d702439a0ea]]
## /* DIRECTORY */
- grant read, write on directory 
