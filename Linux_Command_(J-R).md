# Linux Commands (J-R)
## Commands (J-R)
### j
#### jobs
- 
  実行中のジョブを表示する。

#### joke
##### sl
- 
  slが走る。いくつかオプションも存在する。

##### banner
- 
  バナーっぽいアスキーアートが表示できる。

##### aafire
- 
  AAの炎が表示される。

##### cmatrix
- 
  matrixっぽい表示

### k
#### kill
- [-s signal] pid
  プロセスおよびジョブを強制終了する
- -l
  シグナルの一覧を表示する
  |----+---------+--------------------------------------------------------------------------------|
  |  1 | SIGHUP  | 端末との接続が切断された(Hangup)ことによるプロセスの終了                       |
  |  2 | SIGINT  | キーボードからの割り込み(Interrupt)によるプロセスの終了                        |
  |  3 | SIGQUIT | キーボードからの中止(Quit)                                                     |
  |  4 | SIGILL  | 不正な命令(Illegal instruction)によるプロセスの終了                            |
  |  5 | SIGTRAP | トレース(Trace),ブレークポイントとラップ(break point trap)によるプロセスの終了 |
  |  6 | SIGABRT | abrot関数によるプロセスの中断                                                  |
  |  8 | SIGFPE  | 浮動小数点例外(Arithmetic Exception)によるプロセスの終了                       |
  |  9 | SIGKILL | Killシグナルによるプロセスの終了                                               |
  | 11 | SIGSEGV | 不正なメモリー参照(Segmentation fault)によるプロセスの終了                     |
  | 13 | SIGPIPE | パイプ(Pipe)破壊によるプロセスの終了                                           |
  | 14 | SIGALRM | alerm関数によるプロセスの終了                                                  |
  | 15 | SIGTERM | 終了(Termination)シグナルによるプロセスの終了                                  |
  |----+---------+--------------------------------------------------------------------------------|

### l
#### last
- 
  show listing of last logged in sures
  searches the file /var/log/wtmp and displays a list of all users logged in.

#### ld
- See also "[[file:GNULinker.org][GNULinker.org]]"
- linker, linker LoaDer
  combines serevral object files and libraries, resolves references, and produces an output file.
- ld files... [options] [-o outputfile]
##### GNU Options
###### -e entry, --entry=entry
- Use 'entry' as teh explicit symbol for beginning execution of your program, rather than default entry point.
###### -m emulation
- Emulate the 'emulation' linker.
###### -Ifile, --dynamic-linker=file
- Set the name of the dynamic linker.
  This is only meaningful when generating dynamically linked ELF executables.
###### -T scriptfile, --script=scriptfile
###### --dll-verbose, --verbose[=NUMBER]
- Display the version number for ld and list the linker emulations supported.
##### BSD Options
###### Options that control the kind of output
###### Options that control libraries
###### Options that control additional content
###### Options when creating a dynamic library (dylib)
###### Options when creating a main executable
###### Options when creating bundle
###### Options when creating an object file
###### Options that control symbol resolution
###### Options for introspecting the linker
###### Options for controling symbol table optimizations
###### Options for Bitcode build flow
###### Really used Options
#### ld.so, ld-linux.so
- 動的なリンカー/ローダー
  ld.soはa.outバイナリ、ld-linux.so*はELFバイナリを使う。
- https://linuxjm.osdn.jp/html/LDP_man-pages/man8/ld.so.8.html
##### Options
###### --list
- list all dependencies and how they are resolved
###### --verify
###### --inhibit-cache
###### --library-path PATH
###### --inhibit-rpath LIST
###### --audit LIST
##### Environmental Variables
###### LD_ASSUME_KERNEL
###### LD_BIND_NOT
###### LD_DEBUG
- (glibc 2.1以降)動作リンカーの詳細なデバッグ情報を出力する。
  - all : 全ての動的リンカーが持つデバッグ情報を表示する
  - help : カテゴリーのヘルプ情報を表示する
  - libs : ライブラリの探索状況を表示
  - reloc
  - files
  - symbols
  - bindings
  - versions
  - scopes
  - statistics
  - unused
