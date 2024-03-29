# Network
## Classified
### Scale
#### LAN
- Local Area Network
  狭い範囲のネットワーク

##### SAN
- Storage Area Network

#### WAN
- Wide Area Network
  LAN同士を結ぶ広いネットワーク

#### MAN
- Metoropolitan Area Network
  LANよりも広く、WANよりも狭い
  
#### NFC
- Near field radio communication
  近距離無線通信

## Model
### OSI reference model
#### Application
##### About
- 
  ユーザアプリケーションにネットワーク・サービスを提供するレイヤ。
  元々ネットワークに対応したアプリケーション以外に、リダイレクタを使い間接的にネットワークを利用するアプリケーションなどがある。
##### DNS
- 
  ドメイン名とIPアドレスを対応させるシステム。
  ドメイン名はICANNが管理、ホスト名は組織の管理者が管理する。
  
  DNSサーバは各組織に1つずつ存在し、その組織のドメイン名、ホスト名のみを管理している。
  他の組織のホスト名、ドメイン名は、その組織のDNSサーバへ聞きに行く。

###### Root server ルートサーバ
- 
  ドメインネームシステムにおいて、各空間の頂点にある情報を保持するサーバ。
  A-M.ROOT_SERVERS.NETという13台のサーバが存在する。

###### Record
####### SOA
- Start Of Authorityの略。五人に関するオーソリティ情報を示すもの。

- MNAME
- RNAME
- SERIAL
- REFRESH
- RETRY
- EXPIRE
- MINIMUM
  
####### NS
- Name Server。ドメインのネームサーバを指定する。
####### A
- Address。ホストのIPアドレスを設定。
####### AAAA
- IPv6のIPアドレスを設定。
####### CNAME
- 正規名。別名を書くときに利用する。
####### MX
- Mail Exchanger。メールサーバの情報。
####### PTR
- Pointer。逆引きレコード。
#### Presentation
##### About
- 
  ネットワークにデータを提示する層。
  ハードウェアやOSによる差異をなくしたデータ交換を行うための層。
  TCP/IPはこの層の役割をあまりきっちりこなしていない。

- 
  文字コードなどの変換や、圧縮・暗号化等を行い、アプリケーション側で意識せずに通信が行えるようにする。

- 例
  SNMPではBER(Basic Encoding Rule)、
  RPCではXDR(eXternal Data Representation)を用いる。
  
#### Session
##### About
- 
  データ転送の流れを管理する。セッション間の話し合いの管理を行う。

###### 特徴
- セッションの確立
  ポート番号を決定してレイヤ４に渡す
- Dialogue Control ダイアログ制御
  要求と応答の役割分担の取り決めを行う。
- チェックポイントの設置

- コネクションとの違い
  下位レイヤーのTransportは、「データ転送用回線の接続・切断」を示すが、
  セッションはもう一段上の「データ転送の開始と終了」を表す。
  データを送る、と会話を成立させる、の違い。
  
##### Protocol
###### NFS
- Network File System
###### RPC
- Remote Procedure Call
###### NetBIOS
- Network Basic Input/Output System

###### NetBIOS over TCP/IP, NBT
- 
  NetBIOSの機能をTCP/IPでも使えるようにしたもの。
  Windowsのコンピュータ名は、正式にはNetBIOS名と言い、マイネットワークで一覧表示される。
  
#### Transport
- 
  送信元から宛先までのデータ転送を制御・調整する

##### 特徴
###### Acknoledgement 確認応答
- 
  データを受け取った宛先は、受け取ったことを送信元に伝える。

###### Flow Control フロー制御
- 
  送られたデータは一時的にバッファに置かれて、そこで処理する。

###### エンドツーエンドの接続
- 
  ポートでアプリケーションを特定

###### Segment セグメント
- 
  データを分割して転送する。
  Sequence Number（シーケンス番号）というものがつけられる。

##### Protocol
###### TCP
- Transmission Control Protocol
  Protocolへ移動。

###### UDP
- User Datagram Protocol
  Protocolへ移動

##### Port Number
- Port番号
  16ビットの値で、通信データを流すための架空の差込口。
  各アプリケーション（正確にはプロセス毎）にポートを指定し通信を行う。
  アプリケーションとポートの接続の仕組みを「ソケット」といい、OSの「ソケットライブラリ」がTCP/IPとの連携を行う。

###### Wellknown Port : 0 ~ 1023

####### 20,21 FTP
####### 23 telnet
####### 25 SMTP
####### 53 DNS
####### 67,68 DHCP
####### 80 HTTP
####### 110 POP3
####### 161,162 SNMP

###### Registerd Port : 1024 ~ 49151
- 
  
###### Dynamic Port : 49152 ~ 65535
- 
  別名プライベートポート。クライアントPC、

##### NAPT
- Network Address Port Translation
  Linuxにおける実装名から、IP masquerade（IPマスカレード）とも。
  PATやNATe, NAT+など様々な名称で呼ばれている。
  
  IPアドレスだけでなくPort番号の変換も行うことで、
  Port番号の数だけ別の通信を区別できるようになる。
  
###### 静的NAPT
- 
  静的マスカレード、ポートフォワーディング、バーチャルホストなど、各種名称で呼ばれる。
  外部からの接続ができるよう、ソケットを固定してルータ上に設定しておく方法。

###### 問題
- 
  FTPなどデータの内部にアドレスを持つ場合、NAPTでは通信ができなくなる。
  そのため、FTPなどを例外対応として各ルータで変換などを行っているのが現状。

#### Network
##### Logical Address
- Hierarchical Addressing 階層型アドレッシング
  経路探索がしやすい
##### Networking Device
###### Router
- 
  スイッチング機能とルーティング機能を持つ
  スイッチがMACアドレスに基づいてスイッチングをするのに対し、ルータは論理アドレスに基づいてスイッチングを行う。

####### 動作
- 
  1. ホストから、パケットを受け取る。
  2. パケットの宛先IPアドレスから、宛先ネットワークを決定する。
  3. ルーティングテーブルを参照し、宛先ネットワークまでのルートを決定する。
  4. 決定されたルートに従って、決められたポートからパケットを送信する。

####### Routing
- 
  最適な経路を選択する能力。
  宛先への距離、使用するメディアの転送速度、トラフィック量（混み具合）、信頼性などを考慮し、
  よりよいルートを探し出す。
  
######## Dynamic Routing
- 動的
  ルータなどが経路情報を互いに交換しあい、自動的に生成・更新し続ける経路表（ルーティング・テーブル）に基づいて経路選択を行うこと。
  
  ルーティングプロトコルと呼ばれる通信手段に従って、ルータ同士が互いに自分が持っている経路情報を交換し合い、
  それぞれが経路表をっ自動的に生成・更新していく。

- メリット
  一台ずつ人手で経路情報を設定する必要がないため、大規模なネットワークでは機器を効率的に管理でき、
  障害発生時にも普通になった経路の情報が伝播して迂回経路が自動的に構成される。

- デメリット
  1. 外部から不正な経路情報を送りつけられるリスクがある。
  2. 経路情報の交換に一定の通信料を消費するため、通信速度がひっ迫している状況ではデメリットとなる。
  3. 最適ルートを計算する必要がある。
  4. 全てのルータが同一のルート情報を持つ必要がある。迂回が必要な場合に、情報を持っていないルータにより迂回ができなくなるため。
     全てのルータが同一のルート情報を持っている状態を"convergence"という。

######## Static Routing
- 静的
  管理者があらかじめ設定した固定的な経路表を用いる方式。
  最も優先されるルートとなる。

######## Routing Table
- 
  宛先ネットワークまでの距離、次に中継するルータ、距離、つながっている自分のポートなどが記載されている。
  ルーティングテーブルに宛先ネットワークがない場合は、スイッチとは異なり、パケットは破棄される。
  
  Routed Protocol(ルーティング対象プロトコル)毎に、ルーティングテーブルを持つ。
  IP用、IPX用、など。
  
###### Default Gateway
- 
  異なるネットワークへの出口となるルータのこと。
  したがってデフォルトゲートウェイを設定しなければ、他のネットワークとやりとりできない。
  Routerと異なるネットワーク間を接続するときに使用し、IPアドレスと経路制御表を参照してネットワーク間のパケットを中継する。
  経路制御を「ルーティング」、経路制御表を「ルーティングテーブル」という。
  
  主にルータがその役割を果たすが、プロキシサーバなどもデフォルトゲートウェイになることがある。
  
###### Computer
- 
  パソコンのネットワーク機能は、パソコン内部と外部を別のネットワークとして認識している。
  
- Windows
  "route print"で確認できる。
  0.0.0.0をデフォルトルートといい、その他すべてを表す。デフォルトゲートウェイへのパスが入っている。
  
##### Protocol
###### IP
- （詳細は別の「Protocol」を参照。）
  コネクションレス型の通信、ベストエフォート。

####### IP Packet
- 20～60byte : IPヘッダ
- 0～65,515byte : セグメントデータ

