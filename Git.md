# Git
## Commands
### High-level / Procelain
#### Main
##### git-add
##### git-am
##### git-archive
- Create an archive of files from a named tree
###### SYNOPSIS
- git archive [--format=<fmt>] [--list] [--prefix=<prefix>/] [<extra>] [-o <file> | --output=<file>] [...] <tree-ish> [<path>...]
###### Options
####### --format=<fmt>
####### <extra>
####### <tree-ish>
####### <path>
- Without an option path parameter, all files and subdirectories of the current working directory are included in teh archive.
  If one or more paths are specified, only these are included.
##### git-checkout
###### SYNOPSIS
- git checkout [-q] [-f] [-m] [<branch>]
  etc
###### Options
####### -b
- -b causes a new branch to be created as if git-branch were called and then checked out.
##### git-clean
##### git-clone
##### git-commit
##### git-describe
##### git-diff
- Show changes between commits, commit and working tree, etc.
- 
  差分を表示する。オプションをつけない場合はステージされていない変更の表示。
  また、--cached / --stagedオプションをつけると、ステージされた変更の差分を表示する。
  |------+--------------------------+-----------------------------------|
  | tree | stage                    | repository                        |
  |------+--------------------------+-----------------------------------|
  |      | tree  <- (無印) -> stage |                                   |
  |      |                          | stage  <- --cached ->  repository |
  |      | tree          <-   HEAD  | ->                     repository |
  |------+--------------------------+-----------------------------------|

###### Synopsis
- git diff [options] [<commit>] [--] [<path>...]
- git diff [options] --cached [<commit>] [--] [<path>...]
- git diff [options] <commit> <commit> [--] [<path>...]
- git diff [options] <blob> <blob>
- git diff [options] [--no-index] [--] <path> <path>
###### Options
####### --diff-filter=[(A|C|D|M|R|T|U|X|B)...[*]]
- Select only files are:
  - A: Added
  - C: Copied
  - D: Deleted
  - M: Modified
  - R: Renamed
  - T: Type changed
  - U: Unmerged
  - X: Unknown
  - B: Broken
####### --name-only
- Show only names of change files.
####### --stat[=<width>[,<name-width>[,<count>]]]
- Generate a diffstat.
  統計情報を表示する。

##### git-fetch
##### git-grep
##### git-init
##### git-log
##### git-merge
##### git-mv
##### git-pull
- 
  変更を取得した後マージする
  git fetch + git merge origin/master

##### git-push
##### git-rebase
##### git-reset
##### git-rm
##### git-show
##### git-status
##### git-tag
###### Options
####### -f, --force
####### -d, --delete
####### -l, --list
####### -m <msg>, --message=<msg>
####### <tagname>
###### Memo
- https://h2ham.net/git-tag-checkout
####### 過去のコミットにタグを付ける
- git tag -a tagname -m 'comment' <tagname>
####### タグを削除
- git tag -d tagname
####### タグをリモートに送信
- 特定のタグを送信 : git push origin <tagname>
- 全てのタグを送信 : git push origin --tags
##### git-worktree
#### Ancillary
##### Manipulators
###### git-config
- You can query/set/replace/unset options with this command.
- 項目の設定を行う。

####### Options
######## --replace-all
######## --add
######## -e, --edit
- Opens an editor to modify the specified confige file; either --system, --global, or repository (default).
- --global --edit
  グローバルな設定ファイルをテキストエディタでひらくコマンド。
######## --get
######## --global
- For writing options: write to global ~/.gitconfig file rather than the repository .git/config.
- For reading options: read only from global ~/.gitconfig and $XDG_CONFIG_HOME/git/config rather than from all available files.
######## --system
- For writing options: write to system-wide $(prefix)/etc/gitconfig rather than the repository .git/config.
######## --local
- For writing options: write to the repository .git/config file. (Default behavior)
######## -l, --list
- List all variables set in config file, along with their values.
######## --unset
####### Variables
######## alias.*
- Command aliases for the git command wrapper.
- alias.<alias-name> <git-command>
  Gitコマンドのショートカットを設定する。
