# Farmware
## About
- 組み込んだ電子機器本体に所望の動作をさせるためのソフトウェア。
  一般にROMタイプのメモリ素子書き込む形で機器に組み込みを行う。
## 一次ブートローダ
### BIOS
- Basic Input/Output System
  ブートローダを呼び出して、OSを起動させる。
#### BIOS
##### Documents
###### BIOS Boot Specification
- [[http://www.scs.stanford.edu/05au-cs240c/lab/specsbbs101.pdf][BIOS Boot Specification - Version 1.01]]
###### Embedded BIOS 4.1
- ftp://ftp.embeddedarm.com/old/saved-downloads-manuals/EBIOS-UM.PDF
####### C1: Key Eembedded BIOS Concepts
######## 1.1 Architectural Overview
####### C2: The Integrated BIOS Debugger
######## 2.3 Command Reference
######### ?
######### +
######### -
######### BC
######### BIOSDATA
######### BL
######### BP
######### CIS
######### DB
######### DD
######### DW
######### HELP
######### REBOOT
####### C3: BIOS Function Reference
######## 3.1 INT 10H, Video BIOS Services
######### Write Character to Screen (0Ah)
######### Write Teletype Mode (0Eh)
########## Input Parameters:
- AH: 0eh, indicating the whiret teletype mode function
- AL: Character to write
- BH: Video page number
- BL: Foreground color, but only for graphics modes.
######## 3.2 INT 11H, Equipment List Service
######## 3.3 INT 12H, Low Memory Services Service
######## 3.4 INT 13H, Disk Services
######### Status Description
######### 3.4.1 Reset (00h)
########## Input Parameters:
- AH: 00h, indicating the Reset Function.
- DL: Drive number.
########## Output Parameters:
- CY: Set if failure, else clear if success.
- AH: Status code if failure (00h if success).
######### 3.4.3 Read Sectors (02h)
########## Input Parameters:
- AH: 02h
- AL: Number of sectors
- CH: Bottom 8 bits of track number
- CL: ttssssss, as follows:
  - tt: top two bits of 10-bit track number
  - ssssss: 6-bit sector number
- DH: Head number
- DL: Drive number
- ES:BX: Address of user buffer.
########## Output Parameters:
- CY: Set if failure, else clear if success
- AH: Disk status code
- AL: Number of sectors actually read
######### 3.4.4 Write Sectors (03h)
#### SMBIOS
- System Management BIOS システム管理BIOS
##### Link
- https://www.dmtf.org/standards/smbios
### UEFI
- Unified Extensible Firmware INterface
#### Documentations
##### Unified Extensible Firmware Interface Specification - Version 2.6
- http://www.uefi.org/sites/default/files/resources/UEFI%20Spec%202_6.pdf
## Boot loader 二次ブートローダ
### LILO
### GNU GRUB
- GRand Unified Bootloader
- Linuxのブートローダだが、マルチブート仕様のため、さまざまなOSを起動可能。
### SYSLINUX
- 軽量なLinux用ブートローダ。
### BOOTMGR
- Windows
### NTLDER
- Windows NT/2000/XP
## Memo
### IBM PC互換機のブート手順(x86)
- BIOSの存在する0xFFFF0番地のメモリにある命令を実行する。
  リアルモードのシステムメモリのほぼ最後尾。
- BIOS初期プログラムの位置へのジャンプ命令が含まれていて、BIOSへ制御が渡る
- Power On Self Test (POST)を実行して必要な機器が正常に動作するかチェックする。
  ブート可能なデバイスを探す。第１セクタの最後尾が0xAA55であるもの。
- ブート可能デバイスを発見すると、0x7c00アドレスにそのブートセクタをロードして実行する。
- HDDの場合、ブートセクタはMBRと呼ばれ、OSに依存しない。

#### Link
- http://softwaretechnique.jp/OS_Development/Grub/grub01.html
- https://ja.wikipedia.org/wiki/%E3%83%96%E3%83%BC%E3%83%88#%E4%BA%8C%E6%AC%A1%E3%83%96%E3%83%BC%E3%83%88%E3%83%AD%E3%83%BC%E3%83%80
