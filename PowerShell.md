# PowerShell
## Command
### PowerShell[.exe]
#### Options
##### -ExecutionPolicy <ExecutionPolicy>
## Command-lets
### Add-Content
#### ac
### Add-PSSnapin
#### asnp
### Clear-Content
#### cls
### Clear-History
#### clhy
### Clear-Host
#### clear
#### cls
### Clear-Item
#### cli
### Clear-ItemProperty
#### clp
### Clear-Variable
#### clv
### Compare-Object
#### compare
#### diff
### Compress-Archive
- PowerShell5.0より。
### Connect-PSSession
#### cnsn
### Convert-Path
#### cvpa
### Copy-Item
#### copy
#### cp
#### cpi
#### cpp
### Disable-PSBreakpoint
#### dbp
### Disable-PSRemoting
- Prevents remote users from running commands on the local computer
### Disconnect-PSSession
#### dnsn
### Enable-PSBreakpoint
#### ebp
### Enable-PSRemoting
- Configures the computer to receive remote commands
### Enter-PSSession
#### etsn
### Exit-PSSession
#### exsn
### Expand-Archive
- PowerShellv5.0より。
### Export-Alias
#### epal
### Export-Csv
#### epcsv
### Export-PSSession
#### espn
### ForEach-Object
#### Aliases
##### %
##### foreach
### Format-Custom
#### fc
### Format-List
#### fl
### Format-Table
#### ft
### Format-Wide
#### fw
### Get-Alias
#### Aliases
##### gal
### Get-ChildItem
#### Aliases
##### dir
##### gci
##### ls
#### Options
##### -Exclude
- 取得結果から除外するパスを指定する
##### -Filter
- 取得結果に含めるパスを指定する
##### -Path
- ディレクトリパスを指定する
##### -Recurse
- サブディレクトリ配下を含めて再帰的に取得する
### Get-Command
- コマンドレットを取得する
#### gcm
### Get-Content
#### Aliases
##### cat
##### gc
##### type
#### Options
##### -ReadCount <long>
##### -TotalCount <long>
- 先頭から行数分取得する
##### -Tail <int>
- 末尾から行数分取得する
##### -Filter <string>
##### -Wait
- 更新を待ち、更新があった場合に後続を表示する
### Get-EventLog
### Get-ExecutionPolicy
- Gets the execution policies for the current session.
### Get-Help
- Displays information about Windows PowerShell commadns and concepts
#### Aliases
- None
##### (help)
##### (man)
### Get-History
#### Aliases
##### ghy
##### h
##### history
### Get-Item
#### gi
### Get-ItemProperty
#### gp
### Get-Job
#### gjb
### Get-Location
#### gl
#### pwd
### Get-Member
#### gm
### Get-Module
#### Syntax
- Get-Module [-ListAvailable]
#### Aliases
##### gmo
### Get-NetConnectionProfile
#### Aliases
- None
#### Options
### Get-Process
#### gps
#### ps
### Get-PSBreakpoint
#### gbp
### Get-PSCallStack
#### gcs
### Get-PSDrive
#### gdr
### Get-PSSession
#### gsn
### Get-PSSnapin
#### gsnp
### Get-Service
#### gsv
### Get-Unique
#### gu
### Get-Variable
#### gv
### Get-WmiObject
#### gwmi
### Group-Object
#### group
### help
#### man
### Import-Alias
#### Aliases
##### ipal
### Import-Csv
#### SYNTAX
#### ALIASES
##### ipcsv
### Import-Module
#### Aliases
##### ipmo
### Import-PSSession
#### ipsn
### Invoke-Command
#### icm
### Invoke-Expression
#### Aliases
##### iex
### Invoke-History
#### ihy
#### r
### Invoke-Item
#### ii
### Invoke-RestMethod
#### irm
### Invoke-WebRequest
#### Aliases
##### curl
##### iwr
##### wget
#### Options
##### -Uri <uri>
##### -OutFile <string>
### Invoke-WmiMethod
#### iwmi
### Measure-Object
#### About
- オブジェクトの数値プロパティと、テキストのファイルなど文字列オブジェクト内の文字、単語、行を計算する。
#### Syntax
- Measure-Object [-Average] [-Sum] [-Maximum] [-Minimum] [[-Property] <String[]>] [<CommandParameters>]
- Measure-Object [-Line] [-Word] [-Character] [[-Property] <String[]>] [<CommandParameters>]
#### Aliases
##### measure
### mkdir
#### md
### Move-Item
#### mi
#### move
#### mv
### Move-ItemProperty
#### mp
### New-Alias
#### nal
### New-Event
- 新しいイベントを作成する。
### New-EventLog
- イベントソースを作成する。
  Write-EventLogをした際にエラーが表示されなくなる。
