# Linux Commands (A-I)
## Commands (A-I)
### a
#### adduser
- 
  Create a new user or update default new user information.
  
  In Debian, this command works as an interactive way of user adding.
  CentOS or Fedora, this command may not exist, or just a link to "useradd" command.

#### add-apt-repository
- Adds a repository info the /etc/apt/sources.list or /etc/apt/sources.list.d or romeves an existing one
- Synopsis
  - add-apt-repository [OPTIONS] REPOSITORY
#### alias
- 
  別名をつける。

#### apropos
- 
  show result searched from summaries and command names.
  whatisデータベースより文字列を検索する。

#### apt
#### apt-cache
#### apt-get
#### apt-key
- APT key management utility
##### Commands
###### add filename
- Add a new key to the list of trusted keys.
  filename or if the filename is - from standard input.
###### del keyid
###### export keyid
###### exportall
###### list
- List trusted keys.
###### finger
###### adv
###### update
###### net-update
#### aptitude
#### ar
- create, modify, and extract from archives
##### Options
###### t
- Display a table listing the contents of archives
###### x
- Extract members from the archive.
#### as
- ASsembler
  binutilsに属している。
##### Options
###### -v
- Verbose
###### -o
- Output file name
### b
#### basename
- 
  extract filename from path strings.

#### bc
- An arbitrary precision calculator language
##### Options
##### Special Variables
###### scale
###### ibase
- base input number. default: 10.
###### obase
- base output number. default: 10.
###### last
#### bg
- [%jobsid]
  ジョブをバックグラウンドで実行するよう切り替える。

#### blkid
#### bzip2 / bunzip2
### c
#### cat
- 
  Concatenate FILES(s), or standard input, to standard output.
- -A, --show-all
  equivalent to -vET
- -e
  equivalent to -vE
- -E, --show-ends
  display $ at end of each line
- -t
  equivalent to -vT
- -T, --show-tabs
  display TAB characters as ^I
- -v, --show-nonprinting
  use ^ and M- notation, except for LFD and TAB

#### chgrp

#### chkconfig
- 
  起動スクリプトを管理する。
  chkconfig service [on/off/0-6]

- -l, --list
  ランレベルごとの起動スクリプトごとの状態を表示する。

- -a, --add
  起動スクリプトを管理対象として追加する。

- -d, --del
  起動スクリプトを管理対象から削除する。

- --level
  各ランレベルにおける起動スクリプトの状態を設定する。

- --help, -h
  使用方法を表示する。

- --version, -v
  コマンドのバージョンを表示する。
##### run level
- 0 : インスタンス停止
- 1 : シングルユーザーモード
- 2 : ネットワーク通信なしのマルチユーザーモード
- 3 : マルチユーザーモード（通常の起動状態）
- 4 : 未使用
- 5 : グラフィカルユーザーインターフェースが起動する状態
- 6 : インスタンス再起動

#### chmod
- 
  アクセス権限の変更。

  u:所有者 g:グループ o:その他すべて a:すべての権限
  +:権限付与 -:権限削除 =:権限の書き換え
  r:読み込み w:書き込み x:実行 s:セットID t:スティッキービット

  - SUID
    SUID(Set User ID)は特殊なパーミッションのひとつで、
    実行可能ファイルに設定する。
    実行権にRootユーザのユーザIDをセットできる。
    u+s, 4xxx
  - SGID
    SGID(Set Group ID)は特殊なパーミッションのひとつで、
    実行可能ファイルおよびディレクトリに設定する。
    実行権にGroupのグループIDをセットできる。
    g+s, 2xxx
  - スティッキービット
    特殊なパーミッションのひとつで、ディレクトリに対して設定する。
    書き込み権限があっても、自分以外のユーザが所有するファイルを削除できなくなる。
    o+t, 1xxx

#### chown
- chown [user][:.][group] file
  ファイルやディレクトリの所有者を変更する。
  グループも同時に変更可能。
  グループのみの変更は、":group"もしくは".group"と指定する。

- -v, --verbose
  所有者の変更詳細を表示する。

- -R, --recursive
  ディレクトリとその中身を再帰的に変更する。

