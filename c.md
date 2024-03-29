# C
## Specification
### C11
#### Language
##### Notation
##### Concepts
##### Conversions
###### Arithmetic operands
####### Boolean, characters, integers
####### Boolean
####### Signed and unsigned integers
####### Real floating and integer
####### Real floating types
####### Complex types
####### Real and
###### Other operands
##### Lexical elements
###### About
####### Syntax
- token:
  - keyword
  - identifier
  - constant
  - string-literal
  - punctuator
- preprocessing-token:
  - header-name
  - identifier
  - pp-number
  - character-constant
  - string-literal
  - punctuator
###### Keywords
####### Syntax
- keyword: one of
  auto break case char const continue default do double else enum extern float for goto
  if inline int long register restrict return short signed sizeof static struct switch typedef union
  unsigned void volatile while _Alignas _Alignof _Atomic _Bool _Complex _Generic _Imaginary _Noreturn _Static_assert _Thread_local
###### Identifiers
####### General
####### Predefined identifiers
###### Universal character names
###### Constants
####### Integer constants
####### Floating constants
####### Enumeration constants
####### Character constants
###### String literals
###### Punctuators
###### Preprocessing numbers
##### Expressions
###### Primary expresions
###### Postfix operators
####### Arary subscripting
####### Function calls
###### Unary operatiors
###### Cast operators
###### Multiplicative operators
###### Additive operators
###### Bitwise shift operators
###### Relational operators
###### Equality operators
###### Bitwise AND operator
###### Bitwise OR operator
###### Logical AND operator
###### Logical OR operator
###### Conditional operator
###### Assignment operators
###### Comma operator
##### Constant expressions
##### Declarations
###### Syntax
- declaration:
  - declaration-specifiers init-declarator-list(opt) ;
- declaration-specifiers:
  - storage-class-specifier declaration-specifiers(opt)
  - type-specifier declaration-specifiers(opt)
  - type-qualifier declaration-specifiers(opt)
  - function-specifier declaration-specifiers(opt)
- init-declaratior-list:
  - init-declarator
  - init-declarator-list , init-declarator
- init-declarator:
  - declarator
  - declarator = initializer

###### Storage-class specifiers
####### Syntax
- storage-class-specifier:
  - typedef
  - extern
  - static
  - auto
  - register
####### Semantics
######## typedef
######## register
- the register specifier suggests that access to the object be as fast as possible.
- The implementation may treat any regster declaration simply as an auto declaration.
######## extern
###### Type specifiers
####### Syntax
- type-specifier:
  - void
  - char
  - short
  - int
  - long
  - float
  - double
  - signed
  - unsigned
  - _Bool
  - _Complex
  - struct-or-union-specifier
  - enum-specifier
  - typedef-name
####### Constraints
- At least one type specifier shall be given in the declaration specifiers in each declaration, and in the specifier-qualifier list in each struct declaration and type name.
####### Semantics
####### Structure and union specifiers
######## Syntax
- struct-or-union-specifier:
  - struct-or-union identifier(opt) { struct-declaration-list }
  - struct-or-union identifier
- struct-or-union:
  - struct
  - union
- struct-declaration-list:
  - struct-declaration
  - struct-declaration-list struct-declaration
- specifier-qualifier-list:
  - type-specifier specifier-qualifier-list(opt)
  - type-qualifier specifier-qualifier-list(opt)
- struct-declarator-list:
  - struct-declarator
  - struct-declarator-list , struct-declarator
- struct-declarator:
  - declarotor
  - declarator(opt) : constant-expression
####### Enumeration specifiers
######## Syntax
- enum-specifier:
  - enum identifier(opt) { enumerator-list }
  - enum identifier(opt) { enumerator-list , }
  - enum identifier
- enumerator-list:
  - enumerator
  - enumerator-list , enumerator
- enumerator:
  - enumeration-constant
  - enumeration-constant = constant-expression
###### Type qualifiers
####### Syntax
- type-qualifier:
  - const
  - restrict
  - volatile
####### Constraints
- Types other than pointer types derived from object or incomplete types shall not be restrict-qualified.
####### Semanticts
######## const
######## restrict
######## volatile
###### Function specifiers
####### Syntax
- function-specifier:
  - inline
####### Constraints
- Function specifiers shall be used only in the declaration of an identifier for a function.
###### Declarators
####### Syntax
###### Type names
###### Type definitions
###### Initialization
##### Statements and blocks
###### Syntax
- statement:
  - labeled-statement
  - compound-statement
  - expression-statement
  - selection-statement
  - iteration-statement
  - jump-statement
###### Labeled statements
###### Compound statement
###### Expression and null statements
###### Selection statements
####### The if statement
####### The switch statement
###### Iteration statements
####### The while statement
####### The do statement
####### The for statement
###### Jump statements
####### The goto statement
####### The continue statement
####### The break statement
####### The return statement
##### External definitions
###### Function definitions
###### External object definitions
##### Preprocessing directives
###### About
####### Syntax
- preprocessing-file:
  - group(opt)
