# Go
## Reference
### Packages
#### Standard library
- [[file:Go_StandardLibrary.org][Go_StandardLibrary.org]]
#### Other packages
##### Sub-repositories
##### Community
### Commands
#### go
- go command [arguments]
  a tool for managing Go source code.
##### commands
###### build
- compile packages and dependencies
###### clean
- remove object files
###### doc
- show documentation for package or symbol
###### env
- print Go environment information
###### fix
###### fmt
###### generate
###### get
###### install
- compile and install packages and dependencies
###### list
###### run
- compile and run Go program
###### test
- test packages
###### tool
####### tour
###### version
###### vet
#### cgo
- 
  Cgo enables the creation of Go packages that call C code.
  
#### cover
#### fix
#### fmt
- Fmt formats Go packages, it is also abailable as an indippendent gofmt command with more general options.
#### godoc
#### vet
#### yacc
### Language Specification
#### Notation
- The syntax is specified using Extended Backus-Naur Form (EBNF)
  - Production  = production_name "=" [ Expression ] "." .
  - Expression  = Alternative { "|" Alternative } .
  - Alternative = Term { Term } .
  - Term        = production_name | token [ "..." token ] | Group | Option | Repetition .
  - Group       = "(" Expression ")" .
  - Option      = "[" Expression "]" .
  - Repetition  = "{" Expression "}" .

- operators
  Productions are expressions constructed from terms and following operators.
  - |  alternation
  - () grouping
  - [] option (0 or 1 times)
  - repetition (0 to n times)

#### Lexical elements
##### Comments
- // : Line comments
- /* ... */ : General commetns
##### Tokens
- 
###### Semicolons
###### Identifiers
###### Keywords
###### Operators and Delimiters
###### Literals
####### Integer literals
####### Floating-point literals
####### Imaginary literals
####### Rune literals
####### String literals
#### Constans
#### Variables
#### Type
##### Method sets
##### Boolean types
##### Numeric types
##### String types
##### Array types
##### Slice types
##### Struct types
##### Pointer types
##### Function types
##### Interface types
##### Map types
##### Channel types
#### Blocks
#### Declarations and scope
#### Expressions
#### Statements
##### Terminating statements
##### Empty statements
##### Labeled statements
##### Expression statements
##### Send statements
##### IncDec statements
##### Assignments
##### If statements
##### Switch statements
##### For statemens
##### Go statemetns
##### Select statements
##### Return statements
##### Break statements
##### Continue statements
##### Goto statements
##### Fallthrough statements
##### Defer statements
#### Built-in functions
#### Packages
#### Errors
### The Go Memory Model
## Installing Go
## Learning Go
### A Tour of Go
- https://tour.golang.org/list
#### Basics
##### Packages, variables, and functinos
###### Packages
- package main
###### Imports
- import (
      "fmt"
      "math"
  )
###### Exported names
- 大文字で始まる名前は、外部のパッケージから参照できるエクスポートされた名前。
- 小文字で始まるpiやhogeなどは、エクスポートされていない名前。
###### Functions
- func add(x int, y int) int {
    return x + y
  }
- 複数の引数が同じ型である場合、最後の型を残して他は省略可。
  func add(x, y int) int {
    return x + y
  }
###### Multiple results
- return x,y
- a, b := ~
###### Named return value
- 戻り値の変数に名前を付けることができる
  func split (sum int) (x, y int) {
    x = sum * 4 / 9
    y = sum - x
    return
  }
###### Variables
- var i int
###### Variables with initialiers
- var i, j int = 1, 2 (multiple)
###### Short variable declarations
- k := 3 (short declarations)
  関数の中のみ。関数の外では宣言が必要で、暗黙的な宣言(:=)はできない。
###### Basic types
- bool
- string
- int int8 int16 int32 it64
- uint uint8 uint16 uint32 uint64 uintptr
  (int, uint, uintptrは32bitシステムでは32bit, 64bitシステムでは64)
