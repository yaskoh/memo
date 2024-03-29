# Apache HTTP Server
## Features
### 複数バージョンのサポート
### MPM : Multi Processing Module
- 複数OSに最適化
#### プロセスの挙動
##### prefork
- 
  スレッドを使わず、先行してforkを行うウェブサーバ。
  伝統的に親プロセスを1つ持ち、クライアントからリクエストが来るとforkする。実際の通信は子プロセスが受け持つ。
  そのため、接続数だけ子プロセスが起動する。
  forkに時間がかかるため、あらかじめ複数個のプロセスを事前に立ち上げておくため、preforkと呼ばれる。

- メリット
  ある子プロセスがフリーズしても、他のプロセスには影響せず、安定した通信が可能。

- デメリット
  クライアントが多くなるほどメモリやCPU負荷が増えていく。

##### worker
- 
  マルチスレッドとマルチプロセスのハイブリッド型。
  子プロセス1つ1つがマルチスレッドで動作し、スレッド1つが1つのクライアントを受け持つ。

##### event
- 
  workerの一種で、マルチスレッドで動作する。
  違いはKeep-Aliveの処理方法で、Keep-Aliveの処理を別のスレッドに割り振って通信を処理する。
  2.4.1で正式に採用された。

##### winnt
- Windows向け。スレッド対応型。
### モジュールによる機能追加
- 
  モジュールを追加することで拡張可能。(Apache->A patch)
  「Core」がまずあり、モジュールを追加して機能を拡張する。「mod_XXX」と名付けられる。
  
  追加は「静的リンク」と「動的リンク」がある。
  - 静的リンク
    静的リンクはApacheの実行ファイルそのものにモジュールを組み込む。バイナリ的に一体化する。
    早いが再コンパイルが必要。
  - DSO : Dynamic Shared Object、動的共有オブジェクト
    動的リンクはモジュールを別ファイルとして作成し、必要に応じてモジュールのファイルから機能を呼び出す方式。
    あらかじめ「mod_so」モジュールを静的リンクしておく必要がある。
    負荷が高くなるが導入が容易。

## Build
- http://httpd.apache.org/docs/2.4/install.html
### Download
### Expansion
### Setting
- 
  Defaultのパスは/usr/local/apache2

