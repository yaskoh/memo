# Java Language Specification
## Java8
### Lexical Structure
#### Line Terminators
#### Input Elements and Tokens
##### Def
- Input:
  {InputElement} {Sub}
- InputElement:
  WhiteSpace
  Comment
  Token
- Token:
  Identifier
  Keyword
  Literal
  Separator
  Operator
- Sub:
  the ASCII SUB character, also known as "control-Z"

##### White Space
##### Comments
###### About
- There are two kinds of comments:
  - /* text /*
  - // text
###### Def
##### Token
###### Identifiers
###### Keywords
####### List
- abstract assert boolean break byte case catch char class const
  continue default do double else enum extends final finally float
  for if goto implements import instanceof int interface long native
  new package private protected public return short static strictfp super
  switch synchronized this throw throws transient try void volatile while

###### Literals
####### Integer Literals
####### Floating-Point Literals

####### Boolean Literals
####### Character Literals
####### String Literals
####### Escape Sequences for Character and String Literals
####### The Null Literals
######## Def
- NullLiteral:
  null
###### Separator
- 12 tokens
####### Def
- Separator:
  ( ) { } [ ] ; , . ... @ ::
###### Operator
- 38 tokens
####### Def
- Operator:
  =  >  <  !  ~  ?  :  ->
  == >= <= != && || ++ --
  +  -  *  /  &  |  ^  %  <<  >>  >>>
  += -= *= /= &= |= ^= %= <<= >>= >>>=
  
### Types, Values, and Variables
#### Primitive Types and Values
##### Integer Types
##### Floating-Point Types
##### The boolean Types
#### Reference Types and Values
##### Objects
#### Type Variables
##### Syntax
- TypeParameter:
  {TypeParameterModifier} Identifier [TypeBound]
- TypeParameterModifier:
  Annotation
- TypeBound:
  extends TypeVariable
  extends ClassOrInterfaceType {AdditionalBound}
- AdditionalBound:
  & InterfaceType
#### Parameterized Types
#### Variables
##### final
- A final variable may only be assigned to once.
  
### Conversions and Contexts
### Names
### Packages
#### Package Declarations
##### Named Packages
###### Def
- PackageDeclaration:
  {PackageModifier} package Identifier {. Identifier} ;
- PackageModifier:
  Annotation
#### Import Declarations
##### Def
- ImportDeclaration:
  SingleTypeImportDeclaration
  TypeImportOnDemandDeclaration
  SingleStaticImportDeclaration
  StaticImportOnDemandDeclaration
##### Single-Type-Import Declaration
###### Def
- SingleTypeImportDeclaration:
  import TypeName ;
###### Ex
- Single-Type-Import
  import java.util.Vector;
##### Type-Import-onDemand Declarations
- A type-import-on-demand declaration allows all accessible types of a named package or type to be imporetd as needed.
###### Def
- TypeIpmortOnDemandDeclaration:
  import PackageOrTypeName . * ;
###### Ex
- import java.util.*;
##### Single-Static-Import-Declarations
###### Def
- SingleStaticImportDeclaration:
  import static TypeName . Identifier ;
##### Static-Import-on-Demand Declarations
###### Def
- StaticImportOnDemandDeclaration:
  import static TypeName . * ;
### Classes
#### Class Declaration
##### Class Modifiers
###### Def
- ClassModifier:
  (one of)
  Annotation public protected private abstract static final strictfp
###### abstract Classes
###### final Classes
###### strictfp Classes
##### Generic Classes and Type Parameters
##### Inner Classes and Enclosing Instances
##### Superclasses and Subclasses
##### Superinterfaces
##### Class Body and Member Declarations
#### Class Members
#### Field Declarations
##### Field Modifiers
###### Def
- FieldModifier:
  (one of)
  Anntation public protected private
  static final transient volatile
###### static Fields
- if the field is 'static', there exists exactly one incarnation of the field, no matter how many instances of the class may eventually be created.
###### final Fields
- A field can be declared final. Both class and instance variables may be declared final.
###### transient Fields
- transient variables is to indicate that they are not part of the persistent state of an object
###### volatile Fields
#### Method Declarations
##### Def
- MethodDeclaration:
  {MethodModifier} MethodHeader
  MethodBody
- MethodHeader:
  Result MethodDeclarator [Throws]
  TypeParameters {Annotation} Result MethodDeclarator [Throws]
- MethodDeclarator:
  Identifier ( [FormalParameterList] ) [Dims]
##### Formal Parameters
##### Method Signature
##### Method Modifiers
###### Def
- MethodModifier:
  (one of)
  Annotation public protected private 
  abstract static final synchronized native strictfp
###### abstract Methods
- It introduces the method as member, providing its signature, result, and throws clause if any,
  but does not provide implementation.
  A method that is not abstract may be referred to as a "concrete" method.
###### static Methods
- it is called a "class method".  
###### final Methods
- prevent subclasses from overriding or hiding it.
###### native Methods
- It is implemented in platorm-dependent code, typically written in another programming language such as C.
###### strictfp Methods
- The effect of this modifier is to make all float or double expressions within the method body be explicitly FP-strict.
###### synchronized Methods
- This method acquires a monitor before it executes.
  For a class (static) method, the monitor associated with the Class object for the method's class is used.
  For an instance method, the monitor associated with this is used.
##### Generic Methods
##### Method Result
##### Method Throws
###### About
- A throws clause is used to declare any checked exception classes that the statements in a method or constructor body can throw.
###### Def
- Throws:
  throws ExceptionTypeList
- ExceptionTypeList:
  ExceptionType {, ExceptionType}
- ExceptionType:
  ClassType
  TypeVariable
  
##### Method body
##### Inheritance, Overriding, Hiding
#### Member Type Declarations
#### Instance Initializers
##### Def
#### Static Iniitalizers
- A static initializer declared in a class is executed when the class is initialized.
##### Def
- StaticInitialiver:
  static Block
#### Constructor Declarations
#### Enum Types
### Interfaces
#### Annotation Types
##### Predefined Annotation Types
###### @Target
###### @Retention
###### @Inherited
###### @Override
###### @SuppressWarnings
###### @Deprecated
###### @SafeVarargs
###### @Repeatable
###### @FunctionalInterface
- The annotation is used to indicate that an interface is meant to be a functional interface.
#### Annotations
##### Def
- Annotation:
  NormalAnnotation
  MarkerAnnotation
  SingleElementAnnotation
##### Normal Annotations
##### Marker Annotations
##### Single-Element Annotations
#### Functional Interfaces
- A functional interface is an interface that has just one abstract method, and thus represents a single function contract.
  
### Arrays
### Exceptions
#### Kinds
- An exception is represented by an instance of the class Throwable (a direct subclass of Object) or one of its subclasses.
- Exception : the superclass of all the exceptions from which ordinary programs may wish to recover.
- RuntimeException : a direct subclass of Exception.
  It's the superclass of all the exceptions which may be thrown for many reasons during expression evaluation, but from which recovery may still be possible.
- Error : the superclass of all the exceptions from which ordinary programs are not ordinarily expected to recover.
### Execution
#### Java Virtual Machine Startup
#### Loading of Classes and Interfaces
#### Linking of Clases and Interfaces
#### Initialization of Classes and Interfaces
- class
  executing its static initializers and the initializers for static field (class variables) declared in the class.
- interface
  executing the initializers for fields (constants) declared in the interface.
##### When Initialization Occurs
##### Detailed Initialization Procedure
#### Creation of New Class Instances
#### Finalization of Class Instances
#### Unloading of Classes and INterfaces
#### Program Exit
### Binary Compatibility
### Blocks and Statementns
#### The Empty Statement
#### Labeled Statements
#### Expression Statements
#### if
#### assert
#### switch
#### while
#### do
#### for
#### break
#### continue
#### return
#### throw
#### synchronized
#### try
##### Def
- TryStatement:
  try Block Cathes
  try Block [Catses] Finally
  TryWithResourceStatement
- Catches:
  CatchClause {CatchClause}
- CatchFormalParameter:
  {variableModifier} CatchType Variable DeclaratorId
- CatchType:
  UnannClassType {| ClassType}
- Finally:
  finally Block

##### try-catch
##### try-finally, try-catch-finally
##### try-with-resources
###### About
- A try-with-resources statement is parameterized with variables (knwon as resources) that are initialized before execution of the try block and closed automatically.

###### Def
- TryWithResourcesStatement:
  try ResourceSpecification Block [Catches] [Finally]
- ResourceSpecification:
  ( ResourceList [;] )
- ResourceList:
  Resource {; Resource}
- Resource:
  {VariableModifier} UnannType VariableDeclaratorId = Exprssion
#### Unreachable
### Expressions
#### Evaluation, Denotatio, and Result
#### Forms of Expressions
##### Def
- Expression:
  LambdaExpression
  AssignmentExpression
#### Type of an Experssion
#### FP-strict Expressions
#### Expressions and Run-Time Checks
#### Normal and Abrupt Completion of Evaluation
#### Evaluation Order
#### Primary Expressions
##### Def
- Primary:
  PrimaryNoNewArray
  ArrayCreationExpression
- PriamryNoNewArray:
  Literal
  ClassLiteral
  this
  TypeName . this
  ( Expression )
  ClassInstanceCreationExpression
  FieldAccess
  ArrayAccess
  MethodInvocation
  MethodReference

##### Lexical Literals
###### Def
- Literal:
  IntegerLiteral
  FloatingPointLiteral
  BooleanLiteral
  CharacterLiteral
  StringLiteral
  NullLiteral
##### Class Literal
###### Def
- ClassLiteral:
  TypeName {[ ]} . class
  NumericType {[ ]} . class
  boolean {[ ]} . class
  void . class
##### this
##### Qualified this
##### Parenthesized Expressions
#### Class Instance Creation Expressions
#### Array Creation and Access Expressions
#### Field Access Expressions
#### Method Invocation Expressions
#### Method Reference Expressions
#### Postfix Expressions
##### ++
##### --
#### Unary Operators
#### Cast Expressions
#### Multiplicative Operators
#### Additive Opperators
#### Shift Operators
#### Relational Operators
#### Equality Operators
#### Bitwise and Logical Operators
#### Conditional-And Operator &&
#### Conditional-Or Operator ||
#### Conditional Operator ? :
#### Assignment Operators
#### Lambda Expressions
##### About
- 
  関数型インターフェースの代入でラムダ式を渡すことが可能。
  
##### Def
- Lambda Expression:
  LambdaParameters -> LambdaBody
##### Ex
- () -> {}
- () -> 42
- () -> null
- () -> { return 42; }
- () -> { System.gc(); }
- () -> { ... }
- (int x) -> x+1
- (x) -> x+1
- x -> x+1
- (int x, int y) -> x+y
- (x, y) -> x+y
##### Lambda Parameters
###### Def
- LambdaParameters:
  Identifier
  ( [FormalParameterList] )
  ( InferredParameterList )
- InferredFormalParameterList:
  Identifier {, Identifier}
##### Lambda Body
###### Def
- LambdaBody:
  Expression
  Block
#### Constant Expressions
### Definite Assignment
### Threads and Locks
#### Synchronization
##### synchronized statement
##### synchronized method
- it automatically performs alock action when it is invoked;
  its body is not executed until the lock action has successfully completed.
  If the method is an instance method, it locks the monitor associated with the nstance for which it was invoked.
  If the method is static, it locks the monitor associated with the Class object that represents the class in which the method is defined.
#### Wait Sets and Notification
#### Sleep and Yield
#### Memory Model
#### final Field Semantics
#### Word Tearing
#### Non-Atomic Treatment of 'double' and 'long'
### Type Interface
### Syntax
## Memo
### 字句構造
#### コメント
- 
  3種類のコメントがある。

- /* comment */
  伝統的コメント(traditional comment)。
  複数行にわたるコメントの記述に効果的。

