# Microsoft Azure
## About
- 2010/1に正式サービス開始をした、MSのクラウドプラットフォーム(PaaS/IaaS)。
  2014/1にWindows AzureからMicrosoft Azureに名称変更。

### 地域区分
- ジオ、リージョンペア、リージョン、データセンター

#### ジオ
##### 日本（ジオ）
###### 東日本/西日本（リージョンペア）
##### 北米（ジオ）
###### 米国中北部/米国中南部（リージョンペア）
###### 米国東部/米国西部（リージョンペア）
###### 米国東部2/米国中部（リージョンペア）
###### 米国西部2/米国中西部（リージョンペア）
##### ヨーロッパ（ジオ）
###### 北ヨーロッパ/西ヨーロッパ（リージョンペア）
##### アジア（ジオ）
###### 東南アジア/東アジア（リージョンペア）
##### ブラジル（ジオ）
###### ブラジル南部/米国中南部（リージョンペア）
##### オーストラリア（ジオ）
###### オーストラリア東部/オーストラリア西部（リージョンペア）
##### インド（ジオ）
###### インド中部/インド南部（リージョンペア）
##### カナダ（ジオ）
###### カナダ中部/カナダ東部（リージョンペア）
### コスト
#### 購入方法
- 12ヶ月分の前払いで割引を受ける、企業包括契約で事前に予算をコミットし割引を受ける等、複数の購入方法がある。
#### 階層構造
- 下記のような階層構造となっており、各階層で費用を把握することが可能。

- 構造 :
  - Azureの契約アカウント
    - Azureサブスクリプション
      - リソースグループ

- 例 :
  - 企業全体 : 335万円
    - 営業部門 : 300万円
      - 売上管理 : 100万円
      - 商談管理 : 200万円
    - マーケティング部門 : 30万円
      - キャンペーン
      - アンケート
    - 共通コスト : 50万円

### SLA
- 月次SLAが設定されている。
  他のサービスが仮想マシンやストレージに対するSLA提供のみであるのに対し、Azureは正式採用されているサービスには基本的にすべてSLAが設定されている。

### サポート、フォーラム、コミュニティ
#### サポート
- 次の5つ
  - 無償
  - 開発者
  - 標準
  - プロフェッショナルダイレクト
  - プレミア

- 各プランで設定されている応答時間に基づいて対応が行われる。

#### フォーラム
- https://azure.microsoft.com/en-us/support/forums/
- MSDNフォーラム
- stackoverflow

#### コミュニティ
- JAZUG (Japan Azure User Group)
- Tokyo Azure Meetup

## Services
### General
#### Dashboard
#### Resouce groups
#### All resources
#### Subscription
- 現在までの利用金額等を見ることができる。
#### Billing
#### Help + support
### Compute
#### Virtual machines
##### Memo
###### Password Reset
- 手順
  - Virtual machineを選択する
  - サポート+トラブルシューティング/Reset passwordを選択する
  - パスワードを入れる
- https://docs.microsoft.com/ja-jp/azure/virtual-machines/virtual-machines-windows-reset-rdp

###### Size
####### DS1_V2
####### DS2_V2
####### DS3_V2
####### DS4_V2
####### DS11_V2
####### DS1
####### DS2
####### DS3
####### DS4
####### DS11
####### F1S
- Free
###### 課金せずに停止する
- ポータル上で「停止」をクリックする。
  サーバ上でのシャットダウンでなく、割り当てを解除となり、課金されなくなる。
  IP割り当てなども全て解除されてしまうが、マルチインスタンスの場合はどれか一台が残っていればIP等の設定は残る。
- http://cloudsteady.jp/faq/2611.html/
- http://yomon.hatenablog.com/entry/2014/02/19/Azure%E3%81%AE%E4%BB%AE%E6%83%B3%E3%83%9E%E3%82%B7%E3%83%B3%E3%81%AE%E3%82%B7%E3%83%A3%E3%83%83%E3%83%88%E3%83%80%E3%82%A6%E3%83%B3%E6%96%B9%E6%B3%95%E3%81%AB%E3%81%AF%E6%B0%97%E3%82%92%E4%BB%98%E3%81%91
##### Type
###### Linux Virtual Machines / Linux 仮想マシン
###### Windows Virtual Machines / Windows仮想マシン
#### Virtual Machine Scale Sets /仮想マシン スケールセット
#### Functions App
#### App Service
#### Azure Container Service
#### Azure Container Registry
#### Service Fabric clusters
#### Kuberetes services
#### Batch
#### Cloud Services
#### Availability sets / 可用性セット
#### ディスク
#### スナップショット
#### イメージ
#### クラシック
##### 仮想マシン
##### Cloud Services
##### ディスク
##### OSイメージ
##### VMイメージ
### Networking
#### Virtual networks
##### Menu
###### Settings
####### DNS servers
- 
#### Azure Synapse Analytics
#### Load balancers
#### Front Doors Standard/Premium (Preview)
#### CDN profiles
#### ExpressRoute circuits
#### Network Watcher
- 仮想ネットワークのトラブルシューティングツール。
  現在は仮想ネットワークを作成するとデフォルトで有効となる。