- [[http://httpd.apache.org/docs/2.4/programs/configure.html][configure - Configure the source tree - Apache HTTP Server]]
### Compile
### Install
### Customize
### Test
## Modules
### core
- [[http://httpd.apache.org/docs/2.4/mod/core.html][Apache コア機能]]
#### Directives
##### AllowEncodedSlashes
- 説明
  URLの中に符号化されたパス分離文字が先に伝えられるのを許可するかどうかを決定する。
  符号化されたパス分離文字とは、/->%2F、\->%5Cなど。
- 構文
  AllowEncodedSlashes On|Off
- Default
  AllowEncodedSlashes Off
##### <Directory>
- 説明
  指定のファイルシステムのディレクトリとサブディレクトリとのみに適用されるディレクティブを囲む
##### DocumentRoot
- 説明
  ウェブから見えるメインのドキュメントツリーになるディレクティブ
- 構文
  DocumentRoot directory-path
##### ErrorDocument
- Desc : What the server will return to he client in case of an error
- Syntax : ErrorDocument error-code document
- e.g.
  ErrorDocument 403 "Sorry, can't allow you access today"
##### ErrorLog
- Description : サーバがエラーをログ収集する場所
- Syntax : ErrorLog file-path|syslog[:facility]
- Default : ErrorLog logs/error_log (Unix) / ErrorLog logs/error.log (Windows)
##### ErrorLogFormat
- Description : Format specification for error log entries
##### <Files>
- Desc: Contains directives that apply to matched filenames
- Syntax: <Files filename> ... </Files>
- 
  Wild-card strings, Regular expressions can be used.
##### <IfModule>
- Description : モジュールの存在有無に応じて処理されるディレクティブを囲む。
##### Include
- Include file-path|directory-path
  - 設定ファイルをインクルードできる。
  - fnmatchのワイルドカード文字の利用が可能。
  - ファイルは絶対パスかServerRootディレクトリからの相対パス。
- ex)
  Include /usr/local/apache2/conf/ssl.conf
  Include conf/ssl.conf
##### <Location>
- Description : 囲んだディレクティブがマッチするURLのみに適用。
- Syntax : <Location URL-path|URL> ... </Location>

###### When to use
- lives outside the filesystem.
  in the filesystem, use <Directory> and <Files>.
###### Regular expressions
- with the addition of the ~ caharcter.
  e.g.
  <Location ~ "/(extra|special)/data">
      # data
  </Location>
##### Options
- Description : ディレクトリに対して使用可能な機能を設定する。
###### Opitons
####### All
####### ExecCGI
####### FollowSymLinks
- このディレクトリ内でシンボリックリンクを辿れるようにする
####### Includes
####### IncludesNOEXEC
####### Indexes
- URLがディレクトリにマップするリクエストで、かつDirectoryIndexで指定したファイルがディレクトリになければ、
  mod_autoindexがディレクトリ内の一覧を整形して返す。
####### MultiViews
####### SymLinksIfOwnerMatch
##### ServerAdmin
- Description : サーバがクライアントに送るエラーメッセージに含める電子メールのアドレス
##### ServerTokens
- Description : Configures the Server HTTP response header
##### Timeout
- Description : 各イベントについて、リクエストを失敗させるまでにサーバが待つ時間
- Syntax : TimeOut seconds
##### TraceEnable
- Description : Traceメソッドのリクエストに対する応答方法を決める
##### <VirtualHost>
### MPM
- Multi Prosessing Module
#### About
- 
  |---------+------------------------|
  | Netware | mpm_netware            |
  | OS/2    | mpmt_os2               |
  | Unix    | prefork, worker, event |
  | Windows | mpm_winnt              |
  |---------+------------------------|

#### Modules
##### mpm_common
- Apache MPM共通ディレクティブ
###### Directives
####### Group
- リクエストに応答する際に所属するグループ
####### MaxClients
- Description : 
####### MaxMemFree
- Description : free()が呼ばれない限り、主メモリアロケータが保持し続けられるメモリの最大量。
- Default : MaxMemFree 0
- 
  設定されていないか、ゼロに設定されている時は無制限。
####### ServerLimit
- Description : 
####### ThreadLimit
- Description : 設定可能な子プロセス毎のスレッド数上限を設定する
- Default : 1920(mpm_winnt) / 64 (その他)
- 
  ThreadsPerChildよりもずっと大きな値に設定された場合、余計な未使用共有メモリが割り当てられてしまう。
  
####### ThreadPerChild
- Description : 子プロセスそれぞれに生成されるスレッド数
- Defalut : 64(mpm_winnt) / 25 (その他)
####### User
- Description : 
##### event
##### prefork
##### worker
- マルチスレッドとマルチプロセスのハイブリッド型
##### mpm_winnt
##### mpm_netware
##### mpm_os2
### Other defaluts
#### mod_access_compat
- mod_authz_hostにとってかわられるべきっぽい。
##### Directives
###### Allow
- Description: Controls which hosts can access an area of the server.
###### Deny
###### Order
- Default: Order Deny,Allow
###### Satisfy
##### Memo
###### アクセスの制御
- ホスト制御(Order, Allow, Deny)
- ユーザ認証制御(Auth*, Require)
- Satifsfy
  - デフォルトでAll。すべての条件を満たす必要がある
  - anyとすると、どれかを満たせばよい。
- [[http://koseki.hatenablog.com/entry/20100913/ApacheAccessControl][Apacheのアクセス制御をちゃんと理解する。 - こせきの技術日記]]
###### 
#### mod_actions
#### mod_alias
#### mod_asis
#### mod_auth
#### mod_auth_anon
#### mod_auth_dbm
#### mod_auth_digest
#### mod_auth_ldap
#### mod_authz_core
- Core authorization
##### Topics
##### Directives
###### AuthMerging
###### Require
- Require all granted
- Require all denied
- Require env [env-var]
- Require method [http-method]
- Require expr [expression]
- Require user [user]
- Require group [group-name]
- Require valid-user
- Reuire ip [ip-addr]
###### <RequireAll>
###### <RequireAny>
###### <RequireNone>
##### Memo
- [[https://qiita.com/ngyuki/items/779ea21eec2ae6c450d5][Apache 2.4 の Require ディレクティブのマージとか - Qiita]]
#### mod_authz_host
- Group authorizations based on host
##### Directives
###### Require
####### Require ip
####### Require host
####### Require forward-dns
####### Require local
#### mod_autoindex
- Discription : UnixのlsやWinのdirシェルコマンドと似たディレクトリインデックスを生成する。
#### mod_cache
#### mod_cern_meta
#### mod_cgi
#### mod_cgid
#### mod_charset_lite
#### mod_dav
#### mod_dav_fs
#### mod_deflate
#### mod_dir
- Description : 最後のスラッシュのリダイレクト、ディレクトリのインデックスファイルを扱う機能を提供。
##### Directives
###### DirectoryCheckHandler
###### DirectoryIndex
###### DirectoryIndexRedirect
###### DirectorySlash
###### FallbackResource
#### mod_disk_cache
#### mod_dumpio
#### mod_echo
#### mod_env
- CGIスクリプト及びSSIに渡される環境変数を変更する機能を提供する。

##### Directives
###### SetEnv
- Description:
  環境変数を設定し、それをCGIスクリプトとSSIページに渡す
- Syntax:
  SetEnv env-variable value
#### mod_example
#### mod_expires
#### mod_ext_filter
#### mod_file_cache
#### mod_headers
- HTTPリクエストヘッダとレスポンスヘッダをカスタマイズする
##### Directives
###### Header
- 説明 : HTTPレスポンスヘッダの設定
####### Syntax
- Header [condition] action header [value] [early|env=[!]variable]
####### Actions
######## add
######## append
######## echo
######## edit
######## edit*
######## set
######## unset
- 指定された名前の応答ヘッダが存在している場合、削除する。
####### conditions
###### RequestHeader
- Configure HTTP request headers
####### Syntax
- RequestHeader set|append|add|unset header [value] [early|env=[!]variable]
######## set
- リクエストヘッダを設定する。同じ名前のヘッダが存在していると、それを置き換える。
######## append
######## add
######## unset
#### mod_imap
#### mod_include
#### mod_info
#### mod_isapi
#### mod_ldap
#### mod_log_config
- サーバへのリクエストのロギング機能
##### Format
##### Directives
###### BufferedLogs
###### CustomLog
- ログファイルの名前と書式を設定する
###### GlobalLog
###### LogFormat
- Description : ログファイルで使用する書式を設定する
- アクセスログファイルの書式を指定する。
###### TransferLog
#### mod_log_forensic
#### mod_logio
#### mod_mem_cache
#### mod_mime
#### mod_mime_magic
#### mod_negotiation
#### mod_nw_ssl
#### mod_proxy
- HTTP/1.1 proxy/gateway server
##### Directives
#### mod_proxy_connect
#### mod_proxy_ftp
#### mod_proxy_http
- HTTP support module for mod_proxy
##### Environment Variables
###### proxy-nokeepalive
- Forces the proxy to close the backend connection after each request.
##### Directives
###### ProxyPass
- Description
  Maps remote servers into the local server URL-space
- Syntax:
  ProxyPass [path] !|url
- Example:
  ProxyPass /mirror/foo http://backend.example.com
###### ProxyPassReverse
- Description:
  Adjusts the URL in HTTP response headers sent from a reverse proxied server
- Syntax:
  ProxyPassReverse [path] url
###### ProxyPreserveHost
- Description:
  Use incoming Host HTTP request header for proxy request
- Syntax:
  ProxyPreserveHost On|Off
- Default:
  ProxyPreserveHost Off
###### ProxyTimeout
- Description:
  Network timeout for proxied requests
- Syntax:
  ProxyTimeout seconds
#### mod_remoteip
- Replaces the original client IP adderss for the connection with the useragent IP adderss list
  presented by a proxies or load balancer via the request headers.
##### Directives
###### RemoteIPHeader
###### RemoteIPInternalProxy
###### RemoteIPInternalProxyList
###### RemoteIPProxyHeader
###### RemoteIPTrustedProxy
###### RemoteIPTrustedProxyList
#### mod_rewrite
- Provides a rule-based rewriting engine to rewrite requested URLs on the fly.
- 
  Apache Webサーバにおいて、クライアントからリクエストのあったURLの内部書き換えや、
  さまざまな環境変数等に応じたリダイレクトを可能とするモジュール。
  正規表現を使用したマッチングを行うことができる。

- 使用方法
  - httpd.confに設定する
    こちらの方が望ましい

  - .htaccessに設定する
    処理が遅くなるので、httpd.conf推奨。

##### Directives
###### RewriteBase
###### RewriteCond
- Description:
  Defines a condition under which rewriting will take place
- Syntax:
  RewriteCond TestString CondPattern
###### RewriteEngine
- Description:
  Enables or disables runtime rewriting engine
- Syntax:
  RewriteEngine on|off
- Default:
  RewriteEngine off
###### RewriteRule
#### mod_setenvif
#### mod_so
#### mod_speling
#### mod_ssl
##### Environmental Variables
##### Directives
###### SSLCertificateFile
###### SSLCertificateKeyFile
#### mod_status
#### mod_suexec
#### mod_unique_id
#### mod_userdir
#### mod_usertrack
#### mod_version
#### mod_vhost_alias
### Etc
#### mod_jk
- 
  Tomcat redirector module.
- 
  https://tomcat.apache.org/connectors-doc/webserver_howto/apache.html
### link
- http://httpd.apache.org/docs/2.4/mod/
## Settings
### httpd.conf
#### TypesConfig
- mimeタイプと拡張子の組み合わせを設定するファイルパスの指定
  デファルトで設定されたファイル名はmime.types
#### AddType
- MIMEタイプを追加する。
  例 : AddType MIMEタイプ 拡張子
#### CustomLog
- ログファイルの位置を設定する。
  例 : CustomLog ログファイルの場所 ログファイルのフォーマット
  
### .htaccess
- this files provide a way to make configuration changes on a per-directory basis.
### mime.types
- MIMEタイプと拡張子の組み合わせを設定する。
  httpd.confファイル中の"TypesConfig"でパスを設定している。
  httpd.confファイル内で、AddTypeを行いMIMEタイプを追加することも可能。
## Command
- bin/
### httpd
#### -k
##### install
##### uninstall
##### start
##### stop
##### restart
## Structure
### htdocs
- 
  default Apache web server document directory
### conf
- 
  the directory where all server configuration files are located.

### logs
- 
  the directory where servere logs are kept, and includes Apache access logs and error logs.
  
### cgi-bin
- 
  the directory where CGI scripts are kept.
## Manual
### Referense Manual
### User's Guide
#### Getting Started
##### Clients, Servers, and URLs
- URL
  - protocol
  - servername
  - URL-path
  - query string : e.g. ?arg=value
- 
  - client : request
  - server : response
##### Hostnames and DNS
- DNS
- hosts file
- virtual hosts
##### Configuration File and Directives
- 
### How-To / Tutorials
### Platform Specific Notes
### Other Topics
### Link
- https://httpd.apache.org/docs/2.4/en/

## Memo
### 暗号化
- 証明書の作成
  - opensslによる例
    - 秘密鍵 : openssl genrsa -aes256 -out server.key 2048
    - CSR : openssl req -new -key server.key -sha256 -out server.csr
    - 証明書 : openssl x509 -in server.csr -days 365 -req -signkey server.key -sha256 -out server.crt
- mod_ssl.soの設定
  LoadModuleのコメントアウトを外す
- httpd-ssl.confの設定
  conf/extra/httpd-ssl.confのIncludeのコメントアウトを外す
  extra/httpd-ssl.confに、証明書、秘密鍵、各種パスの設定を行う
- mod_socache_shmcb.so
  LoadModuleのコメントアウトを外す
#### Link
- http://www.maruko2.com/mw/Apache/SSL%E8%87%AA%E5%B7%B1%E8%A8%BC%E6%98%8E%E6%9B%B8%E3%81%AE%E4%BD%9C%E6%88%90%E3%81%A8mod_ssl%E3%81%AE%E8%A8%AD%E5%AE%9A
- http://d.hatena.ne.jp/ozuma/20130511/1368284304
- http://www.lesstep.jp/step_on_board/apache/335/
### アクセス制御
#### ディレクティブ
- ファイルシステム向けのコンテナ
  <Directory>ディレクティブ
  <Files>ディレクティブ
- Web空間向けコンテナ
  <Location>ディレクティブ
- [[https://httpd.apache.org/docs/2.4/ja/sections.html][セクションの設定 - Apache]]
#### アクセス制御
- mod_authz_host (,mod_access_compat)も参照
- [[https://qiita.com/YasuyukiKawai/items/727d2238572851000c79][Apache:アクセス制御をする - Qiita]]
### Rewriteについて
- RewriteRuleの前にRewriteCondを記述。
- 複数Ruleが必要なら、そのたびにRewriteCondを直前に記述する。

#### Link
- https://weblabo.oscasierra.net/apache-rewritecond-base/
- http://blog.livedoor.jp/tak_bon/archives/6508443.html
### Secure属性を付与
- mod_headersモジュールでCookieに変更を入れる。
  Header edit Set-Cookie ^(.*)$ $1;secure
  https://qiita.com/yuba/items/034dd027dbde15f6a795
### Apacheでリバースプロキシした際のプロトコル変換
- X_FORWARDED_PROTOを利用する
  RequestHeader set X_FORWARDED_PROTO 'https'
- SSLをLBやApacheまでで終わらせ、内部通信はhttp通信の場合に、
  アプリケーション側がプロトコルをhttpだと勘違いする場合に、上記設定を行う。
  Railsだと解釈をしてくれるのでうまく動作する。

- Link
  - https://qiita.com/yusabana/items/1e61f46094b965a66599
  - http://www.rarul.com/mt/log/2015/05/reverseproxyred.html
  - https://qiita.com/HeRo/items/7063b86b5e8a2efde0f4
## Link
- [[https://httpd.apache.org/][Apache HTTP SERVER PROJECT]]

- [[https://www.nic.ad.jp/ja/materials/iw/2005/proceedings/T16.pdf][自信を持ってApacheを操るために]]