- // line-comment
  行末コメント(end of line comment)
  行末までがコメントとなる。

- /** documentation */
  自動生成文書を作成する。
  複数行にわたることができる。

#### 識別子
- 
  識別子(identifier)は、変数、ラベル、メソッド、クラスなどに与えられる名前のこと。

#### キーワード
- 
  abstract boolean break byte case catch char class const continue
  default do double else extends final finally float for goto
  if implements import instanceof int interface long native new package
  private protected public return short static super switch synchronized this
  throw throws transient try void volatile while

#### リテラル
##### 整数リテラル
- 
  整数型の定数を表す。
  
- 種類
  - 10進数リテラル (int / long)
  - 8進数リテラル (int / long)
    先頭に0をつけて2桁以上で表記する。
    ex) 013 (10進数で11)
  - 16進数リテラル (int / long)
    先頭に0xまたは0Xを付けて表記する。
    ex) 0xA (10進数で10), 0x13(10進数で19)

##### 浮動小数点リテラル
- 
  浮動小数点接尾語(float type suffix)を使って表す。
  double型の指定はd, D, 若しくは指定しない場合、
  float型の指定はf, F。
  ex) 80.0  // double
      80.0D // double
      80.0F // float
  
  整数部や小数部を省略可能。
  ex) .5   // 0.5
      10.  // 10.0
      .5f  // 0.5
      1D   // 1.0

