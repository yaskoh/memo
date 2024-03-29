# Assembly
## x64 Assembly
### Link
- [[https://software.intel.com/en-us/articles/introduction-to-x64-assembly][Introduction to x64 Assembly]]
## Assembler アセンブラ
### nasm Netwide Assembler
- MASMと互換性の高いx86 CPU用アセンブラ
- nasm -f elf -o program.o program.asm
  (link: ld -o program program.o)
#### 構文
##### 特徴
- Intel構文、TASMやMASMなど大多数のアセンブラがサポート。
- メモリー・オペランドの前にbyte ptr, word ptr, dword ptrをつける
#### manual documents
- https://www.nasm.us/xdoc/2.13.03/html/nasmdoc0.html
##### C1: Introduction
###### S1.1: What Is NASM?
####### S1.1.1: License Conditions
##### C2: Running NASM
###### S2.1: NASM Command-Line Syntax
####### S2.1.1: The -o Option: Specifying the Output File Name
####### S2.1.2: The -f Option: Specifying the Output File Format
- 
- show list: -hf
######## Memo
- -f -elfとした際に "~is incompatible with i386:x86-64"と出る場合、64bitにして置く必要があるので、-f -elf64とする。
- https://stackoverflow.com/questions/4252227/error-when-trying-to-run-asm-file-on-nasm-on-ubuntu?utm_medium=organic&utm_source=google_rich_qa&utm_campaign=google_rich_qa
###### S2.2: Quick Start for MASM Users
##### C3: The NASM Language
###### S3.1: Layout of a NASM Source Line
###### S3.2: Pseudo-Instructions
####### S3.2.1: DB
####### S3.2.2: RESB
####### S3.2.3: INCBIN
####### S3.2.4: EQU
####### S3.2.5: TIMES
###### S3.3: Effectie Addresses
###### $3.5: Expressions
- $ and $$
  - calculating the current assembly position:
  - $: evaluates the assembly position at the beginning of the line containing the expression
  - $$: evaluates to the beginning of the current section
####### 3.5.1: |: Bitwise OR Operator
###### S3.9: Local Labels
- NASM gives special treatment to symbols beginning with a period.
  A label beginning with a single period is treated as a "local" label.
##### C4: The NASM Preprocessor
##### C5: Standard Macro Packages
##### C6: Assembler Directives
###### S6.1:
###### S6.5: EXTERN: Importing Symbols from Other Modules
- it is assumed to be defined in some other modules and needs to be referred to by this one.
###### S6.6: GLOBAL: Exporting Symbols to Other Modules
- other end of EXTERN:
##### C7: Output Formats
##### C8: Writing 16-bit Code
##### C9: Writing 32-bit Code
##### C10: Mixing 16 and 32 Bit Code
##### C11: Writing 64-bit Code
##### C12: Troubleshooting
##### ApA: Ndisasm
##### ApB: Instruction List
##### ApC: NASM Version History
##### ApD: Building NASM from Source
##### ApE: Contact Information
#### Link
- https://www.nasm.us/
### gas GNUアセンブラ
- x86, 680x0, SPARC, VAXなど各種CPU用のアセンブラ
- as -o program.o program.s
  (link: ld -o program program.o)

#### 構文
##### 特徴
- AT&T構文、GASや一部の古いアセンブラに特有、比較的初期の構文。
  最近は".intel_syntax"というIntel構文を使えるディレクティブをサポート
- 即値オペランドの前に$を置く
  レジスターオペランドの前に%を付く
- メモリー・オペランドのサイズはオペコード名の最後の文字で決まる。
  b(8bit), w(16bit), l(32bit)

### MASM Microsoft Macro Assembler
- インテルのx86 CPU用にマイクロソフトが開発したアセンブラ
  「命令 書き込み先 読み込み先」の順で書かれる。GASと逆。

### TASM Turbo Assembler
- ボーランドが開発していたMASMと互換性の高いx86 CPU用アセンブラ

### COMET II
### CASL
- 情報処理技術者試験用に作られたアセンブリ言語。

### as
- UNIX用のアセンブラ

### HLASM / IBM High Level Assembler
- 
  IBM系メインフレーム用のアセンブラ。
  MainFrame。
  
- 
  1-8 ラベル
  10- 命令
  16- オペランド
  
  命令が6文字以上の場合オペランドを合わせてずらすが、
  行が継続する場合は16文字目から。

- コメント
  行全体をコメントとする場合、1桁目に*をおく。
  オペランドが終わった後空白を1文字以上置けばコメントとなる。
  
- 開始
  CSECT命令を使う。
  一般に最初のセクション開始がSTRAT、2番目以降のセクション開始がCSECTとされるが、
  特別な理由がない限りSTARTを使う必要はない。

  CSECTは制御セクションのこと。

- 終了
  END命令を使う。
  END命令はプログラムの実行開始位置を指定することもできる。
  
#### アセンブラ命令
##### CSECT, END
- 
  CSECTが制御セクション（プログラム）の開始、ENDが終了を示す。
  1つのソースプログラム内に複数のCSECTを持つこともできるが、
  CSECT単位にプログラムメンバーを分けて作成し、リンケージエディタでまとめるほうがわかりやすい。

##### EQU
- 
  式や数値に名前をつけるために使う。
  レジスター番号の表記によく使われる。

##### USING, DROP
- 
  ベースレジスタの設定・解除を行う。
  ベースレジスタは、プログラム内で分岐先やデータフィールドを名前で指し示す際に、
  基本となるアドレスがどのレジスタに入っているかをアセンブラに知らせるために用いられる。

  通常はプログラムの先頭アドレスが格納されるレジスタ番号を指定する。
  1つのベースレジスタでアドレスできる範囲は4096バイト。4KB以上の大きさを持つ場合、
  4KB毎に異なるレジスタを用いることとなる。
  
  USINGが設定、DROPが解除。

  USING LABELA,8とすると、LABELAがベースアドレスでベースレジスタは8番。
  USING *,12とすると、USING命令を書いたところがベースアドレスでベースレジスタは12。

##### DC, DS, ORG
- 
  定数又は変数の定義を行う。
  一般にDC命令は定数、DS命令は変数を定義するものと理解されるが、CPUは定数と変数を区別しない。
  定数で定義しても命令で書込みすれば内容は変更できる。
  単にデータ領域、データフィールドをプログラム内に定義する命令と考えればよい。
  
  定義したデータ域に初期値を設定するのがDC命令。

- 定数・変数型
  |--------+-------+------------------------------------------+------|
  | タイプ | 長さ  | 説明                                     | 備考 |
  |--------+-------+------------------------------------------+------|
  | C      | 1byte | 文字領域（バイト域）を設定する           |      |
  | X      | 1byte | 16進数を定義する                         |      |
  | F      | 4byte | フルワードの整数を定義する               |      |
  | H      | 2byte | ハーフワードの定数を定義する             |      |
  | Y      | 2byte | ハーフワード定数をラベルで定義する       |      |
  | D      | 8byte | ダブルワードの浮動小数点を定義する       |      |
  | P      | nbyte | パック10進数を定義する                   |      |
  | A      | 4byte | 命令ラベルや定数のアドレスを定義する     |      |
  | V      | 4byte | 外部モジュールの入口点アドレスを定義する |      |
  |--------+-------+------------------------------------------+------|

##### TITLE, PRINT, SPACE, EJECT
- 
  アセンブルリストの制御に使われる命令。

- TITLE
  リストの各ページの先頭につける見出しを設定する。
  "で囲まれた任意の文字列を見出しとして指定できる。

- PRINT
  ON|OFF（PRINT命令以降のリストを印刷する/しない）、
  GEN|NOGEN（マクロ命令内の各CPU命令などを印刷する/しない）、
  DATA|NODATA（8バイトを超える定数データの内容を全部印刷する/しない）がある。

  NO, NOGEN指定のアセンブルリストはデバッグの役に立たないので指定するべきでない。

- SPACE
  アセンブルリスト中に1行以上の空白行を挿入する。
  SPACE 2とすると2行の空白行が入る。
  パラメータを省略すると1行。

- EJECT
  改ページを行う。
  SPACEおよびEJECT命令自体は印刷されない。

##### SAVE, RETURN
- 
  SAVEマクロ命令は、制御が上位モジュールから渡されたとき
  そのときのレジスターを上位モジュールの保管域に保管する。

  RETURNマクロ命令は、制御を上位モジュールに返す。
  そのときに、保管されたレジスタの復元や戻りコードを設定する。

##### BASR, BAS, BALR, BAL
- 
  BASはBranch And Save。
  第2オペランドで指定されたアドレスへ分岐する。
  一般的には外部サブルーチン呼び出しをBASR、内部呼び出しにBAS命令を使う。
  第1オペランドのレジスタに格納される内容は、呼び出されたサブルーチンから見ると呼び出し下への復帰アドレスとなる。
  
  BAL/BALR(Branch And Link)は昔の命令。

#### Link
- [[http://www.arteceed.net/?cat=12]['S/370アセンブラー講座' Category - 「メインフレーム・コンピュータ」で遊ぼう]]
- [[http://homepage1.nifty.com/ttakao/370asm/index.html][OS/390アセンブラハンドブック]]
### OpenWatcom
- 手動ビルド
  - C:\WATCOM\owsetenv.bat
  - wasm file.asm
  - wcl -ecc -D__MSC__ test.c test.obj
## IDE
### SASM
- https://dman95.github.io/SASM/english.html
### Visual MASM
- https://github.com/ThomasJaeger/VisualMASM
## Memo
### nasmとGASの比較
#### 構文
- nasm: Intel, GAS: AT&T
- 
- 例
  - Intel(nasm): mov eax, 4
  - AT&T(GAS): movl $4, %eax

## Link
- [[https://www.ibm.com/developerworks/jp/linux/library/l-gas-nasm.html][GAS と NASM を比較する - IBM developerWorks]]
- [[http://qiita.com/usk83/items/c97066c3c663c5007658][(スクリプト言語しか書けないあなたへ)FreeDOSとdebugコマンドで8086アセンブラ入門 - Qiita]]