- IP Header
  |-----+--------------------------+--------------------------------------------|
  | Bit | Name                     |                                            |
  |-----+--------------------------+--------------------------------------------|
  |   4 | バージョン               | IPのバージョン                             |
  |   4 | ヘッダ長                 | IPヘッダの長さ                             |
  |   5 | サービスタイプ           | 上位プロトコルによって割り当てられた重要度 |
  |  16 | データ長                 | IPヘッダとセグメントデータを合わせた長さ   |
  |  16 | ID                       | 大きいデータを分割した際につける識別番号   |
  |   3 | フラグ                   | 分割する際に使用するフラグ                 |
  |  13 | フラグメント・オフセット | 分割を繋ぎ合わせるときに使う               |
  |   8 | TTL / Time To live       | パケットの生存時間                         |
  |   8 | プロトコル               | 使用している上位プロトコルの番号           |
  |  16 | ヘッダ・チェックサム     | IPヘッダのエラーチェック                   |
  |  32 | 送信元IPアドレス         | 送信元の論理アドレス                       |
  |  32 | 宛先IPアドレス           | 宛先の論理アドレス                         |
  |  0~ | オプション               | なくてもよい（最大40バイト）               |
  |-----+--------------------------+--------------------------------------------|

####### Organization
######## ICANN
- The Internet Corporation for Assigned Names and Numbers
  インターネットでの資源（IPアドレス、ドメインネーム）などの管理ポリシーを策定する非営利企業。
  かつてはIANA[Internet Assigned Numbers Authority]が行っていた業務を移管して設立した。
  2015年に民営化。
######## RIP
- Regional Internet Registry / 地域インターネットレジストリ
- 管轄地域において、インターネットリソースの配分と登録を管理する組織。
######### ARIN
- American Registory for Internet Numbers
######### RIPE NCC
- RIPE Network Coordination Centre
######### APNIC
- Asia Pacific Network Information Center
  アジアを管轄するNIC
########## 配下NIR
- National Internet Registry
  主にアジアでみられるが、アジア以外ではメキシコとブラジルに存在する。
  NIRの活動はそのエリアのRIRの配下にある。
########### JPNIC
- Japan Network Information Center
  日本を管轄するNIC。
########### APJII
- インドネシア
########### CNNIC
- 中国
########### IRINN
- インド
########### KISA
- 韓国
########### TWNIC
- 台湾
########### VNNIC
- ベトナム
######### LACNIC
########## 配下NIR
########### NIC Brazil
########### NIC Mexico
######### AfriNIC
######## InterNIC
- Internet Network Information Center
  かつてインターネットのドメイン名とIPアドレスの割り当てを管理していた。
  1972年から活動し、1998/9/18にICANNに役割を引き継いだ。
######## NIC
- Network Information Center
  ICANN下の資源管理団体。管理する範囲ごとに、地域・国でそれぞれ存在。

###### IPX

###### DDP

###### ICMP
- Internet Control Message Protocol
##### Routing Protocol
- 
  ルーティングテーブルを他のルータと交換するためのプロトコル。
  近接ルータ間とネットワークの交換を行い、ルーティングテーブルを変更する。

  AS(各組織が保有・運用する小規模なネットワーク)内で用いられるIGP(Interior Gateway Protocol)と、
  異なるAS間で用いられるEGP(Exterior Gateway Protocol)とに大別される。
  IGPとEGPは一般名詞。
  
  ルータ同士が交換する情報をルーティングアップデート(routing update)という。

###### Classification
####### State
######## IGPs
######### RIP
######### CSPF
######### IGRP
######### EIGRP
######## EGPs
######### BGP
######### EGP
####### Method
######## Distance-vector protocol
- 
  Bellman-Ford(ベルマンフォード)型とも。
  距離と方向の情報を交換する。

  ルーティングテーブルにディスタンス（メトリック）とベクタ（送信ポート）が記載されているので、ディスンタスベクタ型という。
  
######### Routing loop
- 
  コンバージェンスが遅く、ルーティングアップデートがループしてしまう、という欠点がある。
  
########## Split Horizon
- 
  ルートを教えてもらったルータには、そのルートより良いルート以外は教えない。

########## Holddown Timer
- 
  変更された直後には変更を適用せず、全体に伝わるまでしばらく待ったうえで変更する。

######### Protocol
########## RIP
########## IGRP
######## Link-state protocol
- 
  
######### Protocol
########## OSPF
######## Enhanced Distance-Vector
- 

######### Protocol
########## EIGRP
###### Metric
- 
  最適ルートを決定する際の判断基準。
  これらの判断基準、ホップ数や回線のスピード、混み具合、エラー発生率などを元に計算する。
  使用するルーティングプロトコルによりメトリックは異なる。
  例えば、RIPはホップ数のみ、OSPFは回線のスピードなど。

#### Datalink
- MAC。フレームの伝送制御

##### LAN
###### IEEEの規格
####### LLC
- Logical Link Control Sub-Layer 論理リンク制御副層
  実際の機器に依存しない部分。
  エラー制御、上位サービスの指定など。
####### MAC
- Media Access Control Sub-Layer メディアアクセス制御副層
  メディアへの接続の取り決め。
  メディア・アクセス制御（共有メディアのアクセス方法。誰が送信を行うかの制御）。

###### LAN仕様
####### Ethernet(DIX)
- レイヤ1、2
  メディア：同軸・UTP・光ファイバ
  メディアアクセス制御方式：CSMA/CD
  物理トポロジ：バス・スター

######## Ethernet Frame
- 8Byte （プリアンプル）
- 6Byte 宛先MACアドレス
- 6Byte 送信先MACアドレス
- 2Byte フレームタイプ
- 46-1500Byte パケット
- 4Byte FCS

####### IEEE802.3
- レイヤ1、MAC
  メディア：同軸・UTP・光ファイバ
  メディアアクセス制御方式：CSMA/CD
  物理トポロジ：バス・スター

- 
  イーサネットとほぼ同一。
  LLC副層が少し異なるため、制御情報が異なってくるが、相互互換している。

######## Frame
- 8Byte （プリアンプル）
- 6Byte 宛先MACアドレス
- 6Byte 送信先MACアドレス
- 2Byte 長さ・タイプ
- 46-1500Byte パケット
- 4Byte FCS

######## Extention 拡張
######### IEEE802.3u
- Fast Ethernet
  1995年制定。100Mbps、下位互換。
  同軸ケーブルが規格から外れ、バス型物理トポロジが使えなくなりスターのみに。
  
######### IEEE802.3z
- Gigabit Ethernet
  光ファイバ
######### IEEE802.3ab
- Gigabit Ethernet
  ツイストペア。
######### IEEE802.3ae
- 10Gigabit Ethernet
  下位互換。

####### IEEE802.5
- レイヤ1、MAC
  メディア：同軸・UTP
  メディアアクセス制御方式：トークンパッシング
  物理トポロジ：リング・スター
  転送速度が4Mbps/16Mbps

- 
  元はIBMが1970年代に開発したトークンリング。
  
- MSAU
  MultiStation Access Unit。ハブ。
  
####### FDDI
- レイヤ1、MAC。Fiber distributed data interface
  メディア：同軸・UTP・光ファイバ
  メディアアクセス制御方式：トークンパッシング
  物理トポロジ：二重リング
  100Mbpsで、最長20KmのLANを作り出せる。

- 
  二重リングとトークン・パッシング制御方式により信頼性が高い
  光ファイバでデータ転送速度も速い。
  ただし価格も高い。

- 
  プライマリ・リングと、予備のセカンダリ・リングがある。
  プライマリとセカンダリは逆向きに信号が流れる。

- Node
  - DAS : Dual Attachment Station
    両方のリングに接続された機器のこと。
  - SAS : Single Attachment Station
    プライマリ・リングとしか接続されない。
  - Concentrator
    集線装置。複数の回線を一つにまとめる。
    複数のSASと接続される。

####### IEEE802.2
- LLC

###### MACアドレス
- 
  Nicにつけられたアドレス。ROMに書き込まれている。
  48bitを16進数で12桁にしている。
  
- OUI : Organizational Unique Identifier
  MACアドレスの先頭24bit（6桁目）まで。ベンダーコードとも。
  また、残りの24bitはベンダ割り当てコードで、ベンダが任意につけた値。

###### Media Access Control
####### CSMA/CD
- Collision Domain Multiple Access with Carrrier Avoidance
  
######## Ethernetの場合
- 
  1. 送信準備
     イーサネットフレームを作成。衝突カウンタを0にする
  2. CSMA
     キャリア信号を検知する。なければ一定時間待った後、送信開始。
  3. CD
     送信中に衝突したかどうか検出。衝突していなければ送信完了。
     衝突していた場合、フレーム送信を一時中断しJAM信号を送信。4へ。
  4. バックオフ
     衝突カウンタをプラス1．16ならばフレームを破棄し送信中止。
     16未満ならばランダムな待機後2へ。
####### CSMA/CD
- Carrier Sence Multiple Access with Collision Domain

####### Token Passing
- 
  トークン、と呼ばれる制御フレームを使う。
  1. 誰も使用していない状態を"フリートークン"といい、データを乗せる。
  2. データが乗ったトークンを"ビジートークン"という。この状態では新たにデータを乗せることはできない。
  3. データが自分宛てでなければ、何もせず送り出す。
  4. 自分宛てのデータであれば、データを受け取り受信済みを表すデータを乗せる。
  5. 受信済みビジネストークンを送信者が受け取ったら、再びフリートークンとなる。

- 
  衝突が発生せず、受け取りの確認も可能。
  ビジーとなった状態で送り元が故障した場合など、フリーに戻らない場合があるため、監視するノードが必要。
  
##### Networking Device
###### Bridge
####### Type
######## Source-route bridge
- SRB、ソースルートブリッジ。
  IEEE802.5(トークンリング)同士をつなげるブリッジ。
  他リング宛てのパケットを受け取ると、全ルート探索パケットを使って、宛先までのすべての道筋を探し出す。
  それをルーティング情報(Routing Information Field)として表を持つ。ルータのルーティングテーブルとは別物。
  
