# Infrastructure
## Server
### Structure
#### Proxy プロキシ
- 
  内部のクライアントと外部のサーバの間に立って要求を代理で処理する。
  以前は回線速度を補うための処置として利用されていたが、同目的では最近は利用されない。
  セキュリティ上の

#### Reverse Proxy リバースプロキシ
- 
  クライアントとWebサーバの間に立って要求を代理で処理する。
  外部クライアントからの接続要求を内部サーバへ中継する機能。
  Webサーバはリバースプロキシへ応答を返す。

#### Application アプリケーション
#### Database データベース
#### Sorry
## OS
### Posix
## Hypervisor
- [[http://syuu1228.github.io/howto_implement_hypervisor/][ハイパーバイザの作り方]]
## Network
### Glossary
#### Contents Delivery Network, CDN
- 
  ユーザのネットワーク位置に応じた最適な配布ポイントを指示することで、
  大容量のコンテンツをスムーズにユーザに配信できるようにする。

## Database
### Relational
#### Oracle
- [[file:OracleDB.org][OracleDB.org]]

#### SQL Server
- [[file:./SQLServer.org][SQLServer.org]]

#### MySQL
- [[file:./MySQL.org][MySQL.org]]

#### PostgreSQL
- [[file:./PostgreSQL.org][PostgreSQL.org]]

### NoSQL
- [[file:./NoSQL.org][NoSQL.org]]

### Link
- [[http://yuuki.hatenablog.com/entry/architecture-of-database-connection][Webシステムにおけるデータベース接続アーキテクチャ - ゆううきブログ]]
### Glossary
#### 垂直分割
- 
  列ごとに（またはテーブル単位で）分割

#### 水平分割
- 
  行ごとに分割

#### sharding データベースシャーディング
- 
  shard -> 「破片」といったような意味

## Storage

## Operation
### Monitoring
- 監視目的
  - セキュリティ監視
  - ログ監視
  - ネットワーク監視
  - サービス監視
  - パフォーマンス/リソース監視

#### 死活監視
- 
  pingの応答監視、プロセスの起動監視、ポートの応答監視等


#### リソース管理
- 
  CPU、メモリ、ディスク、ネットワークなど、OSやハードウェアのリソース使用状況を収集する。

### Security
- [[file:Security.org][Security.org]]
## Performance
### Memory
#### Linux
##### Link
- [[http://www.math.kobe-u.ac.jp/~kodama/tips-free-memory.html][Linux のメモリー管理(メモリ－が足りない？,メモリーリークの検出/防止) - K.Kodama's page]]
- [[http://www.atmarkit.co.jp/ait/articles/0810/01/news134.html][減り続けるメモリ残量！ 果たしてその原因は!(1/3) - @IT]]

### Glossary
#### Throughput
- 単位時間にどれだけ理できるか

#### Latency
- 処理にかかる時間
## Glossary
### Bare Metal ベアメタル
#### Bare Metal
- OSなどのソフトウェアを組み込んでいない、ハードディスクやンピュータのこと。
  「むき出しの金属装置」といったニュアンス。

#### Bare Metal Cloud
- 仮想サーバの設計として、物理サーバ上にOS層を設けず、ハイパーバイザーを組み込み、
  その上に直接仮想サーバを構築する技術をベアメタル方式、という。
  これらの方式で提供されている仮想サーバをベアメタルサーバといい、
  ベアメタルサーバで提供されているクラウドサービスを一般にベアメタルクラウドという。
  
### Converged Infrastructure コンバージドインフラストラクチャ
- 有名製品
  VCE「Vblock」、シスコとNetApp「FlexPod」など。
### Hyperconverged Infrastructure ハイパーコンバージドインフラストラクチャ
- 特徴
  - 共有ストレージアレイを使わず、各サーバのローカルストレージを使う
  - 複数台ネットワーク接続してクラスタ構成とする
  - Software-Defined Storage機能により、ローカルストレージをスケールアウトストレージにする機能を備える
- 有名
  - Nutanix
- http://cn.teldevice.co.jp/column/detail/id/98
### 3 Tier
- サーバ、SANスイッチ（ネットワーク）、ストレージ、の3層構成。
- コンバージドに対しての説明のためよく用いられる。
  コンバージドは、上記を1台のラックに検証済みの状態でパッケージングされており、
  
### SDN / Software Defined Network
### SDS / Software Defined Storage
### SRE / Site Reliability Engineering
- サイトの信頼性保証
- 
## Link
- [[http://yuuki.hatenablog.com/entry/large-scale-infrastructure][はてなで大規模サービスのインフラを学んだ - ゆううきブログ]]a
- [[http://blog.harukasan.jp/entry/2014/09/11/181006][インターン生向け講義で発表しました#pixiv - BLOG::はるかさん]]