######## color.*
######### color.branch
######### color.diff
######### color.ui
- This variable determines the default value for variables such as color.diff and color.grep that control the use of color per command family.
- --global color.ui "auto"
  ユーザインターフェースを自動で色付けする。

######## core.*
######### core.autocrlf
- true: same as auto
- auto: CRLF at working directory and LF at the repository.
######### core.editor
- Commands such as commit and tag that lets you edit messages by lauching an editor uses the value of this variable
- --system core.editor <editor>
  git commandのようなコマンドを実行する際のエディタを指定する。
######### core.eol
######### core.fileMode
- Tells Git if the executable bit of files in the working tree is tobe honored.
- ファイルの権限・モードの設定。falseで無視する。
######### core.hideDotFiles
######### core.ignoreCase
######### core.gitProxy
######### core.pager
######### core.worktre
######## user.email
- Your email address to be recorded in any newly created commits.
- user.email <email>
  オーサーEメールアドレスを設定する。
######## user.name
- Your full name to be recorded in any newly created commits.
- user.name <name>
  コミットのオーサー名を設定する。
####### Values
- boolean
  - true
  - false
- integer
- color
- pathname
####### Files
######## $(prefix)/etc/gitconfig
- システム全体の設定ファイル
######## $XDG_CONFIG_HOME/git/config
- リポジトリ毎の設定ファイル
######## ~/.gitconfig
- ユーザ固有ファイル
######## $GIT_DIR/config
####### Environment
######## GIT_CONFIG
######## GIT_CONFIG_NOSYSTEM
###### git-remote
###### git-replace
##### Interrogators
###### git-blame
#### Interactive with otehrs
##### git-svn
### Low-level / Plumbing
#### Manipulation
##### git-apply
##### git-commit-tree
##### git-mktag
#### Interrogation
##### git-cat-file
#### Synching repositories
##### it-daemon
#### Internal helper
##### git-check-attr
### tmp
#### git add
- 
  作業ディレクトリ内の変更をステージングエリアに追加するコマンド。
  git commitを実行するまでは変更が実際に記録されることはない。
  追跡対象にしたり、変更をステージしたりする。
- -p, --patch
  インタラクティブにパッチの一部を追加する。
  y:ステージする
  n:無視する
  s:より小さい部分に分割
  e:手作業で編集
  q:終了する
  ?:ヘルプ。他のコマンドを確認できる。
- i, --interactive
  インタラクティブにファイルを追加する。

#### git archive
アーカイブを作成する。
- <tree-ish>
  アーカイブするツリーやタグを指定する。HEADなど。
- --format=<fmt> 
  フォーマットを指定する。zip, tarなど。
- --prefix=<pfx>
  格納フォルダを設定する。

#### git bisect
- 
  二分探索する
- start
- bad
- good
- reset
- visualize
- log
- replay
- run
  テストスクリプトを投げ、テスト結果からgood/badを判断する。
  正常は0, スキップは125, 終了はそれ以外の正数値（普通は1)

#### git blame
- <file>
  各行ごとに、最後に編集した情報が出力される。
- L <start>,<end>
  出力する行を指定をする。
  "12,13"や、"12,+2"等の指定が出来る。
  正規表現の指定も出来るので、'"/<\/body>/",-2'等の表記も可能。
- -- <file>
  ファイル名の指定。ファイル名が変わった場合などに、以前のファイル名を指定するためのオプション。
    ex) git blame -L "/<\/body>/",-2 4333289^ -- hello.html
- -M
  移動された行や同ファイル内でコピーされた行も検出して出力する。
- -C -C
  ファイル間のコピーを検出できるようにする。

#### git branch
- 
  ブランチの作成、一覧表示、リネーム、削除を行うコマンド。
  何も指定しない場合、リポジトリ内のブランチを一覧表示する。
  ブランチは単なるコミットへのポインタで、ブランチを作成しただけではリポジトリは変更されない。
- <branch>
  <branch>という名称の新規ブランチを作成する。
- d <branch>
  指定したブランチを削除する。マージされていない変更が残っている場合は拒否される。
- D <branch>
  マージされていない変更が残っていても強制的に削除するコマンド。
- m <branch>
  現在のブランチの名前を<branch>に変更する。
- m <old> <new>
  <old>ブランチの名前を<new>に変更する。