##### 論理値リテラル
##### 文字リテラル
- 
  単一の文字を表す。
  シングルクォート(')で囲む。

##### 文字列リテラル
- 
  文字の並びを表す。
  ダブルクォート(")で囲む。

###### 拡張表記
- 拡張表記(escape sequentce)
  |----------------+-------------------------+--------------------------------------------+-------------|
  | 拡張表記       | 意味                    | 内容                                       | Unicode拡張 |
  |----------------+-------------------------+--------------------------------------------+-------------|
  | \b             | 後退(backspace)         | 表示位置を直前の位置へ移動する。           | \u0008      |
  | \f             | 書式送り(form feed)     | 改ページして、次のページの先頭へ移動する。 | \u000c      |
  | \n             | 改行(new line)          | 改行して、次の行の先頭へ移動する。         | \u000a      |
  | \r             | 復帰(carriage return)   | 現在の行の先頭位置へ移動する。             | \u000d      |
  | \t             | 水平タブ(horiontal tab) | 次の水平タブ位置へ移動する。               | \u0009      |
  | \"             | 文字"                   | 二重引用符                                 | \u0022      |
  | \'             | 文字'                   | 単一引用符                                 | \u0027      |
  | \\             | 文字\                   | バックスラッシュ                           | \u005c      |
  | \ooo(oは8進数) |                         | 8進数でoooの値を持つ文字。                 |             |
  |----------------+-------------------------+--------------------------------------------+-------------|

- Unicode拡張
  \uhhhh(hは16進数)で、16進数でhhhhの値を持つ文字を表す。

##### 空リテラル
- 
  null

#### 分離子
- 
  以下の9個のASCII文字をJava分離子(separators)とする。
  ( ) { } [ ] ; ,

#### 演算子
- 
  以下の37個のトークンをJava演算子(operators)とする。
  = > < ! ~ ? : == <= >= != && || ++ --
  + - * / & | ^ % << >> >>>
  += -= *= /= &= |= ^= %= <<= >>= >>>=

### 型、値
#### Primitive Type
- 
  プリミティブ型、値型、基本型

##### Numeric Type
- 
  数値型

###### Integral Type
- 
  整数型

- byte
  -128 ~ 127
  1バイトデータ
- short
  -32768 ~ 32767
- int
  -2147483648 ~ 2147483647
- long
  -9223372036854775808 ~ 9223372036854775807
- char
  '\u0000' ~ '\uffff' (0 ~ 65535)

####### 整数演算
######## 比較演算子
- 数値比較
  < <= > >=

- 数値等価演算子
  == !=

######## 数値演算子
- 単項符号演算子
  + -

- 乗除演算子
  * / %

- 加法演算子
  + -

- 増分演算子
  ++（接頭語及び接尾語）

- 減分演算子
  --（接頭語及び接尾語）

- 符号付き、符号無しシフト演算子
  << >> >>>

- ビット単位補数演算子
  ~

- 整数ビット単位演算子
  & | ^

######## 条件演算子
- 条件演算子
  ?:

######## キャスト演算子

######## 文字列連結演算子
- 文字列連結演算子
  +

###### Floating Point Type
- 
  浮動小数点型

- float
  s * m * 2e
  s : +1 or -1
  m : m < 2^24
  e : -149 <= e <= 104

- double
  s * m * 2e
  s : +1 or -1
  m : m < 2^52
  e : -1075 <= e <= 970

- 正及び負のゼロ、正及び負の無限大、並びにNot-a-Number(NaN)を含む。

####### 順序
- 
  負の無限大 < 負の有限非ゼロ < 負のゼロ < 正のゼロ < 正の有限非ゼロ < 正の無限大
  正のゼロと負のゼロの比較結果は等しい。(-0.0=0.0)
  NaNは順序付けしない。

####### 浮動小数点演算
######## 比較演算子
- 数値比較
  < <= > >=

- 数値等価演算子
  == !=

######## 数値演算子
- 単項符号演算子
  + -

- 乗除演算子
  * / %

- 加法演算子
  + -

- 増分演算子
  ++（接頭語及び接尾語）

- 減分演算子
  --（接頭語及び接尾語）

######## 条件演算子
- 条件演算子
  ?:

######## キャスト演算子

######## 文字列連結演算子
- 文字列連結演算子
  +

##### Boolean
- 
  論理型

- true
- false

###### 演算
- 関係演算子
  == !=
- 論理補数演算子
  !
- 論理演算子
  & ^ |
- 条件付きAND及びOR演算子
  && ||
- 条件演算子
  ?:
- 文字列連結演算子
  +

#### Reference Type
- 
  参照型。
  クラス型、インターフェース型、配列型が存在する。
  参照値はオブジェクトのポインタ、もしくはいかなるオブジェクトも参照しない特別な空参照となる。

##### Class Or Interface Type

###### Class Type

####### クラス
- 
  メソッドと処理対象となるデータを組み合わせた構造。

- 宣言
  new Class()

- 等価演算子
  ==でインスタンス同士を比較した場合、インスタンスの参照先が同じか否かで比較を行う。
  例えば内部フィールド値が全て等しくても、違うメモリ空間を指していた場合はfalseが返る。

####### メンバ

######## フィールド
- 
  メソッドの外で宣言された変数。

- アクセス
  メンバアクセス演算子(meber access operator)を使う。ドット演算子(.)。

######## メソッド
- void
  値を返さないメソッドは戻り値の型をvoidとする。

- return
  return文で値を呼び出し元に返却する。

- 仮引数
  formal parameter
  メソッドの頭に記載する変数名。呼び出し時に初期化される。
  finalをつけると仮引数を変更できなくなる。

- 実引数
  actual argument
  メソッド呼び出し時に受け渡すことを指定する値。
  左から順に評価される。

- this参照
  自分を起動したインスタンスへの参照をthisとして持っている。

######### overload
- 
  多重定義。同じシグネチャのメソッドは多重定義できない。
  シグネチャは、メソッド名と、仮引数の個数と型の組合せのこと。戻り値型は含まれない。

######## コンストラクタ
- 
  構成子
  クラス名と同名の戻り値を持たないメソッドと同様の形式で記述する。
  ちなみにクラス名と同名のメソッドも定義できるが、推奨されない。

  厳密にはコンストラクタはメンバに含めないらしい。
  

####### その他

######## Object Class
- 
  Objectはすべての他のクラスのスーパークラスとなる。
  すべてのクラス及び配列型はObjectを継承する。

###### Interface Type

##### Array Type
- 
  配列型

- 宣言
  以下のどちらでも可（ただし、一般に1の方が好まれる）。
  1. int[] a;
  2. int a[];
  
- 生成
  newによって生成する。
  ex) a = new int[5];

- 規定値
  |---------+-------------------|
  | 型      | 規定値            |
  |---------+-------------------|
  | byte    | ゼロ / (byte)0    |
  | short   | ゼロ / (short)0   |
  | int     | ゼロ / 0          |
  | long    | ゼロ / 0L         |
  | float   | ゼロ / 0.0f       |
  | double  | ゼロ / 0.0d       |
  | char    | 空文字 / '\u0000' |
  | boolean | 偽 / false        |
  | 参照型  | 空参照 / null     |
  |---------+-------------------|

- 初期化
  { }の中にカンマ区切りで値を書くと、その値で初期化される。
  ex) int[] a = {1, 2, 3, 4, 5}
  
  以下のように初期化子を代入することはできない。
  a = {1, 2, 3, 4, 5}
  以下なら可能。
  a = new int[]{1, 2, 3, 4, 5}

