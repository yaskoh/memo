# Hardware
## CPU
- [[file:CPU.org][CPU.org]]
## Memory
## Storage
### Type
#### HDD
#### SSD
### Interface
#### SCSI / Small Computer System Interface
- SASI(Shugart Associates System Interface)を拡張し、ANSIによって規格化されたバス型インターフェース。
- 大型のコネクタ・バス等は役目を終えたが、デバイス間の通信プロトコルとしてSCSIコマンドは高速規格でもやりとりされている。
##### 規格
###### SCSI-1
- 1986年ANSIで制定
###### CCS (Common Command Set)
- HDD以外の製品との制御方式統一用コマンドセット。ANSIは無関係。
###### SCSI-2
- 1989年ANSIで制定
###### Ultra SCSI
- 1992年ANSIで制定
##### SCSI Command コマンド
###### Command List
- 00 : TEST UNIT READY
- 01 
###### Link
- https://www.ibm.com/developerworks/jp/linux/library/l-scsi-subsystem/index.html
- http://archive.linux.or.jp/JF/JFdocs/SCSI-Programming-HOWTO.txt
- https://ja.wikipedia.org/wiki/SCSI%E3%82%B3%E3%83%9E%E3%83%B3%E3%83%89
##### Connector コネクタ
##### Terminator ターミネータ
#### ATA / Advanced Technology Attachment
- Parallel ATA
  旧形式。パラレル転送。
- PCとHDD間のインタフェース
##### IDE / Integrated Drive Electronics
- 1986に開発される。
  各社独自の拡張が行われ、互換性に問題が出てきたため、1989年にATAを制定。
  1994年にATA-1として規格化された。
###### 拡張仕様
####### Ultra ATA/33
- 1996年に制定。業界標準であり、IDEの公式な企画ではない。
  しかしATA/ATAPI-4,5などに受け継がれ、規格化されている。
####### Ultra ATA/66
####### Ultra ATA/100
####### Ultra ATA/133
##### EIDE / Enhanced IDE
##### ATAPI / ATA Packet Interface
##### 48bit LBA
##### 規格（ATA/ATAPI）
###### ATA-1
- 1994, ANSI旧規格X3.221-1994
###### ATA-2
- 1996, ANSI旧規格X3.279-1996
###### ATA-3
- 1997, ANSI旧規格X3.298-1997
###### ATA/ATAPI-4
- 1998, ANSI INCITS 317-1998
###### ATA/ATAPI-5
- 2000, ANSI INCITS 340-2000
###### ATA/ATAPI-6
- 2002, ANSI INCITS 361-2002
###### ATA/ATAPI-7
- 2005, ANSI INCITS 397-2005
###### ATA/ATAPI-8 コマンドセット
- 2008, ANSI INCITS 452-2008
###### ATA-8
#### SATA
- Serial ATA
  シリアル転送。
##### 規格
###### SATA1.0
###### SATA1.0a
###### SATA2.0
###### SATA2.5
###### SATA2.6
###### SATA3.0
###### eSATA / External Serial ATA
###### SATA Express
#### AHCI
- Advanced Host Controller Interface
#### NCQ
- Native Command Queuing
#### DAS
- Direct Attached Storage
#### SAN関連
- Storage Attached Network
##### Fibre Channel
- FC-SAN
##### iSCSI
- Internet Small Computer System Interface
- IPネットワークを利用してSANを構築するプロトコル規格。IP-SAN。
  Fibre Channelよりも低価格にSANを構築可能。
  TCP/IP上でネットワークを構築可能。
- SCSIコマンド、データの転送をIPに変換して通信する方式。

###### ターゲット
- 提供する
###### イニシエータ
- ネットワーク経由で利用するクライアント。PCなど。
###### Memo
####### Windowsでの構築
- 2012サーバ以降に搭載されたターゲットサーバと、
  Vista以降に標準搭載されているiSCSIイニシエータを利用する。
