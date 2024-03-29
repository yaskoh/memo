# Perl
## About
- Perl - Practical Extraction and Report Language
  
## Options
### -e
- perl -e '[PerlScript]'
  オプションに与えられた文字列をスクリプトとして実行する。

### -i
- -i [extentions]
  edit <> files in place (makes backup if extension supplied)

### -l
- perl -ple '[PerlScript]'
  n, pオプションと組み合わせて使い、ループの前でchompを実施する。
  while(<>) {
    chomp $_;
    [PerlScript]
    print $_;
  }
  
### -n
- perl -ne '[PerlScript]'
  以下のループの内部にスクリプトがあるような動作をする。
  while(<>) {
    [PerlScript]
  }

### -p
- perl -pe '[PerlScript]'
  以下のループの内部にスクリプトがあるような動作をする。
  while(<>) {
    [PerlScript]
  } continue {
    print $_;
  }

### -w
- 
  疑わしいことに警告を出す。
  実際には、内部の$^W変数を有効にするだけ。
  
### -0
- -0[digits]
  入力レコードセパレータ($/)を8進数で示す。digitsを指定しないとヌル文字がセパレータとなる。
  
### Link
- [[http://perldoc.jp/docs/perl/5.6.1/perlrun.pod][perlrun]]
- [[http://blog.layer8.sh/ja/2012/04/16/35881/][Perlコマンド実行時のオプション一覧 - LAYER8]]
## Glammer
### Execution
- running
  perl progname.pl

- file extention
  (something).pl

#### #!
- #!/usr/bin/env perl
  env program
- #!/usr/bin/perl
  bin

#### Safety 
- Perl by default is forgiving. Making more robust, start with the below.
  #!/usr/bin/perl
  use strict;
  use warings;

### Basic syntax
#### syntax
- ;
  statemants end in a semi-colomn;
  ex) print test;

- whitespaces
  irrelevant, except inside quoted strings.

- "
  double quotes is used around literal strings,
  and iinterpolate variables and special characters.
  ex) print "hello, $name\n"  # work fine!

- '
  single quote is used around literal strings, too,
  and not iterpolate special characters etc.

- #
  start with #(hash)

#### conditional and looping costructs
##### if
- format
  if ( condition ) {
    ...
  } elsif ( other condition ) {
    ...
  } else {
    ...
  }

##### unless
- negated version of "if".
- format
  unless ( condition ) {
    ...
  }

##### while
- format
  while ( condition ) {
    ...
  }

- post-condition
  ex) print "LA LA LA" while 1;

##### until
- format
  until ( condition ) {
    ...
  )

##### for
- format
  for ($i = 0; $i <= $max; $i++) {
    ...
  }

##### foreach
- format
  foreach (@array) {
    ...
  }

#### Meta Characters
##### \n
- 改行
##### \f
- Asciiの改ページ
##### \b
- 

### Variables
#### Types
##### Scalars $
- Represents a single value
  Values can be strings, integers, floating point numbers.
  Perl automatically convert between them as required.
  
  There is no need to pre-declare your variable types,
  but daclare variables with "my" keyword, when the first time you use variables.(requirements of [use strict;])
  
  ex) my $test = "test words";
##### Arrays @
- a list of values.
  ex) my @mixed = ("camel", 42, 1.23);

- zero-indexed.
  ex) print $animals[0];
      print $animals[1];

- $#array
  $#array tells the index of the last element of an array.
  ex) print $mixed[$#mixed];

- @array
  return number of elemens (like 「$#array + 1」)

- 
  @array[0,1];  # gives No.0 and No.1 elements
  @array[0..2]; # gives from 0 to 2

##### Hashes %
- a set of key/value pairs.
  ex) my %fruit_color = ("apple", "red" , "banana", "yellow")

- you can define by => operator
  ex) my %fruit_color = (
        apple  => "red",
        banana => "yellow",
      );

- get at hash elemens
  ex) $frout_color{"apple"};   # gives "red"

- get at lists with "keys()" or "values"
  ex) my @fruits = keys % fruit_colors;

#### Scope
##### (none)
- global scope
  ex) $test = "test var";

##### my
- lexical scope
  レキシカルスコープ
  Perl5から実装された。
  Perl4まではlocalだが、5ではmyを使うのが一般的。
  
##### local
- ダイナミックスコープ
  グローバル変数に、一時的に変数名を付け替えるような方式。

#### Special
##### $_
- 
  デフォルト変数。
  
#### Link
- [[http://perldoc.perl.org/perldata.html][perldata]]
### Builtin funcitons
#### Operaters
##### Arithmetic
- + : addition
- - : subtraction
- * : multiplication
- / : division
##### Numeric comparison
- == : equality
- != : inequality
- <  : less than
- >  : greater than
- <= : less then or equal
- >= : greater than or equal
##### String comparison
- eq : equality
- ne : inequality
- lt : less than
- gt : greater than
- le : less than or equal
- ge : greater than or equal
##### Booliean logic
- && : and
- || : or
- !  : not
##### Miscellaneous
- =  : assignment
- .  : string concatenation
- x  : string multiplication
- .. : range operator
##### combined
- many operators can be combined with a =.
  ex) $a += 1;
      $a -= 1;
      $a .= "\n";
#### Files and I/O
##### open()
- open a file for input or output.
##### print()
-
##### printf()
- print formatted
  ex) printf "%.2f C is %.2f F\n", $celsius, $fahrenheit;
