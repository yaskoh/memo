# AWS
## Services
### Compute
#### EC2
- クラウド内の仮想サーバー
##### Menu
###### Network & Security
####### Security Group
###### Load Balancing
####### Load Balancer / ロードバランサー
- 以前のELB
######## 種類
######### Application Load Balancer / ALB
######### Network Load Balancer / NLB
######### Gateway Balancer
######### Classic Load Balancer / CLB
####### Target group
##### Instance type
###### 汎用 t2, m4, m3
###### コンピューティング最適 c4, c3
###### GPUインスタンス g2
###### メモリ最適 r4, r3, x1
###### ストレージ最適 d2, i2
##### Status
###### pending
###### running
###### rebooting
###### stopping
###### stopped
###### shutting-down
###### terminated
##### Glossary
###### インスタンス
- 1台のサーバー
###### EBS
- Amazon Elastic Block Store
  サーバーのハードディスクに相当する仮想ディスク
###### AMI
- Amazon Machine Image
  OSや各種ミドルウェア・アプリのイメージ
##### Memo
###### 再起動と停止・起動
- 再起動だとIPアドレス及びホストマシンは変わらないが、
  停止し起動すると、どちらも変更される。
###### 課金
- EC2は稼働している間課金されるので、利用しないインスタンスは停止しておく。
- ebsは利用した容量に関係なく、サイズによって課金される。インスタンスが不要になったらすみやかに破棄するとよい。
##### Old
###### EBS
- EC2向けブロックストレージ
  EC2のデータを保持するストレージサービス。
  EC2のハードディスク、SSDのような役割をする。
#### Lightsail
#### Lamdba
- LambdaファンクションというJava/Node.js/Pythonのいずれかで書いたプログラムを登録しておくて、
  イベントが発生した時に自動で実行してくれるサービス。
- 実行時にコンテナが作成され、終了時に破棄される。
#### Batch
- バッチ処理。大規模な科学計算やシミュレーションといった用途でよく利用される。
- 膨大な量のコンピューティングリソースを、コンテナ型のアプリケーション実行基板上で並列実行する多延の仕組みを提供するもの。
#### Elastic Beanstalk
- ウェブアプリの実行及び管理
  EC2, S3, ELB, Auto Scalingなどの環境を自動で生成し、Webアプリを容易に構築できるサービス。
- 次の開発プラットフォームをサポートしている。
  - .NET Core on Linux
  - .NET on Windows Server
  - Docker
  - GlassFish
  - Go
  - Java
  - Node.js
  - PHP
  - Python
  - Ruby
  - Tomcat

##### EB CLI
- AWS Elastic Beanstalkのコマンドラインインターフェース。
  https://docs.aws.amazon.com/ja_jp/elasticbeanstalk/latest/dg/eb-cli3.html

###### EB CLIコマンド
- https://docs.aws.amazon.com/ja_jp/elasticbeanstalk/latest/dg/eb3-init.html
####### eb init
####### eb create
- 新しい環境を作成し、アプリケーションバージョンをデプロイする。  
####### eb deploy
- アプリケーションソースバンドルをデプロイする
  
#### Serverless Application Repository
#### AWS Outposts
#### EC2 Image Builder
#### AWS App Runner
### Container
#### Elastic Container Registry
- Dockerイメージの保存と取得
#### Elastic Container Service
- Dockerコンテナを実行および管理
- 
##### Fargate
- ECSでコンテナを実行する起動タイプのうちの一つ。
  EC2起動タイプとFargete起動タイプから選択可能。

