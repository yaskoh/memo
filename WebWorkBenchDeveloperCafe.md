# WebWorkBench Develoer Cafe
## API
### 1.30_210
#### jp.co.tenartni
- WWB全体で利用するクラスを集めたパッケージ
##### Classes
###### VersionInfo
- WWB製品のバージョン情報を管理するクラス
###### WRCVersionINfo
- ReportCafe製品のバージョン情報を管理するクラス
###### WWBSystemProperty
- WWBで使用するシステムプロパティ定義クラス
##### Exceptions
###### WWBException
- WWB製品で発生する例外の親クラス
#### jp.co.tenartni.data
#### jp.co.tenartni.data.txt
#### jp.co.tenartni.data.validator
#### jp.co.tenartni.log
#### jp.co.tenartni.log.log4j
#### jp.co.tenartni.sql
- SQLの実行などに関するパッケージ
##### Interfaces
###### databaseMetaDataCache
###### SQLResolvingListener
##### Classes
###### DatabaseMetaDataCacheImpl
###### SQLRowSet
####### About
- SQL問い合わせ(SELECT文)を実行し、結果データを保持するXRowSet実装クラス。
- 継承関係
  java.lang.Object
  > jp.co.tenartni.data.DataHandler
  > jp.co.tenartni.data.XRowSet
- インターフェース
  java.io.Serializable
####### Fields
######## jdbcResultSet
######## resultSetColumnNames
######## UNKNOWN_COLUMN_NAME
####### Methods
######## SQLRowSet()
- コンストラクタ

###### SQLUpdate
###### STPUpdate
##### Exceptions
#### jp.co.tenartni.sql.helper
#### jp.co.tenartni.util
#### jp.co.tenartni.util.res
#### jp.co.tenartni.xqa
##### Classes
###### ClientRowSet
- データベースから取得したデータを行×列の形式で保持するクラス
  取得だけでなく更新も可能
####### Fields
####### Methods
######## ClinentRowSet()
- public ClientRowSet()
- Constractor
######## 
##### Exceptions
#### jp.co.tenartni.xqa.external
#### jp.co.tenartni.xsv
##### Interfaces
##### Classes
###### HtmlTableHandler
- HTMLの表データの自動生成を行ったり、Webブラウザからの入力データの管理を行うクラス。
####### Fields
####### Methods
######## HtmlTableHandler()
- Constractor
######## 
##### Exceptions
#### jp.co.tenartni.xsvif
#### jp.co.tenartni.xxml

### old
#### 1.30_200
##### jp.co.tenartni
##### jp.co.tenartni.data
##### jp.co.tenartni.data.txt
##### jp.co.tenartni.data.validator
##### jp.co.tenartni.log
##### jp.co.tenartni.log.log4j
##### jp.co.tenartni.sql
- SQLの実行などに関するパッケージ
###### Interfaces
####### databaseMetaDataCache
####### SQLResolvingListener
###### Classes
####### DatabaseMetaDataCacheImpl
####### SQLRowSet
######## About
- SQL問い合わせ(SELECT文)を実行し、結果データを保持するXRowSet実装クラス。
- 継承関係
  java.lang.Object
  > jp.co.tenartni.data.DataHandler
  > jp.co.tenartni.data.XRowSet
- インターフェース
  java.io.Serializable
######## Fields
######### jdbcResultSet
######### resultSetColumnNames
######### UNKNOWN_COLUMN_NAME
######## Methods
######### SQLRowSet()
- コンストラクタ

####### SQLUpdate
####### STPUpdate
###### Exceptions
##### jp.co.tenartni.sql.helper
##### jp.co.tenartni.util
##### jp.co.tenartni.util.res
##### jp.co.tenartni.xqa
###### Classes
####### ClientRowSet
- データベースから取得したデータを行×列の形式で保持するクラス
  取得だけでなく更新も可能
######## Fields
######## Methods
######### ClinentRowSet()
- public ClientRowSet()
- Constractor
######### 
###### Exceptions
##### jp.co.tenartni.xqa.external
##### jp.co.tenartni.xsv
###### Interfaces
###### Classes
####### HtmlTableHandler
- HTMLの表データの自動生成を行ったり、Webブラウザからの入力データの管理を行うクラス。
######## Fields
######## Methods
######### HtmlTableHandler()
- Constractor
######### 
###### Exceptions
##### jp.co.tenartni.xsvif
##### jp.co.tenartni.xxml

## link
- [[http://www.tenartni.com/man/wdc/130se/][WebWorkBench DeveloperCafe ver.1.30_201]]
- [[http://www.tenartni.com/man/wdc/130se/api/index.html][WebWorkBench DeveloperCafe StandardEdition ver.1.30_200 API]]
