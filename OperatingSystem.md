# Operating System
## Role
### はじめて読む486
#### プロセス管理
- 
  アプリケーションの実行を支援し、管理する機能のこと。

##### マルチタスク
- イベント駆動
  イベントを待つタイミングで他のタスクに切り替える
  完全なマルチタスクでないという意味で「擬似マルチタスク」という。

- プリエンプティブ
  一定時間毎にハードウェア割り込みを発生させる回路を利用して、次のタスクに切り替える。
  「完全なマルチタスク」とも呼ばれる。

#### メモリ管理
- 
  メモリ保護や仮想記憶を実現するには、MMU(Memory Management Unit)と呼ばれるハードウェアが必要。

##### メモリ割り当て
- 
  アプリケーションソフトウェアの要求に応じて、メモリを割り当てたり、回収したりする機能。
  システム領域とユーザ領域に分けられる。

##### メモリ保護
- 
  プログラムからアクセスできるメモリ領域を制限する機能。
  他のアプリケーションのメモリにアクセスできないように制限する。

###### アドレス変換機能
- 
  タスクごとにアドレスの対応を変えることによって、すべてのアドレスを自分のメモリのように使える機能。
  逆に、他のタスクのメモリやOSのメモリにはアクセスできないこととなる。

- MMU(Memory Management Unit)の働き
  アドレス変換はMMUによって実現されている。
  アドレス変換表を内部に持ち、それに沿って送られてきた指示番号のアドレス部分を変換する。
  小さな領域を連続した領域として見せることもできる。

- 論理アドレスと物理アドレス
  MMUを通る前のアドレスが論理アドレス、MMUを通り実際にアクセスするアドレスを物理アドレスという。
  その対応状態をメモリマッピングという。

##### 仮想記憶
- 
  実際に搭載されているよりも多くのメモリ領域があるように見せる機能。
  メモリの内容を主記憶へ退避する事で、より多くのメモリが存在するように見せる。
  MMUにメモリ上にデータが存在するかどうかのフラグがある。

#### ファイルシステム
- 
  ディスク装置などの記憶媒体の管理を支援する機能

#### 入出力管理
- 
  さまざまな周辺機器を接続し、アプリケーションから利用できるようにする機能

### Wikipedia
#### ハードウェアの抽象化
#### リソースの管理
#### コンピュータの利用効率の向上
## Components
### Kernel
#### Program execution
#### Interruputs
#### Modes
#### Memory management
#### Virtual memory
#### Multitasking
#### Disk access and file systems
#### Device drivers
### Networking
### Security
### User Interface
## Function
### Main Functions
#### Process Management
- 
  supporting and managing application software's execution.

- Multitask
  Tasks are being switched rapidly, it gets us like that some tasks are executing in same time.
  When program requests I/O and need to wait, then the task is switched to another one, the task is handled and not to lose the time just waiting.

- Event driven
  Pseudo multitask
  Event switches when waiting for new event.

- Preemptive multitask
  
#### Memory Management
- 
  allotting memory by request of program. 

#### File System
- Supporting data storage devices.
  File systems enable to arrange data as directory hierarchies or call them by file name.
- [[file:FileSystem.org][FileSystem.org]]
#### I/O Management
- 
  Enable to connect various peripheral devices and use them by application software.
  "Driver",
#### Protection
## Glossary
### RCU
- read-copy-update
  一種の排他制御を実装する同期機構で、リーダーライターロックの代替手段として使われることがある。

## Kind
### Proprietary
#### IBM
##### MainFrame
###### OS/360系
####### OS/360
####### OS/VS
###### DOS/360系
###### Unix系
##### Mid Range
##### x86
#### Apple
##### Apple II
##### Apple III
##### Apple Lisa
##### Macintosh
###### Classic Mac OS
####### System 1
####### System 2
####### System 3
####### System 4
####### System 5
####### System 6
####### Mac OS 8
####### Mac OS 9
###### Newton
####### Newton OS
###### (Monolithic)
####### A/UX
###### (Mach kernel, Unix-like)
####### MkLinux
####### macOS
######## Mac OS X v10.0
######## Mac OS X v10.1
######## OS X v10.8
######## OS X v10.9
######## OS X v10.10
######## OS X v10.11
######## matOS Sierra
######## Darwin
####### iPhone/iPad/iPod touch
######## iOS
#### Microsoft
##### DOS
###### MS-DOS
###### MSX-DOS
##### OS/2
##### Windows
###### Windows 1.0
###### Windows 2.0
###### Windows 3.x
###### Windows 9x
###### Windows NT
####### Windows NT 3.1
####### Windows 2000
####### Windows XP
####### Windows Server
######## Windows Server 2012
######## Windows Server 2016
####### Windows Vista
####### Windows 7
####### Windows 8.x
######## Windows 8
######## Windows 8.1
####### Windows 10
##### Windows CE
### Non-proprietary
#### Unix-like
##### Research
###### MINIX
###### Unix
##### Free, open source
###### BSD
####### FreeBSD
- [[https://www.ibm.com/developerworks/jp/opensource/library/os-freebsd/][なぜFreeBSDか - developerWorks IBM]]
######## darwin
####### NetBSD
######## OpenBSD
- [[http://cruel.org/openbsd/][OpenBSDの巣窟]]
###### GNU Hurd
###### Linux
###### Link(Free, open source)
- [[https://mag.osdn.jp/05/06/15/0141255][LinuxとBSD - Linusに聞く - OSDNMagazine]]
- [[https://mag.osdn.jp/05/06/20/0123202][BSDから見たLinux - OSDNMagazine]]
#### Non-Unix-like
### Disk operating systems DOS
### Network operating systems
### Embedded
#### Personal digital assistants (PDAs)
#### Mobile phones and smartphones
##### BlackBerry OS
##### Embedded Linux
###### Android
###### Firefox OS
###### Tizen
###### Ubuntu Touch
###### webOS
##### iOS
##### Palm OS
##### Windows Mobile
#### Routers
### Real-time OS, RTOS
#### μITRON
#### Windows CE
## Link
- [[http://kozos.jp/kozos/index.html][独自OSを作ってみよう！ (KOZOS)]]