- M <old> <new>
  <new>ブランチを<old>ブランチで上書きする（？）
- r
  リモートのブランチを表示する。
- a
  リモートとローカルのブランチ全てを表示する。
- v
  
#### git checkout
- 
  ファイルのチェックアウト、コミットのチェックアウト、ブランチのチェックアウトの
  3つの異なる機能を有するコマンド。
- <commit>
  コミットのチェックアウト
  作業ディレクトリ内の全てのファイルを、指定したコミットと同一の状態に更新するコミット。
  コミットハッシュまたはタグを仕様できる。
  "detached HEAD"状態。git checkout master等で、元のブランチに戻る。
- <commit> <file>
  ファイルのチェックアウト
  ファイルの過去のリビジョンをチェックアウトするコマンド。
  作業ディレクトリの他の部分に一切影響を与えることなくファイルの過去のリビジョンを確認できる。
  作業ディレクトリ自体は変更されてしまうので、変更が不要であればgit checkout HEAD <file>等で元に戻す。

- <existing-branch>
  ブランチのチェックアウト
  <existing-branch>が現在のブランチとなり、それと一致するように作業ディレクトリが更新される。
- b <new-branch>
  新規ブランチ<new-branch>を作成して即時チェックアウトするコマンド。
  git branch <new-branch> -> git checkout <new-branch> と同様。
- b <new-branch> <existing-branch>
  現在のブランチでなく、<exsiting-branch>を基点として作成する。
  タグも指定可。

#### git cherry-pick
- 
  別ブランチの1つのコミットだけを取得してマージする。
- -n
  コミットを控えるので、連続適用することで、いくつかのコミットをチェリーピックできる。

#### git clean
-
  追跡対象外のファイルを削除する。
  普通にrm等で削除してもよいが、利便性のために存在している。
  reset同様非可逆な操作となる。
- -n
  git cleanで削除されるファイルの一覧が表示される。実際には削除されない。
- -f
  追跡対象外のファイルをカレントディレクトリから削除するコマンド。
- -f <path>
  対象範囲を指定したパスに限定し、追跡対象外ファイルを削除する。

#### git clone
- 
  既存リポジトリのコピーを取得する
  git clone url [directory]
- --depth n <url>
  直近のnコミットだけをダウンロード

#### git commit
- 
  ステージされた変更をコミットする。
  SVNは差分を蓄積するが、Gitはスナップショットを取得する。
  - v diffの内容も表示する。
  - m インラインでメッセージを記載
  - a 追跡対象となっているファイルを追加してからコミット
- コミットメッセージ
  1行目にコミットの全体的説明を50文字以内で、2行目を空白行、3y合目以降に詳細を記述するのが標準的。
  ex:) Change the message displayed by hello.py
       
       - Update the sayHello() function to output the user's name
       - Change the sayGoodbye() function to a friendlier message
- --amend
  ステージされた変更を直前のコミットと結合し、
  その結果生成されるスナップショットで直前のコミットを置き換えるコマンド。
- -C <commit>
  指定した<commit>のメッセージを指定してコミットする。
- -c <commit>
  <commit>のメッセージを記入した状態でエディタが立ち上がる。

#### git fetch
- 
  変更をリモートリポジトリから取得するが、ローカルブランチにマージしない。

#### git gc
- 
  リポジトリの大きさを圧縮する
- --agressive
  デルタを一から再計算し、より強い最適化を実行する

#### git gui
- 
  GUIで編集・確認ができる。らしい。
  見れたことはない。

#### git help
- <verb>
  <verb>コマンドのヘルプを確認する。
  同様のコマンドに、git <verb> --help, man git-<verb>がある。

#### git init
- 
  Gitリポジトリを新たに作成するコマンド。
  git initは本来中央リポジトリを作成する際に一度だけ使用するものであり、
  ここの開発者がローカルリポジトリを作成する際はgit cloneしてコピーする。
- --bare
  作業ディレクトリを持たない空のGitレポジトリを作成できる。
  共有レポジトリは必ず--bareフラグを使用して作成する。
  ノンベアリポジトリにプッシュを行うと変更の誤書き込みを起こす可能性があるため。

#### git log
- 
  コミット履歴を表示する。