- byte (uint8の別名)
- rune (int32の別名)
- float32 float64
- complex64 complex128
###### Zero values
- 数値型: 0
- bool: false
- string: ""(空文字列)
###### Type conversions
- 変数vの型Tへの変換はT(v)。
  i := 42; f := float64(i); u := uint(f);
###### Type inference
- 右側の変数から型推論される。
- 型を指定しない数値である場合、精度に基づいてint, float64, complex128の型が使われる。
###### Constants
- 文字、文字列、boolean、数値のみで使える。:=による宣言はできない。
- const World = "世界"
- 数値の定数でk棚がない場合、状況によって必要な型を取る。
###### Numeric Constants
- 型のない定数は状況によって必要な型をとる。
  intで桁数が足りない場合、定数を使うと良い。
##### Flow control statements: for, if, else, switch and defer
###### For
- セミコロンで初期化stmt, 条件式, 後処理stmtを書く。()で囲む必要はない。
  処理の中括弧{ }は必要。
  - for i := 0; i < 10; i++ {
      sum += i
    }

- 初期化と後処理stmtは省略可
  - for ; sum < 1000; {
      sum += sum
    }
  
- セミコロンの省略も可能。whileのように利用可能。
  - for sum < 1000 {
      sum += sum
    }

- ループ条件を省略して無限ループを書ける。
  - for {
    }

###### If
- Basic
  - if x < 0 {
      return sqrt(-x) + "i"
    }

- with a short statement
  - if v := math.Pow(x, n); v < lim {
      return v
    }

- else
  - if v := math.Pow(x, n); v < lim {
      return v
    } else {
      fmt.Printf("%g >= %g\n", v, lim)
    }

###### Switch
- 条件なしはswitch trueと同じ。ifの積み重ねより簡潔になる。
###### Defer
- defer: 関数が元の関数がreturnするまで遅延される
- 複数ある場合はLIFOで実行される
##### More types: structs, slices, and maps
###### Pointers
- p := &i
  *p = 21
###### Structs
- type StructA struct {
    X int
    Y int
  }
###### Struct Fields
- アクセスはドット
- v := StructA{1,2}
  v.X = 4
###### Pointers to structs
- Structのポインタで、要素は(*p).Xだが、
  代わりにp.Xと記載可能
  