######## Transparent bride
- 
  同じアクセス制御方式のセグメントを繋ぐ。イーサネット同士、FDDI同士など。
  
######## Source-route transparent bridge
- SRTB、変換ブリッジ
  異なる方式のネットワーク同士を繋ぐ。
  
######## Encapsulation Bridge
- 
  WAN用にカプセル化するブリッジ。

####### 特徴
######## Filtering
- 
  MACアドレスで、ブリッジを通過できるかどうか判断する。
  知らないアドレスであれば通過させる。
  ブリッジはアドレステーブルを持ち、ポートと接続しているデバイスを覚えている。

######## 欠点
- 
  ハブと異なりパケットを処理するため、時間がかかる。
  また、ブロードバンドは止められない。

###### Switching hub
- Layer 2 switch
  スイッチング機能を持つ。
  マルチポートであり、ブリッジとは異なりどのポートに送るか、まで判断する。
  
  衝突が発生せず、全二重通信を実現することが可能。

####### 方式
######## Store and Forward
- 
  スイッチでバッファメモリを持っており、そこでデータのバッファリングを行い、
  送信できるタイミングになったら相手へ送信を行う。
  
######## cut through
- 
  バッファせずに、宛先を確認した時点で送る方法。
  遅延はないが、アレーフレームの送信の可能性がある。

######## fragment free
- 
  基本はcut throughだが、64バイトまでバッファしエラーチェックする。
  イーサネットで一番多いショートフレームを除去できる。

##### Protocol
###### ARP
- 実際にはレイヤ2か。

####### 動作
- データ転送時の動作
  1. ARPテーブルを参照し、宛先IPアドレスに対するMACアドレスが分かるか確認する。
  2. なければ、"ARP要求"をブロードキャスト送信する
  3. ARP要求を受け取った各ホストは、宛先IPアドレスと自分のIPアドレスを比較する。
     1. 一致しなければ無視
     2. 一致した場合、"ARP応答"を送信
  4. ARP応答を受け取ったホストは、ARPテーブルにMACアドレスを追加する。

#### Physical
##### 接続方式
###### 一般電話回線
- モデム
###### ISDN
- TA、DSU
###### LANケーブル
- NIC
###### CATV
- NIC、ケーブルモデム
###### ADSL
- NIC、ADSLモデム、スプリッタ

##### 問題
- 減衰
  信号が弱まってしまうこと
- ノイズ
  電気信号の形が崩れること
  - 原因
    - クロストーク
      隣の同線の影響
    - 熱雑音
    - EMI/RFI
      Electromagnetic interference 電磁干渉 / Radio frequency interference 無線周波干渉
  
- Collision 衝突
- 拡散（光ケーブル）

##### Networking Media
###### Cable ケーブル
####### 同軸ケーブル
- 
  中央に銅製の導体、周りにプラスティックの絶縁体、一番外側にプラスティックの皮膜。
  プラスティックの間に金でできた網状の"シールド"がある。外部からの干渉を防ぐため。

####### ツイストペアケーブル
- 
  8本の細い銅線を、2本ずつ4つの組にして、より合わせた構造。
  寄り合わせることによって、互いの磁場を消滅させ、外部からの干渉も防ぐ。キャンセレーションという。
  
######## UTP
- Unshielded Twisted-Pair Cable 非シールドツイストペア
  シールドがないため干渉に強くなく、あまり長距離まで信号が届かない。
  代わりに安価で柔らかい。

######## STP
- Shielded Twiste-Pair Cable シールドツイストペアケーブル
  あまり使われない。

####### 光ファイバケーブル
- 
  中央の反射率の高いガラスで作られた部分に信号が通る。その周りをプラスティックで覆う。
  更に周りにケブラーという防弾チョッキにも使われている繊維を、干渉保護材として配置する。
  一切の電磁的な干渉を受けず高速だが、高価。

- モード
  - シングルモード
    1本の強力なレーザー光を通すタイプ
  - マルチモード
    複数の弱い光を反射させるタイプ

###### 規格団体
####### IEEE
####### EIA/TIA
####### UL
- 
  製品の安全性を試験する団体
###### 規格
####### IEEE
- 
  |-------------+----------------+-----------------------------------------------|
  | 規格名      | ケーブルの種類 | 備考                                          |
  |-------------+----------------+-----------------------------------------------|
  | 10BASE5     | 同軸           | 別名:Thicknet                                 |
  | 10BASE2     |                | 別名:Thinnet                                  |
  |-------------+----------------+-----------------------------------------------|
  | 10BASE-T    | UTP            | 最長距離:100m                                 |
  | 100BASE-TX  |                | 最長距離:100m                                 |
  | 1000BASE-T  |                | 最長距離:100m                                 |
  |-------------+----------------+-----------------------------------------------|
  | 100BASE-FX  | 光ファイバ     | マルチモード412mまたは2km, シングルモード20km |
  | 100BASE-SX  |                | 最長距離:マルチモード550m                     |
  | 1000BASE-LX |                | 最長距離:5km(どちらのモードも)                            |
  |-------------+----------------+-----------------------------------------------|

- 規格名
  規格の数字はデータ転送量。Mbps。
  BASEはデータ伝送方式で、ベースバンド伝送を用いる、ということを表す。
  最後の数字は距離(100m、ただし2でも185m)、Tはツイストペア、他は光ファイバ。

- リピータ
  10BASE-Tなら4つ、100BASE-Tなら2つまでリピータを繋げてよい、とされている。
 
####### EIA/TIA
- 
  |----------+----------|
  | カテゴリ | 特徴     |
  |----------+----------|
  |        1 | 電話専用 |
  |        2 | 電話専用 |
  |        3 | 10Mbps   |
  |        4 | 16Mbps   |
  |        5 | 100Mbps  |
  |----------+----------|

##### Networking Device
###### Repeater
- 
  信号を増幅・整形する。

###### Hub
- 
  別名マルチポートリピータ。
  多くの機器を繋ぐ時に使用する。信号の増幅や整形も行う
  
##### Topology
###### 物理トポロジ
- 機器とメディアの配置

####### バス型
####### リング型
####### スター型
####### ツリー型
- 
####### メッシュ型
- 
  すべてのノードが相互に直接接続されている

###### 論理トポロジ
####### バス型

####### リング型

### Internet (TCP/IP) Protocol Suite
#### Application
- HTTP
- FTP
- DNS
- SMTP
- telnet
- etc
#### Transport
- TCP
- UDP
#### Internet
- IP
#### Link
- 各種
## Protocol
### TCP/IP Protocol Suite
#### Application layer
##### BGP
- 
  パスベクター(Path Vector)型プロトコルと呼ばれている。
  
##### DHCP
- 
  Bootpの上位互換。
  オプション以外はBOOTPと似たようなもの。

###### DHCPメッセージ
- 
  |----------+----------------------------------+------------------------------------------------|
  | バイト数 | 名前                             | 説明                                           |
  |----------+----------------------------------+------------------------------------------------|
  |        1 | オペレーションコード             | クライアント⇒サーバ:1, サーバ⇒クライアント:2 |
  |        1 | ハードウェアタイプ               | 10Mイーサネット:1                              |
  |        1 | ハードウェアアドレスタイプ       | 10Mイーサネット:6                              |
  |        1 | リレーエージェントhop数          | リレーエージェントの経由数                     |
  |        4 | トランザクションID               | 一連の通信で使用される識別番号                 |
  |        2 | 経過時間                         | クライアントの初期化後の時間                   |
  |        1 | フラグ                           | ブロードキャスト・フラグ                       |
  |        4 | クライアントIPアドレス           | 現在のクライアントのアドレス（再リース時）     |
  |        4 | 割り当てIPアドレス               | サーバが割り当てたアドレス                     |
  |        4 | サーバIPアドレス                 | サーバのアドレス                               |
  |        4 | DHCPリレーエージェントアドレス   | リレーエージェントのアドレス                   |
  |       16 | クライアントハードウェアアドレス | クライアントのMACアドレス                      |
  |       64 | サーバ名                         | サーバのホスト名                               |
  |      128 | ブートファイル名                 | ブーとファイルの名前                           |
  |     可変 | オプション                       | クライアントのその他設定                       |
  |----------+----------------------------------+------------------------------------------------|

####### Message Type
- 
  |----+--------------+------------------------------------------------|
  | No | Message Name | Meanings                                       |
  |----+--------------+------------------------------------------------|
  |  1 | DHCPDISCOVER | DHCPサーバを見つけるためのメッセージ           |
  |  2 | DHCPOFFER    | サーバからクライアントへ候補を伝えるメッセージ |
  |  3 | DHCPREQUEST  | 候補から決定したアドレスを伝えるメッセージ     |
  |  5 | DHCPACK      | サーバからクライアントへ取得を認めるメッセージ |
  |  6 | DHPCNAK      | サーバからクライアントへ取得エラーメッセージ   |
  |  7 | DHCPRELEASE  | クライアントからサーバへリリース要求メッセージ |
  |----+--------------+------------------------------------------------|

####### 動作
- 
  1. クライアントがサーバを発見するためDHCPDISCOVERを送信
  2. サーバは割り振る候補のアドレスをDHCPOFFERで送信
  3. クライアントは要求するIPアドレスをDHCPREQUESTで送信
  4. サーバは、要求を認めるならDHCPACK、拒否するならDHCPNAKを送信。
  5. DHCPACKならばクライアントはアドレスを設定する。DHCPNAKなら再度REQUESTを送信。

