# Web
## Tools
### Web Icon
#### Font Awesome
- scalable vector icons

- classに「fa」と、各アイコンに割り振られている「fa-xxxx」を利用することで表示される。
  
- [[http://fontawesome.io/][Font Awesome]]
- [[https://h2ham.net/font-awasome][楽して便利！Webアイコンフォント『Font Awesome』の使い方と活用 Tips - HAM MEDIA MEMO]]
## Documents
### Web Application Development Introduction
#### Chapter1 : Goal
##### Type
- .NET
- LAMP
- Ruby on Rails
- Java EE

#### Chapter2 : Environment Settings
- Download and install OS on the virtual environment
  Use VMWare and Debian(installed)

- Download Apache and PHP
  Apt-get apache, php and php-pear,
  access localhost to test whether http server is going,
  and set permisson of /var/www.

- Download JDK
  Get openjdk-6-jdk.
  Latest IDE required latar version of jdk, and I installed jdk 7.
  openjdk-7 and update-alternatives --config to set java7.

- Download IDE
  Install NetBeans or Eclipse on their websites.
  PHP in not containd normal Eclipse version,
  and you need to download another version or add PHP Developer Tools(PDT).
 
  I download netbeans installer on the website and do the script.
  Eclipse is on Synaptic Package Manager, and select and install relating modules.

- Use IDE
  - Netbeans
    - Create New Project
    - Java Web -> Java Application
    - Name and Location Settings, and set later all default.
    - Run(Test)
  - Eclipse
    - 

- Create PHP Application
  - NetBeans
    - Create New Project
    - PHP -> PHP Application
    - select index.php and right click, Run.
  - Eclipse

#### Chapter3 : How to Write Web pages
- Web Browser
  Reccomended Firefox as some reasons.

- HTML Foundamental
  - Heading(h1-h6)    
  - Paragraph(p)
  - Anchor(a)
  - List(ul, ol, dl)
    - Definition List(dl)
      - dl : Include Term and Despciption. Definition List.
      - dt : Definition Term
      - dd : definition Description
      ex)
      <dl>  
      <dt>dl element</dt>
      <dd>Definition List it has terms and descriptions</dd>
      <dt>dt element</dt>
      <dd>Definition Term</dd>
      <dt>dd elements</dt>
      <dd>Description</dd>
      </dl>

  - Table(table, tr, th, tb)
    - table
      table element
    - tr
      table row
    - th
      table header
    - td
      table data
    - ex
      <table>
        <caption>caption area</caption>
        <tr>
          <th>tag</th><th>role</th>
        </tr>
        <tr>
          <td>table</td><td>table</td>
        </tr>
      </table>

- Additional HTML Elements
  - image(img)
  - line break(br)
  - preformatted text(pre)
  - quotation(blockquote, q)
  - emphasis(em, strong)

- HTML Validator

- Style Sheet
  - font size
    - "font" will be abandon in the future.
      so "<font size='5'> is not good.
      use <span style='font-size: 14pt;'>

#### Chapter4 : Program performing on the browser
- How to write JavaScript
  - alert()
    show diagram.
    enclose script on the tag <script type="text/javascript>.

- jQuery
  - Library for using javascript as same appearence over browsers.
  
### Memo
#### Web Server
##### Apache
- Download
  (on debian)
  sudo apt-get install apache2

- Setting
  Set the permisson of /var/www as 775.

###### Modules
####### mod_rewrite
- 

###### Link
- [[https://httpd.apache.org/][Apache HTTP SERVER PROJECT]]

#### Lang
##### PHP
- Download
  (on debian)
  sudo apt-get install php5 php-pear

- What's pear?
  Pear is "PHP Extension and Application Repository",
  a framework and distribution system for reusable PHP components.

##### Java 
- Download
  sudo apt-get install openjdk-6-jdk
  (sudo apt-get install default-jre)
  (sudo apt-get install default-jdk)
  sudo apt-get intall openjdk-7-jre
  sudo apt-get intall openjdk-7-jdk
  
- Managing
  sudo update-alternatives --config java
  sudo update-alternatives --config javac
  [[https://www.digitalocean.com/community/tutorials/how-to-install-java-on-ubuntu-with-apt-get][How To Install Java on Ubuntu with Apt-Get]]

#### IDE
##### NetBeans
##### Eclipse

## Link
- [[https://developer.mozilla.org/en-US/Learn][Learning web development - MDN]]
- [[https://developer.mozilla.org/en-US/docs/Web][Web technology for developers - MDN]]

- [[https://github.com/hatena/Hatena-Textbook][Hatena-Textbook - GitHub]]
- [[https://css-tricks.com/app-from-scratch-1-design/][Creating a Web App from Scratch - Part 1 of 8: Basic Idea and Design - CSS-TRICKS]]
- [[https://netbeans.org/kb/docs/web/quickstart-webapps.html][Introduction to Developing Web Applications - NetBeans]]
- [[http://gihyo.jp/dev/serial/01/start_webap][目指せ！Webアプリケーションエンジニア]]


### 参考
- [[http://bookma.org/][bookma! v3]]
- [[http://www.ikesai.com/][ikesai.com]]
- [[http://lp-web.com/][ランディングページ集めました。]]
## Glossary
### Carousel カルーセル
- Webデザインの一種で、画像などのコンテンツをスムーズに横にスライドさせる表示方法。

### WebService
- HTTPなどのインターネット関連技術を応用し、SOAPと呼ばれるXML形式のプロトコルを用いメッセージの送受信を行う技術。
  WSDL、SOAP、REST、Axis2など
#### WSDL
- Web srevices Description Language
  http://www.wakhok.ac.jp/~sakamoto/WS/web_service_c3.html
## Memo
### HTML Editor
#### TinyMCE
- 
  HTMLコンテンツを容易に作成することができるWYSIWYGエディター。
  ブラウザで利用可能。
  オープンソースとの親和性が高い。
  開発元はMokiecode System AB。
  [[https://www.tinymce.com/][tinymce]]

### CMS
- Contents Management System
#### TeamSite
#### MODX

### MIME Type
- RFC 2045
### Query String
- クエリ文字列
  WebブラウザなどがWebサーバに送信するデータをURLの末尾に特定の形式で表記したもの。
  URL末尾に「?」マークを付け、続けて「名前=値」の形式で記述する。
  値が複数ある時は「&」で区切る。
  例)http://example.com/foo/var.php?name1=value1&name2=value2
### Session, Cookie
#### Cookie
- https://tools.ietf.org/html/rfc6265
##### 
###### Session Cookie
- Webサイトから離脱すると削除される
###### Persistent Cookie
- ブラウザのフォルダに保存されたままとなるCookie。
##### Cookieヘッダの属性
###### 名前=値
###### expires=有効期限（日時）
###### Max-Age=有効期限（秒数）
###### domain=ドメイン名
###### path=パス
###### secure
- HTTPSなどSecureな通信が行われている時のみ、Cookieを送信する。
###### httponly
- JavaScript経由でCookieを取得できないようにする
#### Session ID
- サーバ側で保持し、セッション管理に利用するID。cookieによる管理の場合、値はCookieと同じ。
### Percent-Encoding
- 
  URIにおいて使用できない文字を使う際に行われるエンコードの名称。一般にURLエンコードとも。
  RFC3986のSection2.1で定義されている。
  日本語の文字などで、どの符号化を用いるかは環境により異なる。
  
### apple-touch-icon
- スマホ用のWebクリップアイコン
### Performanceの原則
- ネットワーク処理最適化に関する基本原則は以下３つ
  - データの転送サイズをなるべく小さくすること
  - データの転送回数をなるべく少なくすること
  - データの転送距離をなるべく短くすること