- http://www.windows-tips.info/2013/03/26/windows-server-2012-%E3%81%A7-iscsi-%E3%82%BF%E3%83%BC%E3%82%B2%E3%83%83%E3%83%88%E3%82%B5%E3%83%BC%E3%83%90%E3%82%92%E6%A7%8B%E6%88%90%E3%81%99%E3%82%8B%E3%80%82/
- (一部Macも)
  https://www.qnap.com/ja-jp/how-to/tutorial/article/qnap-turbo-nas-%E3%81%A7-iscsi-%E3%82%BF%E3%83%BC%E3%82%B2%E3%83%83%E3%83%88%E3%82%B5%E3%83%BC%E3%83%93%E3%82%B9%E3%82%92%E4%BD%9C%E6%88%90%E3%81%97%E4%BD%BF%E7%94%A8%E3%81%99%E3%82%8B%E6%96%B9%E6%B3%95
##### Link
- https://www.newtech.co.jp/topics/column/ip_san/i1/index.html
- http://www.fujitsu.com/jp/products/computing/storage/lib-f/tech/interface/iscsi/
### Brand
#### HP Storage
##### ディスクストレージ システム
###### HP P9500 Disk Array / XP
###### 
##### ファイルサービス システム
###
### Memo
- [[http://www.nkjmkzk.net/?p=946][サーバ仮想化環境でのお薦めストレージ構成 - nkjmkzk.net]]
## Mother board / マザーボード
### Chipset
#### Northbridge
- CPU、メモリ、PCIエクスプレス、AGPなどをコントロールしている
#### Southbridge
- SATA、PCIスロット、ドライブ類、各種I/Oポートなどをコントロールしている
##### PCI IDE ISX Xcelerator, PIIX, Intel 82371
- マザーボード上のチップセット内でサウスブリッジとして使用されるインテルの集積回路の開発コードネーム
 
##### I/O Controller Hub, ICH, Intel 82801
- マザーボード上のチップセット内でサウスブリッジとして使用されるインテルの集積回路のコードネーム。
###### ICH
###### ICH 2
###### ICH 3
###### ICH 4
###### ICH 5
###### ICH 6
###### ICH 7
###### ICH 8
###### ICH 9
###### ICH 10
## Monitor
## Connector/Cable コネクタ/ケーブル
### 音声・映像用
#### Analog アナログ
##### Phone Connector フォンコネクタ
###### サイズ
####### 6.3mm
- エレキギターなど
####### 4.4mm
####### 3.5mm ミニ
- 一般的な音楽プレーヤーやパソコンなど。
####### 2.5mm ミニミニ、マイクロ
- ポータブル機器、データレコーダ・ICレコーダのコントロール端子など
###### 構造
- 
  |-------------+----------+--------------|
  |             | モノラル | ステレオ     |
  |-------------+----------+--------------|
  | チップ(T)   | 信号線   | 左チャンネル |
  | リング(R)   | N/A      | 右チャンネル |
  | スリーブ(S) | 設置     | 設置         |
  |-------------+----------+--------------|

####### 2極 TS
####### 3極 TRS
####### 4極 TRRS
####### その他
##### S端子
- SはSeparateの略。
##### コンポーネント端子
###### D端子
- 3種類のコンポーネント映像信号を1本のケーブルにまとめ、接続しやすくしたもの。
  日本独自規格。
####### 種類
######## D1
######## D2
######## D3
######## D4
######## D5
##### RCA端子
- 赤、白、黄色の三色。
  コンポジット映像+LR端子。
##### VGA端子、アナログRGB端子
###### バリエーション
- 1: DE-15(ミニD-Sub15)
- 2: 1にVESA DDCの信号を追加
- 3: 1と同等の信号線を9ピンD-Subコネクタに配置
- 4: 1と同等の信号線を同軸ピンを内包した13W3
###### Mini-VGA
##### XLR端子
- マイクの接続など。
#### Digital デジタル
##### DVI
- Digital Visual Interface
##### HDMI
- High-Definition Multimedia Interface
###### Type
####### Type A
- 標準、19ピン
####### Type B
- 29ピン
####### Type C
- ミニHDMI、19ピン。
####### Type D
- マイクロHDMI、19ピン
####### Type E
- 自動車用、19ピン
###### Cable
####### スタンダードHDMIケーブル
- 720p
####### ハイスピードHDMPケーブル
- 1080p
###### Pin
###### Version
####### HDMI 1.0
####### HDMI 1.1
####### HDMI 1.2
######## HDMI 1.2a
####### HDMI 1.3
######## HDMI 1.3a
####### HDMI 1.4
######## HDMI 1.4a
####### HDMI 2.0
######## HDMI 2.0a
######## HDMI 2.0b
####### HDMI 2.1
##### DisplayPort
###### Version
####### 1.0
####### 1.1
####### 1.1a
####### 1.2
####### 1.2a
####### 1.3
####### 1.4
###### Pin
### 通信用
#### LAN端子 (RJ-45)
#### RS-232C (D-Sub 25pin, 9pin) / EIA-232-D/E
- RS-232Cとして広く知られるが、正式規格はEIA-232-D/E。
##### D-sub 9pin, EIA-574
- Dサブ9ピンは規定外で、EIA-574という別の企画に相当する。
###### Pin
##### D-sub 25pin
### コンピュータ用
#### USB / Universal Serial Bus
##### Version
###### USB 1.0
###### USB 1.1
###### USB 2.0
###### USB 3.0
###### USB 3.1
###### USB 3.2
##### Connector / 端子
###### Type 種類
- http://uzurea.net/usb-type-complate-list/
####### USB A
####### USB B
####### Mini USB
######## Mini A
######## Mini B
######## Mini AB
####### Micro USB
######## Micro A
######## Micro B
######## Micro AB
###### 定義の対応
####### USB 2.0まで
- Standard-A
- Standard-B
- Mini USB
- Micro USB
####### USB 3.0まで
- Standard-A
- Standard-B
- Micor USB (B)
####### USB 3.1まで
- Standard-A
- USB-C
#### IEEE 1394コネクタ / FireWire
##### 拡張規格
###### IEEE 1394a-2000
###### IEEE 1394b-2002
###### IEEE 1394c-2006
#### D-subminiature / D-subコネクタ
##### 種類
- 形状およびピン数によって分類される
  1文字目がDサブコネクタを表し、
  2文字目がシェルサイズ(A=15pin, B=25pin, C=37pin, D=50pin, E=9pin)、
  3文字目がピン数を表す。
###### DE-9
- RS-232などのシリアルポートに使われる
###### DA-15
###### DE-15
- 主にAT互換機でアナログディスプレイの接続で使われ、同用途に限りVGA端子と呼ばれる。
###### DB-23F
###### DB-25
###### DC-37
### 電気用
### 同軸
### 
## tmp
### 光学ドライブ
### 電源
### マウス
### キーボード
### 割り込みコントローラ
#### APIC, Advanced Programmable Interrupt Controller
- インテルにより開発された、x86アーキテクチャにおける割り込みコントローラのこと。
##### Local APIC
##### IOAPIC
## Glossary
### HBA
- host bus adapter
  ホストシステム（コンピュータ）と他のネットワーク機器やストレージ機器を接続するハードウェアである。
  主にSCSI、ファイバーチャネル、シリアルATAを接続するデバイスを流石、IDE、Ethernet、Firewire、USBなどを接続するデバイスもホストバスアダプタと呼ぶ。

### IOPS
- Input/Output per Second
  ディスクが1秒当たりに処理できるI/Oアクセスの数。
  I/O処理に係る時間は、平均アクセス時間とデータ転送時間を足した数字であり、
  これが1秒間に何回実行できるかがIOPS。
- 
  [[http://itpro.nikkeibp.co.jp/article/lecture/20070104/258117/?rt=nocnt][Part4 IOPSを理解する - サーバー選択の基礎]]
  
## Memo
### GPU, FPGA
- http://www.atmarkit.co.jp/ait/articles/1604/25/news021.html
  