### New-Item
#### ni
### New-Module
#### nmo
### New-Object
#### 概要
- Microsoft .NET FrameworkまたはCOMオブジェクトのインスタンスを作成する。
#### 構文
### New-PSDrive
#### mount
#### ndr
### New-PSSession
#### nsn
### New-PSSessionConfigurationFile
#### npssc
### New-Variable
#### nv
### Out-GridView
#### ogv
### Out-Host
#### oh
### Out-Printer
#### lp
### Pop-Location
#### popd
### powershell_ise.exe
#### ise
### Push-Location
#### pushd
### Receive-Job
#### rcjb
### Receive-PSSession
#### rcsn
### Remove-EventLog
#### Options
##### -LogName logname
##### -Source sourcename
### Remove-Item
#### del
#### erase
#### rd
#### ri
#### rm
#### rmdir
### Remove-ItemProperty
#### rp
### Remove-Job
#### rjb
### Remove-Module
#### rmo
### Remove-PSBreakpoint
#### rbp
### Remove-PSDrive
#### rdr
### Remove-PSSession
#### rsn
### Remove-PSSnapin
#### rsnp
### Remove-Variable
#### rv
### Remove-WmiObject
#### rwmi
### Rename-Item
#### ren
#### rni
### Rename-ItemProperty
#### rnp
### Resolve-Path
#### rvpa
### Resume-Job
#### rujb
### Select-Object
#### select
### Select-String
#### sls
### Set-Alias
#### sal
### Set-Content
#### sc
### Set-ExecutionPolicy
### Set-Item
#### si
### Set-ItemProperty
#### sp
### Set-Location
#### cd
#### chdir
### Set-Location
#### sl
### Set-PSBreakpoint
#### sbp
### Set-Variable
#### set
#### sv
### Set-WmiInstance
#### swmi
### Show-Command
#### shcm
### Sort-Object
#### sort
### Start-Job
#### sajb
### Start-Process
#### saps
#### start
### Start-Service
#### sasv
### Start-Sleep
#### sleep
### Start-Transcript
- Start-Transcript [[-Path] <string>] [-Append] [-Force] [-NoClobber] [-WhatIf] [-Confirm] [<CommonParameters>]
### Stop-Job
#### spjb
### Stop-Process
#### kill
#### spps
### Stop-Service
#### spsv
### Stop-Transcript
- Stop-Transcript [<CommonParameters>]
### Suspend-Job
#### sujb
### Tee-Object
#### tee
### Test-Path
- Determines wheher all elemens of a path exists.
### Trace-Command
#### trcm
### Update-Help
- Downloads and installs the newest help files on your computer.
### Wait-Job
#### wjb
### Where-Object
#### 概要
- Selects objects from a collection based on their property values.
#### Aliases
##### ?
##### where
### Write-EventLog
### Write-Host
- Writes customized output to a host
### Write-Output
#### Alias
##### echo
##### write
## Command-lets(etc,tmp)
### Server Manager Cmdlets
- https://technet.microsoft.com/ja-jp/library/jj205465(v=wps.630).aspx
#### Add-WindowsFeature
- "Install-WindowsFeature"のAlias
#### Install-WindowsFeature
- 役割と機能をインストールする。
  管理ツールを含めるには、"IncludeManagementTools"パラメータをコマンドレットに追加する。