###### メソッド
(どこにどのように書くべきか迷っているところ)
- length
  
### 変数、変換
#### 種類
- クラス変数 class variable
  staticをつけて宣言されたフィールド。
- インスタンス変数 instance variable
- 配列構成要素 Array components
- メソッド仮引数 Method parameters
- コンストラクタ仮引数 Constructor parameters
- 例外ハンドラ仮引数 exception-handler parameter
- 局所変数 Local variables

#### 変換

##### 種別
###### 恒等変換

###### プリミティブ型の拡大変換

###### プリミティブ型の縮小変換

###### 参照型の拡大変換

###### 参照型の縮小変換

###### 文字列の変換

##### 文脈

###### 代入変換
###### メソッド呼び出し変換
###### キャスト変換
- 
  

###### 文字列変換
###### 数値昇格
####### 単項数値昇格
####### 二項数値昇格
- 
  binary numerical promotion
  特定の演算子のオペランドに対して、より大きい型に変換された上で実行される。
  以下のような規則に従う。
  - 一方のオペランドがdoubleであればdoubleに、
    そうでなくfloatであればfloatに、
    そうでなくlongであればlongに、
    そうでなければintに変換する。

### 名前
- 
  宣言した実態を参照するために使用する。
  有効範囲を持つ。

#### 宣言 declaration
- 
  実態を導入し、参照するために名前として使用できる識別子を取り入れる。

