# Unix V6
## Manual
### General commands
### System calls
#### break
#### chdir
#### chmod
#### chown
#### close
#### creat
#### csw
#### dup
#### exec
#### exit
#### fork
#### fstat
#### getgid
#### getpid
#### getuid
#### gtty
#### indir
#### intro
#### kill
#### link
#### mknod
#### mount
#### nice
#### open
#### pipe
#### profil
#### ptrace
#### read
#### seek
#### setgid
#### setuid
#### signal
#### sleep
#### stat
#### stime
#### stty
#### sync
#### time
#### times
#### umount
#### unlink
#### wait
#### write
### C library functions
### Special fiels and devices
### File formats and conventions
### User contributed
### Misc
### System Administration commands and daemons
## Resource Structure
### root
#### sys
##### proc.h
- definition of proc[]の定義
##### ken
###### sys1.c
####### exec()
####### rexit()
####### exit()
####### wait()
####### fork()
####### sbreak()
##### user.h
- definition of user(u)
### src
#### s4
##### fork.s
- fork in C library, written in assembly.
## Assembler
- from "UNIX Assembler Reference Manual by Dennis M. Ritche"
- the usange and input syntax of the UNIX PDP-11 assembler "as".
### Usage
-  as [ - ] file ...
### Lexical conventions
#### Identifiers
#### Temporary symbols
#### Constants
#### Operators
- 
  There are several single- and double-character operators: see the other chapter.
#### Blanks
- 
  Blank and tab characters may be interespersed freely between tokens, but may not be used within tokens.
#### Comments
- /
  The character "/" introduces a comment, which extends through the end of the line on which it appears.
### Segments
### The location counter
- .
  special symbol, ".", is the location counter.
  Its value at any time is the offset within the appropriate segment of the start of the statement in which it appears.
### Statements
#### Labels
- 
  There are two kinds of lable: name labels and nmeric labels.

- name labels
  a name followed by a colon(:).

- numeric labels
  A numeric label consitst of a digit 0 to 9 followed by a colon(:).
  Such a label serves to define temporary symbols of the form "nb" and "nf", where n in the digit of the label.
#### Null statements
#### Expression sattements
#### Assignment statements
#### String statements
#### Keyword statements
### Expressions
#### Expression operators
- Operators
  - (blank)
  - +
  - -
  - *
  - \/
  - &
  - |
  - >>
  - <<
  - %
  - !
  - ^

#### Types
##### undefined
##### undefined external
##### absolute
##### text
##### data
##### bss
##### external absolute, text, data, or bss
##### register
- The following symbols are predefined as register symbols.
  - r0 ...r5
  - fr0 ...fr5
  - sp
  - pc
##### other types
#### Type propagation in expressions
### Pseudo-operations
#### .byte
- .byte expression [, expression ] ...
#### .even
#### .if
- .if expression
#### .endif
#### .global
- .global name [, name ] ...
#### .text
#### .data
#### .bss
#### .comm
- .comm name , expression
### machine instructions
#### Sources and Destinations
#### Simple machine instructions
- symbols
  - clc
  - clv
  - clz
  - cln
  - sec
  - sev
  - sez
  - sen
#### Branch
- symbols
  - br
  - bne
  - beq
  - bge
  - blt
  - bgt
  - ble
  - bpl
  - bmi
  - bhi
  - blos
  - bvc
  - bvs
  - bhis
  - bec (=bcc) : branch on error clear
  - bcc
  - blo
  - bcs
  - bes (=bcs) : branch of error set
#### Extended branch instructions
- sybmols
  - jbr
  - jne
  - jeq
  - jge
  - jlt
  - jgt
  - jle
  - jpl
  - jmi
  - jhi
  - jlos
  - jvc
  - jvs
  - jhis
  - jec
  - jcc
  - jlo
  - jcs
  - jes
#### Single operand instructions
#### Double operand instructions
#### Miscellaneaus instructions
#### Floating-point unit instructions
### Other symbols
#### ..
#### System calls
- 
  - break
  - chdir
  - chmod
  - chown
  - close
  - creat
  - exec
  - exit
  - fork
  - fstat
  - getuid
  - gtty
  - link
  - makdir
  - mdate
  - mount
  - nice
  - open
  - read
  - seek
  - setuid
  - signal
  - stat
  - setuid
  - signal
  - stat
  - stime
  - stty
  - tell
  - time
  - umount
  - unlink
  - wait
    - 
  - write

