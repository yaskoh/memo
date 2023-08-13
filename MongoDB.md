# MongoDB
## Shell Commands
### mongo
- データベースへ接続
- usage: mongo [options] [db address] [file name (ending in .js)]
#### Options
## Mongo Commands
### show
#### show dbs
#### show collections
### use [db_name]
### db
- 接続中のデータベース
#### db.createCollection("xxx")
- コレクションの作成
#### db.dropDatabase()
- 現在のDBを削除する
#### db.xxx
- コレクション関連
##### db.xxx.drop()
 - コレクションの削除
##### db.xxx.find()
 - コレクションの確認
##### db.xxx.insertOne()
##### db.xxx.insertMany()
##### db.xxx.deleteOne()
##### db.xxx.update()
## Link
- https://www.mongodb.com/docs/
