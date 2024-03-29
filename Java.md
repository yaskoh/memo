# Java
## Language Specification
- [[file:Java_LangSpec.org][Java_LangSpec.org]]
## History
### Java 8
#### ラムダ式（クロージャ）
#### ForEachメソッド、メソッド参照
#### Stream API
#### Optionalクラス
#### インターフェースのデフォルトメソッド
#### 新Time API
#### Link
- [[http://www.oracle.com/technetwork/jp/java/javase/overview/8-compatibility-guide-2156366-ja.html][JDK 8の互換性ガイド - ORACLE]]
- [[http://qiita.com/Usek/items/8f689d9ad59c0c441626][今更人に聞けないJava5からの新機能(Java SE 8) - Qiita]]
### Java 7
#### NIO2
#### Fork/Join Framework
#### try-with-resources
#### ダイヤモンド記法
- Example
  List<String> l = new ArrayList<>()
#### 例外のマルチキャッチ
- Example
  try {
      ...
  } catch(IOException | ClassNotFoundException e) {
      //IOException or ClassNotFoundException
  }
#### switchの文字列使用
- Example
  switch (test) {
  case "a": case "b":
      System.out.println("a or b");
      break;
  case "test":
      ...
  default:
      ...
  }
#### Link
- [[http://www.oracle.com/technetwork/java/javase/compatibility-417013.html][Java SE 7 and JDK 7 Compatibility - ORACLE]]
- [[http://qiita.com/Usek/items/3b0ae76a08d2f1678884][今更人に聞けないJava5からの新機能(Java SE 7) - Qiita]]
### Java 6
#### Link
- [[http://www.oracle.com/technetwork/java/javase/compatibility-137541.html][Compatibility - ORACLE]]
### Java 5.0
#### Genericsの追加
#### ワイルドカード
#### Autoboxingの追加
#### enumの追加
#### 拡張For文の追加
- 配列もしくはIterableインターフェースを実装したクラスのオブジェクトに適用可能。
#### Annotation
#### Concurrency Utilities
#### 可変長引数
#### static import
#### Link
- [[http://qiita.com/Usek/items/3ff30e7a1a87ba64cb58][今更人に聞けないJava5からの新機能(J2SE 5.0) - Qiita]]
### Java 1.4
### Java 1.3
### Java 1.2
### Java 1.1
### Java 1.0
### Link
- [[https://risaiku.net/archives/1764/][昔のソースコードのリファクタリングでJava 15年間の歴史(Java 1.3～Java 8)を一気に把握！ - risaiku リサイク]]
## Java Platform
### Edition
#### Java SE
- Java Platform, Standard Edition。
  汎用的な用途に使われる。
##### Package
###### General
####### java.lang
######## java.lang.ref
######## java.lang.reflect
####### java.io
####### java.nio
####### java.math
####### java.net
####### java.text
####### java.util
###### Special
####### java.applet
####### java.beans
#### Java EE
- [[file:Java_EE.org][Java_EE.org]]
#### Java ME
- Java Platform, Micro Edition。
  組み込みシステムなどを用途として想定したエディション。
  機器の種類に応じ、ライブラリのいくつかの異なるセット（プロファイル）を規定している。
### 配布形態
#### Java Runtime Environment(JRE)
- 
  Javaを実行するために必要なソフトウェア。
  Java仮想マシン(JVM)とAPIから成る。
  仮想マシンとAPIは互いに互換性がなければならず、共にバンドルされている。
  プログラムを実行するだけであれば、JDKは必要なくJREのみでよい。

##### Java Virtual Machine(JVM)
- 
  Javaバイトコードとして定義された命令セットを実行するスタック型の仮想マシン。

##### Application Programming Interface(API)
- 
  関数群。クラスライブラリ。

#### Java Development Kit(JDK)
- ソフトウェア開発キット。
  Javaプログラムの開発を支援する基本的なソフトウェア。
  各プラットフォームの全ての実装。
  Javaコンパイラ、javadoc、デバッガなどを含む多くの開発ツールを含む。
  Private Runtimeと呼ばれる完全なJREも含む。

##### 内容
- (個別の詳細はJava_SE_Commandを参照)
- appletviewer
- apt
- extcheck
- idlj
- java
- javac
- javadoc
- jar
- javah
- javap
- javaws
- JConsole
- jdb
- jhat
- jinfo
- jmap
- jps
- jrunscript
- jstack
- jstat
- jstand
- keytool
- pack200
- policytool
- VisualVM
- wsimport
- xjc

([[http://ja.wikipedia.org/wiki/Java_Development_Kit][Java DevelopmentKit]])

### Binary
#### Oracle JDK
#### Oracle OpenJDK
#### AdoptOpenJDK
#### GraalVM
#### Amazon Corretto
#### Red Hat OpenJDK
#### Zulu
#### Link
- [[https://qiita.com/nowokay/items/edb5c5df4dbfc4a99ffb][Javaのサポートについてのまとめ - Qiita]]
- [[https://speakerdeck.com/kishida/java-is-still-free?slide=18][Javaは今でも無償です、という話 ]]
## Commands
- [[file:Java_SE_Command.org][Java_SE_Command]]
## Warnings
### Comparing identical expressions
- 同じものを比較。
- 抑止：なし
### finally block does not cemplete normally
- finally中にreturnやthrowなどを記述
- 抑止：@Suppress Warnings("finally")
### Link
- http://kidotaka.hatenablog.com/entry/20091122/1258922844
## API
- [[file:Java_SE_API.org][Java_SE_API]]
## Tools
### Web Application Framework
#### Spring
#### Play
#### JSF
- JavaServer Faces
#### Apache Wicket
#### Apache Struts
### Web container
- 
  Java EEアーキテクチャのコンポーネント規約を実装するソフトウェア。

#### Oracle WebLogic Server
##### Installation
- UNIX
  java -jar fmw_12.2.1.~_wls_generic.jar
- Window
  java -jar fmw_12.2.1.~_wls_generic.jar
- [[http://docs.oracle.com/middleware/12211/lcm/WLSIG/toc.htm][Fusion Middleware Installing and Configuring Oracle WebLogic Server and Coherence - ORACLE]]
##### Domain Structure
- ドメインディレクトリ（ディレクトリ名=ドメイン名）
###### autodeploy
- 自動デプロイメントディレクトリ（開発モード用）
###### bin
- 起動・停止スクリプトetc
####### stratWebLogic.sh(cmd)
- 管理サーバ起動スクリプト
####### startManageWebLogic.sh(cmd)
- 管理対象サーバ起動スクリプト
###### common
###### config
- コンフィグレーションディレクトリ
####### config.xml
###### console-ext
###### init-info
- ドメインの初期化情報
###### lib
###### nodmanager
- ノートマネージャ・ホームディレクトリ
###### resources
###### security
- セキュリティファイル
###### servers
- サーバローカルディレクトリ
##### Server Status
###### SHUTDOWN
- 構成されているが、非アクティブになっている。
###### STARTING
- 起動コマンドの結果としてSHUTDOWN状態からSTANDBY状態に遷移する。
  クライアント・リクエストも管理リクエストも受け付けることができない。
###### STANDBY
- 通常のリスニング・ポートがクローズされているためリクエストを処理しない。
  管理ポートはオープンされており、RUNNNING状態またはSHUTDOWN状態に遷移させるライフサイクル・コマンドを受け付ける。
  ホット・バックアップとして待機させておくことができる。
###### ADMIN
- 起動して実行状態にあるが、受け付けるのは管理操作のみとなり、ユーザーはサーバーおよびアプリケーション・レベルの管理タスクを実行できる。
  - 管理コンソールが使用できる
  - サーバー・インスタンスはadminロールのユーザーからのリクエストを受け付ける
  - アプリケーションはADMIN状態でアクティブ化される。
  - JDBC, JMS, JTAの各サブシステムの管理操作が実行可能。
  - デプロイメント・再デプロイメントは許可される。
  - ClusterServiceはアクティブで、他のクラスタ・メンバーからのハートビートおよび通知をリスニングする。
###### RESUMING
- STANDBY状態またはADMIN状態からRUNNING状態への移動に必要な処理を実行している。遷移状態。
###### RUNNING
- 完全に機能しており、クライアントにサービスを提供し、クラスタの正規メンバーとして機能できる。
###### SUSPENDING
- ADMIN状態への移動に必要な処理を実行する。
  サブシステムおよびサービスを順に中断し、進行中のアプリケーション作業の事前に定義済みの部分を完了する。
###### FORCE_SUSPENDING
- ADMIN状態への移動に必要な処理を実行する。
  処理中の作業を正常に中断しない。
###### SHUTTING_DOWN
- サブシステムおよびサービスの中断を完了し、アプリケーション・リクエストも管理リクエストも受け付けない。
###### FAILED
- メモリー不足例外やアプリケーション・スレッドのスタック状態の結果として、あるいはいくつかの重要なサービスが機能しなくなった場合に、サーバー・インスタンスで障害が発生することがある。
###### FAILED_NOT_RESTARTABLE
##### Management Console 管理コンソール
- 管理サーバだけにデプロイされる管理用Webアプリケーション
- Access
  http://hostname:port/console
  https://hostname:port/console
  デフォルトポートは7001
##### Glossary
###### WLST
- WebLogic Scripting Tool
##### Link
###### 12.2.1.1.0
- [[http://docs.oracle.com/middleware/12211/wls/index.html][Oracle WebLogic Server 12.2.1.1.0]]

- [[http://docs.oracle.com/middleware/12211/cross/referencedocs.htm][Reference and APIs 12.2.1.1.0]]
- [[http://docs.oracle.com/middleware/12211/wls/WLAPI/toc.htm][Java API Reference for Oracle WebLogic Server]]
- [[http://docs.oracle.com/middleware/12211/wls/WLTAG/toc.htm][JSP Tags Reference for ORacle Weblogic Server]]
- [[https://docs.oracle.com/middleware/1221/wls/ADMRF/index.html][Command Reference for Oracle WebLogic Server]]

###### 12.2.1
- [[http://docs.oracle.com/cd/E72987_01/wls/index.html][Oracle WebLogic Server 12.2.1 - ORACLE Help Center]]
- [[http://docs.oracle.com/cd/E72987_01/wls/INTRO/toc.htm][Oracle® Fusion Middleware Oracle WebLogic Serverの理解 12c(12.2.1)]]
- [[http://docs.oracle.com/cd/E72987_01/wls/START/toc.htm][Oracle® Fusion Middleware Oracle WebLogic Serverサーバーの起動と停止の管理 12c (12.2.1)]]
- [[http://docs.oracle.com/cd/E72987_01/wls/ADMRF/toc.htm][Oracle® Fusion Middleware Oracle WebLogic Serverコマンド・リファレンス 12c (12.2.1)]]

###### Tmp
####### Slide
- [[http://www.slideshare.net/OracleMiddleJP/20140527-wlstudy-startjee1handsout][Java EE & WebLogic Server入門: はじめてのJava EEアプリケーション開発シリーズ： 第1回 - SlideShare]]
- [[http://www.slideshare.net/OracleMiddleJP/20141218-wlstudy-wlsbasichandsout][Oracle WebLogic Server 12.1.3入門 - SlideShare]]
- [[http://www.slideshare.net/OracleMiddleJP/20130821-wlstudy-jeeapphandsout][Java EE アプリケーションをWebLogic Serverで動かしてみよう - SlideShare]]

####### Deploy
- [[http://alctail.sakura.ne.jp/tip/linux_kannrenn/weblogic/][Weblogic10.3を使ってみる - この世果てのしっぽの方]]
- [[https://blogs.oracle.com/wlc/entry/weblogic_c122][【後編】インストールからアプリケーションの配備まで - WebLogic Channel]]
- [[http://www.oracle.com/technetwork/jp/ondemand/application-grid/wls11g-handson-1034-354365-ja.pdf][意外と簡単!? WebLogic Serverのインストールと運用 - ORACLE]]

#### JBoss, Wildfly
- 
  Java EEアプリケーションサーバ。
  オープンソース版についてはWildFlyという名称となっている。
  
  ライセンスはLGPLである。
  JBoss Inc.をRed Hatが買収したため、現在はRed Hatが運営を行っている。

##### 概要
- 
  Javaのオープンソース・フレームワーク群。
  EJBを動かすもの、というのが基本。
  もとはEJBoss(Enterprise JavaBeans Open Source Software)という名前あったが、商標の関係によりJBossとなった。

###### TomcatでなくJbossを選ぶ理由
- [[http://nekop.hatenablog.com/entry/20110421/1303372984][TomcatでなくJBossを選ぶ○○の理由 - nekop's blog]]

##### 機能
###### JavaEE
####### JTAトランザクションマネージャ
####### EJB
####### MDB
####### JPA
####### JMS
####### JCA
####### JAX-WS
###### JBoss固有
####### JMX
####### log4jを用いたログ基盤
####### 分散キャッシュなどの各種クラスタリングサービス
##### Projects
###### Wildfly
###### JBoss Web
###### JBoss ESB
###### JBoss Messaging
###### JBoss Tools
###### Hibernate
#### GlassFish
- 
  サン（オラクル）を中心のコミュニティで開発された、Java EE準拠のアプリケーションサーバの名称。
  以前は商用サポートも行っていたが、v4.0で廃止され、以降は参照実装としての位置づけになっている。

- 
  [[http://www.coppermine.jp/docs/programming/2014/01/the-end-of-glassfish.html][GlassFishの落日 - Programming Studio]]
  [[https://blogs.oracle.com/yosshi/entry/glassfish_%E3%81%A8_tomcat_%E3%81%AE%E9%81%95%E3%81%84_part][GlassFishとTomcatの違い Part3 - 寺田 佳央 (Yoshio Terada)]]
  
##### 機能
###### Servlet
###### JSP
###### EJB
###### JMS(Java Message Service)
###### JNDI(JavaNaming and Directory Interface)
###### JBI(Java Business Integration)
###### ORB(Object Request Brocker)
#### Tomcat
##### 概要
- 
  ServletやJSPを実行するためのWebコンテナ。
  Apache License 2.0を採用。
  現在はApache Software FoundationのApache Tomcat Projectで開発されている。
  以前はJakartaプロジェクト内で開発されていた。
  
  静的コンテンツのHTTPサーバとしても使えるので単体で用いることもできる。
  また、別のHTTPサーバがHTTPリクエストを受け、必要に応じてサーブレットコンテナにリクエストを渡す、という構成でHTTPサーバと連携させて用いることもできる。
  ただし、別HTTPサーバと連携させるとAdvanced IOなど一部機能が使えなくなる。
  Apacheととモジュール連携を行う場合mod_jkを配布している。mod_proxy_ajpモジュールを用いる方法もある。

  EJBはサポートしていないらしい（2010年情報、最新未確認だがおそらく同様）。

##### 機能
###### Servlet
###### JSP
###### JDBC接続プール
##### Folder
###### %CATALINA_HOME%
####### bin
####### conf
######## web.xml
- 
- servlet/init-param
  param-name:listingsのparam-value:trueとすると、フォルダにアクセスした際に配下のファイルが一覧として見えるようになる。
  セキュリティ上、Tomcat 6.0以降この値がTrueとなりデフォルトで表示されなくなった。

####### lib
####### webapps
- 
  ユーザが作成したアプリケーションを格納するためのデフォルトのアプリケーションフォルダ。
  .warファイルを配下に置いておくと、アプリケーションが自動的に展開する。

##### Environmental Variables
- CATALINA_HOME
  Tomcatフォルダを配置した場所を設定する。
 
##### Tools
###### Tomcat Manager
- 
  現在のアプリケーションの状態を確認し、アプリケーションの配置や起動・終了などをブラウザ画面から確認できる。
  インストール時に設定したユーザ名/パスワードが必要。
  http://localhost:8080/manager/html
#### WebSphere Application Server

### IDE
#### Eclipse
- [[file:Eclipse.org][Eclipse.org]]

#### IntelliJ Idea
#### NetBeans
### Framework
#### SpringFramework
#### Seasar2
#### S2Util
- Seasar2からスピンアウトしたプロジェクトで、様々なUtil ClassをLibraryとして提供する。
  Seasar2ではJ2EE1.4を前提としていたものが多かったが、Java5以降のジェネリックや可変長配列に対応する変更なども加えられている。
##### APIs
###### 0.0.1
####### org.seasar.util.beans.util
######## Classes
######### BeanMap
######### BeanUtil
- JavaBeansとJavaBeans、あるいはJavaBeansとMapの間でプロパティをコピーするためのユーティリティ。
########## Methods
########### copyBeanToMap(Object src, Map<String,Object> dest)
- BeanからMapにコピーを行う。
########### copyBeanToMap(Object src, Map<String,Object> dest, CopyOptions options)
######### CopyOptions
- BeanUtilでJavaBeansやMapをコピーする際に指定するオプション。
##### Link
- http://s2util.sandbox.seasar.org/apidocs/index.html
### Apache ActiveMQ
- Java Message Serviceを実装したメッセージ関連のオープンソースのミドルウェア。
  http://activemq.apache.org/getting-started.html

### Editor
### GUI
#### JavaFX
- 
  Java仮想マシンで動作する立地インターネットアプリケーション(RIA)のGUIライブラリ。
  JavaSE7 Update2以降に標準搭載されている。
  Swingと異なり、FXMLと呼ばれるXMLとCSSを併用してデザインを記述する。

##### History
- JavaFX 1
  2008/12/4リリース。JavaFX Scriptというプログラム言語を用いて開発する仕組みだった。
- JavaFX 2
  2011/10/10リリース。
  JavaFX Scriptを廃止し、普通のJava APIに置き換えることで、JRuby, Groovyなどでも利用可能となる。
- JavaFX 8
  - Java8からバージョン番号を揃え、JavaFX 8となった。
  
#### Swing
- 
  JavaのGUIツールキット。AWTを拡張したもの。
  AWTはOSのウィンドウシステムに準じたデザインになるのに対し、SwingはJavaプログラム上で描画されるので、より柔軟な設計が可能となる。
  
- 
  [JFrame]に部品(コンポーネント)を張り付けていく。

#### Abstract Window Toolkit, AWT
- 
  Java独自のプラットフォーム非依存ウィンドウシステム、UI、ウィジェットツールキット。
  現在はJava Foundation Classes(JFC)に含まれ、GUIを提供する標準APIの一部となっている。

### Build
#### Gradle
- [[file:Gradle.org][Gradle.org]]
#### Apache Maven
- [[file:Maven.org][Maven.org]]
#### Apache Ant
- ビルドツール
### Memory
#### GCViewer
- https://github.com/chewiebug/GCViewer
- a little tool that visualizes verbose GC output generated by Java Virtual Machines.
### JavaScript Engine
#### Rhino
- Mozilla製、Java 6からサポートされていた。
#### Nashorn
- JDK 8に搭載された。
  - http://openjdk.java.net/jeps/174
- JEP 335でNashornがDeprecateに。
  - http://openjdk.java.net/jeps/335
- https://www.publickey1.jp/blog/18/javajavascriptnashornecmascriptgraalvm.html
#### GraalJS (on GraalVM)
## Settings
### Environmental Variables
#### CLASSPATH
- 
  クラス検索パスの設定を行う。
  実行時に"-classpath"オプションを指定しない場合、はCLASSPATH環境変数を用いることになる。
## Glossary
### Java applet
- 
  Webページの一部として埋め込まれてWebブラウザ上で実行されるもの。

### Java console
- 
  http://www.java.com/en/download/help/javaconsole.xml
  https://www.java.com/en/download/help/disable_java_icon.xml

### JAR/WAR/EAR
- いずれもJava仕様に準拠して定義されたZIP形式の圧縮ファイル。
#### JAR
- Java ARchive
  クラスファイルや設定ファイル(XML形式のものなど)がまとめられている。
  多くのクラスライブラリがこの形式で配布される。
  MVCモデルでいうところのModelにあたる。

#### WAR
- Web Application Resources, Web Application Archive
  J2EE仕様によってフォルダ構造が決められている。
  MVCにおける"VC"の部分。
  クラスファイル、設定ファイルのほか、JSPやHTMLも含まれる。
  またweb.xmlが含まれ、Tomcatなどのアプリケーションサーバに配布すると、これを元にデプロイされる。

#### EAR
- Enterprise ARchive
  J2EE仕様によってフォルダ構造が決められている。
  複数のWARファイル、(EJB)JARファイルを含む。
  application.xmlが含まれ、J2EEコンテナ（JBoss, WebSphereなど）に配布すると、これを元にデプロイされる。

### POJO
- Plain Old Java Object、普通のJava。
### コンテナ
- 
  JSP&サーブレットコンテナ。
  JSP&サーブレットを実行する環境という意味で、アプリケーションサーバとも呼ばれる。
  WebLogicやJRun、Tomcatなどが該当する。

#### Tomcat
- バージョン関係
  |--------+-----+--------------|
  | Tomcat | JSP | サーブレット |
  |--------+-----+--------------|
  |    7.x | 2.2 |          3.0 |
  |    6.x | 2.1 |          2.5 |
  |    5.x | 2.0 |          2.4 |
  |    4.x | 1.2 |          2.3 |
  |    3.x | 1.1 |          2.2 |
  |--------+-----+--------------|

### 関数型インターフェース
- 大雑把に言って、定義されている抽象メソッドが1つだけあるインターフェース。
  staticメソッドや絵フォルトメソッドは含まれていても構わない。
### OUI, Oracle Universal Installer
### JavaBeans
- コンポーネントを進めるため、いくつかのルールに従って作られているJavaのクラス。
  現実的には、「JSPで使用する、プロパティを持つクラス」が一般的な受け入れられ方。
- 特徴
  - クラス名末尾がBean : 慣例。
  - プロパティ : 
  - 永続化 : java.io.Serializableインターフェースを実装
  - 引数なしのコンストラクタ
- [[http://www.wakhok.ac.jp/~tomoharu/web2004/text/index_c4.html][JavaBeansとJSP - JavaによるWebアプリケーション入門]]
### JNDI
- Java Naming and Directory Interface
  ネーミング・サービス、ディレクトリー・サービスを扱うためのインターフェースを規定した仕様。
- http://www.ne.jp/asahi/hishidama/home/tech/java/j2ee/jndi.html
- [[http://www.ibm.com/developerworks/jp/websphere/library/was/was_jndi/][今さら人に訊けないJNDI - IBM developerWorks]]
### JDBC(temp)
- 
  Java Database Connectivityの略と言われているが、実際には名称であり略称でないとのこと。
  RDBMSへ接続する機能を標準化・抽象化している。
  JavaSDKに同梱されているが、規格はJavaSDKとは独立して行われている。

  java.sqlインターフェースを介して実装されている。

#### JDBC Driver
##### 概要
###### Type1 : JDBC-ODBCブリッジ・ドライバ
- 
  JDBCからのクエリー要求をODBCを経由して受け渡し、データベースとアクセスするもの。
  ODBCドライバが必須であり、ハードウェアとOSに依存する。
  Java7では非推奨となり、Java8では標準から削除された。

###### Type2 : ネイティブ・ブリッジ・ドライバ
- 
  JDBCからのクエリ要求をOS上のDDLや専門ライブラリに受け渡し、そこからデータベースにアクセスするもの。
  Type1に比べて階層が薄く高速化が期待できTCP/IPに依存しない利点があるが、ハードウェアとOSに依存する。
- 
  Oracleの場合、Oracle Call Interface(OCI)ドライバ。
  
###### Type3 : ネット・プロトコル・ドライバ
- 
  JDBCからのクエリー要求をJavaで記述されたドライブ内で独自のプロトコルに変換し

###### Type4 : ネイティブ・プロトコル・ドライバ
- 
  Oracleの場合、Thinドライバ。
###### サーバー側Thinドライバ
###### サーバー側内部ドライバ
##### DB
###### Oracle
- classes111.jar : JDK1.1
- classes12.jar : JDK1.2~JDK1.3
- ojdbc14.jar : JDK1.4~JDK5(JDK1.5)
- ojdbc5.jar : JDK5(JDK1.5)
- ojdbc6.jar : JDK6(JDK1.6)
- ojdbc7.jar : JDK7(JDK1.7)
### Serializable
- 
  Serialize可能、直列可能、ということを保証するInterface。
  直列可能、というのは、StreamやConnectionで操作可能、そのままファイルに出力できる、という程度の意味。
  ObjectInputStream/ObjectOutputStreamクラスで、インスタンスをファイルに出力したり、ファイルから復元したりすることが可能。
  [[http://d.hatena.ne.jp/daisuke-m/20100414/1271228333][難解なSerializableという仕様について俺が知っていること、というか俺の理解 - 都元ダイスケ IT-PRESS]]

- serialVersionUID
  クラスの構造が変わった場合に判断が付くようにするため、振るID。

### JAXB
- Java Architecture for XML Binding
  software framework that allows Java developers to map Java classes to XML representations.
- v1.0 : JSR 33
  v2.0 : JSR 222
## Link
- [[http://docs.oracle.com/javase/specs/][Java Language and Virtual Machine Specification - ORACLE]]
- [[http://docs.oracle.com/javase/8/docs/api/][Java™jj Platform, Standard Edition 8 API Specification]]
- [[http://docs.oracle.com/javase/jp/8/docs/api/][Java(tm) Platform, Standard Edition 8 API仕様]]
- [[http://docs.oracle.com/javase/tutorial/java/index.html][The Java Tutorials]]

- [[http://www.jpcert.or.jp/java-rules/][Java セキュアコーディングスタンダード CERT/Oracle 版 - JPCERT]]
## Memo
### リソース付きtry
- 
  try(AutoCloseable Class; ...){
  }
  括弧の中身のリソースについて、自動でclose()が呼ばれる。

### インスタンス初期化子
- 
  {実装}
  何も修飾せず実装を書くと、コンストラクタが呼び出される前にメソッドとして呼び出される。
  匿名クラスなどで使い道がある。

### 匿名クラス
- 
  new スーパークラス名(コンストラクタ引数) { サブクラス実装 }
  スーパークラスのサブクラスとして、名前のないクラスを作成できる。
  作成時にインスタンス化もして、そのまま使い捨てる。

### apt-getでインストール
- Installing Java 8 on Ubuntu
  $ sudo add-apt-repository ppa:webupd8team/java
  $ sudo apt-get update
  $ sudo apt-get install oracle-java8-installer
  [[http://tecadmin.net/install-oracle-java-8-jdk-8-ubuntu-via-ppa/][How to Install JAVA 8 (JDK 8u51) on Ubuntu & Linux Mint Via PPA]]

- add-apt-repostioryが使えない場合
  $ sudo apt-get install python-software-properties

- 1.7
  $ sudo apt-get install openjdk-7-jdk

- (古かった。1.6)
  JRE : "sudo apt-get install default-jre"
  JDK : "sudo apt-get install default-jdk"
  [[https://www.digitalocean.com/community/tutorials/how-to-install-java-on-ubuntu-with-apt-get][How To Install Java on Ubuntu with Apt-Get]]

### セキュリティ・プロンプトの復元
- 
  セキュリティ・プロンプトの復元により、非表示にしたプロンプトが再表示される。

### 実行
- 実行時は、packageと同階層のフォルダの下に置いた実行ファイルを、.(dot)で区切った形でパス指定して実行。
- ex)
  package abc.def, file abc/def/main.classの場合、
  その上のフォルダで"java abc.def.main"と実行する。
### Throwable、例外
#### Error エラー
#### Exceptoin 例外
- チェック例外・非チェック例外
  - チェック例外(Exception) : 例外が発生した場合にcatch節で補足し処理するか、throws句を記述しないとコンパイルエラーが発生するため、例外発生時の対処をプログラムで矯正される例外。
  - 非チェック例外(RuntimeException) : 通常、例外が発生した際にcatch節やthrow区で対応しない/してはならない例外。
- 発生状況別
  - 論理例外 : アプリケーションで論理的に発生しうる例外。補足して処理する。
  - システム例外 : システムが正常に動作する条件が整っていない場合や、連携する外部アプリケーションのエラーに起因する例外。アプリケーションで処理しない/処理しても意味がない。
  - プログラムエラー : コーデイングの間違い、連携するAPIの使用方法の間違いなど。本来的に発生しない者なので、対処しても意味がないエラー。

#### Link
- [[http://ebc-2in2crc.hatenablog.jp/entry/20120729/1343557350][Java のチェック例外と非チェック例外の考察まとめ - 全力で怠けたい]]

### .class
- クラス名.class、とすることでクラスが取得できる。
  どこかのクラスメソッドかと思いきや、これはJavaのsyntaxに組み込まれていた。
  Java 1.8 Specificationの「15.8.2 Class Literals」にある。
  
  ちなみにインスタンスからクラス名を取得するには、Object#getClass()で可。
### varargs
- 可変長引数を取れるようにするもの。
  (そのうち文法に統合するなどしてください。@SafeVarargs, @SuppressWarningsとかも)
### "exit code = 13"の対処
- "Java was started but returned error code=13"となった場合の対処法。
  Win7でDBeavor実行時に同様の状況に陥った
  ショートカット先のJavaを読んでいたので、x64側を読むように*.iniにvmを設定したところ、問題なく動いた。
- https://blog.clock-up.jp/entry/2015/01/17/eclipse-exit-code-13
- https://stackoverflow.com/questions/27019786/eclipse-java-was-started-but-returned-error-code-13
### temp
#### 修飾子
##### アクセス修飾子
- 
  メンバ変数とメソッド、クラスに指定できる修飾子で、
  その変数やメソッドを参照できる範囲を指定する。

  |-----------+----------------------------------------------------|
  | 修飾子    | 説明                                               |
  |-----------+----------------------------------------------------|
  | private   | 同じクラス内からのみアクセス可能                   |
  | 指定無し  | 同一クラス、パッケージのみアクセス可能             |
  | protected | 同一クラス、パッケージ、サブクラスのみアクセス可能 |
  | public    | どこからでもアクセス可能                           |
  |-----------+----------------------------------------------------|

##### abstract修飾子
- 
  メソッド、クラスに指定できる。
  付加すると抽象クラス、抽象メソッドとなる。

##### final修飾子
- 
  変数、メソッド、クラスに指定できる。
  どれに付けたかによって意味合いが変わる。
  
  |----------+------------------------------------------------------------|
  | 対象     | 説明                                                       |
  |----------+------------------------------------------------------------|
  | 変数     | 定数となる。変数宣言時に代入が必要となり、その後変更不可。 |
  |          | メンバー変数、ローカル変数どちらにも指定可能。             |
  | メソッド | オーバーライド不可                                         |
  | クラス   | クラスに付けた場合は、そのクラスは継承不可。               |
  |----------+------------------------------------------------------------|

##### static修飾子
- 
  メンバー変数・メソッドに指定することができる修飾子。
  staticを指定するとインスタンスを生成しなくても使用できるようになる。

  ex) public static String aa = "ABC";
      public static void method() { }

##### native修飾子
- 
  ネイティブ修飾子
  対象はメソッド。
  メソッドがネイティブメソッドであることを示す。

##### synchronized修飾子
- 
  同期修飾子
  対象はメソッド、ブロック。
  メソッドがマルチスレッド環境で実行される場合、排他制御が行われる。
  ひとつのインスタンスが複数のスレッドを持つ場合は排他制御が行われるが、
  複数のインスタンスで実行される場合ははいた制御されない。

##### transient修飾子
- 
  一時的修飾子
  対象は変数。
  変数を一時的な状態とし、シリアライズの対象から除外する。

##### volatile修飾子
- 
  揮発性修飾子
  対象は変数。
  複数のスレッドから参照される可能性のある変数に付けることで、
  参照・変更した値がメモリに書き戻されないことを防ぐ。

##### strictfp修飾子
- 
  厳密浮動小数修飾子
  対象はクラス、インターフェース、メソッド。
  指定したクラスでは、浮動小数点演算が、プラットフォームに依存しない厳密な動作をするようになる。

##### const修飾子
- 
  定数修飾子
  キーワードとして定義されているが、実際に使われるケースはない。
#### アノテーション annotation
- 
  JavaSE 5から追加された。

##### 分類
- マーカーアノテーション
- 単一値アノテーション
  1つのデータを持つアノテーション
- フルアノテーション
  少なくとも2つ以上のデータを持つアノテーション
- メタアノテーション
  
##### 種類
###### 標準
####### @Override
- 
  スーパークラスのメソッドをオーバーライドする、という注釈をつけたいときに使用する。

####### @Deprecated
- 
  クラスやメソッドが非推奨であるという注釈を付けたいときに使用する。

####### @SuppressWaring
- 
  コンパイル時の警告を抑制する。

####### @Target
- 
  アノテーションが利用可能なプログラム要素を定義する

####### @Retention
- 
  アノテーションの保持ルールを決める

###### javadoc
####### @author
####### @param
####### @return
####### @exception
####### @version
####### @see
####### @deprecated
###### jUnit
####### @Test
####### @Before
####### @AFter
####### @BeforeClass
####### @AfterClass
##### 定義
- @interface命令
