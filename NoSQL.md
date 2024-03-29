# NoSQL
## Classification / 分類
### Column / 列指向 ワイドカラムストア
#### Apache HBase
##### 特徴
- 
  Hadoop上で動作する。

  HadoopがGoogle File SystemとMapReduceの実装だったのに対し、
  HBaseはBigTableのオープンソース実装といえる。

  - Big Table
    - Big Tableは"スパース"で分散され、永続性のある、多次元ソートマップである。
    - 各"マップ"はソートされた行キー、カラムキー、タイムスタンプでインデックスされ、値は解釈されていないバイト列

- 高いスケーラビリティ
  単純にサーバ台数を増やすことで拡張可能。
- シャーディングによる負荷の分散
  リージョンに格納されたデータに対する処理を、各サーバで並列に実行可能。
- 強い一貫性
  結果整合性モデルと異なり、書き込みがあった後の読み出しで、必ず書き込んだデータが読めることをシステム全体で保証している。
- 自動フェールオーバーによる高可用性
  HDFSが高可用性構成に対応しており、単一障害点はない。
- シンプルなAPI
  基本的にGet, Put, Scan程度の簡単なAPIしか用意されていない。
- Hadoopとの親和性
  Hadoopクラスタ上に構築され、HDFSに格納される。
  

##### 実装
- Region Server : データを格納・処理する
- Master : メタデータを管理し、各サーバを調整する
- ZooKeeper : 構成情報を管理する

- 構造
  行、列、タイムスタンプという多次元の要素からなるキーと、そこから一意に定まる値のペアがデータ構造を表現している。

- 
  データは行キーでソートされた状態で格納されている。
  行キーの範囲を基準として"リージョン"という単位に分割され、
  各リージョンはクラスタ内のRegion Sererに分散して格納、処理される。

  さらにカラムは"カラムファミリー"という単位でグループ化され、各カラムファミリーは独立したメモリ領域やファイルのセットを管理する。


##### Folder
###### bin
- start-hbase.sh
  - provinding a convinient way to start HBase.
- stop-hbase.sh
  - stop HBase deamons.
- hbase.cmd
  - command
  - hbase shell
    Connect to HBase instance using HBase Shell.

###### conf
- hbase-env.sh
  - "JAVA_HOME" should be set to a directory which contains "bin/java", which is usually /usr.

- hbase-site.xml
  - By default, new directory, where HBase and Zookeeper write data, is created under /tmp.
    /tmp are usually deleted on many servers every time rebooting, and you should set other place to save data.
    Write settings from <property> tags beneath the <configuration> tags.
  
##### HBase Shell Command
###### help
- 
  display some basic usage information for HBase Shell

###### create
- 
  create a new table. Specify the table name and the ColumnFamily name.
  ex) create 'test', 'cf'

###### list
- 
  list information about a table
  ex) list 'test'

###### put
- 
  put data into a table.
 set tablename,  row, column, and value.
  ex) put 'test', 'row1', 'cf:a', 'value1'

###### scan
- 
  one of the way to get data from HBase.
  ex) scan 'test'

###### get
- 
  Use "get" to get a single row of data at a time.
  ex) get 'test', 'row1'

###### disable
- 
  Disable table first for deleting or changing the table.
  ex)disable 'test'

###### enable
- 
  Enable a table.
  ex)enable 'test'

###### drop
- 
  Delete (drop) a table.
  ex)drop 'test'

###### quit
- 
  Exit the HBase Shell and disconnect from the cluster.
  HBase is still running in the background.

##### Link
- [[http://hbase.apache.org/book.html][Apache HBase Rference Guide]]      

#### Apache Cassandra
- [[file:Cassandra.org][Cassandra.org]]
### Document / ドキュメント指向
#### MongoDB
##### 特徴
- 
  JSONに似た形式でデータを格納する。
  整合性は担保されない。

- キーバリューよりも複雑なデータが簡単に扱える
- データ構造の変更が柔軟
- エンジニアでなくても全貌がわかる
- ウェブサービスやM2Mの標準的なデータ構造

##### memo
- 
  32bit OSでは、mongodbのver3はインストールできない。
  32bitのubuntuではダメで、64bit版のdebianでダウンロードしたら取得できた。
  
#### Couchbase

### Key-Value / キー・バリュー
#### Riak
#### Redis

### Graph / グラフ
#### Neo4j
##### Link
- [[https://neo4j.com/][neo4j]]
- tmp
  - [[http://engineer.wantedly.com/2014/01/02/neo4j-introduction.html][グラフDBのNeo4jを1日触ってみた - Wantedly Engineer Blog]]
## Link
- [[https://medium.baqend.com/nosql-databases-a-survey-and-decision-guidance-ea7823a822d#.x7otznnfv][NoSQL Databases: a Survey and Decision Guidance]]
- [[http://dev.classmethod.jp/event/dbtechsowcase-tokyo-2015-e-22/][(レポート)NoSQLの必要性と主要プロダクト比較]]

