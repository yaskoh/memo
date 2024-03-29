# Linux Commands (S-Z#)
## Commands (S-Z#)
### s
#### sar
- Collect, report, or save system activity information.
  sar [ options ] [ interval [ count ] ]
- sysstatパッケージに含まれている、システムの統計情報を取得するコマンド。
  System Admin Reporterの頭文字。
- topやvmstatと異なり、cronで定期実行することで過去の情報を保存、後から確認ができる。
##### Options
###### まとめ
- CPU : -u
- CPU core : -P (ALL)
- Load Average : -q
- Memory : -r
- Swap : -W, -S
- Network
  - Interface : -n DEV
  - Error : -n EDEV
  - Socket : -n SOCK
  - IP : -n IP
  - TCP : -n TCP
- DiskIO : -b
- Context switch : -w
###### -A
- This is equivalent to specifying "-bBdFHqRSuvwWy -I SUM -I XALL -m ALL -n ALL -r ALL -u ALL -P ALL"
###### -B
###### -f [ filename ]
- Extract records from filename.
###### -o [ filename ]
- Save the readings in the file in binary form.
###### -P { cpu [,...] | ALL }
- Report per-processor statistics for the specified processor or processors.
###### -q
- Report queue length and load averages
####### runq-sz
- 実行待ちキューに入っているプロセス数
####### plist-sz
- プロセスリスト中のプロセス数とスレッド数
####### ldavg-1
- 直近1分のロードアベレージ
####### ldavg-5
- 直近5分のロードアベレージ
####### ldavg-15
- 直近15分のロードアベレージ
####### blocked
###### -u [ ALL ]
- Report CPU utilization. ALL keyword indicates that all the CPU fields should be displayed.
####### fields
######## %user
- ユーザが利用しているCPU使用率
######## %usr
######## %nice
- nice値を変更しているプロセスのCPU使用率
######## %system
- システムが利用しているCPU使用率
######## %sys
######## %iowait
- IO待ちしているしているCPU使用率
######## %steal
- ゲストOSが割り当て要求をし、割り当てられなかったCPU
######## %irq
######## %soft
######## %guest
######## %gnice
######## %idle
- 待機中のCPU使用率
##### Link
- http://makaaso.hatenablog.com/entry/2015/07/31/171740
- http://naoberry.com/tech/sar/
- https://qiita.com/hana_shin/items/6f00ca48a8de90478f88
#### scp
- scp [[user@]sourcehost1:]filename1 ... [[user@]desthost2:]filename2
  データコピーを安全に行う。
  sshを使ってデータをコピーする。

- -F ssh_config
  sshの設定ファイルを指定する。

- Wildcardを使う方法
  サーバ側がglobで解釈できるよう、エスケープして渡す。
  ex) scp 'SERVERNAME:/DIR/\*' .

#### screen
- screen manager with VT100/ANSI terminal emulation
##### Synopsis
- screen [-options] [cmd [args]]
- screen -r [[pid.]tty[.host]]
- screen -r sessionowner/[[pid.]tty[.host]]
#### seq
- usage
  - seq [OPTION]... LAST
  - seq [OPTION]... FIRST LAST
  - seq [OPTION]... FIRST INCREMENT LAST

- about
  Print numbers, from FIRST to LAST, in steps of INCREMENT.

- options
  - -f, --format=FROMAT
    use printf style floating-point FORMAT
  - -s, --separator=STRING
    use STRING to separate numbers (default: \n)
  - -w, --equal-width
    equalize width by padding with leading zeros
  - --help
  - --version

#### service
- 
  指定されたLinuxデーモンの起動や停止、ステータスの確認を実行する。
  中身はシェルスクリプト。
#### set
- set [-options] [-o options]
  シェルのオプションを設定する。環境変数とシェル変数どちらも表示されるため、"env"との差分がシェル変数となる。
  -aのように位置文字で設定する場合と、-oの後にスペースを空けて単語を指定する2種類の書式が存在する。
  「-」の代わりに「+」を用いると意味が逆になる。
