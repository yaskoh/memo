# Scoop
  - emacsを利用するために導入した。便利そう。
  環境を汚さずに導入でき、環境変数も併せて設定してくれる、とのこと。
- https://scoop.sh/
  
## Installed
- scoop list
  Installed apps:  (2021/10/15)
    7zip 19.00 [main]
    dig 9.14.8 [main]
    emacs 27.2 [extras]
    git 2.33.0.windows.2 [main]
    innounp 0.50 [main]
    less 590 [main]
    openjdk 16.0.2-7 [java]
    openssl 3.0.0 [main]
    pwsh 7.1.5 [main]

## Tips
### Installation
- Invoke-Expression (New-Object System.Net.WebClient).DownloadString('https://get.scoop.sh')
- iwr -useb get.scoop.sh | iex

- If policy needed to change:
  - Set-ExecutionPolicy RemoteSigned -scope CurrentUser

### Commands
#### help
#### search
#### bucket
- bucketの追加、一覧表示、削除
##### add
- scoop bucket add java、でjavaのbucketを追加、その後openjdkをinstallした。
#### insntall
#### update
- アプリを最新のバージョンに更新するコマンド
- scoop update : scoop自身のアップデート
- scoop update <app> : appのアップデート
  - scoop update * : 全appのアップデート
<<<<<<< HEAD:Scoop.md
#### uninstall
## Link
=======
**** uninstall
** Memo
***  バージョンを変更
- scoop reset app@version
  - scoop reset emacs@27.2、など。
    ただし本当にこれが良いやり方なのかは、よいくわからない。
- https://qiita.com/akiakishitai/items/67de2d8dded401f218a2
** Link
>>>>>>> refs/remotes/origin/master:Scoop.org
- [[https://qiita.com/nimzo6689/items/1ab33380366e324c0b84][全Scoopコマンド解説 その１ ～使用頻度（高）～ - @nimzo6689 - Qiita]]


