# Ruby on Rails
## Philosophy
- Don't Repeat Yourself: DRY
- Convention Over Configuration

## REST
### GET
- 
  データ読取

### POST
- 
  作成

### PATCH
- 
  更新。
  以前はPUTリクエストを使っており、Rails40でもサポートはされているが、
  PATCHの方が意図にあうため、PATCHが推奨されている。

### DELETE
- 
  削除

## Architecture
### Controller
- 
  "@"をつけて変数を定義すると、ビュー中で使用できる。

### View
- 
  アクションはファイル名を手がかりにビューを探すので、
  コントローラ名とアクション名に対応させる必要がある。
  コントローラと同じフォルダ配下にアクション名とマッチするビューファイルを置く。

### Model
#### ActiveRecord::Base
##### クラスメソッド
- new
  ユーザを作成する
- create
  new + saveまで行うメソッド。
  DBにレコードが追加される。
- find
  idを引数にとり、該当するユーザを返す。
- find_by_(column_name)
  (column_name)の属性に基づいて、引数を検索する。
- find_by
  第1引数にカラム名、第2引数に検索条件をとり、値を検索する。
  find_by_(column_name)メソッドより普遍性が高く、こちらの使用が推奨される。
  ex) User.find_by(email: "mhartl@example.com")
- first
  最初のユーザを返す
- all
  全てのユーザを配列で返す。
  
##### インスタンスメソッド
- save
  レコードを保存する
- (column_name)
  ドット記法を使って属性にアクセスできる。
- (column_name)=
  ユーザの属性を更新する。更新後saveが必要。
- destroy
  レコードを削除する。
- reload
  データベース情報を元にオブジェクトを再読み込みする。
  従ってsaveしていない情報は消える。
- valid?

## Command
### rails
#### new
- 
  create new rails application.
  ex) rails new appname

- -h
  show command options

#### server
- 
  サーバを起動する。
  "rails s"でもよい。
#### generate
##### controller
- controllerName actionName
  キャメルケースで渡すと、スネークケースのファイルを自動的に生成する。
  ただし単なる慣習なので、スネークケースのコントローラ名を入力しても
  同様にスネークケースのファイル名が出力される。

- 
  ex)generate controller welcome index
  Above, a controller, which called "welcome" with an action called "index", is created.

##### model
- 
  モデルを作成する。
  慣習として、controllerには複数形を使い、modelには単数形を使う。
  ex) rails generate model User name:string email:string
##### integration_test

#### console
- 
  Railsアプリケーションを対話的に操作することが出来る。
  exitを入力すると終了できる。
  Ctrl-Cでスタックから抜ける。Ctrl-Dで完全にコンソールを終了する。
  "rails c"でもOK。

- --sandbox
  サンドボックスモードで起動する

#### dbconsole
- 
  figuring out which database you're using and drops you into whichever command line interface you would use it.
  It supported MySQL, PostgreSQL, SQLite and SQLite3.

#### runnner
- 
  runner runs Ruby code in the context of Rails non-interactively.

#### destroy
- 
  generateの逆で作成したコードを削除する
  ex) rails destroy controller FooBars baz quux

### rake
- 基本はRuby.org/Toolsに記載。
  ここにはrailsで定義されているものを記載する予定
#### db
- db:migrate
  マイグレーションを変更する
  初めて実行した際にdb/development.sqlite3というファイルが生成される。
  - VERSION=0
    最初の状態に戻す
- db:rollback
  1つ前の状態に戻す

#### routes
- 
  list all of defined routs.

#### test
- test:prepare
  データモデルdb/development.sqlite3がテストデータベースdb/test.sqlite3に反映されるようにするもの。
  たまにテストデータベースが壊れるので、このコマンドを実行する必要があるらしい。

## File/Directory

- README.rdoc
  アプリケーションの簡単な説明

- Rakefile
  rakeコマンドで使用可能なタスク

- Gemfile
  このアプリケーションに必要なGemの定義ファイル

- Gemfile.lock
  アプリケーションの全てのコピーが同じgemのバージョンを使用していることを確認するために使用されるgemリスト

- config.ru
  Rackミドルウェア用の設定ファイル

- .gitignore
  Gitに含めないファイルを指定する。

### app/
- 
  モデル、ビュー、コントローラ、ヘルパーなどを含む主要なアプリケーションコード

#### app/assets/
- 
  アプリケーションなどで使用するCSS(Cascading Style Sheet)、JavaScriptファイル、画像などのアセット