- リースの延長
  アドレスなどわかっているので、いきなりDHCPREQUESTを投げる

##### DNS

###### Header
- 
  
##### FTP
- File Transfer Protocol
  
##### HTTP
###### Specification
####### HTTP 1.1
######## RFC7230 - Message Syntax and Routing
######### Architecture
######### Message Fromat
########## Def 
- HTTP-message = start-line
                 *( header-field CRLF )
                 CRLF
                 [ message-body ]
########## Start Line
- start-line = request-line / status-line (depends on requests / responses)
########### Request Line
############ Def
- request-line = method SP request-target SP HTTP-version CRLF
########### Status Line
############ Def
- status-line = HTTP-version SP status-code SP reason-phrase CRLF
- status-code = 3DIGIT
- reason-phrase = *( HTAB / SP / VCHAR / obs-text )
########## Header Fields
########### Def
- header-field = field-name ":" OWS field-value OWS

- field-name = token
- field-value = *( field-content / obs-fold )
- field-content = field-vchar [ 1*(SP / HTAB ) field-vchar ]
- field-vchar = VCHAR / obs-text

- obs-fold = CRLF 1*( SP / HTAB )

########### Field Extensibility
########### Field Order
########### Whitespace
- OWS : optional whitespace
- RWS : required whitespace
- BWS : "bad" whitespace
########### Field Parsing
########### Field Limits
########### Field Value Components
########## MessageBody
########### Transfer-Encoding
########### Content-Length
########### Message Body Length
########## Handling Incomplete Messages
########## Message Parsing Robustness
######### Transfer Coding
######### Message Routing
######### Connection Management
######### ABNF List Extension
######### IANA Considerations
######### Security Considerations
######## RFC7231 - Semantics and Content
######### Representations
######### Request Methods
########## Method Definitions
########### GET
########### HEAD
########### POST
########### PUT
########### DELETE
########### CONNECT
########### OPTIONS
########### TRACE
######### Request Header Fields
########## Controles
########### Excpect
########### Max-Forwards
########### Cache-Control (Defined in RFC7234)
########### Host (Defined in RFC7230)
########### Pragma (Defined in RFC7234)
########### Range (Defined in RFC7233)
########### TE (Defined in RFC7230)
########## Conditionals
########### If-Match (Defined in RFC7232)
########### If-None-Match (Defined in RFC7232)
########### If-Modified-Since (Defined in RFC7232)
########### If-Unmodified-Since (Defined in RFC7232)
########### If-Range (Defined in RFC7233)
########## Content Negotiation
########### QUality Values
########### Accept
########### Accept-Charset
########### Accept-Encoding
########### Accept-Language
########## Authentication Credentials
########### Authorization (Defined in RFC7235)
########### Proxy-Authorization (Defined in RFC7235)
########## Request Context
########### Form
########### Referer
########### User-Agent
######### Response Status Codes
########## Informational 1xx
########### 100 Continue
########### 101 Switching Protocols
########## Successful 2xx
########### 200 OK
########### 201 Created
########### 202 Accepted
########### 203 Non-Authoritative Information
########### 204 No Content
########### 205 Reset Content
########### 206 Partial Content (Defined in RFC 7233)
########## Redirection 3xx
########### 300 Multiple Choices
########### 301 Moved Permanently
########### 302 Found
########### 303 See Other
########### 304 Not Modified (Defined in RFC 7232)
- document has not been modified.
########### 305 Use Proxy
########### 306 (Unused)
########### 307 Temporary Redirect
########## Client Error 4xx
########### 400 Bad Request
########### 401 Unauthorized (Defined in RFC 7235)
########### 402 Payment Required
########### 403 Forbiden
########### 404 Not Found
########### 405 Method Not Allowed
########### 406 Not Acceptable
########### 407 Proxy Authentication Required (Defined in RFC 7235)
########### 408 Request Timeout
########### 409 Conflict
########### 410 Gone
########### 411 Length Required
########### 412 Precondition Failed (Defined in RFC 7232)
########### 413 Payload Too Large
########### 414 URI Too Long
########### 415 Unsupported Media Type
########### 416 Range Not Satisfiable (Defined in RFC 7233)
########### 417 Expectation Failed
########### 426 Upgrade Required
########## Server Erorr 5xx
########### 500 Internal Server Error
########### 501 Not Implemented
########### 502 Bad Gateway
########### 503 Service Unavailable
########### 504 Gateway Timeout
########### 505 HTTP Version Not Supported
######### Response Header Fields
########## Control Data
########### Origination Date
############ Date/Time Formats
############ Date
- Requrements
  - the sender SHOULD generate its field value
  - An origin serever MUST NOT send a Data header field if it does not have a approximate time.
    An origin server MAY send a Data header field if the response is in the 1xx or 5xx class of status code.
    An origin server MUST send a Date header field in all other class.
- Def
  - Date = HTTP-date
- Exapmle
  - Date: Tue, 15 Nov 1994 08:12:31 GMT
########### Location
- Requirements
- Def
  Location = URI-reference
########### Retry-After
- Def
  Retry-After = HTTP-date / delay-seconds
########### Vary
########### Age (Defined in RFC7234)
########### Cache-Control (Defined in RFC7234)
########### Expires (Defined in RFC7234)
########### Warning (Defined in RFC7234)
########## Validator Header Fields
########### ETag (Defined in RFC7232)
########### Last-Modified (Defined in RFC7232)
########## Authentication Challenges
########### WWW-Authenticate (Defined in RFC7235)
########### Proxy-Authenticate (Defined in RFC7235)
########## Response Context
########### Allow
########### Server
- Requirements
  - An origin server MAY generate a Server field in its responses.
- Def
  Server = product *( RWS ( product / comment ))
- Example
  Server: CERN/3.0 libwww/2.17
########### Accept-Ranges (Defined in RFC7233)
######### IANA Considerations
######### Security Considerations
######## RFC7232 - Conditional Requests
######### Validation
########## Last-Modified
- Def
  Last-modiified = HTTP-date
- Example
  Last-Modified: Tue, 15 Nov 1994 12:45:26 GMT
########### Generation
- An origin server SHOULD send Last-Modified for any selected representation
########## ETag
- About
  a response provided the current entity-tag for the selected representation
- Def
  - ETag = entity-tag
  - entity-tag = [ weak ] opaque-tag
  - weak = %x57.2F;"W/",case-sensitive
  - opaque-tag = DQUOTE *etagc DQUOTE
  - etagc = %x21 / %23-7E / obs-text
########### Generation
- An origin server SHOULD send an ETag for any selected representation
######### Precondition Header Fields
########## If-Match
########## If-None-Match
########## If-Modified-Since
########## If-Unmodified-Since
########## If-Range
######### Status Code Definitions
########## 304 Not Modified
########## 412 Precondition Failed
######### Evaluation
######### Precedence
######### IANA Considerations
######### Security Considerations
######## RFC7233 - Range Requests
######### Range Units
########## Byte Ranges
########## Other Range Units
########## Accept-Ranges
- Def
  - Accept-Ranges = acceptable-ranges
  - acceptable-ranges = 1#range-unit / "none"
