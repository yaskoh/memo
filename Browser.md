# Browser
## Browsers
### GoogleChrome
#### Developer Tool
##### About
- 右クリック、要素の検証
- 開く:
  Ctrl+Shift+I, F12
##### Kind
###### 要素検証モード
###### Device Mode (Ctrl+Shift+M)
- デフォルトでOn。
###### Elements
- DOMとCSSを自由に操作してサイトのレイアウトやデザインを反復処理可能
####### Sidebar
######## Style
######### Filter
- 要素のフィルター可能
######### :hov
- 擬似クラス(:active、:hoverなど)の状態を固定
######## Computed
- ボックスモデルに基づき、選択要素の状態をわかりやすく表示する
######## Event Listeners
- 選択した要素に関連するイベントリスナを確認できる
######## DOM Breakpoints
- DOM更新に対するブレークポイントを管理できる
  DOMツリー対象を右クリックしてBreak on...メニューから設定する。
######## Properties
######## Accessibility
###### Console
- 開発中に診断情報を記録したり、イその情報をシェルとして使用してページ上のJavascriptを操作したりできる。

- 改行
  改行の入力はShift+Enter

- 通常、Console内の実行コンテキストはwindowだが、ブレークポイントで一時停止している最中は、
  スクリプトが停止している領域の実行コンテキストとなる。

####### Clear console (Ctrl + L, ⌘ + K)
####### Filter
- 通常のテキストまたは正規表現によるフィルタリングが行える。
####### Levels
- Verbose
- Info
- Warning
- Erros
####### Check boxes
######## Group similar
######## Hide network
- Webページ内リソースの404エラーや、XMLHttpRequestのログを非表示にできる
######## Log XMLHttpRequests
- XMLHttpRequestsが実行された時、リクエストの送信先がログとして表示される。
######## Preserve log
- ほかのページに遷移した際もログを残しておく
######## Show timestamps
######## Selected context only
######## Autocomplete from history
###### Sources
- ブレークポイントを使用してJavaScriptをデバッグしたり、ワークスペース経由でローカルファイルを接続、DevToolsラライブディタを使用したりできる。
- http://postd.cc/javascript-debugging-tips-and-tricks/

###### Network
- リクエストされたリソースやダウンロードされたリソースを詳しく調べたり、ページ読み込みパフォーマンスを最適化したりできる
####### Record network / Stop recording network
####### Clear
####### Capture Screenshot
- DOMContentLoadからLoadイベントまでのアイド、数ミリ秒間隔でキャプチャ取得が行われる。
####### Filter
######## Filter Text Box
######## Hide data URLs
######## Type Filter (All, XHR, JS, ...)
####### View
######## Use large/small request raws
######## Show/Hide overview
####### Data
######## Name
######## Method
######## Status
######## Protocol
######## Type
######## Initiator
######## Size
######## Time
######## Watarfall
######## Context Menu (Right Click)
######### Clear browser cache
######### Clear browser cookie
######### Copy
########## Copy as cURL
########## Copy All as cURL
########## Copy All as HAR
######### Replay XHR
- XHRを再実行できる
######### Save as HAR with content
####### Data Sub Panel
######## Headers
- ヘッダ、クエリパラメータの横のview sourceとview URL encodedを押すとパースされていないものに切り替わる。
######### General
######### Response Headers
######### Request Headers
######### Query String Parameters
######## Preview
- 変換されたリソースのプレビュー
######## Response
- 返却されたリソースの生データ
######## Cookies
- リクエストおよびレスポンスに付与されたCookieが一覧化される
######## Timing
- ネットワークのどのような処理にどれだけの時間を要したかが可視化される。
######### Connection Start
- 接続をセットアップするフェーズ
  - Queueing: キューイング
  - Stalled: 接続待ちなどのリクエスト開始までの時間
  - Proxy Negotiation: 接続確立に要した時間
  - DNS Lookup: DNSルックアップに要した時間
  - Initial Connection: SSLやTCPのネゴシエーションを含めた接続確立までの時間
  - SSL: SSLのハンドシェイクに要した時間

