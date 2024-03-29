# Python 2 Language
## Tutorial
### 実行
- python
- python <program-name>
- python -c <command-name> [arg] ...

### ソースコードの文字コード
- 
  # -*- coding: encoding -*-
### 文字列
- immutable
  変更不可能。
- slice
  word[0:2]
### 制御フロー
#### if
- 
  - 例
    if x < 0: 
        x = 0;
    elif x == 0:
        print 'Zero'
    else:
        print 'More'

#### for
- 
  - 例
    for w in words:
        print w, len(w)
    
#### range
- 
  - 例
    range(0, 10, 3)
    
#### break, continue, else
- 
  ループにelseが存在する。ループが終了した際に実行されるが、breakで抜けた場合は実行されない。
  continueは次のイテレーションを実行する
  - 例
    for n in range(2, 10):
        for x in range(2, n):
            if n % x == 0:
                print n, 'equals', x, '*', n/x
                break
        else:
            print n, 'is a prime number'
    
#### pass
- 
  何もしない。構文上何か書かなければいけない時に書く。
  - 例
    class MyEmptyClass:
        pass

#### 関数定義
- 
  def fib(n):
      definition
  
##### default argument
- 
  - 例
    - def ask_ok(prompt, retries=4, complaint='Yes or no, please!'):
          (def)
##### keyword argument
- 
  kwarg=valueという形式のキーワード引数を使って呼び出すことができる。
  - 例
    - def parrot(voltage, stage='a stiff', action='voom', type='Norweign Blue'):
          (def)
      
##### unpack
- 
  *演算子を使ってリストやタプルから引数をアンパックする。
  **オペレータを使って辞書でもキーワード引数を渡すことができる。
  - 例
    args = [3, 6]
    range(*args)
##### lambda
- 
  - 例
    def make_incrementor(n):
        return lambda x: x + n

## Command line
- -?, -h, --help
  オプションの使い方を出力する。
- -V, --version
  バージョン番号を表示する。
- -i
  実行後にインタラクティブモードに入る。
- -c <command-name>
- -m <module-name>
## Environmental variables
### PYTHONHOME
### PYTHONPATH
## Language
### Parser
#### line structure
##### logical line
##### physical line
##### Comments
- 
  ハッシュ"#"から始まり、同じ物理行の末端で終わる。
##### encoding declaration
##### 明示的な行継続
##### 非明示的な行継続
##### 空行
##### インデント
##### トークン間の空白
#### Token
#### Identifier
#### Keyword
#### Literal
##### Strings literal
##### Concatenation
##### Number literal
##### Integer literal
##### float literal
##### imaginary literal
##### operator
##### delimiter

### Data model
### Exec model
### Expression
#### Arithmetic conversion
#### Atom
#### Primary
#### Awati expression
#### power operator
- power ::= await ["**" u_expr]
##### **
#### unary arithmetic and bitwise operation
- u_expr ::= power | "-" u_expr | "+" u_expr" | "~" u_expr
##### -
##### +
##### ~ 反転
- 整数引数をビット単位反転(bitwise invert)したものを与える。
#### binary arithmetic operation
- m_expr ::= u_expr | m_expr "*" u_expr | m_expr "@" m_expr |
             m_expr "//" u_expr | m_expr "/" u_expr | m_expr "%" u_expr
- a_expr ::= m_expr | a_expr "+" m_expr | a_ekpr "-" m_expr
##### *
- multiplication 乗算

##### @
- 行列の乗算

##### /
- division 除算
##### //
- floor division 切り捨て除算
  除算にfloorを適用したもの。
##### %
- modulo 剰余
##### +
##### -
#### shifting operation
#### binary bitwise operation
#### comparing
#### boolean operaiton
#### Conditional Expressions
#### lambda
#### list of expressions
#### evaluate order
#### primarity of operand
### Simple statement
### Compound statement
#### if
#### while
#### for
#### try
#### with
### Top Level
## Library
### Standard Library
#### built-in
##### Function
###### abs()
###### all()
###### any()
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
###### print()
- print(*objects, sep='', end='\n', file=sys.stdout)
  object(複数でも可)をsepで区切りながらストリームfileに表示し、最後にendを表示する。
  sep, end, fileが与えられる場合、キーワード変数として与えられる必要がある。

