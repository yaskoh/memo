# Nginx
## About
- 処理性能、高い並行性、メモリ使用量の小ささに焦点を当てて開発されている。
  5億アクセス/日を処理可能
- HTTP, HTTPS, SMTP, POP3, IMAPのリバースプロキシ機能や、ロードバランサ、HTTPキャッシュ機能を持つ
- BSDライクライセンス

## Memo
### Apacheとの違い
#### 1
- ApacheはHTTPサービスに特化、Nginxは他サービスにも柔軟に対応可能。
  ロードバランサーのような利用や、メールサーバに指示を出す等も可能。
- Apacheは重たい仕事も全部自分でこなす
  Nginxは早く処理するために作られているので、自分で重たい仕事をせず、他に割り振ることを得意としている。
- Nginxは同時リクエストを多く処理することに特化しているため、余計な機能をつけていない非常にシンプルなもの。
  メモリ使用量も少ない。
- https://academy.gmocloud.com/qa/20160616/2761

#### 2
- Apache HTTP Server
  - マルチプロセスモデル : 接続ごとにプロセスをフォークするのでメモリを多く使う
  - 利点 : メモリ空間が独立しており、スクリプト言語が組み込みやすい
    WindowsサーバだとApacheのほうが早い
  - 欠点 : メモリ欠乏しやすい
    →モジュールを利用してイベント駆動モデルにもできる

- Nginx
  - イベント駆動モデル : 1プロセスないで接続ごとにイベント処理を行う
  - 利点 : 接続数が増えてもプロセスやスレッド数が増えない。消費メモリが増えない
  - 欠点 : 1つのメモリ空間で動作するため、スクリプト言語を組み込めない
    →プロキシサーバとして利用して呼び出すことは可能

- https://qiita.com/tomoyamachi/items/06b2eca14987a30b8fda

## Link
- http://nginx.org/
- http://nginx.org/en/docs/

- http://mogile.web.fc2.com/nginx/