###### LD_LIBRARY_PATH
- ライブラリ探索パスを設定
- 探索順序 : 
  1. LD_LIBRARY_PATH
  2. /etc/ld.so.cache
  3. /lib
  4. /usr/lib
  
###### LD_TRACE_LOADED_OBJECTS
- プログラムを普通に実行するのではなく、動的ライブラリの依存関係をリスト表示させる。
##### Search libraries
- 
  - LD_LIBRARY_PATH
  - /etc/ld.so.cache
  - /lib
  - /usr/lib
#### ldconfig
- configure dynamic linker run-time bindings
- ld.so.cacheの再構築を行う
##### Options
###### -p
- Print the lists of directories and candidate libraries stored in the current cache.
- ld.so.cacheの値を表示する
###### -v
###### -V
#### ldd
- List Dynamic Dependencies
- 共有ライブラリの依存関係を表示する。
  ld.so -listと同じ
- 実態はbashシェルスクリプト。
  LD_TRACE_LOADED_OBJECTS=1とした上で該当プログラムを実行している。
#### less
- 
  pager

- +F
  display added lines like tail -f.
  Ctrl+F change mode to this mode from normal mode, and Ctrl-c 

- mulit files
  - :n
    move next file
  - :p
    move previous file
  - :x
    move first file
  - :d
    remove current file on the list

#### lldb
- [[file:LLVM.org][LLVM.org]]
#### ln
- 
  リンクを作成する
- -s, --symbolic
  シンボリックリンクの作成
- -v, --verbose

#### loadkeys
- load keyboard translation tables
#### locale
- Get locale-specific information.
  
#### locate
- 
  ファイルを高速に検索する。
  あらかじめ作成したデータベースを用いるため、findコマンドより高速。
  データベースはスーパーユーザ権限でupdatedbコマンドを実行して作成する。

#### logrotate
- 
  logrotate is designed to ease administration of systems that generate large number of log files.
  It allows automatic rotation, compression, removal, and mailing of log files.

- -d
  Turns on debug mode and implies -v.

- -v
  Turn on verbose mode.

  
- -f, --force
  
#### ls
- 
  ls means list.
  show files and directories on the target directory.
- -l
  show details.
- -r  
  show reverse sorted.
- -t
  show sorted by timestamp
- -S
  sorted with file size.
- +F
  wait for data updating

##### Subcommand
- F
  waiting and following the updating data. same as +F

- :n
  show next file (when opening some files)

#### lsblk
- list block devices
##### Synopsis
- lsblk [options] [device...]
##### Options
###### -a, --all
###### -b, --bytes
#### lsb_release
- print distribution-specific information
  providing certain LSB (Linux Standard Base) and distribution-specific information.
- Synopsis
  lsb_release [options]
##### Options
###### -v, --version
###### -c, --codename
###### -s, --short
#### lsof
- list open files
  
- -p [pid]
  
#### lsx
- module in "lrzsz"
##### Usage
- lsx [options] file ...
  lsx [options] -{c|i} COMMAND
##### Options
###### -h, --help
- print usage, etc
#### lvcreate
- 
  create a new logical volume in a volume group.

- -n, --name LogicalVolume[Name|Path]
  Sets the name for the new logical volume.
  
- -p, --permisson {r|rw}
  Sets access permissons to read only (r) or read and write (rw).

- -s, --snapshot OriginalLogicalVolume[Name|Path]
  Creates a snapshot logical volume for an existing, so called original logical volume or origin).

- -L, --size LogicalVolumeSize[bBsSkKmMgGtTpPeE]
  Gives the size to allocate for the new logical volume.

- ex) lvcreate -s -L 40G -n snapshot_vol -p r /dev/vg01/lvol01

#### lvdisplay
- 
  display attributes of a logical volume
  
#### lvextend
- 
  extend the size of a logical volume.

#### lvreduce
- 
  reduce the size of a logical volume

- -L, --size [-]LogicalVolumeSize[bBsSkKmMGtTpPeE]
  Reduce or set
  ex) lvreduce -L -20G /dev/mapper/vg01-lvol01
  