#### chroot
     ルートディレクトリを変更してコマンドを実行する。
     chroot directory [command [args]]

#### clang
- C, C++ and Objective-C compiler
- Synopsis
  clang [options] filename a|
##### Description
###### Driver
###### Preprocessing
- handles tokenization of the input source file, macro expansion,
  #include expansion, other preprocessor directives.
- Output
  - a.ia (C)
  - a.iia (C++)
  - a.mia (Objective-C)
  - a.miia (Objective-C++)
###### Parsing and Semantic Analysis
- parses input file, translating preprocessor tokens into a parse tree.
###### Code Generation and Optimization
- translates an AST into low-level intermediate code and ultimately to machine code.
###### Assembler
- target assembler to translate the output of the compiler into a target object file.
###### Linker
- the target linker to merge multiple object files into an executable or dynamic library.
##### Options
###### Stage Selection Options
####### -E
- Run the preprocessor stage.
####### -fsyntax-only
####### -S
- Run the previous stages as well as LLVM generation and optimization stages and target-specific code generation, producing an assembly file.
####### -c
- Run all of the above, plus the assembler, generating a target a.oa object file.

####### (no stage selection)
- all stages above are run, and linker is run to combine the results into an executable or shered library.
###### Language Selection and Mode Options
###### Target Selection Options
###### Code Generation Options
###### Driver Options
####### -save-temps
- save intermediate compilation results
###### Diagnostics Options
###### Preprocessor Options
#### clear
   
#### col
- 改行コードなどのエスケープシーケンスをフィルタし、変換・削除するコマンド。
  manページをテキストファイルに出力する場合によく利用される。

#### cp
- 
  
- -i
  
- -p
#### cpp
- プリプロセッサ
##### Options
###### -D
- コマンド上でのマクロ指定
  -Dxxxx=yyy
###### -H
- インデント形式でインクルードの状況を表示
###### -M
- Makefile形式で外部依存ファイルリストを表示
###### -v
- verbose
###### -nostdinc
- NO StanDard INClude files
  既定のCプリプロセッサ内部のヘッダーファイル探索パスをリセットするためのオプション
###### -I
- 探索パスの追加。Include
  -Iディレクトリ名
###### -I-
- セパレータ。
  これより前で定義されたパスはローカルヘッダーファイル用の探索パス、
  後方で定義されたパスはシステムヘッダーファイル、ローカルへだーファイル双方に対するパスとして登録される。
  利用する場合、デフォルトのカレントディレクトリに対する探索パスは削除されるため注意。
  明示的にカレントディレクトリを指定する場合、"-I./"と指定する。
###### -dM
- ソースファイル中で定義されている全てのマクロについて、宣言文を表示する
#### crontab
- maintain crontab files for individual users
##### Synopsis
- crontab [-u user] file
- crontab [-u user] [-i] {-e | -l | -r}
##### Options
-
#### cu
- Call up another system
##### Synopsis
- cu [options] [system|phone|"dir"]
##### Commands
###### ~.
- Terminate the conversation
###### ~! command
- Run command in a shell
###### ~$ command
- Run command, sending the standard output to the romete system.
###### ~| command
- Run command, taking the standard input from the remote system.
###### ~+ command
- Run command, taking the standard input from the remote system and sending the standard output to the remote system.
###### ~?
- List all commands
##### Options
###### -l line, --line line
- Name the line to use by giving a device name.
#### curl
##### Options
###### -f, --fail
- ()Fail silently on server errors.
###### -L, --location
- (HTTP/HTTPS) If the server reports that the requested page has moved to a different location, 
  making curl redo the request on the new place.
###### -s, --silent
- Silent or quiet mode. Don't show progress meter or eror messages.
###### -S, --show-error
- Whet used with -s it makes curl show an error message if it fails.
#### cut
- 
  特定の文字で区切られた項目を分割する。
  文字列の中から所定の位置にある特定の項目を抜き出したい場合に利用する。
  cut [option] [file]

- -c 文字数
  切り出す文字数を指定する。

- -d 文字
  区切り文字を指定する。デフォルトはタブ。