- [[https://www.cloudou.net/virtual-network/vnet013/][ネットワーク調査ツール「Network Watcher」を見る！！ - くらう道]]

##### Next hop

##### Packet capture
- パケットキャプチャをNetwork Watcher上で設定して取得できる。
  https://docs.microsoft.com/ja-jp/azure/network-watcher/network-watcher-packet-capture-manage-portal
      
#### Network security groups
- NSG secures inbound and outbound traffic.
##### Menu
###### Settings
####### Inbound security rules
####### Outbound security rules
####### Network intrefaces
####### Subnets
####### Properties
####### locks
####### Automation script
###### Monitoring
###### Support + Toroubleshooting
#### Network interfaces
#### Public IP addresses
#### Pubilc IP Prefixes
#### On-premises Data Gateways
#### Route tables
#### Route filters
#### Application security groups
#### DDoS protection plans
#### Service endpoint policies
#### Private DNS zones
#### Web Application Firewall policies (WAF)
#### Private Link
#### Virtual WANs
#### Bastions
#### DNS zones
#### Traffic Manager profiles
#### Application gateways
##### WAF
###### Link
- [[https://docs.microsoft.com/ja-jp/azure/application-gateway/log-analytics][Log Analytics を使用して Application Gateway Web アプリケーション ファイアウォール (WAF) のログを調べる]]
- [[https://docs.microsoft.com/ja-jp/azure/web-application-firewall/ag/web-application-firewall-troubleshoot][Azure Application Gateway の Web アプリケーション ファイアウォール (WAF) のトラブルシューティング]]

#### NAT gateways
#### Front Doors
#### IP Groups
#### Firewall Manager
#### Firewall Policies
#### Firewalls
#### Connections
#### Local network gataways
#### Virtual network gataways
##### Memo
###### BGP on VPN
- [[https://docs.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-bgp-overview][About BGP with Azure VPN Gateway - Microsoft Docs]]
#### ExpressRoute Direct
### Storage
#### Storage accounts
##### Menu
###### Settings
####### Access keys
####### Configuration
#### Recovery Services vaults
#### Data Lake Storage
#### StorSimple
#### Backup
#### Site Recovery
### Web
#### App Service
#### API Management services
#### Media Services
#### Search services
#### Notification Hubs
### Mobile
### Containers
### Database
#### SQL Database
#### SQL Data Warehouse
#### NoSQL
#### SQL servers
#### SQL Server Stretch Database
#### DocumentDB
#### Redis Cache
#### Data Factory
### Analytics
#### Azure Databricks
### Blockchain
### AI + machine learning
### Internet of Things
### Mixed reality
### Integration

### Identity
#### Azure Active Directory
#### Azure AD Domain Services
#### Groups
#### Users
### Security
#### Key vaults
### DevOps
### Migrate
### Monitor
#### Log Analytics workspaces
##### Link
- [[https://docs.microsoft.com/ja-jp/azure/azure-monitor/logs/log-analytics-tutorial][Log Analytics のチュートリアル]]
##### Memo
###### Kusto Query Language
- [[file:KustoQueryLanguage.org][KustoQueryLanguage.org]]
### Management + governance
### Intune
### Other
    
## Azure Powershell
- [[https://docs.microsoft.com/en-us/powershell/azure/install-azurerm-ps?view=azurermps-4.2.0][Install and configure Azure PowerShell - Microsoft Azure]]
### Command-let
#### Popular
- Get-AzVM : 仮想マシンのプロパティを取得する
- Update-AzVM : Azure仮想マシンの状態を更新する
- New-AzDiskConfig : 構成可能なディスクオブジェクトを作成する
- Add-AzVMDataDisk : データディスクを仮想マシンに追加する
#### Modules
- https://docs.microsoft.com/en-us/powershell/module/?view=azps-6.2.1
##### Az.Compute
###### Get-AzVM
### Link
- [[https://docs.microsoft.com/en-us/powershell/azure/?view=azps-6.2.1][Azure Powershell documentation - Microsoft Docs]]
## Azure CLI
### Commands
#### az
##### az configure
##### az feedback
##### az find
##### az interactive
##### az login
##### az logout
##### az account
- Manage subscription
##### az acr
##### az acs
##### az ad
##### az appservice
##### az batch
##### az billing
##### az cdn
##### az cloud
##### az cognitiveservices
##### az group
###### az group create
- Create a resource group
- ex:
  az group create --name myResourceGroup --location eastus

####### Options
######## --name
######## --locatios
- eastus
- japaneast
- japanwest
###### az group delete
##### az vm
###### az vm create
- Creat a VM
- ex:
  az vm create --resource-group myResouceGroup --name myVM --image win2016datacenter --admin-username azureuser --admin-password myPassowrd12
  
####### Options
######## -g, --resource-group
######## --name
######## --image
######## --admin-username
######## --admin--password
###### az vm open-port
####### Options
######## --port
######## --resource-group
######## --name
### Link
- [[https://docs.microsoft.com/en-us/cli/azure/overview][Azure CLI 2.0 - Microsoft Aure]]
- [[https://docs.microsoft.com/en-us/cli/azure/][Azure CLI 2.0: Command reference - az - Microsoft Azure]]
## Reverse lookup
### Storageの追加
- 仮想マシンの画面→ディスク、で作成
- https://azure-recipe.kc-cloud.jp/2016/06/vm-data1/

### 仮想ネットワークの変更
- https://blogs.msdn.microsoft.com/ainaba-csa/2017/06/16/change-azure-vnet-configuration/
### IPの固定化
- 内部IP: ネットワークインターフェースから変更
- Public IP: パブリックIPアドレスから変更
### デフォルトDNS設定
- 仮想ネットワークで設定⇒DNSサーバー→カスタムにより指定。
### VMのリージョンを移動する
- Azure Resource Moverを利用する。
  - https://docs.microsoft.com/ja-jp/azure/resource-mover/tutorial-move-region-virtual-machines

- 

## Documentaiton
- [[file:MSAzure_Documentation.org][MSAzure_Documentation.org]]
## Template
- [[https://github.com/MSBrett/azure-quickstart-templates/tree/master/sql-server-2016-fci-existing-vnet-and-ad][SQL Server 2016 Failover Cluster using Windows Serer 2016 Storage Spaces Direct - github]]
## Memo
### Azure China
- 中国アカウントはGlobalアカウントとは切り離されており、MSアカウントの別途作成が必要。
  また、支払はAlipay, Unionpayのみ、中国の携帯電話番号が必要、法人アカウントの場合は中国国内の営業許可証が必要となるなど、要求が多い。
  MSでなく、21Vianetというローカル企業が運用を行っているとのこと。
### Resource Manager
#### Classic / V1 / ASM
- Azure Service Manager
  設定ファイル: XML
  クラシックポータル
#### Resource Manager / V2 / ARM
- Azure Resource Manager
  設定ファイル: JSON
  Azureポータル
### WindowsでAzureファイル共有
- Azureファイル共有のマウント方法：
  - エクスプローラからMap network drive
  - FolderにUNCパスを入力。
    - 形式：\\<storageAccountName>.file.core.windows.net\<fileShareName>
    - 例：\\anexampleaccountname.file.core.windows.net\example-share-name
  - ユーザー名に"AZURE\ストレージアカウント名"、パスワードにストレージアカウントキーを入力。

- https://docs.microsoft.com/ja-jp/azure/storage/files/storage-how-to-use-files-windows    
### ホストキャッシュ / host caching
- [[https://docs.microsoft.com/ja-jp/azure/virtual-machines/disks-performance][仮想マシンとディスクのパフォーマンス - Microsoft Docs]]

### Azureのディスクパフォーマンスが出ない
- [[https://docs.microsoft.com/ja-jp/learn/modules/caching-and-performance-azure-storage-and-disks/][Azure Storageディスクのキャッシュとパフォーマンス - Microsoft Docs - Learn]]
- [[https://blog.ryukiy.net/2015/06/12/premium-storage-part2/][IOPS とスループットの関係を解説します ～Premium SSD を使ってみよう～ - RyukiY's Blog]]
- [[https://teratail.com/questions/117126][Azureのディスク速度の遅さ、どうにかなりませんか？ - teratail]]
  
### ルーティングに関する問題を診断
- Network Watcher / ネットワークウォッチャーを利用して、次ホップ機能を使用して通信をテスト可能。Azure Portal上でも利用可能。
  https://docs.microsoft.com/ja-jp/azure/network-watcher/diagnose-vm-network-routing-problem-powershell
    
### 運用関連
- [[https://www.slideshare.net/mihochannel1/azure-98590356][こわくない！Azure運用管理 - slideshare]]

### 命名規則
- [[https://docs.microsoft.com/ja-jp/azure/cloud-adoption-framework/ready/azure-best-practices/resource-naming][名前付け規則を定義する - Microsoft Docs]]
    
## Link
- [[https://docs.microsoft.com/ja-jp/azure/][Document]]
- [[http://www.buildinsider.net/web/azure/01][まだ知らない人のための最新Microsoft Azure入門 - BulidINSIDER]]

- [[https://blogs.technet.microsoft.com/jpaztech/2017/12/06/azure-datacenter-infrastructure-1/][Azure データセンター ネットワーク インフラストラクチャー - Microsoft TechNet]]
- [[https://blogs.technet.microsoft.com/jpaztech/2016/08/09/storage-service-grs-failover/][ストレージサービスの地理冗長(GRS)の障害時の挙動について - Microsoft TechNet]]
- [[https://www.school.ctc-g.co.jp/columns/takeda/takeda02.html][第2回 高い可用性を持つMicrosoft Azure IaaSのデータセンターについて (武田正樹) - CTC]]