- -n <limit>
  表示するコミット数を<limit>に制限する。
- --oneline
  各々のコミット内容を1行に圧縮して表示するコマンド。
- --stat
  改変されたファイルおよびその中での追加行数と削除行数を増減数で表示する。
- -p
  各々のコミットに対するパッチを表示する。
- --author="<pattern>"
  特定のオーサーが行ったコミットを検索する。
- --grep="<pattern>"
  コミットメッセージが<pattern>(プレーンテキスト又は正規表現)と一致するコミットを検索する。
- --prety=format:"<fmt>"
  フォーマット指定する。
- --since="<time>"
  <time>以降のログを取得する。5 hours, 1 minute, 2008-10.01(!) 等で指定可能
- --before="<time>"
  <time>以前のログを取得する。
- <since>..<until>
  <since>と<until>の間に位置するコミットのみを表示する。
  2個の引数には、コミットID、ブランチ名、HEAD、その他任意のリビジョンリファレンスを用いることが出来る。
- <file>
  特定のファイルを含むコミットのみ表示する。
- --graph --decorate --oneline
  見やすくするための各種オプション

- -C -C -p
  コピーを検出する。

#### git merge
- 
  git branchで作成された独立な複数の開発ラインをひとつのブランチに統合するコマンド。
  以下では現在のブランチへのマージを行う。現在のブランチは更新され、ターゲットブランチはそのまま残る。
- <branch>
  指定したブランチを現在のブランチにマージするコマンド。
  マージアルゴリズムは自動的に選択される。（早送りマージか三方向マージ）
- --no-ff <branch>
  常にマージコミットを作成してマージする。
- --squash
  他のブランチから持ってきたコミットを、1つのコミットに圧縮して登録する。

#### git mergetool
- 
  マージを行うためのツールを立ち上げる。
  設定されたmerge.toolの値を見に行く。

#### git mv
- 
  ファイルを移動する。git mv <old> <new>
  実際は以下と一緒。
    mv file_from file_to
    git rm file_from
    git add file_to

#### git push
- 
  変更をoriginリポジトリの対応するブランチに送信する。
- --dry-run
  プッシュされる変更を確認する

#### git rebase
- <base>
  ブランチの基点となるコミットを別のコミットに移動する操作。
- i <base>
  インタラクティブなベースセッション。

#### git reflog
- Manage reflog information
- reflogという機能が働いていて、ブランチの先端に対する更新の追跡が行われており、
  いかなるブランチからもタグからも参照されていない更新内容であっても戻ることができる。

##### Synopsis
- git reflog <subcommand> <options>
##### Options
###### --all
###### -n, --dry-run
###### --rewrite
###### --verbose
#### git remote
リモート接続。リンクではなくブックマークのようなもの。
通常はHTTPプロトコルはリードオンリーで、プッシュが出来ない。
SSHは両方可能。
- 
  他のリポジトリへのリモート接続一覧が表示される
- v
  各々のURLも表示される
- add <name> <unl>
  リモートリポジトリに対する新規接続を作成するコマンド。
- rm <name>
  <name>リポジトリへの接続を削除するコマンド。
- rename <old-name> <new-name>
  <old-name>から<new-name>へリネームするコマンド。
- show <name>
  <name>リモートリポジトリの情報が表示される。
- prune <name>
  古くなったリモートリポジトリを取り除く

#### git reset
- 
  git resetコマンドを使用して元に戻ると、元の状態を復元する方法はない。
  そのため、ローカルな変更を元に戻す場合に限るべき。
  何も指定しない場合、作業ディレクトリに何の変更も加えず、
  ステージエリアをリセットして直前のコミット時の状態と一致させる。
- <file>
  指定したファイルをステージングエリアから削除するコマンド。
- --hard
  作業ディレクトリとステージエリアを直前のコミット時の状態と一致させるコマンド。
- <commit>
  ブランチの先端を<commit>の位置に戻しステージングエリアをその状態と一致するようにするが、
  作業ディレクトリはそのままにしておく。
- --hard <commit>
  <commit>位置に戻し作業ディレクトリもあわせる。

#### git revert
- <commit>
  <commit>により加えられたすべての変更を元に戻す新しいコミットを生成し、
  それを現在のブランチに適用するコマンド。