- -f フィールド数
  切り出すフィールド数を指定する。

- -s
  区切り文字を含まない文字列は出力しない。

- --compliment

- --outputdelimiter 'delimiter'
  デリミタを変更した形で出力する

##### examples
- select columns for characters
  ex) cut -c2 test.txt
  mn) display 2nd character from each line.
  
  ex) cut -c1-3 test.txt
  mn) display first three characters in the file from each line.
  
  ex) cut -c-8 test.txt  #1st to 8th
  ex) cut -c8- test.txt  #8th to end
  ex) cut -c- test.txt   #all

- select specified field
  ex) cut -d':' -f1 /etc/passwd
  mn) divide by ':' in the row and display first culomn each line in passwd file.
  
  ex) grep "/bin/bash" /etc/passwd | cut -d':' -f1-4,6,7
  mn) select first to 4th, 6th and 7th coloumn field.

- other options
  -s
  ex) grep "/bin/bash" /etc/passwd | cut -d':' -s -f1
  mn) "-s" option exclude a line not containing the deliminater, in this case ':'.
  
  --compliment
  ex) grep "/bin/bash" /etc/passwd | cut -d':' --comlement -s -f7
  mn) it contains all lines excepting 7th field.

  --output-delimiter
  ex) grep "/bin/bash" /etc/passwd | cut -d':' -s -f7 --output-delimiter='#'
      -> root#/root#/bin/bash
  mn) change delimiter from ':' to '#'

### d
#### date
- date
  show 

- (format)
  - ex
    date "+%Y%m%d-%H%M%S"

- -d (expr)
  - expr ex
    - '1 day'
    - '2 days' (or '2 day')
    - '1 day ago'
    - '-1 day'
    - yesterday
    - tomorrow
    - week
    - fortnight
    - '1 month ago'
    - '1 year ago'
    - '1 hour ago'
    - '1 minute ago'
    - '1 second ago'
    - '2015/04/25'

- link(tmp)
  https://hydrocul.github.io/wiki/commands/date.html

#### dd
- dd [operands ...]
- convert and copy a file
  The dd utility copies the standard input to the standard output.
- dataset definitionの略。元IBMメインフレームのDD Statementからきているため、引数の構文が他のUnixコマンドと異なる。
##### Options
###### bs=n
- bs=n
  Set both input adn output block size to n bytes, supersending the ibs and obs operands.
###### cbs=n
- cbs=n
###### count=n
- copy only n input blocks
###### files=n
- Copy n input files before terminating.
###### if
- if=file
  Read input from file instead of the standard input.
###### of
- of=file
  Write output to file instead of the standard output.
###### seek=n
- Seek n blocks from beginning of the output before copying.
###### conv=value[,value ...]
- Where value is one of the symbols 

####### Values
######## ascii, oldascii
######## block
######## ebcdic
######## notrunc
- Do not truncate the output file.
#### df
- 
  ファイルシステムについて、使用領域と空き領域のサイズを表示する。
  disk free : display free disk space.

- -h
  適当なサイズの単位をつけてくれる。(human readable)
- -a
  サイズが0のファイルシステムも出力
- -t fstype, --type=fstype
  ファイルシステムの種類(ex: ext4)の種別を指定
- -T
  ファイルシステムの種類を表示
- -s, --summarize
  display only a total for each argument
- --max-depth=N
  print the total for a directory only if it is N or fewer levels below the command line argument;
  specify 0 is the same as --summarize.

#### diff

##### Options
###### -u
###### -p
###### -r
###### -N
#### dig
- DNS lookup utility
  a flexible tool for interrogating DNS name servers.
#### dirname
- 
  extract directory path from full-path string

#### diskutil
##### mac
#### dmesg
- 
  カーネルのメッセージバッファの内容を表示する。"display message"の略。
  print or control the kernel ring buffer.
  the porgram helps users to print out their bootup messaes.

#### dstat
- 
  pythonスクリプト。

#### du
- du [filename...]
  ディレクトリ内のファイル容量を表示する。
  実際に使用しているディスク容量なので、ファイルサイズとは一致しない場合がある。

