# FileFormat
## Object File オブジェクトファイル
### ELF / Executable and Linkable Format
- コンパイラが生成するオブジェクト、ライブラリとリンクされた実行ファイルのフォーマット。
  a.outフォーマット、COFFの後継として広く採用されている。
  定義は/usr/include/elf.hに存在。
- System V Release 4 (SVR4)が採用し、GNUツールチェーンがサポートしている。
  BSD派生OSやLinuxをはじめとするフリーなOSにおける実行ファイルフォーマットとして数多く使われる。
- Extensions
  - なし, .o, .so, .elf, .app
- システムローダはプログラムヘッダテーブルに記述されたセグメント集合として扱い、
  コンパイラ、アセンブラ、リンカはセクションヘッダテーブルに記述された論理セクション集合としてELFを扱う。
#### Type
##### 再配置可能オブジェクト
##### 実行可能
##### 共有オブジェクト
##### コア
#### Structure
##### ELF header / ELFヘッダ
- /usr/include/elf.h, Elf[32|64]_Ehdr
###### Structure
####### e_ident[EI_NIDENT]
######## 0 / EI_MAG0
- マジックナンバー１
  0x7F, '\177'
######## 1 / EI_MAG1
- マジックナンバー２
  'E', 0x45
######## 2 / EI_MAG2
- マジックナンバー３
  'L', 0x4c
######## 3 / EI_MAG3
- マジックナンバー４
  'F', 0x46
######## 4 / EI_CLASS
- ファイルクラス
######## 5 / EI_DATA
- データエンコーディング
######## 6 / EI_VERSION
- ファイルバージョン
######## 7
######## 8
######## 9
######## 10-15
- 未定義 (0パディング)
####### e_type
######## 0 / ET_NONE
- 未知のタイプ
######## 1 / ET_REL
- 再配置可能なファイル
######## 2 / ET_EXEC
- 実行可能ファイル
######## 3 / ET_DYN
- 共有オブジェクト
######## 4 / ET_CORE
- コアファイル
######## 0xFF00 / ET_LOPROC
- プロセッサー依存
######## 0xFFFF / ET_HIPROC
- プロセッサー依存
####### e_machine
######## 0 / EM_NONE
- 不明
######## 1 / EM_M32
- AT&T WE 32100
######## 2 / EM_SPARC
- SPARC
######## 3 / EM_386
- intel 80386
######## 4 / EM_68K
- Motorola 68000
######## 5 / EM_88K
- Motorola 88000
######## EM_486
- intel 80486
######## 7 / EM_860
- intel 80860
######## EM_MIPS
####### e_version
######## 0 / EV_NONE
- 無効なバージョン
######## 1 / EV_CURRENT
- 現在のバージョン
####### e_entry
####### e_phoff
####### e_shoff
####### e_flags
####### e_ehsize
####### e_phentsize
####### e_phnum
####### e_shentsize
####### e_shunm
####### e_shstrndx
##### Program header / プログラムヘッダテーブル
- /usr/include/elf.h, Elf[32|64]_Phdr
  セグメントの情報、プログラムを実行するための情報
###### Structure
####### p_type
####### p_offset
####### p_vaddr
####### p_paddr
####### p_filesz
####### p_memsz
####### p_flags
####### p_align
##### Segment / Section
###### 特殊なセクション
####### .bss
- 未初期化データ
####### .comment
- バージョン管理情報
####### .data
- 初期値付きデータ
####### .datal
- 初期値付きデータ
####### .debug
- デバッグ時に使用するシンボル情報
####### .dynamic
- 動的リンク情報やSHF_ALLOC、SHF_WRITEのような属性
####### .hash
- シンボルハッシュテーブル
####### .line
- デバッグ時に使用するプログラムソースとマシン語を対応させたシンボルの行番号
####### .note
- ELFフォーマットについての情報
####### .rodata
- 読み込み専用のデータ
####### .rodatal
- 読み込み専用のデータ
####### .shstrtab
- セクション名
####### .strtab
####### .symtab
- シンボルテーブル
####### .text
- テキスト、またはプログラムの命令
##### Section header / セクションヘッダテーブル
- /usr/include/elf.h, Elf[32|64]_Shdr
  セクションの情報