- group:
###### Coditional inclusions
###### Source file inclusion
###### Macro replacement
###### Line control
###### Error directive
###### Pragma directive
###### Null directive
###### Predefined macro names
###### Pragma operator
##### Future language directions
### C99
### ANSI C, C89
### GNU C
### C A REFERENCE MANUAL
- [[https://savedparadigms.files.wordpress.com/2014/09/harbison-s-p-steele-g-l-c-a-reference-manual-5th-ed.pdf][C A REFERENCE MANUAL Fifth Edition (pdf)]]
#### Lexical Elements
##### Characetr Set
###### Characters
- defined in the Basic Latin block of ISO/IEC 10646:
  1. the 52 Latin capital and small letters
  2. the 10 digits
  3. the SPACE
  4. the horizontal tab(HT), vertical tab(VT), and form feed(FF) control characters
  5. the 29 grapihc characters and their official names
     |------+----------------------|
     | Char | Name                 |
     |------+----------------------|
     | !    | EXCLAIMATION MARK    |
     | #    | NUMBER SIGN          |
     | %    | PERCENT SIGN         |
     | ^    | CIRCUMFLEX ACCENT    |
     | &    | AMPERSAND            |
     | *    | ASTERISK             |
     | (    | LEFT PARENTHESIS     |
     | _    | LOWLINE              |
     | )    | RIGHT PARENTHEIS     |
     | -    | HIPHEN-MINUS         |
     | +    | PLUS SIGN            |
     | =    | EQUALS SIGN          |
     | ~    | TILDA                |
     | [    | LEFT SQUARE BRACKET  |
     | ]    | RIGHT SQUARE BRACKET |
     | '    | APOSTROPHE           |
     | ｜   | VERTICAL LINE        |
     | \    | REVERSE SOLIDUS      |
     | ;    | SEMICOLON            |
     | :    | COLON                |
     | "    | QUOTAITON MARK       |
     | {    | LEFT CURLY BRACKET   |
     | }    | RIGHT CURLY BRACKET  |
     | ,    | COMMA                |
     | .    | FULL STOP            |
     | <    | LESS-THAN SIGN       |
     | >    | GREATER-THAN SIGN    |
     | /    | SOLIDUS              |
     | ?    | QUESTION MARK        |
     |------+----------------------|

###### Execution Character Set
###### Whitespace and Line Termination
###### Character Encoding
###### Trigraphs
###### Multibyte and Wide Characters
##### Comments
###### /* */
- bigen with /* and ends with */.
###### //
- from C99
  commentt, up to the next line break
##### Tokens

##### Operators and Separators
- 
  |-------------------------------+------------------------------------|
  | Token class                   | Tokens                             |
  |-------------------------------+------------------------------------|
  | Simple operations             | ! % ^ & * - + = ~ ｜ . < > / ?     |
  | Compound assignment operators | ＋= -= *= /= %= <<= >>= &= ^= ｜=  |
  | Ohter compound operators      | -> ++ -- << >> <= >= == !+ && ｜｜ |
  | Separator characters          | ( ) [ ] { } , ; : ...              |
  | Alternate token spellings     | <% %> <: :> %: %:%:                |
  |-------------------------------+------------------------------------|
  
##### Identifiers
##### Keywords
- Keywords
  auto break case char const continue default do double
  else enum extern float for goto if int long register
  return short signed sizeof static struct switch typedef union unsigned void volatile while

- new keywords in C99 (not reserved in C++)
  _Bool _Complex _Imaginary inline restrict

- iso646.h
  Identifiers in iso646.h are reserved in C++, and might to wish to treat as reserved macros.
  - list
    and and_eq bitand bitor compl not not_eq or or_eq xor xor eq
###### Predefined Identifiers
- 
##### Constants
###### def
- constants:
  - integer-constant
  - floating-constant
  - character-constant
  - string-constant
###### Integer Constants
####### def
- integer-constant:
  - decimal-constant integer-suffix(opt)
  - octal-constant integer-suffix(opt)
  - hexadecimal-constant integer-suffix(opt)
- deciaml-constant:
  - nonzero-digit
  - decimal-constant digit
- octal-constant:
  - 0
  - octal-constant octal-digit
- hexadecimal-constant:
  - 0x hex-digit
  - 0X hex-digit
  - hexadecimal-constant hex-digit
- digit : one of 
  0 1 2 3 4 5 6 7 8 9
- nonzero-digit: one of
  1 2 3 4 5 6 7 8 9
- octal-digit: one of
  0 1 2 3 4 5 6 7
- hex-digit: one of
  0 1 2 3 4 5 6 7 8 9 A B C D E F a b c d e f
- integer-suffix:
  - long-suffix unsigned-suffix(opt)
  - long-long-suffix unsigned-suffix(opt)
  - unsigned-suffix long-suffix(opt)
  - unsigned-suffix long-long-suffix(opt)
- long-suffix: one of
  l L
- long-long-suffix: one of
  ll LL

###### Floating-Point Constants
###### Character Constants
###### String Constants
###### Escape Characters
###### Character Escape Codes
###### Numeric Espace Codes
##### C++ Compatibility
#### C Preprocessor
- lines beginning with the character #.
##### Preprocessor Commads
- original
  - #define
  - #undef
  - #include
  - #if
  - #ifdef
  - #ifndef
  - #else
  - #endif
  - #line
- Not original but common now
  - #elif
  - defined
- New in standard C
  - #operator
  - ##operator
  - #pragma
  - #error
##### Preprocessor Lexical Convention
###### Objectlike Macro Definitions
###### Defining Macros with Parameters
###### Rescanning of Macro Expressions
###### Predefined Macros
- 
  |--------------------------+-------|
  | Macro                    | Value |
  |--------------------------+-------|
  | __LINE__                 |       |
  | __FILE__                 |       |
  | __DATE__                 |       |
  | __TIME__                 |       |
  | __STDC__                 |       |
  | __STDC_VERSION__         |       |
  | __STDC_HOSTED__          |       |
  | __STDC_IEC_559__         |       |
  | __STDC_IEC_559_COMPLEX__ |       |
  | __STDC_ISO_10646__       |       |
  |--------------------------+-------|

###### Undefining and Redefining Macros
- #undef name
##### Definition and Replacement
##### File Inclusion
###### def
- #include < h-car-sequence >
- #include " q-char-sequence "
- #include preprocessor-tokens
- h-char-sequence:
  any sequence of characters except > and end-of-line
- q-char-sequence:
  any sequence of characters except " and end-of-line
- preprocessor-tokens:
  - any sequence of C tokens - or non-whitespace characters
    that cannot be interpreted as tokens - that does not begin with < or "
##### Condition Compilation
###### #if, #else, #endif
###### #elif
###### #ifdef, #ifndef
###### Constant Expressions
###### defined
##### Explicit Line Numbering
###### #line
##### Pragma Directive
##### Error Directive
##### C++ Compatibility
#### Declarations
##### Organization of Declarations
##### Terminology
###### External Names
####### external
###### Compile-Time Names
##### Storage Class and Function Specifiers
##### Type Specifiers and Qualifiers
##### Declarators
##### Initializers
##### Implicit Declarations
##### External Names
##### C++ Compatibility
#### Types
#### Conversions and Representations
#### Expressions
#### Statements
#### Functions
## Standard C library
- 
  標準Cライブラリ。
  /libの中のファイルらしい。
  linuxで普通使われているlibcはGNU libc(glibc)。
  Unix系の場合/usr/includeあたりにある場合が多い。

### assert.h

### complex.h

### ctype.h

#### isalnum
- 
  半角の英字か数字なら0以外（真）を返す。それ以外は0を返す。

- def
  #include <ctype.h>
  int isalnum(int ch);

#### isalpha
- 
  引数chが半角英字なら0以外（真）を、それ以外は0を返す。

- def
  #include <ctype.h>
  int isalpha(int ch);

### errno.h

### fenv.h
- added in C99
### float.h

### inttypes.h
- added in C99
### iso646.h
- added in Amendment 1 to C89
### limits.h

### locale.h

### math.h

### setjmp.h

### signal.h

### stdarg.h
- 
  可変長の引数を定義するためのヘッダ。
  va_listという型の変数を宣言して、使い始める前にva_start、使い終わったらva_endを呼ぶ。
  va_startの第2引数には、va_startが書かれている関数の可変長引数の1つ前の引数を書く。
  va_listを直接渡せる関数が標準ライブラリにいくつかあり、"vfprintf()"などのように先頭にvがついている。

- def
  #include <stdarg.h>
  
  void va_start(va_list ap, last);
  type va_arg(va_list ap, type);
  void va_end(va_list ap);
  void va_copy(va_list dest, va_list src);

### stdbool.h
### stddef.h

### stdint.h
- added in C99
### stdio.h
- 概要
  ストリームおよびファイルの操作に関する型・マクロ・関数の宣言定義
#### fopen(3)
- 
  システムコールのopen()に対応するAPI。

- def
  #inculde <stdio.h>
  FILE *fopen(const char *path, const char *mode);

- argument
  mode:ストリームの性質を指定する。
  |------+-------------------------------+--------------------------------------------------------------|
  | 値   | 対応するopen(2)のmode         | 意味                                                         |
  |------+-------------------------------+--------------------------------------------------------------|
  | "r"  | O_RDONLY                      | 読込み専用。ファイルの存在が前提。                           |
  | "w"  | O_WRONLY ^ O_CREAT ^ O_TRUNC  | 書込み専用。存在しなければ作成。存在したら新たに書込み       |
  | "a"  | O_WRONLY ^ O_CREAT ^ O_APPEND | 追加書込み専用。存在しなければ作成。存在したら末尾に書込む。 |
  | "r+" | O_RDWR                        | 読み書き両用。ファイルの存在が前提。                         |
  | "w+" | O_RDWR ^ O_CREAT ^ O_TRUNC    | 読み書き両用。存在しなければ作成。存在したら新たに書込み。   |
  | "a+" | O_RDWR ^ O_CREAT ^ O_APPEND   | 読み書き両用。存在しなければ作成。存在したら末尾に書込む。   |
  |------+-------------------------------+--------------------------------------------------------------|

- return
  失敗した場合はNULLを返し、原因を表す定数をerrnoにセットする。

#### fclose(3)
- 
  システムコールのclose()に対応する。

- def
  #include <stdio.h>
  int fclose(FILE *stream);

- return
  失敗した場合は定数EOFを返す。
  EOFはstdio.hで定義されるが、普通は-1。

#### fgetc(3), fputc(3)
- 
  バイト単位の入出力API

- def
  include <stdio.h>
  int fgetc(FILE *stream);
  int fputc(int c, FILE *stream);

- fgetc
  streamから1バイト読み込んで返す。
  ストリームが終了した場合はEOF(マクロ、普通は-1)を返す。
  
- fputc
  streamにバイトcを書込む。
  fgetcした値をそのままfputcできるよう、引数のcはcharでなくint。

#### getc(3), putc(3)
- 
  マクロとして定義されたAPI。
  速度のため定義されているが、最近の環境ではfgetc/fputcと対して変わらない。

- def
  #include <stdio.h>
  int getc(FILE *stream);
  int putc(int c, FILE *stream);

#### getchar(3), putchar(3)
- 
  入力元・出力先が固定されているバイト単位の入出力API。
  getchar()はgetc(stdin), putchar(c)はputchar(c, stdout)と同じ意味。

- def
  #include <stdio.h>
  int getchar(void);
  int putchar(int c);

#### ungetc(3)
- 
  バイト単位で値をバッファに戻す。
  読込んだストリームを１つ戻すことができる。

- def
  #include <stdio.h>
  int ungetc(int c, FILE *stream);

#### fgets(3)
- 
  行単位の入力API
  streamから一行読み込んでバッファbufに格納する。
  ただし最大でもsize-1バイトまでしか読み込まない(最後に\0がつくため)。

- def
  #include <stdio.h>
  char *fgets(char *buf, int size, FILE *stream);

- return
  正常に読み込むか、size-1バイト読み込んだ場合はbufを返す。
  一文字も読まずにEOFにあたった場合はNULLを返す。

#### gets(3)
- 
  fgets(3)と類似機能で、1行を取得するが、
  バッファサイズを示す引数がなく、バッファオーバーフローが起こる可能性があるため、
  この関数は使ってはいけない。

- def
  #include <stdio.h>
  char *gets(char *buf);

#### fputs(3)
- 
  文字列bufをstreamに出力する。

- def
  #include <stdio.h>
  int fputs(const char *buf, FILE *stream);

- return
  問題なく出力できた場合は0以上の数字を返す。
  全てのバイト列を書き終わったか、問題が起きた場合はEOFを返す。
  errnoにも値がセットされるが、ストリームが終了した場合と区別するため、
  あらかじめerrnoを0に設定しておく必要がある。

#### puts(3)
- 
  bufを標準出力に出力後、'\n'を出力する。
  fputs(3)との違いは、出力先が標準出力固定の点と、末尾に'\n'が入る点。

- def
  #include <stdio.h>
  int puts(const char *buf);

#### printf(3), fprintf(3)
- 
  fmtで指定した体裁にしたがって後続の引数をフォーマットした文字列を出力する。
  printf(3)は標準出力固定、fprintf(3)はstreamに出力する。

- def
  #include <stdio.h>
  int printf(const char *fmt, ...);
  int fprintf(FILE *stream, const char *fmt, ...);

- 型指定子
  |------+------------------------------------------------|
  | 文字 | 出力                                           |
  |------+------------------------------------------------|
  | c    | unsigned char型の値を文字として出力            |
  | s    | unsigned char*型が示す値を文字列として出力     |
  | d, i | 整数型の値を10進数で出力                       |
  | u    | 符号なし整数型の値を10進表記で出力             |
  | o    | 符号なし整数型の値を8進表記で出力              |
  | x, X | 符号なし整数型の値を16進表記で出力             |
  | f, F | 浮動小数点数型の値を小数点表現(XX.XXXX)で出力  |
  | e, E | 浮動小数点数型の値を「e表記」(XX.XXe+XX)で出力 |
  | g, G | %f(F)と%e(E)の短い方                           |
  | p    | ポインタを16進表記で出力                       |
  |------+------------------------------------------------|

  - X, F, E
    出力するアルファベットが大文字になる。
    %x, 77 -> 4d, %X, 77 -> 4D
  - h, l
    short, long型を取得する場合につける。
    %lxで、long型を16進出力できる。
  - 桁数
    %と型指定子の間に数字を挟む。
    %10dなど。
  - 左詰め
    マイナスを前置する。
    %-5sなど。
  - 0埋め
    0を前置すると空いた部分が0で埋められる。
    %010x, 7 -> 000000004d

- 問題
  標準入力から1行取得してそのままprintf()した場合、%が入っていた場合に問題が起こる可能性あり。
  下記bufに%が入っていた場合に問題発生する。
  ex) char buf[1024];
      fgets(buf, sizeof buf, stdin);
      printf(buf);

#### scanf(3), fscanf(3), sscanf(3), vfscanf(3), vscanf(3), vsscanf(3)
- input format conversion

- フォーマットを指定して入力できる。
  ただし、潜在的にgets()と同様バッファオーバーフローを起こす危険がある。
  ex) scanf("%d", &n);
  また、%s指定した場合も、最初のホワイトスペース(tab, space, 改行)にぶつかった時点で読み込みをやめるので、
  使い方が難しく、gets()が使われる場合が多い。