######### Requset/Response
- 実際にデータのやり取りを行うフェーズ
  - Request sent: リクエスト送信に要した時間
  - Waiting(TTFB): 送信後最初のレスポンスを受信するまでの時間。Time To First Byteとも。
  - Content Download: サーバからのレスポンスデータを受信するのにかかる時間
  
####### Fotter
######## Requests
######## Transferred
######## Finish
######## DOMContentLoaded
- DOMツリーの構築完了時間
  ウォーターフォールビューなどの青い線
######## Load
- DOMツリーに起因するサブリソースの取得および描画の完了
  ウォーターフォールビューなどの赤い線
###### Performance
- 旧Timeline?
###### Memory
- 旧Profiles
###### Application
- 旧Resources
####### Header
######## Record
######## Stop profiling
######## Clear
######## Load/Save Profile
######## Checkbox
######### Screenshots
######### Memory
######## Collect Grabage
######## Capture settings
######### Disable JavaScript samples
######### Enable advanced paint instrumentation (slow)
######### Network
######### CPU
####### Main1 / Activity
######## FPS : フレームレート
######## CPU : CPUの実行時応対
######## NET : ネットワーク処理
####### Main2 / Event Record List
######## Network
######## Frame
######## Interactions
######## Main
######## Raster
######## GPU
######## ScriptStreamerThread
####### Main3 / Summary, Aggregated Details
######## Summary
######## Bottom-Up
- view which activities directly took up the most time in aggregate
- 元Aggregated Details(下記も同様)
######### Filter
######### Grouping
########## No Grouping
########## Group by Activity
########## Group by Category
########## Group by Domain
########## Group by Frame
########## Group by Product
########## Group by Subdomain
########## Group by URL
######### Heaviest stack
######## Call Tree
- view which root activities cause the most work.
- Bottom-Upと基本的に同じ
######## Event Log
- view activities in the order in which they occured during the recording.
######### Filter
########## Text
########## Selectbox
########### All
########### >=1ms
########### >=15ms
########## Checkbox
########### Loading
########### Scripting
########### Rendering
########### Painting
####### Event Type
- Loading(水色) : HTTPリクエストやHTMLのパースなど
- Scripting(黄色) : JavaScriptで行われた処理全般
- Rendering(紫色) : スタイル評価やレイアウト算出など
- Painting(緑色) : ペイント処理やラスタライズなど

###### Security
- 混合コンテンツの問題、証明書の問題などをデバッグ
###### Audits