#### setfont(8)
- load EGA/VGA console font
- 引数なしで使うとデフォルトに戻る。
- ex) setfont Lat2-Terminus16
#### sh(dash)
- 
  'sh -c -x "コマンド内容"'などととすることで、
  シェルがどのようにコマンドを展開しているか理解するのに役立つ。
  
  パイプで受け取った入力をコマンドとして実行するのに利用できる。

- -c
  Read commands from the command string operand instead of from the standard input.
  
- -x xtrace
  Write each command to standard error befor it is executed. Useful for debugging.

#### shopt
- Bash built-in.
- (no-option)
  オプション一覧を表示
- -s Options
  set
- -u Options
  unset
##### Options
###### autocd
###### expand_aliases
- If set, aliases are expanded as described below under Aliases.
##### Link
- [[https://www.gnu.org/software/bash/manual/html_node/The-Shopt-Builtin.html][The Shopt Builtin - Bash Reference Manual]]
#### showconsolefont(8)
- Show the current EGA/VGA console screen font
#### showkey(1)
- examine the codes sent by the keyboard
##### Options
###### -h, --help
###### -a, --ascii
- 'ascii' dump mode.
###### -s, --scancodes
- Starts showkey in scan code dump mode.
###### -k, --keycodes
- Starts sohwkey in keycode dump mode. default.
#### sftp
- 
  interactive file transfer program, similar to ftp.
  performing all operations over an encrypted ssh transport.
  
##### interactive commands
- bye
- cd path
- chgrp grp path
- chmod mode path
- chown own path
- df [-hi] [path]
- exit
- get [-P] remote-path [local-path]
- help
- lcd path
  change local directory to 'path'
- lls [ls-options [path]]
  Display local directory listing
- lmkir path
  Create local directory
- ln oldpath newpath
- lpwd
  print local working directory
- ls
- lumask umask
- mkdir path
- progress
  Toggle display of progress meter
- put [-P] local-path [remote-path]
  Upload file
- pwd
- quit
- rename oldpath newpath
- rm path
- rmdir path
- symlink oldpath newpath
- version
- !command
  Execute 'command' in local shell
- !
  Escape to local shell
- ?

#### sort
- sorts the contents of a text file, line by line.

##### Options
###### -c, --check
- Check for sorted input; do not sort.

###### -d, --dictionary-order
- Consider only blanks and alphanumeric characters.

###### -f, --ignore-case
- Fold lower case to upper case characters.
  
###### -k, --key=POS1[, POS2]
- start a key at at POS1 (origin 1), end it at POS2 (default end of line)

###### -n, --numeric-sort

###### -t, --field-separator=SEP
- use SEP instead of non-blank to blank transition

###### -r, --reverse

###### -u, --unique
- With -c, check for strict ordering; without -c, output only the first of an equal run.

#### source
- 
  "source filename"で、filenameで指定されたスクリプトファイルを実行する。
  ファイルの内容を、自分で手で打っていくのと同じ。
  
  子プロセスの変数を親プロセスで使う場合に利用することができる。

#### split
- 
  ファイルを分割する。
  usage: split [-b bytes[bkm]] [infile [outfile-prefix]]

- -b bytes[bkm]
  bytesで示したバイト数で分割する。

- -l 行数
  指定した行数ごとに分割

- infile
  元ファイルを指定する

- link
  [[http://itpro.nikkeibp.co.jp/article/COLUMN/20060227/230888/][【split】ファイルを分割する - Linuxコマンド集]]

#### ss
- Socket Statistics、旧netstat相当の機能。
#### ssh
- secure shell.
##### Options
###### -D [bind_address:]port
- Specifies a local "dynamic" application-level port forwarding.
- ダイナミックポートフォワーディング

###### -L LocalPort:RemoteHost:RemotePort
- port forwarding.
  ex) ssh -L 8080:192.168.111.200:8080 User@192.168.111.1

###### -R LocalPort:RemoteHost:RemortPort
- like -L option, but port is opened in remote server.

###### -N
- Do not execute a remote command. This is useful for just forwarding ports.
###### -g
- Allows remote hosts to connect to local forwarded ports.

###### -p
- connection port setting
  ex) ssh user@192.168.100.1 -p 8080

###### -o options
- see config explanation, or "man ssh-config"
###### -X
- Enables X11 forwarding.
##### Memo
###### config
- write down port forwarding settings to  ~/.ssh/config or /etc/ssh/ssh_config
  and not to need to set everytime to connect.
- see "man ssh-config"

####### Description
######## Host
- Restricts the folowing declarations to only for those hosts that match one of the patterns given after the keyword.
######## HostName
######## Port
######## User
######## IdentityFile
######## IdentitiesOnly
- yes / no
######## LocalForward
######## DynamicForward
######## PubkeyAuhtentication
- Specifies whether to tory public key authentication
- value: yes / no
######## StrictHostKeyChecking
######## TCPKeepAlive
- yes / no
####### Ex
- ex1
  Host server1
    HostName     192.168.11.101
    Port         2222
    User         user01
    IdentityFile ~/.ssh/server1/id_rsa

###### .ssh on win
- ssh try to see settings on /home/username/.ssh.

###### pubkeyを使わずログインしたい場合
- "ssh -o PubkeyAuthentication=no"
- https://qiita.com/smallpalace/items/a29ee4a3b170804355b9
#### ssh-add
- adds private key identities to the authentication agent, ssh-agent.
##### Synopsis
- ssh-add [-cDdkLlXx] [-E fingerprint_hash] [-t life] [file ...]
- ssh-add -s pkcs11
- ssh-add -e pkcs11
##### Options
###### -l
- Lists fingerprints of all identities currently represented by the agent.
#### ssh-agent
- authentication agent
  ssh-agent is a program to hold private keys used for pubilc authentication.
- Synopsis
  - ssh-agent [-c | -s] [command [arg ...]]
##### Memo
- 起動
  ssh-agent bash(任意のシェル)
  バックグラウンドでagentが動作し、指定されたシェルを起動。
- 秘密鍵の登録
  ssh-add ~/.ssh/id-rsa
- 転送機能
  ssh -A
  .ssh/configに"ForwardAgent yes"と書いても同様。
- https://qiita.com/isaoshimizu/items/84ac5a0b1d42b9d355cf
#### ssh-copy-id
- use locally available keys to authorise logins on a remote machine
- SSH接続先のサーバに公開鍵を設定する
##### Synopsis
- ssh-copy-id [-f] [-n] [-i [identity_file]] [-p port] [-o ssh_option] [user@]hostname
- ssh-copy-id -h | -?
##### Options
###### -i identity_file
###### -f
###### -n
###### -p port
###### -o ssh_option
- see "ssh -o" option
#### ssh-keygen
- 認証用の鍵を生成、管理、および変換する。

#### sshd
- daemon program for ssh.
##### Descriptions
###### Options
###### Authentication
###### Login Process
###### sshrc
###### authorized_keys
###### ssh_known_hosts
###### Files
##### sshd_config
- https://euske.github.io/openssh-jman/sshd_config.html
###### 
####### Port
####### AddressFamily
####### ListenAddress
####### Protocol
####### HostKey
###### Ciphers and keying
###### Logging
####### SyslogFacility
- Values:
  - DAEMON
  - USER
  - AUTH
  - LOCAL0-7
####### LogLevel
- Values:
  - QUIET
  - FATAL
  - ERROR
  - INFO
  - VERBOSE
  - DEBUG
  - DEBUG1
  - DEBUG2
  - DEBUG3

##### Memo
###### サービスをリスタートしても接続は切断しない
- sshdのルートプロセスのみが消え、代わりにinitが親プロセスとなり、子プロセスは再起動対象となる。
  http://equj65.net/tech/sshdprocess/
#### stat
- 
  display file or file system status

#### stop
- [%jobsid]
  バックグラウンドで停止するコマンドのジョブ番号を指定する

#### strace
- 
  動作中のプログラムが呼んだシステムコールを表示してくれる。

#### strings
- print the strings of printable characters in files.
#### strip
- Discard symbols from objet files.
- オブジェクトファイルからシンボル(デバッグ用のデータ)を切り捨てる。

#### stty
- 
  端末ラインの設定を変更・表示する

- -a
  すべてのオプション設定の現在の状態を標準出力に書き出す

- memo
  デフォルトでCtrl-sにstop機能が割り当てられており、キー入力が受け付けられなくなる可能性がある。
  Ctrl-qでstartとなるので、再度入力ができるようになる。
  無効とするには、"stty stop undef"とする。

#### su
- 
  ユーザを切り替える。

- -, -l, --login 
  シェルをログインシェルにする。
  
- 
  "su"だと、環境をuserから引き継ぐ。
  "su -"だと、rootの環境となる。

#### sudo
- execute a command as another user
##### Synopsis
- sudo -h | -K | -k | -V
- sudo -v [-AknS] [-h host] [-p prompt] [-u user]
- sudo -l [-AknS] [-h host] [-p prompt] [-u user]
- sudo [-AbEHnPS] [-AknS] [-h host] [-p prompt] [-u user]
##### Description
##### Options
###### -U user, --other-user=user
- Used in conjunction with -l option to list the privileges for user instead of for the invoking user.

###### -u user, --user=user
- Run the command as a user other than the default target user.
#### svn
- [[file:Subversion.org][Subversion.org]]
#### sync
- sync
  force completion of pending disk writes
#### sysctl
- 
  system settings
  /proc/sys/net/ipv4/ip_forward -> net.ipv4.ip_forward (in /etc/sysctl.conf)

### t
#### tail
- 
- -n, --lines=K
  output the last K lines, instead of the last 10

- -f, --follow[={name|descriptor}]
  output appended data as the file grows;

- -F
  same as --follow=name --retry

#### tar
- 
  ファイルを書庫化、展開する。
  - メインオプション
    - -A, --catenate
      tarファイルを書庫に追加する
    - -c, --create
      書庫を新規作成する
    - -d, --diff
      書庫とファイルシステム比較する
    - --delete
      書庫内からファイルを削除する
    - -r, --append
      書庫の後部にファイルを追加する
    - -t, --list
      書庫の内容を表示する
    - -u, --update
      新しいファイルのみ追加する
    - -x, --extract
      書庫内からファイルを取り出す
  - その他
    - -f
      ファイルを指定
    - -v, --verbose
      ファイル一覧を詳細に表示
    - -C, --directory=DIR
      change to deriectory DIR
  - 形式別圧縮解凍(最近は自動判断)
    - -z
      tar + gzip
    - -j
      tar + bzip2
    - -J
      tar + xz

#### tc
- 
  show / 
#### tcpdump
- 

- -i [interface]
  select inetrface 

- -w [filename]
  output results to file.

- -r [filename]
  read from file

- -A
  show packet by ASCII
  
- -p
  execute not being promiscous mode
  
##### expression
- type
  host, net, port
- dir
  src, dst, src or dst, src and dst
- proto
  ether, fddi, mopdl, ip, ip6, arp, rarp, decnet, lat, sca, moprc, mopdl, icmp, icmp, tcp, udp
  
#### tee
- 
  標準入力から読み込んだ内容を、標準出力とファイルの両方へ出力する。

#### telnet

#### test, [
- 

- Expression
  - exp1 -a exp2
    both exp1 and exp2

  - exp1 -o exp2
    either exp1 or exp2

- String
  - [-n] string
    the length of string is nonzero

  - -z string
    the length of string is zero

  - STRING1 = STRING2
    the strings are equal

  - STRING1 != STRING2
    the strings are not equal

- Integer
  - INTEGER1 -eq INTEGER2
  - INTEGER1 -ge INTEGER2
  - INTEGER1 -gt INTEGER2
  - INTEGER1 -le INTEGER2
  - INTEGER1 -lt INTEGER2
  - INTEGER1 -ne INTEGER2

- File
  - FILE1 -ef FILE2
    FILE1 and FILE2 have the same device and inode numbers

  - -b FILE
    FILE exists and is block special

  - -c FILE
    FILE exists and is character special

  - -d FILE
    FILE exists and is a directory

  - -f FILE
    FILE exists and is a regular file

- Return
  set $? as 0(true) or 1(false)

- Link(temp)
  - http://linux.about.com/library/cmd/blcmdl1_test.htm

#### time
- run programs and summarize system resource usage
#### top
- 
  CPUのプロセスをリアルタイムで表示する。
- 
  |----------+-----------------------------------------------|
  | 表示項目 | 説明                                          |
  |----------+-----------------------------------------------|
  | PID      | プロセスID                                    |
  | USER     | プロセスを実行しているユーザ名                |
  | PRI      | 優先度                                        |
  | NI       | ナイス値                                      |
  | SIZE     | 仮想イメージの大きさ                          |
  | RSS      | 使用中の物理メモリー量                        |
  | SHARE    | 使用中の共有メモリー量                        |
  | STAT     | プロセスのステータス。                        |
  |          | Rは実行可能、Sは停止、Dは割り込み不可の停止、 |
  |          | Tは停止またはトレース中、Zはゾンビプロセス、  |
  |          | Wはスワップアウトしたプロセス、               |
  |          | Nはナイス値が正であることを表す               |
  | LIB      | ライブラリが使用するページサイズ              |
  | %CPU     | CPU占有率                                     |
  | %MEM     | メモリー占有率                                |
  | TIME     | プロセス開始からの実行時間                    |
  | COMMAND  | タスクのコマンド名                            |
  |----------+-----------------------------------------------|

- -c

#### touch
- touch [options] file...
  change file timestamp

- -a, --time=atime, --time=access, --time=use
  change access time only.
- -c, --no-create
  not creating a new file when target file is not exist
- -d, --date time
  
- -t MMDDhhmm[[CC]YY][.ss]

#### tmpwatch
- tmpwatch time dirs
  removes files which haven't been accessed for a period of time
  recursively removes files which haven't been accessed for a given time.

#### tr
- translate or delete characters
- Format
  tr [OPTION]... SET1 [SET2]

- Ex
  - echo abcde | tr '[a-z]' '[A-Z]' -> ABCDE

#### trap
- 
  システム割り込み時の処理を設定する。
- -l
  シグナル名と対応する番号の一覧を表示する
- -p
  単独で用いた場合、現在各シグナルに対して設定されている処理内容を表示する。

#### true
- Return true value
#### tty
- 
  どの端末が割り当てられたか確認する

#### type
- 
  コマンドに関する情報を表示する
- -a
  コマンドのパス名として、実際に起動されるパス以外にその他のパスも表示する。
- -p
  コマンド名を指定した場合に、実行されるファイル名を表示する。
- -t
  コマンドの型を表示する
  alias, shell builtin, file, function, keywordがある。

#### tzselect
- 
  タイムゾーンを選択する。

### u
#### ufw
- Uncomplicated FireWalls
  tools for iptables settings on Ubuntu. / Frontend of iptables
#### umask
- 
  The user file-creation mask is set to mode.
  If mode begins with a digit, it is interpreted as an octal numbers;
  otherwise it is interpreted as a symbolic mode mask similar to that accepted by chmod.

#### umount / unmount
- 
  unmount file systems

#### unalias
- unalias name
- コマンドの別名を抹消する
#### uname
- 
  OSやCPUのアーキテクチャ、ホスト名、カーネルバージョン等のシステム情報が表示される。
- -a
  全ての情報を表示する。
- -n
  ホスト名を表示する

#### uniq
- 
  reporting or filtering out repeated lines in a file.
  
  uniq does not detect repeated lines unless they are adjacent.
  You may want to sort the input first, or use "sort -u" instead of "uniq".

- -c, --count
  Prefix lines with a number representing how many times they occurred.

- -d, --repeated
  Only print duplicated lines.

- -i, --ignore-case
  This option performs case-insensitive comparisons.

- -u, --unique
  Only print unique lines.

#### unset
- 
  指定した変数や関数を削除する。
  ただし、シェルが始めから利用している変数や
  readonlyが指定されている変数は削除できない。

#### updatedb
- 
  locate用ファイル・データベースを更新する。

#### uptime
- 
  show how long the system has been runnning.
  this is the same information contained in the header line displayed by w.
  - Current time, The actual up time, How many users logged in, The load average
  - Path : (Mac)/usr/bin/uptime

#### useradd
- 
  新規ユーザの作成
- -s
  shellを設定する。
- -g 
  主グループを設定する。
- -G
  主でないグループを設定する。複数設定可。
- -m, --create-home
  ホームディレクトリが存在しない場合に作成する。
- -k, --skel
  -mと同時に指定すると、指定したフォルダ以下のファイルがコピーされる。
  指定しない場合は/etc/skel以下をコピー。
  The skelton direcotry
- -d, --home-dir HOMEDIR
  The new user will be created using HOME_DIR as the value for the user's login directory.

- ex)
  - useradd -d /user1 -m -g user1 user1

#### userdel
#### usermod
- usermod [options] LOGIN
  modify a user account
- -a, --append
  Add the user to the supplementary group(s)

- -c, --comment COMMENT
- -d, --home HOMEDIR
- -g, --gid GROUP
- -l, --login
- -L, --lock
- -p, --password
- -s, --shell SHELL
- -u, --uid UID
### v
#### vgdisplay
- 
  display attributes of volume groups

#### vgextend
- 
  add physical volumes to a volume group

- ex)
  sudo vgextend centos /dev/sdb1
  