- 宣言される実態
  - package宣言で宣言したパッケージ
  - 型インポート宣言で宣言した型
  - クラス型宣言で宣言したクラス
  - 参照型のメンバ
    - フィールド
      - クラス型で宣言したフィールド
      - インタフェース型で宣言したメソッド(abstract)
  - 仮引数
    - クラスのメソッド又はコンストラクタの仮引数
    - インターフェースのabstractなメソッドの仮引数
    - try文のcatch節で宣言した例外ハンドラの仮引数
  - 局所変数
    - ブロックにおける局所変数宣言
    - for文における局所変数宣言

#### 決定
- 
  名前の決定には三段階が必要。
  1. 名前を5つの分類のどれかに分類する。
     PackageName, TypeName, ExpressionName, MethodName, AmbiguousName 
  2. AmbiguousNameに分類された名前は、有効範囲の規則によってPackage, Type Expressionのどれかに分類する。
  3. 名前の意味を最終的に決定する。意味をもたなければコンパイルエラーとする。

#### 名前付け規則
##### パッケージ名
- 
  広く利用可能にするには、最初の構成要素をすべて大文字で書く。
  Sun.COMのようなドメインを逆順にし(COM.Sun)、以降は組織内の規約(部、課、プロジェクト等)を利用する。
  ex) COM.Sun.sunsoft.DOE
      EDU.cmu.cs.bovik.cheese
  局所使用だけを意図したパッケージ名は、小文字で始まる識別子をもつことが望ましい。
  識別子javaで始まるパッケージ名は標準javaパッケージを名前付けするために予約されている。