- 数字を読み込む時などはscanfを使わず、fgets()を使って取得したデータをsscanfでフォーマットするのがおすすめ。
  - fgets(line, sizeof(line), stdin);
    sscanf(line, "%d", &number);


##### Synopsis
- #include <stdio.h>
  int fscanf(FILE *restrict steam, const char *restrict format, ...)
      
#### fread(3)
- 
  streamより、(size * nmemb)バイト読み込み、bufに格納する。
  失敗したか、読みきる前にEOFに到達した場合はnmembより小さい値を返す。
  '\0'を期待しないので、バッファ末尾に'\0'は書き込まない。

- def
  #include <stdio.h>
  size_t fread(void *buf, size_t size, size_t nmemb, FILE *stream);

#### fwrite(3)
- 
  (size * nmemb)バイト分のバイト列をbufからstreamに書き込む。
  成功したらnmembを返す。
  失敗したらnmembより小さい値を返し、errnoをセットする。

- def
  #include <stdio.h>
  size_t fwrite(const void *buf, size_t size, size_t nmemb, FILE *stream);

#### fseek(3), fseeko(3)
- 
  lseek()システムコールに対応する関数。
  streamのファイルオフセットを、whenceとoffsetで示される位置に移動する。
  whenceはlseek()と同じ。
  long型で表せる限度が2GBなので、fseeko()が存在する。
  off_tはデフォルトでlongだが、"#define _FILE_OFFSET_BITS 64"とすることで64ビット符号付整数型となる。

