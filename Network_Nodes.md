# Network Nodes
## L1
### Repeater
### Hub
### Modem
- 
  EIA/TIA-232（シリアルポート）規格のケーブルで接続する。
 
### TA
- Terminal Adapter
  EIA/TIA-232（シリアルポート）規格のケーブルで接続する。
### DSU
- Digital Service Unit
  回線用デジタル信号と、コンピュータなどの端末用デジタル信号は異なるため、それを合わせる装置。
### ケーブルモデム
- CATVで使用されるケーブルとの接続に使用されるモデム。
  LANケーブルで接続される。
### ADSLモデム
- ADSL用のモデム。
  LANケーブルで接続される。
### スプリッタ
- 
  音声信号とデータ信号を振り分ける機械。
## L2
### Bridge

### Switch
#### Layer 2
#### Layer 3
#### Layer 4

## L3
### Router

## L4-
### Firewall
#### Classification
##### Interface Type
###### デュアルホームドホスト
- 2つ以上のネットワークインターフェースを持っている
###### ゲート
- 1つしかネットワークインターフェースがないもの
##### OSI基本参照モデル
###### パケットフィルタリング
###### サーキットレベルゲートウェイ
###### アプリケーションレベルゲートウェイ
#### Feature
##### パケットフィルタリング
##### ステートフル・インスペクション/動的ルール
##### DMZ（非武装セグメント）
### Load Balancer
#### Functions 機能
##### Balancing ロードバランシング、負荷分散
###### Balancing Algorithm
####### Static
######## Round Robin
######## Ratio
####### Dynamic
######## Least Connection
- 最も少ないコネクションのサービスにリクエストを振り分ける。
######## Fastest
######## Observed
######## Predictive
######## Dynamic Ratio
##### Persistence パーシステンス、セッション維持
###### Persistence Type
####### Source address afinity persistence
- クライアントの送信元IPアドレスを見て、転送するサーバを固定する
####### Cookie persistence
######## Insert Mode
######## Rewrite Mode
######## Passive Mode
######## Hash Mode
####### SSL persistence
- SSLセッションIDに従ってリクエストを振り分ける。
- IEはデフォルト2分でSSLセッションを再手続してしまうものがあり、現実的には採用が難しい。
####### Destination address affinity persistence
##### Moniter モニター、監視
###### Helth check type
####### Address Check / ICMP
####### Service Check / TCP
####### Content Check / HTTP
####### Interactive Check / FTP
####### TCP-ECV
####### HTTP-ECV
####### UDP-ECV
####### PING
#### MachineKind 機種
##### BIG-IP / F5
###### Memo
####### データ圧縮とRAMキャッシュの最適化
######## http
######## http-wan-optimized-compression
- データ圧縮を最適化しつつ他の設定にhttpプロファイルのデフォルト値を使いたい場合に適している。
######## http-lan-optimized-caching
######## http-wan-optimized-compression-caching
###### Link
- [[http://www.f5networks.co.jp/shared/f5pm/manual/bigip/data/ja/10_0/BIG-IP_LTM_100_guide_ja.pdf][BIG-IP Local Traffic Management 設定ガイド バージョン 10.0.0.0]]

#### Link
- https://www.macnica.net/citrix/ns_01.html/ (citrix)
- http://www.infraexpert.com/study/loadbalancer4.html
- http://news.mynavi.jp/series/load_balancer/001/
- http://ascii.jp/elem/000/000/506/506272/

### DNS Server
#### About
##### Root Server
- 世界に13台(グローバルアドレスの数。実際は冗長化されている)。
#### Records
##### SOA
- Start Of a zone Of Authority
- ドメイン/ゾーン情報を記載する。
  - ドメインのDNSサーバ名
  - ドメイン管理者のメール・アドレス・シリアル番号
  - 更新間隔(refresh)
    ゾーン転送感覚時間を秒で指定する
  - 転送再試行時間(retry)
    ゾーン転送に失敗した場合の再試行までの有効時間を秒で指定する
  - レコード有効時間(expire)
  - キャッシュ有効時間(TTL)
##### NS
- ドメインのDNSサーバ名を指定する
##### A
- ホストのIPアドレス。正引きのためのレコード。
##### PTR
- IPアドレスに対するホスト名。逆引きのためのレコード。
##### CNAME
- ホスト名のエイリアス（別名）
##### MX
- ドメインのメール・サーバ名
##### HINFO
- ホストの追加情報。ホストのハードウェア・ソフトウェア(OS)情報を記述する
##### WKS
- ホストで実行されているサービス情報(Well Known Services)
##### TXT
- ホストへのテキスト情報
##### Link
- http://www.atmarkit.co.jp/ait/articles/0112/18/news001.html