##### クラス及びインターフェース型名
- 
  各単語の先頭文字を大文字とし、大文字小文字を混在させた、記述的なー名詞または名詞句が望ましい。
  ex) ClassLoader
      SecurityManager
  インターフェースは、名詞又は名詞句でもよい。抽象スーパークラスでは特に適している。
  また、java.lang.Runnableやjava.lang.Cloneableのように、振る舞いを記述する形容詞としてもよい。

##### メソッド名
- 
  先頭文字を小文字とし、それに続く各単語の先頭文字を大文字とする、大文字と小文字を混在させた動詞またh動詞句が望ましい。

##### フィールド名
- 
  finalでないフィールドの名前は、先頭文字は小文字で始まり、それに続く単語の先頭文字を大文字とした、
  大文字小文字を混在させたものとすることが望ましい。
  名詞、名詞句または名詞の省略形の名前を持つことが望ましい。

##### 定数名
- 
  全て大文字で、下線"_"で区切られた構成要素を持つ、一つ以上の単語、頭文字又は略語の並びとすることが望ましい。
  クラス型のfinal変数も、慣例として、同じ並びとしてよい。

##### 局所変数および仮引数名
- 
  短いが意味のあるものとするのが望ましい。普通、単語ではない短い小文字の列とする。
  ex) in, out, off, len, bufなど

