# Resin
## Commands
- see "Command Line"
- [[http://caucho.com/resin-4.0/admin/resin-admin-command-line.xtp][command line resin administration - Resin Documentation]]
## Structure
### Unix
#### /etc/resin/
##### resin.properties
- Configuration properties
##### resin.xml
##### licenses/
##### keys/
#### /var/resin/
##### webapps/
#### /var/log/resin/
#### /usr/local/share/resin/
### Windows
#### resin.exe
- 実行ファイル。サーバが起動。
#### conf/
##### resin.properties
- configuration variable values
  resin.xmlなどで使う変数を定義している。
- jvm_args : インストール値に応じたメモリ値、ヒープ最大サイズを設定する。
- app.http : ポート番号。必要に応じ変更する。
- remote_admin_enable : 
- cluster_system_key : 
##### resin.xml
- 
##### licenses/
- licens location
##### keys/
- openssl keys
#### log/
- logs
##### access.log
##### (service).log
##### watchdog-manager.log
#### resin-data/
#### webapps/
- default deployment directory
## Manual
### admin/configuration
#### Configuration
##### resin.properties
- http://caucho.com/resin-4.0/admin/config-resin-properties.xtp
###### Properties
##### resin.xml
###### Properties
####### cluster
######## id="app"
######### host-default
########## web-app-deploy
###### Link
- http://caucho.com/resin-4.0/admin/config-resin-xml.xtp
#### Command Line
- http://www.caucho.com/resin-4.0/admin/resin-admin-command-line.xtp#webappstartstartingapplication
##### enabling commands
- set resin.xml files settings.
##### available commands
###### deploy
###### undeploy
###### deploy-list
###### deploy-copy
###### restart-webapp
- Start an application with
- resinctl webap-stop [option] <name>
###### start-webapp
- Starting application
- resinctl webap-stop [option] <name>
###### stop-webapp
- Stop an applicatoion
- resinctl webap-stop [option] <name>
###### restart-webapp
###### heap-dump
###### thread-dump
###### profile
###### jmx-list
###### jmx-dump
###### jmx-set
###### jmx-call
###### log-level
###### pdf-report
#### Logging
##### Overview
- using "java.util.logging"
- Resin uses the JDK standard java.util.logging for all its internal logging,
  and configuration for the logging format and the logging level.
##### Log names
###### ""
- Debug everything
###### com.caucho.ejb
- EJB handling
###### com.caucho.jsp
- Debug jsp
###### com.caucho.java
###### com.caucho.server.port
###### com.caucho.server.http
###### com.caucho.server.webapp
###### com.caucho.server.cache
###### com.caucho.sql
###### com.caucho.transaction
##### Log level
###### off
###### severe
###### warning
###### info
###### config
###### fine
###### finner
###### finest
###### all
#### Health
##### Health Checking
###### Configuration
###### <health:HealthSystem>
###### Health checks
###### Health actions
###### Health conditions
####### Basic conditions
####### Cobining conditions
####### Health check conditions
####### Lifecycle conditions
##### Meters
##### Report
##### Watchdog
#### Web Server
##### HTTP server
##### Virtual Hosts
##### Web Applications
##### Proxy Cache
### development
### Reference
#### <close-dangling-connection>
- child of <database>
#### <connection>
- child of <database>
##### Attributes
###### catalog
###### read-only
###### transaction-isolation
#### <connection-wait-time>
- child of <database>
#### <database>
- child of <resin>, <cluster>, <host>, <web-app>
##### Attributes
###### jndi-name
#### <driver>
- child of <database>
#### <max-active-time>
- child of <database>
#### <max-close-statement>
- child of <database>
#### <max-connections>
- child of <database>
#### <max-create-connections>
- child of <database>
#### <max-idle-time>
- child of <database>
#### <max-overflow-connections>
- child of <database>
#### <max-pool-time>
- child of <database>
#### <password>
- child of <database>
#### <ping>
- child of <database>
#### <ping-table>
- child of <database>
#### <transaction-timeout>
- child of <database>
#### <logger>
##### Parents
- child of <resin>, <cluster>, <host>, <web-app>
##### Attributes
###### level
- the java.util.logging level: finest, finer, fine, config, info, warning, severe
- default : info
###### name
- the java.util.logging name, typically a classname
###### use-parent-handlers
- if true, parent handlers are also invoked
## Deployment
### Webapps Directory
- Copy a .war file containing application to a webapps directory.
  Resin will detect the .war archive, expand it, and start serving requests.
### Command-Line
### Cloud
## Source
### 4.0.56
#### modules/
##### c/
##### resin/
###### src/
####### com/caucho/
######## resin/
## Memo
### Intramart
#### Resinでクラスタを組む
- Resinでクラスタを組む場合、ライセンスが必要となる。
  Try版などで提供されるライセンスが登録されていないResinではクラスタを組むことができない。
  https://www.intra-mart.jp/download/product/iap/iap_release_note/texts/limitations/resin.html
### resin-dataについて
- [[https://www.slideshare.net/open-intra-mart/resindata-133478090][resin-dataに関する障害について / NTTデータイントラマート開発本部 - SlideShare]]
- [[https://dev.intra-mart.jp/wp-content/uploads/2018/06/resin-data-documents.pdf][resin-dataに関する障害について / NTTデータイントラマート開発本部 (PDF)]]

- [[https://www.caucho.com/resin-4.0/admin/config-resin-data.xtp][resin data directory - Resin Documentation]]

#### resin-dataフォルダ構造
##### app-X
###### .git/
- デプロイされたアプリケーション情報(warファイルの内容)を保持する
- 問題：肥大化
  - 内容：繰り返しデプロイを行うと[.git]ディレクトリ配下が大きくなる
  - 対策：Resinを停止し.gitディレクトリを削除。その後デプロイを再実施
  - 改善策：Resin Deployを利用せず、直接warファイルを配置する。
###### distcache/
- セッションと分散キャッシュ情報を保持する
####### data.db
- セッション情報と分散キャッシュのvalue値を保持する
####### mnode.db
- セッション情報と分散キャッシュのKey/Value構成を保持する
###### log/
- PDFレポートおよびResin-Adminに出力するためのログ情報を保持する
####### log_data.db
- PDFレポートおよびResin-Adminに出力するためのログ情報(実体)を保持する
####### log_name.db
- PDFレポートおよびResin-Adminに出力するためのログ情報(名前)を保持する
###### tmp/
- ファイルサイズの大きいファイル操作の一時ディレクトリ
###### xa.log */
- 分散トランザクションログ

###### stat_data.db
- Resin統計データベースで、PDFレポートおよびResin-Adminにグラフ表示する情報等を保持する
###### stat_name.db
- Resin統計データベースで、PDFレポートおよびResin-Adminにグラフ表示する名前等を保持する
## Link
- [[http://caucho.com/][Resin - caucho]]
- [[http://caucho.com/resin-4.0/][Resin Documentation]]
