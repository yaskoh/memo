# Redmine
## Display
### Home / ホーム
### My page / マイページ
#### パーソナライズ
### Project / プロジェクト
#### 各プロジェクト
##### 概要
##### 活動
##### チケット
##### ガントチャート
##### カレンダー
##### ニュース
##### 文書
##### Wiki
##### ファイル
##### 設定
### Administration / 管理
#### Projects / プロジェクト
##### 新しいプロジェクト
##### 各プロジェクト / 設定
###### 情報
###### モジュール
###### メンバー
###### バージョン
###### チケットのカテゴリ
###### Wiki
###### リポジトリ
###### フォーラム
###### 作業分類（時間管理）
#### Users / ユーザー
##### 新しいユーザー
- 新規ユーザの作成
#### Groups / グループ
#### Roles ad permissions / ロールと権限
#### Trackers / トラッカー
#### Issue statuses / チケットのステータス
#### Workflow / ワークフロー
#### Custom fields / カスタムフィールド
#### Enumerations / 列挙項目
#### Settings / 設定
##### 全般
###### ホスト名
###### プロトコル
##### 表示
###### デフォルトの言語
###### ユーザー名の表示形式
##### 認証
##### API
##### プロジェクト
##### チケットトラッキング
##### ファイル
###### 添付ファイルとリポジトリのエンコーディング
- 以下のようにカンマ区切りで設定することで、utf-8, cp932等が扱える
  utf-8,cp932,EUC-JP
##### メール通知
##### 受信メール
##### リポジトリ
#### LDAP authentication / LDAP認証
#### Plugins / プラグイン
#### Information / 情報
### Help / ヘルプ
### My account / 個人設定
## Documentation
### Redmine guide
- https://www.redmine.org/projects/redmine/wiki/Guide
- http://guide.redmine.jp/

#### Installation guide インストールガイド
##### Installing Redmine
###### インストール手順
####### 動作環境
- OS : ほぼなんでも
- Ruby : 3.4 -> ruby 1.9.3, 2.0.0, 2.1 - 2.4
- DB : 
  - MySQL 5.0 - 5.5
  - PostgreSQL 8.3 - 
    - 日付形式はISO(default)にする
- Options
####### Step1 Redmine本体のインストール
- e.g.
  wget http://www.redmine.org/releases/redmine-3.4.4.tar.gz
####### Step2 空のデータベースとユーザーの作成
- Postgres : role "redmine"の作成と、DB"redmine"を作成したロール（ユーザ）をオーナーとして作成
  
####### Step3 データベース接続設定
####### Step4 依存するソフトウェアのインストール
- gem install bundler
- redmineのGemfileがあるところでgem install [--without development test rmagick]

- memo 2018/2/25
  - 詰まったところ
    - nokogiri : いくつかライブラリが必要。nokogiriのサイトへ行ってapt-get
    - pg : postgresのdevelが必要。apt-get insttall libpq-dev
####### Step5 セッションストア秘密鍵の生成
- bundle exec rake generate_secret_token
  - rakeはよくわからないが、lib/tasks/initializers.rakeで定義されている模様。
    -> config/initializers/secret_token.rb
####### Step6 データベースのテーブル等作成
- RAILS_ENV=production bundle exec rake db:migrate
  - おそらくrailsのrake定義
####### Step7 デフォルトデータ
- RAILS_ENV=production bundle exec rake redmine:load_default_data
####### Step8 ファイルシステムのパーミッション
- Redmine実行OSユーザは、以下のディレクトリに対する書き込み権限が必要
  - files
  - log
  - tmp, tmp/pdf
  - public/plugin_assets
