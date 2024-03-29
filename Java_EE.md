# Java EE
- 
  Java Platform, Enterprise Edition。
  Java SEに加え、多層クライアントサーバの大規模システムを開発するための、さまざまなAPIが追加されている。
  企業用機能セット。
  Java EE自体は仕様であるため、各社がライセンスを受け実装し、販売などをしている。

## API
### Java EE 7
#### javax.ejb
#### javax.faces
#### javax.inject
##### Annotations
###### Inject
- Identifies injectable ocnstructors, methods, and fields.
###### Named
###### Qualifier
###### Scope
###### Singleton
##### Interface
###### Provider<T>
#### javax.servlet
### Java EE 6
## Architecture
### 関係
- 
  Servletの上にJSPが存在し、その上にJSP STLが存在する関係。

## Functions
### Java Servlet
#### About
- 
  MVCでいうところのControllerに該当。

  クライアントを受け付ける。
  1つのServletから生成されたスレッドはメモリ空間を共有する。

  処理を簡単にいうと、
  1. クライアントからリクエストを受け
  2. リクエストに応じた処理を行い
  3. クライアントへレスポンスを返す

- 
  最初の呼び出しのみインスタンス化され、それ以降はスレッドが生成されるのみ。
  スレッド同氏はメモリ空間を共有する。

- 
  HttpServletやGenericServletが存在する

#### Life cycle
- 最初にインスタンス生成が要求された場合のみ、インスタンス化する。
  その際initが呼び出され初期化処理が行われる
  2回目以降はinitは呼び出されない。
- GetまたはPostが要求されると、doGet, doPostメソッドが呼び出さえっる。
  HttpServletRequestのgetParameterを使い、ブラウザで入力された値を取得し、要求に応じる。
- 消滅は明示的に行わず、管理コンソールの停止指示や、サーバ地震の停止の前に呼び出される。
  