######### Range Requests
########## Range
########## If-Range
######### Responses to a Range Request
######### IANA Considerations
######### Security Considerations
######## RFC7234 - Caching
######### tmp
########## Cache-Control
########### 分類
############ 一般ヘッダー
############# Cache-Control
############## Directives
############### Cacheability
################ private
- Indicates that the response is intended for a singe user and must not be stored by a shared cache.
################ no-cache
- Forces caches to submit the request to the origin server for validation before releasing a cached copy.
############### Expiration
############### Revalidation and reloading
################ must-revalidate
- The cache must verify teh status of the stale resources before using it and expired ones should not be used.
############### Other
################ no-store
- The cache should not store anything about the request or server response.
############ 要求ヘッダー
############ 応答ヘッダー
############ エンティティヘッダー
######## RFC7235 - Authentication
####### RFC7239 - Forward HTTP Extension
######## Link
- [[https://tools.ietf.org/html/rfc7239][RFC7239 Forwarded HTTP Extension]]
###### Reference
####### HTTP headers
- https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers
######## Cache-Control
######## X-Content-Type-Option
######## X-XSS-Protection
###### Memo
####### X-Forwarded-For / XFF
- HTTPヘッダフィールドの一つ。
  RFCの標準的なヘッダフィールドではないが、同種の"Forwarded"の標準化作業が開始されている。
  プロキシサーバやロードバランサを経由してアクセスするクライアントの送信元IPアドレスを特定する際のデファクトスタンダード。
  多くのプロキシサーバやキャッシュ・エンジンでサポートされている。
- 2014年にRFC7239により、"Forwarded"が制定された。
######## Format
- X-Forwarded-For : client1, proxy1, proxy2
  接続元がclient1、proxy1とproxy2を経由してproxy2に到達する場合のデータ。
######## Link
- [[http://3.1415.jp/kc47fh1k/][HTTPクライアントの接続元IPアドレスを知る - 3.1415.jp]]
####### X-Forwarded-Host
####### X-Forwarded-Proto / XFP
- de-facto standard header for identifying the protocol (HTTP or HTTPS) that a client used to connect to your proxy or load balancer.
######## Syntax
- X-Forwarded-Proto: <protocol>
######## Directives
- protocol:
  http or https
####### X-Forwarded-Port
###### Link
- [[https://triple-underscore.github.io/RFC723X-ja.html][Hytertext Transfer Protocol (HTTP/1.1) - RFC 7230 〜 7235 - 日本語訳]]

- [[https://tools.ietf.org/html/rfc7230][RFC7230 HTTP/1.1 Message Syntax and Routing]]
- [[https://tools.ietf.org/html/rfc7231][RFC7231 HTTP/1.1 Semantics and Content]]
- [[https://tools.ietf.org/html/rfc7232][RFC7232 HTTP/1.1 Conditional Requests]]
- [[https://tools.ietf.org/html/rfc7233][RFC7233 HTTP/1.1 Range Requests]]
- [[https://tools.ietf.org/html/rfc7234][RFC7234 HTTP/1.1 Caching]]
- [[https://tools.ietf.org/html/rfc7235][RFC7235 HTTP/1.1 Authentication]]

- [[https://www.w3.org/Protocols/rfc2616/rfc2616.html][RFC2616 Hypertext Transfer Protocol -- HTTP/1.1]]
- https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html

##### IMAP

##### IRC

##### LDAP

##### MGCP

##### NNTP

##### NTP
- Network Time Protocol
- Application Layer, UDP123
###### SNTP
- Simple Network Time Protocol
- NTPのサブセット
- [[https://milestone-of-se.nesuke.com/l7protocol/ntp/ntp-summary/][【図解】NTPプロトコルの概要・仕組み（時間補正の計算・仕様・シーケンス） - SEの道標]]
##### POP

##### RIP

##### RPC
- Remote Procedure Call
  
##### RTP

##### SIP

##### SMTP

##### SNMP

##### SSH

##### Telnet
- 
  RFC 15, extended in RFC 854.
  ネットワーク仮想端末(Network Virtual Terminal, NVT)の仕様に基づいてデータの変換を行う。
  ポート番号は23。
  
  基本的に1文字ずつTCP/IPで送信される。
  ASCIIを使い、ヘッダを付けない。
  例） L2ヘッダ + IPヘッダ + TCPヘッダ + データ(dのみ、など)

- 

###### 標準NVT文字
- 
  ASCIIではいくつか制御文字が用意されている。telnetでは以下が利用可能。
  |------+------+------+------------------|
  | 文字 | 10進 | 16進 | 意味             |
  |------+------+------+------------------|
  | NUL  |    0 | 0x00 | ヌル文字         |
  | BEL  |    7 | 0x07 | Bell文字         |
  | BS   |    8 | 0x08 | バックスペース   |
  | HT   |    9 | 0x09 | 水平タブ         |
  | LF   |   10 | 0x0A | 改行             |
  | VT   |   11 | 0x0B | 垂直タブ         |
  | FF   |   12 | 0x0C | フォームフィード |
  | CR   |   13 | 0x0D | 復帰             |
  |------+------+------+------------------|

###### 制御機能
- 
  |--------+-------+------------------------------------------+--------------------------------|
  | コード | 制御  | 意味                                     | 役割                           |
  |--------+-------+------------------------------------------+--------------------------------|
  |   0xF2 | Synch | [Data Mark]データマーク                  | データ削除・リセット           |
  |   0xF4 | IP    | [Interrupt Process]プロセス中断          | 操作の一時中断・割り込み・停止 |
  |   0xF5 | AO    | [Abort Output]出力中止                   | 出力を抑止                     |
  |   0xF6 | AYT   | [Are You There]相手確認                  | 相手が動作しているかどうか確認 |
  |   0xF7 | EC    | [Erase Character]文字消去                | 最後の文字を消去               |
  |   0xF8 | EL    | [Erase Line]行消去                       | 最後の行を消去                 |
  |   0xFF |       | [Interpret as Command]コマンドとして解釈 | telnetエスケープシーケンス |
  |--------+-------+------------------------------------------+--------------------------------|

##### TFTP

##### TLS/SSL

##### XMPP
#### Transport layer
##### TCP
- Transmission Control Protocol
###### Header
- 
  |-----+------------------|
  | Bit | Name             |
  |-----+------------------|
  |  16 | 送信元ポート番号 |
  |  16 | 宛先番号         |
  |  32 | シーケンス番号   |
  |  32 | 確認応答番号     |
  |   4 | データオフセット |
  |   6 | 予約             |
  |   6 | 制御ビット       |
  |  16 | ウィンドウ       |
  |  16 | チェックサム     |
  |  16 | 緊急ポインタ     |
  |     | オプション       |
  |-----+------------------|

####### 制御ビット
- 
  |-----+-----+-----+-----+-----+-----|
  | URG | ACK | PSH | RST | SYN | FIN |
  |-----+-----+-----+-----+-----+-----|

- URG
  緊急に処理するデータがあることを示す
- ACK
  転送許可要求
- PSH
  受け取ったセグメントをすみやかにアプリケーションに受け渡すよう要求する。
- RST
  接続を強制的に切断する。
- SYN
  転送許可
- FIN
  終了要求を送る。
####### Sequence Number
- 
  送るデータの先頭バイトの番号。
  最初のスリーウェイハンドシェイクの際に、お互いにランダムな数値を送り合うことで初期値が決定する。
  値にデータ長を足して、確認応答番号として返答する。

####### Window Size
- 
  どれだけのサイズのバッファを持つかを連絡する。
  スリーウェイハンドシェイク時に設定する。
  そのバッファ内であれば、確認応答が来る前にデータを送ってしまう。
  確認応答が届いたら、該当部分を「枠」から外し、未送のデータを送る。
  その方法を"Sliding Window"という。

###### Three way handshake
- 接続
  1. Terminal A (Closed), Server B (LISTEN)へ要求を出す。初期状態、CLOSED-LISTEN
  2. AからBに、SYNを1にしたデータを転送する。SYN_SENT-LISTEN
  3. SYNを受け取ったBは、ACKに1、SYNに1を入れて返答する。SYN_SENT-SYN_RCV
  4. Aが通信を受け取り、A->Bの通信路が確立された。BへACK1を返す。ESTABLISHED-SYN_RCV
  5. BがACKを受けとり、B->Aの通信路も確立された。ESTABLISHED-ESTABLISHED

- 切断
  1. AからBへ切断要求を行う。ESTABLISHED-ESTABLISHED
  2. FINに1を入れて送信する。ACKは最初以外常に1。FIN_WAIT1-ESTABLISHED
  3. 受け取ったBはACKを返す。FIN_WAIT1-CLOSE_WAIT
  4. AがBから返答を受け、A->Bは切断OKとなったが、B->Aは切断要求できないため、待ち。FIN_WAIT2-CLOSE_WAIT
  5. Bが切断してもよい状態になれば、BからAへFINを送る。FIN_WAIT2-LAST_ACK
  6. Bの切断要求にAがACKで返答する。TIME_WAIT-LAST_ACK
  7. BがACKを受け取り、切断する。TIME_WAIT-CLOSED
  8. BがACKを受け取りCLOSEDにしただろう、と思われる時間を待った後に、CLOSEDとする。CLOSED-CLOSED
###### Connection Status
- CLOSED
- LISTEN
- SYN_SENT
- SYN_RCV
- ESTABLISHED
- FIN_WAIT1
  相手からのACK待ち
- FIN_WAIT2
  相手からのFIN待ち
- CLOSE_WAIT
- LAST_ACK
- TIME_WAIT
  相手にACKが届く時間の待ち。

###### Window Control
- 
  基本は、確認応答が返ってこなかったら再送する。
  同じ確認応答が3回来た場合も再送する。

- 
  TCPでは必ず番号順に処理を行うので、途中でパケットが届かなかった場合も、
  バッファ内で並び替えを行い番号順に処理を行う。

- 
  Window sizeは16bit, 64KByteが最大だが、ウィンドウスケールオプションを使うことで最大1GBまで拡張可能。

###### Congestion Control
- 輻輳制御
  
####### Slow-start Algorithm
- 
  最初は1つ送り、問題なく返答がきたら2つ、4つ、8つ、、、と送るセグメントの数を倍々に増やしていく。
  ある閾値をまでいったら、その後は1つずつ増やす。16、17、18、、、など。
  確認応答が返ってこなかった時点で、一旦送る数を減らし、またそこから徐々に増やしていく。
  基本は1まで送信数を落とすが、輻輳が発生する度に半分に落とす、という応用パターンもある。

  ウィンドウサイズまで増えれば、ウィンドウ制御により打ち止めとなる。

###### MMS
- Maximum Segment Size
  データが長い場合は分割して送信するが、そのサイズ。
  イーサネットでは約1460となる。
  スリーウェイハンドシェイク時（の最初の2回）にサイズが決定される。
###### RTT
- Round Trip Time、往復遅延時間
  
##### UDP
- User Datagram Protocol
  制御を行わないが、スループットの低下が起こらない。
  コネクションレス。

###### Header
- 
  |-----+------------------|
  | Bit | Name             |
  |-----+------------------|
  |  16 | 送信元ポート番号 |
  |  16 | 宛先ポート番号   |
  |  16 | セグメントサイズ |
  |  16 | チェックサム     |
  |-----+------------------|
  
##### DCCP

##### SCTP

##### RSVP
#### Internet layer
##### IP
###### IPv4
####### IP Address
######## Class
- 
  |-------+--------------+---------+------+---------------+-----------------+---------------|
  | class | Leading bits | network | rest | Start address |     End address |   Subnet Mask |
  |-------+--------------+---------+------+---------------+-----------------+---------------|
  | A     |            0 |       8 |   24 |       0.0.0.0 | 127.255.255.255 |     255.0.0.0 |
  | B     |           10 |      16 |   16 |     128.0.0.0 | 191.255.255.255 |   255.255.0.0 |
  | C     |          110 |      24 |    8 |     192.0.0.0 | 223.255.255.255 | 255.255.255.0 |
  | D     |         1110 |         |      |     224.0.0.0 | 239.255.255.255 |               |
  | E     |         1111 |         |      |     240.0.0.0 | 255.255.255.255 |               |
  |-------+--------------+---------+------+---------------+-----------------+---------------|
######## Subnet Mask
- 
  ネットワーク番号・サブネット番号のビットをすべて1、ホスト番号を0としたもの。

######## CIDR
- Classless Inter-Domain Routing
  クラスに関係なくIPアドレスを割り当てる方法。
  
######## 予約済みアドレス
######### Private Address
- 
  |--------------+----------------+-------------+-----------------+------------------|
  |              | Class          |       Start |             End | No. of addresses |
  |--------------+----------------+-------------+-----------------+------------------|
  | 24-bit block | Class A        |    10.0.0.0 |  10.255.255.255 | 16,777,216       |
  | 20-bit block | Class B × 16  |  172.16.0.0 |  172.31.255.255 | 1,048,576        |
  | 16-bit block | Class C × 256 | 192.168.0.0 | 192.168.255.255 | 65,536           |
  |--------------+----------------+-------------+-----------------+------------------|

######### Network Address
- 
  ホスト部がすべて0のもの。
  ネットワークそのものを表す。

######### Broadcast Address
- 
  ホスト部がすべて1のもの。
  ネットワーク内の全員が受け取るためのアドレス。

######### Loopback Address
- 
  自分自身宛てのアドレス。127.0.0.1が主に使われる。

######## NAT
- Network Address Translator
  ネットワークアドレス変換の一つで、プライベートIPアドレスをグローバルIPアドレスに変換すること。

####### IP fragmentation
######## MTU
- Maximum Transmission Unit
  1回の転送（1フレーム）で送信できるデータの最大値を示す伝送単位のこと。
  

######### Path MTU Discovery 経路MTU探索
- 
  https://en.wikipedia.org/wiki/Path_MTU_Discovery

####### IP Packet
- 20～60byte : IPヘッダ
- 0～65,515byte : セグメントデータ

######## IP Header
- 
  |-----+--------------------------+--------------------------------------------|
  | Bit | Name                     |                                            |
  |-----+--------------------------+--------------------------------------------|
  |   4 | バージョン               | IPのバージョン                             |
  |   4 | ヘッダ長                 | IPヘッダの長さ                             |
  |   5 | サービスタイプ           | 上位プロトコルによって割り当てられた重要度 |
  |  16 | データ長                 | IPヘッダとセグメントデータを合わせた長さ   |
  |  16 | ID                       | 大きいデータを分割した際につける識別番号   |
  |   3 | フラグ                   | 分割する際に使用するフラグ                 |
  |  13 | フラグメント・オフセット | 分割を繋ぎ合わせるときに使う               |
  |   8 | TTL / Time To live       | パケットの生存時間                         |
  |   8 | プロトコル               | 使用している上位プロトコルの番号           |
  |  16 | ヘッダ・チェックサム     | IPヘッダのエラーチェック                   |
  |  32 | 送信元IPアドレス         | 送信元の論理アドレス                       |
  |  32 | 宛先IPアドレス           | 宛先の論理アドレス                         |
  |  0~ | オプション               | なくてもよい（最大40バイト）               |
  |-----+--------------------------+--------------------------------------------|

###### IPv6
###### IP Protocol Number プロトコル番号
- 
  IPで通信する際に、上位層のプロトコルがなんであるかを識別するための番号。
  IPパケットのヘッダに8ビットの値として記載される。
  [[http://www.iana.org/assignments/protocol-numbers/protocol-numbers.xhtml][Protocol Numbers]]
  [[https://ja.wikipedia.org/wiki/%E3%83%97%E3%83%AD%E3%83%88%E3%82%B3%E3%83%AB%E7%95%AA%E5%8F%B7%E4%B8%80%E8%A6%A7][プロトコル番号一覧 - Wikipedia]]

####### List
- 
  |---------+------------+-----------|
  | Decimal | Keyword    | Reference |
  |---------+------------+-----------|
  |       0 | HOPOPT     |           |
  |       1 | ICMP       | [[http://tools.ietf.org/html/rfc792][RFC792]]    |
  |       2 | IGMP       |           |
  |       4 | IP         |           |
  |       6 | TCP        |           |
  |       7 | CBT        |           |
  |       8 | EGP        |           |
  |       9 | IGP        |           |
  |      17 | UDP        |           |
  |      41 | IPv6       |           |
  |      43 | IPv6-Route |           |
  |      44 | IPv6-Frag  |           |
  |      45 | IDRP       |           |
  |      46 | RSVP       |           |
  |      47 | GRE        |           |
  |      50 | ESP        |           |
  |      51 | AH         |           |
  |      55 | MOBILE     |           |
  |      58 | IPv6-ICMP  |           |
  |      59 | IPv6-NoNxt |           |
  |      60 | IPv6-Opts  |           |
  |      88 | EIGRP      |           |
  |      89 | OSPF       |           |
  |      94 | IPIP       |           |
  |     103 | PIM        |           |
  |     112 | VRRP       | [[https://tools.ietf.org/html/rfc5798][RFC5798]]   |
  |     113 | PGM        |           |
  |     115 | L2TP       |           |
  |---------+------------+-----------|

##### ICMP
- Internet Control Message Protocol
  [[https://tools.ietf.org/html/rfc792][RFC792 Internet Control Message Protocol]]a
  IPを利用するネットワークで用いられるプロトコルの一つで、IP通信の制御や通信状態の調査などを行うためのもの。
  TCP、UDPなどと同様にインターネット・プロトコル上位のプロトコルだが、
  IPと同じネットワーク層のプロトコルであるように特別の処理をされる。
  
  pingやtracerouteなどがICMPを利用している。
  大きく分けて、調査のためのQueryメッセージと、エラー通知のためのErrorのメッセージがある。

###### ICMP Packet
- 
  本来セグメントが入る部分に、ICMPメッセージが入って送信される。
  EthernetFrame | IP Header | ICMP Message

###### Structure
- 
  |------+--------+--------+--------------+------------+--------|
  | Byte |      1 |      1 |            2 |          4 |     64 |
  |------+--------+--------+--------------+------------+--------|
  | Name | タイプ | コード | チェックサム | オプション | データ |
  |------+--------+--------+--------------+------------+--------|

###### Message Type
- 
  |--------------+-------------------------+-------|
  | タイプコード | 内容                    | 種類  |
  |--------------+-------------------------+-------|
  |            0 | Echo Reply              | Query |
  |            3 | Destination Unreachable | Error |
  |            5 | Redirect                | Error |
  |            8 | Echo Request            | Query |
  |           11 | Time Exceeded           | Error |
  |--------------+-------------------------+-------|
  |            4 | Source Quench           | Error |
  |           12 | Parameter Problem       | Error |
  |           13 | Timestamp Request       | Query |
  |           14 | Timestamp Reply         | Query |
  |           15 | Information Request     | Query |
  |           16 | Information Reply       | Query |
  |--------------+-------------------------+-------|

####### 3 : Unreachable Messages
- 
  |---------+----------------------------------------------------------------------+--------------------------------------------------------------------------|
  | Code    | ICMP到達不能メッセージ                                               | 内容                                                                     |
  |---------+----------------------------------------------------------------------+--------------------------------------------------------------------------|
  | Code 0  | Network Unreachable                                                  | 指定されたネットワークに到達できない。ルータが経路情報を保持していない   |
  | Code 1  | Host Unreachable                                                     | ホストに到達できない。ホストがネットワークに接続されていない             |
  | Code 2  | Protocol unreachable                                                 | プロトコルに到達できない。指定されたプロトコルが利用できない。           |
  | Code 3  | Port unreachable                                                     | ホストのポート(SSH/HTTPなど)に到達できない。待ち受け状態になっていない。 |
  | Code 4  | Fragmentation required, and DF flag set                              | パケットの分割したいが、不可となっている。                               |
  | Code 5  | Source Route Failed                                                  | ソースルートが不明                                                       |
  | Code 6  | Destination network unknown                                          | 指定されたネットワークが発見できない。到達する経路が発見できない。       |
  | Code 7  | Destination host unknow                                              | 指定されたホストが発見できない。ホストに到達する経路が発見できない       |
  | Code 8  | Source Host Isolated                                                 |                                                                          |
  | Code 9  | Communication with Destnation Network is Administratively Prohibited |                                                                          |
  | Code 10 | Communication with Destination Host is Administratively Prohibited   |                                                                          |
  | Code 11 | Destination Network Unreachable for Type of Service                  |                                                                          |
  | Code 12 | Destination Host Unreachable for Type of Service                     |                                                                          |
  | Code 13 | Communication administratively prohivited by filtering               | ファイヤーウォールやウィルス対策ソフトのため到達できない                 |
  |---------+----------------------------------------------------------------------+--------------------------------------------------------------------------|

####### 5 : Redirect
- 
  ホストにルート変更の情報が伝わらないため、最適ルートの情報をホストへ伝える。
  オプションに新しい最適ルータのIPアドレスを入れてホストへ送り返す。

- 
  |------+--------------------------------------------------------+--------------------------------|
  | code | 説明                                                   | 意味                           |
  |------+--------------------------------------------------------+--------------------------------|
  |    0 | Redirect datagrams for the Network                     | 対象ネットワークへのルート変更 |
  |    1 | Redirect datagrams for the Host                        | 対象ホストのみへのルート変更   |
  |    2 | Redirect datagrams for the Type of Service and Network | ネットワークのルート変更       |
  |    3 | Redirect datagrams for the Type of Service and Host    | ホストへのルート変更           |
  |------+--------------------------------------------------------+--------------------------------|

##### ICMPv6
- Internet Control Message Protocol for IPv6
  IPv6で用いられるICMPプロトコル。ただしv4から各種定義しなおされている新しいプロトコル。

###### Path MTU Discovery
- パスMTU探索
  IPv6のパケット断片化は送信元のみでルータでは行われないので、
  送信元が配送される全経路で通過できるパケットのサイズ(パスMTU)を知らなければならない。
  これを行うのがパスMTU探索。RFC1981。
  
  最初はインターフェースのMTU値などできるだけ大きな値を用いて送信され、
  途中のルータでMTU値がパケットより小さければ、送信元へ「パケット過大(Packet too big)」エラーを返す。
  この時送信可能なMTU値も返されるので、再度送信元はそのサイズに合わせて再送信。
  これを繰り返すことでパスMTUを知る。

##### NDP

##### IGMP

##### IPsec
##### VRRP
- インターネット上でのルーターの冗長化をサポートするプロトコル。
  同じLANにつながる数台のルーターを仮想的に1台の仮想的ルーターとして扱えるようにする。
  仮想ルーターに利用するIPアドレスは、マスタールーターと同じにするか別とするか選べる。異常時にtelnet等での接続ができるよう、別とした方が利便性が増す。
- 1995/4にRFC2338で定義された。
  現在の最新プロトコルは2010/3のRFC5798。
###### Link
- [[https://tools.ietf.org/html/rfc5798][RFC 5798 - Virtual Router Redundancy Protocol (VRRP) Version 3 for IPv4 and IPv6]]
#### Link layer
##### ARP
- Address Resolution Protocol
  イーサネット環境で、IPアドレスから対応するMACアドレスを動的に得るためのプロトコル。
  IPv6ではARPでなく、ICMPv6の「近接探索プロトコル」を用いる。
  RFC826で定義され、その後RFC5227, RFC5494でエンハンスが行われている。
  
  宛先IPアドレスを取得して、その情報を元に宛先MACアドレスを知るためにARPテーブルを参照する。

###### ARPテーブル
- 
  IPアドレスとMACアドレスの情報。
  winのcmdでは"arp -a"とすると確認可能。
  この中にデータが存在しない場合に、ARP要求をしてデータを取得する。
  
####### ARP entry
- static
  手動で入力したもの。
- dynamic
  ARPによって取得したIPアドレスとMACアドレス

###### 動作
- 
  

###### ARPパケット
- 
  上位のプロトコルを使わず、ARPパケットをethernet Frameで包むだけ。

####### Fromat
- 
  |------+----------------------+---------------------|
  | byte | name                 | meaning             |
  |------+----------------------+---------------------|
  |    4 | アドレスタイプ       | アドレスの方式      |
  |    2 | アドレス帳           | アドレスの長さ      |
  |    2 | オペレーションコード | 要求か応答か        |
  |    6 | 送信元MACアドレス    | 送信元のMACアドレス |
  |    4 | 送信元IPアドレス     | 送信元のIPアドレス  |
  |    6 | 送信先MACアドレス    | 送信先のMACアドレス |
  |    4 | 送信先IPアドレス     | 送信先のIPアドレス  |
  |------+----------------------+---------------------|
  
##### RARP
- Reverse Address Resolution Protocol
  MACアドレスからIPアドレスを取得するためのプロトコル。
  近年では同機能でより高機能なDHCPなどにより代替されることが多い。

##### BOOTP

##### OSPF
##### SPB
##### L2TP
##### PPP
##### MAC
- Media Access Control

###### Ethernet
###### IEEE 802.11
###### DSL
###### ISDN
### IPX/SPX
#### Network
##### IPX
- アドレス
  ネットワークID+MACアドレス(32bit+48bit)
  ex) 4d.0060.3e86e220

### AppleTalk
#### Session
##### AppleTalk Session Protocol
#### Network
##### DDP
- アドレス
  ネットワーク番号+ノード番号(15bit+8bit)
  
### SNA

### UMITS
### Miscellaneous
#### Application
#### Presentation
#### Session
##### NFS
- Network File System
##### NetBIOS
#### Transport
#### Network
##### NetBIOS Fraems protocol, NBF
- 
#### Datalink
#### Physical
### Rooting
#### RIP
- Routing Information Protocol
##### RIPv1
- 
  ルーティングテーブルを30秒に1回交換する。
  6回アップデートを受け取らなかった場合、ルータが故障しているとみなし、そのルータを使うルートを消す。
  
  最大で25ルート分を交換する。
  メトリックにはホップ数を使う。

###### Routing Update
- 
  |------+----------------------------|
  | Byte | Content                    |
  |------+----------------------------|
  |    1 | コマンド                   |
  |    1 | バージョン                 |
  |    2 | ZERO                       |
  |------+----------------------------|
  |    2 | アドレス識別子             |
  |    2 | ZERO                       |
  |    4 | 宛先ネットワークIPアドレス |
  |    4 | ZERO                       |
  |    4 | ZERO                       |
  |    4 | メトリックス               |
  |------+----------------------------|
  
##### RIPv2
### Unclassified
#### Remote Desktop Protocol, RDP
- TCPポート3389およびUDPポート3389を医療する。
##### Link
- [[https://msdn.microsoft.com/en-us/library/cc240445.aspx][(MS-RDPBCGR): Remote Desktop Protocol: Basic Connectivity and Graphics Remoting - Developer Network]]
- [[https://wiki.wireshark.org/RDP][Remote Desktop Protocol (RDP) - WIRESHARK]]
- [[https://msdn.microsoft.com/en-us/library/bb892075(v=vs.85).aspx][Remote Desktop Services - Developer Network]]
#### SOCKS
- ネットワーク・ファイアウォール越えやアクセス制御等を目的として、
  クライアントサーバ型のプロトコルが透過的に使用できるよう設計されたプロキシのプロトコル、及びシステム。
  SOCKetSの略。
### Binary protocol
- バイナリデータの通信プロトコル
#### XMODEM
##### 種類
###### XMODEM/SUM
- 128バイト単位でデータを転送。8ビットのチェックサムを使用する
###### XMODEM/CRCm
- 128バイト単位でデータを転送。16ビットのCRCを使用する
###### XMODEM/1k
- 1024バイト単位でデータを転送。16ビットのCRCを使用する
###### Flying-XMODEM
- ACKをデータブロックを受け取り終わる前に先に送ることで転送速度の向上を測る。
  どのプロトコルとも併用できる。
  規約違反で、エラーがあっても回復できない。
##### 手順
- SOH, STX, EOT, ACK, NAK, CANの6つのコントロールノードと文字'C'(43h)を使用して通信制御を行う。
#### YMODEM
#### YMODEM-g
#### ZMODEM
### Link
- https://en.wikipedia.org/wiki/OSI_model
## Command
### Posix
#### arp
#### ifconfig
- 
#### ip
#### netstat
  
#### ping
- 接続確認
#### route
#### rsync
#### scp
#### sftp
#### ssh
#### tcpdump
- ネットワークのトラフィックをダンプ
#### traceroute
- ホストまでの経路を表示
#### Download
##### curl
- transfer a URL
##### wget
- non-interactive network downloader
#### DNS lookup
##### nslookup
- 対話的にDNSサーバへ問合せ
##### host
##### dig
### Windows
#### route
##### print
- 
  routing tableを表示させる。

#### ping
- 
  ICMPのecho requestとecho replyを使う。
  
- 確認手順
  1. ping 127.0.0.1
  2. ping 自分のNICのIPアドレス
  3. ping 同じハブ・スイッチに接続されているデバイスのIPアドレス
  4. ping 違うハブ・スイッチに接続されているデバイスのIPアドレス
  5. ping デフォルトゲートウェイのIPアドレス
  6. ping DNSサーバのIPアドレス
  7. ping 目的のIPアドレス

#### tracert
- tracert IPアドレス
  宛先までのルートを教えてくれるコマンド。

#### pathping
- pathping 宛先IPアドレス
  途中のルータ間での情報も収集できる。

#### netstat
- 
  プロトコルの統計と現在のTCP/IPネットワーク接続を表示する。
  0.0.0.0:XXはすべてのインターフェースに関するXXポート、の意。
  自分がサーバ側か接続側かは、ローカルのポートがwell-knownか否かで判断する。
  
- -a
  すべての接続とリッスンポートを表示する
- -e
  ethernetの統計情報。
- -n
  アドレスとポート番号を数値形式で表示する。
- -r
  ルーティングテーブル
- -s
  プロトコルごとの統計を表示する。

#### telnet
- 
  サーバへの接続。平文でユーザIDとパスワードが送信される。

### Link
- [[http://itpro.nikkeibp.co.jp/article/COLUMN/20060224/230618/?rt=nocnt][管理者必見！ネットワーク・コマンド集]]
- [[http://enakai00.hatenablog.com/entry/20140712/1405139841][RHEL7/CentOS7でipコマンドをマスター - めもめも]]  
- [[http://www.21linux.com/archives/180network/][ネットワーク関係のカテゴリ - Linux コマンド百科事典]]
- [[http://webkaru.net/linux/cat/command/network/][ネットワーク(Linuxコマンド集) - Linux入門]]

## History
### Internet
- https://en.wikipedia.org/wiki/History_of_the_Internet

## Nodes
- [[file:Network_Nodes.org][Network_Nodes.org]]
## Wireless
### Security Protocol
#### WEP
- Wired Equivalent Privacy
#### WPA
- Wi-Fi Protected Access
## Error Detection and Correction
### Error detection schemes
#### Repetition codes
#### Parity bits
#### Checksums
#### CRC
- Cyclic redundancy check、巡回冗長検査。
  あるビット列で割った余りを比較することで、データの誤りを検出する。
  [[http://funini.com/kei/math/crc_basic.shtml][CRCの計算方法]]
  [[http://ja.wikipedia.org/wiki/%E5%B7%A1%E5%9B%9E%E5%86%97%E9%95%B7%E6%A4%9C%E6%9F%BB][ウィキペディア 巡回冗長検査]]

### Error correction
### Application
## Organization
### IETF
- The Internet Enineering Task Force, インターネット技術特別調査委員会

#### RFC
- Requests For Comments
  
## Term
### AS
- Autonomous System、自立システム。
  経路ドメイン、経路制御ドメインとも。
  
  各組織が保有・運用する自立したネットワーク。
  
  単一の経路制御ポリシーを共有するネットワークで、
  個々のISPや企業などが保有するネットワークがこれにあたる。
  
  ASは各国のNIC（日本ではJPNIC）などが発行するAS番号によって識別される。

#### AS Number
- 
  ICANNが管理している、ASごとの番号。16bit。
  日本の場合はJPNIC。
  64512-65534までは、IPアドレス同様プライベートで使用可能。

### CRC
- Cyclic Redundancy Check

### EGP
- 
  Exterior Gateway Protocol
  AS間の経路制御に使われるプロトコル。
  BGPなど。
  
  もともとネットワーク生成期の具体的なプロトコルの一つでもあるが、
  上記のようにBGPなどの総称としても用いられるため、文脈により判断が必要。

### FCS
- Frame Check Sequence

### IGP
- 
  Interior Gateway Protocol
  AS内の経路制御に使われるプロトコル。
  RIPやOSPFなど。

### ISP
- 
  Internet Service Provider

### LLC
- Logical Link Control

### MPLS
- Multi-Protocol Label Switching
- LSP: Label Switched Pathと呼ばれるパスを構成し、通信を行う。
### NIC
- 
  Network Information Center

#### mode
##### ユニキャスト
- 
  宛先アドレスが自分のアドレスを指している場合に取り込むもの。

##### ブロードキャスト
- 
  ブロードキャスト・パケットを受信するフィルタ。
  ハードウェア・ブロードキャスト・アドレスは「FF-FF-FF-FF-FF-FF」。

##### マルチキャスト
- 
  あらかじめ登録されたグループ・アドレスあてのパケットを受信するフィルタ。
  どのパケットを受信するかは、NIC内のマルチキャスト・リストに登録されている。
  TCP/IPでは「01-00-5E-xx-xx-xx(xx-xx-xxはグループ番号)」にすればマルチキャストされる。

##### オール・マルチキャスト
- 
  グループアドレスに関係なく、すべてのマルチキャスト・パケットを受信するフィルタ。
  実際には、MACアドレスの中のグループ・ビットがオンになっているすべてのパケットを受信する。
  グループ・ビットは、MACアドレス1バイト目の最下位ビット。

  マルチキャストとオール・マルチキャストの検出方法が違うが、
  

##### Promiscous mode
- 
  NICの持つ動作モードの一つ。
  自分宛て以外のデータパケットも信号を取り込んで処理をする。
  
  標準では自分のMACアドレス宛以外へ送信されたパケットは、
  ブロードキャストなど一部例外を除き上位に通知しない状態となっている。
### OUI
- Organiation Unique Identifier

### PDU
- Protocol Data Unit
  プロトコルが扱うデータの単位。

#### Message
- アプリケーション層

#### Segment
- TCP、トランスポート層

#### Datagram データグラム
- UDP、トランスポート層

#### Packet パケット
- ネットワーク層（OSI参照モデル）
- IP、インターネット層(TCP/IP）

#### Frame フレーム
- Ethernet、Wi-Fi、PPP、HDLC、データリンク層

#### Cell セル
- ATM、データリンク層

#### Bit
- 物理層

### PoE
- Power over Ethernet

### SNAP
- SubNetwork Access Protocol

### VPN
- Virtual Private Network
#### 種類
- インターネットVPN、IP-VPNの二種類。
##### インターネットVPN
###### IPsec-VPN
###### SSL-VPN
##### IP-VPN
###### MPLS-VPN
### Broadcast Storm
- 
  ブロードキャストが多発しすぎて、ネットワーク全体が通信不能になってしまう状態。

#### Type
##### サイト間VPN
##### リモート
## Link
- [[https://en.wikipedia.org/wiki/Computer_network][Computer network Wikipedia]]
- [[http://blog.amedama.jp/entry/2017/03/29/080000][Python: ソケットプログラミングのアーキテクチャパターン - CUBE SUGAR CONTAINER]]
## Glossary
### Remote IP Adress
- Webサーバが受け取るアドレス。
  Apacheの場合、REMOTE_ADDR, %{REMOTE_ADDR}(mod_rewriteの場合)など。
  ロードバランサやプロキシを経由する場合、そのIPアドレスとなってしまうので、
  元のIPが欲しい場合はXFFなどを利用する。
  
  RFC3875(CGI)で規定されている。
### Inbound, Outbound
- Inbound
  外から中へ入ってくる通信
- Outbound
  中から外へ出す通信
### Router
#### CE Router
- Customer Edge Router
#### PE Router
- Provider Edge Router
## Reverse Lookup
### Global IPを調べる
- 基本的には外部サービスを利用
- ifconfig.ioを利用
  https://ifconfig.io/
  curl ifconfig.io
- ieserver.net
  http://www.ieserver.net/
  wget -q -O - ipcheck.ieserver.net
## Memo
### Free Wi-fi
### プロミスキャスモード端末の特定
- 
  [[http://sonickun.hatenablog.com/entry/2014/07/28/223049][ARPを利用してプロミスキャスモードの盗聴ホストを特定してみた - sonickun.log]]

### アドレス
- 物理アドレス
  レイヤ２。メディアに直接接続されている誰に届けるかを識別する
- 論理アドレス
  レイヤ３。どのネットワークの誰に届けるかを識別する。
### Segment
- 
  衝突ドメインのようなネットワークの区切りのこと。
  ルータ、ブリッジ、スイッチによって分断されたネットワークの区切り。
#### Collision Domain
- 衝突ドメイン
  ブリッジ・スイッチが区分けする。
#### Broadcast Domain
- ブロードキャストドメイン
  ルータが区分けする。

### データの送信
#### アドレス取得の流れ
- 
  1. 送信元MACアドレスは、NICを取り付けた時点でわかる（割り振られている）
  2. 送信元IPアドレスは、手動で割り付けるか、DHCPで割り振られる。
  3. 宛先IPアドレスは、宛先のホスト名（もしくはNetBIOS名など）が分かれば、DNS（もしくはNBT）で取得できる。
  4. 宛先MACアドレスは、宛先IPアドレスがわかればARPによりMACアドレスが分かる。

#### 他ネットワークへの送信
- 
  自分のネットワークにいない場合、デフォルトゲートウェイに送信を行う。

  デフォルトゲートウェイのIPアドレスは、DHCPサーバに教えてもらうか、手動で設定する。
  ARPしてデフォルトゲートウェイのMACアドレスを取得した上で、データを送る。
  
### Dynamic Port Forward ダイナミックポートフォワード
- 固定IPでWebアクセスしたい場合に、踏み台サーバにダイナミックポートフォワードする。
  プロキシ設定を行うことで、その踏み台サーバのアドレスでブラウザアクセス等ができるようになる。
  SOCKSプロトコル、というものに対応していれば利用できる模様。
  [[http://vogel.at.webry.info/201505/article_6.html][ダイナミックポートフォワーディングは便利 - パソコン鳥のブログ]]
### キャリアの利用するIPアドレス
#### DoCoMo
- https://www.nttdocomo.co.jp/service/developer/smart_phone/spmode/index.html
#### SoftBank
- https://www.support.softbankmobile.co.jp/partner/home_tech1/
### サブネット分割した場合の値
- サブネットの表現は、256に不足している数が最小単位。
  例：224なら32、248なら16。
  最小単位で割り切ったあまりがネットワークのアドレス部。
#### 1 - 128
- 0:0
- 1:128
#### 2 - 192
- 00:0
- 01:64
- 10:128
- 11:192
#### 3 - 224
- 000:0
- 001:32
- 010:64
- 011:96
- 100:128
- 101:160
- 110:192
- 111:224
#### 4 - 240
- 0000:0
- 0001:16
- 0010:32
- 0011:48
- 0100:64
- 0101:80
- 0110:96
- 0111:112
- 1000:128
- 1001:144
- 1010:160
- 1011:176
- 1100:192
- 1101:224
- 1111:240
#### 5 - 248
#### 6 - 252
#### 7 - 254

### APIPA
- APIPA / Automatic Private IP Adressing
- 静的なアドレスの割当がなく、またDHCPアドレスの割当が失敗した場合や、そういった機構がない場合に利用されるアドレス。
- IPv4では169.254.0.0/16に定義されている。
    

## Tools
### GNS3
- ネットワーク機器をエミュレートできるアプリケーション。