#### git rm
追跡対象からファイルを削除し、作業ディレクトリからも除く。
- --cached
  ステージ上からのみファイルを取り除く。
- f
  すでにステージされた変更も含めて削除したい場合。

#### git show
- 
  
#### git status
- 
  ステージされたファイル、ステージされていないファイル、追跡対象外のファイル一覧を表示する。

#### git submodule
（サブモジュールは使い方がいまいち不明）
- 
  サブモジュールを表示する
- add <url> <name>
  サブモジュールを追加する
- init <sbmdl>
  サブモジュールを初期化する
- update <sbmdl>
  サブモジュールを最新に更新する

#### git tag
- 
  タグを表示する
- <tagname>
  軽量版(lightweight)のタグをつける。
- -a
  注釈付きタグ(annotated)を作成する
- -am
  注釈付きタグにメッセージをつける
- -n
  メッセージ付きでタグを表示する
- -d <tagname>
  タグを削除する

## Options
### --version
### --help
### -C <path>
### --exec-path[=<path>]
## Evrironment Variables
### Git Repository
#### GIT_INDEX_FILE
#### GIT_INDEX_VERSION
### Git Commits
### Git Diffs
### other
## Tools
### Git LFS
#### Client
##### Commands
###### High level commands
####### git lfs env
####### git lfs checkout
####### git lfs clone
####### git lfs fetch
- Download Git LFS files from a remote.
####### git lfs fsck
####### git lfs lock
####### git lfs locks
####### git lfs logs
####### git lfs ls-files
- Show information about Git LFS files in the index and working tree.
######## Options
######### -l, --long
######### -s, --size
######### -d, --debug
######### -a, --all
######### --deleted
######### -I <paths>, --include=<paths>
######### -X <paths>, --exclude=<paths>
####### git lfs migrate
####### git lfs prune
####### git lfs pull
####### git lfs push
####### git lfs status
####### git lfs track
####### git lfs uninstall
####### git lfs unlock
####### git lfs untrack
####### git lfs update
####### git lfs version
###### Low level commands
####### git lfs clean
####### git lfs pointer
####### git lfs pre-push
####### git lfs smurge
##### Specification
- https://github.com/git-lfs/git-lfs/blob/master/docs/spec.md
##### Memo
###### git lfs help <command>, git lfs <command> -h
-
#### Server
##### API
- https://github.com/git-lfs/git-lfs/tree/master/docs/api
#### Link
- https://git-lfs.github.com/
- https://github.com/git-lfs/git-lfs
### GitHub
#### Webページの公開
- https://qiita.com/budougumi0617/items/221bb946d1c90d6769e9
##### GitHubPages - ユーザアカウントのページ
- Create a reository named "username.github.io"
  https://pages.github.com/
##### リポジトリごとのページ
- 以下どちらか
  - masterにdocsディレクトリを作る
  - gh-pagesブランチを切る
## Reverse lookup
### 変更を取り消す
- http://www-creators.com/archives/1116
#### コミットを戻す
- インデックス、ワークツリーを残す
  git reset --soft <commit>
- インデックスは戻す、ワークツリーは残す
  git reset --mixed <commit>
- インデックス、、ワークツリーも戻す
  git reset --hard <commit>
#### 打消しコミットを作る
- git revert
#### commitしたコメントを修正
- 最後のコメントを修正
  git commit --amend
#### 歴史の修正
- git rebase (-i) <commit>
#### ローカル
- git checkout file
  
  チェックアウトを選ぶ場合は、
  git checkout <code> file

### 普通にrmしたファイルをcommitに乗せる
- git rm <file>
  ファイルを消してしまって実体がいない場合でも、
  git rmで対象を削除、stageに乗せることができる。
  ただし既にファイルがない場合、globが効かないので*などで補完してくれない。

- git add -u
  削除コミット以外も含め一旦stagingに乗せる場合。
  その後不要なファイルはstagingから落とせばよい。
  (unstageはgit reset HEAD <file>...)