##### close()

##### <>
- <FileHundle>
  行入力演算子。
  open(TEST,"<testfile");などと指定したファイルハンドル（この場合TEST）を設定する。

- <STDIN>
  標準入力

- <>
  "$_"というデフォルト変数

#### tmp
##### die()
##### undef()
- undef, undef([EXPR])
  Undefines the value of EXPR, which must be an lvalue.
  引数に指定した変数などを未定義(undef)に設定する。
  
- undef $/;
  テキストをまとめて読み込めるようになるとのこと。

#### Link
- [[http://perldoc.perl.org/perlfunc.html][perlfunc]]
### Regular expressions
#### // : Simple matching
- default, m//
  ex) if (/foo/) { ... }      # true if $_ contains "foo"
      if ($a =~ /foo/) {...}  # true if $a contains "foo"

#### s/// : Simple substitution
- 
  ex) s/foo/bar/;
      $a =~ s/foo/bar/;
      $a =~ s/foo/bar/g;

#### qr// : Regexp quote-like.
- 
  正規表現オブジェクト。
  正規表現を変数に保存できるようにする。
  http://perldoc.perl.org/perlop.html#Regexp-Quote-Like-Operators

#### Modifiers 修飾子
##### m
- 
  Treat string as multiple lines. 
  That is, change "^" and "$" from matching the start of the string's first line and the end of its last line
  to matching the start and end of each line within the string.

- 
  マルチラインモード。実際に行うのは、^と$を入力の最初と最後にマッチさせるよう変更させるのみ。

##### s
- 
  Treat string as single line.
  That is, change "." to match any character whatsoever, even a newline, which normally it would not match.

- 
  シングルラインモード。.(dot)を改行にもマッチさせるように変更する。

##### i
- 
  Do case-insensitive paattern matching.
  大文字と小文字を区別しない。

##### x
- 
  フリーフォームの正規表現。
  ほとんどの空白が無視されるため、複数行に渡っての記載ができる。

- ex)
  $text =~ s{
    \b
    # アドレスを$1にキャプチャする
    {
      username reex
      \@
      hostname regex
    }
    \b
  }{<a href="mailto:$1">$1</a>}gix;

##### g
- 
  グローバル
##### p
- 
  Preserve the string matched such that ${^PREMATCH}, ${^MATCH}, and ${^POSTMATCH} are available for use after matching.

##### n
- 
  Prevent the grouping metahcaracters () from capturing.

#### Backtrace
- Use variables, like $1, $2, ...

#### Escape
- 
  文字クラス内では、$は末尾を指すことはないので、変数のprefixとしてperlでは処理されてしまう。
  同様に@も配列のprefixとみなされるので、文字にマッチさせる場合は@, $をエスケープして使う必要がある。

#### Link
- [[http://perldoc.perl.org/perlre.html][perlre - Perl regular expressions]]
- [[http://perldoc.perl.org/perlretut.html][perlretut - Perl regular expressions tutorial]]
- [[http://perldoc.perl.org/perlrequick.html][perlrequick - Perl regular expressions quick start]]

### Writing subroutines
- Define
  sub subname {
    ...
  }

- Use
  subname();

## Specification
### Perl5 Reference
#### Syntax
#### Data types
#### Subroutine function
#### Operator
#### Functions
##### last
- exit block prematurely
- syntax
  - last LABEL
  - last EXPR
  - last
- 
  The last command is like the break statement in C (as used in loops);
  
##### split
- split up a string using a regexp delimiter
- syntax
  - split /PATTERN/,EXPR,LIMIT
  - split /PATTERN/,EXPR
  - split /PATTERN/
  - split
## Memo
### Interactive mode
- 
  デフォルトでは存在しない。
  
  1. debugger
     perl -de 0

  2. perlish

  3. pirl(Shell::Perl)

  4. re.pl(Devel::REPL)
  
### Numeric and String operator
- 
  Without special variable types, perl need by functions to execute objects numerically or alphabetically.
  when numeric, 99 < 100. when alphabetic, 100 lt 99.

### use, require
- use
  use only after Perl 5.
  evaluate while compiling

- require
  all versions available.
  evaluate when executing
  
### 複数行に渡る置換
- 
  1. Option -0
     本来一行ずつ読み込むところ、セパレータをnullに変更してファイル全体で読み込み処理をする。
  2. modifire s(single line mode, '/s')
     .を改行文字にもマッチさせるように変更する。.*などで改行にもマッチするようになる。
     
## DocMemo
### perlintro memo
- http://perldoc.perl.org/perlintro.html
## Link
- [[https://www.perl.org/][The Perl Proggramming Language]]
- [[http://perldoc.perl.org/index.html][perldoc.perl.org]] 