##### app/assets/stylesheets
- 
  stylesheetが入っている。scss。

##### app/assets/javascripts
##### app/assets/images

#### app/controllers/
#### app/models/
- 
  モデルファイルが格納される。
#### app/views/
##### app/views/layouts/
- 
  Webサイトのレイアウトが格納されている。
  ex) application.html.erb

##### app/views/static_pages/
- 
  
#### app/helpers/
- 
  ヘルパーの定義ファイルが格納されている
  モジュールを定義すると、Railsが自動的に全てのビューにインクルードしてくれる。

### bin/
- 
  バイナリ実行可能ファイル
- rails
  コード生成、コンソールの起動、ローカルのWebサーバの立ち上げなどに使用するRailsスクリプト

### config/
- 
  アプリケーションの設定
- routes.rb
  - root 'welcome#index'
    アプリケーションのルートURLへのアクセスをwelcomeコントローラのindexアクションに割り当てる。
  - get 'welcome/index'
  - get 'static_pages/home'
    /static_pages/homeというURLに対するgetリクエストに対し、
    StaticPagesコントローラのhomeアクションと結びつける。
  - match '/about', to: 'static_pages#about', via: 'get
    '/about'へのGETリクエストにマッチし、StaticPagesコントローラのaboutアクションにルーティングされる。
    また、自動的に名前付ルートを生成する。
    - about_path -> '/about'
      about_url  -> 'http://localhost:3000/about'
  - root 'static_pages#home'

- [[http://railsguides.jp/routing.html][Railsのルーティング - RailsGuides]]

### db/
- 
  データベース関連のファイル
- development.sqlite3
  初めてdb:migrateが実行された際に生成される。
  SQLiteデータベース。
#### db/migrate/
- 
  マイグレーションと呼ばれるファイルが置かれる。
  マイグレーションはデータベースをインクリメンタルに変更する手段を提供する。
##### マイグレーションファイル
- 
  データベースの変更を定義したchangeメソッドの集まり。

### doc/
- 
  マニュアルなど、アプリケーションのドキュメント

### lib/
- 
  ライブラリモジュール

- assets
  ライブラリで使用するCSS、JavaScripts、画像などのアセット

### log/
- 
  アプリケーションのログファイル

### public/
- 
  エラーページなど、一般（Webブラウザなど）に直接公開するデータ

### test/
- 
  アプリケーションのテスト（spec/ディレクトリがあるため、現在は使用されていない。)

### tmp/
- 
  一時ファイル

### vendor/
- 
  サードパーティのプラグインやgemなど

- assets
  サードパーティのプラグインやgemで使用するCSS、JavaScripts、画像などのアセット

## Helper
### link_to
- 
  アンカータグaを使用したリンクを作成する。
  第1引数がリンクテキスト、第2引数がURL、第3引数がオプションハッシュ。

### image_tag
- 
  画像ファイルのパスと任意のオプションハッシュを取る。
  ex) image_tag("rails.png", alt: "Rails")
      => <img alt="Rails" src="/assets/rails.png" />

### render
- 
  ファイルを探してその内容を評価し、結果を挿入する。パーシャルという機能。
  "render 'layouts/shim'"とした場合、app/views/laiyouts/_shim.html.erbというファイルを利用する。
### stylesheet_link_tag
### javascript_include_tag
### csrf_meta_tags
## Memo
### form_for
- 
  
### heroku
(他に書くところもないので、とりあえず。。)

#### command

- heroku login
- heroku create
- git push heroku master
- heroku open
- heroku rename

### rspec
- 
  ダブルクォート""で囲った文字列は評価しない
  ex)
  describe "Home page" do
    it "should have the content 'Sample App'" do
      visit '/static_pages/home'
      expect(page).to have_content('Sample App')
    end
  end

- beforeブロック
  ex)
  before { visit root_path }

- pending
  成功と失敗の間の状態を発生させる

- be_(return_boolian)
  真偽値を返すfoo?メソッドにオブジェクトが応答する場合、
  テストメソッドbe_fooが自動的に存在する。

### erb
- 
- <% ... %>
  中に書かれたコードを単に実行する。表示されない。
- <%= ... %>
  中に書かれたコードが実行され結果がテンプレートに挿入する。中身が表示される

### Rails環境
- development
- test
- production
### Asset Pipeline
- 
  アセットをディレクトリに配置し、さまざまなプリプロセッサエンジンを介してそれらを実行し、
  ブラウザに配信できるようそれらをマニフェストファイルを用いて結合する。

  プログラマにとっては分割され見やすく、
  実行環境にとってはファイルが1つにまとめられるので取込のオーバーヘッドがない。
  また空白を取り除くことでファイルサイズも縮小してくれる。

