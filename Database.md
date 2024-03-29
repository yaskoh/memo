# Database
## Type
### RDB
#### Products
##### OracleDB
- [[file:OracleDB.org][OracleDB.org]]
##### SQLServer
- [[file:SQLServer.org][SQLServer.org]]
##### MySQL
- [[file:MySQL.org][MySQL.org]]
##### PostgreSQL
- [[file:PostgreSQL.org][PostgreSQL.org]]
#### Design
##### 手順
###### 永続化（格納）するデータを決定する
###### 異なるデータ間要素の関連（リレーションシップ）の集まりを決定する
###### 論理構造を重ね合わせる
##### 概念設計
- 
  
##### 論理設計
##### 物理設計
- インデックスやキーなどのテーブル定義決定
- データ容量、ディスク容量見積もり
- テーブル配置、スペース定義
- パフォーマンスなどの最適実装の検討
- DDL作成
##### 運用設計
##### Link
- [[http://gihyo.jp/dev/feature/01/database/0001][第1回 データベース設計とは - 初めてのデータベース設計]]
- [[http://www.insight-tec.com/mailmagazine/ora3/vol291.html][Oracle新人のRACインストール その１ - Insight Technology]]
- [[http://nippondanji.blogspot.jp/2013/12/db.html][DB設計の難しさ - 漢のコンピュータ道]]
  - リレーショナルモデルの適用範囲は狭い。
  - リレーショナルモデルの適用範囲は「表」。
  - リレーショナルは「正規化」と「直行性」を利用してやる。
  - リレーショナルモデルで扱えないデータをうまく扱う方法を考えるのが難しい。

#### Log
##### 論理ロギングと物理ロギング
- 
  論理ロギングは、SQL文レベルで変更履歴を管理する。
  物理ロギングは、変更があったデータブロックをバイナリイメージで保存する。
  
  MySQLのバイナリログは前者、InnoDBログは後者。
#### Performance
- DBMS, 特にOLTPでは、ディスクのIOPSが重要と言われている。
  
##### Link
- [[https://use-the-index-luke.com/ja/sql/table-of-contents][USE THE INDEX, LUKE]]

### NoSQL
- [[file:NoSQL.org][NoSQL.org]]
## Tools
### Client software
#### Multi-Platform Client
##### DBeavor
###### Wiki
- https://github.com/dbeaver/dbeaver/wiki
####### General User Guide
######## Installation
######## Application Window Overview
######### Menu Bar
######### Toolbar
######### Shortcut Bar
######### Workspace: Views and Editors
########## Changing Workspace Layout
########## Maximizing, Minimizing and Restoring View and Editors
######## Views
######## Database Object Editor
######## SQL Editor
######## Filters
######## Search
######## Projects
######## Bookmarks
####### Database Management
###### Memo
####### Java was started but returned exit code=1で起動しない
- dbeaver.iniに以下のような項目を追加する。
-VM
C:/Program Files/Java/jdk1.8.0_31/bin/javaw.exe

###### Link
- https://dbeaver.io/
- https://github.com/dbeaver/dbeaver
- https://qiita.com/nanasess/items/609c7cda4adee344221c
##### A5:SQL Mk-2
- https://a5m2.mmatsubara.com/
- http://www.vector.co.jp/soft/dl/winnt/business/se422726.html
##### DataGrip
- https://www.jetbrains.com/datagrip/
##### TeamSQL
- https://teamsql.io/
##### Emacs
- SQLi
  http://emacsredux.com/blog/2013/06/13/using-emacs-as-a-database-client/
  https://truongtx.me/2014/08/23/setup-emacs-as-an-sql-database-client
##### Link
- [[https://geekflare.com/multi-platform-sql-client/][Multi Platform Database Client - GEEK FLARE]]
## Query
- [[file:SQL.org][SQL.org]]
## Glossary
### OLTP
- OnLine Transaction Processing
  
