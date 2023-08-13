# MySQL
## ClientProgram
### mysql
#### About
- MySQLコマンド行実行ツール
#### Options
- https://dev.mysql.com/doc/refman/5.6/ja/mysql-command-options.html
##### --help, -?
- --help, -?
  ヘルプメッセージを出して終了する
  
##### --password, -p
- --password[=password], -p[password]
  サーバに接続する際に使用するパスワード。
  短いオプションを使用する場合は間にスペースは置かない。

##### --user, -u
- --user=user_name, -u user_name
  サーバへの接続時に使用するMySQLユーザ名
#### mysqlCommand
- 
  mysql自身が解釈するコマンド。
  mysql>プロンプトでhelpまたは\hと入力するとリストを確認可能。
##### List
###### ? (\?)
###### clear (\c)
- clear command
###### connect (\r)
###### edit (\e)
###### exit (\q)
- Exit mysql. Same as quit.
###### help (\h)
###### quit (\q)
###### source (\.)
###### status (\s)
###### system (\!)
###### tee (\T)
### mysqladmin
- mysqladmin [options] command [command-arg] [command [command-arg]]
  管理操作を実行するためのクライアント。

#### Command
##### create db_name
##### debug
##### drop db_name
##### extended-status
##### flush-hosts
##### flush-logs
##### kill id, id, ...
##### password new-password
##### ping
- サーバが使用可能かどうかをチェックする。
  サーバーが稼働中の場合はmysqladminのリターンステータスは0となり、稼働していない場合は1となる。
##### processlist
- アクティブなサーバースレッドのリストを表示する。
##### shutdown
- サーバーを停止する。
##### variables
- サーバーシステム変数とその値を表示する
##### version
- サーバーからのバージョン情報を表示する。
#### Option
##### --password, -p
- --password[=password], -p[password]
  サーバーに接続する際に使用するパスワード。

##### --user, -u
- --user=user_name, -u user_name
  サーバーの接続時に使用するMySQLユーザー名。

### mysqlcheck
### mysqldump
### mysqlimport
### mysqlshow
### mysqlslap
## SQL
### Language Structure
### DataType
### Function, Operator
### Statement
### Information Schema
## Storage Engine
### InnoDB
### Alternative
## Settings
### Environmental Variables
#### PATH
## Memo
### バイナリログ
- 
  バイナリログは論理ロギング。
  （InnoDBログは物理ロギング）
  
### テーブル確認
- 
  SHOW TABLES FROM db_name

### Login
- 
  mysql -h hostname -u username -P portnumber

### commands(memo)
- select User from mysql.user;
- grant all privileges on DB名.* to user@"hostname" identified by 'password' with grant option;
- exit
- revoke all privileges on DB名.* to "user"@"host"

#### CREATE USER
- 
  CREATE USER username IDENTIFIED BY 'password';

#### DROP USER
- 
  DROP USER username;

#### CREATE DATABASE
- 
  CERATE DATABASE dbname;
  
#### SHOW DATABASE
- 
  SHOW DATABASES;

#### USE DATABASE
- 
  
### show grants
- 
  show grants for username

### delete "grant usage"
- 
  Usage only user is written in the mysql.user table with all global privileges turned off.
  
  [[http://dba.stackexchange.com/questions/13083/cant-remove-grant-usage][can't remove "GRANT USAGE"]]

### path of my.cnf
- 
  mysql --help | grep my.cnf
  ⇒in this case, files is in /etc/my.cnf

### installation
- CentOS
  sudo yum install mysql-server
  sudo /sbin/server mysqld start
  
  then, run the following command (to be secure)
  sudo /usr/bin/mysql_secure_installation
  
  sudo chkconfig mysqld on
  
### my.cnf and settings files
- 
  there are samples of my.cnf on /usr/share/mysql/.
  |------------------------+--------+----------------------------------|
  | sample file            | memory | usage                            |
  |------------------------+--------+----------------------------------|
  | my-small.cnf           | ~64MB  | small db                         |
  | my-medium.cnf          | ~128MB | shared-small                     |
  | my-large.cnf           | ~512MB | for server mostly used for mysql |
  | my-huge.cnf            | 1G~2G  | for server used for mysql only   |
  | my-innodb-heavy-4G.cnf | 4GB    | InnoDB                           |
  |------------------------+--------+----------------------------------|

### Default Log Location
- 
  /var/log/mysqld.log

### change port on centos
- 
  SELinux disables ports
  - [[http://yu-ya45.hatenablog.com/entry/2013/06/23/193204][CentOS6.4でMySQLのポートを変更するときにはまった - 個人プログラマーの備忘録！]]

## Link
- [[https://dev.mysql.com/doc/refman/5.6/ja/][MySQL 5.6 リファレンスマニュアル - MySQL]]
- [[http://www.rackspace.com/knowledge_center/article/installing-mysql-server-on-centos][Installing MySQL Server on CentOS - Rackspace Support Network]]