#### vgs
- 
  report information about volume groups

#### vigr
- 
  edit /etc/group

#### vim
- [[file:Vim.org][Vim.org]]
#### vipw
- 
  edit /etc/password

- -s
  edit /etc/shadow

#### visudo
- 
  Edit /etc/sudoers.
  
  Format: User Host=(Permisson) Command
  ex) root ALL=(ALL) ALL

#### vmstat
- vmstat (options) [interval [times]]
  システム内の情報を表示するコマンド。

- Options
  - -f
    fork数を表示する
  - -n
    ヘッダを一度だけ表示する
  - -s
    書く情報を詳しい上毛名と共に表示する
  - -d
    ディスクに関する統計を表示する
  - -S 単位
  
##### Status
###### オプションなし
- procs : アクティブなプロセスに関する統計
  - r : 実行待ち状態にあるプロセス数
  - b : 割り込み不可能なスリープ状態にあるプロセス数
  - w : スワップアウトされており、実行可能なプロセス数
- memory : メモリーの使用量と仕様可能量に関するデータ
  - swpd : 仮想メモリ―量
  - free : 空きメモリ―量(Kバイト)
  - buff : バッファとして用いられているメモリー量(Kバイト)
  - cache
- swap : スワップに関する統計
  - si : ディスクからスワップインしているメモリー量(Kバイト/秒)
  - so : ディスクにスワップしているメモリー量(Kバイト/秒)
