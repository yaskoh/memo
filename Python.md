# Python
## Command
### python
- usage
  python [-bBdEhilOqsSuvVWx?] [-c command | -m module-name | script | -] [args]

- -c <command>
- -m <module-name>
- -
  標準入力(sys.stdin)からコマンドを読み込む。
- <script>
  script内のPythonコードを実行する。

- -?, -h, --help
  全コマンドラインオプションの短い説明を出力する。
- -V, --version
  Pythonのバージョンを表示する
### argument
- sys.argv変数にスクリプト名やそれ以降の引数が格納される。
### Environmental variables
#### PYTHONHOME
- 標準Pythonライブラリの場所を変更する。
#### PYTHONPATH
- モジュールファイルのデフォルトの検索パスを追加する。
#### PYTHONSTARTUP
- この変数が読み込み可能なファイル名の場合、対話モードで最初のプロンプトが表示される前にそのファイルのPythonコマンドが実行される。
#### PYTHONPTIMIZE
#### PYTHONDEBUG
#### PYTHONINSPECT
#### PYTHONUNBUFFERED
#### PYTHONVERBOSE
#### PYTHONCASEOK
#### PYTHONDONTWRITEBYTECODE
#### PYTHONHASHSEED
## Language
### Lexical analysis
- This describes how the lexical analyzer breaks a file into tokens.
- lexical analyzer generates 'tokens', then parser reads them.
#### Line structure
- A Python program is divided into a number of "logical lines".
##### Logical lines
- The end of a logical line is represented by the token NEWLINE.
  A logical line is constructed from one or more physical lines.
##### Physical lines
- a sequence of characters terminated by an end-of-line sequence.
##### Comments
- A comment starts with hash (#), and ends at the end of physical lise.
- ハッシュ"#"から始まり、同じ物理行の末端で終わる。
##### encoding declaration
- 
  スクリプトの一行目か二行目にあるコメントが正規表現"coding[=:]\s*([-\w.]+)"にマッチする場合、コメントはエンコード宣言として処理される。
  推奨系は以下。
  - Emacs : # -*- coding: <encoding-name> -*-
  - vim:fleeencoding=<coding-name>
- By default, Python source files are treated as encoded in UTF-8.
##### Explicit line joining 明示的な行継続
##### Implicit line joining 非明示的な行継続
##### 空行
##### Indent インデント
##### トークン間の空白
#### Token
##### Identifier
- 
###### reserved
##### Keyword
- 
  False, None, True
  and, as, assert, break, class, continue
  def, del, elif, else, except, finally
  for, from, global, if, import, in, is,
  lambda, nonlocal, not, or, pass, raise, return,
  try, while, whithe, yield, pass, raise

##### Literal
###### Strings literal
- 
  - stringliteral ::= [stringprefix](shortstring | longstring)
  - stringprefix ::= "r" | "u" | "R" | "U"
  - shortstring ::= "'" shortstringitem* "'" | '"' shortstringitem* '"'
  - longstring ::= "'''" longstringitem* "'''" | '"""' longstringitem* '"""'

###### Concatenation
###### Number literal
####### Integer literal
####### Iloat literal
####### Imaginary literal
- imagnumber ::= (floatnumber|intpart) ("j"|"J")
- ex)
  3.14j 10J
##### Operator
- 
  +, -, *, **, /, //, %, @, <<, >>, &, |,
  ^, ~, <, >, <=, >=, ==, !=

##### Delimiter
- 以下は文法上のデリミタとして働く
  ( ) [ ] { } , : . ; @ = ->
  += -= *= /= //= %= @= &= |= ^= >>= <<= **=
  
- 他のトークンの一部として特殊な意味を持っていたり、字句解析にとって重要な意味を持つ。
  ' " # \