- -c, --total
  検索したすべての容量の総計を表示する

- -k, --kilobytes
  単位をキロバイトにする

- -m, --megabytes
  単位をメガバイトにする

- -s
  report only the sum of the usage in the current directory

#### dumpkeys(1)
- dump keyboard translation tables
### e
#### e2fsdk
- e2fsck DEVICE
  ext2/ext3/ext4ファイルシステムの整合性をチェックし、修復する。
  マウント中のファイルシステムに実行すると壊れる恐れがあるため注意。

- -f
  ファイルシステムにcleanマークが付いていても強制的にチェックアウトする。

#### echo
- 
  display a line of text
  メッセージを表示する

##### Options
###### -e
###### -n
- do not output the trailing newline
   
#### efivar
- Tool to manipulate UEFI variables
- efivar [OPTION...]
##### Options
###### -L, --list-guids
###### -l, --list
- list current variables
###### -p, --print
- print variables specified by --name
#### env
- 環境変数の表示。
  シェル変数も合わせて確認する場合は、"set"を利用する。
  
#### exec
- 
  現在実行中のシェルに変わり、指定したコマンドを実行する。
  コマンドを実行すると普通forkして子プロセスを生成するが、
  execから呼ぶとforkせずコマンドが呼ばれる。

#### exit
- 
  スクリプトの実行を終了する。
  returnと異なり、関数がどれだけネストしていても全体が終了される。
  数字を指定して終了ステータスを返すことが出来る。

#### expect
- programme dialogue with interactive programs
- tcl
##### syntax
- expect [-dDinN] [-c cmds] [ -[f|b] cmdfile] [args]
##### install
- yum install expect
- apt-get install expect
- pacman -S expect
##### Command
###### expect
- expect [[-opts] pat1 body1] ... [-opts] patn [bodyn]
  spawnされたプロセスの出力がパターンのどれかにマッチするか、指定された時間が経過するか、eof-of-fileを見つけるか、のいずれかが成立するまでウェイとする。
###### spawn
- spawn [args] program [args]
  program argsを走らせる新しいプロセスを生成する。
  標準入力と標準出力はExpectに結び付けられる。
###### send
- send [-flasgs] string
  stringを現プロセスに送る。
###### interact
#### export
- export VAR
  set VAR as environment variables.
  
- export VAR="value"
  set value on VAR as environment variables.
  This form may give an error in bash, sh(ash) of FreeBSD, etc.

  変数を大域変数として追加する。
  ex) export FOO="BAR"

##### Options
- (-p)
  show environ variables
  
- -n VAR
  Remove VAR from export lint

- csh, tcsh
  in csh or tcsh, use "setenv" instead of export.

- 
  環境変数を設定する。

- -n
  指定した環境変数を削除する

- -p
  環境変数の一覧を取得する

### f
#### false
- Return false value.
- Path : shell built-in command
#### fdisk
- fdisk (option) device
  ディスクのパーティションを設定する。

- -l
  get list about partition  (sudo fdisk -l /dev/sda)

- -s partition
  
#### fg
- [%jobsid]
  バックグラウンドで実行しているジョブをフォアグラウンドに切り替える。

#### file
- 
  実行可能ファイルかテキストかその他データかなどのファイルのタイプを判定して表示する。
  テキストファイルの文字コードを調べるのに利用可能。
- -b
  簡易モードで表示する。
- -i
  ファイルをmimeタイプ文字列にする。
- -z
  圧縮ファイルの中も調べる
- -v
  バージョンを表示する

#### find
- 
  ファイルやディレクトリを検索する。
  用法: find [option] [path...] [expression]
  用法：find [path] [condition] [action]

##### Options
- symbolic link
  - -P
    Never follow symbolic links.
  - -L
    Follow symbolic links.
  - -H
    Do not follow symbolic links, except while processing the command line arguments.

- debug
  - -D
    - help
    - tree
    - stat
    - opt
    - rates

- level
  - -Olevel
    - 0
    - 1
    - 2
    - 3
##### Expressions
- -name
  ファイル名を検索、パターンマッチ可。

