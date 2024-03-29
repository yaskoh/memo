# Tools
- Temporary use. Locate what not being categorised other files. 
  Transfer to somewhere else if each tools collecting enough volumes.

## Programming Language
### elm
- 
  関数型のフロントエンドのための言語。
  html, css, javascriptに変換される。
  
- 
  [[http://doloopwhile.hatenablog.com/entry/2014/12/01/200000][Elmとはどんな言語か？その７つの特徴【Elmアドベントカレンダー2014 1日目】 - None is None is None]]

## Parser Generator
### yakk/bison
- 
  [[file:./Compiler.org][Compiler.org]]

## Parser
### SintyaxNet
- 
  neural models of syntax.

- 
  http://googleresearch.blogspot.tw/2016/05/announcing-syntaxnet-worlds-most.html?m=1
  https://github.com/tensorflow/models/tree/master/syntaxnet

## Lexical Analyzer
### lex/flex
- 
  [[file:./Compiler.org][Compiler.org]]

## Shell
### GNU Readline
- キーバインドを設定する。
  デフォルト設定ファイルは~/.inputrc。
## File
### Samba
- Unix系OSでWindowsのファイル共有機能を提供するもの。
- [[https://www.samba.org/][SAMBA]]
- [[https://wiki.samba.org/index.php/Main_Page][Main Page - SAMBA wiki]]
## Database
### HeidiSQL
- http://celtislab.net/archives/20130826/heidisql%E3%81%A7mysql%E3%83%87%E3%83%BC%E3%82%BF%E3%83%99%E3%83%BC%E3%82%B9%E3%81%B8%E6%8E%A5%E7%B6%9A%E3%81%97%E3%81%A6%E3%81%BF%E3%82%8B/

### MySQL Workbench
- https://www-jp.mysql.com/products/workbench/

## WebServer
### Architecture
#### シリアルモデル
#### マルチプロセスモデル
#### マルチスレッドモデル
#### イベント駆動モデル
#### ハイブリッドモデル
#### 計量プロセスモデル
#### Link
- [[http://yuuki.hatenablog.com/entry/2015-webserver-architecture][2015年Webサーバアーキテクチャ序論 - ゆううきブログ]]

### Apache HTTP Server
- [[file:ApacheHttpServer.org][ApacheHttpServer.org]]
### nginx
- [[file:Nginx.org][Nginx.org]]
### IIS
- Windows
### Built-in Web Server
- for PHP
- ex) >$ php -S localhost:8000
### webrick
- ruby products
### for Dev
#### Web Server for Chrome
- Chore Apps
#### 04WebServer
- Windows application
### DIY
- [[http://kmaebashi.com/programmer/webserver/index.html][本当の基礎からのWebアプリケーション入門 -Webサーバを作ってみよう-]]
## Reverse Proxy Server
### Squid
### Varnish Cache
### Apache Traffic Server, ATS
## Load Balancer
### Kind
#### NAT
- 
  パケットがすべてロードバランサを経由する

#### DSR, Direct Server Return
- 
  復路がロードバランサを経由しない

### Linux Virtual Server, LVS
- 
  Linuxをロードバランサとして利用するためのソフトウェア。
  Linuxカーネルに組み込んで使うカーネルモジュールと、設定や管理を行うipvsadmコマンドから構成されている。

### HAProxy
- 
  http://www.haproxy.org/

### Elastic Load Balancing, ELB
- 
  https://aws.amazon.com/jp/elasticloadbalancing/

## Monitoring
### Zabbix
### Nagios
### Hinemos
- NTTData
  複数のコンピュータを単一のコンピュータのイメージで運用管理することを実現するオープンソースソフトウェア。
### JP1
- Hitachi
### WebSAM
- NEC
### OpenView
- hp
### Keepalived
- 
  routing software written in C.
  The main goal of this project is to provide smple and robust facilities for loadbalancing and high-availability to Linux system and Linux based infrastructures.

- 
  サービスの稼働状態を監視するソフトウェア。
  LVSと合わせて利用し、サーバが停止・LBが停止していたら、他へ振り分けることを行う。

- 
  http://www.keepalived.org/

### Pacemaker
- HAクラスタソフト。
  以前は「Heartbeat」といった。
  複数のコンピュータをNW等で連携し、故障を検知したら他のコンピュータにフェイルオーバさせるなどし、高可用性を実現する。

#### 機能
##### アプリケーション監視・制御機能
##### ネットワーク監視・制御機能
##### ノード監視機能
##### 自己監視機能
##### ディスク監視・制御機能

#### Link
- [[http://linux-ha.osdn.jp/wp/manual/pacemaker_outline][Pacemakerの概要 - LINUX-HA JAPAN]]
### Heartbeat
- 
  The High Availability Linux Projectが開発したもので、アクティブ・スタンバイクラスタを提供する基本的な機能を提供する。

- 機能
  - フェールオーバーとフェールバック
  - 稼働監視
  - 共有リソース管理
  - サービス監視

- 
  http://linux-ha.org/wiki/Heartbeat

## BigData
### BigQuery
- 
  ビッグデータの分析に使われるcloudサービス。

## Browser
### Firefox
#### XUL
- XML User Interface Language, ずーる
  Mozilaアプリケーションを作成するためのユーザインターフェースマークアップ言語。

### Chrome

## Web Tools
### Google Analytics
#### Link
- [[https://www.google.com/intl/ja_jp/analytics/][Google Analytics]]
- [[https://developers.google.com/analytics/][Googleアナリティクス]]
- [[https://liginc.co.jp/web/seo/107795][Googleアナリティクスの用語の意味と基本的な使い方をおさえよう - LIG INC.]]
## Network
### Apache Thrift
- Facebookに開発されたRPCフレームワーク。
  C++, C#, Java, Perl, Python, PHP, Erlang, Rubyなどの言語観でシームレスに動作するサービス開発を可能とする。
#### Link
- [[https://thrift.apache.org/][Apache Thrift]]
### Apache ZooKeeper
- 設定情報の集中管理や名前付けなどのサービスを提供するソフトウェア。
  分散システムの
#### Link
- [[https://zookeeper.apache.org/][Apache ZooKeeper]]
## CI
### Jenkins
### TravisCI
### CircleCI
### Wercker

## Project Management
### Redmine
- [[file:Redmine.org][Redmine.org]]

### Trac
### Cloud Products
#### Wrike
- https://www.wrike.com/ja/
#### Asana
- https://asana.com/ja/?noredirect
#### Jooto
- https://www.jooto.com/
#### Trello
- https://trello.com/en
#### JIRA
- https://www.atlassian.com/software/jira

## Testing
### JUnit
- [[file:UnitTest.org][UnitTest.org]]
## Memory
### valgrid
- programming tool for memory debuging, memory leak detection, and profiling.
  http://valgrind.org/
  https://en.wikipedia.org/wiki/Valgrind
### memcached
- 
  a general-purpose distributed memory caching system.
  汎用の分散型メモリキャッシュシステム。

### Oracle Coherence
- 
  インメモリ・データグリッド製品
  実体はJavaクラスライブラリ(100% Pure Java)
  ライブラリはJava/C++/.NET
## Log
### Fluentd
### Elasticsearch
### Kibana
- 
  Elastic社のログ解析/可視化ツール。
  基本的にElasticsearchとセットで使われる。

## Chat
### idobata
### Slack
## Package Management
### OSX
#### brew
#### MacPorts
- [[https://www.macports.org/][The MacPorts Project Official Homepage]]
#### Fink

## C
## Java
- [[file:./Java.org][Java.org-Tools]]

## Ruby
### Library
#### Rack
- 
  WSGIに影響されて開発された、Rubyにおけるサーバとアプリケーション／フレームワーク間のインターフェースの役割を果たすライブラリ。

- 
  [[http://gihyo.jp/dev/serial/01/ruby/0023][第23回 Rackとは何か（1）Rackの生まれた背景 - Ruby Freaks Lounge - gihyo.jp]]

### Web Server
#### Unicorn
- Rack Web Srever.
  RackとWebサーバーの機能を併せ持つ。

- 
  Unicorn+Railsで公開も可能だが、レスポンスがApacheやNginxに劣るため、Nginx+Unicorn+Railsでの公開が一般的。
  ちなみにNginxはRailsの機能をサポートしていないため、Nginx+Railsでは動作しない。

#### WEBrick
- 汎用HTTPサーバフレームワーク
  単純なHTTP Webサーバの機能を提供するRubyのライブラリ。
  
#### Mongrel

#### Thin
#### Passenger
## Python
### Library
#### WSGI
- Web Server Gateway Interface
  PythonのためのWebサーバとWebアプリケーション・フレームワーク間の標準インターフェースを定める仕様。

- 
  フレームワークの実装が特定のWebサーバに依存していることが多く、フレームワークかサーバが制限される場合が多くあった。
  そのため、お互いに複数の環境に対応するため
  
- 他言語への影響
  - PSGI(Perl)
  - Rack(Ruby)
  - SCGI
  - Ring(Clojure)
  - WAI(Haskell)

### Web Application Framework

#### Django

#### Flask
#### Pyramid
#### Tornado
- 
  Facebook製。

#### CherryPy

#### Bottle
#### Zope

#### Twisted

#### TurboGears
### Web embeddedable
#### Text Editor
##### Ace
- embeddeddable code editor written in JavaScript.
- https://ace.c9.io/
## Perl
### Web Server
#### Starlet
#### Starman
#### Monoceros
## PHP
### Library
#### PSGI
- PHP版WSGI
## XML
### Apache Xerces
- アパッチ ザーシーズ
  XML文書のパースと操作を行うための一群のソフトウェアパッケージ。
## Posix互換
### Cygwin
- 
  互換性レイヤーなしでバイナリを作ることをサポートしていない、とのこと。
  Red Hatの従業員が一部開発に従事しているらしい。

### Msys2
- 
  mingwビルドチームのAlexey Pavlovによって始められたプロジェクトで、最新のCygwinをきちんと追跡している。
  パッケージ管理ソフトのPacmanを移植している。

- 
  [[http://msys2.github.io/][MSYS2 installer]]
  [[http://verifiedby.me/adiary/055][MSYS2を試してみる - kashiの日記]]
  [[http://yaritakunai.hatenablog.com/entry/2015/11/07/201000][Windows上で動く最新のUnix環境、MSYS2について改めてまとめた - できないことはやりたくない]]
  [[http://amekujira.seesaa.net/article/420665358.html][MSYS、MSYS2、Cygwin、msysgitの違い - 雨鯨のたそがれ]]

### MSYS
- Minimal System
  メンテナンスが追い付いていない模様

### MinGW
- Minimalist GNU for Windows
  GNUツールチェーンのWindows移植版。

## Graphics editor
### Drawing / Vector
#### Inkscape
#### Adobe Illustrator
#### LibreOffice Draw
### Paint / Raster
#### GIMP
##### Menu
###### File(F)
###### Edit(E)
###### Select(S)
###### Image(I)
###### Layer(L)
###### Color(C)
###### Tool(T)
###### Filter(R)
###### Window(W)
####### ツールボックス/新しいツールボックス(Ctrl+B)
####### ドッキング可能なダイアログ(D)
######## Layer レイヤー(L)
- レイヤーウィンドウを表示する
###### Help(H)
##### Link
- [[http://www.geocities.jp/gimpfile/gum_jp/guide.html][GIMPユーザーズマニュアル日本語版]]
#### Adobe Photoshop
#### CLIP STUDIO PAINT
## Chart 図説
### draw.io
- https://www.draw.io/
### Cacoo
### Gliffy
### mermaid.js
- Library
## Documentation
### Pandoc
- Pandoc is a library and/or Command Line Tool written by Haskell, which convert format of a document to another.
#### Guide
##### Synopsis
- pandoc [options] [input-file]...
##### Options
###### General options
####### -f FORMAT, --from=FORMAT, -r FORMAT, --read=FORMAT
####### -t FORMAT, --to=FORMAT, -w FORMAT, --write=FORMAT
####### -o FILE, --output=FILE
####### -v, --version
- バージョンを出力する。
####### -h, --help
###### Reader options
###### General writer options
#### Link
- [[https://pandoc.org/][Pandoc a universal document converter]]
- [[https://github.com/jgm/pandoc/releases/tag/1.19.2.1][jgm/pandoc - github]]
- [[http://sky-y.github.io/site-pandoc-jp/users-guide/][Pandoc ユーザーズガイド 日本語版]]
### Sphinx
#### Link
- [[http://sphinx-users.jp/][Sphinx-Users.jp]]
## Undefined
## Glossary
- 
  現状は、行き場のないTempなもの。
  Toolsとは直接関係ない。

### グリッド・コンピューティング
- 
  インターネットなどの広域のネットワーク上にある計算資源を結びつけ、
  ひとつの複合したコンピュータシステムとしてサービスを提供する仕組み。

## Memo