##### Non-essential Function
##### Constant
##### Type
###### Truth Value Testing
###### Boolean Operations
###### Comparisons
###### Numeric Types
####### Bitwise Operations on Integer
####### Aditional Methods on Integer
####### Additional Methods on Float
###### Iterator Types
###### Sequence Types
- str, unicode, list, tuple, bytearray, buffer, xrange
####### String Method
######## str.split()
- str.split([sep[, maxsplit]])
  sepを単語の境界として文字列を単語に分解し、分割された単語からなるリストを返す。
  
###### Set Types
###### Mapping Types
###### File Object
- 
  Cのstdioパッケージを使って実装されており、組み込み関数のopen()で生成することができる。
  
####### Methods
######## file.close()
######## file.flush()
######## file.read()
- file.read([size])
  最大でsizeバイトをファイルから読み込む。
  size引数が負であるか省略された場合、EFに到達するまでのすべてのデータを読み込む。
######## file.readline()
######## file.readlines()
######## file.seek()
- file.seek(offset[, whence])
  ファイルの現在位置を設定する。

- whence
  - 0, os.SEEK_SET
    絶対位置指定。デフォルト。
  - 1, os.SEEK_CUR
    現在のファイル位置から相対的にseekする
  - 2, os.SEEK_END
    ファイルの末端から相対的にseekする
######## file.write()
- file.write(str)
  文字列をファイルに書き込む。戻り値はない。
######## file.name
- 
  ファイルオブジェクトがopen()を使って生成された時のファイルの名前。
######## file.mode
- 
  ファイルのI/Oモード。
  Version 2.6で追加。
###### memoryview type
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
##### Exception
#### 文字列処理
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
#### データ型
#### 数値と数学モジュール
#### ファイルとディレクトリへのアクセス
##### glob
- Unix形式のパス名のパターン展開
###### glob
- glob.glob(pathname)
  pathnameにマッチする空の可能性のあるパス名のリストを返す。
###### iglob
- glob.iglob(pahtname)

#### データの永続化
#### データ圧縮とアーカイブ
#### ファイルフォーマット
#### 暗号関連のサービス
#### 汎用オペレーティングシステムサービス
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
####### os.listdir()
- os.listdir(path)
  pathで指定されたディレクトリ内のエントリ名が入ったリストを返す。
  利用できる環境 : Unix, Windows
###### Process Management
###### Miscellaneaus System Information
###### Miscellaneaus Function
#### オプションのオペレーティングシステムサービス
#### プロセス間通信とネットワーク
#### インターネット上のデータの操作
#### 構造化マークアップツール
#### インターネットプロトコルとサポート
#### マルチメディアサービス
#### 国際化
#### プログラムのフレームワーク
#### Tkを用いたグラフィカルユーザインターフェース
#### 開発ツール
#### デバッグとプロファイル
#### ソフトウェア・パッケージと配布
#### Pythonランタイムサービス
##### sys
- システムパラメータと関数
###### sys.argv
- 
  Pythonスクリプトに渡されたコマンドライン引数のリスト。
  argv[0]はスクリプトの名前となるが、フルパスかどうかはOSによる。

###### sys.stdin, sys.stdout sys.stderr
- 
  インタープリタの標準入力・標準出力・標準エラー出力に対応するファイルオブジェクト。
  stdinはスクリプトの読み込みを除く全ての衆力処理で使用され、input()やraw_input()もstdinから読み込む。

###### sys__stdin__, sys.__stdout__, sys.__stderr__
- 
  それぞれ起動時のstdin, stdout, stderrの値を保持する。終了処理時に利用される。

#### カスタムPythonインタプリタ
#### 制限実行
#### モジュールのインポート
#### Python言語サービス
#### Pythonコンパイラパッケージ
#### 各種サービス
#### MSWin固有
#### Usix固有
#### MacOSX固有
## Link
- [[http://docs.python.jp/2/tutorial/][Pythonチュートリアル 2]]