- -exec (command, etc)
  検索後コマンドを実行する。
  \;でコマンドの終端を表す。{}で引数として渡すことができる。

- -empty
  空ファイルを対象とする
  ex) find . -empty

- -type (type)
  f : file
  d : directory

#### finger
- 
  ユーザ情報を表示する。
  ただし、最近はセキュリティの強化のためfingerを通さないよう設定している場合が多い。

#### free
- 
  
- -t
#### ftp
- ftp [-options] [host]
  
- -A
  Use active mode for data transfers.
  
- -P
  Use passive mode for data transfers.

- -v
  Verbose option forces ftp to show all responses from the remote server,
  
- Client Host
  - ?
    Commands.
  - !
  - $
  - bye
    Terminate the FTP session with the remote server and exit ftp.

  - ls
  - open
    
#### fsdk
- 
  実際にはLinuxで利用できるさまざまなファイルシステムチェッカーへの単なるフロントエンド、とのこと。

### g
#### gcc
- コンパイルする。
##### Options
###### Overall Options
####### -c
- アセンブルまで行いオブジェクトファイルを出力する
- Compile or assemble the source file, but do not link.
####### -S
- コンパイルまでを行いアセンブリファイルを出力する
####### -E
- プリプロセスだけ処理して標準出力する
####### -o outfile
- 出力ファイル名を指定する。
  ex) gcc -o hello.exe hello.c
####### -v
- 詳細を表示
  - Target: に標的システム名が表示される
    通常ハイフンで3つに区切られ、CPU名、マシンのベンダー名、OSもしくはカーネル名が

####### --help
####### --version
###### C Language Options
###### C++ Language Options
###### Language Independent Options
###### Warning Options
####### -Wall
- ANSI Cスタイルの宣言と定義を使った場合に、一般的な警告オプションがすべてOnになり、
  細かな警告をしてくれる。
- "enable ALL of the Warnings"の略
####### -Werror
- 警告をエラーとして解釈させる
###### Debugging Options
####### -g
- gdbでのデバッグが可能となる。
####### -dumpversion
- バージョンを表示する
####### -print-file-name=library
- 外部ファイルの絶対パスを表示する
####### -print-libgcc-file-name
- GCCランタイムライブラリの絶対パスを表示する
####### -print-prog-name=name
- gccドライバが起動する外部プログラムの絶対パスを表示する
####### -save-temps
- 中間ファイルを保存する
  SAVE TEMProrary filesS
###### Optimization Options
####### -O1(O), -O2, -O3
- 最適化オプション。数字が大きい方が強力な最適化が行われる。
  ただしO3はバグが多い印象があるとのこと。
###### Preprocessor Options
####### -Dmacro
####### -Umacro
####### -Wp,option
###### Assembler Option
####### -Wa,opition
###### Linker Options
####### -llibrary
- ダイナミックリンクを行う。
  引数としてメイン関数を先、ライブラリを後に並べる必要ある。
  -lの後にスペースはあけず、ライブラリ名のlibを除いたものを指定する。
  ex) libmをリンクしたければ、-lmとする。
####### -shared
- Produce a shared object which can then be linked with other objects to form an executable.
####### -static
- 静的リンクが行われる
####### -Wl,option
- pass option as an option to the linker.
  If option contains commas, it is split into multiple options at the commas.
###### Directory Search Options
####### -Idir
- Add the directory 'dir' to the head of the list of directories to be searched for header file.
####### -Ldir
- Add directory 'dir' to the list of directories to be searched for -l.
###### Machine Dependent Options
####### ARM
####### Darwin
####### GNU/Linux
####### i386 ad x86-64
######## -m32 / -m64
- Generate code for a 32-bit or 64-bit environment.
###### Code Generation Options
####### -fPIC
- emit position-independent code, suitable for dynamic linking and avoiding any limit on the size of the global offset table.
- "位置独立コード"を生成するためのオプション。
##### Link
- https://linux.die.net/man/1/gcc
#### gdb
- デバッグを行う。
- run (options)
  プログラムを開始する。オプションをつけるとオプション付きで実行する。
- backtrace, bt
  バックトレースを表示する。呼び出し順の逆に列挙される。