- iO : デバイスとの転送量
  - bi : ブロック・デバイスから受け取ったブロック数(ブロック/秒)
  - bo : ブロック・デバイスから送られたブロック数(ブロック/秒)
- system : システム全体の割り込みおよびコンテキストの切替レート
  - in : 毎秒の割り込み回数
  - cs : 毎秒のコンテキスト・スイッチ回数
- cpu : CPUの使用量の割合
  - us : ユーザー時間
  - sy : システム時間
  - id : アイドル時間
  - wa : IO待ち時間

### w
#### w
- 
  ログインユーザ名とその利用状況を表示する。

#### w3m
- 
  pager / text-based web-browser.

#### wall
- wall [-n] [ message ]
  send a message to everybody's terminal
  a message to everybody logged in with their mesg(1) permission set to yes.

#### wc
- 
  ファイルのバイト、行、文字および単語をカウントする。
  行数・単語数・文字数・バイト数・ファイル名の順に、オプション指定された情報だけ表示する。
- -c
  バイト数を出力する。
- -l
  行数を出力する。改行コードの数を行数とみなす。
- -m
  文字数を出力する。マルチバイト文字も1文字としてカウントする。
- -w
  単語数を出力する。単語数はスペース、タブおよび改行で区切られた文字列の数とする。

