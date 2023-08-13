# Apache Cassandra
## Specification
### Data Model
- すべて4次元か5次元の連想配列のようになっている。
  [keyspace] [ColumnFamily] [key] ([SuperColumn]) [カラム]
- Contents
  - key
  - value
#### keyspace キースペース
- RDBMSでいうところのデータベース。一般に1アプリケーションで1つ使用する。
#### ColumnFamily カラムファミリ
- カラムまたはスーパーカラムの集合を扱う単位。RDBMSのテーブルに相当。
  カラムの集合をrowロウと呼び、ロウにキーを付けて管理する。
  ロウにはカラムが入る場合とスーパーカラムが入る場合があり、一つのカラムファミリにはどちらか片方しか入れることができない。
  各カラムファミリはロウごとにソートされている。
- Contents
  - key
  - value
#### SuperColumn スーパーカラム
- カラムの集合を扱う単位。複数のカラムを束ねて、1つのキーでアクセスできるようになる。
- Contents
  - key : スーパーカラムにアクセスするためのキー
  - value : スーパーカラムで保持するカラムの配列
#### column カラム
- データの最小単位。実際のキーと値、タイムスタンプを持つ。
- Contents
  - name
  - value
  - timestamp
### Architecture
#### Dynamo
##### Replication
###### SimpleStrategy
###### NetworkTopologyStrategy
##### Tunable Consistency
###### Consistency levels
- ONE : Only a single replica must respond.
- TWO : Two replicas must respond.
- THREE : Three replicas must respond.
- QUORUM :
- ALL :
- LOCAL_QUORUM :
- EACH_QUORUM :
- LOCAL_ONE : 
- ANY : 
#### Storage Engine
##### Memtables
- 書き込み時にコミットログに追加で書き込んでいく。
  実体のMemtableはメモリ上にカラムファミリごとに展開する。
  サイズの閾値を持っており、その閾値に達するとディスクに書き出す（フラッシュ）。
- 設定値 : commitlog_directory
##### SSTables
- Memtableのフラッシュにより書き出される構造。
  一度書き出されるとその内容は不変。
- 設定値 : data_file_directories
- 物理データとして以下の3つがセットで書き出される。
  （インデックスとブルームフィルタは読み込みを高速化するための仕組み）
  - インデックス
  - ブルームフィルタ
  - データファイル
## Folder Structure
### 1.1.12
#### Windows
##### bin
###### cassandra
- 本体の起動シェル
###### cassandra.bat
- 実行ファイル(win)
####### Properties
- -Xms : 最小ヒープサイズ
- -Xmx : 最大ヒープサイズ
- -Dcom.sun.management.jmxremote.port : ポート番号
###### cassandra-cli
###### cassandra-cli.bat
- コマンドラインツール。
###### cqlsh
- interactive command-line interface.
##### conf
###### cassandra.yaml
- cluster_name : the name of cluster
- seed_provider
  - class_name
    - seeds : a comma separated list of the IP addresses of cluster seeds
- storage_port : no need to change this. check the port not blocking by firewall.
- listen_address : IP address of node.
- data_file_directories : データの保存場所
- commitlog_drectory : CommitLogの保存場所
- saved_caches_directory : キャッシュデータの保存場所
###### cassandra-env.sh
- set environment variables.
###### log4j-server.properties
- log4j.appender.R.File : logファイルの出力場所
## Commands
### ; (Terminator)
- ;で一文が終了となる。
### help / ?
- Display help
### help <command>
- Display command-specific help
### exit / quit
- Exit utility.
### assume
### connect
- Connect to a Cassandra node.
- ex) connect localhost/9160
### consistencylevel
### count
### create column family
#### Syntax
- create column family <name>;
- create column family <name> with <att1>=<value1>;
- create column family <name> with <att1>=<value1> and <att2>=<value2>...;
#### Parameters
- name : Name of the new column family.
#### Attributes
##### column_metadata
###### Parameters
####### Required
- name
- validator :
  - values are :
    - AsciiType
    - BooleanType
    - CounterColumnType
    - DataType
    - DoubleType
    - FloatType
    - Int32Type
    - IntegerType
    - LexicalUUIDType
    - LongType
    - UTF8Type
    - CompositeType
####### Optional
- index_name
- index_type
- index_options
##### bloom_filter_fp_chance
##### column_type
- Standard or Super, default is Standard.
##### comment
##### comparator
- Validator to use to validate and compare column names in this column family.
##### default_validation_class
##### key_validation_class
##### gc_grace
##### read_repair_chance
##### dclocal_read_repair_chance
##### subcomparator
- Only applied to Super column families.
  Default is ByteType.
##### max_compaction_threshold
##### min_compaction_threshold
##### replicate_on_write
##### compression_options
### create keyspace
- create a keyspace with the specified attribuets.
#### Syntax
- create keyspace <keyspace>;
- create keyspace <keyspace> with <att1>=<value>;
- create keyspace <keyspace> with <att1>=<value> and <att1>=<value> ...;
#### Parameters
- keyspace: "system" is reserved for Cassandra internals.
#### Attributes
##### placement_strategy
- Class used to determine how replicas are distributed among nodes.
###### Supported values
####### SimpleStrategy
####### NetworkTopologyStrategy
####### OldNetworkTopologyStrategy
##### strategy_options
##### durable_writes
### del
### decr
### describe cluster
### describe
### drop column family
### drop keyspace
### drop index
### get
### incr
### list
### set
### show api version
### show cluster name
### show keyspaces
### show schema
### truncate
### update column family
### update keyspace
### use
## CQL / The Cassandra Query Language
### Data Types
### Data Definition
### Data Manipulation
### Secondary Indexes
### Materialized Views
### Security
### Functions
### JSON Support
### Triggers
### Link
- [[http://cassandra.apache.org/doc/latest/cql/index.html#cql][The Cassandra Query Language (CQL)]]
## Environment variables
### CASSANDRA_HOME
- Cassandraのインストール場所
- Default : 現在のディレクトリ
### CASSANDRA_CONF
- Default : %CASSANDRA_HOME%\conf
### CASSANDRA_MAIN
- Default : org.apache.cassandra.thrift.CassandraDaemon
## Configuration
### Link
- [[http://cassandra.apache.org/doc/latest/configuration/cassandra_config_file.html][Cassandra Configuration File - Apache Cassandra]]
## About
- オープンソースの分散データベース管理システム。
  キー・バリュー型のデータストア。
## Link
- [[http://cassandra.apache.org/][Apache Cassandra]]
- [[http://cassandra.apache.org/doc/latest/][Apache Cassandra Documentation]]
- [[https://wiki.apache.org/cassandra/FrontPage][Apache Cassandra Wiki]]