- link
  [[http://seriousbirder.com/blogs/lvreduce-ext4-example/][lvreduce ext4 example]]

#### lvremove
- 
  removes one or more logical volumes.
  
- -f, --force
  Revome active logical volumes without confirmation.

- ex)
  lvremove -f vg00/lvol1

#### lvs
- 
  report information about logical volumes

#### lynx
- 
  text-based web-browser.
  
### m
#### mail
- 

##### Subcommands
- mailnumber
  show mail of mailnumber
- n
  show next mail
- -
  show previous mail
- p
  show being selected now
- h
  show list of mails
- m receiver
  send mail to receiver
- r
  現在選択中のメールに返信する
- d mailnumber
  delete selected mail
- u
  undo delete mail
- q
  save changes and exit
- x
  exit without saving changes


- 
  http://www.uetyi.com/server-const/command/entry-166.html
#### make
     コンパイル等の処理を自動で行う。
     [-k, --keep-going] エラーが発生してもできるだけ処理を継続させる。
     [-n, --just-print, --dry-run] 実際には処理せず実行コマンドのみ表示する。

#### man
- マニュアルを呼び出す。
  |------------+------------------------|
  | セクション | 分類                   |
  |------------+------------------------|
  |          1 | ユーザコマンド         |
  |          2 | システムコール         |
  |          3 | ライブラリ関数         |
  |          4 | デバイスファイルなど   |
  |          5 | ファイルフォーマット   |
  |          6 | ゲーム                 |
  |          7 | 規格など               |
  |          8 | システム管理用コマンド |
  |------------+------------------------|

#### md5sum
- md5sum [OPTION]... [FILE]...
  compute and check MD5 mesage digest

#### merge
- merge (option) file1 file2 file3
  file2からfile3へのすべての変更をfile1に併合する。
#### minicom
- 端末エミュレータ
##### Options
###### -s
- セットアップ画面
#### mkdir
#### mkfs
- 
  ファイルシステムの作成
- -t
  ファイルシステムタイプを指定する。
- -V
  verboseもversionも兼用しているようです。
  ex: mkfs -v -t ext4 /dev/sdb1

#### mknod
     特殊ファイルを作成する。
     mknod [オプション] ファイル名 タイプ メジャー マイナー
     [-m] アクセス権を設定する。デフォルトは0666からumaskを引いたもの。
     タイプ: b ブロック(buffered)型、c,u キャラクタ(unbuffered)型
             p FIFO(名前つきパイプ)
             ※pを指定を指定した場合はデバイス番号（メジャーマイナー）を指定しない。

#### mkswap
- 
  スワップ領域を設定する。
  mkswap /dev/sbd2

#### mount
##### Linux
- mount a filesystem
###### Synopsis
###### Opiotns
- 
  現在マウントされているファイルシステムを調べる。
####### --bind
- すでにマウントされているツリーの一部を別の場所にマウントする。
####### -v, --verbose
####### -t vstype
- ファイルシステムのタイプを指定
   ext3, ntfs, sysfs, devpts, proc, tmpfsなど。

##### BSD
- mount file systems
###### Synopsis
###### Options
####### -a
####### -d
####### -f
####### -o
####### -r
####### -t lfs | external type
####### -u
####### -v
####### -w
- Mount the file system read-write.
#### mpstat
- Report processors related statistics
  
- -A
  equivalent to specifying "-I ALL -u -P ALL"

#### mtools
- utilities to access DOS disks in Unix.
- https://www.gnu.org/software/mtools/manual/mtools.html
##### mcopy
- copy MSDOS files to/from Unix
  The mcopy command is used to copy MS-DOS files to and from Unix.
##### mformat
- add an MSDOS fliesystem to a low-level formatted floppy disk
###### Syntax
- mformat [options] drive:
###### Options
####### -B boot_sector
- Use the boot sector stored in the given file or device instead fo using its own.
####### -C
- Creates the disk image file to install the MS-DOS file system on it.
####### -f size
- Specifies the size of the DOS file system to format.
####### -i
#### mv
- 
  リネームとかファイルの移動とか。
  mv aaa{,bbb}とするとaaa->aaabbbにリネームされる。

### n
#### nasm
- the Netwide Assembler, a portable 80x86 assembler
##### Synopsis
- nasm [-@ response file] [-f format] [-o outfile] [-l listfile] [options...] filename
##### Options
###### -f format
- Specifies the output file format.
###### -g
- Causes nasm to generate debug information in selected format.
###### -@ filename
#### nc
- netcat.
  arbitrary TCP and UDP connections and listens.
  nc utility is used for just about anything under the sun involving TCP and UDP.

##### Options
###### -l
- used to specify that nc should listen for an incoming connection rather than initiate a connection to a remote host.

###### -p
- source port

###### -v
- give more verbose output.
  
###### -z
- Specifies that nc should just scan for listening daemons, without sending any data to them.

##### Memo
###### Port scan
- 
#### nm
- list symbols from object files. symbol NaMe
##### Symbol
- D, d : The symbol is in the initialized data section.
- R, r : The symbol is in a read only data section.
- T, t : The symbol is in the text (code) section.
- U : The symbol is undefined.
  外部参照されている
- u : The symbol is a unique global symbol.
- W, w : The symbol is a weak symbol that has not been specifically tagged as a weak object symbol.
##### Options
#### netstat
- 

- State
  |-------------+--------------------------------------|
  | name        |                                      |
  |-------------+--------------------------------------|
  | LISTENING   | サーバとしてクライアントの接続待機中 |
  | ESTABLISHED | コネクション確立中（通信中）         |
  | CLOSE_WAIT  | コネクション通信待ち                 |
  | TIME_WAIT   | コネクション終了後                   |
  |-------------+--------------------------------------|
  
#### nslookup
- query Internet name servers interactively
  a program to query Internet domain name servers.
  two models, interactive and non-interactive mode, exists.
### o
#### objdump
- display information from object files.
##### Options
###### -a, --archive-header
###### -d, --disassemble
- Dissassemble
  Display the assembler mnemonic for the machine instructions from objfile.
###### -h, --section-headers, --headers
###### -i, --info
- Display a list showing all architectures 
###### -j セクション名
- 解析対象オプションの選択
###### -s
- セクション内容をダンプ
#### od
- dump files in octal and other formats
##### Options
###### -A, --address-radix=RADIX
- output foramt for file offsets
  RADIX is one of [doxn], Deximal, Octal, Hex or None.
###### -j, --skip-bytes=BYTES
- skip BYTES input bytes first
###### -N, --read-bytes=BYTES
- limit dump to BYTES input bytes
###### -t, --format=TYPE
- select output format or formats.
####### TYPE
######## a
- named character
######## c
- printable character or backslash escape
######## d[SIZE]
######## f[SIZE]
######## o[SIZE]
######## u[SIZE]
######## x[SIZE]
- hexadecimal, SIZE byets per integer.
###### -w[BYTES], --width[=BYTES]
- output BYETS byets per output line; default 32.
##### Traditional Options
###### -x
- same as -t x2, select hexadecimal 2-byte units
#### openssl
- openssl command [command opts] [command args]
  OpenSSL command line tool
##### Description
- OpenSSL is a cryptography toolkit implementing the Secure Sockets Layer
  and Transport Layer Security network protocols and related cryptography standards required by them.

##### Commands
###### Standard
####### genrsa
- openssl genrsa [Options] [numbits]
- Generation of RSA Private Key. Superceded by genpkey.
######## Options
######### -help
######### -out filename
######### -passout arg
######### -aes128|-aes192|-aes256|-des|-des3
######### [numbits]
- the size of the private key to enerate in bits.
  This must be the last option specified. The default is 2048.

####### req
- openssl req [Options]
- PKCS#10 X.509 Certificate Signing Request (CSR) Management.
######## Options
######### -inform DER|PEM
- This specifies the input format.
######### -new
- this option generates a new certificate request.
######### -[digest]
- such as "-md5", "-sha1"
######### -key filename
- This specifies the file to read the private key from.
######### -out filename
- This specifies the output filename to write to or standard output by default.
######### -x509
####### s_client
####### s_server
####### x509
- openssl x509 [Options]
- a mulit purpose certificate utility.
  It can be used to display certificate information, convert certificates to various form,
  sign certificate requests like a "mini CA" or edit certificate trust settings.
######## Options
######### INPUT, OUTPUT, GENERAL PURPOSE
########## -in filename
########## -out filename
########## -md2|-md5|-sha1|-mdc2
######### DISPLAY OPTIONS
######### TRUST SETTINGS
######### SIGNING OPTIONS
########## -signkey filename
- this option causes the input file to be self signed using the supplied private key.
  
########## -days arg
- specifies the number of days to make a certificate valid for.
########## -req
- by default a certificate is expected on input.
  With this option a certificate request is expected instead.
###### Message Digest
####### md5
- md5 Digest
####### sha1
####### sha256
####### sha384
####### sha512
###### Encoding and Cipher
### p
#### parted(8)
- GNU Parted - a partition manipulation program
  a program to manipulate disk parittions
##### Synopsis
- parted [options] [device [command [optoins...]...]]
##### Options
###### -h, --help
###### -l, --list
###### -v, --version
#### passwd
- 
  ユーザパスワードを変更する。

- ex)
  passwd user

