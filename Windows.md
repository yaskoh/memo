# Windows
## Version
### Windows 7
### Windows 10
#### Tips
##### バージョン情報の確認
- Windows -> 設定 -> システム -> バージョン情報
- Windows -> Settings -> System -> Version
### Windows Server 2012 R2
#### Server Manager サーバーマネージャー
##### Add Roles and Features Wizard
- Role-based or feature-based installation / 役割ベースまたは機能ベースのインストール
- Remote Desktop Services installation / リモートデスクトップ サービスのインストール
## Shell
### cmd
#### Command
##### Internals / 内部コマンド
- helpで確認
###### assoc
###### attrib
###### break
###### bcdedit
###### cacls
- 
  ファイルやフォルダに対して設定されているACLの内容を確認したり、
  変更するために利用するコマンドラインのツール。

###### call
###### cd
###### chcp
###### chdir
###### chkdsk
###### chkntfs
###### cls
- 画面上の文字を消去する。
  POSIX系shellだとclearかCtr+l。

###### cmd
###### color
###### comp
###### compact
###### convert
###### copy
####### Options
######## /A
######## /B
######## /D
######## /V
- 新しいファイルが正しく書き込まれたか検査します。
######## /N
######## /Y
- 受け側既存ファイルを上書きする前に確認のメッセージを表示しません。
######## /-Y
- 受け側既存ファイルを上書きする前に確認のメッセージを表示します。
###### date
###### del
###### dir
###### diskcomp
###### diskcopy
###### diskpart
###### doskey
###### drivequery
###### echo
###### endlocal
- バッチプログラムで一時的に変更した環境変数のローカル化を終了する。
###### erase
###### exit
###### fc
- fc (option) [file1] [file2]
  2つのファイルを比較して相違点を表示する。
- /L
  テキストファイルとして比較する。
- /B
  バイナリファイルとして比較する
- /A
  最初と最後の行のみ表示する
- /LB(行数)
  (行数)以上続いた場合に比較をやめる。

###### find
###### findstr
###### for
- FOR %変数 IN (セット) DO コマンド [コマンドパラメーター]
  指定されたコマンドをファイル セットの各ファイルに対して実行する
  - %変数 : 単一文字の置き換え可能なパラメーターを指定
  - (セット) : ファイル セットを指定する。ワイルドカードを使用可能。
  - コマンド : 各ファイルごとに実行するコマンドを指定
  - コマンドパラメーター : 指定されたコマンドのパラメーターまたはスイッチを指定する
- バッチプログラムでは、%変数の代わりに%%変数を使用する。
####### Switch
######## /D
######## /R
######## /L
######## /F
- Format
###### format
###### fsutil
####### Commands1
######## 8dot3name
######## behavior
- ファイルシステムの動作の制御
######### Commands2
########## query
- パラメータを照会
########### Options
############ AllExtChar
############ BugcheckOnCorrupt
############ Disable8dot3
############ DisableCompression
############ DisableEncryption
############ DisableLastAccess
############ EncryptPagingFile
############ MftZone
############ MemoryUsage
############ QuotaNotify
############ SymlinkEvaluation
- シンボリックリンクの許可設定を表示
############ DisableDeleteNotify
########## set
- パラメータを変更
########### Options
############ SymlinkEvaluation
- 許可設定を変更。
  R2R:1でRemote to remoteのlinkを許可とする。
######## dirty
######## file
######## fsinfo
######## hardlink
######## objectid
######## quota
######## repair
######## reparsepoint
######## resource
######## sparse
######## transaction
######## usn
######## volume
###### ftype
###### goto
###### gpresult
###### graptbal
###### help
- 
  コマンドの一覧を取得できる。
  内部コマンドも外部コマンドもあると思われる。

###### icals
###### if
####### defined
- 環境変数が設定されているかチェックするには、DEFINEDを使う。
- ex) 
    IF DEFINED ENV echo OK
