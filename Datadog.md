# Datadog
## Documents
### はじめに
#### Datadog
- Integration
- Log
- APM & Continuous Profiler
  - Datadog Application Performance Monitoring
- Infrastructure
- Host Map
  - Infrastructureメニュー内
- Events
- Dashboards
- Moritors
- Network Performance Monitoring / NPM
  - Infrastructureメニュー内
- リアルユーザーモニタリング / RUM
- Serverless
- Security Monitoring
#### Datadogサイト
- 各サイトは完全に独立しており、サイト間でデータを共有できない。
- URLで確認可能。
#### Agent
##### 概要
- ホストにインストール。
  インテグレーション、DogStatsD、またはAPIを介して、ホストのメトリクスとイベントをDatadogに報告する。
##### セットアップ
###### Configuration
- 設定ファイル: datadog.yaml
  - 必須パラメーターはDatadog APIキー、AgentのデータをオーガニゼーションとDatadogサイト(datadoghq.com)に関連付ける。
    - 構成オプションの詳細: https://github.com/DataDog/datadog-agent/blob/main/pkg/config/config_template.yaml
    
###### 検証
- ステータスコマンドを実行する
###### コマンド
##### 収集データ
###### メトリクス
####### エージェント
####### チェック
- メトリクスを収集する幾つかのコアチェックがデフォルトで有効になっている
  
###### イベント
起動または再起動の際に、イベントをDatadogに送信する

###### サービスチェック
- datadog.agent.up: 接続できない場合にCRITICAL
- datadog.agent.check_status: Agentチェックがメトリクスを送信できない場合にCRITICAL

       
##### トラブルシューティング

#### インテグレーション
- 新しい構築方法：
  - [[https://docs.datadoghq.com/ja/developers/integrations/new_check_howto/?tab=configurationtemplate][新しいインテグレーションの設定]]
- インフラストラクチャーからすべてのメトリクスとログを収集して、統合システムを全体として把握できる。
- 3つのインテグレーション
  - エージェントベース、checkというPythonクラスメソッドを使用して、収集するメトリクスを定義する
  - 認証（クローラー）ベース、APIを使用してメトリクスを取得するための資格情報を指定する。Slack, AWS, Azure, PagerDutyなど
  - ライブラリインテグレーション、Datadog APIを使用して、記述言語に基づいてアプリケーションを監視できる

##### インテグレーションの設定
- Datadog Agentパッケージに、公式にサポートとしているインテグレーションコアが含まれる。
- [[https://docs.datadoghq.com/ja/agent/guide/integration-management/][インテグレーション管理]]

###### APIキーとアプリケーションキー
- APIキーが必要。

###### インストール
クローラーまたはライブラリベースのインテグレーションに接続する場合、来b手ウに確認

###### Agentインテグレーションの構成

##### 複数インテグレーションのインストール
##### 自動検出インテグレーション
##### セキュリティ対策

#### ダッシュボード

#### ログ

#### トレーシング

#### タグ

#### API

#### Syntheticモニタリング

#### ラーニングセンター

### Agent
- https://docs.datadoghq.com/ja/agent/
#### 基本的なAgentの利用方法
##### Agentアーキテクチャ
##### CLI
- <AGENT_バイナリパス> <サブコマンド> <オプション>
<<<<<<< HEAD:Datadog.org
****** check
****** configcheck
****** health
****** help
*** Integration
*** Dashboard
*** Infrastracture
*** Metrics
*** Alert
*** Log
** Datadog Agent
*** Command
**** RHEL
***** datadog-agent
****** check
- Run the specified check
****** completion
- Generate the autocompletion script for the specified shell
****** config
- Print the runtime configuration of a running agent
****** configcheck
- Print all configurations loaded & resolved of a running agent
****** diagnose
- Check availability of cloud provider and container metadata endpoints
****** dogstatsd-capture
- Start a dogstatsd UDS traffic capture
****** dogstatsd-replay
- Replay dogstatsd traffic
****** dogstatsd-stats
- Print basic statistics on the metrics processed by dogstatsd
****** flare
- Collect a flare and send it to Datadog
****** health
- Print the current agent health
****** help
- Help about any command
****** hostname
- Print the hostname used by the Agent
****** import
- Import and convert configuration files from previous versions of the Agent
****** integration
- Datadog integration manager
****** jmx
- Run troubleshooting commands on JMXFetch integrations
******* collect
******* list
******** collected
- List attributes that will actually be collected by your current instances configuration.
******** everything
- List every attributes available that has a type supported by JMXFetch.
******** limited
- List attributes that do match one of your instances configuration but that are not being collected because it would exceed the number of metrics that can be collected.
******** matching
- List attributes that match at least one of your instances configuration.
******** not-matching
- List attributes that don’t match any of your instances configuration.
******** with-metrics
- List attributes and metrics data that match at least one of your instances configuration.
******** with-rate-metrics List attributes and metrics data that match at least one of your instances configuration, including rates and counters.
****** launch-gui        starts the Datadog Agent GUI
****** run:   Run the Agent
****** secret            Print information about decrypted secrets in configuration.
****** secret-helper     Secret management provider helper
****** snmp:  Snmp tools
****** status            Print the current status
****** stop:  Stops a running Agent
****** stream-logs       Stream the logs being processed by a running agent
****** tagger-list       Print the tagger content of a running agent
****** version           Print the version info
****** workload-list     Print the workload content of a running agentr
=======
###### check
###### configcheck
###### health
###### help
### Integration
### Dashboard
### Infrastracture
### Metrics
### Alert
### Log
## 
>>>>>>> da64b3e6149158f439ef4f2f452104987db5f3cf:Datadog.md
