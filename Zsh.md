# Zsh
## Built-in Functions
- See `man zshbuiltins`
### alias
### autoload
- 遅延評価でシェル関数を読み込むzshの機能
  ファイルシステム上にある関数定義を読み込む。
  探索するディレクトリは"FPATH"に入っている。
  -X, +X, -wなしの"functions -u"と等しい
- -U
  aliasの内部展開を行わない。
### bg
### bindkey
### break
### builtin
### bye
### cap
### cd
### chdir
### clone
### command
### comparguments
### compcall
### compctl
### compdescribe
### compfiles
### compgroups
### compquote
### comptags
### comptry
### compvalues
### continue
### declare
### dirs
### disable
### disown
### echo
### echotc
### echoti
### emulate
### enable
### eval
### exec
### exit
### export
### false
### fc
### fg
### float
### functions
- 
  -Mなしの"typeset -f"と等しい
### getcap
### getln
### getopts
### hash
### history
### integer
### job
### jobs
### kill
### let
### limit
### local
### log
### logout
### noglob
### popd
### print
### printf
### pushd
### pushln
### pwd
### read
### readonly
### rehash
### return
### sched
### set
### setcap
### setopt
### shift
### source
### stat
### suspend
### test
### times
### trap
### true
### ttyctl
### type
### typeset
- 変数宣言を行う。
- -f
  関数の宣言
- -g
  グローバルフラグ
- -u
  自動読み込みする
- -x
  宣言した変数が環境変数であることを意味する。
### ulimit
### umask
### unalias
### unfunction
### unhash
### unlimit
### unset
### unsetopt
### vared
### wait
### whence
### where
### which
### zcompile
### zformat
### zftp
### zle
### zmodload
### zparseopts
### zprof
### zpty
### zregexparse
### zsocket
### zstyle
### ztcp
  
## Options
- see `man zshoptions`
  use setopt, unsetopt, set -o, set +o
### Description
#### Changing Directories
##### AUTO_CD (-J)
- cdを入力せずcdできる
##### AUTO_PUSHD (-N)
- CD時にPUSHD
#### Completion
#### Expansion and Globbing
#### History
##### EXTENDED_HISTORY
##### HIST_IGNORE

##### HIST_IGNORE_DUPS (-h)
#### Initialisation
#### Input/Output
##### CORRENT (-0)
- 間違えてコマンド入力しても修正して確認、動作する
##### FLOW_CONTROL
##### PRINT_EIGHT_BIT
- 日本語ファイル名を表示可能にする
#### Job Control
#### Prompting
#### Scripts and Functions
#### Shell Emulation
#### Shell State
#### Zle
### Alias

### Single Letter Options
## Parameters
- See `man zshparam`
### Set by shell
### Used by shell
## Miscellaneous
- See `man zshmisc`
### Prompt conditional strings
#### Parameters
- parameter
  - %M
  - %m
  - %d
  - %~
  - %C
  - %c
  - %n
  - %#
  - %?
  - %D
  - %W
  - %w
  - %*
  - %T
  - %t
  - %F{color} %f
    colorized characters between %F and %f
  - %K{color} %k
    colorized background between %F and %f
    
#### Colors
- color
  - black   : 0
  - red     : 1
  - green   : 2
  - yellow  : 3
  - blue    : 4
  - magenta : 5
  - cyan    : 6
  - white   : 7
## Shell Functions
### default
- See folder '/usr/share/zsh/functions'
  load by 'autoload'
#### Calender
#### Chpwd
##### chpwd
- cd時に任意のコマンドを実行させられる。
#### Completion
##### compinit
#### Exceptions
#### MIME
#### Misc
##### colors
#### Newuser
#### Prompts
##### promptinit
#### TCP
#### VCS_Info
#### Zftp
#### Zle
## Modules
- See `man zshmodules`
## Tools
### zplug
- プラグインマネージャ
  
### Prezto
- フレームワーク。

### old
#### oh-my-zsh
- 設定フレームワーク。
  
#### Antigen
- プラグインマネージャ
#### zgen
- Antigenの改良版
## Link
- [[http://zsh.sourceforge.net/Doc/Release/index.html#Top][The Z Shell Manual]]
- [[http://news.mynavi.jp/column/zsh/][漢のzsh]]

- [[http://qiita.com/yuku_t/items/77c23390e52168a2754a][.zshrcで見かけるautoloadの意味と使い方 - Qiita]]

- http://qiita.com/ktr_type23/items/3eb782f98c7a5f4c60b0
- http://qiita.com/scalper/items/ed83c24f568cbf7f132b
- http://post.simplie.jp/posts/60
- http://tegetegekibaru.blogspot.jp/2012/07/blog-post_27.html