### gitで日本語ファイルを扱う
- core.quotepath を false とする。
- 例: git config --[global|local] core.quotepath false
- [[http://dev.classmethod.jp/tool/git/git-avoid-illegal-charactor-tips/][日本語ファイルの文字化けを回避する - Developers.IO]]
### 一部のフォルダのみを使う(sparse checkout)
- 1. configでsparsecheckoutを許す
  git config core.sparsecheckout true
- 2. 対象ディレクトリを設定する
  echo 目的のフォルダ > ./git/info/sparse-checkout

- https://mseeeen.msen.jp/git-sparse-checkout/
### 差分ファイルのみを抽出する
- git archive <rev> `git diff <rev0> <rev> --name-only --diff-filter=ACMR` -o <filename.like.zip>
- https://www.granfairs.com/blog/staff/git-archivediff
### 末尾の^M表示抑制
- 原因: 末尾のCRLF
  空白文字の扱いを決めるcore.whitespaceという設定があるが、blank-at-eolが有効だと改行コード前の空白文字をエラーとして報告する。
  デフォルトでCRは改行コードでなく空白文字として扱われるため、CRLFのCR部分が"blank-at-eol"に引っかかり^Mで反転表示される。
- 対応: 行末のCRを許容する設定
  git config --local core.whitespace cr-at-eol
- http://amano41.hatenablog.jp/entry/git-diff-treats-cr-at-eol-as-error
### 設定を削除する
- --unsetを使う。
  git config --unset core.filemode
## Memo
### Initialize Setting 初期設定
- git config --global user.name "your name"
- git config --global user.email "your.email@domain.com"
- git config --global core.filemode false  # ignore file mode like 755 and 644
- git config --global core.quotepath false # using Japanese file name
- git config --global core.editor vi

- git config --list  # check your settings (git config -l)

#### Local設定
- 現状確認 : git config -l --local
- ユーザ名設定 : git config --local user.name Name
- メール設定 : git config --local user.email Mail

### ~N
- 
  ~(チルダ)は親コミットの相対参照を行う場合に使用する。
  3157e~1は3157eの一つ前の親コミット、HEAD~3は現在のコミットの3つ前のコミット。
  "HEAD~10..HEAD"等指定してやると便利。

### ^
- 
  ^(キャレット)は一つ前をあらわす。
  "18f822e^"は"18f822e"のひとつ前のリビジョン、"18f822e^^^"は3つ前のリビジョンを表す。
  チルダと組み合わせて、"HEAD~1^^"や"HEAD^~2"なども可能。

### status
- 
  |--------------------+------------------+-------------------+-----------|
  | untractked         | unmodified       | modified          | staged    |
  |--------------------+------------------+-------------------+-----------|
  | add the file =>    |                  |                   |           |
  |                    | edit the file => |                   |           |
  |                    |                  | stage the file => |           |
  | <= remove the file |                  |                   |           |
  |                    |                  | <= commit         | <= commit |
  |--------------------+------------------+-------------------+-----------|

### .git/info/exclude
- 
  ローカルのレポジトリだけに生成されるものを除外する。
  すべてのレポジトリに生成されるファイルを除外するには、.gitignoreを使用する。

### タグとブランチの名前
- 先頭が.(ピリオド)であってはならない
- 末尾が/(スラッシュ)であってはならない
- 特殊文字の中には使えないものがある。
  スペース, ~(チルダ), ^(キャレット), ?(クエスチョンマーク), *(アスタリスク), [(開ブラケット), ASCIIの制御文字等
- ピリオドの連続(..)は使えない

### .gitignore
- 
  *はフォルダを跨がない。"/*/"は/test/local/には当てはまらず、/test/のみ当てはまる。
  **はフォルダを跨ぐ。"/**/"は/test/, /test/local/, /test/local/bin/すべてに当てはまる。
  
### git fetch
- https://qiita.com/Teloo/items/95a860ae276b49edb040
- https://qiita.com/osamu1203/items/cb94ef9da02e1ec3e921
## Link
- [[https://git-scm.com/book/ja/v2][Book - git]]
- [[https://github.com/Shinpeim/introduction-to-git][Gitをはじめからていねいに - Shinpeim/introduction-to-git - GitHub]]

- [[https://www.atlassian.com/ja/git/tutorial][Gitチュートリアル Atlassian]]

