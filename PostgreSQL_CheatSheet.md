# PostgreSQL Cheat Sheet
## /* on shell - commands like psql, etc */
psql {-f filename | -c command} -U username -h hostname -d dbname -o outputfile -f filename

set PGPASSWORD=""

psql -l  # see database list
export PG_DATA=/usr/local/var/postgres  #set postgers location

pg_ctl [start|stop] #pg server startup / stop

createuser -P username
createdb dbName -O userNameOfOwner

### on Mac
initdb /usr/local/var/postgres -E utf8  #init db on utf-8
postgres -D /usr/local/var/postgres     #manual startup

- uninstall
  open /Library/PostgreSQL/9.6/uninstall-postgresql.app  #if binary set up is made
  https://nektony.com/how-to/uninstall-postgresql-on-mac

## /* on psql - meta command */
\l : list of databases
\d : list of tables, etc
\c <database> : connec to the database
\conninfo : connection information

\encoding utf8
\o outputfile
\i queryscriptfile

## /* query */
### /* set parameters */
alter system set (parameter) = (value)
set (parameter) = (value) -- �ꎞ�I
show {name|ALL}

select pg_reload_conf();

### /* create user|role */
CREATE ROLE username LOGIN ...;
### /* create database */
CREATE DATABASE databaseName WITH OWNER = ownerName ...;

### /* alter */
#### table
alter table {tablename} rename to {renamedname};
alter table {tablename} add column {colname} {type};
alter table {tablename} drop column {colname};

#### index
alter index {indexname} set tablespace {tablespace_name}

### /* slow query */
log_min_duration_statement

### /* show locale */
- encoding
  psql -l
  \l
  select * from pg_database;
- locale
  select name, setting, context from pg_settings where name like 'lc%';
### /* auto_explain */
auto_explain.log_min_duration
auto_explain.verbose

### explain

### /* prewarm */
select pg_prewarm('program','buffer')

### /* Sequence */
- functions
  - lastval('regclass') -- �ŐV�l
  - nextval('regclass') -- ������߂���A�V�����l
  - setval('regclass',bigint[,iscalled]) -- �V�[�P���X�̌��ݒl��ݒ�

### /* copy */
#### copy to
#### copy from
#### \copy to
psql -U raapp -c "\copy tablename (col1, col2, col3) FROM 'file.csv' (FORMAT csv, HEADER true, ENCODING 'UTF8')" dbname >> %tnum%_in.log
#### \copy from
### /* tablespace */
create tablespace spacef location 'C:\\windows\\directory\\path';
drop tablespace spacef;

### /* get ids */
- SELECT datid, datname FROM pg_stat_database;
- SELECT relid, relname FROM pg_stat_all_tables;
- SELECT oid, * FROM pg_tablespace;

## /* data 20181225 */
select * 
 from pg_class where relname in ('', '');

select * 
 from pg_indexes where tablename like '%%' and indexdef like '%%';

select * 
 from pg_stats where tablename in ('', '')
and attname = '';

-- check current process
select pid, state, client_port, query_start, wait_event_type, query, * 
 from pg_stat_activity where datname = '';

select * from pg_stat_all_tables
 where relname = '';

select * from pg_stat_user_tables;

-- kill process
SELECT pg_terminate_backend(62655);

-- settings
show statement_timeout;
alter system set statement_timeout = 0;
set effective_cache_size = 100; --�����s���p�����[�^�̐ݒ�

select pg_reload_conf();
