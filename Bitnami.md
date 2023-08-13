# Bitnami
## Applications
### Redmine
#### Memo
##### インストールフォルダの注意点
- インストールフォルダを"redmine-3.2.1-0"などとするとエラーとなる模様。
  "redmine"などとするとよいかも。
  http://labo.ysreading.co.jp/2016/04/12/bitnami-redmine%E3%82%92%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%AB%E3%81%99%E3%82%8B%E9%9A%9B%E3%81%AB%E6%B0%97%E3%82%92%E3%81%A4%E3%81%91%E3%82%8B%E3%81%9F%E3%81%A0%EF%BC%91%E3%81%A4/
##### コマンドの利用
- 「Bitnami Redmine Stack を使用する」を使うと、パスが通ったcmdを利用可能。
  更にlsなどのコマンドも利用可能。
##### プラグインのインストール
- 以下に配置
  - Bitnami/redmine/apps/redmine/htdocs/plugins/{plugin_folder}
- migrateなど
  - bundle install --without development test postgresql sqlite xapian
  - bundle exec rake redmine:plugins:migrate RALIS_ENV=production
- https://dgz.jp/redmineplg/
### WordPress