#### Link
- [[https://jcp.org/en/jsr/detail?id=340][JSR 340: Java Servlet 3.1 Specification - Java Community Process]]
### JSP
#### About
- JavaServer Pages
  MVCでいうところのViewに相当。
  HTML内にJavaのコードを埋め込んでおき、Webサーバで動的にWebページを生成してクライアントに返す技術。
  サーブレットの機能の一つとして実装されており、Servletに書き換えられて実行される。
  同種の技術にPHP、ASP.NETなど。
- 
  「Ajaxの羽根飾りのついたHTMLの仮面をかぶったServlet」
  Servletの上に乗った仕様であり実装。Servletに翻訳された後コンパイルされる。
  動的なコンテンツの作成が可能。

- 
  登場当時はHTMLにJavaコードを書ける、ということで飛びついた場合も多かったが、
  現在はJavaコードを極力書かないのが流儀となっている。

- 
  JSPの中でメソッドを宣言しない場合、processRequestメソッドの内部をコーディングしていることと同じ。
  <%! int a = 0 %>のように変数を宣言するとフィールド変数となり、メモリの奪い合いが起きる。

- 
  自らでコンパイル作業が必要ない。コンテナが自動的に処理を行う。
  サーブレットは自前でコンパイルしたclassファイルを実行する。

#### scope
##### application
- 型：ServletContext
  コンテキストルート配下で構成されるアプリケーションを指す。
  Tomcatでいうwebapps配下に配置するwarファイル。
  「Java EE 5 Tutorial」のWebモジュール構造に従うと、Assembly Rootが該当。

##### session
- 型：HttpSession
  セッションの間、クライアント同士を隔離する範囲がsessionスコープ。
  Servletのフィールド変数と異なり、sessionに変数を定義すると、このような状況を回避できる。
  ただし、すべてのオブジェクトをセッションに入れると、非常に重いアプリケーションとなるので、
  他のスコープに格納することも検討する。
  
##### request
- 
  クライアントからWebコンポーネントに要求が送られる間のみ保持されるスコープ。
  1回のリクエスト内で保持されるのがrequestスコープ。

##### page
- 
  JSP pageのこと。processRequestメソッドに相当するメソッドを記述するのと同義。
  JSPはServletのメソッドを記述していることになるため、そこで定義したものがローカル変数となる。
  JSP内部のみからアクセスできる範囲。

#### 構造
##### Tag
- HTMLの中に特殊タグを記述可能。
- 
  |------------------+----------------------+-----------------------------------|
  | 名称             | タグ                 | 説明                              |
  |------------------+----------------------+-----------------------------------|
  | ディレクティブ   | <%@ ディレクティブ > | 処理時の属性をWebコンテナに伝える |
  | 宣言             | <%! 宣言 %>          | JSPで使用する変数やメソッドを宣言する |
  | スクリプトレット | <% Javaコード %>     | タグ内にJavaのコードを自由に記述する |
  | 式              | <%= 式 %>           | 式の評価結果をHTML内に出力する    |
  | アクション       | <jsp:アクション名>   | JSPでよく行う処理をタグで簡潔に記述する |
  | コメント         | <%-- コメント --%>   | JSPとしてのコメントを記述する                  |
  |------------------+----------------------+-----------------------------------|

###### Directive ディレクティブ
####### page
- 
  JSP pageのこと。
  JSPそのものに関する処理の仕方をコンテナに伝えるもの。
  <%@ page page_directive_attr_list %>
  
- 例
  <%@ page buffer="32kb" autoFlush="true" %>

######## page_directive_attr_list
######### language
######### extends
######### import
- 
  java.lang.*, javax.servlet.*, javax.servlet.jsp.*, javax.servlet.http.*以外のクラスを使用する場合に指定する。

######### session
- 
  "true"の場合javax.servlet.http.HttpSessionが使える。

######### buffer
- 
  "none"の場合、JSPで処理される度にクライアントに結果が送られる。
  "none"以外はkbで指定する。デフォルトは8kb。
######### autoFlush
######### isThreadSafe
######### isErrorPage
######### errorPage
######### contentType
######### pageEncoding
######### isELIgnored
######### deferredSyntaxAllowedAsLiteral
######### trimDirectiveWhitespaces
####### taglib
- 
  カスタムタグを使用できるようにするための設定を行う
  
  <% taglib (uri="tagLibraryURI" | targdir="tagDir") prefix="tagPrefix" %>

######## attr
######### uri
- 
  taglib-uriの要素内容を指定する。
  TLD(tag library descriptor)の名前を検索するために使われる。

######### tagdir
- 
  JSP2.0から導入された属性で、タグファイルのディレクトリを指定する。

######### prefix
- 
  <myPrefix:myTag>のように記述する。

- myPrefixに以下は使用できない。
  - jsp:
  - jspx:
  - java:
  - javax:
  - servlet:
  - sun:
  - sunw:

####### include
- 
  テキストファイルやその他のJSPファイルをインクルードする。
  インクルードは、JSPからServletに変換する際に行われる。
  
- 
  翻訳時にfile属性で指定したリソースに置き換えてくれとJSPコンテナに指示を出すもの。
  pageディレクティブのimport属性は累積的な指定ができるが、その他は矛盾を起こす可能性があり、注意する必要がある。
  矛盾がある場合は翻訳時にエラーとなる。
  
- 
  属性はfileのみ。
  <%@ include file="relativeURLspec" %>

###### Expression Language, EL式, 式言語
- 
  JSFにおいても独自に定義されていたが、JSP 2.1, JSF 1.2で一つの仕様(Unified EL, 統合式言語)に統合され、
  EL 3.0ではJSPから独立したJava EE 7の仕様の一つとなっている。
  
  式言語では演算の結果だけでなくオブジェクトのプロパティの値も返すことができる。
  
- 構文
  ${expr}
  
###### スクリプティング要素
- 
  式言語がJSP 2.0で取り入られたため、機能的に重なる部分が多くなり、どちらを採用するかはプロジェクト判断、という位置づけとなっている。
####### 宣言
- 
  フィールドで定義されるため、同期化に注意する必要がある。

- 変数宣言
  <%! int i = 0; %>
- メソッド宣言
  <%! public boolean isAdult(int age) {boolean adult = false; if (age >= 20) return true; } %>

####### スクリプトレット
- 
  <% if (age >= 20) {%> 成人 <% } else {%> 未成年 <% } %>

####### 式
- 
  演算結果やオブジェクトの戻り値などの値を返す。
  式言語は翻訳時にString型に変換するが、式では型変換してくれない。

  <%= employee.getName() >

###### アクション
- 
  サーバ側のJavaロジックを呼び出すもの。

####### 種類
######## jsp:include
######## jsp:param
######## jsp:forward
######## jsp:plugin
######## jsp:fallback
######## jsp:getProperty
######## jsp:setProperty
######## jsp:useBean
- 例
  <jsp:useBean id="employee" class="jp.kawakubo.Employee" scope="session" />

- 
  Javabeanとしてインスタンスできない場合、classでなくtypeで指定する。
  抽象クラス、インターフェース、publicでもなくかつ引数が存在するコンストラクタを持つクラスの場合、typeで指定する。
  クラスが.serファイルに存在する場合、beanNameで指定する。

  scope属性をしえ亭可能。

  bodyでjsp:setPropertyアクションを指定すると、クラスからインスタンス化する際、setPropertyで指定したプロパティに値が設定される。

###### JSTL
- JavaServer Pages Standard Tag Library, JSP標準タグライブラリ
  Webアプリケーションで多用されるであろうアクションをあらかじめ提供することで、
  同じアクションを重複して開発することを回避し、可読性や生産性を高めるためのもの。

####### Core (prefix : c)
- 
  主にJSP自体の記述を簡単にするための機能が集められている。
  変数の設定・削除、例外の補足、制御ロジックなど。

####### XML (prefix : x)
######## XMLコアアクション
- <x:parse>
  XMLを解析する
- <x:out>
  XPath式の評価結果を出力する
- <x:set>
  XPath式への評価結果を変数へ設定する

######## XMLフロー制御アクション
- 
  条件式にXPath式を使用するフロー制御アクション。
- <x:if>
- <x:choose>
- <x:when>
- <x:x:otherwise>
- <x:forEach>

######## XML変換アクション
- <x:transform>
  XSLTシートを使用してXML文書を変換する。

####### i18n / Internationalization (prefix : fmt)
- 
  字コードのエンコーディング。

####### SQL (prefix : sql)
- 
  JSP pageからデータベース操作できる機能が集められている。

####### Function (prefix : fn)
- 
  主に文字列操作を行う機能が集められている。

### Java Beans (EJB)
- 
  MVCとしての利用では、Modelに相当すると位置づけられる。
  再利用可能なソフトウェアコンポーネント、またはその技術。

  ビジネス層に関しては基本的にEJBを使う。
  CDIと通常のJavaクラス(POJO:Plain Old Java Object)によって作ることも可能だが、
  EJBにはトランザクションを制御する機能が備わっているので、これを使った方が信頼性の高いアプリケーションを簡単に作れる。

#### Component
##### Session Bean
- 
  クライアント・サーバ間やシステム間のやり取りを通じて実行するビジネスロジックを実装するためのEJBコンポーネント。
  以下の種類がある。
  - Stateless Session Bean
  - Stateful Session Bean
  - Singleton Session Bean

##### Message Driven Bean
- 
  メッセージ・サーバからの要求に応じてビジネスロジックを実行するEJBコンポーネント。
  メッセージングを介したシステム連携を行う場合に作成する。

##### Entity Bean
- 
  データベースへのデータ永続化に使用するEJBコンポーネント。
  道央の機能を実現する技術としてJPAが導入されたため、現在は非推奨扱い。

### JSF
- JavaServer Faces
  高機能なユーザインターフェースを効率的に作るためのWebアプリケーションフレームワーク。

#### 要素
##### FacesServlet (Controller)
- 
  クライアントとのやり取りの窓口の役割を果たす。
  リクエストを受け取ると適切なコンポーネントに処理を受け渡し、処理結果をクライアントに送り返す。

##### Facelets (XMTML)
- 
  画面の構成要素を記述する。XHTML内にJSFのタグを記述すると、そおｎタグに対応したコンポーネントが必要な処理を行う。
  画面レイアウトと、ユーザーが画面の構成要素（ボタンやリスト、フォームなど）

##### Maneged Bean
- 
  画面遷移やビジネスロジックの呼び出し、入出力値の管理などを行うコンポーネント。

### JPA
- Java Persistence API
  データベースへのアクセスなど永続化相の処理の開発にはJPAを使う。
  RDBMSのテーブルに格納されているレコードをJavaオブジェクトとして扱えるようにしてくれるO/Rマッピングフレームワーク。
  なお、JDBCではSELECT文やUPDATE文をJavaプログラム内に書くのでRDBの知識が必要となるが、
  JPAを使う場合そういったコードを書く必要はない。
  
  JavaEEだけでなく、JavaSEでも使用可能。

### CDI
- Container Dependency Injection
  DI(Dependency Injection、依存性の注入)機能を備えたDIフレームワーク。
  各層のコンポーネントを柔軟に結びつける役割を果たす。
  プレゼンテーション層のJSFからビジネス層のEJBコンポーネントを呼び出すといった、層をまたいだコンポーネント間アクセスの方法を標準化している。
  
  またCDIはオブジェクトのライフサイクル（寿命）を管理する機能を備えており、
  たとえばあるセッションだけで有効なオブジェクトや、あるリクエストだけで有効なオブジェクトなど、
  オブジェクトの有効期間を指定して生成することができる。
  
### JAX-RS
- RESTアーキテクチャに基づくWebサービスのための機能を提供するJava言語のAPI。
  リソースクラス（POJOのJavaクラス）をWebリソースにマッピングするのを助けるアノテーションを提供する。
  JAX-RS自体はAPIであり、実装は別。
#### 実装
##### Apache CXF
- Webサービスフレームワーク
##### Jersey
- オラクル(Sun)によるリファレンス実装
##### RESTeasy
##### WebSphere Application Server
#### Link
- [[https://backpaper0.github.io/ghosts/jaxrs-getting-started-and-practice.html#60][JAX-RS入門および実践]]
### JAX-WS
- Java API for XML Web Services
  主にSOAPを扱うためのAPI
#### Link
- [[http://itpro.nikkeibp.co.jp/article/COLUMN/20080801/311972/?rt=nocnt][「Java SE 6完全攻略」第81回 JAX-WS その1 - ITPro]]
## Glossary
### Deployment Descriptor, DD
- デプロイメント記述子
  アプリケーションまたはモジュールに対する構成オプションおよびコンテナー・オプションを指定するXMLファイル。
#### web.xml
- Webモジュール(WARファイル)の設定情報
#### ejb-jar.xml
- EJBモジュール(EJB-JARファイル)の設定情報
#### application.xml
- Webアプリケーション(EARファイル)の設定情報
#### application-client.xml
- クライアント・アプリケーション(クライアントJARファイル)の設定情報
#### webservices.xml
#### ra.xml
- リソース・アダプタ・モジュール(RARファイル)の設定ファイル
## Memo
### Packaging
#### JAR
##### Structure
##### Link
- [[https://docs.oracle.com/javase/jp/8/docs/technotes/guides/jar/jar.html][JARファイルの仕様 - Java Documentation]]
#### WAR
##### Structure
- /WEB-INF/web.xmlが必須。その他は必要に応じ設置。
###### /
####### .
- webクライアントからアクセスされるファイルを格納する。
  WEB-INF以外のサブディレクトリに格納することもできる。
####### META-INF
- 管理情報を格納するディレクトリ。jarコマンドで自動的に作成される。
######## .
######### MANIFEST.MF
- jarコマンドのmオプションで指定されたファイルが格納される
####### WEB-INF
- パブリックドキュメントツリーの一部でなく、クライアントへ直接提供されるファイルはない。
######## .
######### web.xml
- 必須。servlet仕様で規定されたDD。

######### *.tld
- Java Server Pages仕様で規定されたタグライブラリ・ディスクリプタのファイル。
######## classes
- サーブレットやその他のクラスファイルを格納するディレクトリ。
  クラスパスに自動で追加される。
######## lib
- サーブレットやその他のクラスを扱うJARファイルを格納するディレクトリ。
  クラスパスに自動で追加される。
#### EJB-JAR
##### Structure
###### /
####### .
- 
####### META-INF
######## .
######### ejb-jar.xml
- EJB仕様で規定されたDD。
  EJB2.0仕様のEnterprise Beanでは必須。アノテーションに対応したEnterprise Beanでは不要。
######### MANIFEST.MF
#### EAR
##### Structure
###### /
####### META-INF
######## .
######### application.xml
- J2EEで規定されたDD。必須。
######### MANIFEST.MF
## Link
- [[https://jcp.org/en/jsr/platform?listBy=3&listByType=platform][JSRs: Java Specification Requests - Java Community Process]]
- [[https://docs.oracle.com/javaee/7/tutorial/index.html][The Java EE Tutorial - Java Platform, Enterprise Edition 7]]

- APIs
  - [[https://docs.oracle.com/javaee/7/api/][Java(TM) EE 7 Specification APIs]]
  - [[https://docs.oracle.com/javaee/6/api/][JavaTM Platform, Enterprise Edition 6 API Specification]]

- [[https://netbeans.org/kb/trails/java-ee_ja.html][Java EEおよびJava Webの学習 - NetBeans]]
- [[http://qiita.com/tkxlab/items/3c0d4073defacb1215f5][JavaEEをはじめよう！ - Qiita]]