###### Struct Literals
###### Arrays
- [n]T
- var a [10]int
###### Slices
- a[low:high]
###### Slices are like references to arrays
- 
###### Slice literals
- 配列リテラル
  [3][bool{true, true, false}
  [][bool{true, true, false}
###### Slice defaults
###### Slice length and capacity
- len(s) : スライスの長さ
- cap(s) : スライスの容量
###### Nil slices
- nil
###### Creating a slice with make
- a := make([]int, 5)
- a := make([]int, 1, 2)
  2は容量(capacity)
###### Slices of slices
###### Appending to a slice
- スライスへ要素の追加
  s = append(s, 0)
###### Range
- range: スライスやマップをひとつずつ反復処理するために使う
###### Range continued
- "_"への代入で値を削除できる
###### Execise: Slices
###### Maps
- var m map[string]Vertex
- m = make(map[string]Vertex)
###### Map literals
- map[string]Vertex{
    "Bell Labs": Vertex{
      123, 456,
    },
    "ABC": Vertex{
      111, 123,
    },
  }
###### Map literals continued
- 型名を推測して省略可能
  map[string]Vertex{
	"Bell Labs": {40.68433, -74.39967},
	"Google":    {37.42202, -122.08408},
  }

###### Mutating Maps
- m["test"] = 10
  delete(m, "test")
###### Exercise: Maps
###### Function values
- 関数も変数。
###### Function closures
- Goの関数はクロージャ。
###### Exercise: Fibonacci closuer
#### Methods and interfaces
##### Methods
###### Methods
- classの仕組みはないが、型にmethodを定義できる。
  メソッドは、receiver引数を関数にとる
###### Methods are functions
- レシーバ引数を伴う関数
###### Methods continued
- レジーバを伴うメソッドの宣言は、レシーバ型が同じパッケージ内にある必要がある
###### Pointer receivers
- 変数レシーバよりもポインタレシーバの方が一般的
###### Pointers and functions
###### Methods and pointer indirection
###### Methods and pointer indirection 2
- 変数レシーバの場合、変数、ポインタいずれかのレシーバとしてとることができる
  p.Abs()は(*p).Abs()として解釈される
###### Choosing a value or pointer receiver
- ポインタレシーバを使う理由
  1. 変数を更新するため
  2. 変数のコピーを避けるため（レシーバが大きな構造体である場合など）
- 変数レシーバ、ポインタレシーバを混在させるべきではない。
###### Interfaces
- インターフェース型
  メソッドのシグニチャの集まりで定義
  type Abser interface {
      Abs() float64
  }
###### Interfaces are implemented implicity
- 明示的にインターフェース実装を宣言しなくてよい
###### Interface values
- インターフェースの値は、下記のような型のタプル
  (valuen, type)
###### Interface values with nil underlying values
###### Nil interface values
###### The empty interface
###### Type assertions
- 型アサーション
###### Type switches
- 型switch
  いくつかの型アサーションを直列に使用できる構造
###### Stringers
- Stringerインターフェース: String() stringを持つ
  stringとして表現できる型
###### Excercise: Stringers
###### Errors
- error型
  インターフェースとしてError() stringを持つ
###### Exercise: Errors
###### Readers
- ioパッケージ "io"
- strings.NewReader("message")
- r.Read(b) : Reader rから読み込んだ文字をbに書き込む。
  戻り値: 文字数, エラー

- 終端はエラーにio.EOFを返す
###### Exercise: Readers
###### Exercise: rot13Reader
###### Images
- imageパッケージ, Imageインターフェース
###### Exercise: Images
#### Concurrency
##### Concurrency
###### Goroutines
- goroutine: 軽量なスレッド
  go f(x, y, z)
###### Channels
- Channel型
  チャネルオペレータの <- を用いて値の送受信ができる
###### Buffered Channels
- make時、第二引数にバッファのサイズを入れる
  make(chan int, 100)
###### Range and Close
- for i := range c
  チャネルが閉じられるまで繰り返し値を受信する。
###### Select
- selectステートメント
  goroutineを複数の通信操作で待たせる。
  caseのいずれかが準備できるようになるまでブロックし、準備できたcaseを実行する。
  複数のcaseの準備ができている場合、caseはランダムに選択される。
###### Default Selection
###### Excercise: Equivalent Binary Trees
###### Excercise: Equivalent Binary Trees
###### sync.Mutex
###### Excercise: Web Crawler
###### Where to Go from here...
### How to write Go code
- https://golang.org/doc/code.html
- [[https://www.youtube.com/watch?v=XCsL89YtqCs][Writing, building, installing, and testing Go code - YouTube]]

#### Introduction
#### Code organization
##### Overview
- typically keep all Go code in single workspace
##### Workspaces
- directories
  - src: Go source files
  - pkg: package objects
  - bin: executable commands
##### The GOPATH environment variable
- export PATH=$PATH:$(go env GOPATH)/bin
  export GOPATH=$(go env GOPATH)
##### Import paths
##### Your first program
##### Your first library
##### Package names
#### Testing
- import "testing"
  func TestXXX(t *testing.T)
  
- command:
  go test
#### Remote packages
- go get
#### What's next
### Editor plugins and IDEs
### Effective Go
- https://golang.org/doc/effective_go.html
## Tools
### Delve
- https://github.com/derekparker/delve
## Source
- [[file:Go_Source.org][Go_Source.org]]
## Memo
## Link
- [[https://golang.org/][The Go Programming Language]]

- [[http://ascii.jp/elem/000/001/235/1235262/][Goならわかるシステムプログラミング - プログラミング]]
- [[https://motemen.github.io/go-for-go-book/][GoのためのGo]]

- [[http://qiita.com/tenntenn/items/0e33a4959250d1a55045][Go言語の初心者が見ると幸せになれる場所 - Qiita]]
- [[https://astaxie.gitbooks.io/build-web-application-with-golang/content/ja/index.html][Go Web プログラミング]]
