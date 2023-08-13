# OracleDB Performance
## Performance
### 実行計画
#### Optimiser オプティマイザ
- 最も効率的な実行計画を決定する
##### CBO コストベース・オプティマイザ
- 情報統計をもとに各アクセス方法のコストを計算して、最もコストが低い実行計画を選び出す方法。
  正確な統計情報がないと、最適な実行計画が生成されないため、統計情報を定期的に更新する必要がある。
##### ルールベース・オプティマイザ
- あらかじめ決められたルールに基づいて最適化された実行計画を作成する方法。
  7.2で仕様凍結後、10gでサポート外となっている。
  
#### アクセス・パス
##### 全表スキャン
- HWM(High Water Mark、最高水位標)までのすべてのデータ・ブロックにアクセスしてすべてのレコードを読み込み、
  指定された条件にマッチするか判定を行う。
##### 索引スキャン
- 索引を読み込んでROWID情報を取得し、そのROWIDを使用して表のレコードにアクセスする。
##### ROWIDスキャン
- 最も高速に目的のレコードにアクセスする方法。
  ROWIDは、DB内の「どのデータ・ファイルの、何番目のデータ・ブロック中の、何番目のレコード」といったレコード位置を表す、Oracleの内部的な表現。
  指定すると直接目的のレコードを含むデータ・ブロックへアクセスできるが、表の移動等でROWIDは変更されるため、検索条件とすることは難しい。
#### 結合方法
- 結合順序も影響を及ぼす
##### ネステッド・ループ結合
- インデックスを使用して結合できるレコードを検索
  最初の1件を返すのが早いため、少数の結果を返す処理に向く。
  外部表からレコードをフェッチし、結合条件に一致するレコードを内部表から検索して結合する。
##### ソート/マージ結合
- 
##### ハッシュ結合
- 結合キーのハッシュ表を最初に作成し、それをもとに結合できるレコードを検索
  最初にフルスキャンが発生するがそれ以降は高速。大量のレコードを扱う場合に向く。
  外部表を読み込んで結合キーのハッシュ表をPGA領域に作成し、そのハッシュ表をもとに内部表を検索して結合する方式。
  PGA領域が不足するとディスクの一時表領域を使うためパフォーマンスが低下するため注意が必要。
  その場合pga_aggregate_targetでPGAサイズを拡張することも検討する。
#### 表示項目
##### Id
##### Operation
##### Name
##### TQ
- 各ステップで処理された行が渡されるテーブル・キューのID
- Format:Q${IDofQC},${IDofTQ}
##### IN-OUT
- プロセス間通信しない方式
  - PCWP : Parallel Combined with Parent
    次のステップも同一のQSが行う
  - PCWC : Parallel Combined with Child
    前のステップと同一のQSが行う
- プロセス間通信する方式
  - P->P : Parallel to Parallel
    QSが次のスレーブ・セットにデータを送る
  - P->S : Parallel to Serial
    QSがQCにデータを送る
  - S->P : Serial to Serial
    QCがQSにデータを送る
##### PQ Distrib
- HASH
- RANGE
- PART(KEY)
  パーティションキーで分散させて各QSに送る
- BROADCAST
  表全体をQSに送る
#### 操作
##### COUNT STOPKEY
- 必要な行数が取り出せた時点で内部的な処理を中断する。
  「最初のN行のみ」
##### FIXED TABLE FULL
##### HASH JOIN
##### INDEX FAST FULL SCAN
##### INDEX RANGE SCAN
##### INDEX UNIQUE SCAN
##### MERGE JOIN
##### NESTED LOOPS
###### ANTI
###### OUTER
###### PARTITION OUTER
###### SEMI
##### PARTITION HASH ALL
##### PX BLOCK ITERATOR
- Parallel slave process - iterates through a set of blocks
##### PX COORDINATOR
- Coordinates parallel statement execution
- パラレル実行のコーディネーター
##### PX SEND
- パラレル・セット間における配分方法の実装。
  ランダム、ハッシュ、レンジによるパーティション化