### パッケージ
### 例外
### ブロック及び文
#### ブロック
- 
  文の並びを{ }で囲んだ物をブロック(block)という。
  構文上単一の文と見なされる。

#### 文
- 
  文(statement)は、基本的にセミコロン(;)で終える。

##### if
###### if-then
###### if-then-else
##### switch
- ex)
  switch (a) {
    case 1  : c = 10; break;
    case 2  : c = 20; break;
    case 3  : c = 50; break;
    default : if ( b == 4 ) c = 80; break;
  }

##### while
- 
  while ( codition ) {
    ...
  }

##### do
- 
  do {
    ...
  } while ( condition )

##### for
- 
  for (初期化部; 制御部; 更新部) {
    ...
  }

- 拡張for文
  for-each文やfor-in文とも呼ばれる。

  for (<型> <変数名> : <配列やList型>) {
    ...
  }


##### break
- 
  breakにラベルを付けると、任意のループから抜けられる。
  ラベル付きbreakは、ループの中でなくても使える。

##### continue
- 
  continueにラベルを付けて、

##### return
##### throw
##### synchronized
##### try
###### try-catch
###### try-catch-finally

### 式
- 
  式(expression)とは以下の総称。
  - 変数
  - リテラル
  - 変数やリテラルを演算子で結合したもの

#### クラスインスタンス生成式
#### 配列生成式
#### フィールドアクセス式
#### メソッド呼出し式
#### 配列アクセス式
#### 後置式
##### ++ 後置インクリメント演算子
##### -- 後置デクリメント演算子
#### 単項演算子
##### ++ 前置インクリメント演算子
##### -- 後置デクリメント演算子
##### + 単項演算子
##### - 単項マイナス演算子
##### ~ ビット毎の補数演算子
##### ! 論理的な補数演算子
#### キャスト式
- 
  キャスト演算子で指定した型に変換する。
  括弧内に指定した名前の型に変換する。

- 形式
  (型)式

- 縮小変換
  より小さい型への代入時(double -> intなど)はキャストが必要。
  ex) a = (int)10.0;

  代入時に右辺の式や初期化子の定数式が変数の型(byte, short, charのみ)で表現できる場合は、
  縮小変換が自動で行われる。
  定数式に限られるため、変数の代入はエラーとなる。
  ex) short a = 53;  // OK
      byte b = a;    // NG

  浮動小数点については自動で変換が行われないため、floatにdouble型の値は代入不可能。
  ex) float a = 3.14;        // NG。3.14はdouble
      float b = 3.14f;       // OK
      float c = (float)3.14; // OK

- 拡大変換
  拡大変換時はキャスト不要。
  ex) int a = '5';       // OK
      long b = a;        // OK
      double c = 3.14f;  // OK

#### 乗除演算子
##### * 乗算演算子
##### / 除算演算子
##### % 剰余演算子
#### 加減演算子
##### + 文字列連結演算子
##### +, - 数値加減演算子
#### シフト演算子
- << 左シフト
  x << n : xをnビット左にシフトして、空いたビットに0を詰めた値を生成する。

