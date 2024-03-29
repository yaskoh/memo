# IIS
## FTP
### 構築手順
- https://technet.microsoft.com/ja-jp/library/hh831655(v=ws.11).aspx
### Memo
#### Logの形式
- [[https://oshiete.goo.ne.jp/qa/8939779.html][WindowsServer2008(IIS7.5)のFTPサイトはIISログ形式(日本時間)が不可？ - 教えて!goo]]
  FTP サーバーでサポートしているログ形式は W3C のみである、と明記されており、UTC で記録するのは仕様となる
- [[https://docs.microsoft.com/ja-jp/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831624(v=ws.11)?redirectedfrom=MSDN][FTP Logging - Mcrosoft Docs]]
  This version of the FTP server only supports W3C Extended Log File format.
#### ステータスコード
- https://support.microsoft.com/ja-jp/help/969061/the-ftp-7-0-status-codes-in-iis-7-0
## Settings
### Server Level
### Site Level
#### Actions
##### Add Website
##### Set Website Defaults
##### Add FTP Site
##### Set FTP Site Defaults
####### General
####### Behavior
######## Connections
######## Credential Caching
######## File Heading
### WebSite Sites
#### Actions
### FTP Sites
#### Actions
##### Bindings
##### Basic Settings
##### Manage FTP Site
- Restart
- Start
- Stop
###### Advanced Settings
## Feature View
### IIS
### FTP
#### FTP Authentication
#### FTP Authorization
#### FTP Current Sessions
#### FTP Directory Browsing
- ディレクトリ参照オプション
##### Directory Listing Style
- MS-DOS
  MS-DOSに準拠した方法で内容を表示
- UNIX
  UNIXに準拠した方法でディレクトリを表示
##### Directory Listing Options
- Virtual directories / 仮想ディレクトリ
- Available bytes / 空き容量
- Four-digit years / 西暦を4桁で表示
#### FTP Firewall Supports
- Configure port ranges and external IP addresses for FTP connections
#### FTP IP Address and Domain Restrictions
#### FTP Logging
- Configure how IIS logs requests on the FTP server
##### One log file per:
- Site
- Server
##### Log File
###### Select W3C Fields
###### Directory
###### Encoding
##### Log File Rollover
- Schedule
  - Hourly
  - Daily
  - Weekly
  - Monthly
- Maximum file size
- Do not create new log files
#### FTP Logon Attempt Restrictions (Server Level)
- Enable FTP Logon Attempt Restriction
#### FTP Messages
- FTPサイトに接続した場合に送信されるメッセージの設定
##### Message Behavior
- Suppress default banner
  規定のバナーを表示しない
- Support user variables in messages
  メッセージ内のユーザー変数をサポートする。
  - Vars
    - %BytesReceived% : サーバーからクライアントに送信されたバイト数
    - %BytesSent% : クライアントからサーバーに送信されたバイト数
    - %SessionID% : 現在のセッションの一意の識別子
    - %SiteName% : ホストしているFTPサイトの名前
    - %UserName% : ログオンしているユーザーのアカウント名
- Show detailed messages for local requests
  
##### Message Text
- Banner:
- Welcome:
- Exit:
- Maximum Connections:
#### FTP Request Filtering
- 要求フィルター
##### File Name Extensions
##### Hidden Segments
##### Denied URL Sequences
##### Commands
#### FTP SSL Settings
#### FTP User Isolation
- ユーザーを分離するようにFTPサーバーを構成できる。
  これにより、同じFTPサイトの他のユーザーのディレクトリにアクセスできなくなる。
##### Do not isolate users / ユーザーを分離しない
###### FTP root directory
- すべてのFTPセッションが、FTPサイトのルートディレクトリで開始される
###### User name directory
- フォルダーが存在する場合、すべてのFTPセッションが、現在のログオンユーザーと名前が同じ物理または仮想ディレクトリで開始される。
##### Isolate users / ユーザーを分離する
###### User name directory (disable global virtual directories)
- FTPユーザーアカウントと同じ名前の物理または仮想ディレクトリに分離
###### User name physical directory (enable global virtual directories)
- FTPユーザーアカウントと同じ名前の物理ディレクトリに分離
###### FTP home directory configured in Active Directory
- Active Directoryアカウント設定で構成されているホームディレクトリにユーザセッションを分離
###### Custom
- 高度な機能
##### Link
- [[https://technet.microsoft.com/ja-jp/library/dd939054.aspx][FTP7.5 ユーザー分離の構成 - TechNet]]
- [[https://technet.microsoft.com/ja-jp/library/dd722768(v=ws.11).aspx][FTPユーザーの分離 - Technet]]
### Management
#### Configuration Editor
## Security
### Memo
- http://www.atmarkit.co.jp/fwin2k/operation/iisftpsec01/iisftpsec01_01.html
- 匿名ユーザーのアクセスを禁止する
- 接続元IPでアクセスを制限する
- 最大同時接続数を最小限にする