#### アセットディレクトリ
- 3.0以前
  Rails3.0以前は静的ファイルは以下に置かれていた。
  - public/stylesheet
  - public/javascrit
  - public/images

- 3.1以降
  3.1以降では、静的ファイルを目的別に分類する、標準的な3つのディレクトリが使用される。
  - app/assets
    現在のアプリケーション固有のアセット
  - lib/assets
    開発チームによって作成されたライブラリ用のアセット
  - vendor/assets
    サードパーティのアセット

#### マニフェストファイル
- 
  アセットをどのように1つのファイルにまとめるかを指示する。
  実際にまとめるのはSprockets gem。
  CSSとJavaScriptには適用されるが、画像ファイルには適用されない。

#### プリプロセッサエンジン
- 
  ファイルの拡張子を使用してどのプリプロセッサを使うか判断する。
  Sass用の.scss、CoffeeScript用の.coffee、埋め込みRuby(ERb)用の.erbあたりが一般的。
  つなげて実行することが出来る。
  
  ex) foobar.js.erb.coffee
  上の例の場合、CoffeeScriptとERbの両方で実行される。
  コードは右から左に実行されるので、CoffeeScriptが先に実行される。
  
### Error
#### Routing Error
- This error occurs because the route needs to have a controller defined in order to serve the request.
#### Unknown action
- This error indicates that Rails cannot find the new action inside the controller.
#### Template is missing
- Rails expects plain actions like this one to have views associated with them to display their information.
#### ActiveModel::ForbiddenAttributesError...
### Progress Memo
#### Link
- link_to helper
  <%= link_to "text", "URL" %>
  writing on .erb file

#### 名前付きルート
- rake routes
  ex) about GET /about home#about
      →about_pathは/aboutを指す。
        左側の名前に_pathをつけたものが名前付きルートになる。

#### ルートパス
- 
  /直後にURLが置かれないものの指定を行う
  routes.rbに以下のように書く。
  ex) root 'home#top'

#### ビューの共通部分
- 
  application.html.erbに書かれる。
  格ビューファイルのコードは、<%= yield %>の部分に代入されて表示される。
  
  stylesheet_link_tagでcssを、javascript_include_tagでjsを読み込んでいる。
  
#### command

##### rails generate model
- rails generate model モデル名 カラム名：データ型
- 指定したカラム以外に、id, created_at, updated_atカラムが自動で生成される。

##### rake db:migrate
- 
  dbの生成

##### rails console
- 
  console操作ができる

###### quit
##### bundle install
- gemfileに書いた内容をインストールしてくれる

#### helper

##### link_to
##### stylesheet_link_tag
##### javascript_include_tag
##### redirect_to
- 
- 引数の省略
  1. redirect_to note_path(@note.id)
  2. redirect_to note_path(@note)
  3. redirect_to @note

##### view
###### form_tag
- メソッドの指定
  method:'patch'
###### text_field_tag
###### text_area_tag
###### submit_tag
###### form_for
#### Model
##### Class.new

##### instance.save

##### Class.all

##### Class.find()

##### instance.destroy

##### validate
- 
  ex) validates:column_name, presence:true, other_validations:...

###### validations
- presence: true
- length: {maximum:140}
#### Verb
- Create : POST
- Read : GET
- Update : PATCH
- Delete : DELETE
  
#### scaffold
- 
  rails g scaffold (ModelName) Column:DataType ...
  
#### resources
- 
  
#### before_action
- 
  各アクションが行われる前に指定したメソッドを呼び出すことができる。

##### only
- 
  ex) before_action :set_note, only: [:show, :edit, :update, :destroy]

#### strong parameter
- 
  ex) params.require(:note).permit(:title, :content)
#### render method
- 
  redirect_toと異なりアクションを経由せず、ビューファイルを表示する。

#### errors.full_messages
- 
  ex) @note.errors.full_messages.each

#### notice function
- 
  一度だけ表示したいメッセージを簡単に設定できる。
  redirect_toの第二引数で設定して(ex: redirect_to @note, notice:'メッセージ'),
  viewで表示する(ex: <%= notice %>)
## Link
- [[https://railsguides.jp/][Ruby on Rails ガイド]]
- [[https://railstutorial.jp/][Ruby on Rails チュートリアル]]

  
