# Linux
## Linux OS
### 構成要素
- shell
  bash, ash, csh, tsch, zsh, pdksh, ...
- util-linux
  init, getty, login, reset, fdisk, ...
- procps
  ps, pstree, top, ...
- GNU coreutils
  ls, cat, mkdir, rmdir, cut, chmod, ...
- GNU grep, find, diff
- GNU libc
- libraries 
  ncurses, GDMB, zlib, ...
- development enviroment
  gcc, binutils, make, bison, flex, headerfiles, ...
- X Window System
- GNOME, KDE
(「ふつうのLinux」p.27)

### アドレス空間の構造
- テキスト領域
  機械語のプログラム
- データ領域
  グローバル変数や関数内のスタティック変数のうち初期化済みのもの、
  文字列リテラルがおかれる。
- BSS領域
  グローバル変数や関数内のスタティック変数のうち初期化が必要ないものがおかれる。
- ヒープ領域
  malloc()が管理する領域
- スタック領域
  関数呼び出しに関連したデータを置くところ。
  関数の引数やローカル変数がおかれる。

### File
- memo
  以下は広義ではすべてファイル。

- regular file
- directory
- symbolic link
- device file
  - character device file
    プリンタやモデムなど。
    データの読み書きを1バイトずつ行う。
  - block device file
    ハードディスクなど。
    データの読み書きをブロック単位で行うハードウェアを抽象化したもの。
- named pipe
  プロセス間通信に使うファイル。FIFO。
- UNIX domain socket

## Kernel
- [[file:./Linux_Kernel.org][Linux_Kernel.org]]
## Directory Structure
### FHS
- [[file:Linux_Specification.org][Filesystem Hierarchy Standard@Linux_Specification]]
## System calls
- [[file:./Linux_Functions.org][Linux_Functions.org]]
## Commands
- [[file:./Linux_Command.org][Linux_Command.org]]
## Boot Process
### Switch
### BIOS/UEFI
#### BIOS
#### UEFI
### Bootloader
#### GRUB
#### LILO
### Linux Kernel
### Init daemon
#### SysVinit
- 
  First, kernel make init daemon start.
  then init gets services to start by following description of /etc/inittab.
  
  1. init read /etc/inittab
  2. init execute /etc/rc.sysinit
  3. init execute /etc/rc
  4. /etc/rc execute Start-up scripts on /etc/rc(runlevel).d

- /etc/rc*.d
  files on it are symbolic links of /etc/init.d

- log
  - /var/log/messages
    information of the whole system.
  - /var/log/boot.log
    information about whether each prosess status when booting up is ok or not.
  - /var/log/dmesg
    messages when system booting