- frame N, f
  フレームNに飛ぶ。
  （番号を指定することで、backtraceで確認した番号の処理に飛べる。）
- list, l
  現在の関数のソースコードを表示する。
- print EXPR, p
  式EXPRの値を表示する
- continue, c
  続きを実行する
- quit, q
  gdbの終了する

#### glob
- 
  パス名をglobする

- Wildcard match
  - ? : あらゆる単一の文字にマッチする。
  - * : あらゆる文字列にマッチする。空も次にもマッチする。
  - 文字クラス
    - "[...]"
      続く最初の文字が"!"以外であれば、ブラケット内のいずれかの文字にマッチする。
      最初の文字が"!"であれば補集合となる。
      - "]" : ブラケットの直後に置くことで、指定文字に含まれる
      - "-" : 範囲指定。ブラケット内最初か最後に置くことで、指定文字に含む。
- pathname
  '/'は'?'や'*'にはマッチせず、陽に'/'文字を含むことはできない。
  
#### global
- 説明
  ソースコードの関数定義等に素早くアクセスできるようにする。
  apt-getやbrew等でglobalをインストールして使う。

- global 関数名
  関数からソースコードを探す。

- -f ファイル名
  そのファイルで定義されているファイル一覧を出力する。

- -r 関数名
  関数呼び出しの箇所を探す

- -c 関数名の一部
  関数名の一部から関数を探す。

- -g 検索文字列
  ソースコードのgrep

#### grep
- grep [OPTIONS] PATTERN [FILE...]
- grep [OPTIONS] [-e PATTERN | -f FILE} [FILE...] 
  searches the named input FILEs for lines containing a match to the given PATTERN.

##### Options
###### -a, --text, --binary-files=text
- Process a binary file as if it were text

###### -B NUM, --before-centext=NUM
- Print NUM lines of leading context before matching lines.
###### -v, --invert-match
- to select non-matching lines.

###### -C NUM, -NUM, --context=NUM
- Print NUM lines of output context.
###### -E, --extended-repex
- interpret pattern as an extended regular expression (ERE).

###### -F, --fixed-strinngs, --fixed-regexp
- interpret pattern as a list of fixed strings, not as a regular exression.

###### -G, --basic-regexp
- as a bacis regular expression (BRE)

###### -P, --perl-repexp
- as a Perl regular expresion.

##### egrep
- 
  the same as grep -E

##### fgrep
- 
  the same as grep -F

#### groupadd
- 
  新しいグループの作成

- ex)
  groupadd group01

#### gtags
- 
  tagを作成する。
  Gnu globalと共にインストールする。
- -f, --file filename
  Browse through all files whose names are listed in file.

- -v, --verbose
##### Files
###### GTAGS
###### GRTAGS
###### GPATH

#### gzip / gunzip
- 
  gzip形式で圧縮/解凍する。
  
- gzip -l, --list
  圧縮された個々のファイルについて、以下のフィールドを列挙する。
  compresed size, uncompressed size, ratio, uncompresed_name

### h
#### head
- output the first part of files
#### hexdump
- 
  ascii, decimal, hexadecimal, octal dump
##### Options
###### -C
- Canonical hex+ASCII display.
###### -n length
- Interpret only length bytes of input.
#### history
- display the command history list with line numbers.
  Lines listed with a * have been modified.
##### Options
###### -d num
- delete the No.num line
##### Memo
###### Historyの削除
- history -d numで消すか、~/.bash_historyなどを直接編集する。
#### host
- DNS lookup utility
  normally used to convert names to IP addresses and vice versa.
#### htags
- 
  ソースコードをhtmlに変換する。

- -a, --alphabet
  アルファベット順の関数一覧を作成する

- -n, --line-number
  ソースコードに行番号を表示する

- -s, --symbol
  関数だけでなくシンボルにもリンクを張る

- -x, --xhtml
  XHTML形式で表示する

### i
#### iconv
- convert text from one character encoding to another

- Usage:
  iconv [options] [-f from-encoding] [-t to-encoding] [inputfile]...