#### patch
- patch [options] [originalfile [patchfile]]
  (unually)patch -pnum < patchfile
  apply a diff file to an original
  
##### Options
###### -pnum, --strip=num
###### -R, --reverse
- Assume that this patch was created with the old and new files swapped.
- パッチを当てた後で元に戻す時に使える。
##### Memo
###### Patchファイルをdiffで作成
- patchfileは、以下のように作る
  diff -u [oldfile] [newfile]
- http://d.hatena.ne.jp/mrgoofy33/20101019/1287500809
  https://qiita.com/astro_super_nova/items/e30dcaf4d106deebc63c
#### perf
- [[https://qiita.com/ryuichi1208/items/87658621d332d31b9450][Linux 性能解析ツールperfを使ってみた - Qiita]]
#### pgrep
- 
  選択基準にマッチするプロセスのプロセスIDを標準出力する
- -l
  プロセス名をプロセスIDと一緒に表示する
- -o
  マッチしたプロセスの中から最古のものを表示する
- -U ユーザID
  ユーザIDがリストのどれかであるプロセスを表示する
- -G グループID
  実グループIDがリストのどれかであるプロセスのみマッチする
  
#### printenv
- show list of environment variables.

#### printf
- 
  メッセージを整形して表示する。
  '\n'を入れないと改行されない。

#### ps
##### About
- 
  displays information about selection of the active processes.
  実行中のプロセスを表示する。

- 
  accepts several kinds of options:
  1. Unix options, which may be grouped and must be preceded by a dash.
  2. BSD options, which may be grouped and must not be used with a dash.
  3. GNU long options, which are preceded by two dashes.
  
  Options of different types may be freely mixed, but conflicts can appear.

- 
  - Standard(Unix)
    ps -e
    ps -ef
    ps -ely
  - BSD
    ps ax
    ps aux

###### Items
######## PID
- プロセス番号
######## TTY
- 端末名
######## TIME
- プロセスの総実行時間
######## CMD
- 実行しているコマンド
##### Unix
###### -e
- Select all processes. Identical to -A.
  全てのプロセスを表示する。
###### -f
- プロセスの親子関係を表示する
###### -u
- -uユーザ
  指定されたユーザ名（ユーザID）に対応するプロセスのみ表示する
###### -A
- Select all processes. Identical to -e.

##### BSD
###### a
- 自分以外のユーザのプロセスも表示する
###### f
- プロセスの親子関係をツリー状に表示する
###### l
- ロングフォーマット・詳細情報を表示する
####### Items
######## F
- 現在の状態を表す16新フラグ
######### 00
- 終了している。
######### 01
- システムプロセス。常にメモリー上にある。
######### 02
- 親プロセスからトレースされている。
######### 04
- 親プロセスからトレースされて、停止している
######### 08
- シグナルで起動できない
######### 10
- メモリー上にあり、イベント終了までロックされている
######### 20
- スワップできない
######## PPID
######## RI
######## NI
######## WCHAN
###### r
- 実行中のプロセスのみ表示する
###### u
- プロセスのユーザ情報を表示
####### Items
######## USER
- プロセスの所有ユーザ
######## %CPU
- CPUの占有率
######## %MEM
- 実メモリでの占有率
######## SIZE
- 仮想分も含めた使用サイズ(KByte)
######## VSZ

######## RSS
- 実メモリ上の使用サイズ(KByte)
######## STAT
- プロセスの状態
######### 1文字目
########## R
- Runnable, 実行可能
- 稼働中
########## S
- 一時停止中
- 20秒未満のsleep状態
########## D
- 停止不可能で一時停止
- ディスク（あるいは他の割り込み不可能な短期間の）待ち状態
########## T
- 終了処理中
- stop状態
########## Z
- ゾンビプロセス
########## W
- 実メモリになく、スワップアウトしている
########## N
- nice値
######### 2文字目以降
########## +
- 制御端末のフォアグラウンドプロセスグループに属している
########## >
- CPUのスケジュール優先度があげられている
########## <
- メモリ要求に対するソフトリミットが設定されており、現在そのリミットを超えている。
########## A
- ランダムなページスワップを要求
########## E
- 終了しようとしている
########## L
- 実メモリ中にロックされたページを持っている
########## N
- スケジューリング優先度が下げられている
########## S
- FIFOページスワップを要求した
########## s
- セッションリーダ
########## V
- vforkの間、一時中断されている
########## W
- スワップアウトされている
########## X
- トレースされているかデバッグされている
######## START
- プロセスの開始時間
######## COMMAND
- 実行コマンドとパス
###### x
- 制御端末のないプロセスの情報も表示する
##### GNU long

#### pstree
- [ pid | user ]
  実行中のプロセスをツリー形式で実行する。
  pidを基点として表示するが、省略されるとinitを基点とする。

#### pvcreate
- 
  initialize a disk or partition for use by LVM

- ex)
  sudo pvcreate /dev/sdb1
  
#### pvdisplay
- 
  display attributes of a physical volume

#### pvs
- 
  report information about physical volumes

### q

### r
#### rar / unrar
#### read
- read [varname]
  標準入力から1行読み取り、読み込んだ内容をvarnameに指定したシェル変数に格納する。

##### Options
- -n nchars
  read returs after reading nchars characters.

#### readelf
- Displays information about ELF files.
- ELFファイルに関する情報を表示
  binutilsに含まれる。
##### Options
###### -d, --dynamic
- Displays the contents of the file's dynamic section, if it has one.
- ダイナミックセクションの情報を表示
###### -h, --file-header
- Displays the information contained in the ELF header at the start of the file.
###### -l, --program-headers, --segments
- Displays the information contained in the file's segment headers, if it has any.
- プログラムヘッダーを表示
###### -S, --section-headers, --sections
- Sectionsオプション
- セクションヘッダーテーブルを表示
  実行コード領域.text、固定データ領域.rodata、初期化済みデータ領域.dataなどが表示される
###### -s
- シンボル情報を表示
###### -x <number or name>, --hex-dump=<number or name> 
#### readlink
     シンボリックリンクの値を読む。
     readlink [OPTION]... FILE...

#### readonly
- readonly 変数
  変数を読み込み専用にする。上書きやunsetができなくなる。
#### resize2fs
- 
  resize ext2, ext3, or ext4 file system.
  It can be used to enlarge or shrink an unmounted file system located on device.

#### return
- 
  関数の実行を終了する。
  数字を指定して終了ステータスを返すことが出来る。

#### rsync
- Usage
  - Local:
    - rsync [OPTION...] SRC... [DEST]
  - Access via remote shell:
    - Pull:
      rsync [OPTION...] [USER@]HOST:SRC... [DEST]
    - Push:
      rsync [OPTION...] SRC... [USER@]HOST:DEST
  - Access via rsync daemon:
    - Pull:
      rsync [OPTION...] [USER@]HOST:SRC... [DEST]
      rsync [OPTION...] rsync://[USER@]HOST[:PORT]/SRC... [DEST]
    - Push:
      rsync [OPTION...] SRC... [USER@]HOST:DEST
      rsync [OPTION...] SRC... rsync://[USER@]HOST[:PORT]/[DEST]

#### run-parts
- 
  run scripts or programs in a directory.
  
- 
  cronで使われている。
  またdebian系とRHEL系で動きが違うとのこと。

#### rm
- 
  ファイルを削除する

#### rmdir