- 以下はPythonでは使われておらず、文字列リテラルやコメントの外部にある場合、無条件でエラーとなる。
  $ ? `

##### NEWLINE
##### INDENT
##### DEDENT
#### Identifiers and keywords
##### Keywords
- The following identifiers are used as reserved words(keywords):
  - False None True and as assert break class continue def del elif else except
    finally for from global if import in is lambda nonlocal not or pass raise
    return try while with
##### Reserved classes of identifiers
###### _*
- Not imported by "from module import *".
###### __*__
- System-defined names.
###### __*
- Class-private names.
#### Literals
##### String and Bytes literals
###### Def
- stringliteral ::= [stringprefix](shortstring|longstring)
- stringprefix ::= "r"|"u"|"R"|"U"|"f"|"F"|"fr"|"Fr"|"fR"|"FR"|"rf"|"rF"|"Rf"|"RF
- shortstring ::= "'"shortstringitem*"'"|'"'shortstringitem*'"'
- longstring ::= "'''"longstringitem*"'''"|'"""'longstringitem*'"""'
####### Prefix
######## b/B
- Bytes literals always prefixed with 'b' or 'B'
######## f/F : formatted string literal
- formatted string literal
  
######## r/R : raw strings
- raw strings, and treating backslashes as literal characters.
  
###### Escape Sequences
- 
  |-----------------+------------------------------------------------|
  | Escape Sequence | Meaning                                        |
  |-----------------+------------------------------------------------|
  | \newline        | Backslash and newline ignored                  |
  | \\              | Backslash (\)                                  |
  | \'              | Single quote (')                               |
  | \"              | Double quote (")                               |
  | \a              | ASCII Bell (BEL)                               |
  | \b              |                                                |
  | \f              |                                                |
  | \n              | ASCII Linefeed (LF)                            |
  | \r              | ASCII Carriage Return (CR)                     |
  | \t              | ASCII Horizontal Tab (TAB)                     |
  | \v              | ASCII Vertical Tab (VT)                        |
  | \ooo            | Character with octal value ooo                 |
  | \xhh            | Character with hex value hh                    |
  | \N{name}        | Character named "name" in the Unicode database |
  | \uxxxx          | Character with 16-bit hex value xxxx           |
  | \Uxxxxxxxx      | Character with 32-bit hex value xxxxxxxx       |
  |-----------------+------------------------------------------------|

#### Operators
#### delimiters
### Data model
#### Object, Value, Type
#### The standard type hierarchy
##### None
- 単一の値のみを持つ。この値を持つオブジェクトはただ一つしか存在しない。
  組み込み名"None"でアクセスされる。
##### NotImplemented
- 単一の値のみを持つ。この値を持つオブジェクトはただ一つしか存在しない。
  組み込み名"NotImplemented"でアクセスされる。
##### Ellipsis
- 単一の値のみを持つ。この値を持つオブジェクトはただ一つしか存在しない。
  リテラル"..."または組み込み名"Ellipsis"でアクセスされる。
##### numbers.Number
###### numbers.Integral
####### Integers (int)
####### Booleans (bool)
###### numbers.Real (float)
###### numbers.Complex (complex)
##### Sequence
- 有限の順序集合(ordered set)を表現する。
  要素は非負の整数でインデクス化されている。
###### Immutable sequence
####### String
####### Tuple
####### Byets
###### Mutable sequence
####### Lists
####### Byte Arrays
##### Set types
- 順序のない、ユニークで不変なオブジェクトの有限集合を表見する。
###### Sets
- 可変な集合型。set()コンストラクタで作成され、後からadd()などのいくつかのメソッドで変更できる。
###### Frozen sets
- 不燃あ集合型。frozenset()コンストラクタによって生成される。
##### Mapping
- 任意のインデクス集合でインデクスされた、オブジェクトからなる有限の集合を表す。
###### Dictionary
- ほぼ任意のインデクスされたオブジェクトからなる有限の集合を表す。
##### Callable type
- 関数呼び出し操作を行うことができる型。
###### User-defined functions
####### Special attributes
######## __doc__
######## __name__
######## __qualname__
###### Instance methods
- クラス、クラスインスタンスと任意の呼び出し可能オブジェクト（通常はユーザ定義関数）を結びつける。
###### Generator functions
- yield文を使う関数もしくはメソッドをジェネレータ関数と呼ぶ。
  そのような関数が呼び出された時は常に、関数の本体を実行するのに使えるイテレータオブジェクトを返す。
###### Coroutine functions
- async defを使用して定義された関数やメソッドをコルーチン関数(coroutine function)と呼ぶ。
###### Built-in functions
- C関数へのラッパ。len()やmath.sin()など。
###### Built-in methods
- 実際には組み込み関数を別の形で隠蔽したもの。
###### Classes
###### Class instances
- Instances of arbitrary classes can be made callable by defining a __call__() method in their class.
  任意のクラスのインスタンスは、クラスで__call__()メソッドを定義することで呼び出し可能となる。
##### Module
##### Custom classes
##### Class instances
##### I/O objects (file objects)
- file objectは開かれたファイルを表す。
##### Internal types
###### Code objects
- バイトコンパイルされた実行可能なPythonコード（バイトコード・bytecode）を表現する。
  関数オブジェクトとの違いは、関数オブジェクトは関数のグローバル変数に対し明示的な参照を持っているのに対し、
  コードオブジェクトにはコンテキストがないということ。
###### Frame objects
- 実行フレーム(execution frame)を表す。実行フレームはトレースバックオブジェクト内に出現する。
  
###### Traceback objects
###### Slice objects
###### Static method objects
###### Class metod objects
#### Method name
#### Co-routine
### Execution model
#### Program Structure
#### Naming and binding
#### Exceptions
### Import System
#### importlib
#### Package
#### Search
#### Load
#### path based finder
### Expressions
#### Arithmetic conversion
#### Atom
##### Identifiers
##### Literals
##### Parenthesized forms
##### Displays for lists, sets and dicts
###### Listed explicitly
####### List displays
####### Set displays
####### Dictionary displays
###### Comprehension
- syntax
  - comprehension ::= expression comp_for
  - comp_for ::= "for" target_list "in" or_test [comp_iter]
  - comp_iter ::= comp_for | comp_if
  - comp_if ::= "if" expression_nocond [comp_iter]
- computed via a set of looping and filtering instructions
- ex
  - [ i for i in range(10) ]
  - a,b,c = [ False for i in range(3) ]

##### Generator expressions
##### Yield expressions
#### Primary
#### Awati expression
#### power operator
#### Unary arithmetic and bitwise operations
##### -
##### +
##### ~
- bitwise invert ビット単位反転
  xのビット単位反転は"-(x+1)"として定義されている。
#### Binary arithmetic operations
##### *
##### //
- floor division 切り捨て徐算
  
##### /
##### %
##### @
- 行列の遠山に対し使用される。Pythonの組み込み型はこの演算子を実装していない。
##### +
##### -
#### shifting operation
#### Binary bitwise operation
##### &
##### ^
##### |
#### Comparisons
##### <
##### >
##### ==
##### >=
##### <=
##### !=
##### is [not]
##### [not] in
#### boolean operaiton
#### Conditional Expressions 条件式
- 
  条件式、しばしば三項演算子、とも。もっとも優先度が低いPyhonの演算。
  "x if C else y"はCを評価し、trueの場合xが評価され値が返る。それ以外はyが評価され返る。

#### lambda
- syntax
  lambda_expr ::= "lambda" [parameter_list]: expression
#### list of expressions
#### evaluate order
#### primarity of operand
### Simple statement
- 単一の論理行内に納められる文。
#### expression statement 式文
#### assignment statement 代入文
- syntax
  - assignment_stmt ::= (target_list "=")+ (expression_list | yield_expression)
  - target_list ::= target ("," target)* [","]

- 
  代入文は式のリストを評価し、得られた単一の結果オブジェクトをターゲット(target)のリストに対し左から右へと代入していく。
  式のリストは単一の式でもカンマで区切られた式リストでもよい。後者はタプルとなる。
  
  代入はターゲット(リスト)の形式に従って形式に従って再帰的に行われる。
  
##### Augumented assignment statement
- 累積代入文は、二項演算と代入分を組み合わせて一つの文にしたもの。
- syntax
  - augmented_assignment_stmt ::= augtarget augop (expression_list | yield_expression)
  - augtarget
  - augop ::= "+=" | "-=" | "*=" | "@=" | "/=" | "//=" | "%=" | "**=" | ">>=" | "<<=" | "&=" | "^=" | "!="
#### assert
- syntax
  assert_stmt ::= "assert" expression ["," expression]
#### pass
- syntax
  pass_stmt ::= "pass"
  ヌル操作。構文的には文が必要だが、コードとしては何も実行したくない場合のプレースホルダとして有用。
#### del
- syntax
  del_stmt ::= "del" target_list
- 
  オブジェクトの削除。各々のターゲットを左から右へ順に再起的に削除する。
  
#### return
- syntax
  return_stmt ::= "return" [expression_list]
#### yield
- syntax
  yield_stmt ::= yield_expression
- 
  意味はyield expressionと同じ。yield文を用いるとyield式文で必要な確固を省略できる。
  
#### raise
#### break
#### continue
#### import
- 
  import          ::= "import" module ["as" name] ( "," module ["as" name] )*
                      | "from" relative_module "import" identifier ["as" name] ( "," identifier ["as" name] )*
                      | "from" relative_module "import" "(" identifier ["as" name] ( "," identifier ["as" name] )* ["," ")"
                      | "from" module "import" "*"
  module          ::= (identifier ".")* identifier
  relative_module ::= "."* module
  name            ::= identifier

- 基本の実行ステップ
  1. モジュールを見つけ出し、必要であればロードし初期化する
  2. import文が現れるスコープのローカル名前空間で名前を定義する。

- from形式での手順
  1. from節で指定されたモジュールを見つけ出し、必要であればロードし初期化する
  2. import節で指定されたそれぞれの識別子に対し以下の処理を行う
     1. インポートされたモジュールがその識別子名の属性を持っているかを確認する
     2. 持っていなかった場合はその識別子名でサブモジュールのインポートを試み、再度その属性がインポートされたモジュールにあるか確認する
     3. 属性が見つからない場合はImportErrorを送出
     4. 属性が見つかった場合は、as節があるならそこの名前、そうでないなら属性名を使って、その値への参照がローカル名前空間に保存される

#### global
#### nonlocal
### Compound statement
- 複合文には他の文（のグループ）が入る。
  中に入っている他の文の実行の制御に何らかのやり方で影響を及ぼす。
#### if
- syntax
  if_stmt ::= "if" expression ":" suite
              ( "elif" expression ":" suite )*
              ["else" ":" suite]

#### while
- syntax
  while_stmt ::= "while" expression ":" suite
                 ["else" ":" suite]

- 
  式の値が真である間、実行を繰り返す。
  式が偽であれば、else節がある場合にはそれを実行し、ループを終了する。

#### for
- syntax
  for_stmt ::= "for" target_list "in" expression_list ":" suite
               ["else" ":" suite]

- 
  シーケンス（文字列、タプルまたはリスト）や、その他の反復可能なオブジェクト(iterable object)内の要素に渡って反復処理を行うために使われる。

#### try
- 
  try_stmt  ::= try1_stmt | try2_stmt
  try1_stmt ::= "try" ":" suite
                ("except" [expression ["as" identifier]] ":" suite) +
                ["else" ":" suite]
                ["finally" ":" suite]
  try2_stmt ::= "try" ":" suite
                "finally" ":" suite
#### with
#### function defenition
- 
  funcdef        ::=
  decorators     ::=
  decorator      ::=
  dotted_name    ::=
  parameter_list ::= 
  parameter      ::=
  defparameter   ::=
  funcname       ::=

- 
  ユーザ定義関数オブジェクトを定義する、実行可能な分。
  関数定義を実行すると、現在のローカルな名前空間で関数名を関数オブジェクトに束縛する。
  
#### class defenition
- 
  classdef    ::=
  inheritance ::=
  classname   ::=

- 
  クラスオブジェクトを定義する、実行可能な文。
  
#### co-routine
##### co-routine function definition
##### async for
##### async with
### Top Level
## Library
### Standard Library
#### Built-in
##### Function
###### abs()
###### all()
###### any()
###### chr(i)
- Unicodeコードポイントが整数iである文字を表す文字列を返す。ord()の逆。
###### dir()
- dir([object])
  引数がない場合、現在のローカルスコープにある名前のリストを返す。
  引数がある場合、そのオブジェクトの有効な属性のリストを返そうと試みる。
  
###### enumerate()
- enumerate(iterable, start=0)
  erumerateオブジェクトを返す。
  iterableは、シーケンスかiteratorか、あるいはイテレーションをサポートするその他のオブジェクトでなければならない。
  
###### help()
- help([obeject])
  組み込みヘルプシステムを起動する。
  引数が与えられていない場合、インタプリタコンソール上で起動する。
  
###### id()
- id(object)
  return the "identity" of an object.
- CPython implementation : This is the address of the object in memory.
###### input()
- input([prompt])
  引数promptが存在すれば、それが末尾の改行を除いて標準出力に書き出される。
  次に、関数から1行を読み込み、文字列に変換して返す。
- 例）
  
###### list()
- class list([iterable])
  実際には関数でなくミュータブルなシーケンス型。
###### map()
- map(function, iterable, ...)
  functionを、結果を返しならがiterableのすべての要素に適用するイテレータを返す。

###### max()
- 
  max(iterable, *[, key, default])
  max(arg1, arg2, *args[, key])
- 
  iterableの中で最大の要素、または2つ以上の引数の中で最大のものを返す。

###### print()
- print(*objects, sep='', end='\n', file=sys.stdout)
  object(複数でも可)をsepで区切りながらストリームfileに表示し、最後にendを表示する。
  sep, end, fileが与えられる場合、キーワード変数として与えられる必要がある。
###### open()
- open(name[, mode[, buffering]]
  ファイルを開いて、fileオブジェクトを返す。開けない場合IOErrorが送出される。
  nameは開きたい名前で、modeはファイルをどのようにして開くかを指定する。

  - mode
    - r
    - w
    - a : 追加書き込み
    - b : バイナリファイルを開く場合
    - r+
    - w+
    - a+
###### ord(c)
- 1文字のUnicode文字を表す文字列に対し、その文字のUnicodeコードポイントを表す整数を返す。chr()の逆。
###### range()
- range(stop)
- range(start, stop[, step])
  実際には関数でなくイミュータブルなシーケンス型。
###### round()
- round(number[, ndigits])
  numberを小数点以下ndigits桁に丸めた浮動小数点数の値を返す。
  ndigitsが省略された場合、入力に最近節の整数を返す。
  偶数を選ぶ方に丸められる。（例：0.5と-0.5は0, 1.5は2に丸められる）
###### type()
- class type(object)
  - With one argument, return the type of an object.
    The return value is a type object and generally the same object as returned by object.__class__.
  - 引数が1つだけの場合、objectの型を返す。返り値は型オブジェクトで、一般にobjcet.__class__によって返されるのと同じオブジェクト。
- class type(name, bases, dict)
  
###### zip(*iterables)
- それぞれのイテラブルから集めたイテレータを作る。
  この関数はタプルのイテレータを返し、そのi番目のタプルは引数シーケンスまたはイテラブルそれぞれのi番目の要素を含む。
##### Non-essential Function
##### Constant
###### False
###### True
###### none
###### NotImplemented
###### Ellipsis
###### __debug__
###### Constants added by site module
####### quit
####### exit
####### copyright
####### license
####### credit
##### Type
###### Truth Value Testing
###### Boolean Operations
- and, or, not
####### and
- x and y
  xが偽ならx, そうでなければy
####### or
- x or y
  xが偽ならy, そうでなければx
####### not
- not x
  xが偽ならTrue、そうでなければFales
###### Comparisons
###### Numeric Types
- int, float, complex
####### Bitwise Operations on Integer
####### Aditional Methods on Integer
####### Additional Methods on Float
###### Iterator Types
###### Sequence Types
- basically: list, tuple, range
####### Sequence Operations
######## x in s
######## x not in s
######## s + t
######## s * n, n * s
######## s[i]
######## s[i:j]
######## s[i:j:k]
######## len(s)
######## min(s)
######## max(s)
######## s.index(x[, i[, j]])
- s中でxが最初に出現するインデックスを、i移行からjまでの範囲で返す。
######## s.count(x)
####### Type
######## Immutable
######## Mutable
####### Basic Sequences
######## List
######## Tuple
######## Range
####### Text Sequences
- str
######## Class
- 
  - class str(object='')
  - class str(object=b'', encoding='utf-8', erros='strict')
- 
  objectの文字列版を返す。objectが与えられなかった場合、空文字が返される。
  
######## Methods
######### str.capitalize()
######### str.casefold()
######### str.center(width[, fillchar])
######### str.count(sub[, start[, end]])
######### str.find(sub[, start[, end]])
- 文字列のスライスs[start:end]に部分文字列subが含まれる場合、その最小のインデックスを返す。
  subが見つからなかった場合-1を返す。
######### str.isalnum()
- 文字列中のすべての文字が英数字で、かつ1文字以上あるなら真を、そうでなければ偽を返す。
######### str.isdecimal()
######### str.isdigit()
- 文字列中のすべての文字が数字で、かつ1文字以上あるなら真を、そうでなければ偽を返す。
  数字は、十進数字と、互換上付き数字のような特殊操作を必要とする数字を含む。
######### str.isidentifier()
######### str.islower()
- 文字列中の大小文字の区別のある文字すべてが小文字で、かつ大小文字の区別のある文字が1文字以上あるなら真を、そうでなければ偽を返す。
######### str.isnumeric()
- 文字列中のすべての文字が数を表す文字で、かつ1文字以上あるなら真を、そうでなければ偽を返す。
  数を表す文字は、数字とUnicodeの数値プロパティを持つすべての文字を含む。
######### str.isprintable()
######### str.isspace()
######### str.istitle()
######### str.isupper()
- 文字列中の大小文字の区別のある文字すべてが大文字で、かつ大小文字の区別のある文字が1文字以上あるなら真を、そうでなければ偽を返す。
######### str.join(iterable)
- イテラブルiterable中の文字列を結合した文字列を返す。
  セパレータは、このメソッドを提供する文字列。
######### str.lower()
######### str.lstrip([chars])
- 文字列の先頭の文字を除去したコピーを返す。charsは除去される文字の集合を指定する文字列。
  charsが省略されるかNoneの場合、空白文字が除去される。
######### str.replace(old, new[, count])
- 文字列をコピーし、現れる部分文字列old全てをnewに置換して返す。
  countが指定されている場合、先頭からcount個のoldだけを置換する。
  
######### str.rfind(sub[, start[, end]])
######### str.rindex(sub[, start[, end]])
######### str.rsplit(sep=None, maxsplit=-1)
######### str.rstrip([chars])
######### str.split(sep=None, maxsplit=-1)
- 
  文字列を、sepをデリミタ文字列として区切った単語のリストを返す。
  maxsplitが与えられていれば、最大でmaxsplit回分割される。
######### str.strip([chars])
- 
  文字列の先頭および末尾部分を除去したコピーを返す。charsは除去される文字の集合を指定する文字列。
  charsが省略されるかNoneの場合、空白文字が除去される。
####### Binary Sequences
- bytes, bytearray, memoryview
######## bytes
######## bytearray
###### Set Types
- set, frozenset
###### Mapping Types
- dict
####### dict
######## Constructors
######### class dict(**kwarg)
######### class dict(mapping, **kwarg)
######### class dict(iterable, **kwarg)
######## 
###### Context Manager Types
###### Other Built-in Types
####### Modules
####### Classes, Class Instances
####### Functions
####### Methods
####### Code Objects
####### Type Objects
####### The Null Object
####### The Ellipsis Object
####### Boolean Values
####### Internal Objects
###### Special Attributes
####### ojbect.__dict__
- オブジェクトの（書き込み可能な）属性を保存するために使われる辞書またはその他のマッピングオブジェクト。
####### instance.__class__
- クラスインスタンスが属しているクラス。
####### class.__bases__
- クラスオブジェクトの基底クラスのタプル
####### class.__name__
- クラスまたは型の名前。
####### class.__qualname__
- クラスまたほ型のqualified name。
####### class.__mro__
- メソッドの解決寺に基底クラスを探索するときに考慮されるクラスのタプル
####### class.mro()
- クラスのインスタンス化時に呼ばれ、結果は__mro__に格納される。
  メタクラスによって、そのインスタンスのメソッド解決の順序を上書きされる可能性がある。
####### class.__subclasses__()
- それぞれのクラスは、それ自身の直接のサブクラスへの弱参照を保持する。
  それらの山椒のうち、生存しているもののリストを返す。
##### Exception
###### Base classes
####### exception BaseException
####### exception Exception
####### exception ArithmetricError
####### exception BufferError
####### exception LookupError
###### Concrete exceptions
####### Exceptions
######## exception AssertionError
######## exception ImportError
######## exception MemoryError
######## exception NameError
####### OS exceptions
######## exception FileExistsError
######## exception FileNotFoundError
- 要求されたファイルやディレクトリが存在しない場合に送出される。
  "errno ENOENT"に対応。
###### Warnings
#### Text Processing Services / 文字列処理
##### string
###### Const
####### string.ascii_letters
- ascii_lowercaseとascii_uppercaseを合わせたもの。
####### string.ascii_lowercase
- 小文字'abcdefghijklmnopqrstuvwxyz'。
####### string.ascii_uppercase
- 大文字'ABCDEFGHIJKLMNOPQRSTUVWXYZ'。
####### string.digits
####### string.hexdigits
##### re
- 正規表現操作
  正規表現マッチング操作を提供
###### Syntax
###### Module Contents
####### re.compile()
- re.compile(pattern, flag=0)
  正規表現パターンを正規表現オブジェクトにコンパイルする。

####### re.search()
- re.search(pattern, string, flags=0)
  string全体を走査して、正規表現patternがマッチを発生する最初の位置を探して、対応するMatchObjectインスタンスを返す。
  もし文字列内にマッチする位置がない場合Nneを返す。
####### re.match()
- re.mathch(pattern, string, flags=0)
  stringの先頭で0個以上の文字が正規表現patternとマッチすれば、MatchObjectインスタンスを返す。
###### re.RegexObject
- class re.RegexObject
####### Methods
######## search()
###### re.MatchObject
####### Methods
######## expand()
- expand(template0

######## start(), end()
- start([group]), end([group])
  groupとマッチした部分文字列の先頭と末尾のインデックスを返す。
  マッチしたサブ文字列は"m.string[m.start(g):m.end(g)]"で
##### difflib
- 差分の計算を助ける

###### class difflib.SequenceMatcher

###### class difflib.Differ

####### compare
###### class difflib.HtmlDiff
#### Binary Data Services
#### Data Types / データ型
##### datetime
- 基本的な日付型および時間型
  日付や時間データを簡単な方法と複雑な方法の両方で操作するためのクラスを提供している。
  
###### Datatype
####### class datetime.date
####### class datetime.time
####### class datetie.datetime
- dateオブジェクトおよびtimeオブジェクトのすべての情報が入っている単一のオブジェクト。
######## Class Method
######### classmethod datemite.today()
- 現在のローカルなdateteimeをtzinfoがNoneであるものとして返す。
######### classmethod datemite.now(tz=None)
- 現在のローカルな日付および時刻を返す。

######## Properties
######### datetime.min
######### datemite.max
######### datetime.year
######### datetime.month
######### datetime.day
######### datetime.hour
######### datetime.minute
######### datetime.second
######## Instance Method
######### datetime.date()
######### datetime.time()
######### datetime.tmietz()
######### datetime.strftime(format)
- 明示的な書式化文字列で制御された、日付および時刻を表現する文字列を返す。
- ex)
  datetime.now().strftime('%Y%m%d%H%M%S')
####### class datetime.timedelta
- 経過時間、すなわち二つの日付や時刻間の差を表す
##### collections
- 汎用の組み込みコンテナdict, list, setおよびtupleに代わる、特殊なコンテナデータ型を実装している。

###### Classes
####### class collections.defaultdict([default_factory[, ...]])
####### class collections.Counter([iterable-or-mapping])
- 
  ハッシュ可能なオブジェクトをカウントするdictのサブクラス。
  要素を辞書のキーとして保存し、そのカウントを辞書の値として保存する。
######## Methods
######### elements()
- それぞれの要素を、そのカウント分の回数だけ繰り返すイテレータを返す。
######### most_common([n])
- 最も多いn要素を、カウントが多いものから少ないものまで順に並べたリストを返す。
######### subtract([iterable-or-mapping])
#### Numeric and Mathematical Moduels / 数値と数学モジュール
#### Functional Programming Modules
#### File and Directory Access / ファイルとディレクトリへのアクセス
##### glob
- Unix形式のパス名のパターン展開
###### glob
- glob.glob(pathname)
  pathnameにマッチする空の可能性のあるパス名のリストを返す。
###### iglob
- glob.iglob(pahtname)

#### Data Persistence / データの永続化
#### Data Compression ad Arhciving / データ圧縮とアーカイブ
#### File Formats / ファイルフォーマット
#### Cryptographic Services / 暗号関連のサービス
#### Generic Operating System Services / 汎用オペレーティングシステムサービス
##### os
###### Process Parameters
###### File Object Creation
###### File Descriptor Operations
###### Files and Directories
####### os.chdir()
- os.chdir(path)
  現在の作業ディレクトリをpathに設定する。
  環境 : Unix, Windows
####### os.getcwd()
- 
  現在の作業ディレクトリを表す文字列を返す。
  環境 : Unix, Windows
####### os.chmod()
- os.chmod(path, mode)
  pathのモードを数値modeに変更する。
####### os.chown()
- os.chown(path, uid, gid)
  pathの所有者(owner)idとグループidを、数値uidおよびgidに変更する。
####### os.listdir()
- os.listdir(path)
  pathで指定されたディレクトリ内のエントリ名が入ったリストを返す。
  利用できる環境 : Unix, Windows
####### os.mkdir()
- os.mkdir(path[, mode])
  数値で指定されたモードmodeをもつディレクトリpathを作成する。
####### os.mkdirs()
- os.makedirs(path[, mode])
  再帰的なディレクトリ作成関数。中間の全てのディレクトリを作成する。

####### os.remove()
- os.remove(path)
  pathを削除する。
####### os.removedirs()
- os.removedirs(path)
  再帰的なディレクトリ削除関数。
####### os.rename()
- os.rename(src, dst)
  ファイルまたはディレクトリsrcをdstに名前変更する。
####### os.renames()
- os.renames(old, new)
  再帰的にディレクトリやファイル名を変更する関数。
####### os.rmdir()
- os.rmdir(path)
  ディレクトリpathを削除する。
####### os.walk()
- os.walk(top[, topdown=True[, onerror=None[, followlinks=False]]]
  ディレクトリツリー以下のファイル名を、ツリーをトップダウンもしくはボトムアップに走査することで生成する。
  topを根に持つディレクトリツリーに含まれる、各ディレクトリ(top含む)から、タプル(dirpath, dirnames, filenames)を生成する。
###### Process Management
###### Miscellaneaus System Information
###### Miscellaneaus Function
##### io
##### time
- 時刻データへのアクセスと変換
###### Methods
####### time.sleep
- time.sleep(secs)
  与えられた秒数の間、呼び出したスレッドの実行を停止する。
  より精度の高い実行停止時間を指定するために、引数は浮動小数点にしてもよい。
##### errno
- 標準のerrnoシステムシンボル
###### errno.errorcode
###### errno.EPERM
###### errno.EINTR
###### errno.EIO
#### Concurrent Execution / 並列実行
##### subprocess
- サブプロセス管理
###### run()
#### Interprocess Communication and Network / プロセス間通信とネットワーク
#### Internet Data Handling / インターネット上のデータの操作
##### email
##### json
###### Methods
####### json.dump(obj, fp, ...)
- 変換表を使い、objをJSON形式のfp(file-like object)へのストリームとして直列化する。
  常にbyetsオブジェクトでなくstrオブジェクトを生成する。
####### json.dumps(obj, ...)
- 変換表を用い、objをJSON形式のstrオブジェクトに直列化する。
####### json.load(fp, ...)
- 変換表を用い、fpをPythonオブジェクトへ脱直列化する。
####### json.loads(s, ...)
- 変換表を用い、s(JSONドキュメントを含んでいるstrインスタンス)をPyhtonオブジェクトへ脱直列化する。
###### Classes
####### class json.JSONDecoder(...)
- 単純なJSONデコーダ。
- デフォルトでは、以下の変化を行う。
  |---------------+--------|
  | JSON          | Python |
  |---------------+--------|
  | object        | dict   |
  | array         | list   |
  | string        | str    |
  | number (int)  | int    |
  | number (real) | float  |
  | true          | True   |
  | false         | False  |
  | null          | None   |
  |---------------+--------|
  
######## Methods
######### decode(s)
######### raw_decode(s)
####### class json.JSONEncoder(...)
###### Exceptions
####### exception json.JSONDecodeError(msg, doc, pos, end=None)
#### Structured Markup Processing Tools / 構造化マークアップツール
#### Internet Protocols and Support / インターネットプロトコルとサポート
##### urllib
- URLを扱うモジュール群
##### urllib.request
- URLを開くための拡張可能なライブラリ
  
###### 関数
####### urllib.request.urlopen(url,data=None, ...)
####### urllib.request.install_opener(opener)
####### urllib.request.build_opener([handler, ...[)
##### urllib.response
##### urllib.parse
##### urllib.error
- 
  urllib.requestによってなげられる例外を定義している。基底クラスはURLError。


###### exception urllib.error.URLError
- 
  ハンドらが何らかの問題に遭遇した場合、この例外（もしくは派生した例外）を創出する。
  OSErrorのサブクラス。

- reason
  エラーの理由。メッセージ文字列あるいは他の例外インスタンス。

###### exception urllib.error.HTTPError
- 
  例外であると同時に、例外ではないfile-likeな戻り値を返す関数(urlopen()の戻り値と同じ)。
  URLErrorのサブクラス。
- code
  HTTPステータスコード。
- reason
  通常エラーの説明文
- headers
  HTTPErrorの原因となったHTTPリクエストのHTTPレスポンスヘッダ。

#### Multimedia Services / マルチメディアサービス
#### Internationalization / 国際化
#### Program Frameworks / プログラムのフレームワーク
#### Graphical User Interface with Tk / Tkを用いたグラフィカルユーザインターフェース
#### Development Tools / 開発ツール
##### typing
##### pydoc
##### doctest
- Test interactive Python examples
##### unittest
- Unit testing framework originally inspired by JUnit
###### Commad-line options
####### -b, --buffer
####### -c, --catch
####### -f, --failfast
####### --locals
###### Classes and functions
####### Classes
######## class unittest.TestCase(methodName='runTest')
######### setUp()
######### tearDown()
######### setUpClass()
######### tearDownClass()
######### run(result=None)
######### skipTest(reason)
######### debug()
######### assertEqual(first,second,msg=None)
######### assertNotEqual(first,second,msg=None)
######### assertTrue(expr,msg=None)
######### assertFalse(expr,msg=None)
######### assertIs(first,second,msg=None)
######### assertIsNot(first,second,msg=None)
######### assertIsNone(expr,msg=None)
######### assertIsNotNone(expr,msg=None)
######### assertIn(first,second,msg=None)
######### assertNotIn(first,second,msg=None)
######### assertIsInstance(first,second,msg=None)
######### assertNotIsInstance(first,second,msg=None)
##### unittest.mock
##### 2to3
- Automated Python 2 to 3 code translation
##### test
##### test.suppot
#### Debugging and Profiling / デバッグとプロファイル
##### pdb
- Pythonデバッガ
  対話型ソースコードデバッガーを定義する。
###### Debugger command
####### h(elp)
- h(elp) [command]
  引数を指定しない場合、利用できるコマンドの一覧が表示される。
  引数としてcommandが与えられた場合、そのコマンドのヘルプが表示される。
####### w(here)
- 
  スタックの底にあるもっとも新しいフレームとともにスタックトレースをプリントする。
####### d(own)
- d(own) [count]
  スタックフレーム内で現在のフレームをcountレベル（デフォルトは1）新しいフレーム方向に移動する。
####### u(p)
- u(p) [count]
  スタックフレーム内で現在のフレームをcountレベル（デフォルトは1）新しいフレーム方向に移動する。

####### b(reak)
####### tbreak
####### cl(ear)
####### disable
####### enable
####### ignore
####### condition
####### commands
####### s(tep)
- 
  現在の行を実行し、最初に実行可能なものが現れたときに（呼び出された関数の中化、現在の関数の次の行で）停止する。
####### n(ext)
- 
  現在の関数の次の行に達するか、あるいは関数が返るまで実行を継続する。
  stepとの違いは、stepが呼び出さ荒れ田関数の内部で停止するのに対し、nextは関数を実行後現在の関数内の次の行で停止する。
####### unt(il)
####### r(eturn)
- 
  現在の関数が返るまで実行を継続する。
####### c(ont(inue))
- 
  ブレークポイントに出会うまで、実行を継続する。
####### j(ump)
####### l(ist)
####### ll
####### a(rgs)
####### p
- p expression
  現在のコンテキストにおいて、expressionを評価し、その値をプリントする。
####### pp
- pp expressoion
  pコマンドに似ているが、式の値以外は、pprintモジュールを使用して"pretty-print"される。
####### whatis
- whatis expression
  式の型を表示する。
####### source
####### display
- display [expression]
  式の値が変更されていれば表示する。
  式を指定しない場合、現在のフレームのすべての式を表示する。
####### undisplay
####### interact
####### alias
####### unalias
####### !
####### run
- run [args ...]
  デバッグ中のプログラムを再実行する。
####### restart
- restart [args ...]
  デバッグ中のプログラムを再実行する。runの別名。
  
####### q(uit)
- 
  デバッガを終了する。

#### Software Packaging and Distribution / ソフトウェア・パッケージと配布
##### distutils
##### ensurepip
##### venv
- Creation of virutal environment
- New in version 3.3
###### Usage
- python3 -m venv /path/to/nowenv
- source bin/activate
##### zipapp
#### Python Runtime Services / Pythonランタイムサービス
##### sys
- システムパラメータと関数
###### sys.argv
- 
  Pythonスクリプトに渡されたコマンドライン引数のリスト。
  argv[0]はスクリプトの名前となるが、フルパスかどうかはOSによる。

###### sys.exit([arg])
- Pythonを終了する。exit()はSystemExitを送出するので、捕捉可能。
###### sys.stdin, sys.stdout sys.stderr
- 
  インタープリタの標準入力・標準出力・標準エラー出力に対応するファイルオブジェクト。
  stdinはスクリプトの読み込みを除く全ての衆力処理で使用され、input()やraw_input()もstdinから読み込む。

###### sys__stdin__, sys.__stdout__, sys.__stderr__
- 
  それぞれ起動時のstdin, stdout, stderrの値を保持する。終了処理時に利用される。

###### sys.version
- 
  インタプリタのバージョン番号の他、ビルド番号や使用コンパイラなどの情報を示す文字列。
  この文字列はPython対話型インタプリタが起動した時に表示される。
  バージョン情報はここから抜きださずに、version_infoおよびplatformが提供する関数を使う。
###### sys.version_info
- 
  バージョン情報を表す5個のタプル : major, minor, micro, releaselevel, serialが表示される。
  
#### Custom Pyhton Interpreters / カスタムPythonインタプリタ
#### 制限実行
#### Importing Modules / モジュールのインポート
#### Python Language Services / Python言語サービス
#### Pythonコンパイラパッケージ
#### Miscellaneous Services / 各種サービス
#### MS Windows Specific Sercices / MSWin固有
#### Unix Specific Services / Usix固有
#### MacOSX固有
### Other Libraries
#### Beautiful Soup
#### NumPy
- [[http://www.numpy.org/][NumPy]]
#### Matplotlib
#### SciPy
#### scikit-learn
#### Paramiko
- Python implementation of the SSHv2 protocol
##### Link
- http://www.paramiko.org/
- http://docs.paramiko.org/en/2.4/
#### Flask
#### typing
##### Memo
###### Protocolのimportでエラー
- do "pip install typing_extentions"
  Depending upon OS and Python version Protocol class might be within typing module or in typing_extensions.
- [[https://stackoverflow.com/questions/54274630/can-not-import-protocol-from-typing][can not import Protocol from typing - stackoverflow]]
## Python 2.x
- [[file:Python_2_Lang.org][Python_2_Lang.org]]
## PEP
- Python Enhancement Proposals
### About
#### PEP 0 : Index of Python Enhancement Proposals (PEPs)
- https://www.python.org/dev/peps/
- Key
  - S : Standards Track REP
  - I : Informational REP
  - P : Process REP
### PEPs
#### PEP 8 : Style Guide for Python Code
#### PEP 263 : Defining Python Source Code Encoding
- https://www.python.org/dev/peps/pep-0263/
## Style
### PEP 8
- インデントは空白4つを使い、タブは使わない。
- ソースコードの幅が79文字を超えないように行を折り返すこと
- 関数やクラスや関数内の大きめのコードブロックの区切りに空行を使う
- 可能なら、コメントは行に独立で書く
- docstringを使う
- 演算子の前後とコンマの後には空白を入れ、括弧内のすぐ内側には空白を入れないこと
- クラスや関数には一貫性のある名前を付ける。
  CamelCaseをクラス名に使い、lower_case_with_underscoresを関数名やメソッドに使う。
- 風変わりなエンコーディングは使わない
#### Link
- https://www.python.org/dev/peps/pep-0008/

## Tools
### anaconda
#### Memo
- 普通にanacondaをインストールすると、OSで設定しているpythonもすべて奪ってしまうとのこと。
  Winなら問題ないかもしれないが、基本pyenvを使って入れるのが良さそう。
- [[https://www.continuum.io/][ANACONDA]]
- [[http://qiita.com/y__sama/items/5b62d31cb7e6ed50f02c][データサイエンティストを目指す人のpython環境構築 2016 - Qiita]]
### pip
- Pythonにおけるパッケージ管理システム。
  Python 3.4以降は本体に同梱。
#### command
##### help
- 
  ex) pip help
      pip help install

##### search
- 
  Python Package Index(pypi)にあるパッケージをsearchコマンドで検索可能。

##### install
- インストールを行う。

##### freeze
- 
  書き出しておいたパッケージリストを全部インストールする。

##### show
- 
  パッケージの詳細を確認できる。

#### etc
##### install
- 
  githubのget-pip.pyをパイプでpython呼び出しして実行した。
  ただし、pythonをzlib付でビルドしていないとだめらしく、
  configure時に"--with-zlib-dir=/usr/local/lib"とか付けた。
  [[https://github.com/pypa/pip/issues/1919][zipimport.ZipImportError#1919]]

##### Link
- [[https://pip.pypa.io/en/latest/index.html][pip]]
- [[http://tdoc.info/blog/2014/01/15/pip.html][pipの使い方(2014/1バージョン) - そこはかとなく書くよん。]]
#### Memo
##### pipのupgrade
- pip install --upgrade pip
### pyenv
#### commands
- [[https://github.com/yyuu/pyenv/blob/master/COMMANDS.md][Command Reference - pyenv - git hub]]
##### commands
- Lists all available pyenv commands
##### local
##### global
##### shell
##### install
- Usage :
  pyenv install [-f] [-kvp]  <version>
  pyenv install [-f] [-kvp]  <definition-file>
  pyenv install -l|--list

- -l, --list
- -f, --force
- -s, --skip-existing
- -k, --keep
- -v, --verbose
- -p, --patch
- -g, --debug

##### uninstall
##### rehash
##### version
##### versions
##### which
##### whence
#### Environmental variables
##### PYENV_VERSION
##### PYENV_ROOT
- default : ~/.pyenv
  Defines the directory under which Python versions and shims reside.
##### PYENV_DEBUG
##### PYENV_HOOK_PATH
##### PYENV_DIR
#### Link
- [[https://github.com/yyuu/pyenv][yyuu/pyenv - github]]
### virtualenv
- デファクトスタンダードらしい。
  →もはや過去。venvとしてpython3.3で取り込まれ(pyvenv)、
    その後python 3.6でpython -m venvが推奨に。
- インストール
  pip install virtualenv
- 環境作成
  virtualenv env
- Activate
  (Win)Scripts/activate
  (Posix). bin/activate
- Deactivate
  deactivate
#### Command
##### deactivate
- 無効化
#### Link
- https://qiita.com/th1209/items/84f21a4499548b34ec91
## Glossary
### Mutable, Immutable
- Mutable
  値を変更できるオブジェクト。
  dictやlistなど。
- Immutable
  生成後に値を変更できないオブジェクト。
  数値型、文字列型、タプル型のインスタンスなど
### Container
- 他のオブジェクトに対する参照をもつオブジェクト。
  Tuple, List, Dictionaryなど。
## Link
- [[http://docs.python.jp/3/index.html][Python 3 ドキュメント]]
- [[https://docs.python.org/3/index.html][Python 3 documentation]]
- [[http://d.hatena.ne.jp/dplusplus/20100126/p1][Python基礎文法最速マスター - LazyLife@Diary]]

- [[https://docs.python.jp/3/tutorial/index.html][Pythonチュートリアル]]
- [[https://docs.python.org/3/tutorial/][The Python Tutorial]]

- [[https://www.obeythetestinggoat.com/pages/book.html][Obey the Testing Goat!]]

## Reverse Lookup
### 覚書(old)
- time.sleep
  time.sleep(3)で3秒停止。

- string.rstrip()
  string.rstrip()で末尾の改行を削除

- string.find()
  string.find(target)で、string内のtargetの位置を返す。
  'abcde'.find('b')で1(int)が返る。

- shutil.copy
  copyはshutil(shutil.copy, shutil.copytree, shutil.copyfile等)、

- os.rename
  renameはos(os.rename)

- 終了：
  Ctrl-z(Unix系 Ctrl-d)
  quit()
### shellコマンド互換コマンド
- cd  : os.chdir(path)
- ls  : os.listdir(path), glob.glob(pattern)
- pwd : os.getcwd()
### ファイルの読み書き
- ファイルを開いて読む
  - ex
    for line in open('text.txt', 'r'):
        print line

- 改行コードを除く場合
  - ex
    print line[:-1]

- ファイルを丸ごと読む
  - ex
    allLine = open('test.txt').read()

- 多くのファイルを読む
  - ex
    for file in glob.glob('*.txt'):
        for line in open(file, 'r'):
            print line

### 外部プログラムの実行
- 
  subprocessの利用を推奨。
  - 例
    import subprocess
    subprocess.call('ls')

- 
  osやcommandsモジュールは推奨されていない。
  - 例
    os.system('ls')
    commands.getstatusoutput('ls')
  
### jsonを扱う
- jsonモジュールを利用する。(import json)
  
### 連番を作成する
- range()関数をつかう。
  rangne(5,10) -> 
### importでNo module named ...が出る場合
- 存在しない場合は、importする。pip3 import xxxx
- すでに存在してパスが通っていない場合は、以下のように対応すれば暫定的に対応可能。
  - pip3 show xxxx : モジュールの配置箇所を調べる
  - プログラム中で、パスを通す :
    import sys
    sys.path.append('showed path of module')
    import xxxx
- [[https://qiita.com/ymto/items/e00e95543aab2d4d45ee][pythonでimport時に、ModuleNotFoundError: No module namedが出た時の対処手順 - @ymto - Qiita]]
## Memo
### 前回表示結果
- 
  "_"に格納されている。
  - 例
    >>>price=100.50
    >>>price * tax
    12.5624
    >>>price + _
    113.9625 # 前回の値が足されている。

### private
- private
  "__abc"と変数やメソッドの前に"__"を付けるとprivateとなる。
### Tutorial
- https://docs.python.jp/3/tutorial/index.html
### 仮想環境
- Python3.6以降は"python3 -m venv evndir"を推奨。
  3.3からvirtualenv相当のvenvが追加され、"pyvenv"コマンドが推奨されたが、現在非推奨。
- [[https://qiita.com/shinespark/items/1d6ec0de89aa537da505][venvを使ったmacOSのPython開発環境2016]]

- "pip freeze > packages"でインストール済みパッケージリストを出力、
  "pip install -r packages"でインストール可能。
### if __name__ == "__main__"
- python program_name、で呼ばれた時にのみ実行されるようになる。
- https://blog.pyq.jp/entry/Python_kaiketsu_180207
