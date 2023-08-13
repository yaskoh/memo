# Azure Documentation
## Security
- [[https://docs.microsoft.com/ja-jp/azure/security/][Azureのセキュリティのドキュメント - MicrosoftAzure]]
### 基礎のドキュメント / [[https://docs.microsoft.com/ja-jp/azure/security/fundamentals/][Azureのセキュリティの基礎に関するドキュメント]]
#### 概要
##### Azureのセキュリティの概要
###### 概要
####### Azureプラットフォーム
###### Azureのセキュリティ機能の概要
####### Azureプラットフォームをセキュリティで保護するための機能
- 各主の取り組み(Link)
######## 安全なプラットフォーム
######## プライバシー管理
######## コンプライアンス
######## 透明性
####### データとアプリケーションをセキュリティで保護するための機能
- ビルトイン機能は、6つの機能区分に分類される。
  - 操作、アプリケーション、ストレージ、ネットワーキング、コンピューティング、ID
###### 操作・Operations
####### ダッシュボード
- Security Center
- Azure Monitor
####### Azure Resource Manager
####### Application Insights
####### Azure Monitor
####### Azure Monitor Log
####### Azure Advisor
####### Azure Security Center
###### アプリケーション
####### Webアプリケーションの脆弱性のスキャン
- Tinfoil Security
####### 侵入テスト
- 承認プロセスに従い事前の承認を得たうえで実行する必要がある。
  - https://docs.microsoft.com/ja-jp/azure/security/fundamentals/pen-testing
    →2017/6/15時点で、事前承認を求めなくなった。ただし、規則には引き続き従う必要がある。
####### Webアプリケーション ファイアウォール
####### Azuer App Serviceでの認証および認可
####### 複数層セキュリティ アーキテクチャ
####### Webサーバ診断とアプリケーション診断
######## Webサーバー診断
######## アプリケーション診断
###### ストレージ・Storage
####### ロールベースのアクセス制御(RBAC)
####### 転送中の暗号化
- ネットワーク間でデータを転送するときにデータを保護する
  - トランスポートレベルの暗号化(Azureの内外へのデータ転送時のHTTPSなど)
  - ワイヤ暗号化(Azureファイル共有のSMB3.0暗号化など)
  - クライアント側の暗号化(ストレージにデータを転送する雨にデータを暗号化し、ストレージからデータを転送した後にデータを複合化)
####### 保存時の暗号化
- 保存時の暗号化は下記3種類
  - Storage Service Encryption（Azure Storageへデータ書込み時に暗号化）
  - クライアント側の暗号化（保存時の暗号化機能も保持）
  - Azure Disk Encryption（IaaS仮想マシンのOSディスクとデータディスクの暗号化）

####### Storage Analytics

####### CORSを称したブラウザーベースの句アイアンとの有効化

###### ネットワーク
####### ネットワーク層制御
######## ネットワーク セキュリティ グループ NSG
- ファイアウォール、5タプルでアクセス制御。
  - Source IP, Source Port, Dest IP, Dest Port, Protocol
######## ルート制御と強制トンネリング
- ユーザー定義ルートで制御
- 強制トンネリング
######## 仮想ネットワークのセキュリティ アプライアンス
######## Azure Virtual Network
######## VPN Gateway
######## ExpressRoute
######## Application Gateway
######## Webアプリケーション ファイアウォール
- Azure Application Gateway、WAF
######## Traffic Manager
######## Azure Load Balancer
######## 内部DNS
######## Azure DNS
######## Azure Monitor ログ NSG
######## Security Center
###### コンピューティング・Compute
###### ID管理とアクセス管理
###### 次の手順
##### クラウドにおける共同責任
#### Azureのワークロードをセキュリティで保護する
#### Azureプラットフォームとインフラストラクチャ
#### ID管理
#### ネットワークのセキュリティ
#### IaaSセキュリティ
#### データのセキュリティ、暗号化、保管
#### Application
#### 監視、監査、および操作
#### リソース