###### Console Drawer
####### Console
######## Command Line API
- $_, $0: 最後に選択した要素
- $1, $2, $3, $4: 1つ~4つ前に選択した要素
- $(selectorString): document.querySelectorのエイリアス
- $$(selectorString): document.querySelectorAllのエイリアス
- inspect(element): 引数に渡した要素をElementsパネルで選択した状態にする
####### Animations
####### Changes
####### Coverage
####### JavaScript Profiler
####### Layers
####### Network conditions
####### Performance monitor
####### Quick source
####### Remote devices
####### Rendering
####### Request blocking
####### Search
####### Sensors
####### What's New
###### More Tools
####### Animations
####### Changes
####### Coverage
####### JavaScript Profiler
####### Layers
####### Network conditions
####### Performance monitor
####### Quick source
####### Remote devices
####### Rendering
####### Request blocking
####### Search
####### Sensors
##### Link
- https://developers.google.com/web/tools/chrome-devtools/?hl=ja
#### Extensions
##### Vimium
##### The Great Suspender
##### Tab Glue
##### OneTab
##### Smooth Gestures
##### Advanced REST client
##### Google Art Project
##### Google Dictionary
##### Keepa - Amazon Price Tracker
##### Proxy SwitchSharp
##### Obsolete
###### AutoPatchWork
- 規約違反？削除された模様。
#### Options
- http://chrome.half-moon.org/43.html
- https://abhp.net/it/IT_Google_Chrome_950000.html
#### APIs
- [[https://developers.google.com/web/tools/chrome-devtools/console/console-reference?utm_source=dcc&utm_medium=redirect&utm_campaign=2016q3#consolegroupobject-object][Console API Reference - Tools for Web Developers]]
- [[https://developers.google.com/web/tools/chrome-devtools/console/command-line-reference?utm_source=dcc&utm_medium=redirect&utm_campaign=2016q3][Command Line API Reference - Tools for Web Developers]]

#### Memo
##### ブラウザを最新版に更新する
- 基本的には自動アップデートが走るので問題ない。
  手動で確認したい場合は、設定→Chromeについて、で確認、updateがあれば手動更新可能。
##### ブックマークの場所
- バージョンやOSなどによって変わるはず。。
- Win7: C:\Users\UserName\AppData\Local\Google\Chrome\User Data\Default
### InternetExplorer
#### IE8
- 
  2009/3/20公開。
  Windows7、Windows Server 2008 R2に標準提供。
  XP, Vista, 2003, 2008にも追加提供。

#### IE9
- 
  2011/3/15公開。
  Vista, 7, 2008, 2008R2に追加提供。
- 
  ユーザインターフェイスの整理が行われた。
- ウェブ標準
  - HTML
    勧告候補の仕様を中心にHTML5を実装する。
    DOMの対応も強化された。
  - CSS
    勧告候補となったCSS3のかくもじゅーうrに対応。
  - Scripting
    高速なJavaScriptエンジン「Chakra」が含まれ、
    ECMAScript 5th editionまで対応。
  - Typography
    以前までのEmbedded OpenTypeに加えWebOpenFontFormatに新たに対応。
- グラフィックス
- プライバシー・マルウェア
  
- その他
  - トランジション機能の廃止
    ページを移動するときのビジュアル効果が廃止された。

#### IE10
- 
  2012/8/15公開。
  Windows 8, Windows RT, Windows Server 2012に標準提供。
  7, 2008R2に追加提供。
- 新機能
  - input要素内の×ボタンにより文字列の消去が可能
  - password型のinput要素内で、目のアイコンをクリックすると入力文字列が表示される。
  - スクロールバーのデザイン、HTMLユーザインターフェイスの外観変更
  - タブの改良
  - ネットワークにつながれていないときのエラー画面変更
- 廃止機能
  - 条件付コメント
  - Vector Markup Language
    ベクター画像を描画するためのXML言語で、AdobeやSunのPGMLと統合・改良され、SVGとなっている。
  - DXフィルター
    DirectXベースのフィルタとトランジション。主要な機能はCSS3に取り込まれた。
  - HTMLコンポーネント(HTC)
  - XML Data Islands

#### IE11
- 
  2013/10/17公開。
  Windows 8.1, Windows Server 2012 R2に標準提供。
  7, 2008R2に追加提供。
- 変更点
  - SPDY/3
    SPDY/3に対応。win7とWS2008R2では対応しない。
  - Web標準
    - W3C Fulscreen
    - CSS3 Flexboxの更新
    - CSS border-image
    - W3C Web Cryptography API
    ...
  - WebGL
    WebGLを実装
  - ユーザエージェントの変更
    "like Geckoがユーザエージェント末尾に付けられた。
    トークン"MSIE"の後にIEのバージョンがきていたが、リビジョンを表すトークン"rv"で置き換えられた。
  - 他ブラウザとの共通化
    navigator.appNameとnavigator.productが、他のブラウザ同様"Netscape"と"Gecko"を返すようになった。
  
- 削除された機能
  - クイックタグ
  - [ファイル]メニューの"オフライン作業"
  - コンテンツを他のアプリケーションにドラッグアンドドロップ
  - EdgeでのVBScriptサポート
  - インターネットゾーンにおけるCSS expressionsのサポート
### Edge
- EdgeHTMLエンジンを使用。
### Firefox
#### Memo
##### 設定の変更
- "about:config"にアクセスすることで様々な設定の変更が可能。
##### 最後のタブを閉じてもWindowを閉じないようにする
- about:configで以下を設定
  - browser.tabs.close.WindowWithLastTab -> false
### Safari

### Opera

### Sleipnir
### Conkeror
- 
  Conkeror is a keyboard-oriented, highly-customizable, highly-extensible web browser based on Mozilla,XULRunner,
  written mainly in JavaScript, and inspired by exceptional software such as Emacs and vi.

### Konqueror
- 
  KDEデスクトップ環境の中核として開発されたファイルビューアとしての機能を提供するウェブブラウザおよびファイルマネージャ。
  
### PhantomJS
- 
  
## Web browser engine
- HTML rendering engine, layout engine
  a program that renders marked up content(such as HTML, XML, image files, etc) and formatting information (such as CSS, XSL, etc).
  ウェブページ記述用言語で書かれたデータを解釈し、実際に画面に表示する文字や画像などの配置を計算するプログラム。
### Blink
- Googleなどが開発するHTMLレンダリングエンジン。
  2013/4/3にWebKitから分岐した。
#### Browsers
- Google Chrome
- Opera
- Android
### Trident
- IEに搭載されているHTMLレンダリングエンジンの名称で、ライブラリファイルの名称からMSHTMLとも呼ばれている。
  IE4.0から導入されている。
  Win版はupdateを重ねているが、Mac版では5.0移行Tasmanに置き換えられた。
#### Browsers
- Internet Explorer

### Tasman
- MSのMacintosh Business Unitが開発したエンジン。
  
### EdgeHTML
- Microsoftが開発したプロプライエタリなレンダリングエンジン。
  Tridentからフォークし、レガシーな機能を削除しWeb標準を重視し、最新ブラウザとの互換性が確保されている。
#### Browsers
- Microsoft Edge
### Gecko
- Netscapeシリーズ6以降およびMozillaソフトウェアのために開発されたオープンソースのHTMLレンダリングエンジン群の総称。
#### Browsers
- Firefox
- Camino
- SeaMonkey

### Servo
- Mozilla研究によって開発されている実験的なウェブブラウザ用レイアウトエンジン。
  
### KHTML
- used in KDE's Konqueror web browser and wath tha basis for WebKit
  KDEプロジェクトにより開発されているHTMLレンダリングエンジン。
  Konquerorのために開発された。
  
#### Browsers
- Konqueror
### WebKit
- Appleが中心となって開発されているオープンソースのHTMLレンダリングエンジン群の総称。
  HTML、CSS、JavaScript、SVG、MathMLなどを解釈する。
  元々Safariのレンダリングエンジンとして、KHTMLをフォークして開発された。
#### Browsers
- Safari
- OmniWeb

### Presto
#### Browsers

## JavaScript Engine
### Google V8 JavaScript Engine
- Googleが開発するオープンソースのJIT Virtual Machine型JavaScript実行エンジン。
- [[https://developers.google.com/v8/intro][Chrome V8]]
  
#### Browsers
- Google Chrome
- Android Browser
### JavaScriptCore
- built-in JavaScript engine for WebKit.
- [[https://trac.webkit.org/wiki/JavaScriptCore][JavaScritCore]]
### SpiderMonkey
- SpiderMonkey is Mozilla's JavaScript engine written in C/C++.
  It is used in various Mozilla products, including Firefox, and is available under the MPL2.
- [[https://developer.mozilla.org/en-US/docs/Mozilla/Projects/SpiderMonkey][SpiderMonkey - MDN]]
### Chakra
- JavaScript engine developed by Microsoft for IE9.
  
## Etc
### CG Libraries
#### Skia
- Googleが開発している、C++で書かれたオープンソースの2次元コンピュータグラフィックスライブラリ。
  Skia.inc.が開発していたが、2005年にGoogleが買収、その後修正BSDライセンスとしてオープンソースライブラリとなった。

##### 利用
- Mozilla Firefox
- Google Chrome
- Android
- Google Chrome OS
- Blink
### Build Tool
#### GYP
- 自動ビルドツール。Googleにより作成された。
  Chromiumウェブブラウザをビルドするために統合開発環境のプロジェクトファイルを生成するオープンライセンスソフトウェア。
  BSDライセンス。

## Link
- [[http://www.html5rocks.com/ja/tutorials/internals/howbrowserswork/][ブラウザの仕組み:最新ウェブブラウザの内部構造 - HTML5 ROCKS]]

### ブラウザの仕組み / リクルート
- [[https://speakerdeck.com/recruitengineers/browser-b45d3a59-af2b-449c-992e-fd7563745f80][ブラウザ / Browser - SQUARESPACE]]
- 2021年度リクルート エンジニアコース新人研修の講義資料

#### Structure
- Structure
  - User Interface : ブラウザのインターフェース。アドレスバーとか戻るボタンとか
  - Browser Engine : レンダリングエンジンを操作するブラウザの核、データ層と調停する
  - Rendering Engine : コンテンツの描画。HTMLならページをパースしてロードする
  - Network : ネットワーク層、HTTP/HTTPSリクエストをしたりする
  - JavaScript Engine : JavaScript実行エンジン。v8, SpiderMonkeyなど
  - UI Backend : inputのUIなど、共通ウィジェット部分のUI。場合によってはOS共通のことも。
  - Data Storage : ディスクに保存するレイヤ。Cookieとかlocalstorageとか。

#### レンダリングエンジン
- レンダリングプロセス
  - [html] -> Parse -> [DOM] -> Style -> [Styled] -> Layout/Paint -> [Screen]

### [[https://browserbook.shift-js.info/][ちいさなWebブラウザを作ろう]]
- [[https://speakerdeck.com/lmt_swallow/build-your-own-web-browser][ちいさなWebブラウザを作ってみよう(オンライン講義版) - speakerdeck]]

### Browser実装対応状況
- [[http://caniuse.com/][Can I Use?]]
- [[http://fmbip.com/litmus/][HTML5 & CSS3 Support - findmebyIP.com]]

- [[https://developer.microsoft.com/en-us/microsoft-edge/platform/status/][Platform status - Microsoft Edge]]
- [[https://www.chromestatus.com/features][Chrome Platform Status]]
- [[https://developer.apple.com/library/mac/releasenotes/General/WhatsNewInSafari/Introduction/Introduction.html][What's New in Safari - Mac Developer Library]]


### Chrome / Chromium
- [[https://www.youtube.com/playlist?list=PLNYkxOF6rcICgS7eFJrGDhMBwWtdTgzpx][Chrome Univercity - YouTube]]
- [[https://docs.google.com/presentation/d/12wd3hLkXVny0b5LnzizmH_3xe8zJ2WY5_9JprfIkp-o/edit#slide=id.g82989a6582_1_134][電子情報学特論：Chromiumのアーキテクチャを解き明かす ～EEICの授業が生きるプロダクトの世界～]]

### Ablaze
- https://ablaze.one/
- 中高生でFireboxベースのブラウザを作っているとのこと。。

## Memo
### Font
#### EmbeddedOpenType
- 
  EmbeddedOpenType(EOT)は、OpenTypeファイルをコンパクトに格納した形式で、米マイクロソフトが開発。
  Webページの組み込みフォントとして用いられる。
  一般に拡張子「.eot」を使用する。

#### WebOpenFontFormat
- 
  WOFF(Web Opne Font Format)はMozillaが中心となり開発したWebフォント。
  @font-faceタグをCSSに記述して利用する。
  拡張子は「.woff」

#### TrueType
- 
  拡張子は「.ttf」

#### OpenType
- 
  拡張子は「.ttf, .otf」

#### SVG Font
- 
  拡張子は「.svg, .svgz」
### Langage Settings
- 
  ブラウザの言語設定を変更する。

- Link
  [[http://freesoft.tvbok.com/youtube_f/method/browser_jp.html][ブラウザやＯＳの言語をチェックする (逆に日本語以外にする裏技) - ぼくんちのTV別館]]
  [[http://memorva.jp/internet/pc/browser_language.php][ブラウザの言語設定 - 日本語が表示されない・英語が表示される - MEMORVA]]
### Proxy
- IE, Firefoxは別プロキシ設定らしい。
- Chromeは、--proxy-server起動オプションを付ける、
- Proxyを操作するChrome Extentionも複数存在。
  - Proxy SwitchyOmega
  - Proxy SwitchyShrap