- 
  [[http://orangeclover.hatenablog.com/entry/20110127/1296135692][バッチファイル/コマンドプロンプトで環境変数が設定されているかチェックする方法]]

####### Link
- tmp
  - [[http://qiita.com/sawa_tsuka/items/8edf3d3d33a0ae86cb5c][.bat（バッチファイル）のifコマンド解説。 - Qiita]]
###### label
###### md
###### mkdir
###### mklink
- MKLINK [[/D] | [/H] | [/J]] link target
  シンボリックリンクを作成する。
####### /D
- ディレクトリのシンボリックリンクを作成する。
  デフォルトはファイルのシンボリックリンクを作成する。
####### /H
- シンボリックリンクでなくハードリンクを作成する
####### /J
- ディレクトリジャンクションを作成する。
###### mode
###### more
###### move
###### penfiles
###### path
###### pause
###### popd
###### print
###### prompt
###### pushd
###### rd
###### recover
###### rem
###### ren
###### rename
###### replace
###### rmdir
###### robocopy
- Windows の堅牢性の高いファイルコピー
- フォルダを同期するためのコマンド。
  Robust File Copyの略で、堅牢で確実なファイル・コピーという意味を持つ。
  コマンドラインでなくGUIから使いたい場合は、richcopyが利用できる。

####### Usage
- robocopy source dest files (option)
  sourceがコピー元、destがコピー先、filesでコピーするファイルを指定する。
  filesはワイルドカード指定可能で、規定値は*.*。
####### Options
######## Copy Options
######### /S
- サブディレクトリをコピーするが、空のディレクトリはコピーしない。
  
######### /E
- 空のサブディレクトリを含むサブディレクトリをコピーする。

######### /LEV:n
- コピー元ディレクトリツリーの上位nレベルのみをコピーする。

######### /PURGE
- 既にコピー元に存在しないコピー先のファイル・ディレクトリを削除する
######### /MIR
- 2つのフォルダを同期させる。
  destファイルにsourceにないファイルがあれば削除し、古いファイルがあれば上書きされる。
  /purgeと/Eを組み合わせた挙動と同じ。

######### /COPY:コピーフラグ
- ファイルにコピーする情報
  D:データ、A:属性、T:タイムスタンプ
######### /XJ
- ジャンクションポイントを外す。
  シンボリックリンクも除いてくれる模様(2018/4, Win7/2012R2)
######### /XJD
- ディレクトリのジャンクションポイントを外す
######### /XJF
- ファイルのジャンクションポイントを外す
######## File Selection Options
######## Retry Options
######## Log Options
######### /TS
- 出力にコピー元ファイルのタイムスタンプを含める

######### /FP
- 出力にファイルの完全なパス名を含める

######### /BYTES
- サイズをバイトで出力する

######### /TEE
- コンソールウィンドウとログファイルに出力する

######## Job Options
####### Memo
######## 
- [[http://www.atmarkit.co.jp/ait/articles/1309/27/news116.html][Windowsのrobocopyコマンドでコピーするファイルの種類を選択／変更する - @IT]]
###### set
- SET [変数名=[文字列]]
  環境変数を表示、設定、または削除する。

- 現在の環境変数を表示するには、パラメータを指定せず"SET"のみ入力する。
- 変数名のみを指定して実行すると、プレフィックスが一致するすべての変数の値が表示される。
  例えば、"SET P"とすると、'P'で始まるすべての変数が表示される。
####### Switch スイッチ
######## /A
- SET /A 式
  等号の右側の文字列が、評価する数式であることを指定する。
######## /P
- SET /P 変数=[プロンプト文字列]
  ユーザによって入力された入力行を変数の値として設定できるようにする。
###### setlocal
- 
  バッチファイルでの環境変数のローカル化を開始する。
  以前の設定を復元するにはENDLOCALを実行する。
  バッチスクリプトが終了すると、そのバッチスクリプトで発行されたSETLOCALコマンドに対し、
  暗黙のENDLOCALが実行される。

###### sc
- Service Control
  SC is a command line program used for communicating with the Service Control Manager and services.
- Usage:
  sc <server> [command] [service name] <options>...

####### Commands
######## query
- サービスの状態を照会したりサービスの種類ごとに状態を列挙したりする。
######## queryex
######## start
######## pause
######## interrogate
######## continue
######## stop
######## config
- 設定を変更する
  sc config ServiceName option= value
######### Options
########## start
- values
  - auto
  - boot
  - system
  - demand : manualの意
  - disabled
  - delayed-auto : 遅延自動起動
########## password
########## error
######## sdshow
- Displays the service's security descriptor in SDDL format.
  サービスセキュリティ記述子をSDDL形式で表示する
- Usage:
  sc <server> sdshow <service name> <showrights>
######## sdset
- Sets a service's security descriptor.
###### schtasks
###### shift
###### shutdown
###### sort
###### start
###### subst
###### systeminfo
###### tasklist
###### time
###### title
###### tree
###### type
###### ver
###### verify
###### vol
###### xcopy
###### wmic
- System Programのwbemも参照。
##### Externals / 外部コマンド
- "System Programs"等を参照
##### ネットワークコマンド
###### arp
- 
  OSが管理しているAPRテーブルを表示したり削除したりするコマンド。
  ARPテーブルは、IPアドレスとMACアドレスを関連付けた一覧。

- -a
  ARPテーブルを表示する

- -d IPアドレス
  指定したIPアドレスのエントリーを削除する

###### getmac
- 
  ネットワークにつながっている別のWindowsのMACアドレスを調べる。
  getmacを使うには管理者権限が必要なので、

- /s target /u username /p password
  サーバ名、管理者のユーザ名、パスワードを指定して、マックアドレスを確認する。

###### hostname
- 
  現在のホスト名を出力する

###### ipconfig
- 
  コンピュータのネットワーク設定情報を表示する

- /all
  すべてのNIC情報を表示する

- /release
  すべてのNICのIPv4のIPアドレスを開放する

- /renew
  すべてのNICのIPv4のIPアドレスを更新する

- /displaydns
  DNSリゾルバのキャッシュを表示する

- /flushdns
  DNSリゾルバのキャッシュをクリアする

###### nbtstat
- 
  Windowsネットワークを管理するためのコマンド。
  NBTとは"NetBIOS over TCP/IP"のこと。

- -c
  キャッシュしている情報を表示する

- -R
  キャッシュ内容をクリアする

- -n
  自分自身の情報を表示する

###### net
- 
  ネットワーク関係の設定を行ったり、現在の状態を表示させたりするために使われるコマンド。
  サブコマンドをいれずに使うとサブコマンド一覧が表示される。
  [[http://www.atmarkit.co.jp/fwin2k/win2ktips/258netcommand/netcommand.html][netコマンドの使い方 - @IT]]
  [[http://pasofaq.jp/windows/command/net7.htm][NETコマンド(Windows 7)]]

####### net accounts

####### net computer

####### net config
- サーバ・サービスやワークステーション・サービスに関する情報の表示/設定
######## net config server
######## net config workstation
####### net continue
- 
  サービスの再開

####### net file
- 
  使用されているファイルの一覧の表示/強制終了。
  net shareで公開されたリソースのうち、どのようなファイルが実際に外部マシンで利用されているか調べる。

####### net group

####### net help
- 
  各コマンドの使い方の表示

####### net helpmsg
- 
  エラー番号に対する詳しいエラーメッセージの表示

####### net name
- 
  NetBIOS名の表示・追加。
  新しく追加された名前はnet sendコマンドの宛先として利用できる。

####### net pause
- 
  サービスの一時停止

####### net print

####### net send
- 指定されたユーザやコンピュータに対するメッセージの送信

####### net session
- 
  ユーザアカウントに対するログオンやパスワードの要件の表示/強制終了

####### net share
- 
  共有リソースの公開/公開停止。ローカルのリソースを公開して、外部のマシンでnet useできるようにする。

####### net start
- サービスの表示/開始

####### net statistics
- 
  ネットワーク・プロトコルやリソースの公開/共有サービスに対する統計情報の表示

####### net stop
- 
  サービスの停止

####### net time
- 
  時間情報の表示や外部との同期

####### net use
- 
  共有リソースの使用/解除。net shareされたネットワーク上のリソースをローカルで使う場合に使う。

####### net user

####### net view
- 
  リソースが共有されているマシンの列挙や、特定のマシンが公開している共有リソースの一覧を調べる

###### netsh
- 
  netsh（ネットシェル）は、コンピュータのネットワーク設定情報を書き換えるコマンド。
  対話型と結果表示型、どちらも可能。
  Win純性のみでパケットのキャプチャを取得する場合にも利用。

- ?
  コマンド一覧が表示される

- exit
  終了する

####### Commands
######## ?
######## add
######## Advfirewall
######## bridge
######## delete
######## dump
######## exec
######## firewall
######### ?
######### add
- adds firewall configuration
######### delete
######### dump
######### help
######### set
######### show
######## help
######## http
######## trace
- パケットキャプチャを取得する。
  Microsoft Message Analyzerで解析が可能。

###### netstat
- 
  コンピュータの通信状況を一覧表示する。
  どのコンピュータとどんなプロトコルを使って何番ポートで通信しているかわかる。
  標準設定では、相手のコンピュータはホスト名、プロトコルはウェルノウンポートのプロトコル名で表示される。

####### Options
######## -a
- すべての接続とリッスンポートを表示する
######## -n
- 実行結果にコンピュータやプロトコル名を使わず、IPアドレスとポート番号で表示する
######## -o
- Displays the owning process ID associated with each connection.
######## -s
- プロトコルごとの統計を表示する。

###### nslookup
- DNSサーバと通信して名前解決の「正引き」や「逆引き」を行うコマンド。
  IPアドレスかドメイン名を入力する。
- Usage
  - nslookup [-opt ...]

###### pathping
- 
  ノード間のネットワークの状態を確認する。
  pingとtracertを組み合わせたようなイメージ。

###### ping
- 
  ICMPのサブコマンドechoを使った、単純なパケット通信テストプログラム。
- -t
  中断されるまでホストをpingする
- -n 要求数
  送信するエコー要求数を設定する

###### route
- ROUTE [-f] [-p] [-4|-6] command [destination] [MASK netmask] [gateway] [METRIC metric] [IF interface]
  ルーティングテーブルに関する情報を表示、または変更する。

####### Options
######## -f
- デフォルトゲートウェイを含む全ての静的ルーティング情報を消去する。

######## -p
- Addコマンドと併用された場合、システムの再起動後もルートが維持される。
######## -4
- IPv4の使用を強制する
######## -6
- IPv6の使用を強制する
######## command
- 以下のいずれか
  - PRINT
  - ADD
  - DELETE
  - CHANGE
####### Commands
- add|change|delete 宛先アドレス [mask ネットマスク] ゲートウェイ
  指定したルーティング情報を追加、変更、消去する。

- print
  ルーティング情報を表示する。

###### telnet
- 
  ネットワーク越しに別のコンピュータを操作するコマンド。
  Vista以降はコントロールパネルで有効化する必要がある。
  平文で送信されるので、使う範囲はLAN内に限定するべき。

###### tracert
- 
  実行するコンピュータから通信相手までの経路上にあるルータを一覧表示するコマンド。
  pingと同様ICMPのエコー要求・応答を利用している。
  TTLが1からスタートし、1つずつ大きくして経路上のルータを一覧表示する機能。

###### 外部link

- [[http://itpro.nikkeibp.co.jp/article/COLUMN/20060224/230618/][管理者必見！ネットワーク・コマンド集]]
- [[http://itpro.nikkeibp.co.jp/article/COLUMN/20131219/525889/][最重要ネットコマンド10]]
- [[http://blog.asial.co.jp/1157][使えると便利なWindowsネットワークコマンド]]

##### Linuxとの比較
- 
  |-------------+---------|
  | Linux shell | Win cmd |
  |-------------+---------|
  | cat         | type    |
  | clear       | cls     |
  | cp          | copy    |
  | ls          | dir     |
  | mv          | move    |
  | pwd         | cd      |
  | rm          | del     |
  |-------------+---------|

#### Batch
##### 実行元フォルダに移動
##### IF文の複数条件指定
- 

  ANDやORに相当する機能はない。ただし、AND条件であればIF文を並べて記述できる。
  ex:) IF %A% == 1 IF %B% == 2 (
         REM 1かつ2のAND条件
     ) ELSE (
         それ以外
     )
- 
  [[http://capm-network.com/?tag=Windows%E3%83%90%E3%83%83%E3%83%81%E3%83%95%E3%82%A1%E3%82%A4%E3%83%AB%E5%88%B6%E5%BE%A1%E6%A7%8B%E6%96%87][CapmNetwork Windowsバッチファイル制御構文]]

##### 処理の途中で改行を入れる
- 
  バッチファイルでのエスケープシーケンスは「^(hat)」なので、
  改行前に^をおくと複数行を1行として扱える。
  ex:) IF %ABCDEFGHIJKLM% ==1 ^
       IF %NOPQRSTUVWXYZ% ==2 (
         REM 処理
     )
- [[http://orangeclover.hatenablog.com/entry/20100810/1281450669][みちしるべ バッチファイルで長い1行の処理を改行を入れて複数行に分けて書きたい]]
- [[http://pf-j.sakura.ne.jp/program/dos/doscmd/str_circumflex.htm][ProgrammingField DOSコマンド一覧 ^(ハット記号)]]

##### 環境変数の消し方
- 
  "SET 変数="とする。
  たとえば変数XYZを初期化したければ、"set XYZ="でよい。

- [[http://orangeclover.hatenablog.com/entry/20090826/1251293551][みちしるべ 3.環境変数 (1)環境変数の使い方 〜意外に削除の仕方はしらない人が多い〜 【コマンドプロンプト、バッチファイルを使わなきゃならなくなった人向けのメモ】]]

##### バッチでの標準入力待ち
- 
  "SET /P 変数=出力文字列"、という感じの構文。
  たとえば"set /P var=好きな英数字を入力してください。"とすると、
  "好きな英数字を入力してください。"と画面に出力された後入力待ちになり、
  改行するまでの文字列がvarに格納される。
  バッチファイルでユーザーに入力させた値を取得する

##### Batchで日時を入力
- 
  %date%, %time%を使えばよいが、%time%は一桁時のときスペースを入れてくるため、
  スペースを0に置換する等の手段を取る必要がある。
  ex: echo %time% -> " 9:20:30.93"

- ex
  rem ***日時定義***
  set today=%date:/=%
  set time_tmp=%time: =0%
  set now=%today%%time_tmp:~0,2%%time_tmp:~3,2%%time_tmp:~6,2%

##### バッチ実行を一時停止/sleepする
- Linuxのsleepなどと同じような"待ち"をしたい場合、timeout.exeを使う。
  "timeout 60"とすると60秒間キー入力を待ち受け、何もなければ60秒後に次のコマンドへ移る。
- http://www.atmarkit.co.jp/ait/articles/1206/08/news137.html
  
##### for文
###### 無限ループ
- for /l %%i in (0,0,0) do (
    echo loop
  )
- http://d.hatena.ne.jp/simply-k/20100821/1282490379
##### エラーレベルの確認
- 表示
  echo %errorlevel%
- 条件分岐
  if errorlevel [number] [command]
- https://jj-blues.com/cms/command-errorlevel/
### WSH
- Windows Script Host
- Windows環境でスクリプトを実行するための環境。
  標準では、VBScriptとJScriptを利用できる。
#### Programs
##### cscript.exe
##### wscript.exe
#### Objects
##### Basic Objects
###### WScript
###### WshArguments
###### WshController
###### WshEnvironment
###### WshNetwork
###### WshShell
###### WshShortcut
###### WshSpecialFolders
###### WshUrlShortcut
###### FileSystemObject
##### Win OS Objects
###### ADODB.Connection
###### ADODB.Stream
###### XMLHTTP
###### CDO.Message
###### InternetExplorer.Application
###### Shell.Application
###### ADSI (Active Directory Service Interfaces)
###### WMI (Windows Management Instrumentation)
#### Memo
##### 文字コード
- UTF-8では実行時にエラーが出た。設定方法はあるかもしれない。
  Shift_JISにしたところ問題なく実行できた。
#### Link
- [[https://msdn.microsoft.com/ja-jp/library/cc364455.aspx][Windows Script Host - Developer Network]]
- [[http://www.atmarkit.co.jp/ait/articles/0606/02/news116.html][基礎解説 演習方式で身につけるチェック式WSH超入門 - @IT]]
- [[http://news.mynavi.jp/articles/2009/01/25/wsh/][ゼロからはじめるWindows Script Host - 基本編 - マイナビニュース]]
### PowerShell
- [[file:PowerShell.org][PowerShell.org]]
### WSL
#### General
##### Tips
###### WSLとWindowsファイルシステム間のアクセス
- WSL -> Windowsには、/mnt/DriveLetterからアクセス可能。
- Windows -> WSLは、\\wsl$で確認ができるらしい。が、現時点では試したところ不可。
  - https://qiita.com/quzq/items/1096c638c0d86795be13
###### ホームフォルダを変更
- passwdの設定で、パスを/home/usernameから/mnt/c/Users/usernameに変更するといろいろと便利。
  - sudo vim /etc/passwd
###### パスワードを忘れたとき
- cmdなどで、"wsl -u root"を実行すると、rootユーザでログインできる。
  そこで"passwd username"などをして変更すればよい。
- [[https://qiita.com/iszk/items/557cd99739ea6cc82941][wsl でパスワードを忘れてしまった際の対処 - Qiita]]
#### debian
#### ubuntu
### WSL2
### MSYS2
#### pacman
- [[file:Linux.org][Linux.org(PackageManagement/pacman参照)]]
#### Commands
##### cygpath
- Convert Unix and Windows format paths, or output system path information.
- Usage:
  - cygpath (-d|-m|-u|-w|-t TYPE) [-f FILE] [OPTION]... NAME...

###### Options
####### Output
######## -d, --dos
######## -m, --mixed
######## -M, --mode
######## -u, --unix
- default
  print Unix form of NAMEs
######## -w, --windows
######## -t, --type TYPE
#### Memo
##### PATHを引き継ぐ
- Windowsの環境変数"MSYS2_PATH_TYPE"にinheritを設定すると、設定が引き継がれる。
  [[http://chirimenmonster.github.io/2016/05/09/msys2-path.html][MSYS2でPATHが引き継がれない - めもらんだむ]]
##### ファイルパスの扱い
- Windows式のパスをそのまま入力すると、エスケープが処理されcdなどに失敗するが、
  ""(double quote)で囲って利用すると問題なく利用可能。
##### /home/userを上書き
- $HOME設定、/etc/passwd設定をしているものの、
  sshで~/.sshでなく/home/username/.sshが読まれていたので、fstabでmountする。
  - ex) C:/Users/username /home/username ntfs override,binary,auto 0 0
#### Link
- [[https://msys2.github.io/][MSYS2 installer]]
- [[https://sourceforge.net/p/msys2/wiki/Home/][MSYS2 - sourceforge]]
- [[https://github.com/Alexpux/MSYS2-packages][Alexpux/MSYS2-packages - github]]
### Cygwin
#### Command
##### Cygutils
###### cygstart
- start a program or open a file or URL
  
## System Programs
- [[file:Windows_SystemPrograms.org][Windows_SystemPrograms.org]]
## Files
### pagefile.sys
- C:\pagefile.sys
  paging file.
- [[http://lifehacker.com/5426041/understanding-the-windows-pagefile-and-why-you-shouldnt-disable-it][Understanding the Windows Pagefile and Why You Shouldn't Disable It - lifehacker]]

### hiberfil.sys
- C:\hiberfil.sys
  when hybernation is start, data on memory is moved this file.
## Settings
### Control Panel
#### Win7
##### システムとセキュリティ
###### 電源オプション
- プラン
  - バランス
  - 省電力
  - 高パフォーマンス
    ⇒パフォーマンスを優先、電力の消費が増える可能性あり。
##### ユーザーアカウント
###### 資格情報の管理
####### 汎用資格情報
- 
  [[http://news.mynavi.jp/special/2009/windows7/081.html][第6章 Windows 7のセキュリティとメンテナンス - パスワードを一括管理する「資格情報マネージャー」 - マイナビ ニュース]]

- command
  cmdkey (/list, /add)
  [[http://blog.putise.com/windows%E3%81%AE%E3%83%8D%E3%83%83%E3%83%88%E3%83%AF%E3%83%BC%E3%82%AF%E8%B3%87%E6%A0%BC%E6%83%85%E5%A0%B1%E3%83%A6%E3%83%BC%E3%82%B6%E3%83%BC%E5%90%8D%E3%83%BB%E3%83%91%E3%82%B9%E3%83%AF%E3%83%BC/][Windowsのネットワーク資格情報(ユーザー名・パスワード)を記憶させる方法。コマンドもある - puti se blog]]

##### フォント
- フォントをここに置くと適用される。
### Registry
#### Structure
##### HKEY_CLASSES_ROOT\
- HKCR
  HKEY_LOCAL_MACHINE\Softwareのサブキー。
  エクスプローラを使用してファイルを開くときに正しいプログラムを起動するための情報が格納される。
##### HKEY_CURRENT_USER\
- HKCU
  現在ログオンしているユーザの構成情報のルートが格納されている。
  現在ログオンしているユーザのフォルダ、画面の色、コントロールパネル設定などが格納される。
  HKEY_USERSのサブキー。
##### HKEY_LOCAL_MACHINE\
- HKLM
  コンピュータに固有の構成情報が格納される。
###### SOFTWARE\
####### Microsoft\
######## Windows\
######### CurrentVersion\
########## Policies\
########### System\
############ Audit\
############ kerberos\
############ UIPI\
############ dontdisplaylastusername
- サインイン時のユーザアカウント入力設定を変更する。
  ローカルセキュリティポリシーの「対話型ログイン: 最後のユーザー名を表示しない」と同じはず。
- 0: 普段と変わらない動作(？)
  1: ユーザアカウントの表示名、ドメインおよびユーザー名
  2: ユーザーアカウントの表示名のみ
  3: 一切の情報を表示しない
- [[https://news.mynavi.jp/article/windows-227/][Win 8編: サインイン時にユーザーアカウントの入力を求める - Windowsスマートチューニング - マイナビニュース]]
############ dontdisplaylockeduserid
- ロック時のユーザアカウント入力設定を変更する。
  ローカルセキュリティポリシーの「対話型ログイン: セッションがロックされているときにユーザーの情報を表示する」と同じはず。
  [[https://news.mynavi.jp/article/windows-229/][Win 8編: ロック画面解除時にユーザーアカウントの入力を求める - Windowsスマートチューニング - マイナビニュース]]
###### SYSTEM\
####### CurrentControlSet\
######## Control\
######### Keyboard Layout
######### Keyboard Layouts\
######## Services\
######### EventLog\
########## Application\
- イベントログソースが保存されている。
  Event Log Source
######### LanmanWorkstation\
########## Parameters\
########### EnableNetBTForSmb2
- Win8, Win8.1, Win2012, Win2012R2でSMBバージョン2を使用して通信したい場合に1とする。
  Win10では使用できない。
########### SMB1NATCompatibility
##### HKEY_USERS\
- HKU
  コンピュータ上に読み込まれた有効なユーザプロファイルがすべて格納される。
###### .DEFAULT\
####### Keyboard Layout\
######## Preload\
- local layoutが表示される
##### HKEY_CURRENT_CONFIG\
- 
  システムの起動時にローカルコンピュータにより使用されるハードウェアプロファイルに関する情報が格納されている。
#### Type
- REG_BINARY
  バイナリ値
- REG_SZ
  文字列値。改行を含まない固定長文字列
- REG_EXPAND_SZ
  展開可能な文字列値。環境変数で展開される文字列(%~%)
- REG_MULTI_SZZ
  複数行文字列。改行を含む文字列
- REG_DWORD
  DWORD(32bit)値。32bit符号なし整数値
- REG_QWORD
  QWORD(64bit)値。64bit符号なし整数値
#### Tips
##### Dvorak
- [[https://teratail.com/questions/44008][Win10 1607でDvorakにするレジストリがストアアプリに効かない - teratail]]
  Keyboard Layoutではうまく反映されない場合がでてくる（日本語キーボード限定かもしれない）。
  その場合に、①キーボードレイアウトを"英語キーボード(101/102キー)"に変更、②下記のようにキーボードレイアウトをレジストリエディタで変更。
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\i8042prt\Parameters\LayoutDriver JPN
  kbd101.dll -> kbddv.dll
  
###### old
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Keyboard Layouts\00000411
  KBDJPN.DLL -> KBDDV.DLL

- Win10利用時、ログインなどシステム利用時にQWERTYに戻ってしまう場合があったため、
  加えて"00000409"のUS分もKBDDV.DLLに変更した。
##### Default Settings
- HKEY_USERS\.DEFAULT\Keyboard Layout\Preloadに記載あり
  http://www.itprotoday.com/management-mobility/how-do-i-configure-default-keyboard-layout-during-login

##### caps<->ctrl
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Keyboard Layout\Scancode Map(なければ作成)
- 値のデータ
  00 00 00 00 00 00 00 00
  03 00 00 00 1D 00 3A 00
  3A 00 1D 00 00 00 00 00 
  
- 内容
  00 00 00 00 : header version[4byte]
  00 00 00 00 : flags[4byte]
  03 00 00 00 : エントリ数、terimnate含む
  3A 00 1D 00 : 3A 00 -> 1D 00
  1D 00 3A 00 : 1D 00 -> 3A 00
  00 00 00 00 : terminate

- Link
  [[http://uguisu.skr.jp/Windows/winCaps.html][「Caps」と「Ctrl」の入れ替え]]

##### Keycode(106 keyboard) Scancode
  - ESC : 00 01
  - TAB : 00 0F
  - CapsLock : 00 3A
  - 左Shift : 00 2A
  - 右Shift : 00 36
  - 左Alt : 00 38
  - 右Alt : E0 38
  - 左Ctrl : 00 1D
  - 右Ctrl E0 1D
  - Enter : 00 1C
  - Del : E0 53
  - Backspace : 00 0E
  - Win右 : E0 5C
  - Win左 : E0 5B
  - 半角/全角 : 0x29
  - 変換 : 0x79
  - 無変換 : 0x78

###### Link(Scancode)
- [[https://www.win.tue.nl/~aeb/linux/kbd/scancodes.html#toc1][Keyboard scancodes]]
- [[https://ja.wikipedia.org/wiki/%E3%82%B9%E3%82%AD%E3%83%A3%E3%83%B3%E3%82%B3%E3%83%BC%E3%83%89][スキャンコード - Wikipedia]]
- [[http://softwaretechnique.jp/OS_Development/Tips/scan_code_set1.html][Tips スキャンコード一覧 スキャンコードセット1 - 0から作るソフトウェア開発]]
- [[http://yanor.net/wiki/?Windows%2FTIPS%2F%E3%83%AC%E3%82%B8%E3%82%B9%E3%83%88%E3%83%AA%E3%82%92%E4%BF%AE%E6%AD%A3%E3%81%97%E3%81%A6CAPSLOCK%E3%81%AE%E5%89%B2%E3%82%8A%E5%BD%93%E3%81%A6%E5%A4%89%E6%9B%B4][レジストリを修正してCAPSLOCKの割り当て変更 - yanor.net]]

##### Key設定
###### PC
####### 2018/6/18
- 00 00 00 00 : header version[4byte]
  00 00 00 00 : flags[4byte]
  03 00 00 00 : エントリ数、terimnate含む
  1D 00 3A 00 : 左Ctrl で CapsLock を上書
  79 00 38 E0 : 変換 で 右Alt を上書
  00 00 00 00 : terminate
####### 2017/12/18
  00 00 00 00 : header version[4byte]
  00 00 00 00 : flags[4byte]
  04 00 00 00 : エントリ数、terimnate含む
  3A 00 1D 00 : CapsLock で 左Ctrl を上書
  1D 00 3A 00 : 左Ctrl で CapsLock を上書
  79 00 38 E0 : 変換 で 右Alt を上書
  00 00 00 00 : terminate
###### GDP Pocket
- 2017/8/26

#### Link
- [[https://support.microsoft.com/ja-jp/kb/256986][上級ユーザー向けの Windows レジストリ情報 - Microsoft]]
- [[http://www.akadia.com/services/windows_registry_tutorial.html][Windows Registry Tutorial]]

### Local Security Policy
#### Windows Server 2012 R2, Windows 7
##### Security Settings セキュリティの設定
###### Account Policies アカウント ポリシー
####### パスワードのポリシー
####### アカウント ロックアウトのポリシー
###### Local Policies
####### Audit Policy 監査ポリシー
####### User Rights Assighnment ユーザー権利の割り当て
####### Security Options セキュリティオプション
######## User Account Control: ユーザー アカウント制御:
######### Run all administrators in Admin Approval Mode 管理者承認モードですべての管理者を実行する
######## 対話型ログオン:
######### セッションがロックされているときにユーザーの情報を表示する
- レジストリでいうと、おそらく"HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\DontDisplayLockedUserId"
######### 最後のユーザー名を表示しない
- 
###### Windows Firewall with Advanced Security セキュリティが強化された Windows ファイアウォール
### Local Group Policy (gpedit.msc)
#### コンピュータの構成
##### ソフトウェアの設定
##### Windowsの設定
##### 管理用テンプレート
#### ユーザーの構成
##### ソフトウェアの設定
##### Windowsの設定
##### 管理用テンプレート
###### Windows コンポーネント
## Environment Variables
### Values
#### APPDATA
#### LOCALLAPPDATA
#### OS
#### PATH
#### PATHEXT
- 自動で補完される拡張子の情報
#### ProgramFiles
- %SystemDrive%\Program Files
#### SystemDrive
- ex) C:
#### SystemRoot
- ex)%SystemDrive%\Windows
#### USERPROFILE
- ユーザのプロファイルのパス
  ex) C:\Users\UserName, C:\Dcuments and Settings\UserName
#### windir
- ex)%SystemDrive%\Windows
### 動的な環境変数
#### %CD%
- 現在のディレクトリ文字列
#### %DATE%
- DATEコマンドと同じフォーマットの現在日付
#### %TIME%
- TIMEコマンドと同じフォーマットの現在時刻
#### %RANDOM%
- 0から32767の間の任意の10進数
#### %ERRORLEVEL%
- 現在のERRORLEVELの値
#### %CMDEXTVERSION%
#### %CMDCMDLINE%
#### %HIGHESTNUMANODENUMbER%
### Memo
#### Setting 設定
- setを使って、表示や設定を行う
#### Replace 置換
- ex)%PATH:文字列 1 = 文字列2%
  PATH環境変数に含まれるすべての"文字列 1"を"文字列 2"に置き換える。
#### 副文字列の指定
- ex)%PATH:~10,5%
  11番目(オフセット10)の文字から5文字だけを使う。
- ex)%PATH:~-10%
  最後の10文字が展開される
- ex)%PATH:~0,-2%
  最後の2文字以外のすべてが展開される
#### 遅延評価関数
- 実行時に環境変数を展開する。
  変数は感嘆符"!"で囲む。
## Structure
### Windows(%systemroot%)
#### system
- 16bit時代のsystemファイル。
#### System32
- 32bit OSであれば32bit、64bit OSであれば64bit用のシステムファイル。
##### Boot
##### com
##### CompatTel
##### Dism
##### drivers/
###### etc/
####### hosts
##### DriverStore
##### IME
##### migwiz
##### oobe
##### Speech
##### spool
##### sysprep
##### wbem/
##### WindowsPowershell/
##### winevt/
###### Logs/
- イベントログが保存される
####### Application.evtx
####### Security.evtx
####### System.evtx
#### SysWOW64
- 64bit OSで32bit OSをエミュレーションする際に利用される、32bit用のシステムファイル。
## Account
### Service
#### System (Local System)
- NT AUTHORITY\System
- 権限:Administratorsグループメンバと同等
- ネットワークアクセス時の資格情報:ローカルのコンピュータ・アカウント
- Memo:ドメイン参加していないサーバ間では、ネットワーク接続が許可されない可能性がある。
#### Local Service
- NT AUTHORITY\LocalService
- 権限:Usersグループメンバと同等
- ネットワークアクセス時の資格情報:匿名
- Win XPより追加。
#### Network Service
- NT AUTHORITY\NetworkService
- 権限:Usersグループメンバと同等
- ネットワークアクセス時の資格情報:ローカルのコンピュータ・アカウント
- Win XPより追加。
#### Link
- http://www.atmarkit.co.jp/ait/articles/0905/08/news095.html
## Functions
### Storage Space Direct, S2D
- Windows Server 2016に追加。
  フェールオーバークラスターに参加するノードのローカルディスクを1つの共有ボリュームとして構成することを可能とする機能。
- アーキテクチャ
  - コンバージド型
  - ハイパーコンバージド型
#### Link
- https://docs.microsoft.com/ja-jp/windows-server/storage/storage-spaces/storage-spaces-direct-overview
- https://mhiroblog.wordpress.com/2016/12/25/storage-space-direct-s2d-%E3%81%A8%E3%81%AF/
- https://docs.microsoft.com/ja-jp/system-center/vmm/s2d?view=sc-vmm-1801
- https://qiita.com/tsurun/items/b875ef74da6ce3e03b7d
### Server Roles & Features
- [[https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831669(v%3dws.11)]]
#### Server Roles
##### Active Directory Certificate Services
##### Active Directory Domain Services
###### 2012 R2
- Server Manager : Dashboard -> Add roles and features
  setting...
- Server Manager : AD DS
  setting...
- http://www.rem-system.com/post-671/
##### Active Directory Lightweight Directory Services
##### Active Directory Rights Management Services
##### Application Server
##### DTCP Server
##### DNS Server
##### File and Storage Services
###### File and iSCSI Services
####### File Server
####### iSCSI Target Server
####### iSCSI Target Storage Provider (VDS and VSS hardware providers)
###### Storage Services
##### Hyper-V
#### Features
##### IIS
- [[file:IIS.org][IIS.org]]
##### Failover Clustering
- MSCS / Microsoft Clustering Service
- WSFC / Windows Server Failover Cluster (Windows Server 2008以降)
###### Memo
####### Error: A weak event was created ...
- It's a bug, and just run a Windows Update.
  http://www.itprocentral.com/resolving-failover-cluster-error-message-a-weak-event-was-created-and-it-lives-on-the-wrong-object-there-is-a-very-high-chance-this-will-fail-please-review-and-make-changes-onyour-code-to-prevent-t/
###### Link
- [[https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831579(v=ws.11)][Failover Clustering Overview - Microsoft Docs]]
- [[http://blog.engineer-memo.com/2013/05/08/alwayson-%E3%82%92-azure-%E4%B8%8A%E3%81%AB%E6%A7%8B%E7%AF%89%E3%81%97%E3%81%A6%E3%81%BF%E3%82%8B-wsfc-%E3%81%AE%E6%A7%8B%E7%AF%89%E7%B7%A8/][AlwaysOn を Azure 上に構築してみる – WSFC の構築編 – SEの雑記]]
- [[https://msdn.microsoft.com/ja-jp/library/dn505754(v=ws.11).aspx][フェールオーバー クラスターを作成する - Developer Network]]
- [[https://techinfoofmicrosofttech.osscons.jp/index.php?MSCS%2FWSFC][MSCS/WSFC - Open棟梁Project - マイクロソフト系技術情報 Wiki]]

- [[https://blog.engineer-memo.com/2009/09/26/wsfc-%E3%81%AE%E3%83%AD%E3%82%B0%E3%81%AB%E3%81%A4%E3%81%84%E3%81%A6/][WSFC のログについて - SE の雑記]]

##### Multipath I/O
- [[https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc725907(v=ws.11)]]
##### RPC over HTTP Proxy
###### 設定
- ポート設定 :
  - 静的ポート : 135/tcp
  - 動的ポート : 49152-65535 (Windows Server 2008, Vista以降)
  - Link :
    - https://blogs.technet.microsoft.com/jpntsblog/2009/09/02/rpc/
    - http://www.dell.com/support/article/jp/ja/jpbsd1/sln283117/windows-server-rpc-server-unavailable-rpc%E3%82%B5%E3%83%BC%E3%83%90%E3%81%8C%E3%81%82%E3%82%8A%E3%81%BE%E3%81%9B%E3%82%93-%E3%82%A8%E3%83%A9%E3%83%BC%E3%81%AE%E3%83%88%E3%83%A9%E3%83%96%E3%83%AB%E3%82%B7%E3%83%A5%E3%83%BC%E3%83%86%E3%82%A3%E3%83%B3%E3%82%B0?lang=ja
    - https://support.microsoft.com/ja-jp/help/179442/how-to-configure-a-firewall-for-domains-and-trusts
- レジストリ :
  - HKLM\SYSTEM\CurrentControlSet\Control\Terminal Server\AllowRemoteRPC, value "1" means accept.
  - Link :
    - https://stackoverflow.com/questions/22155943/qwinsta-error-5-access-is-denied
###### Link
- https://blogs.technet.microsoft.com/jpntsblog/2009/09/02/rpc/
##### Windows PowerShell
## Shortcuts
### Windows 7
#### Win + f : エクスプローラ・"検索結果"を開く
#### Win + Ctrl + f : コンピュータを検索します
#### Win + e : エクスプローラ・"コンピュータ"を開く
#### Ctrl + Shift + Esc : Windowsタスクマネージャー
### Windows 10
#### Win + Ctrl + d : 仮想デスクトップの作成
#### Win + Ctrl + →(←) : 仮想デスクトップの切り替え
#### Win + Ctrl + F4 : 仮想デスクトップの削除
#### Win + v : クリップボード履歴
## License
### CAL / Client Access License
- Windowsサーバを利用するのに必要なライセンス。
  ユーザーCALとデバイスCALが存在する。
#### Link
- http://www.pg-direct.jp/blog/?p=7718
- http://www.pg-direct.jp/user_data/cal.php
- http://wa3.i-3-i.info/word12578.html
## Glossary
### System32 / SysWOW64
- System32には64bitプログラム用のファイル（現在使用しているもの）、
  SysWOW64には32bitプログラムを動かすための32bitバイナリが入っている。
  
### WOW64
- Windows 32-bit On Windows 64-bit
  64bit版のWindowsで、Win32アプリケーションを実行する、エミュレーションレイヤー・サブシステム。
  32bitのプログラムはシステムフォルダ(%systemroot%\System32)には直接アクセスできず、
  自動的に%systemroot%\SysWOW64へリダイレクトされる動作となる。配下には32bitのバイナリが用意されている。
  
### SafeSEH, SoftwareDEP
- http://resemblances.click3.org/?p=1449
### Network関連
#### SMB, Server message Block
- ネットワーク(LAN)上の複数のWinマシン間でファイル共有やプリント共有を行うためのプロトコルおよび通信サービス。
- 下位のプロトコルとしてNetBIOS、近年では更に下位のプロトコルとしてTCP/IPを利用する(NetBT, NetBIOS over TCP/IP)。
#### CIFS, Common Internet File System
- SMBを拡張し、Windows以外のOSやアプリケーションソフトでも利用できるように仕様を公開したもの。
  TCP/IPを基盤としており、NetBIOSは必要ではなくなっている。
### MMCスナップイン
- Windowsの管理用ツールの中身。
  外側はMicrosoft管理コンソール。「mmc.exe」がMicrosoft管理コンソールの本体。
  スナップインは、たとえば"eventvwr.msc"、"services.msc"など。
### セキュリティ周り
#### DACL
- Discretionary Access Control List 随意アクセス制御リスト
  リソースに対するアクセスの許可/拒否を制御する。
  ACEが1つ以上格納されているリスト。
#### SACL
- システムアクセス制御リスト
  リソースに対する監査を制御する
#### ACL
#### ACE
- Access Control Entry
#### SDDL
- Security Descriptor Definition Language
  セキュリティ記述子を表現するための汎用的な表記方法。
  DACLだけでなく監査の設定やDCOMのセキュリティ設定などで広く利用される。
##### Description
###### O:UserSID
###### G:GroupSID
###### D:DACLFlag(ACE strings)...
####### DACLFlag
######## P / SE_DACL_PROTECTED
- DACLが継承されたACEによって変更されないように保護する
######## AR / SE_DACL_AUTO_INHERIT_REQ
- DACLを子オブジェクトへ継承するように要求する
######## AI / SE_DACL_AUTO_INHERITED
- 継承によって作成されたDACLであることを示す
###### S:SACLFlag(ACE strings)...
###### ACE strings / ACE文字列
- format:
  (ACL Type;ACE Flag;Rights;Object GUID;Inherit Object GUID; Account SID)
  (ACLタイプ;ACEフラグ;権利;オブジェクトGUID;継承オブジェクトGUID;アカウントSID)
- ex:
  (A;CIOI;GRGWGXSD;;;PU)
- Memo
  - オブジェクトGUIDと継承オブジェクトGUIDはActive DirectoryのオブジェクトのACLのみで使われるもので、通常は空白。
####### ACEタイプ
- ACEの種類を表す
  |--------+---------------------+--------------------------|
  | 文字列 | タイプ名            | 意味                     |
  |--------+---------------------+--------------------------|
  | A      | SDDL_ACCESS_ALLAWED | アクセス許可             |
  | D      |                     | アクセス拒否             |
  | OA     |                     | オブジェクトアクセス許可 |
  | OD     |                     | オブジェクトアクセス拒否 |
  | AU     |                     | 監査                     |
  | AL     |                     | 警告                     |
  | OU     |                     | オブジェクト監査         |
  | OL     |                     | オブジェクト警告         |
  |--------+---------------------+--------------------------|

####### ACEフラグ
- ACEの継承に関する情報を表す
  |--------+----------+------------------|
  | 文字列 | タイプ名 | 意味             |
  |--------+----------+------------------|
  | CI     |          | コンテナ継承     |
  | OI     |          | オブジェクト継承 |
  | NP     |          | 伝播なし         |
  | IO     |          | 継承のみ         |
  | ID     |          | 継承             |
  | SA     |          | 監査成功         |
  | FA     |          | 監査失敗         |
  |--------+----------+------------------|

####### 権利 Rights
- Platform SDKに含まれるsddl.hやWinnt.h、APIの解説なども参照のこと
######## Generic access rights
- 
  |--------+----------+------|
  | 文字列 | タイプ名 | 意味 |
  |--------+----------+------|
  |        |          |      |
######## Standard access rights
- 
  |--------+----------+------|
  | 文字列 | タイプ名 | 意味 |
  |--------+----------+------|
  |        |          |      |

######## Directory service object access rights
- 
  |--------+----------+------|
  | 文字列 | タイプ名 | 意味 |
  |--------+----------+------|
  |        |          |      |
######## File access rights
- 
  |--------+----------+------|
  | 文字列 | タイプ名 | 意味 |
  |--------+----------+------|
  |        |          |      |
######## Registry key access rights
- 
  |--------+----------+------|
  | 文字列 | タイプ名 | 意味 |
  |--------+----------+------|
  |        |          |      |
######## Mandatory label rights
- 
  |--------+----------+------|
  | 文字列 | タイプ名 | 意味 |
  |--------+----------+------|
  |        |          |      |
####### オブジェクトGUID
- パスワードの変更やリセットなど、特別なタスクの実行を許可するための権利を表すオブジェクトのGUID文字列

####### 継承オブジェクトGUID
- ACEを継承するオブジェクトのGUIDを表す文字列

####### アカウントSID
- ACEの提供対象となるSIDを表す。
- https://msdn.microsoft.com/en-us/library/aa379602.aspx
  |--------+------------------------------|
  | 文字列 | タイプ名                     |
  |--------+------------------------------|
  | AN     | Anonymous                    |
  | AO     |                              |
  | AU     | Authenticated Users          |
  | BA     | Built-in Administrators      |
  | BG     |                              |
  | BO     |                              |
  | BU     | Built-in guests              |
  | CA     |                              |
  | CD     |                              |
  | CG     |                              |
  | CO     |                              |
  | DA     |                              |
  | DC     |                              |
  | DD     |                              |
  | DG     |                              |
  | DU     | Domain users                 |
  | EA     |                              |
  | ED     |                              |
  | HI     |                              |
  | IU     | Interactively logged-on user |
  | LA     |                              |
  | LG     |                              |
  | LS     | Local service account        |
  | LW     |                              |
  | ME     |                              |
  | MU     |                              |
  | NO     |                              |
  | NS     | Network service account      |
  | NU     |                              |
  | PA     |                              |
  | PO     |                              |
  | PS     |                              |
  | PU     |                              |
  | RC     |                              |
  | RD     |                              |
  | RE     |                              |
  | RO     |                              |
  | RS     |                              |
  | RU     |                              |
  | SA     | Schema administrators        |
  | SI     |                              |
  | SO     | Server operators             |
  | SU     | Service                      |
  | SY     | Local system                 |
  | WD     | Everyone                     |
  |--------+------------------------------|

##### Link
- [[https://msdn.microsoft.com/en-us/library/aa374928.aspx][ACE Strings - Microsoft Developer Network]]
- [[https://support.microsoft.com/ja-jp/help/914392/best-practices-and-guidance-for-writers-of-service-discretionary-acces][サービスの随意アクセス制御リストを作成する場合の推奨事項およびガイド - Microsoftサポート]]
- http://www.atmarkit.co.jp/ait/articles/0603/25/news016.html
### パス
#### UNC
- Universal Naming Convention
  Windowsネットワーク上で共有されている様々な資源の位置を表記する標準的な記法。
- 「\\コンピュータ名\共有名」のように記述する。
##### Link
- http://e-words.jp/w/UNC.html
- http://desktop.arcgis.com/ja/arcmap/10.3/tools/supplement/pathnames-explained-absolute-relative-unc-and-url.htm#GUID-A2A3F32B-D0AE-4F60-97A9-4DA8AF8DC00B
## Tools
### Package manager
#### winget
- 現時点ではプレビュー版、とのこと。win公式。
#### scoop
- [[file:Scoop.org][Scoop.org]]
#### PackageManagement (OneGet)
- https://qiita.com/japboy/items/451cf30fd0d763d98ae6
- https://qiita.com/arachan@github/items/399da4a19ac3a20205a7
#### Chocolatey
- package manager
##### CLI
###### Commands
####### choco
######## Options and Switechs
#########  -v, --version
####### list
####### search
####### find
####### help
####### info
####### install - installs packages using configured sources
####### pin
####### outdated
####### upgrade - upgrades packages from various sources
######## Usage
- choco upgrade <pkg|all> [<pkg2> ...] [<options/switches>
- cup <pkg|all> [<pkg2> ...] [<options/switches>
####### uninstall
####### pach
####### push
####### new
####### source
####### sources
####### config
####### feature
####### features
####### apikey
####### setapikey
####### unpackself
####### export
###### Default Options and Switches
####### -?,  --help, -h
####### -v, --verbose
#######  -y, --yes, --confirm
##### Memo
###### Install
- [[https://docs.chocolatey.org/en-us/choco/setup][Chocolatey CLI Setup / Install]]
- 2021/9/17にインストールした際は、powershellの管理者権限利用でいれたので、管理者権限でないとうまく扱えていない。

##### Link
- https://docs.chocolatey.org/en-us/
- [[https://community.chocolatey.org/courses/getting-started][Getting Started with Chocolatey]]
  
- https://chocolatey.org/packages?q=
- https://qiita.com/msp0310/items/2a92f8966608260c49c1
#### NuGet
### Terminal
#### Windows Terminal, wt
##### Shortcut
- Ctrl+Shift+T : タブを開く
- Ctrl+Shift+W : タブを閉じる
- Ctrl+Shift+P : コマンドパレットを開く

- Ctrl+Tab : タブの切替
- Ctrl+Shift+Space : ドロップダウンリストの表示
- Ctrl+Shift+F : 検索

- Altを押しながらSettings/設定 : defalut.jsonが開く

- Win + ` : Quakeモード

###### User Shortcut
- Ctrl+Shift+- : 水平分割
- Ctrl+Shift+\ : 垂直分割

##### Settings
- [[https://docs.microsoft.com/ja-jp/windows/terminal/customize-settings/actions][Custom actions in Windows Terminal - Microsoft Docs]]

##### Link
- [[https://qiita.com/whim0321/items/6a6b11dea54642bd6724][Windows Terminal Tips - whim0321 - Qiita]]
  
### PsTools
#### PsExec
-
##### Link
- https://technet.microsoft.com/ja-jp/sysinternals/bb897553
- http://www.atmarkit.co.jp/ait/articles/1205/11/news147.html
### Xming
- Windows上で動作するX Window Systemの実装の一つ。
## Performance
- https://msdn.microsoft.com/ja-jp/library/windows/hardware/dn529133
## Memo
### ACL
- 
  アクセス制御リスト(Access Control List)。
  あるユーザやグループに対して、利用可能な権限を定義したものを
  アクセス制御エントリ(Access Control Entry : ACE)といい、
  これを集めたものがACLとなる。
  （正確には「随意アクセス制御リスト、Discretionary Access Control List:DACL」らしい。）
  [[http://www.atmarkit.co.jp/fwin2k/win2ktips/700whatisacl/whatisacl.html][アクセス制御リストACLとは？ - @IT]]

### cmdをエクスプローラから開く
- 
  エクスプローラからその場のcmdを開くには、
  アドレスバーにcmdと打つとOK。

### ローカルユーザで接続する
- 
  .\user、local\user、servername\user等でアクセスできる。

### システム情報を表示する
- 
  msinfo32。
  スタートからシステム情報も探せるが、プログラム名として打てばよい。
  
### ローカルのAdminパスワードを変更する方法
- 
  管理者のパスワードを忘れてしまった際、ブートディスクでディスクにアクセスして、
  Utilman.exeを退避し、cmd.exeをcopyして名称をUtilman.exeとすると、
  ログイン画面でコマンドプロンプトが使えるようになる。
  [[http://blogs.technet.com/b/meacoex/archive/2011/08/15/reset-your-windows-sever-2008-r2-domain-controller-administrator-password.aspx][Reset your Windows Server 2008 / R2 Domain Controller administrator password - MEA Center of Expertise]]
  [[http://level69.net/archives/752][Windows Server 2012のパスワードを初期化しよう。- 技術的な何か。]]
  
### コントロールパネルをコマンドから開く
- [[https://www.atmarkit.co.jp/ait/articles/0507/02/news016.html][Windowsのコントロールパネルの各アイテムをコマンドラインから起動する - @IT]]
- [[file:Windows_SystemPrograms.org][Windows_SystemPrograms.org]]
  
### Thumbs.db
- 
  エクスプローラで縮小表示を行うと、画像や写真データの縮小イメージが格納されたThumbs.dbが作成される。
  必要に応じ再作成されるため、消しても問題ない。またキャッシュしない設定に変更することも出来る。
  [[http://www.atmarkit.co.jp/ait/articles/0602/04/news012.html][Thumbs.dbファイルを作成しないようにする - @IT]]

### AXキーボード設定
- 
  レジストリを書き換える。
  HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\i8042prt\Parametersを選択し、
  以下のように書き換える。
  |----------------------------+-----------+-------------+------------|
  | 値の名称                   | データ値  | 変更前      | 変更後     |
  |----------------------------+-----------+-------------+------------|
  | LayerDriver JPN            | REG_SZ    | kdb101.dll  | kdbax2.dll |
  | OverrideKeyboardIdentifier | REG_SZ    | PCAT_101KEY | AX_105KEY  |
  | OverrideKeyboardSubtype    | REG_DWORD | 0           | 1          |
  | OverrideKeyboardType       | REG_DWORD | 7           | 7          |
  |----------------------------+-----------+-------------+------------|
  [[http://www.atmarkit.co.jp/fwin2k/win2ktips/041axkbd/axkbd.html][右Altキーに漢字キーを割り当てる方法 - @IT]]
  
### スタートアップ等の特殊フォルダーをすばやく開く
- 
  すばやく特殊フォルダを開くには、shell:startup 等のシェルのショートカットを使うとよい。
  [ファイル名を指定して実行]、検索文字列入力欄、エクスプローラアドレスバーなどで指定する。
  コマンドプロンプトから実行するには、先頭に「start」か「explorer」をつける。
  [[http://www.atmarkit.co.jp/ait/articles/1401/24/news036.html][スタートメニューやスタートアップなどの特殊フォルダーの場所を素早く開く - @IT]]

- コマンド
  |-----------------------------------+------------------------------------------------------------|
  | shell:表記                        | フォルダー                                                 |
  |-----------------------------------+------------------------------------------------------------|
  | メニュー                          |                                                            |
  | shell:Start Menu                  | 現在のユーザの[スタート メニュー]                          |
  | shell:Common Start Menu           | 全ユーザ共通の[スタート メニュー]                          |
  | shell:Programs                    | 現在のユーザの[スタート] - [プログラム]                    |
  | shell:Common Programs             | 全ユーザ共通の[スタート] - [プログラム]                    |
  | shell:Startup                     | 現在のユーザの[スタート] - [プログラム] - [スタートアップ] |
  | shell:Common Startup              |                                                            |
  | shell:Administrative Tools        | 現在のユーザの[スタート] - [プログラム] - [管理ツール]     |
  | shell:Common Administrative Tools |                                                            |
  |-----------------------------------+------------------------------------------------------------|
  | ユーザーフォルダ関連              |                                                            |
  | ...                               |                                                            |

### 環境変数の設定
- 
  よくやるように、コンピュータのプロパティなどからシステム情報に飛び、環境変数を設定すると、
  個別ユーザでなく管理者での登録となる。
  
  コントロールパネルのユーザーアカウントの管理画面左側に、環境変数の設定、という項目があるので、
  個別ユーザでの設定ではそこを選択して設定する。
  
- [[http://note.chiebukuro.yahoo.co.jp/detail/n129063][Windowsで環境変数を設定する - YAHOO!知恵袋]]

### グラフや絵を文字で作るための変換方法
- 
  ただし全て"けいせん"でも出るけれども。
  
  |------------+------+------|
  | 読み       | 細字 | 太字 |
  |------------+------+------|
  | たて       | │   | ┃   |
  | よこ       | ─   | ━   |
  | たてみぎ   | ├   | ┣   |
  | たてひだり | ┤   | ┫   |
  | よこうえ   | ┴   | ┻   |
  | よこした   | ┬   | ┳   |
  | ひだりうえ | ┌   | ┏   |
  | ひだりした | └   | ┗   |
  | みぎうえ   | ┐   | ┓   |
  | みぎした   | ┘   | ┛   |
  | まんなか   | ┼   | ╋   |
  |------------+------+------|

  [[http://support.microsoft.com/kb/883172/ja][特殊文字・記号や罫線文字の入力一覧]]
  [[http://112123.jugem.jp/?eid=2781][【記号】 文字記号でツリーとか階層を作りたい時の変換方法【豆知識】]]

### Cドライブの掃除
#### ディスククリーンアップ
- Cのプロパティ->全般->ツールタブ
#### Tempの削除
- C:\WINDOWS\Temp
- C:\Users\(username)\AppData\Local\Temp
- C:\Documents and Settings\(username)\Local Settings\Temp
#### Internet一時ファイルの削除
#### Link
- http://freesoft.tvbok.com/tips/optimise_vista/increase_freespace_c_drive.html
- https://pctrouble.net/running/c_drive_freespace.html
### システム容量
#### Win7
- [[http://freesoft.tvbok.com/tips/win7rc64/windows7_winsxs.html][Windows7、HDバカ食いの理由 - ぼくんちのTV別館]]
### Scroll Lock
- 
  矢印キーで画面が動いてしまうのは、スクロールロックがかかっているため。
  キーボードや機種により設定は異なるが、現行は"fn + <(左矢印)"でかかる。

### IEの設定を取得する
- 
  reg export <レジストリキー> <出力先パス>
  reg export "HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Internet Settings" Path

- 
  http://yuzuemon.hatenablog.com/entry/20110510/1305043925

### レジストリ操作
- 
  http://www.atmarkit.co.jp/ait/articles/0402/21/news005.html

### アイコン画像作成
- bmpで保存、拡張子を.icoとすればOK。
### Bluetooth設定
#### pairing
- [[http://qa.elecom.co.jp/faq_detail.html?id=4406][【Bluetooth】Windows機能でのヘッドセット・ヘッドフォンペアリング方法 - ELECOM]]
#### connection
### ネットワークドライブの割り当て
- エクスプローラでAlt, 「ネットワークドライブの割り当て」を行う。
- http://www1.ark-info-sys.co.jp/support/all/kakumei/c21.html
### ドライブレターの変更
- Win10系：
  - Windowsマークを右クリック→Disk Management / ディスクの管理、から変更。
    ディスク系は上部に現れないので、下部の画面上、右クリックから変更する。
### ドメイン環境で使用されるポート
- https://blogs.technet.microsoft.com/jpntsblog/2009/03/03/563/
#### ドメインメンバー
- 
  |--------------------------+------------+--------------------------+----------------|
  | ポートを使用するサービス | プロトコル | クライアント側ポート番号 | DC側ポート番号 |
  |--------------------------+------------+--------------------------+----------------|
  | PING                     | ICMP       |                         |                |
  | DNS                      | TCP/UDP    | 一時ポート               |             53 |
  | Kerberos                 | TCP/UDP    | 一時ポート               |             88 |
  | NTP                      | UDP        | 123                      |            123 |
  | RPC                      | TCP        | 一時ポート               |            135 |
  | RPC                      | TCP        | 一時ポート               |     一時ポート |
  | NetBIOS-ns               | UDP        | 137                      |            137 |
  | NetBIOS-dgm              | UDP        | 138                      |            138 |
  | NetBIOS-ssn              | TCP        | 一時ポート               |            139 |
  | LDAP                     | TCP/UDP    | 一時ポート               |            389 |
  | SMB                      | TCP        | 一時ポート               |            445 |
  | KPasswd                  | TCP        | 一時ポート               |            464 |
  | LDAP GC                  | TCP        | 一時ポート               |           3268 |
  | LDAP SSL                 | TCP        | 一時ポート               |            636 |
  | LDAP GC SSL              | TCP        | 一時ポート               |           3269 |
  | AD DS Web Services       | TCP        | 一時ポート               |           9389 |
  |--------------------------+------------+--------------------------+----------------|

#### DC間
- 
  |--------------------------+------------+------------------+----------------|
  | ポートを使用するサービス | プロトコル | 送信元ポート番号 | 宛先ポート番号 |
  |--------------------------+------------+------------------+----------------|
  | WINS                     | TCP        | 一時ポート       |             42 |
  | DNS                      | TCP/UDP    | 一時ポート       |             53 |
  | Kerberos                 | TCP/UDP    | 一時ポート       |             88 |
  | NTP                      | UDP        | 123              |            123 |
  | RPC                      | TCP        | 一時ポート       |            135 |
  | RPC                      | TCP        | 一時ポート       |     一時ポート |
  | LDAP                     | TCP/UDP    | 一時ポート       |            389 |
  | SMB                      | TCP        | 一時ポート       |            445 |
  | DFSR                     | TCP        | 一時ポート       |           5722 |
  |--------------------------+------------+------------------+----------------|

### ハッシュ値を計算する
- certutil -hashfile <filename> <algorithm>
### サービスに対し権限を設定する
- WindowsのServiceを一般ユーザで操作するには、"sc shshow ServiceName"で確認したSDDIを、
  "sc sdset ServiceName NewSDDI"で書き換えればよい。
  (A;;RPWP;;;AU)とすれば、許可、起動・停止、一般ユーザ、となる。
  [[http://buti.blog.so-net.ne.jp/2010-03-03][【Tips】Windowsのサービスを一般（AdminやPowerGroup以外）ユーザで起動できるようにする。 - Butinekoの世界]]
- scでSDDI形式の
### リモートデスクトップでパスワード変更
- Ctrl + Alt + End (deleteでなく!)
  http://grum.hatenablog.com/entry/2016/01/13/022550
### 権限
- everyoneは、ログインできるユーザすべてに対しての権限。
  ユーザ登録していない、ログインできない人も含め全て、の場合はgeustが該当とのこと。
### リンク（ジャンクション、シンボリックリンク、ハードリンク）
#### 種類
- ハードリンク
- シンボリックリンク
- ジャンクション
- [[http://www.atmarkit.co.jp/ait/articles/1306/07/news111.html][Windowsのシンボリックリンクとジャンクションとハードリンクの違い - @IT]]
#### ジャンクション
##### 小技
###### ジャンクションならLinuxでマウントした場合も利用可
- WindowsのフォルダをLinuxでマウントした場合、
  symlinkではLinuxでリンクを辿れないが、ジャンクションなら可能。
  [[http://var.blog.jp/archives/49781846.html][ジャンクションが便利 - nmm実験室]]
###### ジャンクションなら、ファイルダイアログを使ってもパスが変換されない
- シンボリックリンクでは、ファイルダイアログを使う場合パスが変換されてしまう。
  対して、ジャンクションであれば変換されずにそのまま利用可能。
  [[https://qiita.com/go_astrayer/items/ab993cdc420d4f7f50d4][シンボリックリンクの使い方と落とし穴 - Qiita]]
#### シンボリックリンクの設定に関する事項
- [[https://blogs.technet.microsoft.com/jpntsblog/2016/08/31/smbandsymlink/][ファイル共有とシンボリックリンクの利用について - Ask the Network & AD Support Team, Microsoft]]
  アクセス元で"fsutil behavior set symlinkevaluation R2R:1"をしないとRemote間でのリンクは動作しない、など。

- [[http://schinagl.priv.at/nt/hardlinkshellext/hardlinkshellext.html#changesymboliclinkprivilege][Change Symbolic Link Priviledge - Link Shell Extension]]
  シンボリック利用のための権限

#### ジャンクション、シンボリックリンクを避けてコピー
- robocopy {src} {dst} /E /XJ
### イベントログ
#### 設定変更
##### GUI
- Event ViewrのGUI上、右クリックでプロパティを編集
##### CUI
- wevtutilで設定
  - slオプションでSDDLを設定することでアクセス権設定可能
  - eplオプションで出力
#### Link
- http://www.atmarkit.co.jp/ait/articles/0907/31/news106.html
- https://blogs.technet.microsoft.com/askcorejp/2010/03/30/windows-server-2008-2/
- https://qiita.com/sta/items/957d78a8e884f23cb8be
- https://news.mynavi.jp/itsearch/article/hardware/923
### ユーザ、グループのSID確認
- SIDは、whoamiにオプションを付けて確認可能。
  /user, /groups
### スリープ、休止状態
- 意外と待機電力に差がなかった。スリープ有用。
  - シャットダウン後の待機電力 : 0.38W
  - スリープ時の待機電力 : 0.56W
  
- http://affikatsu.com/pc-sleep-hibernation-shutdown-7748/
- https://marvelsoflife.com/2016/12/02/post-2801/
### リモートデスクトップにログインしているユーザの特定
- query user /server:ServerName (or, quser ~)
- query session /server:ServerName (or, qwinsta ~)
- /serverでRPCを使っていると思われるので、ポート開放は必要。
  また、/serverで対応できるためpsexecは不要と思われる。
#### Link
- http://www.atmarkit.co.jp/ait/articles/0910/16/news117.html
- https://qiita.com/MrDairi/items/5a1ac9cd02b3018940e5
  - (別件)https://qiita.com/MrDairi/items/697050b30052bb0894df
- https://social.technet.microsoft.com/Forums/ja-JP/12538f0f-f487-42ea-a697-6ef733134c73?forum=w7itprogeneralja
### ポートの接続確認
- powershellで確認する。telnetなどがデフォルトで入っていないため、、
- 手順:
  $tc = New-Object System.Net.Sockets.tcpClient
  $tc.connect(ターゲット, ポート)
  $tc.connected
  $tc.close()
- https://qiita.com/_norin_/items/8f534bd0531a960af5e9

### 共有フォルダの現在のアクセス確認
- "Computer management"から確認可能。
  http://itdiary.info/windows/post-88/
### sshdサービス
#### Win32-OpenSSH
- https://github.com/PowerShell/Win32-OpenSSH/releases
- https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH

- https://www.rootlinks.net/2017/10/05/install-sshd-on-windows-server-2012-r2-win32-openssh/
#### cygwin/putty
#### Win 10以降
- https://rcmdnk.com/blog/2018/04/27/computer-windows-network/
### X11接続
- XmingなどX Windowサーバをインストール
- sshで-Xオプションを付けて接続
- echo $DISPLAYを確認して割り当てを確認
- GUIアプリケーションを実行する
### ファイルの分割
- makecabを使うと分割できる（らしい。詳細わかっていないので次使うときに調べると良い）
### パケットキャプチャーをソフトを使わずに実行
- start: netsh trace start capture=yes
  end: netsh trace stop
- 確認は、etl2pcapngなどを利用して、変換した情報をWiresharkあたりで確認するのがよい。
  - [[https://github.com/microsoft/etl2pcapng/releases][microsoft/etl2pcapng - Github]]

- 旧情報：確認はMicrosoft Message Analyzer/Microsoft Network Monitorあたりが必要
  - http://www.vwnet.jp/windows/WS16/2017013001/PacketCapture.htm
  →Message Analyzerは開発中止に。

  
### Windowsでwget/curl的なことを行う
- bitsadminコマンドを使う
- 例:
  bitsadmin /TRANSFER htmlget https://url c:\savepath
### 資格情報、リモートサーバへの資格情報
- 以下の方法で、スムーズにリモートのリソースにアクセスできる。
  - ローカルとリモートで、同じユーザ名・パスワードのアカウントを用意しておく
  - 同じドメインに参加させておく
  - ドメインにもローカルにも同じアカウントを用意する
  - 必要な資格情報を、資格情報マネージャーであらかじめ用意しておく
- [[https://www.atmarkit.co.jp/ait/articles/1406/12/news097_2.html][第2回　ファイル共有の使い方 (2/2) - @IT]]
### 「ショートカット」の「ショートカットキー」
- ショートカットのプロパティで設定できる「ショートカットキー」は、
  ショートカットがデスクトップにある場合に、そのキーの組み合わせで起動できるようにする設定。
- [[https://www.724685.com/word/wd190925.htm][「ショートカット」の「ショートカットキー」とは - なにパソ]]

### Program Filesなどに存在しないファイルをショートカットとしたい場合
- プログラムファイルなどに存在しない場合に、ショートカットを作成するのが難しいので、
  まず'shell:AppsFolder'などにアクセスしたうえで、右クリックでアプリケーションのショートカットを（デスクトップに）作成することができる。
- あるいは単に
  https://www.early2home.com/blog/application/edge/post-181.html

### Windows10の電源オプションに「休止」を追加
- 設定→システム→電源とスリープ→電源の追加設定→電源ボタンの動作を選択する→現在利用可能でない設定を利用します
- [[https://www.atmarkit.co.jp/ait/articles/1808/20/news026.html][Windows 10の電源メニューに「休止状態」を表示する - @IT]]
### Windows10のPCディレクトリから「ピクチャ」「ミュージック」などを削除
- レジストリをいじるしかない、とのこと。
  HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\ FolderDescriptions\{0ddd015d-b06c-45d5-8c4c-f59713854639}\PropertyBag
  [[https://www.billionwallet.com/goods/windows10/win10_this_pc_delete.html][ファイルエクスプローラー上のPCに入っているデーターフォルダーを非表示にする - Windows 10 - BILLIONWALLET]]

- 3Dオブジェクトのフォルダを削除して非表示にする。
  HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\MyComputer\NameSpace\{0DB7E03F-FC29-4DC6-9020-FF41B59E513A}
  [[https://www.billionwallet.com/windows10/3d-objects-delete.html][Windows 10 ファイルエクスプローラのPCに入っている3Dオブジェクトのフォルダを削除して非表示にする - BILLIONWALLET]]

- 2021/1に再設定した際に参照したリンク。
  [[https://river-link.co.jp/2020/05/29/%E3%82%A8%E3%82%AF%E3%82%B9%E3%83%97%E3%83%AD%E3%83%BC%E3%83%A9%E3%83%BC%E3%82%92%E3%82%B9%E3%83%83%E3%82%AD%E3%83%AA%E3%81%95%E3%81%9B%E3%82%8B/][エクスプローラーをスッキリさせる - RiverLINK]]

### Windowsのデフォルト壁紙が存在しているところ
- C:\Windows\Web\Wallpaper以下。
  ロック画面はScreen、4K壁紙は4Kフォルダ以下。
- [[https://memorva.jp/internet/pc/windows_default_wallpaper.php#:~:text=Windows%2010%2F8.1%2F7%E3%81%AA%E3%81%A9,%E3%83%87%E3%83%95%E3%82%A9%E3%83%AB%E3%83%88%E3%81%AE%E5%A3%81%E7%B4%99%E3%81%8C%E3%81%82%E3%82%8B%E3%80%82][Windows のデフォルトの壁紙とロック画面の画像が保存されている場所（フォルダ） - MEMORVA]]

### ユーザ辞書のインポート・エクスポート
- 辞書ツールで「一覧の出力」、および「テキストファイルからの登録」
- [[http://office-qa.com/win/win12.htm][MS-IME：日本語入力（MS-IME）のユーザー辞書を他のPCにエクスポートする]]

### Windows10: ワールドワイド言語サポートでUnicode UTF-8を使用について
- 7zipでzip化した際に文字化けする、と連絡あり。該当チェックを外したところ、問題なさそう。
  各種日本語などの文字列をSJISでなくUTF-8処理してしまうため問題となったと考えられる。
  ベータ版であり、しばらくは有効にしない方がよさそう。
- 関連URL: [[https://news.mynavi.jp/article/win10tips-444/][「ワールドワイド言語サポートでUnicode UTF-8を使用」は有効にすべき？ - マイナビニュース]]

### サービスの削除
- sc delete サービス名
    
### サービスの実行ファイルのパス変更方法
- regedit
  -> HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\<サービス名>、のImagePathを変更。
- https://nketomok-asa.hatenadiary.org/entry/20060503

### ルート証明書が信頼されていない
- 問題となっている証明書を、「信頼されたルート証明機関」にインポートして対処した。
  実際には、まず問題となっているルート証明書をエクスポートしたうえで、そのファイルを上記の信頼されたものとしてインポートしなおした。
- [[https://milestone-of-se.nesuke.com/troubleshoot/not-exist-in-trusted-rootca-store/][『 信頼されたルート証明機関のストアに存在しないためこの ca ルート証明書は信頼されていません』または『 このcaルート証明書は信頼されていません。信頼を有効にするにはこの証明書を信頼されたルート証明機関のストアにインストールしてください』と表示される - SEの道標]]
### フォルダーとディレクトリ
- フォルダー：仮想フォルダー/Virtual folderとファイルシステムフォルダー/File system folderからなるオブジェクト。
- ディレクトリ：ファイルシステムフォルダーのみを指すオブジェクト
- [[https://ascii.jp/elem/000/004/081/4081147/][Windowsにおけるフォルダーとディレクトリとは - ASCII.jp]]

- 仮想フォルダー
  代表的なものとしては「コントロールパネル」
- ディレクトリ（ファイルシステムフォルダー）は特殊なファイル。その中に属するファイルのリストを保持している。

### コマンドでウェブページを開く
- strat URLで、ウェブページを開くことができる。
  なお、Macではopen URL。
### UACの仕組みで管理者としてコマンドを実行
- powershellを使って、以下のように実行する。
  - start-process cmd -verb runas
  - (powershell -command start-process cmd -verb runas)
### VPNへコマンドから接続する
- 結局うまくいっていない。rasdial, rasphoneを利用すればよさそうなのだが。
- http://unyouchan.blog.jp/archives/1003946859.html
- https://seesaawiki.jp/w/kou1okada/d/20220215%3A%20Windows10%20-%20VPN%20%A4%CE%BC%AB%C6%B0%C0%DC%C2%B3
  
### (聞いた話メモ)
- 
  ntoskrnl.exe
  カーネル本体

- 
  Hardware abstraction の下にBIOSがいる。
  
- 
  Ntdll.dll
  Kernel32.dll
  Win32

- 
  起動プロセス
  smssだけ、カーネル直で読んでる。
  
- 
  Object manager
  セマフォとか、

- 
  カーネルの中のレジストリとか、
  
- 
  Advanced なんとか。
  
- 
  起動プロセス、

- 