- Options:
  - -f from-encoding, --from-code=from-encoding
  - -t to-encoding, --to-code=to-encoding
  - -c
    Silently discard characters that cannot be converted insteadof terminating when encountering such characters.

#### id
- 
  ユーザIDやグループIDを表示する。

#### ifconfig
- (obsolete)

- memo
  - ifconfig eth1 promisc
    (-> ip link set eth1 promisc on)
    set promiscous mode.

  - ifconfig eth1 up
    
- Path:
  /sbin
#### inetd
- 
  待ち受けポートの監視専用中継デーモン。ポート番号を指定して監視する。
  待ち受けポートに要求が来た場合に、あらかじめ決められたデーモンを起動させる。
  各デーモンで待ち受けていると、リソースが無駄になるので専用ツールが作成された。

- /etc/services
  ポート番号とサービス名の紐付
- /etc/inetd.conf
  サービス名とサーバ名の対応付け

#### info
- 
  emacsを使ってマニュアルを表示する。
  GNU libcの一次情報はinfo。

#### install
     ファイルをコピーして属性の設定をする。
     1. install [OPTION]... SOURCE DEST
     2. install [OPTION]... SOURCE... DIRECTORY
     3. install -d [OPTION]... DIRECTORY...
     [-d, --directory] ディレクトリを作成する。
     [-m, --mode] アクセス権を設定する。
     [-v, --verbose]

#### iostat
- iostat
  Report Central Processing Unit(CPU) statistics and input/output statistics for devices,
  paritions and network filesystems.

- [interval]
  set interval to show

- -n
  Display the network filesystem (NFS) report.

- -x
  Display extended statistics.


##### Status

###### -x
- rrpm/s : マージされた読み込みIO要求。この値が大きいほどディスクの性能を引き出せている。
- wrpm/s : マージされた書き込みIO要求。この値が大きいほどディスクの性能を引き出せている。
- r/s : 秒間読み込みIO要求回数。この数値が大きいほど多くの要求をこなしている。低く保つようにすべき値。
- w/s : 秒間書き込みIO要求回数。この数値が大きいほど多くの要求をこなしている。低く保つようにすべき値。
- rsec/s : 読み込まれたセクタ数。IOによって実際に読み込まれたデータサイズで、真のディスク性能指標として考えられるべき値。
- wsec/s : 書き込まれたセクタ数。IOによって実際に読み込まれたデータサイズで、真のディスク性能指標として考えられるべき値。
- avgrq-sz : 一つの要求の平均セクタサイズ。
- avgqu-sz : IOキューの長さの平均。
- await : 要求を発行する平均時間間隔。
- svctm : 要求に対する平均レスポンスタイム。値が安定していることが非常に重要。サービスタイム。
- %util : 使用率（ビジー率）

#### ip
- ip [ OPTIONS ] OBJECT { COMMAND | help }
  show / manipulate routing, devices, policy rounting and tunnels

##### Objects
- 
  Object := { link | addr | addrlabel | route | rule | neigh | tunnel | maddr | mroute | monitor }

###### ip link (l)
####### ip link set
####### ip link show
###### ip addr (a)
####### ip addr { add | del}
####### ip addr { show | flush }
###### ip addrlabel
####### ip addrlabel { add | del }
####### ip addrlabel { list | flush }
###### ip route (r)
####### ip route { list | flush }
####### ip route get
####### ip route { add | del | change | append | replace | monitor }
###### ip rule
###### ip neigh
###### ip tunnel
###### ip maddr
###### ip mroute
###### ip monitor (mo)
##### Link
- [[https://access.redhat.com/sites/default/files/attachments/rh_ip_command_cheatsheet_1214_jcs_print.pdf][ip COMMAND CHEAT SHEET]]

#### ipcs
- IPCリソース情報の表示。
  
- -i
  後続のidで指定されたリソースの情報だけが出力される。
  
#### ipcrm
- メッセージキュー、セマフォ集合、共有メモリIDを削除する。

#### iptables
- iptables
  handle iptables settings.
  see alse [files]

- ex)
  iptables -t filter -I Input -p tcp -s 123.123.123.123 --dport 80 -j DROP
  