#### wget
- ファイルをダウンロードする。
  wget [option] URL

##### Options
###### Download Options
####### --user=user
- Specify the username "user"
####### --password=password
- Specify the password "password"
###### Directory Options
###### HTTPS (SSL/TLS) Options
####### --no-check-certificate
- Don't check the server certificate against the available certificate authorities.
###### Recursive Retrieval Options
####### -r, --recursive
- 配下全てのデータを取得する。再帰的にファイルを入手する。

####### -l depth, --level/depth
- 再帰的にファイルを入手する場合の階層数を指定する。

###### Recursive Accept/Reject Options
####### -np, --no-parent
- Do not ever ascend to the parent directory when retrieving recursively.

##### Memo
###### SSLサイトから取得
- wget --no-check-certificate <URL>
###### BASIC認証のかかったサーバから取得
- wget --http-user={username} --http-passwd={passwd} {url}
##### Link
- [[http://qiita.com/hirohiro77/items/b774908436ec032df719][wgetでこういう時はこうする!! - Qiita]]
- [[http://webos-goodies.jp/archives/51277893.html][wget で認証付きサイトをダウンロードする - WebOS Goodies]]

#### whatis
- 
  show summary of man, searched from command names.
  簡単な説明とキーワードを含むデータベースを検索し、結果を出力する。

#### whereis
- 
  コマンドのバイナリ、ソース、manページの場所を示す。

#### which
- 
  コマンドのフルパスを表示する。パスが通っているもののみ。
  （パスが通っていないものについては、findやlocateを使用するとよい。）

#### who
- 
  現在ログインしているユーザ情報を表示する

#### write
- write user [ttyname]
  send a message to another user
  to communicate with other users.

### x
#### xauth
#### xhost
- 
  "xhost +host_name"とすると、host_nameからもXサーバにアクセス可能となる。
  "xhost +"とすると全てのホスト（世界中）からアクセス可能となり、スクリーンショットを取ったりプログラムを表示・キーストロークを盗むことが可能となるので、xauthを使う方が望ましい。
  
#### xxd
- 16進ダンプの作成、再変換
##### Options
###### -a, -autoskip
###### -b, -bits
###### -h, -help
###### -r, -revert
- 16進ダンプからバイナリ形式に変換。
#### xz / unxz

### y
### z
#### zip / unzip
### #
#### .
- 
  identical to the source function.
  sourceと同様、カレントシェルで実行が行われる。
  shではsourceがない場合があるようなので、.を利用する。
  
#### !
- !!
  直前に実行したコマンドを再実行する。
- !num
  historyで表示される番号を実行する。
- ![char]
  最後に実行した[char]に当てはまるコマンドを実行する。
  
#### [
- see "test"


