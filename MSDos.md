# MS-DOS
## Commands
### help
#### apropos
#### fasthelp
#### fdhelp
#### fsuite04
#### help
#### htmlhelp
#### whatis
### internal (command.com) / 内部コマンド
#### alias
#### beep
#### break
#### call
#### chdir, cd
#### cdd
#### chcp
#### cls

#### copy
#### ctty
#### date
#### debug
- Format
  DEBUG [commandfile argument]
- Options
  - help / ?
    使用方法の表示
  - assemble / A [address]
    入力したニーモニックコードをアセンブルし、指定アドレスへ格納する。
  - compare / C range address
  - dump / D range
    メモリの指定範囲を16進ダンプする
  - enter / E adresss [list]
    指定アドレスから1バイトずつ16進入力する。
  - fill / F range data
  - go / G [=address] [breakpoint]
    指定したアドレスからプログラムを実行し、ブレークポイントのアドレスに達すると中断する。
  - proceed / P [=address] [step]
    プログラムをステップごとに実行する
  - quit / Q
    デバッグコマンドを終了する。
  - register / R [register]
    引数なしでレジスタ値の表示
    レジスタ名を引数として付けると、レジスタを変更できる
  - unassemble / U [range]
    逆アセンブルする。
#### del, erase
#### dir
#### dirs
#### doskey
#### echo
#### erase
#### exit
#### for
#### goto
#### history
#### if
#### ifnfor
#### lh
#### loadfix
#### loadhigh
#### memory
#### mkdir, md
#### path
#### prompt
#### pushd
#### rd
#### rem
#### ren, rename
#### rmdir, rd
#### set
#### shift
#### time
#### truename
#### type
- テキストファイルの内容を表示する
#### ver
#### verify
#### vol
#### which
### external command / 外部コマンド
#### append
#### apropos
#### assign
#### attrib
#### backup
#### callver
#### chkdsk
#### choice
#### command
#### comp
#### debug
#### display
#### edit
#### fc
#### fdisk
#### find
#### format
#### freecom
#### help
#### join
#### mem
#### more
#### move
#### print
#### replace
#### sort
#### tree
#### xcopy
### config.sys / fdconfig.sys
#### ;
#### !
#### ?
#### break
#### buffers
#### buffershgih
#### country
#### device
#### devicehigh
#### dos
#### dosdata
#### echo
#### eecho
#### fcbs
#### fileshigh
#### idlehalt
#### install
#### installhigh
#### keybuf
#### lastdrive
#### lastdrivehigh
#### menu
#### menucolor
#### menudefault
#### numlock
#### rem
#### screen
#### set
#### shell
#### shellhigh
#### stacks
#### stackshigh
#### switchar
#### switches
#### version
### Batch / autoexec.bat
#### beep
#### call
#### choice
#### cls
#### echo
#### for
#### goto
#### if
#### lh
#### loadhigh
#### paht
#### pause
#### prompt
#### rem
#### set
#### shift
### Utilities
#### bootfix
#### cal
#### devload
#### dosfsck
#### doslfn
#### fdpkg
#### fdrc
#### foxcalc
#### freemacs
#### locate
#### md5sum
#### ospedit
#### password
#### pcisleep
#### pdtree
#### rdisk
#### ripcord
#### shsufdrv
#### tee
#### touch
#### trch
#### unzip
#### xgrep
#### zip
### Link
- [[http://www.geocities.co.jp/SiliconValley-PaloAlto/2099/ms-dos.html][MS-DOSコマンド一覧表]]
## Settings
### AUTOEXEC.BAT
### FDCONFIG.SYS
## Glossary
### DOSエクステンダー
### DPMI
### LMA
- Lower Memory Area
  the first 640 KiB of memory usually thought of as DOS's normal memory.
### UMA
- Upper Memory Area
## FreeDOS
- [[file:FreeDOS.org][FreeDOS.org]]
## Link
- [[http://www.freedos.org/][FreeDOS]]
- [[http://wiki.freedos.org/wiki/index.php/Main_Page][Main Page - FreeDOS]]