- https://technet.microsoft.com/ja-jp/library/jj205467(v=wps.630).aspx
#### Uninstall-WindowsFeature
#### Enable-ServerManagerStandardUserRemoting
#### Disable-ServerManagerStandardUserRemoting
## Shell Variables
### $_
- パイプラインに渡されたオブジェクトを表す変数。
### $Args
- コマンドライン引数
### $env
### $profile
- プロファイルのパスを表示。プロファイルは.bash_profileみたいなもの、起動時の実行コマンドを記述する。
### $PSVersionTable
- Version2.0以降
  PowerShellのバージョン情報を表示する
## Syntax
- [[http://m0t0k1x2.tumblr.com/post/121507591989/powershell%E5%86%8D%E5%85%A5%E9%96%805-%E5%9F%BA%E6%9C%AC%E6%A7%8B%E6%96%87][PowerShell再入門 : 5. 基本構文]]
- [[http://winscript.jp/powershell/202][PowerShell基礎文法最速マスター - PowerShell Scripting Weblog]]
- [[https://codezine.jp/article/detail/2388][Windows PowerShell 入門(5) - 制御構文]]
### for
- for (<初期化>; <条件>; <繰り返し処理>)
  {
    <コードブロック>
  }
### 変数
- $var = a,b,c
- 組み込み変数に値を代入しても無視される。
### 配列
- $a = 0,1,2,3,4
- $a = 0..4 (連続した値)
- アクセス : $a[1] -> 1
### 連想配列
- $h = @{"dog"="犬";"cat"="猫"}
- アクセス : $h[dog] -> 犬
- 追加 : $h["bird"] = "鳥"
### 演算子
#### 比較演算子
- -eq
- -ne
- -lt
- -le
- -gt
- -ge
#### 正規表現演算子
- -match
#### 論理演算子
- -and
- -or
### 関数
- function 
## Shortcut keys
### ↑/↓
- 前/次の履歴
### PageUp/PageDown
- 最初/最後の履歴
### Home/End
- カーソルを先頭/末尾に
### Ctrl + ←/→
- 単語一つ分左/右に移動
### Ctrl + C
- コマンドをキャンセル
### F2
### F3
### F7
- 履歴を表示
### Link
- https://technet.microsoft.com/ja-jp/scriptcenter/powershell_owner03.aspx
## Reverse Lookup
### フィルタ、オブジェクト操作
- オブジェクト操作には以下などを使用
  Where-Object(?,where), Select-Object(select), Sort-Object(sort)などを利用。
- https://qiita.com/Kirito1617/items/bd3937fb26c668eca078
#### Where-Object
- Usage:
  - Where-Object {$_.Column -match "^Pattern*"}
#### Select-Object
- Usage:
  - Select-Object column1, column2
  - Select-Object -First 2 / -Last 2
#### Sort-Object
- Usage:
  Sort-Object column1 [-Descending]
### 関連コマンドの取得
- Get-Command | Where-Object {$_.Name -match "FilterName"}
### ポートの接続確認
- powershellで確認する。telnetなどがデフォルトで入っていないため、、
- 手順:
  $tc = New-Object System.Net.Sockets.tcpClient
  $tc.connect(ターゲット, ポート)
  $tc.connected
  $tc.close()
- https://qiita.com/_norin_/items/8f534bd0531a960af5e9
### シンボリックリンクファイルのリストを取得
- Command:
  Get-ChildItem | Where-Object { $_.Attributes -match "ReparsePoint" }
- [[https://stackoverflow.com/questions/817794/find-out-whether-a-file-is-a-symbolic-link-in-powershell][Find out whether a file is a symbolic link in PowerShell - stackoverflow]]
### Switch文
- https://qiita.com/nimzo6689/items/26373ed44119c303e539
- switch (value) {
    checkVal1 {command 1}
    checkVal2 {command 2}
    checkVal3 {command 3}
    default {default command}
  }
### Tail代わり
- Get-Content -Path "filePath" -Wait -Tail "readLine"
### wc代わり
- Measure-Object (measure)
- $obj.length, $obj.count
  行数を取得可能
- https://operationslab.wordpress.com/2013/03/12/powershell-%E3%81%A7%E8%A1%8C%E6%95%B0%E3%82%84%E6%96%87%E5%AD%97%E6%95%B0%E3%82%92%E3%82%AB%E3%82%A6%E3%83%B3%E3%83%88%E3%81%99%E3%82%8B/
### CSVファイルを読む
- Import-CSV "csvfile"
  オブジェクトが返ってくる。ForEach-ObjectやWhere-Objectなどで操作する。
### ログを取得する
- Start-Transcript ["filename"] [Options]
- Stop-Transcript

- 設定では、グループポリシー(gpedit.msc)で「ユーザーの構成/User Configuration」＞「管理用テンプレート/Administrative Templates」＞「Windows Components」>「Windows PowerShell」配下の、
  「Powershell トランスクリプションを有効にする / Turn on PowerShell Transcription」を設定する。
### クラスタ関連コマンド
#### Get-Cluster
#### Get-ClusterResource
#### Get-ClusterResource pd-racm-im01 | Get-ClusterParameter
#### Get-ClusterGroup
#### Get-ClusterResource "resourceName" | Start-Resource
#### Move-ClusterGroup "resourceName"
#### Get-ClusterAvailableDisk
#### Get-ClusterNode
#### Get-ClusterLog
#### Get-ClusterAccess
#### Grant-ClusterAccess -User userName [-Full|-ReadOnly]
#### Remove-ClusterAccess -User username
### tmp
#### ネットワークプロファイルを調べる
- Get-NetConnectionProfile -IPv4Connectivity Internet
  NetworkCategoryの値を見る。

## Memo
### Default Encode
- UTF-16とのこと。
### ScriptFile実行許可
- Set-ExecutionPolicy RemoteSigned
### ExecutionPolicy 実行ポリシー
#### Values
##### Restricted
- 構成ファイルの読み込みやスクリプトの実行を行わない。デフォルト。
##### AllSgined
- 全てのスクリプトと構成ファイルが信頼された発行元によって署名されていることを要求
##### RemoteSigned
- インターネットからダウンロードされたすべてのスクリプトおよび構成ファイルが、信頼された発行元によって署名されていることを要求する
##### Unrestricted
##### Bypass
##### Undefined
#### Scope
- Set-ExecutionPolicyの-Scopeオプションで設定する
##### Process
- 現在のプロセスのみに影響する
##### CurrentUser
- 現在のユーザのみに影響する
##### LocalMachine
- コンピュータのすべてのユーザに影響する
#### Link
- https://qiita.com/kikuchi/items/59f219eae2a172880ba6
### 大文字小文字
- 区別しない
### 環境変数の確認
- $env:環境変数名
  ex) echo $env:PATH
### Write-Host, Write-Outputの違い
- $a=1,2,3
- Write-Host
  - write-host $a
    1 2 3
  - コンソールに文字を表示。Standard output streamへ出力しない。
- Write-Outut
  - write-output $a
    1
    2
    3
  - Standard output streamにオブジェクトを出力し、コンソールへの表示は行わない。
- https://blog.shibata.tech/entry/2016/01/11/151201
### コピー・ペースト
- 右クリックでどちらも動く。
-
### オブジェクトのパイプライン
- 従来のテキストデータによるパイプラインでなく、「オブジェクトもしくはその配列」が「プロパティ値を保持したまま」パイプを渡る。
### ファイルの先頭・末尾の出力
- Get-Content filename -TotalCount num
- Get-Content filename -Tail num
## Link
- [[https://technet.microsoft.com/ja-jp/library/ee221100.aspx][Windows PowerShell Owner's Manual - TechNet]]
- [[https://technet.microsoft.com/ja-jp/scriptcenter/powershell_owner.aspx][Windows PowerShell オーナーマニュアル - TechNet]]
- [[https://social.technet.microsoft.com/wiki/contents/articles/14301.windows-powershell-ja-jp.aspx][Windows PowerShell(ja-JP) - Wiki - TechNet]]


- [[http://qiita.com/tadnakam/items/f51e03021b95eb39f34b][コマンドプロンプトからPowerShellに乗り換えるための小さな本 - Qiita]]
- [[https://qiita.com/cd01/items/da9a36582372e7d0a7f6][それPowerShellでできるよ - Qiita]]