- def
  #include <stdio.h>
  int fseek(FILE *stream, long offset, int whence);
  int fseeko(FILE *stream, off_t offset, int whence);

- whence
  SEEK_SET:offsetに移動（起点はファイル先頭）
  SEEK_CUR:現在のファイルオフセット+offsetに移動
  SEEK_END:ファイル末尾+offsetに移動

#### ftell(3), ftello(3)
- 
  streamのファイルオフセットの値を返す。

- def
  #include <stdio.h>
  long ftell(FILE *stream);
  off_t ftello(FILE *stream);

#### rewind(3)
- 
  streamのファイルオフセットをファイルの先頭に戻す。
- def
  #include <stdio.h>
  void rewind(FILE *stream);

#### fileno(3)
- 
  streamがラップしているファイルディスクリプタを返す。

- def
  #include <stdio.h>
  int flieno(FILE *stream);

#### fdopen(3)
- 
  fdをラップするFILE型の値を新しく作成してポインタを返す。
  失敗したらNULLを返す。
  modeはfopen()の第2引数と同じ。

- def
  #include <stdio.h>
  FILE *fdopen(int fd, const char *mode);

#### fflush(3)
- 
  streamがバッファリングしている内容を即座にwrite()する。
  成功したら0を返す。失敗したらEOFを返してerrnoをセットする。
  改行せずに文字列を端末に出力したいときなどに使う。

- def
  #include <stdio.h>
  int fflush(FILE *stream);

#### setvbuf(3)
- 
  用意したバッファをstdioに強制的に使わせることができる。

#### feof(3)
- 
  直前の読み込み作業でstreamがEOFに達していたら真を返す。
  この関数は必要になることはないし、初心者は使い方を間違えるため、
  使うな、とのこと。

- def
  #include <stdio.h>
  int feof(FILE *stream);

#### ferror(3)
- 
  直前の入出力操作でエラーが起きていたら真を返す。
  ほとんど使わない。

- def
  #include <stdio.h>
  int ferror(FILE *steram);

#### clearerr(3)
- 
  streamのエラーフラグとEOFフラグをクリアする。
  stdioのルーチンはread()が一度でもEOFを返すとFILEにEOFフラグをセットし、
  それ以降はread()を呼ばなくなってしまうので、clearerr()を使うとEOFフラグをクリアできる。

- def
  #include <stdio.h>
  void clearerr(FILE *stream);

#### perror(3)
- 
  "s:"につづきエラーメッセージを出力する。

- def
  #include <stdio.h>

  void perror(const char *s);
- argument
  s:出力用文字列

#### strerror()
- def
  #include <string.h>
  
  char *strerror(int errnum);

- argument
  errnum:errnoを指定する
- 
  errnoの値errnumに対応したエラーメッセージを返す

#### popen(3)
- 
  commandを起動してそれにパイプをつなぎ、そのパイプを表すstdioストリームを返す。
  modeは"r"か"w"。読み書き両用にしたい場合、pipe()とfork()を使いパイプをつなぐ必要がある。
  プログラムがシェル経由で実行されるので、commandにはリダイレクトやパイプも使える。

- def
  #include <stdio.h>
  FILE *popen(const char *command, const char *mode);

#### pclose(3)
- 
  popen()でfork()した子プロセスをwait()し、そのあとにストリームを閉じる。
  popen()で開いたFILE*はpclose()で閉じないといけない。

- def
  #include <stdio.h>
  int pclose(FILE *stream);

#### sprintf(3)
- 
  fmtで指定した体裁にしたがって、後続の引数をフォーマットした文字列をbufに書き込む。
  
- def
  #include <stdio.h>
  int sprintf(char *buf, const char *fmt, ...);

### stdlib.h
- 概要
  一般ユーティリティに関する型・マクロ・関数の宣言定義

#### exit(3)
- 
  statusを終了ステータスとしてプロセスを終了する。
  _exit(2)と異なりlibc関連の処理を始末する。

- def
  #include <stdlib.h>
  void exit(int status);

#### atoi(3), atol(3)
- 整数表現を含む文字列strから対応する整数値を得る。
  atoi : convert ASCII string to integer
  atol : convert ASCII string to long or long long integer.

- def
  #include <stdilb.h>
  int atoi(const char *str);
  long atol(const char *str);

- return
  整数を返す。
  整数が含まれていない場合やエラーが発生した場合は0を返す。

#### strtol(3)
#### strtoll(3)
#### strtod(3)

#### malloc(3)
- 
  sizeバイトのメモリをヒープ領域に割り当てる。
  戻り値がvoid*なので、キャストして使う必要がある。
  メモリ割り当てに失敗したらNULLを返す。
  割り当てられたメモリの内容は保証されない。
- def
  #include <stdlib.h>
  void *malloc(size_t size);

#### calloc(3)
- 
  size × nmembバイトのメモリをヒープ領域に割り当てうr。
  mallocと違い、割り当てたメモリはゼロクリアされている。
  割り当てに失敗したらNULLを返す。
  頭のcはclear。
- def
  #include <stdlib.h>
  void *calloc(size_t nmemb, size_t size);

#### realloc(3)
- 
  mallocで割り当てたメモリのサイズをsizeバイトに拡張または縮小する。
  ptr自体は移動する可能性があるが、内容はコピーされる。
  メモリ割り当てに失敗する可能性があるので、戻り値をそのままポインタに代入してはいけない。

- def
  #inclued <stdlib.h>
  void *realloc(void *ptr, size_t size);

#### free(3)
- 
  malloc(), calloc(), realloc()でヒープ領域に割り当てたメモリを解放する。
  
- def
  #include <stdlib.h>
  void free(void *ptr);

#### system(3)
- 
  fork(2)を使って子プロセスを作成し、execclを使ってcommandで指定されたシェルコマンドを実行する。
- 
  #include <stdlib.h>
  int system(const char *command);

#### getenv(3)
- 
  環境変数nameの値を検索して返す。nameが見つからなければNULLを返す。
  戻り値の文字列に書き込んではいけない。

- def
  #include <stdlib.h>
  char *getenv(const char *name);

#### putenv(3)
- 
  環境変数の値をセットする。
  stringは「名前＝値」の形式でなければならない。間違っている場合の動作は不定。
  putenvは渡したstringを使い続けるため、stringを静的にするかmalloc()で割り当てる必要がある。
  成功したときは0を返す。失敗したときは-1を返してerrnoをセットする。
  
- def
  #include <stdlib.h>
  int putenv(char *string);

### string.h

#### strcpy()
- 
  文字列srcの内容をdestにコピーする。

- def
  #include <string.h>
  char *strcpy(char *dest, const char *src);

#### strchr()
- 
  文字列strから最初にcが出現する場所を探し、そのポインタを返す。

- def
  #include <string.h>
  char *strchr(const char *str, int c);

#### strcat()

#### strcmp()
- 文字列を比較して、同じ場合に0を返す。
  そのため、if(strcmp(str1,str2)){...}とした場合、一致すると実行がされないので使い方に注意。
  if(strcmp(str1,str2) == 0)などとするとよい。