####### Step9 インストールの確認
- bundle exec rails server webrick -e production
####### Step10 ログイン
- admin/admin
####### 設定
- Redmine設定は"config/configuration.yml"で定義
######## メール・SMTPサーバの設定
######## バージョン管理システムの設定
######## 添付ファイル保存ディレクトリ
######## ログの設定
######## バックアップ
######## Linux/UNIX環境補足
######## Win環境補足
###### Email configuration メールの設定
##### Upgrading an existing installation
##### Migration from other systems
##### Backing up and restoring Redmine
#### Administrator guide システム管理者向けガイド
##### Common configuration
###### Managing projects
###### Managing users
###### Managing groups
###### Roles and permissions
###### Issue tracking system
###### Custom fields
###### Enumerations
###### Application settings
##### Advanced configuration
###### Configurating repositories
###### Receiving emails
###### Sending reminder emails
###### LDAP Authentication
##### Maintenance operations
###### Rake tasks
#### User guide ユーザーガイド
##### Getting Started
##### User accounts
##### Login
##### Register
##### Search
##### My page
##### Project overview
##### Project atcivity
##### Isuue tracking
###### Issue list
####### Issue summary
###### Roadmap
####### Version overview
###### Time tracking
####### Spent-time details
####### Spent-time report
###### Gantt
###### Calendar
###### News
###### Documents
###### Files
###### Forums
###### Wikis
###### Repository
####### Statistics
###### Project settings
###### Files attached to Redmine resources
###### Text formatting in Redmine
####### Textile
####### Markdown
###### Keyborad Navigation
#### Developer guide 開発者ガイド
##### General development
##### Plugin development
##### Theme development
##### Alternative/Custom Authentication
### Redmine.JP
- http://redmine.jp/tech_note/
#### はじめてのRedmine
##### Redmineを使い始めるための初期設定
###### ログイン
- インストール直後はadmin/adminでログイン
###### adminユーザのパスワード変更
- パスワード変更
###### デフォルトデータのロード
- インストール時に以下を行えば不要。
  - rake redmine:load_default_data RAILS_ENV="production"
- 管理
  言語設定後、デフォルト設定のロードを実行
###### 日本語での利用に適した設定
- 「デフォルトの言語」を「日本語(Japanese)」に
  - 管理 -> 設定 -> 表示 -> デフォルトの言語
- 「ユーザ名の表示形式」で姓が先に来るように設定
  - 管理 -> 設定 -> 表示 -> ユーザー名の表示書式
- リポジトリブラウザで文字コードの自動判別を設定
  - 管理 -> 設定 -> ファイル -> 添付ファイルとリポジトリのエンコーディング
###### メールに含まれるRedmineのアドレスを正しく設定する
- ホスト名を設定
  - 管理 -> 設定 -> 全般 -> ホスト名、プロトコル
###### ユーザーの追加
- 管理 -> ユーザー -> 新しいユーザー
###### プロジェクトの追加
- 管理 -> プロジェクト -> 新しいプロジェクト
###### プロジェクトのメンバーを追加
##### Redmineの使い方
###### ログイン
###### パスワードの変更
- 個人設定 -> パスワード変更
###### チケットの確認
- プロジェクト -> プロジェクト選択 -> チケット
- 表示 : 題名を選択
- 絞り込み : フィルタを追加
###### チケットの登録
- プロジェクト、チケット、新しいチケット
###### チケットの更新
- プロジェクト、チケット、選択、編集
###### マイページの活用
-
##### 用語解説
#### インストール
- http://redmine.jp/install/
## Directory Structure
### Linux
#### app/
#### bin/
#### config/
##### configuration.yml
##### database.yml
##### database.yml.example
- DB接続設定テンプレート。コピー・編集して使う。
#### db/
#### doc/
#### files/
#### log/
#### public/
##### assets/
- プラグインが使用する画像やCSS
#### tmp/
##### pdf/
## Plug-ins
### redmine_absolute_dates
- https://github.com/suer/redmine_absolute_dates
- 日付を相対日付でなく絶対日付表示とする。
### redmine_issue_templates
- https://github.com/akiko-pusu/redmine_issue_templates
## 記法
### Redmineのwiki記法
### textile記法
- [[https://www.promptworks.com/textile][Textile Reference Manual - promptworks]]
- [[http://redmine.jp/tech_note/textile/][textile記法 - Redmine.jp]]
## Reveres Lookup
### HTTPS化
## Link
- https://www.redmine.org/projects/redmine
- http://redmine.jp/

- https://www.redmine.org/projects/redmine/wiki/Guide
- http://guide.redmine.jp/

- https://bitnami.com/stack/redmine/installer

- https://qiita.com/y_hokkey/items/44cae35f4a3f359f5c25
