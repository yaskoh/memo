# SQL Server
## Command
### DBCC
- dbcc ind
    隠しコマンド。インデックスのページ割り当て等の情報を見ることができる。
    dbcc ind ( { 'dbname' | dbid }, { 'objname' | objid }, { nonclustered indid | 1 | 0 | -1 | -2 } [, partition_number] )

- dbcc page
    隠しコマンド。ページIDを指定することでページの中身を見ることができる。
    dbcc page ( {'dbname' | dbid}, filenum, pagenum [, printopt={0|1|2|3} ])
    プリントオプションは以下。
        0:ページヘッダのみ 1:ページヘッダ＋データ部 2:ページヘッダ＋データ部の16進ダンプ 3:各行を個別に出力
    出力するためにはトレースフラグ3604を有効にする必要がある。
    
- dbcc help('name')
    nameで指定されたdbccコマンドの構文情報を返す。

- dbcc traceon(数字) / dbcc traceoff(数字)
    指定されたトレースフラグを有効/無効にする。
    カンマ区切りで複数指定可。最後に-1を列挙すると、グローバルに設定が反映される。

- dbcc tracestatus
    トレースフラグの状態を出力する。
    DBCC TRACESTATUS ( [ [ trace# [ ,...n ] ] [ , ] [ -1 ] ] ) [ WITH NO_INFOMSGS ]

- dbcc showcontig
    テーブル・ビューとインデックスの断片化情報を表示する。
    削除予定機能。ただし、代替とされているdm_db_index_physical_statsではエクステントの断片化を見ることができない。

- dbcc opentran(DB名)
    DB内にアクティブなトランザクションが存在するか否かを確認できる。

### Procedure
- sp_helptext 'procedure'
    プロシージャの内容を出力する。

- sp_MSforeachdb / sp_MSforeachtable
    すべてのdb/tableに対して操作を行うことができる。
    ex: sp_MSforeachdb @command1="select '?'"
        ->'?'が補完され、master, tempdb,等のselect結果が返ってくる。
    @command1以外にも、@command2/3, @whereand, @replacechar, @precommand, @postcommandがある。

### 動的管理ビュー

- sys.dm_db_index_physical_stats
    指定したテーブルまたはビューとインデックスに関する、サイズおよび断片化情報を返す。

- sys.dm_tran_locks
    ロックマネージャの情報を返す。

### システムビュー
- システムビュー

  - カタログビュー
  - 情報スキーマビュー
  - 互換性ビュー
  - レプリケーションビュー
  - 動的管理ビューと動的管理関数
  - データ層アプリケーションのビュー

#### カタログビュー

## Built-in Functions
- 組込関数

	関数の種類
		行セット関数
		集計関数
		順位付け関数
		スカラー関数
			構成関数
			変換関数
			カーソル関数
			日付と時刻のデータ型及び関数
			論理関数
			数学関数
			メタデータ関数
			セキュリティ関数
			文字列関数
			システム関数
			システム統計関数
			テキストとイメージ関数



-------------------------------------------------------------

- 行セット関数
	テーブル参照の代わりに使用できるオブジェクトを返す。

	OPENDATASOURCE

	OPENQUERY

	OPENROWEST

	OPENXML



- 集計関数
	値の集まりに対し計算を実行し、1つの値を返す。
	決定的(deterministic)。

	AVG
		平均値
	CHECKSUM_AGG
		チェックサムを返す。テーブルの変更を検出する場合などに使用。
	COUNT
		件数を返す。戻り値はint型。
	COUNT_BIG
		件数を返す。bigintを返す。COUNTと動きは同じ。
	GROUPING
		rollupやcube、grouping setsを使った場合に返されるnullを区別する。
	GROUPING_ID
	MAX
	MIN
	SUM
	STDEV
	STDEVP
	VAR
	VARP

## memo

### GROUPING SETS
- GROUP BY句で、どの単位でまとめるか複数の選択が可能。
  rollupやcubeだけでなく、柔軟な設定ができる。

### データベースの種類
- master
  インスタンスレベルの構成情報やログインなどのセキュリティ情報
- model
  ユーザーデータベースのテンプレート
- msdb
  ジョブやスケジューリング関連情報
- tempdb
  一時テーブルやソートデータなどの格納
  パフォーマンスが要求されるため、専用のボリュームへ配置する。
  多数並行してtempdbのクエリが実行される場合、スペース管理をする特定のページにて
  競合が発生することが知られている。
  サイズが同じデータファイルをプロセッサと同数配置することで緩和できる。
  ドライブは分けなくともよい。
- resource
  システムメタデータ（表示されないが、binn内にmssqlsystemresource.mdf/ldfが存在
- ユーザdb
  ユーザが作成したもの。


### 復旧モデル
- 完全(Full)復旧モデル
  トランザクションログへ全ての処理履歴を完全に記録する。
  Standard以上のデフォルト。
- 一括ログ(Bulk Logged)復旧モデル
  バルク操作する際のパフォーマンスを向上するために、
  ログの記録を最小限に抑えるモデル。
  完全モデルの補完
- 単純(Simple)復旧モデル
  チェックポイント時のログ切捨て。
  チェックポイントが完了する毎に
  現在実行しているトランザクション以外のログを切り捨てる。


### 設定変更手段
- SQL Server構成マネージャ
  起動アカウント、起動モード等
- SQL Server Management Studio Object Explorer
  いつものSSMS。認証モード等、これでのみ変更可能なオプションあり。
- サーバオプション(sp_configue)
- DDLやシステムストアドプロシージャ
  自動拡張の設定など

※照合順序と導入フォルダは、導入後の変更が難しい。


### 書き込みキャッシュ
- 
  書き込みキャッシュと拡張処理能力で、
  ディスクの書き込みがキャッシュされるか否か、
  およびFlush/Write-Throughコマンドを使用するか否か設定する。


### パーティション開始位置
- 
  パーティションの開始位置をMBR後の64番目のセクタから開始するとパフォーマンスが向上する場合あり。
  Diskpart起動、"LIST DISK"で確認、"SELECT DISK X"、"Create Partition Primary Align = 64"とかする。


### インスタントコピー機能
- スプリットミラー方式
  ミラーリングしていたRAIDアレイを、ミラーリングを解くことで瞬時に分割、バックアップとする。
  コピー前に同期が完了している必要があるため、バックアップ時は高速だが、普段はミラーリングのオーバーヘッドが発生する。
- コピーオンライト(Copy-On-Write,COW)方式
  書き換えがあった時に、元のデータを退避する方式。
  コピー前の準備時間は不要だが、実際のコピーが完了する際は時間がかかる。
上記をSQL Serverスナップショットバックアップで利用できるか、製品ごとに異なるので確認する必要あり。


### データサイズ
- 
  データブロックの大きさはでかい方がよいので、I/Oパターンから考えるに64KでNTFSをフォーマットするとよい。

### ファイルグループ
- 
  以下の場合にファイルグループを分ける意味あり。
  1. I/Oが集中するテーブルを他から分ける。
  2. 特定のデータをリストアする要件あり。
  3. パーティションテーブルを個別のファイルグループへ（運用が柔軟になることがある）
  4. 管理上、業務ごとにデータを分けたい。
  5. 特定のファイルグループをRead_onlyにしたい。

### Read_Only
- 
  データベース単位だけでなく、ファイルグループ単位でRead_onlyに設定できる。


### ネーミングルール
- 標準識別子
  - 先頭文字
    Unicode3.2の文字、及び_,@,#を使用可
    @で始まる識別子はローカル変数またはローカルパラメータ
    @@で始まる識別子が、一部のTransact-SQLで使われる。
    #で始まる識別子は一時テーブルまたは一時プロシージャ
    ##で始まる識別子はグローバルな一時オブジェクト
  - 先頭以外
    Unicode3.2、および各国の10進数、_,@,#,$を使用可能
- 区切られた識別子
  標準識別子でないもの。[]か""で囲んで使用する必要がある。


### ページ
- 
  8KB。
  先頭96Byteがページヘッダ、そのあとがデータ。
  ページヘッダにはテーブル識別し等のシステム情報やペ−ジばんごう、ページ上の空き容量、前後のページへのポインタ等が含まれる。
  末尾から「行オフセットテーブル」が始まる。データ行の方向と逆方向に登録される。
  単一のオブジェクトのみに割り当てられる。

### エクステント
- 
  8ページで1エクステント。64KB。
  - 混合エクステント
    複数のオブジェクトが入ったエクステント。
    テーブルページやインデックスページが混ざっているもの。
    新しいテーブルやインデックスを作成すると、まずは混合エクステントが作成される。
    8ページまで拡張すると、単一エクステントに切り替わる。
  - 単一エクステント
    単一のオブジェクトで構成されたエクステント。
    テーブルのエクステントなら、テーブルのページのみ8つが含まれる。
  I/Oアクセスは、基本1ページまたは1エクステント単位で行われる。更に大きい場合もあり。


### データ型
#### 真数
- bigint, bit, decimal, int, numeric, smallint, money, tinyint, smallmoney
#### 概数
- float, real
#### 日付、時刻
- datetime, smalldate, date, time, datetime2, datetimeoffset
#### 文字列
- char, text, varchar
#### Unicode型
- nchar, ntext, nvarchar
#### バイナリ
- binary, image, varbinary
#### 空間データ型
- geometry, geography
#### その他
- cursor, timestamp, sql_variant, uniqueidentifier, table, xml, hierarchyd

#### 優先順位
- 
  異なるデータ型同士で演算を行った場合、優先順位の高いデータ型にあわせて変換される。
  sql_variant, xml, datetimeoffset, datetime2, datetime, smalldatetime, date, time, float, real, decimal, money, smallmoney,
  bigint, int, smallint, tinyint, bit, ntext, text, image, timestamp, uniqueidentifier, nvarchar, char, varvinary, binary


### IDENTITY
- ロールバックした際に欠番が発生する可能性がある。
- 列の一意性を保つ機能ではないため、別途PRIMARY KEY制約やUNIQUE制約と合わせて使用する必要あり。


### 行
- 
  行の最大サイズは8,060Byte。ページサイズからの制限。
  例外として、varchar, nvarchar, varbinary列を含む場合は行あたり8,060Byteを超えられる。
  ただし、各列の長さが8,000Byteに収まる必要がある。


### rebulid, reorganize
- 
  reorganizeはトランザクションによる管理ができないため、
  ユーザトランザクションの内部で使わない。
  commit, rollbackしても結果が変わらないだけでなく、
  トランザクションの影響で、エクステントに対してロックがかかってしまう。
  rebuildはトランザクションによる管理が可能で、commit, rollbackに対応する。
  online処理にすると、実行中の参照･更新が可能だが、実行後はユーザトランザクション中はロックのままとなる。



### バージョン
- 
  'select @@version'でバージョンを取得できる。

  |-----------------------------------+----------------|
  | リリース                          | 製品バージョン |
  |-----------------------------------+----------------|
  | SQL Server 2014 RTM               |   12.0.2000.80 |
  | SQL Server 2012 Service Pack 1    |  11.00.3000.00 |
  | SQL Server 2012 RTM               |  11.00.2100.60 |
  | SQL Server 2008 R2 Service Pack 2 |   10.50.4000.0 |
  | SQL Server 2008 R2 Service Pack 1 |   10.50.2500.0 |
  | SQL Server 2008 R2 RTM            |   10.50.1600.1 |
  | SQL Server 2008 Service Pack 3    |  10.00.5500.00 |
  | SQL Server 2008 Service Pack 2    |  10.00.4000.00 |
  | SQL Server 2008 Service Pack 1    |  10.00.2531.00 |
  | SQL Server 2008 RTM               |  10.00.1600.22 |
  | SQL Server 2005 Service Pack 4    |   9.00.5500.00 |
  | SQL Server 2005 Service Pack 3    |      9.00.4035 |
  | SQL Server 2005 Service Pack 2    |      9.00.3042 |
  | SQL Server 2005 Service Pack 1    |      9.00.2047 |
  | SQL Server 2005 RTM               |      9.00.1399 |
  | SQL Server 2000 Service Pack 4    |      8.00.2039 |
  | SQL Server 2000 Service Pack 3    |       8.00.760 |
  | SQL Server 2000 Service Pack 2    |       8.00.534 |
  | SQL Server 2000 Service Pack 1    |       8.00.384 |
  | SQL Server 2000 RTM               |       8.00.194 |
  |-----------------------------------+----------------|
  
  [[https://support.microsoft.com/ja-jp/kb/321185][SQL Serverとそのコンポーネントのバージョンとエディションを確認する方法]]

- 用語
  - RTM : Release To asufacturing
  - RTW : Release To Web
