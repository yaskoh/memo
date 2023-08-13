# File System
- https://ja.wikipedia.org/wiki/%E3%83%95%E3%82%A1%E3%82%A4%E3%83%AB%E3%82%B7%E3%82%B9%E3%83%86%E3%83%A0
## Kind
### NTFS
#### Glossary
##### Reparse point
- a type of NTFS file system object.
- https://en.wikipedia.org/wiki/NTFS_reparse_point
###### Soft links
####### NTFS symbolic link (SYMLINK)
####### Junction point / directory junction
###### Hard links
####### NTFS HARD link
###### Detect
- Powershell:
  Get-ChildItem | Where-Object { $_.Attributes -match "ReparsePoint" }
### FAT
- File Allocation Table
#### FAT12
- 当初のFATシステム。
  12ビットのクラスタ識別子を利用し、総クラスタ数は最大4084。
  現在は主にフロッピーディスクのフォーマットとして残されている。
- The storage space is divided into units called sectors.
  the size of a sector is 512 bytes.
  In larger storage devices, a bunch of sectors from a cluster.
  But for floppy disk, the number of sectors in a cluster is one.
  
##### Structure
###### Boot Sector (MBR) : Sec 0
####### Boot code (446 bytes)
######## 0-10: Ignore
######## 11-12: Bytes per sector
######## 13: Sectors per cluster
######## 14-15: Number of reserved sector
- FATがどこから始まるか。普通は1セクタ目からとする。
######## 16: Number of FATs
######## 17-18: Maximum number of root directory entries
- ルートディレクトリの大きさ。普通は224。
######## 39-42: Volume id
######## 43-53: Volume label
######## 54-61: File system type
######## 62-: Rest of boot sector (ignore)
####### Partition Tables (64bytes - 16bytes * 4)
####### Boot Signiture (2 bytes)
- 0x55, 0xAA。
  リトルエンディアンなので0xAA55。
###### FAT tables : Sec 1-18
####### FAT1 : Sec 1-9
####### FAT2 : Sec 10-18
###### Root Directory : Sec 19-32
###### Data Area : Sec 33-2879
##### Link
- http://www.dfists.ua.es/~gil/FAT12Description.pdf
- http://fileadmin.cs.lth.se/cs/Education/EDA385/HT09/student_doc/FinalReports/FAT12_overview.pdf

- [[http://park12.wakwak.com/~eslab/pcmemo/fdfat/fdfat4.html][IV. FAT (Fil Allocation Table) - FDの構造とFAT12 - パソコン実習室]]

#### FAT16
#### VFAT
#### FAT32
- FAT12/16/32は完全に下位互換が保たれており、FAT32は12/16、FAT16は12を包含する。
##### 構造
###### ブートセクタ
####### 共通フィールド(0-35)
######## BS_JmpBoot (0,3)
######## BS_OEMName (3,8)
######## BPB_BytesPerSec (11,2)
######## BPB_SecPerClus (13,1)
######## BPB_RsvdSecCnt (14,2)
######## BPB_NumFats (16,1)
######## BPB_RootEntCnt (17,2)
######## BPB_TotSec16 (19,2)
######## BPB_Media (21,1)
######## BPB_FATSz16 (22,2)
######## BPB_ecPerTrk (24,2)
######## BPB_NumHeads (26,2)
######## BPB_HidSec (28,4)
######## BPB_TotSec32 (32,4)
####### FAT12/16(36-512)
######## BS_DrvNum (36,1)
######## BS_Reserved1
######## BS_BootSig
######## BS_VolID
######## BS_VolLab
######## BS_FilSysType
######## BS_BootCode (62,448)
######## BS_BootSign (510,2)
- 0xAA55。有効なブートセクタであることを示すブートシグネチャ。
######## 512-
- 512を超えるセクタサイズの場合は、残りを0で埋める。
####### FAT32(36-512)
##### Memo
###### BPB
- BPB: BIOS Parameter Block
  FATボリュームに関するパラメータが記録される。
  ブートセクタ(VBR:Volume Boot Retord, PBR: Private Boot Record)に配置される
##### Link
- [[http://elm-chan.org/docs/fat.html][FATファイルシステムのしくみと操作法 - ELM]]
#### exFAT
### HFS
### HFS Plus
### HFSX
### ext3
### ext4
## Memo
### Boot sector / ブートセクタ
- HDDやFDなどの補助記憶装置のディスクセクタの一種。
  一般にPC/AT互換機ではブートセクタ、他ではブートブロック(Boot block)と呼ぶことが多い。
- メモリ上の0x7c00に配置される。
#### MBR / Master Boot Record
- PC/AT互換機において、単数・複数のパーティションに分けられたディスクの、パーティション外に存在する先頭セクタ。ブートセクタの一種。
#### PBR / Partition Boot Record