#### strlen()

#### strncasecmp()
- 
  アルファベットの大文字小文字の区別を無視して文字列str1とstr2を比較する。
  な洋画音字なら0を返す。ただし、str1については最初のnバイトしか見ない。
- def
  strncasecmp(const char *str1, const char *str2, size_t n)

#### strspn(3)
- 
  文字列acceptに含まれる文字だけで構成される部分が文字列strの先頭に何文字あるか数え、その長さを返す。

- def
  size_t strspn(const char *str, const char *accept);

### tgmath.h
- added in C99
### time.h
#### localtime(3), gmtime(3)
- 
  time_t型で表された時刻をstruct tm型に変換する。失敗したらNULLを返す。
  localtimeはシステムのローカルタイムゾーン（日本なら日本標準時）を使うが、
  gmtimeは協定世界時(UTC)を使う。
  time_tはタイムゾーン情報が着いていないが、struct tmは時差を含む表現なので、2つのバージョンが必要。
  gmtimeはGMT(Greenwich Mean Time)から。
  静的なバッファに戻り値のstruct tmを確保しているため、もう一度呼ぶと内容が破壊される。
  
- def
  #include <time.h>
  
  struct tm *localtime(const time_t *timep);
  struct tm *gmtime(const time_t *timep);

#### mktime(3)
- 
  localtime()の逆で、struct tm型で表された時刻をtime_t型で表された時刻に変換する。
  失敗したら-1を返す。

- def
  #include <time.h>

  time _t mktime(struct tm *tm);

#### asctime(3), ctime(3)
- 
  時刻を表すデータを"Sat Sep 25 00:43:37 2004\n"のような形式の文字列に変換する。
  asctimeはタイムゾーン情報を考慮するのに対し、ctimeは常にUTC表記。
  戻り値はctimeが静的に管理しているバッファへのポインタなので、もう一度呼ぶと破壊される。

- def
  #include <time.h>
  
  char *asctime(const struct tm *tm);
  char *ctime(const time_t *timep);

#### strftime(3)
- 
  tmの時刻をfmtに従ってフォーマットし、bufに書き込む。ただし、最大でもbufsizeまで。
  呼び出しが成功したらbufに書き込んだバイト数を返し、失敗したら0を返す。

- def
  #include <time.h>
  
  size_t strftime(char *buf, size_t bufsize, const char *fmt,
                  const struct tm *tm);

