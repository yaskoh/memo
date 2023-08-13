# Kusto Query Language
-  
## リファレンス
- [[https://docs.microsoft.com/ja-jp/azure/data-explorer/kusto/concepts/][Kustoの概要]]
### エンティティ
#### クラスター
#### データベース
- データを保持する名前付きエンティティ     
##### テーブル参照
- そのテーブル名を使用して産所う
- ["teblename"]としてエスケープする方法もある。
- データベース、またはデータベースとクラスターを明示的に参照することも可能。
  - cluster("https://help.kusto.windows.net").database("Samples").StormEvents
      
#### テーブル
#### 列
#### ストアド関数
#### 外部テーブル
### データ型
- データ型は、スカラーデータ型とユーザー定義レコードのいずれか。
#### スカラー データ型
##### bool / boolean
##### datetime / date
##### dynamic
##### guid
##### int
##### long
##### real / double
##### string
##### timespan / time
##### decimal
### 関数
- ストアド関数、クエリ定義関数、組み込み関数、がある。
### クエリ ステートメント
- Azure Data Explorerではサポートされているが、Azure Monitorでは未サポート。
#### ユーザークエリステートメント
##### let
##### set
##### テーブル式
#### アプリケーションクエリステートメント
##### alias
##### pattern
##### クエリパラメーター
##### restrict
### テーブル演算子
#### as
#### consume
#### count
 - テーブルの行数が返される
#### datatable
#### dstinct
#### evaluate
#### extend
 - 元の列をすべて結果セットに保存し、追加の列を定義する
#### externaldata
#### facet
#### find
#### fork
#### getschema
#### invoke
#### join
#### limit
#### lookup
#### make-series
#### mv-apply
#### mv-expand
#### order
#### project
 - 結果に含める特定の列を選択する。
#### project-away
#### project-keep
#### project-rename
#### project-reorder
#### parse
#### parse-where
#### partition
#### print
#### range
#### reduce
#### render
 - 結果がグラフィックで表現され、出力される。
#### sample
#### sample-distinct
#### scan
#### search
 - search in (tableName) "searchWord"
#### serialize
#### sort
#### summarize
 - 行のグループを集計する
#### take
 - 最大で指定のデータ行数まで返される
#### top
#### top-nested
#### top-hitters
#### union
#### where
### 特殊な関数
#### cluster
#### database()
#### external_table()
#### materialize()
#### materialized_view()
#### table()
#### toscalar()
### スカラー演算子
#### ビットごとの演算子
##### binary_and
##### binary_not
##### binary_or
##### binary_shift_left
##### binary_shift_right
##### binary_xor
#### datetime/timespanの演算子
#### 論理演算子
#### 数値演算子
#### 文字列演算子
#### between演算子
#### not-between演算子
### スカラー関数
#### ago()
#### bin()
#### case()
#### dcount_hll()
#### extract()
#### startofweek()
#### todynamic(), parse_json()
### 集計関数
#### arg_max()
#### dcount()
#### dcountif()
#### makeset()
#### mv-expand()
#### percentiles()
#### pivot()
#### top-nested
### ウィンドウ関数
#### next()
#### prev()
#### row_cumsum()
#### row_number()
#### row_rank()
#### row_window_session()
### 時系列分析
#### make-series
## 管理コマンド
## 例
### Application Gatewayで
AzureDiagnostics
| where ResourceProvider == "MICROSOFT.NETWORK" and Category == "ApplicationGatewayFirewallLog"
| summarize count() by ruleId_s, bin(TimeGenerated, 5m)
| where count_ > 0
| render timechart 

## Link
- [[https://docs.microsoft.com/ja-jp/azure/data-explorer/kusto/concepts/][Kustoの概要]]
- [[https://docs.microsoft.com/ja-jp/azure/azure-monitor/logs/get-started-queries][Azure Monitor でログ クエリの使用を開始する]]
- [[https://docs.microsoft.com/ja-jp/azure/data-explorer/kusto/query/tutorial?pivots=azuremonitor][チュートリアル:Azure Data Explorer と Azure Monitor で Kusto クエリを使用する]]
- [[https://docs.microsoft.com/ja-jp/azure/data-explorer/write-queries][Azure データ エクスプローラーのクエリを記述する]]
  