###### Structure
####### sh_name
- セクション名
####### sh_type
####### sh_flags
####### sh_addr
####### sh_offset
####### sh_size
####### sh_link
####### sh_info
####### sh_addralign
####### sh_entsize
#### デバッグ情報ファイル
- 定義されていないが、DWARF / Debug With Arbitrary Record Formatがよく使われる。
#### Link
- [[http://surf.ml.seikei.ac.jp/~nakano/JMwww/html/LDP_man-pages/man5/elf.5.html][ELF - BSD mandoc]]
- [[http://softwaretechnique.jp/OS_Development/Tips/ELF/elf01.html][Tips ELFフォーマットその１ ELFフォーマットについて - 0から作るソフトウェア開発]]
- [[http://d.hatena.ne.jp/yz2cm/20131012/1381586006][【ESF形式】ELFヘッダ（１） - ゆずさん研究所]]
- [[http://caspar.hazymoon.jp/OpenBSD/annex/elf.html][ELF Formatについて]]
### a.out
- UNIXで使用されていたオブジェクトフォーマット。
### COFF
- System V Release 3 (SVR3)で使用するために作られたフォーマット。
### PE / Portable Executable
- Portable Executable
  主に32ビットおよび64ビットのMS Windows上で使用される実行ファイルのフォーマット。
  UEFIアプリケーションのバイナリフォーマットにはPEが採用されている。
  COFFと似た構造をしている。
#### Structure
- 大きく分けると「MS-DOS用ヘッダおよびプログラム」、「NTヘッダ」、「セクションテーブルおよびセクションデータ」から成る。
##### MS-DOS用ヘッダおよびプログラム
- MS-DOSと互換性をとるもので、2つのフィールドをのぞいてWindowsでは使用されない。
###### MS-DOSヘッダ
- WinNT.hの_IMAGE_DOS_HEADERで定義
####### e-magic
- 0x5A4D("MZ")というマジックナンバーが格納されている。
  MZは設計者Mark Zbikowskiのイニシャル。
  MS-DOSのCOMを除く実行ファイルは必ず"MZ"という文字列がある。
####### e-lfanew
- 新しい形式のヘッダへのファイル内オフセット。
  PEフォーマットならNTヘッダのこと。
###### MS-DOS Real-Mode Stub Program
- 可変長。
##### NTヘッダ
- WinNT.hの_IMAGE_NT_HEADERSで定義。
  マジックナンバーとヘッダのかたまり。
###### Signature シグネーチャ
- PEファイルであることを示すシグネチャ、
  あたいは0x50450000("PE\0\0")
###### FileHeader ファイルヘッダ
- WinNT.h, _IMAGE_FILE_HEADER
####### Machine
####### NumberOfSections
####### TimeDateStamp
####### PointerToSymbolTable
####### NumberOfSymbols
####### SizeOfOptionalHeader
####### Characteristics
######## Flags
######### 0x0001 IMAGE_FILE_RELOCS_STRIPPED
######### 0x0002 IMAGE_FILE_EXECUTABLE_IMAGE
######### 0x0100 IMAGE_FILE_32BIT_MACHINE
######### 0x0400 IMAGE_FILE_REMOVABLE_RUN_FROM_SWAP
######### 0x1000 IMAGE_FILE_SYSTEM
######### 0x2000 IMAGE_FILE_DLL
###### OptionalHeader オプショナルヘッダ
- _IMAGE_OPTIONAL_HEADERで定義。
  オプショナル、とあるがPEでは必須。
####### MAGIC
####### MajorLinkerVersion
####### MinorLinkerVersion
####### SizeOfCode
####### AddressOfEntryPoint
####### ImageBase
####### SectionAlignment
####### FileAlignment
####### SizeOfImage
####### SizeOfHeaders
####### DataDirectory
##### セクションテーブル
###### SectionHeader セクションヘッダ
- WinNT.hの_IMAGE_SECTION_HEADER
##### セクションデータ
#### Link
- [[https://codezine.jp/article/detail/403][Windows実行ファイルのバイナリ概要]]

- http://home.a00.itscom.net/hatada/mcc/doc/pe.html
- http://www.atmarkit.co.jp/ait/articles/1202/17/news129.html
- http://blog.techlab-xe.net/archives/3134
- https://qiita.com/kobadlve/items/5bf9bd946c9dfb77a0f8
- http://www.wivern.com/security20141205.html
### NE / New Executable
- マイクロソフトの16ビットOSで採用された共有ライブラリおよび実行ファイルフォーマットの一つ。
  32ビットWindowsアプリケーションではPortable Executableが使われるようになった。
### EXE
- 連続した一つのメモリイメージ。
  コード、データ、スタックの全てが別々の複数のセグメント
### BAT
- コマンドプロンプトに行わせたい命令列をテキストファイルに記述したもの。
### COM
- コード、データ、スタックの全てのセグメントが同一。
  ファイルヘッダを持たず拡張性がない。いっさいのメタデータをふっ組まない。
  実行時のメモリイメージがそのままファイルとなっている、もっとも単純な実行可能ファイル形式。
### Mach-O 
- Mach object file
  - a file format for executables, object code, shared libraries, dynamically loaded code, and core dumps.
- NEXTSTEPに由来し、macOSで標準のバイナリファイルフォーマットとして採用されている。
  複数アーキテクチャのバイナリを保持可能（ファットバイナリ）
- まーく・おー
- Extensions / 拡張子
  - なし、.o, .dylib
#### 構造
##### FatHeader
##### fat_arch
##### MachHeader
##### ロードコマンド
### PEF / Preferred Executable Format
- Classic Mac OSおよびmacOSの実行ファイル・オブジェクトファイルのフォーマット。
## ファイルアーカイブ
### 7z
### bzip2
### gzip
### tar
### LHA
### RAR
### ZIP
## 音声
### MP3 / MGEP-1 Audio Layer-3
### AAC / Advanced Audio Coding
### ALAC / Apple Lossless Audio Codec
### WAV / RIFF Waveform Audio Format
### WMA / Windows Media Audio
### FLAC / Free Lossless Audio Codec
## 楽曲
### Standard MIDI File / SMF
### DONE SMAF / Synthetic music mobile Application Format
## 動画
### AVI / Audio Video Interleave
### FLV / Flash Video
### MPEG / Moving Picture Experts Group
#### MPEG-1
#### MPEG-2
#### MPEG-4
### MP4 / MPEG-4 Part 14
### MOV / QuickTime Movie
## 画像・図形
### ラスター
#### BMP
- Windowsビットマップ
#### JPEG
#### PNG
#### RAW画像
#### TIFF
### ベクター
#### SVG