- フォーマット指定文字列
  |------+--------------+-------------------------------------------------|
  | 文字 | ロケール依存 | 意味                                            |
  |------+--------------+-------------------------------------------------|
  | %a   | o            | 曜日の省略形(LC_TIME=CではMon, Tue, ...)        |
  | %A   | o            | 曜日(LC_TIME=CではMonday, Tuesday, ...)         |
  | %b   | o            | 月名の省略形(LC_TIME=CではJan, Feb, ...)        |
  | %B   | o            | 月名(LC_TIME=CではJanuary, February, ...)       |
  | %c   | o            | 現在のロケールでもっとも自然な形式の日付と時刻  |
  | %C   |              | 年の百の桁以上                                  |
  | %d   |              | 日付。2桁で0埋め(01～31)                        |
  | %D   |              | %m%d%yと同じ                                    |
  | %e   |              | 日付。2桁でスペース埋め(" 1"～31)               |
  | %F   |              | %Y-%m-%dと同じ                                  |
  | %h   | o            | %bの別名                                        |
  | %H   |              | 24時間表記の時。2桁で0埋め(01～23)              |
  | %I   |              | 12時間表記の時。2桁で0埋め(01～12)              |
  | %j   |              | 1月1日を起点とした日数。3桁0埋め(001～366)      |
  | %k   |              | 24時間表記の時。2桁でスペース埋め(" 1"～23)     |
  | %l   |              | 12時間表記の時。2桁でスペース埋め(" 1"～23)     |
  | %m   |              | 月の数字表記(01～12)                            |
  | %M   |              | 分(00～59)                                      |
  | %n   |              | '\n'                                            |
  | %p   | o            | 午前午後の表記(LC_TIME=Cでは"AM"または"PM"      |
  | %P   | o            | 午前午後の表記(LC_TIME=Cでは"am"または"pm"      |
  | %r   | o            | 午前午後の表記がついた時刻(01:15:41 AMなど)     |
  | %R   |              | 24時間表記の時分(HH:MM)。%H:%Mと同じ            |
  | %s   |              | UNIXエポックからの秒数                          |
  | %S   |              | 秒。2桁で0埋め(00～61)。60と61は閏秒            |
  | %t   |              | '\t'                                            |
  | %T   |              | %H:%M:%Sと同じ                                  |
  | %u   |              | 曜日を表す番号(1～7)。月曜が1、日曜が7          |
  | %w   |              | 曜日を表す番号(0～7)。日曜が0、土曜が6          |
  | %x   | o            | 年月日                                          |
  | %X   | o            | 時分秒                                          |
  | %y   |              | 年の下2桁(00～99)                               |
  | %Y   |              | 年                                              |
  | %z   |              | メールの形式で表現したUTCとの時差(-1200～+1200) |
  | %Z   | o            | タイムゾーン(LC_TIME=CならGMTやJST)             |
  | %%   |              | '%'                                             |
  |------+--------------+-------------------------------------------------|

### wchar.h
- added in Amendment 1 to C89
### wctype.h
- added in Amendment 1 to C89
## Libraries
### Linux
#### conio.h

##### getche()
- 
  getchar()をインタラクティブに処理したい場合に使う。

##### cprintf()
- 
  printf()関数と同様のはたらきだが、改行文字を(\n)を復帰改行に変換しない。

##### cscanf()
- 
  scanf()と同様のはたらきをする

#### unistd.h
- 
  Unix Standard Header File

##### getopt(3)
- 
  ショートオプションだけを認識するオプション解析API。
  UNIX系OSに古くから存在する。

- def
  #include <unistd.h>
  int getopt(int argc, char * const argv[], const char *optdecl);
  extern char *optarg;
  extern int optind, opterr, optopt;

- getoptに関連したグローバル変数
  |-------+--------+--------------------------------------------------|
  | 型    | 名前   | 意味                                             |
  |-------+--------+--------------------------------------------------|
  | char* | optarg | 現在処理中のオプションのパラメータ               |
  | int   | optind | 現在処理中のオプションのargvでのインデックス     |
  | int   | optopt | 現在処理中のオプション文字                       |
  | int   | opterr | 真ならばエラー時にgetopt()がメッセージを表示する |
  |-------+--------+--------------------------------------------------|

- return
  オプションがなくなった場合に-1を返す。
  オプションが存在する場合はオプションを返す。

##### getcwd(3)
- 
  カレントディレクトリのパスを得る関数。
  自プロセスのカレントディレクトリをbufに書き込む。
  成功したらbufを返し、失敗したらNULLを返してerrnoをセットする。
  また、パスがbufsize以上になるときはERANGEを返す。

  bufsizeはかつてはlimits.hをインクルードしてPATH_MAXを使っていたが、
  カーネル動作中に変更できるため不十分。
  malloc()を使って長さを調整するべき。
  
- def
  #include <unistd.h>
  char *getcwd(char *buf, size_t bufsize);

#### getopt.h

##### getopt_long(3)
- 
  glibcらしい。

- def
  #define _GNU_SOURCE
  #include <getopt.h>

  int getopt_long(int argc, char * const argv[],
                  const char *optdecl,
                  const struct option *longoptdecl,
                  int *longindex);

  struct option {
      const char *name;
      int has_arg;
      int *flags;
      int val;
  };

  extern char *optarg;
  extern int optind, opterr, optopt;

- struct option member
  |----------+-------+--------------------------------------------------------------------|
  | メンバ名 | 型    | 値と意味                                                           |
  |----------+-------+--------------------------------------------------------------------|
  | name     | char* | ロングオプション名。"lines" "help"など                             |
  | has_arg  | int   | no_argument(または0) : パラメータを取らない                        |
  |          |       | required_argument(または1) : 必ずパラメータを取る                  |
  |          |       | optional_argument(または2) : パラメータをとるかもしれない          |
  | flags    | int*  | NULL : getopt_long()はvalメンバの値を返す                          |
  |          |       | NULL以外 : getopt_long()は0を返し、*flagsにvalメンバの値を代入する |
  | val      | int   | flagsメンバで指定されたところに返す値                              |
  |----------+-------+--------------------------------------------------------------------|

#### regex.h
##### regex
- 
  libcの正規表現API。
  実際どこにあるのかは知らない。

- def
  #include <sys/types.h>
  #include <regex.h>

  int regcomp(regex_t *reg, const char *pattern, int flags);
  void regfree(regex_t *reg);
  int regexec(const regex_t *reg, const char *string,
              size_t nmatch, regmatch_t pmatch[], int flags);
  size_t regerror(int errcode, const regex_t *reg,
                  char *msgbuf, size_t msgbuf_size);

- 一部説明
  - regcomp
    正規表現パターンpatternを専用のデータ型regex_tに変換する。
    結果は第1引数regに書込まれる。
    regのメモリ領域は割り当ててそのポインタを渡す必要があるが、
    その他に独自に確保した領域をregex_t内部に確保する。
    成功したら0を返し、失敗したらエラーコードを返す。
    regerror()でエラーメッセージに変換できる。
  - regfree
    regcompで独自に確保した領域を解放する。
  - regexec
    実際に文字列のパターンを照合する。
    文字列stringがパターンregに適合するなら0を返す。
    適合しなければ、定数REG_NOMATCHを返す。

#### dirent.h
##### opendir(3)
- 
  pathにあるディレクトリを読み込みのため開く。
  戻り値はDIRという型のポインタで、構造体ストリームを管理するための構造体。

- def
  #include <sys/types.h>
  #include <dirent.h>

  DIR *opendir(const char *path);

##### readdir(3)
- 
  ディレクトリストリームdからエントリを一つ読込み、エントリを返す。。
  struct direntはOSにより異なるが、Linuxにはエントリの名前を表す「char *d_name」が存在する。
  d_nameは普通の文字列なので、printf()やfputs()に渡せる。
  エントリがなくなるか読込みに失敗するとNULLを返す。
  ちなみにシステムコールのreaddirもあるので、"man 3 readdir"と明示する必要あり。

- def
  #include <sys/types.h>
  #include <dirent.h>

  struct dirent *readdir(DIR *d);

##### closedir(3)
- 
  ディレクトリストリームdを閉じる関数。
- def
  #include <sys/types.h>
  #include <dirent.h>
  int closedir(DIR *d);

##### seekdir()
- 
  fseek()に相当するdir操作

##### telldir()
- 
  ftell()に相当するdir操作

#### pwd.h

##### getpwuid(3), getpwnam(3)
- 
  getpwuidは、ユーザ情報をユーザIDから検索する。
  getpwnamは、ユーザ情報をユーザ名から検索する。
  該当するユーザが見つからないか、エラーが起きたときはNULLを返してerrnoをセットする。
  戻り値は静的に確保したバッファへのポインタなので、
  次にgetpwuid()やgetpwnam()を呼んだ時点で上書きされる可能性がある。

- def
  #include <pwd.h>
  #include <sys/types.h>
  
  struct passwd *getpwuid(uid_t id);
  struct passwd *getpwnam(const char *name);
  
  struct passwd {
      char *pw_name;    /* ユーザ名 */
      char *pw_passwd;  /* パスワード */
      uid_t pw_uid;     /* ユーザID */
      gid_t pw_gid;     /* グループID */
      char *pw_gecos;   /* 本名 */
      char *pw_dir;     /* ホームディレクトリ */
      char *pw_shell;   /* シェル */
  };

#### grp.h

##### getgruid(3), getgrnam(3)

- 
  getgrgidは、グループ情報をグループIDから検索する。
  getgrnamは、グループ情報をグループ名から検索する。
  いずれも成功したらユーザ名をstruct group形式で返す。
  該当するグループが見つからないか、エラーが起きたときはNULLを返してerrnoをセットする。
  戻り値は静的に確保したバッファへのポインタなので、
  次にgetgruid()やgetgrnam()を呼んだ時点で上書きされる可能性がある。

- def
  #include <grp.h>
  #include <sys/types.h>
  
  struct group *getgrgid(gid_t id);
  struct group *getgrnam(const char *name);
  
  struct group {
      char *gr_name;    /* グループ名 */
      char *gr_passwd;  /* グループのパスワード */
      gid_t gr_gid;     /* グループID */
      char **gr_mem;    /* グループのメンバ（ユーザ名のリスト */
  };
  
### Windows
- [[file:./VisualC++.org][VisualC++]]
### tmp
#### libxml2
- XML C library
#### XZ Utils / liblzma
- free general-purpose data compression software with a high compression ratio.
  successor to LZMA Utils.
- https://tukaani.org/xz/
- https://github.com/kobolabs/liblzma
## syntax
### do { ... } while ();

### break;
### continue;
### switch() { case [value]: ... break; ... ; default ... }
### goto [tag];

### const
- 
  const修飾子は定数宣言。
  const int i = 0 でも int const i = 0でも違いはない。
  ポインタの場合、const int *p = aとすると*pの値（ポインタ先の値）の値が変更できなくなり、
  またint * const p = a とするとpの値（ポインタが示すアドレス）が変更できなくなる。

## Preprocessor
### #include

### #define
- #define マクロ名 文字列

### #if, #else, #elif, #endif

### #ifdef, #ifndef

### macro
#### __LINE__
- 
  ソースの行番号を返す

#### __FILE__
- 
  ファイルの名前を表す文字列を定義する。

#### __DATE__
- 
  月/日/年 のフォーマットでシステム日付を返す

#### __TIME__
- 
  プログラムのコンパイルを開始した時間を表す文字列を定義する。

#### __STDC__
- 
  ANSI Cに準拠している場合に1を返す。

### Memo
#### includeファイルのラインマークの意味
- # 行番号 ファイル名 フラグ
- フラグ
  - 1 : 新しいヘッダーファイルの開始
  - 2 : 呼び出し元のファイルへ戻ったことを示す
  - 3 : システムヘッダーファイルからの引用
  - 4 : 以降の行はCソースであることを示す
#### cppコマンド
- プリプロセッサ用コマンド。
#### 定義済みマクロの確認
- cpp -dM
## Compiler
### clang
### GCC, GNU Compiler Collection
- [[https://www.gnu.org/software/gcc/][GCC, the GNU Compiler Collection]]
#### Specifications
##### 6.2
###### Supported Language
####### C
####### C++
####### Objective-C
####### Objective-C++
####### java
####### Fortran
####### Ada
####### Go
###### Options
- [[https://gcc.gnu.org/onlinedocs/gcc-6.2.0/gcc/Option-Index.html#Option-Index][Option Index]]
- [[https://gcc.gnu.org/onlinedocs/gcc-6.2.0/gcc/Option-Summary.html#Option-Summary][3.1 Option Summary]]
####### About
- Compilation can involve up to four stages: preprocessing, compilation proper, assembly, and linking, always in that order.
######## Suffix, Extentions
######### file.c
- C source code that must be preprocessed.
######### file.i
- C source code that should not be preprocessed
######### file.ii
- C++ source code that should not be preprocessed
######### file.m
- Objective-C source code. Note taht you must link with the libobjc library to make an Objective-C program work.
######### file.mi
- Objective-C source code that should not pe preprocessed.
######### file.mm, file.M
######### file.mii
######### file.h
- C, C++, Objective-C or Objective-C++ header file to be turned into a precompiled header(default)
######### file.cc, file.cp, file.cxx, file.cpp, file.CPP, file.c++, file.C
######### file.M
######### file.mii
######### file.hh, file.H, file.hp, file.hxx, file.hpp, file.HPP, file.h++, file.tcc
######### file.f, file.for, file.ftn
######### file.F, file.FOR, file.fpp, file.FPP, file.FTN
######### file.f90, file.f95, file.f03, file.f08
######### file.F90, file.F95, file.F03, file.F08
######### file.go
- Go source code.
######### file.ads
######### file.adb
######### file.s
- Assembler code.
######### file.S, file.sx
- Assembler code that must be preprocesed.
######### other
- An object file to be fed straight into linking. Any file name with no recognized suffix is treated this way.
####### Overall Optoins
######## -c
- Compile or assemble the source files, but do not link.
  By default, the object file name for a source file is made by replacing the suffix '.c' '.i' '.s', etc., with '.o'.
######## -S
- Stop after the stage of compilation proper, do not assemble.
######## -E
- Stop after the preprocessing stage; do not run the compiler proper.
######## -o 'file'
- Place output in file 'file'.
######## -x 'language'
######## -x none
- Turn off any specification of a language, so that subsequent files are handled according to their file name suffixes
######## -v
- Print the commands executed to run the stages of compilation.
######## -###
######## --help[='class'[,...]]
######## --target-help
######## --version
- Display the version number and copyrights of the invoked GCC.
####### C Language Options
####### C++ Language Options
####### Warning Options
######## -Wall
- This enables all the warnings about constructions that some users consider questionable, and that are easy to avoid, even in conjunction with macros.

- -Wall turns on the following warning flags:
  - -Waddress
  - -Warray-bounds=1 (only with -02)
  - -Wbool-compare
  - -Wc++11-compat
  - -Wc++14-compat
  - -Wchar-subscripts
  - -Wcomment
  - -Wenum-compare (in C/ObjC; this is on by default in C++)
  - Wformat
  - Wimplicit (C and Objective-C only)
    ...
####### Debugging Options
######## -g
####### Optimization Options
######## -O, -O1
- Optimize.
  Optimizing compilation takes somewhat more time, and alot of more memory for a large furction.
  The compiler tries to reduce code size and execution time, without performing any optimizations that take a great deal of compilation time.

- -O turnes on the following optimization flags:
  - -fauto-inc-dec
  - -fbranch-coount-reg
  - -fcombine-stack-adjustments
  - -fcompare-elim
  - -fcprop-registers
  - -fdce
  - -fdefer-pop
  - -fdelayed-branch
    ...
######## -O2
- Optimize even more.
  GCC performs nearly all supported optimizations that do not involve a space-speed trade off.
######## -O3
- Optimize yet more.
######## -O0
- Reduce compilation time and make debugging produce the executed results.
######## -Os
######## -Og
####### Program Instrumentation Options
####### Preprocessor OPtions
####### Assembler Options
####### Linker Options
######## -l'library' -l 'library'
- Search the library named 'library' when linking.
####### Directory Options
######## -I'dir'
- Add the directory 'dir' to the head of the list of directories to be searched for header files.
######## -L'dir'
- Add directory 'dir' to the list of directories to be searched for -l.
####### Machine-Dependent Options
######## ARM
######## Darwin
######## GNU/Linux
######## IA-64
######## SPARC
######## System V
######## VMS
######## x86
######## x86 Windows
#### Link
- [[https://gcc.gnu.org/onlinedocs/][GCC online documentation]]
### Microsoft Visual C++
- [[file:./VisualC++.org][VisualC++]]
### C++ Builder
- 前身はBorland C/C++。更に前身はTurbo C/C++。
### HP C
- [[http://h50146.www5.hpe.com/products/software/oe/hpux/developer/document/pdfs/PDFHS03_028_01.pdf][GNU CCとHP Cの比較]]
### OpenWatcom
#### Link
- [[ftp://ftp.openwatcom.org/manuals/current/cguide.pdf][Open Watcom C/C++ User's Guide]]
## Link
- [[http://www.open-std.org/jtc1/sc22/wg14/www/docs/n1570.pdf][ISO/IEC 9899:201x Programming languages - C - N1570 (C11 final draft)]]
- [[http://www.open-std.org/jtc1/sc22/WG14/www/docs/n1256.pdf][ISO/IEC 9899:TC3 N1256]]
- [[https://savedparadigms.files.wordpress.com/2014/09/harbison-s-p-steele-g-l-c-a-reference-manual-5th-ed.pdf][C A REFERENCE MANUAL Fifth Edition (pdf)]]

- [[https://www.gnu.org/software/gnu-c-manual/][The GNU C Reference Manual]]
- [[https://www.gnu.org/software/libc/manual/][The GNU C Library]]

- [[http://www.jpcert.or.jp/sc-rules/][CERT C コーディングスタンダード - JPCERT]]

### 各種
- [[https://www.grapecity.com/tools/support/powernews/column/][もう一度基礎からC言語 - PowerNews連載コラム GrapeCity]]

## Memo
### C standard
#### K&R, Traditional C
- K&R Cは1978年に出版された本がもとになったもの。
#### ANSI C, C89, Standard C(1989)
- 
  ANSI Cといえば、89年に規定されたものを言うのが普通(C89)。
  K&Rに曖昧な点があったため、ISOとANSIが規格化を進めた。
  - The addition of a truly standard Library
  - New preprocessor commands and features
  - Function prototypes, which let you specify hte argument types in a function feclaration
  - Some new keywords, including const, volatile, and signed.
  - Wide characters, wide strings, and multibyte characters.
  - Many smaller changes and clarifications to conversion rules, declarations, and type checking.
#### C95, C89 with Amendment 1, Stadard C(1995)
- new features
  - three new standard library headers: iso646.h, wctype.h, wchar.h
  - several new tokens and macros
  - some new formatting codes for the printf/scanf family of functions
  - a large number of new functions, some types, consonants for multibyte and wide characters.
#### C99, Standard C(1999)
- 
  99年に改訂された企画はC99と呼ぶ。
  ISO/IEO 9899:1999(E)
- new features
  - complex arithmetic
  - extentions to the integer types, including a longer standard type
  - variable-length arrays
  - a Boolean type
  - better support for non-English character sets
  - better support for floating point types, including math functions for all types
  - C++ style comments (//)

- C11(C2011)
  2011年の改訂版はC2011(C11)。
  ISO/IEO 9899:2011
### Clean C
- the common subset of the Standard C and C++ languages.
  the code can be compiled either as a C program or a C++ program.
- example consideration:
  - Clean C programs must use function prototypes. Old-stype declarations are not perimtted in C++.
  - Clean C programs must avoid using names that are reserved words in C++, like class and virtual.
### ファイルディスクリプタとFILE
- 
  FILEは生のストリームにバッファ機能を追加する層で、
  ファイルディスクリプタをラップしている。
  この2つの型を同時に使うと、バッファを介す操作と介さない操作が混在するため、
  出力順がおかしくなる可能性がある。

### 特殊文字
- 
  |------+---------------+---------------+---------------------------|
  | 数値 | ASCIIでの表記 | C言語での表記 | 意味                      |
  |------+---------------+---------------+---------------------------|
  |    0 | NUL           | '\0'          | 文字列の終端              |
  |    7 | BEL           | '\a'          | ベルを鳴らす              |
  |    8 | BS            | '\b'          | バックスペース(backspace) |
  |    9 | HT            | '\t'          | タブ(holizontal tab)      |
  |   10 | LF            | '\n'          | 改行(line feed)           |
  |   12 | FF            | '\f'          | 改ページ(form feed)       |
  |   13 | CR            | '\r'          | 復帰(carrige return)      |
  |------+---------------+---------------+---------------------------|

### keyword
- 
  auto, break, case, char, const, continue, default, do,
  double, else, enum, extern, float, for, goto, if,
  int, long, register, return, short, signed, sizeof, static,
  struct, switch, typedef, union, unsigned, void, volatile, while

### 演算子の優先順位
- 
  |----------+------------|
  | 優先順位 | 演算子     |
  |----------+------------|
  | 高い     | !          |
  |          | > >= < <=  |
  |          | == !=      |
  |          | &&         |
  | 低い     | ll(パイプ) |
  |----------+------------|

### 基本データ型
- 基本データ型
  char, int, float, double, void
- 型修飾子
  long, short, signed, unsigned

### suffix
- 
  数値のデフォルトはintとdouble。
  末尾に接尾子をつけることで型を変えられる。
- F float
- L long
- U unsigned

### Build
#### preprocess
- 
  #includeや#ifdef等を処理する。
  gcc -Eとすると、プリプロセスだけ処理を行った結果が標準出力に出力される。

- 
  ソースコードに一定の規則に従って処理を加える。
  コンパイルの前処理。#includeや#defineといったマクロの処理をする段階。
  .cファイル、.hファイルが利用される。

#### compile
- 
  C言語のソースコード(*.c)をアセンブリ言語(*.s)に変換する。
  gcc -Sとして処理するとコンパイルまでで処理を中断し、
  アセンブリファイル（*.s）が作成される

#### assemble
- 
  アセンブリ言語のソースコード(*.s)をオブジェクトファイル(*.o)に変換する。
  オブジェクトファイルはいくつかの種類がある。
  代表的なのは以下。
  - ELF (Executable and Linking Format)
  - COFF (Common Object File Format)
  - a.out (assembler output)
  
  gcc -cとして処理すると、アセンブルまでで処理を中断し、*.oというファイルが作成される。

#### link
- 
  オブジェクトファイル(*.o)から実行ファイルまたはライブラリ(*.a, *.so)を生成する。
- 
  複数のobjファイルを一つにまとめ、またlibファイルも統合することで実行ファイルを作成する。

#### 参考
- [[http://c-lang.sevendays-study.com/day7.html][第7日目：ファイル分割 - 一週間で身につくC言語の基本]]
- [[http://www.geocities.jp/sugachan1973/doc/funto53.html][システム奮闘記:その53 プログラムで使う静的ライブラリ、共有ライブラリ C言語(libc,gcc)]]
### Library
#### Static Library 静的ライブラリ
- libxxx.a
  スタティックリンクに使うライブラリで、通常「*.a」となる。
  arというプログラムで作ったアーカイブファイルで、多くのオブジェクトファイルが含まれる。

#### Dynamic Library 共有ライブラリ
- libxxx.so
  共有ライブラリはダイナミックリンクに使うライブラリで、ファイル名は通常「*.so」となる。
  「lib.so.6」のようにバージョン番号がつく場合もある。
  静的ライブラリと異なり全体が1つのオブジェクトファイルとして構成される。

  ちなみにダイナミックロードは、実行時にすべてのリンクの結合をおこなうので、
  コンパイル時にライブラリがなくてもよい。
### extern
- 
  修飾子externを使用すると、変数の実際の記憶域と初期値、または関数の本体が別のソースコードモジュールに定義されていることを示す。
  externとし宣言された関数は、staticとして再定義されない限りプログラム内のすべてのソースファイルで可視となる。
  関数プロトタイプへの使用は任意。C++で関数名が変形されないするようにするには、extern "C"を使用する。

  宣言だけ行い、定義は行わないで済ます方法。

  ファイル分割をした結果、グローバル変数が他ファイルで定義されているが、別ファイルでも利用したい場合などに、
  二重に宣言をせず利用はできるようにするために存在する。

### incomplete type 不完全型
- 
  オブジェクトを規定する型で、その大きさを確定するのに必要な情報が欠けたもの。
  void型、大きさのわからない配列型、内容のわからない構造体型・共用体型など。
- 
  構造体のtypedefのみ書いたものなど。
  パブリックファイルでは構造体のタグのみ宣言し、実際の定義はプライベートファイルに書く。
  例: typedef struct CRB_Interpreter_tag CRB_Interpreter;
  型のサイズがわからないため、ポイントしか使うことができない。変数宣言やsizeof関数、メンバの参照などは利用できない。

### struct
- 型枠の宣言
  構造体は以下のように定義する。
  struct 構造体タグ名 { メンバの並び };
  - ex)
    struct _person {
      char name[20];
      char sex;
      int age;
    };
- 変数宣言
  _personに相当するものは構造体のタグ名であり、変数宣言は以下のように行う必要がある。（struct、を省略できない）
  struct 構造体タグ名 構造体変数名。
  - ex)
    struct _person p; /* p という名前の"struct _person"型変数を定義 */

- typedef
  typedefで型名を付けておけば、通常の型と類似した形で扱えるため、良く用いられる。
  - ex)
    typedef struct _person {
      char name[20];
      char sex;
      int age;
    } person_t;
    
    person_t p;
  
### 拡張整数型
- __int8, __int16, __int32, __int64
  Microsoft C/C++が独自拡張で定義した予約語。
### sizeof演算子
- sizeofは組み込みの演算子。Cの定義に含まれるはず。
  Cの標準ライブラリやOSのシステムコール、ではない。
  
### ヘッダファイルの使い方
- defineについて
  http://www.c-lang.org/define.html
