# Security
## Threats
### Vulnerability
#### OS Command Injection

#### XSS / Cross-Site Scripting / クロスサイトスクリプティング
##### Measure
- 利用者
  - 会員登録したサイトを閲覧中は他のサイトを見に行かず、終了後は一旦ブラウザを終了させることでcookieを盗まれないようにする。
- 作成者
  - ユーザIDやユーザ認証に関わる情報は極力cookieには含めないようにし、セッションIDはセッションごとにランダムな値を生成することで、推測できないようにする。
##### Link
- https://www.techmatrix.co.jp/product/appscan/column/check5.html
#### XST / Cross-Site Tracing
##### Link
- [[https://blog.tokumaru.org/2013/01/TRACE-method-is-not-so-dangerous-in-fact.html][実はそんなに怖くないTRACEメソッド - 徳丸浩の日記]]
#### SQL Injection / SQLインジェクション
- 条件に"'1' = '1'"などと入力して任意の結果を得る方法。
- https://www.techmatrix.co.jp/product/appscan/column/check6.html
#### Code Injection

#### Baffer Error

#### Certification・Password Management

#### CSRF / Cross-Site Request Forjery / クロスサイトリクエストフォージェリ
- 概要
  任意のHTTPリクエストを送信させられてしまう

- 手順
  1. 攻撃者が、攻撃用のWebページを作成しWWW上に公開する。
  2. 第三者が、攻撃用のWebページにアクセスする。
  3. 第三者は、攻撃者が用意した任意のHTTPリクエストを送信させられる。
  4. 送信させられたHTTPリクエストによって、攻撃者の意図した操作が行われる。

##### Measure
- 利用者
  ログアウトをしてセッションを破棄しておけば、認証段階の手続きが拒否されるので被害が抑えられる。
- Webサイト作成者側
  - FormをGetする際に、暗号論的擬似乱数値(nonce)を、Cookie値またはセッション、
    およびformのhidden値として発行し、HTTP POST時にその両者の値の同一性を検証する方法がある。
  - HTTP Refererを取得し照合することで、外部からの不正POSTを判別する。
    第三者サイトから、Refererを偽造したPOSTを送信することは不可能。

##### Link
- https://www.techmatrix.co.jp/product/appscan/column/check8.html
#### Session Fixation
##### 概要
- ログイン前に使用されていたセッションIDが、ログイン後も同じ値で使用されている脆弱性。
##### 
- 手順
  1. 攻撃者があらかじめWebサイトからCookieとして有効なセッションIDを取得する。
  2. その後ユーザが攻撃者の仕掛けた悪意のWebサイトにアクセスした際、
     事前に手に入れたセッションIDをそのユーザのブラウザに強制的にセットする。
  3. その後第三者がWebサイトにアクセスすることで、セッションIDとユーザ情報が紐付けられ、
     攻撃者がユーザ情報を紐付いたセッションIDを自由に活用できてしまう。
  
- 原因
  Webサーバが発行し、アクセスするたびに値をブラウザが送り出すのが原則だが、
  ブラウザが送ってきたセッションIDが、自分の発行していないにもかかわらず、
  それを有効なセッションIDとして許可してしまうサーバがある場合、問題となる。

##### Link
- https://www.techmatrix.co.jp/product/appscan/column/check8.html
#### ARP spoofing
- ARPスプーフィング (ARP cache poisoning, ARP poison routing)
  ARPプロトコルの応答を偽装することにより、LAN上で通信機器のなりすましを行う技法。

#### IP spoofing

#### DNS spoofing
- DNS偽装, DNS cache poisoning
#### Buffer overflow, Buffer overrun
- 
#### Directory Traversal / ディレクトリトラバーサル
- 相対パスを用いて、任意のパスの情報を取得できる脆弱性
- https://www.techmatrix.co.jp/product/appscan/column/check7.html
#### Forceful Browsing / 強制ブラウジング
- 許可されていないはずのページにアクセスできてしまう
- https://f5.com/jp/education/glossary/glossary150-21634
- https://www.techmatrix.co.jp/product/appscan/column/check7.html
### Malware
#### Viruses
- 他のファイルに感染することで増殖するもの
#### Worms
- 独立したプログラムで、自身を複製して他のシステムへ拡張する。
##### 例
###### Code Red
- 2001/7/13
###### SQL Slammer
- 2003/1/25
  https://ja.wikipedia.org/wiki/SQL_Slammer
#### Trojan horses
- 独立しているが、ワームと違い自己増殖機能がない。
#### Ransomware
#### Rootkits
- designed to remotely access or control a computer without being detected by users or security programs.
#### Spyware
#### Backdoors
#### Keylogger
#### Spam
#### Evasion

## Attacks
### DoS
- Denial of Service
#### HashDos
- https://blog.tokumaru.org/2011/12/webdoshashdos.html
- https://blog.tokumaru.org/2012/01/cookie-hashdos-attack-defense.html
- http://bakera.jp/ebi/topic/4680
- https://employment.en-japan.com/engineerhub/entry/2018/01/11/110000
### DDoS
- Distributed Denial of Service
### Flood
#### SYN Flood
#### UDP Flood
#### Ping Flood
#### Smurf
- 
  送信元IPアドレスを偽装して、相手ネットワークのブロードキャストアドレス宛に大量のエコーリクエストを送りつける。
#### fraggle
#### Connection Flood
#### Reload

### Scan
#### Address scan
- 会社のドメイン名やwhoisデータベースで得られるイIPアドレスを手掛かりとし、
  周辺のアドレス全般に対しpingコマンドを実行すると、接続可能なホストのIPアドレスの一覧が得られる。
#### Port scan
- ターゲットとするサーバに対し、どのようなサービスが利用できるかを調査する。
  
##### Stealth scan ステルススキャン
- サーバにログを残さずにポートスキャンを行う方法。
  通常の接続手段から外れた応答を行うことによりログを残さずにスキャンすること。
  具体的には、接続確率前にRSTを送信して接続を中断する「SYNスキャン」や、
  接続が確率していないのにFINを送りつけて応答を見る「FINスキャン」などの手法がある。

##### Half-open scanハーフオープンスキャン
#### Banner check バナーチェック
- コンピュータ上で動作しているソフトウェアへ外部からメッセージを送り、それへの応答を取得してソフトウェアの種類やバージョンなどを調べること
### Password Clack
#### 総当り攻撃
#### 辞書攻撃
#### rainbowクラック
- 先にパスワードを暗号化したものをデータベース化（rainbow table）し、
  暗号化されたパスワードとデータベースを比較する
#### 盗聴
### Eavesdrop 盗聴
#### Local
- snifferと呼ばれるネットワーク解析ツールで、プロミスキャスモードとすることでパケットを受信可能。
  SSLやsshを用いることで通信を暗号化することが効果的。
#### Man In The Middle
- ARPキャッシュを改ざんし、通信の間に入り込み盗聴を行う。
  ARPキャッシュを改ざんすることをARPポイズニングという。
#### Key logger
- キーボード操作を記録するプログラム。
### Session hijacking セッションハイジャック
- 通信の当事者でない第三者が何らかの手段でセッションIDを知り、セッションを乗っ取る攻撃手法。
#### 対策
- cookie
- フォームデータのhiddenフィールド
- URL
  - URL中にセッションIDを含める方法。特別な理由がない限り利用すべきでない。
## Defences
### Security Tools or Systems
#### Firewall
#### Encryption
##### PGP
- Pretty Good Privacy
  OpenPGP:RFC4880
### Cryptography
#### Cryptograhic hash function
- 暗号学的ハッシュ関数
##### アルゴリズム
- MD5
- SHA
  - SHA-1
  - SHA-2
    - SHA-224
    - SHA-256
    - SHA-384
    - SHA-512
- SHA-3

### Authentication 認証
#### PPP
##### PAP
##### CHAP
##### Link
- http://itpro.nikkeibp.co.jp/article/COLUMN/20060424/236003/
#### RADIUS
- remote authentication dial in user service
- RFC2865, RFC2866(課金)
##### AAAサービス
- A : Authentication 認証
- A : Authorization 認可
- A : Accounting 課金
##### Link
- http://itpro.nikkeibp.co.jp/article/COLUMN/20060505/236976/
#### Kerberos Authentication
- About
  - ネットワーク認証方式の一つ。シングルサインオンシステムを提供する。
  - MITの「Athena」プロジェクトによって開発され、現在もMITで保守されている。
  - RFC4120, RFC4121で標準化されている。
  - Active Directoryでの推奨の認証機構

##### Memo
###### ITPro
- http://itpro.nikkeibp.co.jp/article/COLUMN/20060518/238303/?rt=nocnt

- 用語
  - レルム
  - プリンシパル
  - KDC / Key Destribution Center
  - AS / Authentication Server 認証サーバー
  - TGS / Ticket Granting Server チケット発行サーバー
  - TGT / Ticket Granting Ticket
###### 
- 概要
  - 元締めのコンピュータに認証を受け、「チケット」を発行してもらう
  - その他コンピュータに対しては、発行されたチケットを使って認証を行う。

- 元締めコンピュータの役割
  - 認証
  - チケット発行
##### Link
- [[http://web.mit.edu/kerberos/][Kerberos: The Network Authentication Protocol]]

### Authorization
### SSL/TLS関連技術
#### SSL/TLS
##### Memo
- セッション層とトランスポート層の境界で動作する。
  (ちなみにIPsecはネットワーク層)
-
##### Link
#### Digital Signature 電子署名
## SSO
### 認証クッキー
- 
  Webは本来ステートレスだが、ブラウザを介してクッキーを伝達することにより、状態を共有する仕掛けを提供する。
  伝達範囲が同じ認証ドメイン内に制限されている。
  
### PMI
- Privilege Management Infrastructure
  
### SAML
- Security Assertion Markup Language
  XMLをベースにした、異なるインターネットドメイン間でユーザ認証を行うためのXMLをベースにした標準規格。
  2002年に策定、2005年にバージョン2.0。
  
  クッキーを用いず、クッキーの柔軟性を継承し、クッキーの持つスケーラビリティの制限とセキュリティ問題を解決することを目指して設計された。

  セキュリティ情報交換のためのXMLベースのフレームワーク。

#### Authentication Assertion
- 認証情報伝達サービス
#### Authorization Assertion
- 属性情報の伝達
  
#### Authorization Decision Assertion
- アクセス制御情報の伝達

#### XACML
- eXtensible Access Control Markup Language
  
- 
  - http://www.atmarkit.co.jp/ait/articles/0210/02/news002.html
  - http://www.cybernet.co.jp/onelogin/function/saml.html

#### Liberty Alliance

#### .NET Passport
#### Link
- [[https://www.oasis-open.org/standards#samlv2.0][SAML v2.0 - OASIS Standards]]

- http://www.atmarkit.co.jp/ait/articles/0210/02/news002.html

## Glossary
### CVE, CVSS, CWE
- https://qiita.com/sahn/items/563db4345f9ce502f3d2
#### CVE / Common Vulnerabilities and Exposures / 共通脆弱性識別子
- 世の中の脆弱性を一意に管理するためのID
#### CVSS / Common Vulnerability Scoring System / 共通脆弱性評価システム
- 脆弱性の深刻度のスコア
#### CWE / Common Weakness Enumeration / 共通脆弱性タイプ一覧
- 脆弱性を種類別に分類した指標
- CVE, CVSSの補足情報としての位置づけ。
##### Structure
###### View
###### Category
###### Weakness
###### Compound Element
##### Link
- [[http://cwe.mitre.org/data/reports.html][CWE List Version 3.1 - Common Weakness Enumeration]]
- [[https://www.ipa.go.jp/security/vuln/CWE.html][共通脆弱性タイプ一覧CWE概説 - IPA]]
### nonce
- number used onceのことで、1回だけ使われる番号、という意味。
  ワンタイムトークンとも呼ばれる。
  
### http referer
- 
  HTTPヘッダの1つで、1つのウェブページまたはリソースから見て、
  それにリンクしているウェブページやリソースのアドレスを指す。
  リファラを参照することで、どこからそのページに要求が来たのかを知ることができ、
  プロモーションやセキュリティの目的で使うことができる。

### Authentication/Authorization 認証・認可
- Authentication 認証
  本人確認。
- Authorization 認可
  特定のリソースへのアクセス権限の付与

### ゼロデイ
- バッチや対応策が準備される前に脆弱性を利用した攻撃コードが広まること
### 認証方法(DV,OV,EV)
#### DV ドメイン認証型
- ドメインの管理権限を元に発行される。SSL証明書の発行が可能。
  人が介在しないので、他の認証に比べ相対的に
  Let's encryptは現段階でDVのみ。将来的には価値が下がっていく可能性がある。
#### OV 実在証明型
- 
#### EV EVタイプ
- 
  URLがグリーンで表示される。
  DVとOVの違いが見た目で
### Guidelines
#### Overseas
- https://www.tripwire.co.jp/solution/compliance/nerc.html
##### NERC
- North American Electric Reliability Corporation
##### FISMA
- Federal Information Security Management Act
##### HIPPA
- Health Insurance Portability and Accountability Act
### OpenPGP
- RFC 1991 : (PGP)当初、PGPの仕様を提供しているだけ 
- RFC 2440 : 1998年に仕様を標準化
- RFC 4880
- RFC 5581 : Camelia
- RFC 6637 : 楕円曲線暗号対応

- PGP/MIME
  - RFC 2015
  - RFC 3156
## Tools
### Pretty Good Privacy, PGP
- フィル・ジマーマンが開発、公開した暗号ソフトウェア。
### GNU Privacy Guard
- Pretty Good Privacyの別実装で、GPLに基づいた暗号化ソフト。
  OpenPGP(RFC 4880)準拠。
### Vulnerability Scan
- https://webrage.jp/techblog/security_tool/
- https://ja.wikipedia.org/wiki/%E8%84%86%E5%BC%B1%E6%80%A7%E6%A4%9C%E6%9F%BB%E3%83%84%E3%83%BC%E3%83%AB
#### OWASP ZAP
- OWASP Zed Attack Proxy
- https://github.com/zaproxy/zaproxy
#### IBM AppScan
#### Fortify WebInspect Hewlett-Packard
### tmp
#### Burp Proxy
- [[https://portswigger.net/burp/proxy.html][Burp Proxy - PORTSWIGGER]]
#### FOCA
- [[https://www.elevenpaths.com/labstools/foca/index.html][FOCA - Eleven Paths]]
#### Evil FOCA
- [[https://www.elevenpaths.com/labstools/evil-foca/index.html][Evil FOCA - Eleven Paths]]

## Memo
### Securityの6要素
#### 3大要素(CIA)
##### Counfidentiality
- 機密性
  認可されたものだけが情報にアクセスできる
##### Integrity
- 完全性
  正確であることおよび完全であることを保証すること
##### Availavility
- 可用性
  認可されたユーザが、必要時に情報および関連財産にアクセスできることを確実にすること
#### 追加された要素
##### Accountability
- 説明追跡性（説明可能性）
  ユーザやサービスの行動、責任が説明できること。
##### Authenticity
- 真正性（認証性）
  ユーザ、システムによる振る舞いが明確であること。
  なりすましや偽の情報でないことが証明できること
##### Reliability
- 信頼性
  システムやプロセスが矛盾なく動作すること。
### 対策の考え方・分類
#### 時系列
##### 事前対策
##### 発生時対策
##### 発生後対応、見直し
##### 日常運用
#### 管理方法
##### 技術面
- 例
  ファイアウォール、ウィルス対策サーバ、
##### 運用面
- 例
  情報収集、入退室管理、
##### セキュリティポリシー面
- 社内規定による罰則、利用停止を含む利用規定の作成
#### リスクコントロール
##### 抑止
- 驚異の発生する可能性をなくす、低くする
  発生する前
##### 予防
- 脅威が発生した際の被害を小さくする、被害を受けにくい状態にしておく。
  発生後
##### 検知
- 問題の発生を速やかに発見できるようにする
##### 回復
- 正常な状態まで戻すことが出来るように備えておく考え方。
#### リスク管理
##### 許容
- 発生頻度や損害額が低いと判断できる場合、特に対策を行わない。
##### 低減
- リスクの発生頻度や損害額を、対策を行い低くすること
##### 移転
- 外部委託を行う等で、自社のリスクを他者に負わせること。
##### 回避
- 脅威発生の要因を停止あるいは全く別の方法に変更することにより、リスクが発生する可能性を取り去ること
### 直接的な脅威の種類
#### 破壊
#### 漏洩
#### 改ざん
#### 盗聴
#### 盗難
#### サービス停止
#### 不正利用
#### 踏み台
#### ウィルス感染
### WebサーバーとAPサーバの分離について
- セキュリティ上のメリットはあまりない、とのこと。
  https://ja.stackoverflow.com/questions/18417/web%E3%82%B5%E3%83%BC%E3%83%90%E3%83%BC%E3%81%A8ap%E3%82%B5%E3%83%BC%E3%83%90%E3%81%AE%E5%88%86%E9%9B%A2%E3%81%AB%E3%81%A4%E3%81%84%E3%81%A6/18449
### News
#### Apache Struts 2の脆弱 S2-045(2017/3/9)
- 影響を受けるバージョン
  Apache Struts 2.3.5 - 2.3.31, 2.5 - 2.5.10
##### Link
- [[https://www.ipa.go.jp/security/ciadr/vul/20170308-struts.html][Apache Struts2 の脆弱性対策について(CVE-2017-5638)(S2-045) - IPA]]
- [[https://www.jpcert.or.jp/at/2017/at170009.html][Apache Struts 2 の脆弱性 (S2-045) に関する注意喚起 - JPCERT]]
#### Ransomware対策(2015/11/11)
- 
  ランサムウェアが猛威を振るっている。
  セキュリティ対策としては、バックアップを取ることが、現在一番重要。

#### DigiNoater(2011)
- オランダの認証局
## Documents
### 経済産業省 独立行政法人 情報処理推進機構
#### サイバーセキュリティ経営ガイドライン
- http://www.meti.go.jp/policy/netsecurity/mng_guide.html
##### v2.0
###### 概要
####### I.
- セキュリティ対策は「コスト」でなく「投資」としてとらえることが重要
####### II.
- 3原則
####### III. サイバーセキュリティ経営の重要１０項目
- 指示1: 
###### 1. はじめに
####### 1.1.
####### 1.2.
###### 2. 経営者が認識すべき３原則
###### 3. サイバーセキュリティ経営の重要１０項目
####### 3.1.
####### 3.2.
####### 3.3.
####### 3.4.
####### 3.5.
###### 付録A
###### 付録B
###### 付録D
###### 付録E
#### 安全なウェブサイトの作り方
- https://www.ipa.go.jp/security/vuln/websecurity.html
##### 安全なウェブサイトの作り方 改訂第7版
###### はじめに
####### 脆弱性対策について
######## 根本的解決
- 「脆弱性を作り込まない実装」を実現する方法
######## 保険的対策
- 「攻撃による影響を軽減する対策」
  - 攻撃される可能性を低減（ヒントを与えない、など）
  - 攻撃された場合に脆弱性を突かれる可能性を低減（入力から攻撃に使われるデータをサニタイズする、など）
  - 脆弱性を突かれた場合に、被害範囲を最小化する（アクセス制御）
  - 被害が生じた場合に、早期に知る（事後通知）
###### 1. ウェブアプリケーションのセキュリティ実装
####### 1.1 SQLインジェクション
######## 発生しうる脅威
######## 注意が必要なウェブサイトの特徴
######## 根本的解決
######### 1-i-a : SQL文の組み立ては全てプレースホルダで実装する
- 静的プレースホルダの方が脆弱性対策としては勝る。
######### 1-i-b : SQL分の組み立てを文字列連結により行う場合は～
- SQL分の組み立てを文字列連結により行う場合は、エスケープ処理等を行うデータベースエンジンのAPIを用いて、SQL分のリテラルを正しく構成する
######### 1-ii : ウェブアプリケーションに渡されるパラメータにSQL文を直接指定しない
######## 保険的対策
######### 1-iii : エラーメッセージをそのままブラウザに表示しない
- データベースのエラーメッセージを画面に表示しない
######### 1-iv : データベースアカウントに適切な権限を与える
- 最小限の権限をDBに与える
####### 1.2 OSコマンド・インジェクション
######## 発生しうる脅威
######## 注意が必要なウェブサイトの特徴
- 外部プログラムを呼び出し可能な関数等を使用している
- 外部プログラウを呼び出し加工な関数の例：
  - Perl: open(), system(), eval(), ...
  - PHP : exec(), passthru(), shell_exec(), system(), ...
######## 届出状況
######## 根本的解決
######### 2-i : シェルを起動できる言語機能の利用を避ける
######## 保険的解決
######### 2-ii : シェルを起動できる言語機能を～
- 引数に埋め込む前にチェックをかけ、本来想定する動作のみを実行するように実装
- ホワイトリスト方式がおすすめ。ブラックリスト方式は漏れる可能性あるためお勧めしない
####### 1.3 パス名パラメータの未チェック/ディレクトリ・トラバーサル
####### 1.4 セッション管理の不備
- この問題を悪用した攻撃手法を「セッション・ハイジャック」という。
- 問題:
  - セッションIDの推測
  - セッションIDの盗用
  - セッションIDの固定化
######## 発生しうる脅威
######## 注意が必要なウェブサイトの特徴
######## 根本的解決
######### 4-i : セッションIDを推測が困難なものにする
######### 4-ii : セッションIDをURLパラメータに格納しない
######### 4-iii
######### 4-iv-a
######### 4-iv-b
######## 保険的対策
######### 4-v
######### 4-vi
####### 1.5 クロスサイト・スクリプティング
- ウェブページにスクリプトを埋め込まれる。
######## 対策について
######### 1.5.1 HTMLテキストの入力を許可しない場合の対策
########## 根本的対策
########### 5-i
########### 5-ii
########## 保険的対策
######### 1.5.2 HTMLテキストの入力を許可する場合の対策
########## 根本的対策
########## 保険的対策
######### 1.5.3 全てのウェブアプリケーションに共通の対策
########## 根本的対策
########## 保険的対策
########### 5-ix HttpOnly属性を加える
########### 5-x ブラウザの脆弱性対策を有効化するレスポンスヘッダを返す
- X-XSS-Protection 1; mode=block
- Content-Security-Ploicy: reflected-xss block
####### 1.6 CSRF
- ログインした状態で、外部サイトを経由した悪意のあるリクエストを受け入れてしまう場合がある。
######## 根本的解決
######### 6-i-a
- 
- hiddenパラメータを前のページで自動生成、実行頁では生成を行わず比較のみを行う。
######### 6-i-b 処理を実行する直前のページで再度パスワードの入力を求め、
######### 6-i-c Refererが正しいリンク元かを確認
######## 保険的対策
####### 1.7 HTTPヘッダ・インジェクション
####### 1.8 メールヘッダ・インジェクション
###### 2. ウェブサイトの安全性向上のための取り組み
- 主に運用面から安全性を向上させるための方策を示す
###### 3. 失敗例
##### 安全なSQLの呼び出し方
##### ウェブ健康診断仕様
## Link
- [[https://jvn.jp/index.html][JVN Japan Volnerability Notes]]
- [[https://jvndb.jvn.jp/index.html][JVN iPedia]]

- [[http://d.hatena.ne.jp/Kango/][piyolog]] 
- [[http://krebsonsecurity.com/][Krebs on Security]]
- [[https://the01.jp/][THE ZERO/ONE]]
- [[https://hackforums.net/index.php][Hack Forums]]
- [[http://securityaffairs.co/wordpress/][security affairs]]

- [[http://ken5scal.hatenablog.com/entry/2017/07/19/%28%E7%BF%BB%E8%A8%B3%29%E3%82%BB%E3%82%AD%E3%83%A5%E3%83%AA%E3%83%86%E3%82%A3%E3%81%A7%E9%A3%AF%E9%A3%9F%E3%81%84%E3%81%9F%E3%81%84%E4%BA%BA%E5%90%91%E3%81%91%E3%81%AE%E5%BF%83%E3%81%AE%E6%8C%81][(翻訳)セキュリティで飯食いたい人向けの行動指針 - Got Some \W+ech?]]
### Blog, tmp
- http://security.nekotricolor.com/
- [[https://the01.jp/p0005947/][日本人マルウェア開発者インタビュー（前編） プログラムの「悪意」とは - THE ZERO ONE]]