###### Link
- [[https://aws.amazon.com/jp/blogs/startup/techblog-container-fargate-1/][AWS ECS 10分チュートリアルでふんわりFargate入門 - yiio - note]]
- [[https://pages.awscloud.com/rs/112-TZM-766/images/A-1.pdf][AWS Fargate かんたんデプロイ選手権 - DEV DAY TOKYO]]
    
#### Elastic Kubernetes Service
#### Red Hat OpenShift Service on AWS
### Storage
#### S3
- クラウド内のスケーラブルなストレージ
##### Glossary
###### バケット
- データの入れ物
###### オブジェクト
- 格納するファイルの呼び方
#### EFS
- EC2のマネージド型ファイルストレージ
  ファイルの追加/削除に伴って、自動で容量を拡張/縮小するストレージ
#### FSx
#### S3 Glacier
- クラウド内の低コストなアーカイブ向けストレージ
  バックアップやアーカイブなどの用途に使う。磁気テープのような使い方が適している。
#### Storage Gateway
- ハイブリッドストレージの統合
  オンプレミスとAWSを接続するストレージゲートウェイ
##### Type
###### File Gateway
###### Volume Gateway
####### Gateway-Stored Volumes
- オンプレスにデータを保存。S3に非同期にバックアップする。低レイテンシーアクセスが可能。
####### Gateway-Cached Volumes
- S3にデータを保存。よく使うデータセットのコピーをオンプレミス側に保存する。オンプレミス側のストレージ容量を抑えられる。
###### Tape Gateway
#### AWS Backup
### Database
#### RDS
- Amazon Relational Database Service
- Aurora, MySQL, PostgreSQL, Oracle, SQL Server, MariaDB向けの
  マネージドリレーショナルデータベースサービス
##### Menu
###### インスタンス
###### Security Group セキュリティグループ
###### Parameter Group パラメータグループ
- 文字コードや接続数などのパラメータを設定する。
  DBの種類ごとに利用できる項目が違う。
###### Option Group オプショングループ
- DBの固有機能について設定する。
###### Subnet Group サブネットグループ
- 仮想プライベートネットワークで稼働させる際に利用する。
##### Glossary
###### マルチAZ
- マルチアベイラビリティーゾーン。
  プライマリデータベースとは異なるゾーンにデータベースを作成し、そこにデータを複製してくれる。
###### Storage
####### 汎用(SSD)ストレージ
####### プロビジョンドIOPS(SSD)ストレージ
- I/Oのパフォーマンスが高速であるSSDストレージ。
####### マグネスティックストレージ
- 磁気ストレージ。安価だがパフォーマンスは劣る。
#### DynamoDB
- マネージドNoSQLデータベース。非構造化データを容易に扱える。
  Key-Value型。
- Read Capacity Unit(RCU)とWrite Capacity Unit(WCU)の指定。

- グローバルテーブルにより、マルチリージョンにマルチマスターデータベースをデプロイできる。
#### ElastiCache
- インメモリキャッシングシステム
  低速のディスクではなく、高速のメモリ内キャッシュから情報を取得する
- RedisとMemcachedを選択可能。
#### Neptune
- グラフデータベース。
#### Amazon QLDB
#### Amazon DocumentDB
#### Amazon Keyspaces
#### Amazon Timestream
### Migration
#### AWS Migration Hub
#### AWS Application Migration Service
#### Application Discovery Service
#### Database Migration Service
- 最小限のダウンタイムでデータベースを移行
  オンプレミスのDBSからの移行などに使う。
#### Server Migration Service
#### AWS Transfer Family
#### AWS Snow Family
##### AWS Snowball
##### AWS Snowball Edge
##### AWS Snowmobile
#### DataSync
### Network & Content Delivery
#### VPC / Virtual Private Cloud
- 独立したクラウドリソース
##### Services
###### Virtual Private Network
####### VPC
####### Subnet
####### Route table
####### Internet Gateway
####### Elastic IP
####### Endpoint
- Amazon VPC Endpoint
- インターネットゲートウェイやNATゲートウェイ、NATインスタンスなどを経由することなく、VPCと他のAWSのサービスとをプライベートに接続できるAWSのサービス。
- ゲートウェイエンドポイント(S3, DynamoDBのみ)と、インターフェイスエンドポイントがある。
  - インターフェースエンドポイントをPrivateLinkと呼ぶ。
####### Endpoint Service
####### NAT Gateway
####### Peering
- VPC Peering
- 異なるAWSアカウントで作成されたVPC、異なるリージョンに存在するVPC間でも設定可能。
######## インターリージョンVPCピアリング
- [[https://dev.classmethod.jp/articles/inter-regrion-vpc-peering/][[新機能]リージョン間のVPCピアリング「Inter-Region VPC Peering」がリリースされました！ #reinvent - DevelopersIO]]

###### Security
####### NetworkACL
####### Serucity Group
####### Memo
######## ネットワークACLとセキュリティグループの違い
- [[https://dev.classmethod.jp/articles/why-i-prefer-sg-to-nacl/][なぜネットワークACLでなくセキュリティグループで細かいトラフィック制御を行なうのか - DevelopersIO]]
- 設定対象：NACLはサブネット、セキュリティグループはインスタンス。
- 設定内容：NACLは許可、拒否共に設定する。番号の低い順に評価される。
  セキュリティグループはデフォルトで通信拒否。許可ルールのみ設定する。
- ステート：NACLはステートレス、セキュリティグループはステートフル。
  

###### Reachability
###### DNS firewall
###### Network Firewall
###### Virtual Private Network
####### Customer Gateway / CGW
####### Virtual Private Gateway / VGW
####### Site to Site VPN Connection
####### Client VPN Endpoint
###### Transit Gateway
###### Mirroring
##### Memo
###### Private Link
- エンドポイントサービスと、インターフェースエンドポイントをつなげる仕組み。
  インターネットを介さずに、特定のエンドポイントへとアクセスが可能となる。
- https://qiita.com/mksamba/items/20903940b8b256ef2487
- https://dev.classmethod.jp/articles/aws-reinvent-vpc-privatelink-endpoint/
###### AWSのグローバルIPの空間はネットワークなのか
- [[https://tech.nri-net.com/entry/2021/05/10/085654][AWSのグローバルIPの空間はインターネットなのか？ - NRI Netcom Design & Tech Blog]]

#### CloudFront
- グローバルなコンテンツ配信ネットワーク
#### Rounte 53
- スケーラブルなドメインネームサービス
  ドメイン名とIPアドレスを対応付けるDNSシステムを構築するためのサービス
#### API Gateway
- Rest APIを容易に作成・管理できるツール。
- REST API、WebSocket API、HTTP APIをサポート。
#### Direct Connect
- AWSへの専用線接続
  オンプレミスのネットワークとAWSのVPCネットワークとを直接に接続するための専用線サービス
##### Connection
##### Virtual Interface
##### LAG
##### Direct Connect Gateway
- [[https://dev.classmethod.jp/articles/direct-connect-gateway/][[新機能] AWS Direct Connect Gatewayで世界中のAWSリージョンとプライベート接続する - DevelopersIO]]
- 仮想インターフェースと仮想プライベートゲートウェイの間に追加するコンポーネント。
  Direct connect GatewayをいずれかのAWSリージョンに作成すると、AWSの全リージョンに複製され、相互接続できる。
  
##### Virtual Private Gateway
##### Transit Gateway
#### AWS App Mesh
#### AWS Cloud Map
#### Global Accelerator
### Developer Tools
#### CodeStar
- ウィザード形式でCI/CDパイプラインを構築。
  プロジェクトテンプレートを選択して、プロジェクト名を決めるだけで、各AWS Codeサービスを構成したCI/CDパイプラインを自動的に作成できる。
#### CodeCommit
- プライベートGitリポジトリでのコード保存
#### CodeArtifact
- プライベートソフトウェア配信リポジトリサービス
- アーティファクト向けのリポジトリを提供するサービス。
  アーティファクトとは、ソフトウェアの分野ではなんらかの生成物、例えばコンパイルやビルドで制しえされたバイナリやパッケージのこと。
  例えば、npmのリポジトリや、MavenやGradleに対応するリポジトリなど。
  https://www.publickey1.jp/blog/20/awsaws_codeartifactnpmmavenpypi.html

#### CodeBuild
- コンパイル、テスト、パッケージングなどのビルドプロセスを提供     
#### CodeDeploy
- コードデプロイの自動化
#### CodePipeline
- 継続的デリバリーを使用したソフトウェアのリリース
#### Cloud9
#### CloudShell
#### X-RAY
#### AWS FIS
     
### Customer Enablement
#### AWS IQ
#### Support
#### Managed Services
#### Active for Startups
### ロボット工学
#### Amazon RoboMaker
### Blockchain
#### Amazon Managed Blockchain

### 衛星
#### Ground Station
### Quantum Technologies
#### Amazon Braket

### Management and Governance / 管理とガバナンス
#### AWS Organizations
- [[https://dev.classmethod.jp/articles/organizations-gettingstarted/][AWS Organizationsとは？rootユーザも制御するその強力さを手を動かして体感してみる - DeveloperIO]]

- 組織単位 / OU
- サービス管理ポリシー / SCP
  - 各サービスの利用を許可するか、拒否するかを設定する。
    実際にIAM上の権限を与えるわけではないので、各アカウント上で別途IAM設定は必要。

#### CloudWatch
- リソースとアプリケーションのモニタリング
##### Services
###### CloudWatch
- リソースの監視
###### CloudWatch Logs
- ログの監視
###### CloudWatch Events
- APIのイベントをトリガーに何らかのアクションを実行させる
#### AWS Auto Scaling
#### CloudFormation
- テンプレートを使ったリソースの作成と管理
- JSONまたはYAMLで記述されたテンプレートを元に、スタックというAWSの集合体を自動構築する。
#### CloudTrail
- ユーザーアクティビティとAPI使用状況の追跡
- AWSに関する操作ログを自動的に取得するサービス。
#### Config
- リソースのインベントリと変更の追跡
#### OpsWorks
- Chefを使った操作の自動化
#### Service Catalog
- 標準化された製品の作成と仕様
#### Systems Manager / SSM
##### Services
###### ノード管理
####### Session Manager / セッションマネージャー
- ssh接続のようなことが行える
####### Run command
####### パッチマネージャー
- パッチルール準拠状況の確認、パッチ適用の自動化などを行える。
- 実態は、メンテナンスウィンドウでのRun command(AWS-RunPatchBaseline)の定期実行。
###### 共有リソース
####### ドキュメント
##### Link
- https://pages.awscloud.com/rs/112-TZM-766/images/20200417_AWSSystemsManagerHandson.pdf
#### AWS AppConfig
#### Trusted Advisor
- パフォーマンスとセキュリティの最適化
- AWSアカウント内の状況を5つの観点でチェックしてくれる。

#### Control Tower
#### AWS License manager
#### AWS Well-Architected Tool
#### Personal Health Dashboard
#### AWS Chatbot
#### Launch Wizard
#### AWS Compute Optimizer
#### Resource Groups & Tag Editor
#### Amazon Grafana
#### Amazon Prometheus
#### AWS Proton
#### Incident Manager
### Media Services
#### Kinesis Video Streams
#### MediaConnect
#### MediaConvert
#### MediaLive
#### MediaPackage
#### MediaStore
#### MediaTailor
#### Elemental Appliances & Software
#### Amazon Interactive Video Service
#### Elastic Transcoder
- 動画のTranscodeを実現する。
#### Nimble Studio

### Machine Learning
#### Amazon SageMaker
##### Old: Amazon Machine Learning
 - 終了。SageMakerを使うように。
 - 機械学習、デベロッパー向け機械学習

#### Amazon Augmented AI
#### Amazon CodeGuru
- 最もコストがかかるコード行を見つけて、コードの品質を向上する
##### CodeGuru Profiler
- アプリケーションのパフォーマンスを可視化、問題の原因を診断することができる
##### CodeGuru Reviewer
- GitHubやCodeCommitなどと連携し、Javaのコードの自動レビューを実行する。
#### Amazon DevOps Guru
#### Amazon Comprehend
#### Amazon Forecast
#### Amazon Fraud Detector
#### Amazon Kendra
#### Amazon Lex
#### Amazon Personalize
#### Amazon Polly
#### Amazon Rekognition
#### Amazon Textract
#### Amazon Transcribe
#### Amazon Translate
#### AWS DeepComposer
#### AWS DeepLens
#### AWS DeepRacer
#### AWS Panorama
#### Amazon Monitron
#### Amazon HealthLake
#### Amazon Lookout for Viion
#### Amazon Lookout for Equipment
#### Amazon Lookout for Metrics
### Analytics
#### Athena
- S3内のデータを標準SQLを利用して直接分析できるようにする対話型のクエリサービス。
- エンジン部分はFresto。
#### Amazon Redshift
- 高速、シンプル、費用対効果の高いデータウェアハウス。
  ペタバイト規模のデータを分析できる。

- 別のリージョンにスナップショットを転送するクロスリージョンスナップショット機能がある。
  
#### EMR
- ホスト型Hadoopフレームワーク
- 元々は"Amazon Elastic Map Reduce"という名前だった。
- Apache Spark、HBase、Presto、Flinkなどが利用可能。
#### CloudSearch
- 検索機能。
#### Amazon Opensearch Service
- Elasticsearch Serviceの後継。
##### Elasticsearch Service
- Elasticsearchクラスターを実行し、スケールする
  CloudSearchがあったが、シェアの高まりを受けElasticserch Serviceを開始。
##### Memo
###### CloudSearchとElasticsearch
- [[https://dev.classmethod.jp/articles/elasticsearch-service-vs-cloudsearch/][Elasticsearch Service と CloudSearch どっちを選べば良いの？ - DevelopersIO]]
- どちらもLuceneベース。
- Elasticsearchは高いカスタマイズ性。
- 簡単に言うとCloudSearchは「サイト内検索アプリ」、Elasticsearchは「検索エンジンプラットフォーム」
#### Kinesis
- リアルタイムストリーミングデータとの連携
- 4つの機能：
  - Data Streams
  - Data Firehose
  - Video Streams
  - Data Analytics
##### 機能
###### Data Streams
###### Data Firehose
###### Video Streams
###### Data Analytics
#### QuickSight
- 高速ビジネス分析サービス
- データの可視化をおこなう。ダッシュボードを作成、ブラウザ経由で閲覧可能。
#### Data Pipeline
- 定期的なデータ駆動型ワークフローに対するオーケストレーションサービス
#### AWS Data Exchange
#### AWS Glue
- データの検出、準備、結合を簡単に行える。ETL / Extract, Transform, Load
- S3のデータを管理してRedshiftなどに変換して格納するといった用途によく利用される。
- 大きく、データを管理する機能と、それを変換するエンジンとしての機能を持っている。
  - データ管理：データを探索するクローラーの機能と、それをメタデータとして管理するデータカタログの機能がある。
  - 変換処理は、PythonやSparkによって実装可能。
  
#### AWS Lake Formation
#### MSK
#### AWS Glue DataBrew
#### Amazon FinSpace
### Security, Identity & Compliance
#### IAM
- ユーザーアクセスと暗号化キーの管理
  認証を行うサービス。アクセスコントロールが可能。
##### Type
###### User
###### Groups
####### AmazonEC2FullAccess
- Provides full access to Amazon EC2 via the AWS Management Console.
####### AmazonRDSFullAccess
- Provides full access to Amazon RDS via the AWS Management Console.
###### Role
###### Policy
- https://devlog.arksystems.co.jp/2020/03/12/9338/
####### 種類
- [[https://docs.aws.amazon.com/ja_jp/IAM/latest/UserGuide/access_policies_managed-vs-inline.html#choosing-managed-or-inline][管理ポリシーとインラインポリシー - aws]]
######## 管理ポリシー / AWS Managed Policies
- AWSが作成及び管理するスタンドアロンポリシー。独自のARNのついたポリシー。
######## カスタマー管理ポリシー / Customer Managed Policies
- ユーザのAWSアカウントで管理・作成できるスタンドアロンのポリシー。
######## インラインポリシー
- IAMアイデンティティ（ユーザー、グループ、ロール）に埋め込まれたポリシー。
  本質的にアイデンティティの一部。
- 管理ポリシーができる前の古い機能。
######## アクセス権限の境界 / Permission Boundary
####### ポリシータイプ
- [[https://docs.aws.amazon.com/ja_jp/IAM/latest/UserGuide/access_policies.html][IAM でのポリシーとアクセス許可 - aws]]
- [[https://dev.classmethod.jp/articles/aws-iam-policy/][AWS IAMポリシーを理解する - DevelopersIO]]
########  1. アイデンティティベースポリシー
- 誰が、どのリソースに対してどんなアクションを実行できるか、を指定。
  IAMアイデンティティ（ユーザー、グループ、ロール）に直接アタッチする
- 管理ポリシーとインラインポリシー
########  2. リソースベースポリシー
- このリソースに対して、誰がどんなアクションを指定できるかを指定。
  リソースにアタッチする。
- アイデンティティベースとの違いは、Principalの有無。
- インラインポリシーしか作成できない
- 最も一般的な例は、S3バケットポリシーとIAMロールの信頼ポリシー。
######### IAMロール信頼ポリシー
- IAMロールの権限委譲操作に特化したポリシー。
  
########  3. アクセス許可の境界
########  4. 組織SCP
########  5. ACL
########  6. セッションポリシー
####### JSONポリシーの要素
- https://docs.aws.amazon.com/ja_jp/IAM/latest/UserGuide/reference_policies_elements.html#Principal
######## Version
- 2つのみ。
######## Id
######## Statement
- ポリシーの主要エレメント。
######## Sid
######## Effect
- AllowとDenyの2種類。
######## Principal
- IAMロールでは、だれがこのロールを引き受けることができるかを指定する。
- リソースベースのポリシーでは、リソースへのアクセスが許可されるアカウントまたはユーザーを指定する。
######## NotPrincipal
######## Action
######## NotAction
######## Resource
- ステートメントで取り扱う一連のオブジェクトを指定する。
  ARNを使用して、リソースを特定する。
######## NotResource
######## Condition
##### Memo
###### 外部ID、混乱した代理問題
- [[https://dev.classmethod.jp/articles/iam-role-externalid/][IAM ロールの信頼ポリシーで設定する外部 ID(sts:ExternalId) について - DevelopersIO]]
#### Resource Access Manager
#### Cognito
#### Secrets Manager
#### GuardDuty
- AWS上での操作や動作をモニタリングして、セキュリティ上の脅威を検出するサービス。
- 機械学習で分析されたログから、攻撃と思われる状況を検知してくれる
- [[https://www.wafcharm.com/blog/amazon-guardduty-for-beginners/][【Amazon GuardDuty とは？】初心者にもわかりやすく解説 - WafCharm]]
#### Inspector
- アプリケーションのセキュリティの分析
#### Amazon Macie
#### AWS Single Sign-On
#### Certificate Manager
#### Key Management Service
- マネージド型の暗号化キー作成と管理
#### CloudHSM
- 法令順守のためのハードウェアベースキーストレージ
  暗号鍵管理のための専用ハードウェア
#### Directory Service
- Active Directoryのホスティングと管理
#### WAF & Shield
- WAF: 悪意のあるウェブトラフィックのフィルター
##### Shield
- DDoS攻撃からAWSリソースを保護するためのマネージドサービス。
- StandardとAdvancedの2種類があり、Standardはすべてのユーザが無料で利用可能。
  Advancedは有料。Elastic IPやELBといった追加のサービスを保護対象とすることができる。
#### AWS Firewall Manager
#### Artifact
#### Security Hub
#### Detective
#### AWS Audit Manager
#### AWS Signer
#### AWS Network Firewall
     
### AWS Cost Management
#### AWS Cost Explorer
#### AWS Budgets
#### AWS MarketplaceSubscriptions
#### AWS Application Cost Profiler

### Mobile Services
#### AWS Amplify
#### Mobile Hub
#### AWS AppSync
#### Device Farm
#### Amazon Location Srevice
### AR, VR
#### Amazon Sumerian

### Application Integration
#### Step Functions
- Lambdaの制御に利用する。ステートマシン。
#### Amazon AppFlow
#### Amazon EventBridge
#### Amazon MQ
#### Simple Notification Service
#### Simple Queue Service
#### SWF
- Simple Workflow
#### Managed Apache Airflow
### Business Application
#### Amaon Connect
-  クラウドコンタクトセンター/コールセンター
#### Amazon Pinpoint
#### Amazon Honeycode
#### Amazon Chime
#### Amazon Simple Email Service
#### Amazon WorkDocs
#### Amazon WorkMail
#### Alexa for Business
### End User Computing
#### WrokSpaces
#### AppStream 2.0
#### WorkLink
### IoT
#### IoT Core
#### FreeRTOS
#### IoT 1-Click
#### IoT Analytics
#### IoT Device Defender
#### IoT Device Management
#### IoT Events
#### IoT Greengrass
#### IoT SiteWise
#### IoT Things Graph
### Game Development
#### Amazon GameLift
## Well-Architected Framework
### 運用の優秀性
### セキュリティ
### 信頼性
### パフォーマンス効率
### コストの最適化
## Memo
- [[https://qiita.com/nakazax/items/20458e146d3d9f2aa615][AWS認定9冠制覇したのでオススメの勉強法などをまとめてみる - Qiita]]
### Security関連
- [[https://aws.amazon.com/jp/blogs/news/aws-hands-on-for-beginners-06/][アカウント作成後すぐやるセキュリティ対策” 編を公開しました！- Monthly AWS Hands-on for Beginners 2020年4月号 - AWS]]
#### MFAの設定
-  IAM→ユーザー→設定したいユーザーを選択→認証情報タブ→MFAデバイスの割り当て、で設定。
  [[https://docs.aws.amazon.com/ja_jp/IAM/latest/UserGuide/id_credentials_mfa_enable_virtual.html][仮想 Multi-Factor Authentication (MFA) デバイスの有効化 (コンソール) - aws]]
#### アカウントIDの確認、アカウントエイリアスの設定
- マネジメントコンソール上右上に表示されるユーザ名のドロップダウンで確認、あるいはその中のマイセキュリティ資格情報内で確認可能。
  [[https://docs.aws.amazon.com/ja_jp/IAM/latest/UserGuide/console_account-alias.html][AWS アカウントのエイリアスの作成、削除および一覧表示 - aws]]
### ELB
- 以前のLB、今は総称ととらえるのがよい。
  現在はALB、NLB、CLBの3種類。
### AzureのDRパターン
- [[https://michimani.net/post/aws-architecture-for-disaster-recovery/][AWS 上でのディザスタリカバリ (DR) 構成 4 パターン - michimani.net]]
- バックアップ＆リストア
- パイロットライト
- ウォームスタンバイ
- マルチサイト（ホットスタンバイ）

## Link
- https://aws.amazon.com/jp/
- [[https://docs.aws.amazon.com/index.html][AWS Documentation]]
### Learn
- [[https://pages.awscloud.com/JAPAN-event-OE-At-least-10-basic-2020-confirmation-639.html][AWS ご利用開始時に最低限おさえておきたい10のこと - aws]]
- [[https://d1.awsstatic.com/webinars/jp/pdf/services/20190123_10things_at_least_for_AWSBeginner.pdf][AWSご利用開始時に最低限おさえておきたい10のこと・資料 - aws]]

  