- 
  [[http://www.seinan-gu.ac.jp/~shito/old_pages/hacking/shell/sh/boot_shutdown.html][initデーモンを理解する--Debian編（bootとshutdown時に自動的に実行されるプログラムの 仕組み）]]

#### Upstart
#### Systemd
##### Unit
- Feature
  1. Configuration file, not script.
  2. Being able to define relation among units.
  3. Some kind of files existing

- Kind
  |-----------+---------------------------------------------|
  | extention | content                                     |
  |-----------+---------------------------------------------|
  | .service  | settings about process start/stop           |
  | .mount    | settings about mount/unmount of file system |
  | .socket   | about monitoring socket connection          |
  | .device   | device informations system recognized       |
  | .path     | monitoring path                             |
  | .target   | gatherd several units                       |
  |-----------+---------------------------------------------|

- Path
  - /usr/lib/systemd/system
    inital settings. not operating it.
  - /etc/systemd/system
    individual settings by users.
    it is superior to read than the file above(/usr~),
    so you can copy the settigns of the file and edit when you want to change default settings.

##### Link
- http://equj65.net/tech/systemd-boot/
- http://enakai00.hatenablog.com/entry/20130914/1379146157
- http://www.slideshare.net/enakai/linux-27872553
- http://www.slideshare.net/moriwaka/systemd

#### launchd
## Files
### /dev/
#### pts/
##### number
#### urandom
- 外部デバイスの割り込みをエントロピーソースにためる。加工したデータのハッシュ値を取る。
### /etc/
#### crontab
- cronのメイン設定ファイル
#### inittab
- 
  being read by init process for the first time system starting.

- format
  id:runlevels:action:process

  - action
    |-------------+-----------------------------------------------------|
    | action      | meaning                                             |
    |-------------+-----------------------------------------------------|
    | respawn     | starting process, and restarting when it stops      |
    | wait        | starting process, and waiting stop                  |
    | once        | executing once when transferred to target runlevel. |
    | initdefault | default run level                                   |
    | sysinit     | process when booting systems                        |
    | powerfail   | process when                                        |
    | powerokwait |                                                     |
    | ctrlaltdel  | the case when [Ctrl] + [Alt] + [Delete] are pressed |

#### os-release
- Operationg system identification
#### rc*.d
- 
  files on it are symbolic links of /etc/init.d

#### rc.sysinit
#### passwd
- Format
  ユーザ名:暗号化パスワード:UID:GID:ユーザのフルネーム:ユーザのホームディレクトリ:ログインシェル
##### Memo
- ログイン不要のユーザアカウントのログインシェルは、/usr/bin/falseなどとしてログインしてもすぐReturn 1(異常終了)が返る。

#### group
- Format
  グループ名:パスワード:GID:ユーザアカウントのリスト(カンマ区切り)

#### nsswitch.conf
- 
  ネームサービススイッチ(NSS)の設定ファイル。
  いろいろなカテゴリの名前サービス情報を、どの情報源からどの順序で取得するかを判断するのに使用される。
  
#### logrotate.d
- 
  
- commands
  - daily
  - weekly
  - monthly
    頻度の指定

  - missingok
    ログファイルが存在しなくてもエラーを出さずに処理を続行
  - nomissingok
    ログファイルが存在しない場合にエラーを出す
    
  - ifempty
    ログファイルが空でもローテーションする
  - notifempty
    ログファイルが空ならローテーションしない

  - create
    ローテーション後に空のログファイルを新規作成。
  - nocreate
    新たな空のログファイルを作成しない。
    
  - compress
    ローテーションしたログをgzipで圧縮
  - delaycompress
  - nocompress
    ローテーションしたログを圧縮しない

  - olddir [dirname]
    指定したディレクトリにログを格納
  - noolddir
    ローテーション対象のログと同じディレクトリにログを格納

  - sharedscripts
    複数指定したログファイルに対し、postrotateまたはprerotateで記述したコマンドを実行
  - postrotate～endscript
    間に記述されたコマンドをログローテーション後に実行
  - prerotate～endscript
    間に記述されたコマンドをログローテーション前に実行

#### fstab
- 
  起動時にマウントされるデバイスの一覧。

#### mtab
- 
  現在マウントされているデバイス一覧。
  手動でマウントしたものなど、mountコマンドに

#### hosts
#### sysconfig/
##### i18n
- 
  i18nはinternationalisationの略。
  LANG設定などを行う。
##### iptables
- 
  iptables, setting of firewalls.

##### network
- 
  接続するネットワークに関する定義を記述する

##### network-scripts/ifcfg-(eth0,and so on)
- (RHEL?)インターフェース設定ファイル
  個々のネットワークデバイスのソフトウェアインターフェースを制御する。
  どのインターフェースをアクティブにして、どのように設定するかを決定する。
  通常ifcfg-[name]と命名される。[name]は設定ファイルが制御するデバイスの名前。
  [[https://access.redhat.com/documentation/ja-JP/Red_Hat_Enterprise_Linux/6/html/Deployment_Guide/s1-networkscripts-interfaces.html][9.2.インターフェース設定ファイル - redhat カスタマーポータル]]
- BONDING_OPTS=(parameter)
- BOOTPROTO=(protocol)
- BROADCAST=(address)
- DEVICE=(name)
- DHCP_HOSTNAME=(name)
- DNS[1,2]=(address)
- ETHTOOL_OPTS=(option)
- HOTPLUG=(answer)
- HWADDR=(MAC-address)
- IPADDR=(address)
- LINKDELAY=(time)
- MACADDR=(MAC-address)
- MASTER=(bondinterface)
- NETMASK=(mask)
- NETWORK=(address)
- NM_CONTROLLED=(answer)
- ONBOOT=(answer)
  - yes:ブート時にアクティブにされる必要がある
  - no:ブート時にアクティブにされる必要はない
- PEERDNS=(answer)
- SLAVE=(answer)
- SRCADDR=(address)
- USERCTL(answer)

### /proc/
#### cpuinfo
- cpuの情報が含まれている
  コア数など調べることができる。

- Processer数（各種計）
  cat /proc/cpuinfo | grep processor

- 物理CPU数
  cat /proc/cpuinfo | grep "physical id"
  同じ番号は同じ物理CPU

- コア数
  cat /proc/cpuinfo | grep "cpu cores"
  また、"core id"でcoreのidを見ることができる。

#### meminfo
- メモリーの情報が含まれている
  メモリサイズなど調べられる。

#### buddyinfo
- primarily for diagnosing memmory fragmentation issue.
  Using the buddy algorithm, each column represents the number of pages of a certain order (a certain size) that are available at any given time.
  
- DMA(direct memory access)32の領域を
  http://esupport.trendmicro.com/solution/ja-jp/1105158.aspx?print=true

<<<<<<< HEAD:Linux.org
**** slabinfo
**** sys/
***** kernel/random/entropy_avail
- エントロピーの値
*** /var/
**** spool/
***** mail
=======
#### slabinfo
### /var/
#### spool/
##### mail
>>>>>>> da64b3e6149158f439ef4f2f452104987db5f3cf:Linux.md
- 
  mailbox. mails that have sent is saved here temporary.
  later read them by mail command or POP3 for mailer, etc.

- how to clear
  cat /dev/null > /var/spool/mail/root

##### cron/(user)
- ユーザの自動タスク設定ファイル
#### log/
##### messages
- 
  standard kernel / OS log

##### secure
- 
  connected ssh logs

##### cron
- 
  logged cron executed

## Services
### /etc/init.d/crond
### /etc/init.d/network
- 
  /sbin/serviceの起動スクリプト

- command
  - start
  - stop
  - restart
  - status
  
## Tools
### DRBD
- Distributed Replicated Block Device
  分散ストレージシステム。
  HAクラスタで使うのが一般的。
  RAID1に似ているあ、ネットワーク上で動作する。
  中・小規模システム向けで、大規模構成には向いていない可能性を考慮する必要がある。
## Environment Variables
- 
  see list with "printenv"

### LANG
- 
  you can change messages on the shell by changing LANG variable
  ex) export LANG=en_US.UTF-8
  also you can use "export LANG=C"
  if you like to use Japanese, set ja_JP.UTF-8

- Setting
  /etc/sysconfig/i18n

#### LC_ALL
- 
  ロケールに関する環境変数を一括で指定する。
  ただし、個別の設定よりも優先順位が高いため、LC_TIMEなどの設定が反映されなくなる。
  LC_ALLは定義せず、個別に変数を設定するのがよい場合もある。
  [[http://d.hatena.ne.jp/kakurasan/20070711/p2][環境変数LC_ALLは未定義のほうがよい?ロケール用環境変数について - 試験運用中なLinux備忘録]]
  
### HOSTNAME

### SHELL

### PATH

### HOME

### LD_LIBRARY_PATH
- 共有ライブラリ検索パス。

## Shells
### bash
### csh
### fish
- [[http://fishshell.com/][fish shell]]
- [[http://fishshell.com/docs/current/tutorial.html][fish tutorial]]
### tcsh
### zsh
- [[http://www.zsh.org/][Welcome to Zsh]]
- [[file:./Zsh.org][Zsh.org]]

## Distributions
### Debian
#### Debian
##### Version
###### Debian 9 / stretch
###### Debian 8 / jessie
###### Debian 7 / wheezy
###### Debian 6.0 / squeeze
###### Debian GNU/Linux 5.0 / lenny
###### Debian GNU/Linux 4.0 / etch
###### Debian GNU/Linux 3.1 / sarge
- 2005/6/6
###### Debian GNU/Linux 3.0 / woody
###### Debian GNU/Linux 2.2 / potato
###### Debian GNU/Linux 2.1 / slink
###### Debian GNU/Linux 2.0 / hamm
#### Ubuntu
#### Obsoletes
##### KNOPIX
### Red Hat
#### Fedora
#### RHEL
- テスト済みFedoraをベースに安定させた。
- 
  [[https://access.redhat.com/ja/node/16476][Red Hat Enterprise Linux のリリース日と収録カーネルの一覧 - redhat]]
#### CentOS
- RHELのクローン
##### Memo
###### host名の変更
- centos7
  "/etc/hostname"を編集
- centos6
  "/etc/sysconfig/network"を編集
- temporary
  hostname newhostname.newdomainname
#### Scientific Linux
- RHELのクローン
#### Obsoletes
##### Mandriva Linux
##### Yellow Dog Linux
- FedoraベースでPowerPC用。
### Slackware
#### Slackware
#### Puppy Linux
#### openSUSE
#### SUSE linux Enterprise Server
- コミュニティによるテスト済みopenSUSEをベースに安定させた商用Dist。
### Arch系
#### Arch Linux
##### Installation
###### Link
- [[https://wiki.archlinux.org/index.php/Installation_guide][Installation guide - archlinux]]
- [[https://wiki.archlinuxjp.org/index.php/%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%AB%E3%82%AC%E3%82%A4%E3%83%89][インストールガイド - archlinux jp]]
##### Principles 原則
###### Simplicity シンプルであること
###### Modernity 最新であること
###### Pragmatism 実用的であること
###### User centrality ユーザー中心であること
###### Versatility 汎用であること
###### Link
- [[https://wiki.archlinux.org/index.php/Arch_Linux][Arch Linux Principles - archlinux]]
- [[https://wiki.archlinuxjp.org/index.php/Arch_Linux][Arch Linux 原則 - archlinux jp]]
##### Packages
- [[file:Linux_Packages.org][Linux_Packages]]
###### base
- [[https://www.archlinux.org/groups/x86_64/base/][Group Details - base (x86_64)]]
##### Structure
###### /
####### /etc/
######## vconsole.conf
- FONT : Default fontを設定
- FONT_MAP : フォントマップを設定する
######## mkinitcpio.conf
- 
####### /usr/share/kdb/
######## /usr/share/kdb/keymaps/
- キーマップのファイル。loadkeysなどで利用。loadkeysを使う際はパスや拡張子は省略化。
######## /usr/share/kdb/consolefonts/
- コンソールフォント。
####### /sys/firmware/efi/efivars
- UEFIモードで起動しているか確認する。配下にディレクトリが存在しない場合、BIOSもしくはCSMモードで起動している。
##### Memo
###### コンソールの切り替え
- alt+arrowで切り替え可能
##### Link
- [[https://www.archlinux.org/][archlinux]]
- [[https://www.archlinuxjp.org/][archlinux jp]]

- [[https://wiki.archlinuxjp.org/index.php/FAQ][FAQ - ArchWiki jp]]
### Gentoo系
#### Gentoo
#### Chromium OS
### Etc
#### CoreOS
#### LFS / Linux From Scratch
##### Link
- [[http://www.linuxfromscratch.org/lfs/][linux from scratch]]
- [[http://lfsbookja.osdn.jp/][LFSブック日本語版(lfsbookja)]]
#### Alpine Linux
- muslとBusyBoxをベースとしたLinuxディストリビューション。
  セキュリティ、シンプルさ、リソース効率を重視するパワーユーザ向け。
### Link
- [[https://wiki.archlinuxjp.org/index.php/Arch_%E3%81%A8%E4%BB%96%E3%81%AE%E3%83%87%E3%82%A3%E3%82%B9%E3%83%88%E3%83%AA%E3%83%93%E3%83%A5%E3%83%BC%E3%82%B7%E3%83%A7%E3%83%B3%E3%81%AE%E6%AF%94%E8%BC%83#Gentoo.2FFuntoo_Linux][Arch と他のディストリビューションの比較 - archlinux]]
## Desktop Environment
### Unity
- Ubuntu
### GNOME
- Debian
- Fedora
- RHEL
- Ubuntu GNOME
### KDE
- Kubuntu
- openSUSE
### Cinnamon
- Linux Mint
### MATE
- Linux Mint
- Ubuntu MATE
### Xfce
- Xubuntu
### LXDE/LXQt
- Lubuntu
## Package Management
### apt
- Advanced Pckaging Tool
- dpkgを管理するためのツール
#### apt
- apt-getより後継。現在はaptの使用を推奨とのこと。
##### Cheatsheet
- sudo apt update : リポジトリを更新
- sudo apt upgrade : パッケージを更新
- sudo apt full-upgrade : 保留パッケージなど含んだ場合の更新
- sudo apt install (packagename) : インストール
- sudo apt remove (pacagename) : 削除
- sudo apt show (packagename) : 詳細情報を表示
- sudo apt list (packagename) : パッケージを検索（完全一致）
- sudo apt search (packagename) : パッケージを検索（部分一致）
- sudo dpkg -l : インストール済みパッケージの一覧を表示（dpkgですが）

#### apt-get
##### apt-get
###### memo
####### GUIのインストール
- sudo apt-get install ubuntu-desktop
  or
  sudo apt-get install xserver-xorg
##### apt-cache
##### apt-key
##### add-apt-repository
#### aptitude
- aptよりも後に開発され、多機能。
  外部プロジェクト。
#### dpkg
#### Link
- https://eng-entrance.com/linux-package-apt-2
### dnf
- 
  Dandified Yum
  rpm-based package system.
  The next generation version of yum.

### yum
- Yellowdog Updater Modified.
  interactive, rpm based, package manager.
  yumは内部でrpmを呼び出していて、rpmよりも高度。
  
#### commands
##### check
##### check-update
##### clean

##### deplist
##### downgrade
##### erase
##### groupinfo
##### groupinstall
- ex: sudo yum -y groupinstall "X Window System"
- リストは"grouplist"で取得する。
##### grouplist
- ex: yum grouplist hidden
##### groupremove
##### info
- 
  show details.

##### install
- 
  install the latest version of a package or group packages while ensuring that all dependencies are satisfied.

- -y
  answer "yes" to questions in the install message.

##### list
- 
  find out which package provides some feature or file.

##### remove

##### search
- 
  This is used to find packages when you know something about package
  but aren't sure of it's name.

##### update
- 
  If run without any packeages, update will update every currently installed package.
  
##### upgrade

#### error
##### cannot find a valid baseurl
- [[http://nksg.org/archives/22][CentOS で yum がエラーを吐いてしまう - nksg.org]]
#### memo
##### groupinstallできるパッケージのリストを取得
- yum grouplist hidden
  (hiddenを付けないと表示されないものがある)
### rpm
- 
  RPM Package Manager

#### Installing, upgrading, and removing packages
- -i, --install

- -U, --upgrade

- -F, --freshen

- -e, --erase

#### General options
- -v
  Print verbose information

#### Install and upgrade options
- -h, --hash
  Print 50 hash marks as the package archive is unpacked.
  
### pacman
- Package manager on Arch, and MSYS2
#### Synopsis
- pacman <operation> [option] [targets]
#### Operations
##### -D, --database
- Operate on the package database.
##### -Q, --query
- Query the package database.
  This operation allws you to view installed package and their files, as well as meta-information about individual packages.
##### -R, --remove
- Remove package(s) from the system.
##### -S, --sync
- Synchronize packages.
##### -T, --deptest
- Check dependencies; this is useful in scripts such as makepkg tocheck installed packages.
##### -U, --upgrade
- Upgrade or add package(s) to the system and instal the required dependencies from sync repositories.
##### -F, --files
- Query the files database. This operation allows you to look for packages owing certain files or display files owned by certain packages.
##### -V, --version
##### -h, --help
#### Options
##### Options
###### -b, --dbpath <path>
###### -r, --root <paht>
###### -v, --verbose
###### --arch <arch>
##### Transaction Options (apply to -S, -R and -U)
##### Upgrade Options (apply to -S and -U)
##### Query Options
###### -c, --changelog
- View the ChangeLog of a package if it exists.
###### -l, --list
- List all files owned by a geven package.
  Multiple packages can be specified on the command line.
###### -u, --upgrades
- Restrict or filter output to packages that are out-of-date on the local system.
###### -i, --info
- Display information on a given package.
##### Remove Options
###### -c, --cascade
- Remove all target packages, as well as all packages that depend on one or more target packages.
###### -r, --recursive
- Remove each target specified including all of their dependencies.
##### Sync Options
###### -y, --refresh
- Download a fresh copy of the master package database from the server(s) defined in pacman.conf.
  This should typically be used each time you use --sysupgrade or -u.
###### -u, --sysupgrade
- Upgrades all packages that are out-of-date.
  Each currently-installed package will be examined and upgraded if a newer package exists.
###### -i, --info
- Display information on a given sync database package.
##### Database Options
###### --k, --check
##### File Options
###### -y, --refresh
###### -l, --list
- List the files owned by the queried package.
###### -s, --search
###### -x, --regex
###### -o, --owns
###### -q, --quiet
#### Memo
##### Usage
###### Installing packages
- pacman -S package_name1 package_name2
###### Removing packages
- pacman -R package_name
###### Upgrading packages
- pacman -Syu
###### Search packages
- pacman -Ss string1 string2 ...
- (local) pacman -Qs string1 string2 ...
###### Display information (detailed info)
- pacman -Si package_name
- (local) pacman -Qi package_name
##### 操作例
###### ヘルプの表示
- pacman -h
- pacman -S -h : 各オペレーションのヘルプ
###### ミラーの最適化
- sudo pacman -g
###### レポジトリとの同期
- pacman -Syy (apt-get updateに相当)
  プログラムも更新するには、"sudo pacman -Syyu"
###### パッケージの検索
- pacman -Ss [pattern]
- pacman -Qs [pattern] (local)

- pacman -Qi [pattern] (詳細情報)
- pacman -Qii [pattern] (さらに詳細情報、iを重ねる)

- pacman -Qdt (孤児パッケージ/orphansの表示)
###### ソフトウェアの一覧を表示
- pacman -Sl
- pacman -Ql (local)
###### キャッシュ削除
- sudo pacman -Sc
- sudo pacman -Scc (完全に削除)
###### ソフトウェアのアンインストール
- pacman -R [package]
- pacman -Rs [package] (依存パッケージも同時に削除)
#### Link
- [[https://www.archlinux.org/pacman/pacman.8.html][pacman(8) Manual Page]]
- [[https://wiki.archlinuxjp.org/index.php/Pacman][pacman - archlinux]]

- [[https://qiita.com/MoriokaReimen/items/dbe1448ce6c0f80a6ac1][Pacmanの使い方 - Qiita]]
### snap
-  https://snapcraft.io/docs
## Packages
- [[file:Linux_Packages.org][Linux_Packages.org]]
## Reverse lookup
### 連番を生成
- seq関数を使う(詳細はCommand参照)
- ex: seq 1 2 10
      -> 1 3 5 7 9
## Memo
- [[file:Linux_Memo.org][Linux_Memo.org]]
## Link
- [[http://qiita.com/kenju/items/7f9f0ee6a5e2e09596d3][Linuxに関わる人が一度は読むべきStackOverflowまとめ - Qiita]]