###### BROADCAST
###### BROADCAST LOCAL
###### HASH
###### PARTITION (KEY)
###### QC (ORDER)
###### QC (RANDOM)
###### RANGE
##### SELECT STATEMENT
##### SORT AGGREGATE
##### SORT JOIN
##### TABLE ACCESS BY INDEX ROWID
##### TABLE ACCESS CLUSTER
##### TABLE ACCESS FULL
- テーブルに対しフルスキャン
##### Link
- [[http://www.juliandyke.com/Optimisation/Operations/Operations.php][Oracle Internals]]
- [[http://www.magata.net/memo/index.php?%BC%C2%B9%D4%B7%D7%B2%E8%A4%CE%C6%C9%A4%DF%CA%FD(Oracle)][実行計画の読み方(Oracle) - 闘うITエンジニアの覚え書き]]
- [[http://www.doppo1.net/oracle/tuning/execute-plan.html][実行計画の解析方法(1) - WalkingAlone]]
- [[http://use-the-index-luke.com/ja/sql/explain-plan/oracle/operations][実行計画の処理 - USE THE INDEX, LUKE]]
### リアルタイムSQL監視
- 実行中のSQL文のパフォーマンスを監視できる。
#### V$ビュー
- V$SQL_MONITOR
- V$SQL_PLAN_MONITOR

- V$ACTIVE_SESSION_HISTORY
- V$SESSION_LONGOPS
- V$SQL
- V$SQL_PLAN
#### 表示項目
- 「実行計画」項目の中身も合わせて確認のこと。
##### 操作
##### オブジェクト
##### オブジェクト・ノード (Parallel時)
##### 順序
##### 行
##### バイト
##### コスト
##### CPU(%)
##### 時間
##### パーティションの開始
##### パーティションの停止
##### TQ (Parallel時)
- テーブルキュー: プロrセス間通信するための構造の総称
##### IN-OUT (Parallel時)
- プロセス間通信の入力と出力
##### PQ配置 / PQ Distrib (Parallel時)
- PX SEND操作のときに出力される。
##### 問い合わせブロック名/オブジェクトの別名
##### 述語
##### フィルタ
##### 予測
### 統計情報
#### 種類
##### 表
- 行数、ブロック数、平均行長
  DBA_TABLESで確認
##### 列
- 列値の種類、NULLの数、データ分布
  DBA_TAB_COLUMNSで確認
##### 索引
- リーフ・ブロック数、階層数、クラスタ化係数
  DBA_INDEXESで確認
##### システム
- CPUパフォーマンスと使用率、I/Oパフォーマンスと使用率
#### 収集
##### 自動統計収集
- 更新が行われた表のみの統計情報を取得する。
##### 手動統計収集
- 特定のオブジェクトみの統計を取得するなど、自分で選ぶことができる。
##### 動的サンプリング
- ハードパース時のSQLの処理に要するメモリとCPUに負荷がかかる。
#### 内容
- [[file:OracleDB_Reference.org][OracleDB_Reference.org]]
  統計情報説明、を参照
#### Link
- [[https://blogs.oracle.com/oracle4engineer/entry/oraclefaq][Oracleの統計情報にまつわる頻出FAQ～概要、確認、収集・取得 - オラクルエンジニア通信 - 技術資料、マニュアル、セミナー]]
- [[http://www.shift-the-oracle.com/sqlplus/tutorial/autotrace.html][SQL*Plus を使った実行計画の取得 - SHIFT the Oracle]]
- [[http://www.atmarkit.co.jp/ait/articles/0410/21/news098_4.html][SQLチューニングの基盤となる統計情報 - Oracle SQLチューニング講座（5） - @IT]]

### オプティマイザ・ヒント
- http://docs.oracle.com/cd/E16338_01/server.112/b56312/hintsref.htm
#### 型
- 単一表
- 複数表
- 問合せブロック
- 文
#### ヒント
##### アクセス・パス
###### FULL
- テーブル全件を読み込ませる
###### CLUSTER
###### HASH
###### INDEX, NO_INDEX
- 指定したインデックスを使ってテーブルを抽出する・しない
###### INDEX_ASC, INDEX_DESC
###### INDEX_COMBINE, INDEX_JOIN
###### INDOX_JOIN
###### INDEX_FFS, NO_INDEX_FFS
###### INDEX_SS, NO_INDEX_SS
###### INDEX_SS_ASC, INDEX_SS_DESC
##### 結合順序
###### LEADING
- ヒント句内に記述された順序の通りに結合を行う
###### ORDERED
- FROM句に記述された順序の通りに結合を行う
##### 結合操作
###### USE_NL, NO_USE_NL
- ネステッドループ結合をする/しない
###### USE_NL_WITH_INDEX
###### USE_MERGE, NO_USE_MERGE
###### USE_HASH, NO_USE_HASH
- ハッシュ結合をさせる・させない
###### NO_USE_HASH
##### オンライン・アプリケーション・アップグレード
###### CHANGE_DUPKEY_ERROR_INDEX
###### IGNORE_ROW_ON_DUPKEY_INDEX
###### RETRY_ON_ROW_CHANGE
##### パラレル実行
###### PARALLEL, NO_PARALLEL
###### PARALLEL_INDEX, NO_PARALLEL_INDEX
###### PQ_DISTRIBUTE
##### 問合せ変数
###### NO_QUERY_TRANSFORMATION
###### USE_CONCAT
###### NO_EXPAND
###### REWRITE, NO_REWRITE
###### MERGE, NO_MERGE
###### STAR_TRANSFORMATION, NO_STAR_TRANSFORMATION
###### FACT, NO_FACT
###### UNNEST, NO_UNNEST
##### その他
###### APPEND, APPEND_VALUES, NOAPPEND
###### CACHE, NOCACHE
###### PUSH_PRED, NO_PUSH_PRED
###### PUSH_SUBQ, NO_PUSH_SUBQ
###### QB_NAME
###### CURSOR_SHARING_EXACT
###### DRIVING_SITE
###### DYNAMIC_SAMPLING
###### MODEL_MIN_ANALYSIS
#### ヒントの書き方
- SELECT /*+ ヒントを書く */
  ...
### List
#### 待機イベント
- [[file:OracleDB_Reference.org][OracleDB_Reference.org]]
##### Memo(待機イベント)
###### 確認方法
- [[http://oracle-pub.wikidot.com/wait-event][待機イベント基礎 - Oracle Pub]]
- V$EVENT_NAME
  待機イベントの種類を知ることができる
- V$SYSTEM_WAIT_CLASS
  待機イベントクラスごとの待機回数と待機時間
###### 待機イベント情報の取得
- V$SESSION
- V$SESSION_WAIT: セッションが現在待機中または待機を完了した直後のイベントを表示する
- V$SYSTEM_EVENT: すべてのセッションがV$SESSION_WAITビューに表示されているイベントを待機した合計回数を表示する
###### UserI/OとWait
- http://www.ex-em.co.jp/oracle-k/oracle-event-%E8%A7%A3%E8%AA%AC/855/
- [[https://www.insight-tec.com/mailmagazine/ora3/vol328.html][待ちイベントに関する検証　その８ - InsightTechnology]]
####### 従来型パスI/O
- SGAのバッファキャッシュにデータが存在しない場合に、サーバプロセスがデータファイルから該当データブロックをバッファ・キャッシュにロードする。
  マルチブロック読み込み方式とシングルブロック読み込み方式に分けられる。
######## マルチブロック読み取り方式
- 1回に幾つかの連続したブロックを読み込む
######## シングルブロック読み取り方式
- 1回に1つのブロックだけを読み込むI/O。
  1回シングル・ブロック読み取りが発生すると、1回のdb file sequential readイベントが発生。

####### sequential read
- ランダムアクセス時。
  単一ブロック読み込みのため、読み込んだデータが（1ブロックなので当然）メモリ上で連続する。
  そのため、"sequential"と表示される。
- タイムアウトは発生せず、読み込み完了まで待機する。

######## 解決策
######### Appレイヤー
######### Oracleメモリ―レイヤー
- バッファキャッシュの大きさが小さすぎる
  慢性的に物理I/Oが発生しdb file sequential read待機が増加することとなる。
  この場合、同時にfree buffer waits待機が発生する確率も高くなる。
- クラスタ化係数(Clustering Factor)が高すぎる
- 行連鎖や行移行が多発
######### I/Oデバイスレイヤー
- V$FILESTATビューを利用することで、データ・ファイルごとにマルチブロック読取とシングルブロック読取の活動性に関する情報を取得できる。
####### scattered read
- シーケンシャル読み込み時。
  複数ブロックを読み込み、それらは連続していないので、"scattered"と表示される。
#### システム統計
- [[http://www.doppo1.net/oracle/tuning/sysstat.html][システム統計一覧 - WalkingAlone]]
### Manual
- 基本的には以下に記載
  [[file:OracleDB_Manuals.org][OracleDB_Manuals.org]]
#### ?
##### 概要
##### パフォーマンス計画
##### インスタンスのパフォーマンス最適化
###### 自動パフォーマンス統計
###### 自動パフォーマンス診断
###### メモリの構成および使用方法
###### I/O構成および設計
###### オペレーティング・システム・リソースの管理
###### パフォーマンス・ビューを使用したインスタンスのチューニング
##### SQL文の最適化
###### 問合せオプティマイザ
###### EXPLAIN PLANの使用方法
###### オプティマイザ統計の管理
###### 索引およびクラスタの使用方法
###### SQL計画の管理の使用方法
###### SQLチューニングの概要
###### 自動SQLチューニング
###### SQLアクセス・アドバイザ
###### オプティマイザ・ヒントの使用方法
###### プラン・スタビリティの使用方法
###### アプリケーション・トレース・ツールの使用方法
### Memo
#### Metrics
##### 2003: User Transaction Per Sec
##### 2004: Physical Reads Per Sec
##### 2005: Physical Reads Per Txn
##### 2006: Physical Writes Per Sec
##### 2016: Redo Generated Per Sec
##### 2017: Redo Generated Per Txn
##### 2018: Logons Per Sec
##### 2026: User Calls Per Sec
##### 2031: Logical Reads Per Txn
##### 2045: Total Parse Count Per Txn
##### 2058: Network Traffic Volume Per Sec
##### 2066: Enqueue Requests Per Txn
##### 2068: DB Block Changes Per Txn
##### 2104: Current Open Cursors Count
##### 2106: SQL Service Response Time
##### 2109: Response Time Per Txn
##### 2121: Executions Per Sec
##### 2144: Average Synchronous Single-Block Read Latency
- The average latency in miliseconds of a synchronous single-block read.
- https://docs.oracle.com/cd/B16240_01/doc/doc.102/e16282/oracle_database_help/oracle_database_instance_throughput_avg_sync_singleblk_read_latency.html
##### 2145: I/O Megabytes per Second
##### 2146: I/O Requests per Second
##### 2147: Average Active Sessions
- AAS
  ロードアベレージ
  DMA(Direct Memory Access)による高頻度なサンプリング方式。
- http://www.oracle.com/technetwork/jp/ondemand/db-new/091028-insight-tuning-250540-ja.pdf
#### OEM Metrics
- https://docs.oracle.com/cd/E17559_01/em.111/b61024/toc.htm
#### Tuningが必要なSQLの洗い出し
- 動的パフォーマンスビューによる洗い出し
  - V$SQL : SQLの累積リソース使用状況
  - V$SQL_TEXT : SQLの全文
  - V$SQL_PLAN : SQLの実行計画
## Tuning
- 以下のような検討を行う(http://www.oracle.com/technetwork/jp/database/articles/tsushima/tsushima-hakushi-38-2236622-ja.html)
  - オプティマイザ統計の再収集（オプティマイザ統計が正しくない
  - 索引の作成（効果的な索引が作成されていない）
  - SQLの変更・ヒントの挿入（複雑なSQLなどで効果的な実行計画にならない）
  - SQL計画ベースラインの設定（ヒントで効果的にできるがSQLを変更できない）
  - SQLチューニング・アドバイザ（どのようにチューニングするか判断できない）
## Tools
### SQL Tuning Advisor / SQLチューニング・アドバイザ
- 1つ以上のSQLに対して自動チューニング・オプティマイザを起動してSQLチューニングを行う。

- 基本はOracle Enterprise Managerを使用。DBMS_SQLTUNEパッケージでも実行可能。

- 実行には、SQLチューニング・アドバイザ・タスクの作成と実行が必要。

#### SQLプロファイル
- より適切な実行計画が生成できるSQLの補助統計情報として、SQLチューニング・アドバイザによって生成される。
#### SQL計画ベースライン
#### Memo
##### 無効化
- DBMS_AUTO_TASK_ADMIN_DISABLEを利用
- http://at-j.co.jp/blog/?p=5503
### 自動チューニング・オプティマイザ
- オプティマイザには、実行計画を作成する標準モードと、標準モードで作成された実行計画をさらに改善できるか分析するチューニング・モードがあり、
  このチューニング・モードを自動チューニング・オプティマイザと呼ぶ。
### 自動SQLチューニング・アドバイザ
- 自動メンテナンス・タスクとして構成される。
  11gから提供。AWRを分析して
#### Memo
- 自動SQLチューニングによるSQL文チューニングの改善
  http://www.oracle.com/webfolder/technetwork/jp/obe/11gr1_db/manage/ast/ast.htm
## Link
- [[http://www.atmarkit.co.jp/ait/series/2413/][Oracle SQLチューニング講座 - @IT]]
- [[http://www.oracle.com/technetwork/jp/articles/index-349908-ja.html][Oracleデータベース 性能対策機能 ～StatspackとDiagnostics Packを使いこなす～ - Oracle Technology Network]]
- [[http://www.oracle.com/technetwork/jp/articles/chapter1-1-085735-ja.html][門外不出のOracle現場ワザ 第１章 目からウロコのOracleパフォーマンス分析テクニック - Oracle Technology Network]]
- [[http://www.oracle.com/webfolder/technetwork/jp/ondemand/ddd2014/A1-4.pdf][オラクル・コンサルが語る！プロフェッショナルのデータベース性能分析手法 AWR/ASHを活用した分析事例 - ORACLE]]
- [[http://www.oracle.com/technetwork/jp/articles/index-088346-ja.html][おら！オラ！Oracle － どっぷり検証生活 現場で役立つOracle DBのパフォーマンスチューニング - Oracle Technology Network]]
- [[http://www.oracle.com/technetwork/jp/ondemand/db-new/091028-insight-tuning-250540-ja.pdf][おら! オラ! Oracle - どっぷり検証生活 - 現場で役立つ Oracle DBのパフォーマンス チューニング(slide)]]

- [[https://docs.oracle.com/en/database/oracle/oracle-database/12.2/tdppt/monitoring-real-time-database-performance.html#GUID-EB19F9B4-A912-4354-8D8D-F89EEFD56704][2 Day + Performance Tuning Guide - ORACLE Help Center]]