## C
## PDP-11/40
## Memo
### Process
#### Kernel function
- カーネル空間からユーザ空間のデータを読み書きするためのもの。
- fubyte
- fuibyte
- fuword
- fuiword
- subyte
- suibyte
- suword
- suiword
- [[http://www.manpagez.com/man/9/fuword/][fetch(9) - BSD Kernel Develoker's Manual]]
#### proc composition
- プロセスに関する情報のうち、常にカーネルから必要とされる情報を扱う。
##### Def
- struct proc
  {
      char p_stat;
      char p_flag;
      char p_pri;
      char p_sig;
      char p_uid;
      char p_time;
      char p_cpu;
      char p_nice;
      int  p_ttyp;
      int  p_pid;
      int  p_ppid;
      int  p_addr;
      int  p_size;
      int  p_wchan;
      int  *p_textp;
  } proc[NPROC];

- /* stat codes */
  #define SSLEEP 1
  #define SWAIT  2
  #define SRUN   3
  #define SIDL   4
  #define SZOMB  5
  #define SSTOP  6

- /* flag codes */
  #define SLOAD  01
  #define SSYS   02
  #define SLOCK  04
  #define SSWAP  010
  #define STRC   020
  #define SWTED  040

- /* NPROC (param.h) */
  #define NPROC  50
  
##### Elements
- 
  |----------+-------------------------------------------------------------------------------------|
  | Elements | Meanings                                                                            |
  |----------+-------------------------------------------------------------------------------------|
  | p_stat   | 状態。NULLの場合はそのproc[]エントリは空と見なされる。                              |
  | p_flag   | フラグ。                                                                            |
  | p_pri    | 実行優先度。値が小さいほど優先度が高い                                              |
  | p_sig    | 受診したシグナル                                                                    |
  | p_uid    | ユーザID                                                                            |
  | p_time   | メモリまたはスワップ領域に存在している時間                                          |
  | p_cpu    | CPUを使用した累積時間                                                               |
  | p_nice   | 実行優先度を下げる補足値。デフォルトは0で、niceシステムコールによりユーザが変更可能 |
  | p_ttyp   | プロセスを操作している端末                                                          |
  | p_pid    | プロセスID                                                                          |
  | p_ppid   | 親プロセスID                                                                        |
  | p_addr   | 割り当てられたメモリの物理アドレス                                                  |
  | p_size   | 割り当てられたメモリのサイズ                                                        |
  | p_wchan  | スリープしている理由                                                                |
  | *p_textp | 使用しているテキストセグメント                                                      |
  |----------+-------------------------------------------------------------------------------------|
  
##### Status
- 
  |--------+-----------------------------------------------|
  | Status | Meanings                                      |
  |--------+-----------------------------------------------|
  | SSLEEP | 休眠状態。実行優先度が負でスリープしている    |
  | SWAIT  | 休眠状態。実行優先度が0以上でスリープしている |
  | SRUN   | 実行可能状態                                  |
  | SIDL   | プロセス生成処理中                            |
  | SZOMB  | ゾンビ状態                                    |
  | SSTOP  | トレースによる介入待ち                        |
  |--------+-----------------------------------------------|
  
##### Flags
- 
  |-------+------------------------------------------------|
  | Flags | Meanings                                       |
  |-------+------------------------------------------------|
  | SLOAD | メモリ上に存在する                             |
  | SSYS  | システムプロセスであり、スワップ対象にならない |
  | SLOCK | スワップアウトしてはいけない                   |
  | SSWAP | スワップアウトにより、user.u_rsav[]の値が不正  |
  | STRC  | トレースされている                             |
  | SWTED | トレース処理に使用                             |
  |-------+------------------------------------------------|
  
#### user composition
- プロセスがオープンしたファイルやカレントディレクトリ情報などを扱う。
##### Elements
- 
  |----------+------------------------------------------------------------------|
  | Elements | Meanings                                                         |
  |----------+------------------------------------------------------------------|
  | u_rsav[] | プロセスの切り替え時に、実行中のr5, r6を退避しておく             |
  | u_fsav[] | save fp registers (PDP-11/40環境では使用しない)                  |
  | u_segflg | ファイルの読み書き時に使用されるフラグ                           |
  | u_error  | エラー時にエラーコードが格納される                               |
  | u_uid    | 実効ユーザID                                                     |
  | u_gid    | 実効グループID                                                   |
  | u_ruid   | 実ユーザID                                                       |
  | u_rgid   | 実グループID                                                     |
  | u_procp  | このuser構造体に対応したproc[]エントリを指す                     |
  | *u_base  | ファイルの読み書きをするときに、パラメータを渡すために使用される |
  |          |                                                                  |
  
##### Error codes
- 
  |------------+----------|
  | Error code | Meanings |
  |------------+----------|
  | EFAULT     |          |
  | EPERM      |          |
  | ENOENT     |          |
  | ESRCH      |          |
  
### Interuption
### Block I/O
### Filesystem
### Character I/O
## Tools
### simh
- download
  Mac : brew install simh
#### Link
- [[http://simh.trailing-edge.com/][The Computer History Simulation Project]]
- [[http://simh.trailing-edge.com/pdf/all_docs.html][Simulator Documentation]]
- [[http://ryochack.hatenablog.com/entry/2013/01/30/213105][はじめてのOSコードリーディング #2 simhでV6を動かす - uragami note]]

- [[http://wwwlehre.dhbw-stuttgart.de/~helbig/os/v6/][Unix V6]]
- [[http://wwwlehre.dhbw-stuttgart.de/~helbig/os/v6/doc/index.html][Documents for Unix Sixth Edition]]
- [[http://d.hatena.ne.jp/oraccha/20101101/1288582382][UNIX v6 on simh - Plan9日記]]

## Link
- [[http://minnie.tuhs.org/cgi-bin/utree.pl][The Unix Tree]]
- [[http://man.cat-v.org/unix-6th/][Unix V6 Manuals - Maunal page archive]]
