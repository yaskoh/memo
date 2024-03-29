# Linux_Specification
## Linux Standard Base
### 5.0
#### Common
#### Core
#### Desktop
#### Runtime Languages
#### Imaging
### Link
- [[http://refspecs.linuxfoundation.org/lsb.shtml][Linux Standard Base]]
- [[https://wiki.linuxfoundation.org/start][Linux Foundation Wiki - THE LINUX FOUNDATION]]
## Filesystem Hierarchy Standard
### v3.0
### old
#### / (FHS)
- 
  第一階層、ルートディレクトリ

##### /bin
- 
  シングルユーザモードで必要となる一般ユーザ向け基本コマンドの実行ファイル。
  /usr/binはシングルユーザ以外の一般ユーザ向けコマンド。
  
- 
  必須: 
  cat, chgrp, chmod, chown, cp, date, dd, df, dmesg, echo, false, hostname,
  kill, ln, login, ls, mkdir, mknod, more, mount, mv, ps, pwd, rm, rmdir,
  sed, sh, stty, su, sync, true, unmount, uname

- 
  オプション: 
  csh, ed, tar, cpio, gzip, gunzip, zcat, netstat, ping

##### /boot
- 
  ブートローダ関連のファイル群。カーネルやinitrd。通常別パーティション。
  カーネルは、vmlinuzに格納されている。
  unix -> vmunix（仮想メモリ機構追加） -> vmlinux -> vmlinuz（圧縮）のように変遷した。

##### /dev
- 
  基本デバイス。/dev/null, /dev/consoleなど。
  Linux2.4ではdevfsという仕組みが導入されたが、USBなどと相性が良くなかったため、
  Linux2.6以降はudevという仕組みが使われる。
  defvsはカーネルの一部だが、udevはカーネルの外。
  "ls -l"などのコマンドで確認すると、キャラクタデバイスかブロックデバイスかが確認できる。

##### /etc
- 
  システム全体の固有設定ファイル群。バイナリファイルを置かない。
  fstab, gateway, group, hosts, password, profile, servicesなど。

###### /etc/opt
- 
  /opt/のための設定ファイル群。
###### /etc/X11
- 
  X Window System用の設定ファイル群。
###### /etc/sgml
- 
  sgml設定ファイル群。
###### /etc/xml
- 
  xml設定ファイル群。
###### /etc/init.d
- 
  デーモンを起動するためのファイルが置かれる。
  これらのファイルは起動スクリプトと呼ばれる。
  /etc/rc*.dディレクトリの起動スクリプトの実態はすべて/etc/init.dに格納されている。

##### /home
- 
  ユーザのホームディレクトリ。オプション。

##### /lib
- 
  /bin や /sbin にある実行ファイルの基本となるライブラリ群。

##### /lost+found (FHSの規定にはなし)
- 
  fsckでディスクチェックした際に作られる、破損ファイルの断片を収めるディレクトリ。

##### /media
- 
  CD-ROMなどのリムーバブル媒体マウントポイント。

##### /mnt
- 
  ファイルシステムの一時マウントポイント。

##### /opt
- 
  オプションのアプリケーションソフトウェアのインストール用

##### /proc
- 
  カーネルやプロセスの情報をテキストで示す仮想ファイルシステム。
  procfs(Process File System)のマウントポイント。

##### /root
- 
  rootユーザのホームディレクトリ。オプション。

##### /sbin
- 
  システム管理系コマンドの実行ファイル群。

- 必須:
  shutdown

- オプション:
  fastboot, fasthalt, fdisk, fsck, fsck.*, getty, halt, ifconfig, init,
  mkfs, mkfs.*, mkswap, reboot, route, swapon, swapoff, update

##### /srv
- 
  システムによって提供された(served)固有のデータ

##### /tmp
- 
  一時ファイル置場。リブート時には内容が削除される。
  /var/tmpは消えない。

##### /usr
- 
  ユーザユーティリティとアプリケーションを格納。
  複数のマシンで共有可能なファイルを置き、多くのマシンにマウントして使ったりする。
  共有できないようなファイルはvarにおく。
  "User Services and Routines"の略らしい。

###### /usr/bin
- 
  一般ユーザ向けだが基本的でないコマンド。
  シングルユーザモードには不要なバイナリで、パッケージの追加削除でファイルは増減する。
  ディストリビューションが管理するディレクトリなので、自分でインストールするプログラムは/usr/local/binなどに置く。

###### /usr/include
- 
  標準includeファイル群。C言語で使う標準ヘッダファイル。
  カーネルのヘッダファイルは/usr/include/linuxと/usr/include/asmにある。
  本来は/usr/include/sys以下がカーネル関連だが、
  Linuxはカーネルとlibcで管理者が置が言うため少し変則的なディレクトリ構造になっている。

###### /usr/lib
- 
  /usr/bin や /usr/sbin にある実行ファイルの基本ライブラリ。

###### /usr/sbin
- 
  基本的でない実行ファイル群。ネットワーク用デーモンなど。
  平常時用のシステム管理コマンドやサーバプログラム。

###### /usr/share
- 
  アーキテクチャに依存しない共有データ
  典型的な例はドキュメント。manやinfoなど。

####### /usr/shar/man
- 
  manページを置く。
  roffというテキスト形式で書かれている。

####### /usr/share/info
- 
  infoドキュメントを置く。
  textinfo形式のファイルがinfo直下に並ぶ。

###### /usr/src
- 
  システムで使っているコマンドのソースコードを置く。
  Kernelのソースコードなど。

###### /usr/X11R6
- 
  X Windows System Version 11 Release 6
  下にbinやlibがある。

###### /usr/local
- 
  ホスト固有のローカルデータを格納する。システム管理者が自分でアプリケーションをインストールする。
  構造はほぼ/usrと同じ。

####### /usr/local/bin
- 
  自分でインストールするコマンド等を配置する。

####### /usr/local/games
####### /usr/local/include
####### /usr/local/lib
####### /usr/local/man
- /local/bin用マニュアル
####### /usr/local/sbin
- /sbinと比べて重要でないシステムバイナリを配置する。
  /sbinは緊急時に必要なもの、/usr/sbinは通常運用時。
####### /usr/local/share
- アーキテクチャに依存しないデータを収める。
####### /usr/local/man
######## /usr/local/man/man1
- ユーザプログラム
######## /usr/local/man/man2
- システムコール
######## /usr/local/man/man3
- Cライブラリ関数
######## /usr/local/man/man4
- スペシャル(デバイス)ファイル
######## /usr/local/man/man5
- ファイルフォーマット
######## /usr/local/man/man6
- ゲーム
######## /usr/local/man/man7
- その他
######## /usr/local/man/man8
- システム管理
####### /usr/local/misc
####### /usr/local/src

##### /var
- 
  可変なファイル群。内容が常に変化するようなファイル群を格納する。
  ログ、スプール、一時的な電子メール等。

###### /var/cache
- 
  アプリケーションのキャッシュデータ。
  普通は要領に上限を設けて、古い順に捨てていく。

###### /var/lib
- 
  状態情報。データベース、パッケージングシステムのメタデータなど。

####### /var/lib/misc

###### /var/local
###### /var/lock
- 
  ロックファイル群。使用中リソースを保持するファイル。排他制御を行いたい場合に使用する。
###### /var/log
- 
  各種ログ
###### /var/opt
###### /var/mail
- 
  メール
###### /var/run
- 
  走行中システムに関する情報。現在ログイン中のユーザ、走行中デーモン等。
  "`kill -HUP `cat /var/run/sendmail.pid`"などするとプロセス番号をタイポせずよい。
  PIDファイルともいう。

###### /var/spool
- 
  処理待ちスプール。プリントキュー、未読メールなど。

####### /var/spool/mail
- 
  互換のためのかつてのメールボックス。

###### /var/tmp
- 
  一時ファイル置場。/tmpとは異なり、リブートしても内容が失われない。

##### memo
- ディレクトリの分類
  |----------+----------------------------+---------------------|
  |          | 共有可能                   | 共有不可            |
  |----------+----------------------------+---------------------|
  | 変化せず | /usr, /opt                 | /etc, /boot         |
  |----------+----------------------------+---------------------|
  | 変化する | /var/mail, /var/spool/news | /var/run, /var/lock |
  |----------+----------------------------+---------------------|

#### / (何を参照したかは忘れた。)
     - vmlinuz
         Linux Kernel
     - boot
         - System.map
         - config
         - grub
         - initrd.img
           init ram disk
     - etc
         Setting Files
     - bin
         commands using by system admin and user
     - sbin
         admin tools using by system admin
     - usr
         directory which has data shared by users using the system
         - bin
         - include
         - lib
         - local
             - bin
             - etc
             - games
             - include
             - lib
             - man
             - sbin
             - share
             - src
         - sbin
         - share
     - home
     - var
         variable data
         - tmp
             directory with sticky bit, that makes the files in the directory not able to delete without the owner
         - log,spool
         - mail
         - run
             having PID in text files
         - lock
     - proc
         procfs(Process File System)
         pseudo file system giving system information
         /proc/PID/oom_score, oom_adj <-concerning with OOM Killer(Out Of Memory Killer)
     - sys
         sysfs: devise info, procfs: process and kernel info
     - dev
         deployed device files
     - tmp
         temporary
         deleted when unmounting or rebooting

### Link
- [[http://refspecs.linuxfoundation.org/fhs.shtml][Filesystem Hierarchy Standard]]
## Link
- [[http://pubs.opengroup.org/onlinepubs/9699919799/][POSIX.1-2008 - IEEE Std 1003.1-2008]]