- >> 右シフト（算術シフト)
  x >> n : xをnビット右にシフトして、空いたビットをシフト前の符号ビットで埋め尽くした値を生成する。

- >>> 右シフト（論理シフト）
  x >>> n : xをnビット右にシフトして、空いたビットに0を詰めた値を生成する。

#### 関係演算子
##### <, <=, >, >= 数値比較演算子
##### instanceof 型比較演算子
#### 等価演算子
##### ==, != 数値等価演算子
##### ==, != 論理型等価演算子
##### ==, != 参照型等価演算子
#### ビット単位の論理演算子
##### &, ^, | 整数値ビット単位演算子
##### &, ^, | 論理型論理演算子
#### 条件AND演算子 &&
- 
  &と異なり、短絡評価(short circuit evaluation)が行われる。
  
#### 条件OR演算子 ||
- 
  短絡評価が行われる。|では両辺が必ず評価される。

#### 条件演算子 ?:
#### 代入演算子
##### = 単純代入演算子
- 
  代入式を評価すると、左オペランドの型と値が得られる。
  代入演算子は右結合。
  ex) a = b = 1 => a = (b = 1)
  
  初期化時は、上記の構文はエラーとなる。
  ex) int a = b = 0;   // コンパイルエラー

##### 複合代入演算子
- 
  演算と代入という二つの働きをもつため、複合代入演算子と呼ばれる。

- 一覧
  *= /= %= += -= <<= >>= >>>= &= ^= |=

### API
#### java.io
#### java.lang
##### java.lang.System
###### System.out
- 
  System.outはコンソール画面と結びつくストリームで、
  標準出力ストリーム(standard output stream)と呼ばれる。

####### println
- 
  改行付きの表示。lnはline。

####### printf
- 
  ex) System.out.printf("x = %3d\n", x);

  %は書式指定の先頭文字なので、文字%を出力したい場合は%%と表記する。

- 変換文字
  |----------+------------------|
  | 変換文字 | 解説             |
  |----------+------------------|
  | %d       | 10進数で出力     |
  | %o       | 8進数で出力      |
  | %x       | 16進数で出力     |
  | %f       | 小数点形式で出力 |
  | %s       | 文字列で出力     |
  |----------+------------------|
  
####### print
- 
  表示後に改行はされない。


###### system.in
- 
  System.inは標準入力ストリーム(standard input stream)

#### java.math
#### java.net
#### java.util
##### java.util.Scanner
- 
  nextInt()やnextDouble()等のメソッドで入力値を取り出す。
  文字列の読込みにはnext()を使う。空白やタブ文字が区切りと見なされる。
  一行読込む場合はnextLine()。

##### java.util.Random
- 
  乱数の生成

- インスタンスの生成
  1. Random rand = new Random();
  2. Random rand = new Random(5);

- メソッド
  |---------------+---------+--------------------------|
  | メソッド      | 型      | 生成される値の範囲       |
  |---------------+---------+--------------------------|
  | nextBoolean() | boolean | true / false             |
  | nexnInt()     | int     | -2147483648 ~ 2147483647 |
  | nextInt(n)    | int     | 0 ~ n-1                  |
  | nextLong()    | long    |                          |
  | nextDouble()  | double  | 0.0以上1.0未満           |
  | nextFloat()   | float   | 0.0以上1.0未満           |
  |---------------+---------+--------------------------|


##### java.util.GregorianCalendar
- 
  日付・時刻を扱うためのクラス。

##### java.util.Date

##### java.util.Calender
#### Link
- [[http://xfs.jp/3sx0wC][Java Platform, Standard Edition 8: API Specification]]

### Java SE 5.0

#### static import
- 
  static変数やstaticメソッドをクラス名を指定せずに使用する機能。

- 
  import static packageName.className.staticVariables;
  import static packageName.className.staticMethods;
  import static packageName.className.*;

## Link
- [[http://docs.oracle.com/javase/specs/jls/se8/html/index.html][The Java Language Spcification (Java SE 8 Edition)]]
