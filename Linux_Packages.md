# Linux Packages
- 必要に応じ、言語別とする、C関連へ移動するなどするかも。
## Packages
### tmp - Distributions
#### LFS
##### LSB
###### Core
####### Bash
####### Bc
####### Binutils
####### Coreutils
####### Diffutils
####### File
####### Findutils
####### Gawk
####### Grep
####### Gzip
####### M4
####### Man-DB
####### Ncurses
####### Procps
####### Psmisc
####### Sed
####### Shadow
####### Tar
####### Util-linux
####### Zlib
###### Runtime
####### Perl
##### Etc
###### Acl
- アクセス制御リストを管理するツールを提供する。
  ファイルやディレクトリに対して、きめ細かく様々なアクセス権限を定義する
###### Attr
###### Autoconf
###### Automake
#### Debian
- https://www.debian.org/distrib/packages
##### apt-transport-https
- https download transport for APT
##### ca-certificates
- Common CA certificates
##### gnupg2
- GNU privacy guard
##### software-properties-common
- manage the repositories that you install software from
#### Ubuntu
- https://packages.ubuntu.com/
##### build-essential
- https://packages.ubuntu.com/xenial/build-essential
##### liblzma-dev
- XZ-format compression library - development
##### zlib1g-dev
- compression library - development
#### Arch Linux
- https://www.archlinux.org/packages/
##### Core
###### base
####### bash
- The GNU Bourne Again shell
######## Degendencies
- glibc
- ncurses
- readline
- bash-completion
####### bzip2
####### coreutils
- The basic file, shell and text manipulation utilities of the GNU operating system
####### cryptsetup
####### device-mapper
####### dhcpcd
####### filesystem
- Base Arche Linux files
####### file
- File type identification utility
####### gawk
####### gcc-libs
- Runtime libraries shipped by GCC
####### glibc
- GNU C Library
####### grep
####### gzip
####### iproute2
####### inetutils
- http://archive.linux.or.jp/JF/JFdocs/LFS-BOOK/chapter06/inetutils.html
- 概要
  - ftp
  - hostname
  - ping
  - ping6
  - rcp
  - rexec
  - rlogin
  - rsh
  - talk
  - telnet
  - tftp
  - traceroute
####### iputils
####### less
####### linux
####### lvm2
####### man-pages
####### nano
####### pacman
####### perl
####### sed
####### shadow
- Password and account management tool suite with support for shadow files and PAM
####### util-linux
- Miscellaneaus system utilities for Linux
####### tar
####### textinfo
####### vi
####### which
###### base-devel
####### autoconf
####### automake
####### binutils
- A set of programs to assemble and manipulate binary and object files
  https://www.gnu.org/software/binutils/
######## ld
######## as
####### bison
####### flex
####### gcc
- The GNU Compiler Collection - C and C++ frontends
######## Dependencies
- binutils
- gcc-libs
####### gettext
####### make
####### patch
####### pkg-config
####### sudo
####### zlib
######## Dependencies
- glibc
###### etc
####### ncurses
- System V Release 4.0 curses emulation library
  http://invisible-island.net/ncurses/ncurses.html
####### readline
- GNU readline library
##### Extra
###### clang
###### git
- the fast distributed version control system
##### Multilib
##### Testing
### tmp
#### binutils
- [[file:GNUSoftware.org][GNUSoftware.org]]
#### GCC / GNU Compiler Collection
- [[file:GNUSoftware.org][GNUSoftware.org]]
#### libjpeg
- C library for reading and writing JPEG image files.
#### libxpm

## Commands
### rpm
### deb
### ports
### pkg
## Memo
### sftp has no instllation catdidate / SFTPがaptで取得できない
- "sftp"でなく、"openssh-server"を取得するようにする。
## Link
- [[https://launchpad.net/ubuntu/+search?text=][Search packages in Ubuntu]]
- [[https://rpmfind.net/linux/RPM/index.html][Rpmfind.net]]
