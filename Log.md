# Log
## logrotate
## rsyslog
- [[http://changineer.info/server/logging/linux_rsyslogd.html][rsyslogd(syslogd)設定 - ネットワークチェンジニアとして]]

## fluentd
- fluentd
  ruby gemによって提供される、ログの転送・集約を行うための仕組み。
  複数台のサーバを運用している時にそれぞれのサーバにたまるログを、簡単な記述で特定の場所に集約できる。

- td-agent
  fluentdのラッパープログラム。
  ruby, gem等のプログラムや起動スクリプトなどの便利なファイルをインストールコマンドひとつで提供してくれる。

### Link
- [[http://www.fluentd.org/][fluentd]]
- [[http://changineer.info/server/logging/fluentd-td-agent.html][fluentd(td-agent)のインストールと設定 ネットワークチェンジニアとして]]

## Log4j
### 概要
- 
  Javaプログラム用のログAPI。

### Ver1.2
#### Fundamentals
##### Logger
- 
  中心クラス。ロギングを行う部分をグループ化し、必要なグループのログだけを出力したり、
  カテゴリーに優先順位をつけることで様々な出力方法を指定可能。
  
- 
  名称の指定自体はjavaのソースで行っており、それを設定ファイルで扱う。
  
- ex
   //設定値上の"tripleLogger"を、ソース上でtripleLとして扱う。下も同様。
  tripleL = Logger.getLogger("tripleLogger");
  fifthL  = Logger.getLogger("fifthLogger");

###### org.apache.log4j.Logger Class
- 
  ログイベントを発生させるために使用されるクラス。
  階層を形成し、親Loggerに設定された属性などは子Loggerに継承される。
  最上位にRootLoggerが存在する。

###### Level
- 
  DEBUG < INFO < WARN < ERROR < FATAL

##### Appender
- 
  ログの出力先を指定するもの。

- addAppender()
  AppenderはaddAppender()メソッドでLoggerにセットすr。鵜
  各Loggerにセットすることで、それぞれのログを様々な宛先に出力することができる。

###### org.apache.log4j.Appender Interface
- 
  出力先を指定する際に使用するクラスは、すべてorg.apache.log4j.Appenderインターフェースを実装している。

- 出力先設定
  |-----------------------------------------------------+-----------------------------|
  | class                                               | output                      |
  |-----------------------------------------------------+-----------------------------|
  | org.apache.log4j.ConsoleAppender                    | コンソール                  |
  | org.apache.log4j.DailyRollingFileAppender           | ファイル                    |
  | org.apache.log4j.FileAppender                       | 〃                          |
  | org.apache.log4j.RollingFileAppender                | 〃                          |
  | org.apache.log4j.WriterAppender                     | Java.io.Writer              |
  | org.apache.log4j.net.JMSAppender                    | JMS（Java Message Service） |
  | org.apache.log4j.net.SMTPAppender                   | 電子メール                  |
  | org.apache.log4j.net.SocketAppender                 | リモートソケットサーバ      |
  | org.apache.log4j.net.SyslogAppender                 | リモートUnixSyslogデーモン  |
  | org.apache.log4j.nt.NTEventLogAppender              | WindowsNTのイベント・ログ   |
  | org.apache.log4j.AsyncAppender                      | その他                      |
  | org.apache.log4j.performance.NullAppender           | 〃                          |
  | org.apache.log4j.varia.ExternallyRolledFileAppender | 〃                          |
  |-----------------------------------------------------+-----------------------------|
  
####### org.apache.log4j.WriteAppender Class

####### org.apache.log4j.ConsoleAppender Class

####### org.apache.log4j.FileAppender Class

####### org.apache.log4j.RollingFileAppender Class
####### org.apache.log4j.DailyRollingFileAppender Class
##### Layout
- 
  ログの出力フォーマットを指定するもの。
  Layoutクラスは抽象クラスで、具体的なフォーマット設定は以下のクラスを利用する。

###### org.apache.log4j.Layout Class
- 
  |--------------------------------+--------------------------------------------------------------------------------------------|
  | class                          | format                                                                                     |
  |--------------------------------+--------------------------------------------------------------------------------------------|
  | org.apache.log4j.SimpleLayout  | 単純なレイアウト                                                                           |
  | org.apache.log4j.PatternLayout | ユーザが指定したフォーマット                                                               |
  | org.apache.log4j.HTMLLayout    | HTMLのテーブル形式                                                                         |
  | org.apache.log4j.TTCCLayout    | 時間とスレッド、カテゴリとネスト化診断コンテキスト情報、そして名前から成り立つフォーマット |
  |--------------------------------+--------------------------------------------------------------------------------------------|


####### org.apache.log4j.SimpleLayout Class

####### org.apache.log4j.PatternLayout Class
####### org.apache.log4j.TTCCLayout Class
####### org.apache.log4j.HTMLLayout Class
#### Configuration File
- 
  「key=value」の形で記述。

##### Properties
###### Logger
- 
  ログ出力レベルと、使用するAppenderの名前を設定する。Appednerは名前だけでよい。
  Appenderは複数設定することができ、既にRootLogerで優先度が設定されている場合継承できる。
  継承する場合はINHERITEDをログ出力レベルに記載する。

- Format
  #RootLogger
  log4j.rootLogger=(出力レベル),appenderName1,appenderName2,...
  
  #Logger
  log4j.logger.logger_name=[ログ出力レベル|INHERITED], appenderName1, appenderName2, ...

- Sample
  #sampleLogger
  log4j.logger.sampleLogger=ERROR,A1 #sampleLoggerにA1という名前のAppenderを設定

###### Appender
- 
  Appenderの設定を行う。使用するAppenderとそのオプションの値を設定することができる。

- Format
  #APPENDERの設定
  log4j.appender.appender_name=appender_class_name
  #Option設定
  log4j.appender.appender_name.option1=value1
    ...
  log4j.appender.appender_name.optionN=valueN

- Sample
  #APPENDERの設定
  log4j.appender.A1=org.apache.log4j.ConsoleAppender
  #PatternLayout設定
  log4j.appender.A1.layout=org.apache.olg4j.PatternLayout
  log4j.appender.A1.layout.ConversionPattern=%-4r [%t] %-5p %c - %m%n

###### 利用
- 
  設定ファイルを使用するには、org.apache.log4j.PropertyConfiguratorクラスを使用する。

##### XML
- 
  [[http://www.techscore.com/tech/Java/ApacheJakarta/Log4J/8/][

#### Link
- 
  [[http://www.techscore.com/tech/Java/ApacheJakarta/Log4J/index/][Log4J - TECHSCORE]]
## Link
- [[http://changineer.info/server/logging][ログ管理方法 - ネットワークチェンジニアとして]]
