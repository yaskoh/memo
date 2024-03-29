# JavaScript
## Specification
### JavaScript(MDN)
#### Global Objects グローバルオブジェクト
##### Value propeties
###### Infinity
###### NaN
###### undefined
###### null literal
##### Function properties
###### eval()
###### isFinite()
###### isNaN()
###### parseFloat()
###### parseInt()
###### decodeURI()
###### decodeURIComponent()
###### encodeURI()
###### encodeURIComponent()
###### uneval() - nonstandard
###### escape() - deprecated
###### unescape() - deprecated
##### Fundamental objects 基本オブジェクト
###### Object
####### Object Object
######## Constructor Properties
######### Object.length
######### Object.prototype
######## Constructor Methods
####### Object Instance / Object.prototype
######## Properties
######### Object.prototype.constructor
- オブジェクトのプロトタイプを生成する関数への参照を返す。
######### Object.prototype.__proto__
- オブジェクトをインスタンス化する際にプロトタイプとして使用するオブジェクトへのポインタ。
######## Methods
######### Object.prototype.hasOwnProperty()
- 指定したプロパティが、プロトタイプチェーンを通じて継承されたものではなくオブジェクトが直接持っているプロパティかどうかを示す真偽値を返す。
######### Object.prototype.isPrototypeOf()
- 指定したオブジェクトが、このメソッドを呼び出した元であるオブジェクトのプロトタイプチェーンにあるかどうかを示す真偽値を返す。
######### Object.prototype.propertyIsEnumerable()
- 内部のEMCAScript[ [ Enumerable] ]属性ね設定状態を示す真偽値を返す。
######### Object.prototype.propertyIsEnumerable()
- 内部のECMAScript[ [Enumerable] ]属性の設定状態を表す真偽値を返す。
######### Object.prototype.toLocaleString()
- toString()を呼び出す。
######### Object.prototype.toString()
- 指定したオブジェクトを表す文字列を返す。
######### Object.prototype.valueOf()
- 指定したオブジェクトのプリミティブ値を返す。プリミティブな値を持たない場合、オブジェクト自身を返す。
  オブジェクトをプリミティブな値に変換するときに呼び出す関数。
  
###### Function
- return文がない、return文で明示的に戻り値を指定しない場合などはundefinedが返る。
####### Constructor
- Syntax:
  new Function ([arg1[, arg2[, ...argN]],] functionBody)
- 一般的にFunction()コンストラクタを直接使用しない。
  eval()を使って関数本体を解析するため、無駄なオーバーヘッドが発生するとみなされるため。
  また、コンストラクタで生成された関数はクロージャを生成せず、スコープチェーンにはグローバルスコープのみが与えられる。
  new演算子を用いる場合と用いない場合で、動作は変わらない。
####### Function Object
######## Properties
######### Function.arguments
- 非推奨。代わりにargumentsオブジェクトを使用する。  
######### Function.length
####### Function Instance
######## Properties
######## Metohds
######### Function.prototype.apply()
- Syntax :
  fun.apply(thisArg[, argsArray])
- thisArgをthisとしてfunに渡す。
  Arrayの形で、argsArrayを引数として取る。
######### Function.prototype.call()
- Syntax :
  fun.call(thisArg[, arg1[, arg2[, ...]]])
- thisArgをthisとしてfunに渡す。
  カンマ区切りの引数を取る。
######### Function.prototype.toString()
- Syntax :
  function.toString(indentation)
- 関数のソースコードを表す文字列を返す。
  Object.prototype.toStringメソッドを上書きする。
  Geckoではindentationは禁止。
####### Memo
######## this, argumnets
- thisとargumentsはすべての関数本体で利用できる。
###### Boolean
###### Symbol
###### Error
####### EvalError
####### InternalError
####### RangeError
####### ReferenceError
####### SyntaxError
####### TypeError
####### URIError
##### Numbers and dates
###### Number
###### Math
####### 
###### Date
##### Text processing
###### String
###### RegExp
##### Indexed collections 索引付きコレクション
###### Array
- Literal : [value, ... ]
####### Array Object
######## Properties
######### Array.legth
######### Array.prototype
######## Methods
######### Array.from()
- 配列型(array-like)や反復型(iterable)オブジェクトから、新しいArrayインスタンスを生成する。
######### Array.of()
####### Array Instance / Array.prototype
######## Properties
######### Array.prototype.constructor
- オブジェクトのprototypeを生成する関数を指定する。
######## Methods
######### Mutator methods 変更メソッド
########## Array.prototype.push()
- 配列の最後に1個以上の要素を追加し、新しい配列の長さを返す。
########## Array.prototype.sort()
- 配列内で要素を整列し、配列を返す。
########### Syntax
- arr.sort([compareFunction])
  
######### Accessor methods アクセサメソッド
########## Array.prototype.join()
- 配列の全ての要素を結合した文字列を返す
######### Iteration methods 反復メソッド
###### Int8Array
###### Uint8Array
###### Uint8ClampedArray
###### Int16Array
###### Int32Array
###### Uint32Array
###### Float32Array
###### Float64Array
##### Keyed collections
###### Map
###### Set
###### WeakMap
###### WeakSet
##### Vector collections
###### SIMD
####### SIMD.Float32x4
####### 
##### Structured data
###### ArrayBuffer
###### DataView
###### JSON
##### Control abstraction objects
###### Promise
###### Generator
###### GeneratiorFunction
##### Reflection
###### Reflect
###### Proxy
##### Internationalization
###### Intl
##### Other
###### arguments
#### Statements 文と宣言
##### Control flow 制御フロー
###### Block ブロック
- 0個以上の文をグループ化するのに使う。波括弧で囲む。
###### break
- 現在実行中のループ、switchによる分岐、あるいはラベル文を終了し、その終了した文に続く文へとプログラムの制御を移行する。
###### continue
- 現在実行中のループ、またはラベル付きループで現在反復している文の実行を終了し、そのループの実行を次の反復から継続する。
###### Empty 空文
- 文が必要ないがJavaScriptの文法上1つの文が必要な場合に用いる。
- 構文
  ;
###### if...else
- 与えられた条件が真の場合はある文を実行する。条件が偽の場合はまた別の文を実行できる。
###### switch
- ある式を評価し、式の値をケース節と照らし合わせ、ケース節に関連付けられた文を実行する。
- 構文
  switch (expression) {
    case value1:
      // statement
      [break;]
    case value2:
      // statement
      [break;]
    ...
    case valueN:
      // statement
      [break;]
    default:
      // statement
      [break;]
  }
###### throw
###### try...catch
##### Declarations 宣言
###### var
- 変数を宣言し、その変数を初期化することもできる。
###### let
- ブロックスコープを持つ局所変数を宣言し、その変数をある値に初期化することもできる。
  (ES6以降)
###### const
- 読み取り専用の名前付き定数を宣言する。
  (ES6以降)
##### Functions and classes
###### function
###### function*
###### return
- 関数によって返される値を指定する。
  関数内でreturn文を呼び出すと、関数の実行が停止する。
###### class
##### Iterations
###### do...while
###### for
###### for...in
- オブジェクトの列挙可能(enumerable)なプロパティに対し任意の順番で反復処理を行う。
- 構文
  for (variable in objcet) {... }
- 対象オブジェクトのプロパティだけでなく、継承したプロパティも列挙する。
###### for...of
###### while
##### Others
###### debugger
###### export
###### import
###### label
#### Expressions and operators 式と演算子
##### Primary expressions 基本式
###### this
- 関数の実行コンテキストを参照する。
###### function
- 関数式を定義する
###### class
- クラス式を定義する
###### function*
- ジェネレータ関数式を定義する
###### yield
###### yield*
###### []
###### {}
###### /ab+c/i
###### ()
##### Left-hand-side expressions 左辺式
###### Property accessors
###### new
- コンストラクタのインスタンスを作成する。
  プリミティブ型のコンストラクタの場合、newとつけるとObject型、つけないとプリミティブ型として動作する。
  - 例: myNum1 = Number(); //Number
        myNum2 = new Number(); //Objcet
###### new.target
###### super
###### ...obj
##### Increment and decrement
###### A++
###### A--
###### ++A
###### --A
##### Unary operators 単項演算子
###### delete
- オブジェクトからプロパティを削除する。
  指定されたオブジェクトのみで機能し、プロトタイプチェーンで継承するプロパティは削除しない。
  varで宣言した変数やfunction文で宣言した関数には適用されない。
- deleteメソッドで配列の要素を削除することも可能。その場合、値はundefinedとなりlengthは維持される。
- 例:
  delete foo.bar // fooオブジェクトのbarプロパティを削除する
###### void
###### typeof
- 与えられたオブジェクトの型を判別する
- 例
  typeof myNumber; // "myNumber"の型を判断する。number, objectなど
###### +
###### -
###### -
###### !
##### Arithmetic operators
###### +
###### -
###### /
###### *
###### %
###### **
##### Relational operators 関係演算子
###### in
- 与えられたプロパティをオブジェクトが持っているかどうか判断する。
- 例:
  'bar' in foo // fooオブジェクトがbarプロパティを持っていればtrue
###### instanceof
- オブジェクトが別のオブジェクトのインスタンスかどうか判断する。
- 注意
  - Objectインスタンスの判定をする場合、全てのオブジェクトはObject()を継承しているため、常にtrueとなる。
  - オブジェクトのみに使用できる。プリミティブ値がラッパーオブジェクトを使用する際、instanceof演算子はfalseを返す。
- 例
  console.log(new Array('foo') instanceof Array)
###### <
###### >
###### <=
###### >=
##### Equality operators
###### ==
###### !=
###### ===
###### !==
##### Bitwise shift operators
###### <<
###### >>
###### >>>
##### Binary bitwise operators
###### &
###### |
###### ^
##### Binary logical operators
###### &&
###### ||
##### Conditional (ternary) operator
###### (condition ? ifTrue : ifFalse)
##### Assignment operators
###### =
###### *=
###### /=
###### %=
###### +=
###### -=
###### <<=
###### >>=
###### >>>=
###### &=
###### ^=
###### |=
###### [a, b] = [1, 2],  {a, b} = {a:1, b:2} 
- Destructurning assignment, 分割代入
  配列かオブジェクトからデータをおtり出して別個の変数に代入することを可能にする構文。

####### Syntax
- 前提: var a, b, rest
- [a, b] = [1, 2]
- [a, b, ...rest] = [1, 2, 3, 4, 5]
- ({a, b} = {a:1, b:2})
- ({a, b, ...rest} = {a:1, b:2, c:3, d:4})
  ※Firefox 47a01では未実装
  
##### Comma operator
###### ,
#### Functions 関数
##### arguments
- 関数へ渡された引数に対応するArrayのようなオブジェクト。Arrayとは異なる。
  すべての関数内で利用可能なローカル変数。
###### Properties
####### arguments.callee
- 現在実行している関数を示す
####### arguments.caller
- 現在実行している関数を呼び出した関数を示す。
####### arguments.length
- 定義されたパラメータの数でなく、実行時に実際に渡された引数の数を返す。
  定義上は2つの引数を定義していても、3つの引数を呼び出し時に渡した場合は"3"を返す。
##### Arrow functions アロー関数
- 
  匿名関数。function式と比べてより短い構文を持ち、thisの値を語彙的に束縛数r。
  
###### 構文
- (param1, param2, ..., paramN) => { statements }
- expression
  - (param1, param2, ..., paramN) => expressoin
    // => { return expression; } と等価
- 引数が一つの場合、()は任意
  - singleParam => { statements }
  - (singleParam) => { statements }
- 引数を取らない場合、()は必須
  - () => { statements }

- Objectリテラル式を返す場合、本体を()で囲む
  - params => ({foo: bar})
- restとデフォルト引数
  - (param1, param2, ...rest) => { statements }
  - (param1 = defaultValue1, param2, ..., paramN = defaultValueN) => { statements}
- 分割代入
  - var f = ([a, b] = [1, 2], {x: c} = {x: a + b}) => a + b + c;
##### Default parameters
##### Rest parameters 残余引数
- 
  不特定多数の引数を配列として表す。
  関数の最後の名前付き引数に"..."の前置辞を付けると、実際に関数に渡された残りの引数による要素の配列となる。
  
###### Syntax
- function(a, b, ...theArgs) {
    // ...
  }
#### Classes クラス
#### Web APIs
- https://developer.mozilla.org/en-US/docs/Web/API
- [[https://developer.mozilla.org/ja/docs/DOM/DOM_Reference][DOMリファレンス - MDN]]
##### Console
###### About
- ブラウザのデバッグコンソールへアクセスする機能を提供する。
  標準化された仕様でなく詳細な動作はブラウザによって異なるが、一般的に共通の機能セットがサポートされる
###### Methods
####### Console.assert()
####### Console.clear
####### Console.debug()
- log()の別名
####### Console.dir() --非標準
- 指定したJavaScriptオブジェクトプロパティの、対話型リストを表示する。
####### Console.error()
- エラーメッセージを出力する
####### Console.group()
- 以降の出力を別のレベルにインデントする、新たなインライングループを作成する
####### Console.groupEnd()
- インライングループから抜ける
####### Console.info()
- メッセージタイプのログ情報を出漁
####### Console.log()
- Output a message to the Web Console.
####### Console.table()
- 表形式のデータを、テーブルを使用して表示する。
####### Console.time()
####### Console.timeEnd()
####### Console.trace()
- スタックトレースを出力する
####### Console.warn()
- 警告メッセージを出力する
###### Link
- MDNでなくChrome版
  [[https://developers.google.com/web/tools/chrome-devtools/console/console-reference?utm_source=dcc&utm_medium=redirect&utm_campaign=2016q3#consolegroupobject-object][Console API Reference - Tools for Web Developers]]
##### Document
###### Properties
####### Extension for HTML document
######## Document.cookie
- 
  documentのcookieのセミコロンで区切られたリストを返すか、一つのcookieを設定する。

######## Document.location
- 
  現在のdocumentのURIを返す。

######## Document.readyState
- 
  読み込み中の場合"loading",
  パースが完了したがサブリソースが読み込み中の場合"inactivate",
  サブリソースの読み込みも完了した時点で"complete"となる。

###### Methods
####### document.getElementsByClassName()
- 
  引数で与えられたclass名を持つエレメント群のリストを返す。
  
####### document.getElementsByTagName()
- 
  引数で与えられたタグ名を持つエレメント群のリストを返す。

####### document.getElementById(String id)
- 
  特定のidを持つエレメントへのオブジェクト参照を返す。

####### document.querySelector(String selector)

####### document.querySelectorAll(String selector)
####### Extentions for HTML document
######## document.close()
- 書き込み用のドキュメントストリームを閉じる
######## document.open()
- 書き込み用のドキュメントストリームを開く
######## document.write(String text)
- ドキュメントにテキストを書き込む
######## document.writeln(String text)
- ドキュメントにテキスト行を書き込む
##### Event
##### EventTarget
- イベントを受け取り、そのためのリスナーを持つ可能性があるオブジェクトにより実装さえたインターフェース。
  Element, document, windowが一般的なイベントターゲットだが、他のオブジェクトもインデントターゲットになり得る。
###### Methods
####### EventTarget.addEventListener()
- EventTarget上に特定のイベント種別のイベントハンドラを登録する。
######## Syntax
- target.addEventListener(type, listener[, options]);
- target.addEventListener(type, listener[, userCapture]);
- target.addEventListener(type, listener[, userCapture, aWantsUntrusted]); // Gecko/Mozillaのみ
######## Parameters
- type
  対象とするイベントの種類を表す文字列
- listener
  指定されたタイプのイベントが発生するときに受け取るオブジェクト。
  EventListenerインターフェースを実装するオブジェクトか、JavaScriptの関数である必要がある。
- options
  対象のイベントリスナーの特性を指定する、オプションのオブジェクト。
  - capture : trueを指定すると、DOMツリーで下に位置する任意のEVentTargetに発送される前に、登録したリスナーに発送される。
  - once : listenerが追加後にたかだか1回しか実行されないことを{jsxref("Boolean")}値で指定する。
    trueを指定するとlistenerは一度実行された時に自動的に削除する。
  - passive : listenerがpreventDefault()を呼び出さないことを表すBoolean値。
    trueを指定すると、ユーザーエージェントは呼び出しを無視し、コンソールに警告を出力する。
  - mozsystemgroup : (標準化されていない)
- useCapture
- WantsUntrusted
####### EventTarget.removeEventListener()
- EventTargetからイベントリスナーを削除する。
####### EventTarget.dispatchEVent()
##### History
- The History interface allows to manipulate the browser session history,
  that is the pages visited in the tab or frame that can current page is loaded in.

###### Methods

####### Properties
######## History.length
######## History.satte
####### Methods
######## History.back()
- 
  Goes to the previous page is session history.
  The same action as when the user clicks the browser's Back button.
  Equivalent to history.go(-1).

######## History.forward()
- 
  Goes to the next page in session history.
  Equivalent to history.go(1).

######## History.go()
- 
  Loads a page from session history, identified by its relative location to the current page.

##### HTMLElement
- https://developer.mozilla.org/ja/docs/Web/API/HTMLElement
###### About
###### Properties
####### HTMLElement.style
- 要素のstyle属性の宣言を表すCSSStyleDeclaration。
###### Methods
###### Events
##### Window
- [[https://developer.mozilla.org/ja/docs/Web/API/Window][window - MDN]]
###### Property
####### Window.console
####### Window.document
- 指定ウィンドウが含む文書への参照を返す
####### Window.history
- historyオブジェクトへの参照を返す
####### Window.location
- windowオブジェクトのロケーション、または現在のURLを取得/設定
####### Window.status
- ブラウザ下部のステータスバーのテキストを取得/設定
###### Method
####### Window.alert()
- 警告ダイアログを表示
####### Window.close()
- カレントウィンドウを閉じる
####### Window.find()
- ウィンドウ内で文字列を検索する
###### Event handler
####### WindowTimers.clearInterval()
- 
  setIntervalを使用して設定された繰り返し動作をキャンセルする。
  ex: window.clearInterval(intervalID)
####### WindowTimers.setInterval()
- 
  一定の遅延間隔を置いて関数を繰り返し呼び出す。
  ex: intervalId = window.setInterval(animate, 500)
####### WindowTimers.setTimeout()
###### Constractor
##### WindowOrWorkerGlobalScope (mixin)
###### Properties
###### Methods
####### WindowOrWorkerGlobalScope.setInterval()
###### Implemented by
- Window
- WorkerGlobalScope
##### Worker
- バックグラウンドで行われるタスクを実行することができる。そのタスクは簡単に生成され、作成元にメッセージを送り返すことができる。
##### XMLHttpRequest
###### Methods
####### abort()
- リクエストが既に送信されている場合、リクエストを中止する。
####### open()
- def
  void open(
    DOMString method,
    DOMString url,
    optional boolean async,
    optional DOMString user,
    optional DOMString password
  );
- argment
  - method : 使用するHTTPメソッド。"GET", "POST", "PUT", "DELETE"など。
  - url : リクエストを送信するURL
  - async : 非同期で操作を実行するかを示す、オプションの真偽値。
  - user : 認証を目的として使用される、ユーザー名のオプション。
  - password : 認証を目的として使用される、パスワードのオプション。

- リクエストを初期化する。
####### send()
- 
  リクエストを送信する。非同期リクエストの場合、メソッドはリクエストを送信して間もなく返る。
  同期リクエストの場合はレスポンスが到着するまで返らない。

###### Properties
####### XMLHttpRequest.onreadystatechange
- readyState属性が変更する都度呼び出されるEventHandler。
####### XMLHttpRequest.readyState
- 
  リクエストの状態をunsigned short型の値で返す。
  
- 
  |-------+------------------+------------------------------------------------------------|
  | value | state            | expression                                                 |
  |-------+------------------+------------------------------------------------------------|
  |     0 | UNSENT           | open()がまだ呼び出されていない                             |
  |     1 | OPENED           | send()がまだ呼び出されていない                             |
  |     2 | HEADERS_RECEIVED | send()が呼び出され、ヘッダーとステータスが通った。         |
  |     3 | LOADING          | ダウンロード中。responseTextは断片的なデータを保持している |
  |     4 | DONE             | 一連の動作が完了した                             |
  |-------+------------------+------------------------------------------------------------|
  
####### XMLHttpRequest.responseText
- リクエストに対するテキスト形式でのレスポンスを含むDOMStringを返す。
  リクエストの失敗または未送信の場合はnullとなる。
####### XMLHttpRequest.state
###### Event
####### onreadystatechange
###### Memo
- JSなどウェブブラウザ搭載のスクリプト言語でサーバとのHTTP通信を行うためのAPI。Ajaxの基幹技術。
- ページ全体を更新する必要なしに、データを受け取ることができる。
  名前はXMLHttpRequestだが、XMLだけでなくあらゆる種類のデータを受け取ることができ、HTTP以外の(fileおよびftp含む)プロトコルにも対応している。
#### Misc.
##### Lexical grammer 字句文法
###### Control characters 制御文字
###### White spaceホワイトスペース
###### Line terminators ラインターミネータ
###### Comments コメント
###### Keywords キーワード
###### Literal リテラル
####### Null literal / NULLリテラル
- null
####### Boolean literal / Booleanリテラル
- true
- false
####### Numeric literal / Numericリテラル
######## Decimal
######## Binary
######## Octal
######## Hexadecimal
####### Object literals / オブジェクトリテラル
- 
  プロパティ名とそれに関連付けられたオブジェクトの値との0個以上の組が波括弧{}で囲まれたもの。

- ex)
  var car = { myCar: "Saturn", getCar: carTypes("Honda"), special: sales };
####### Array literals 配列リテラル
####### String literals /文字列リテラル
######## Hexadecimal escape sequences / 16進数エスケープシーケンス
######## Unicode escape sequences / Unicodeエスケープシーケンス
######## Unicode code point escapes / Unicodeコードポイントエスケープ
####### Regular expression literals / 正規表現リテラル
####### Template literals / テンプレートリテラル
###### Automatic semicolon insertion (ASI) / 自動セミコロン挿入
##### Data type データ型
###### Primitive プリミティブ型
####### Boolean
####### Number
####### String
####### Symbol
####### null
####### undefine
###### Object
##### hoisting 巻き上げ
- 
  関数内で宣言されたローカル変数は、すべてその関数の先頭で宣言されたものとみなされる。
  したがって、関数で使用されるローカル変数は、関数の先頭で宣言を行うようにすることで、間違いを視覚的に減らす。
- 巻き上げられた場合、変数定義はスコープの最初に行われるが、変数への代入は行われない。
  また、let/constは巻き上げが行われ、変数定義は行われるが、参照は実際の変数定義が行われるところまで行えない。

- ex
  var myname = "global";
  function func(){
    console.log(myname); // -> undefined
    myname = "local";
    console.log(myname); // -> "local"
  }
  ↓(以下と同じと解釈される)
  var myname = "global";
  function func(){
    var myname;
    console.log(myname); // -> undefined
    myname = "local";
    console.log(myname); // -> "local"
  }

### ECMAScript
#### ES5
### DOM
- [[file:DOM.org][DOM.org]]
### XMLHttpRequest
- [[https://xhr.spec.whatwg.org/][XMLHttpRequest - Living Standard]]
### data URIs
- data:スキームはデータをインラインで埋め込むことができる
  URLスキームなので、http: と似たような扱い。
#### Link
- https://developer.mozilla.org/ja/docs/data_URIs
- https://tools.ietf.org/html/rfc2397
### Memo
#### Objects
##### Properties
###### Data property
####### [ [Value] ]
####### [ [Writable] ]
####### [ [Enumerable] ]
- If true, the property will be enumerated in for...in loops.
- Type : Boolean
- Defalut : false
####### [ [Configurable] ]
###### Accessor property
####### [ [Get] ]
####### [ [Set] ]
####### [ [Enumerable] ]
- If true, the property will be enumerated in for..in loops.
- Type : Boolean
- Default : false
####### [ [Configurable] ]
#### Constructor コンストラクタ
- オブジェクトを作成し、初期化する関数オブジェクト(Functionオブジェクト)。
  それぞれのコンストラクタは、関連付けされたプロトタイプオブジェクトを持っていて、継承や共有プロパティを実装するために利用できる。
  また、同じコンストラクタから生成されたオブジェクトは、プロトタイプオブジェクトを共有する。
- constructorプロパティ
  - コンストラクタ関数を使ってオブジェクトを生成すると、constructorプロパティが自動生成される。
#### Property プロパティ
##### ドット記法、ブラケット記法
- 
  オブジェクトのプロパティは、ドット記法もしくはブラケット記法でアクセスできる。
  通常はドット記法を用いる。ブラケット記法は、どうしても使用しなければならない場合、使用した方が便利な場合などのみに利用を限定する。
  （プロパティ名を動的に作る場合や、不正なプロパティ名やjsの予約語のプロパティの場合など)
- 例:
  - ドット記法
    cody.living = true;
  - ブラケット記法
    cody["living"] = false;
- ブラケット記法が生きる例
  var foobarObject = { foobar: 'foobar'};
  var string1 = 'foo'; var string2 = 'bar';
  console.log(foobarObject[string1 + string2]);
  
##### 参照の解決
- オブジェクト内に存在しないプロパティにアクセスしようとする場合、常にプロトタイプチェーンを辿ってプロパティを探し当てようとする。
  
#### ホストオブジェクト
- Webブラウザ環境ではwindowsオブジェクトと、windowsオブジェクトに保持されているすべてのオブジェクト(ネイティブオブジェクトを除く)。
  ECMAScript標準の一部ではなく、JavaScript言語仕様とホストオブジェクトの間には何も関係がない。
## Grammer 文法
### Fundamentals Memo
- 文の終了は;(Semicolomn)
- 文字列は"か'で囲む
- コメントは、一文は//、複数行は/* */。
- 変数
  - 宣言はvar, let(ブロックスコープ), const(定数)。
    何も付与しないと常にグローバル変数として遷延される。
  - ES6以前にはブロック文のスコープがない。
    ブロックスコープを利用するにはletを利用する。
  - 変数の巻き上げ(hoisting)が行われる。
  - グローバル変数は、実際にはグローバルオブジェクト(Webページではwindow)のプロパティ。
    window.varでアクセス可能。
- データ型
  - 6つのプリミティブ型とオブジェクト型の7つの型が定義されている。
    - Boolean, null, undefined, Number, String, Symbol, およびObject。

- 演算の省略形として、+=, ++なども使用可能。
- 配列は、var names = [a, b, c, ...]; という形式。
- 連想配列は、var key = { };
- user["name"]と、user.nameは同じ。
- データ型 : 

### W3C
#### Syntax
##### Loop
###### for(;;)
###### for( in )
###### while()
###### do...while()
###### break
###### continue
###### try, catch, throw

#### Function
##### Popup
###### alert
###### confirm
###### prompt

#### Event
##### onload
##### onunload
##### onfocus
##### onblur (when losing focus)
##### onchange
##### onsubmit
##### onmouseover
##### onmouseout

#### Object
##### Document
##### String
###### length
###### toUpperCase()
##### Date
##### Array
##### Boolean
##### Math
##### RegExp
##### Navigator

#### Developer Tool
##### Ctrl-Shift-J or F12

## Edition
### ECMAScript 4
- 標準化作業が分裂したため2008/8に破棄された
### ECMAScript 5 (2009)
- 2009年に標準化
### 5.1
### 6, 2015
- 2015/6/17公開
  
### 2016(7)
- 基本的には、ES6(2015)のバグ修正。加えて、2016/1にStage4となっているProposalが入る。

### 2017(8)
## Tools
### Exec Command
#### osascript (Mac)
- osascript -l JavaScript Sample.js
#### wscript (Win)
- wscript sample.js
#### cscript (Win)
- cscript sample.js
#### on browser
#### node
- node sample.js
### Modules
#### jQuery
- [[file:jQuery.org][jQuery.org]]
#### Underscore.js
- [[file:Underscorejs.org][Underscorejs.org]]
#### node.js
- [[file:Nodejs.org][Nodejs.org]]
#### npm
- node package manager
##### Documentation
- https://docs.npmjs.com/
###### CLI Commands
####### npm
######## Synopsis
- npm <command> [args]

####### access
####### adduser
####### audit
####### bin
####### bugs
####### build
####### bundle
####### cache
####### ci
####### completion
####### config
####### ls
####### install
- Install a package

######## Synopsis
- npm install (with no args, in package dir)
- ...
- npm install <tarball url>
- npm install <folder>

######## Alias
- npm i

######## Options
######### --dry-run
######### -f, --force
######### -g, --global
- 
  npm to install the package globally rather than locally.

####### update
- Update a package
######## Synopsis
- npm update [-g] [<pkg> ...]
######## Aliases
- up
- upgrade
######## Flags
######### -g
- this command will update globally installed packages.
###### Using npm
###### Configuring npm
##### Link
- [[https://www.npmjs.com/][npm]]
- [[https://docs.npmjs.com/][docs - npm]]

#### npm Modules
##### browserify
- browser-side require() the node way
##### EJS
- テンプレートエンジン
###### Docs
####### Options
####### Tags
- <%  : 'Scriptlet' tag, for control-flow, no output
- <%= : Outputs the value into the template (HTML escaped)
- <%- : Outputs the unescaped value into the template
- <%# : Comment tag, no execution, no output
- <%% : Outputs a literal '<%'
- %>  : Plain ending tag
- -%> : Trim-mode ('newline slurp') tag, trims following newline
####### Includes
###### Link
- [[http://ejs.co/][EJS]]
##### Express
- Fast, unopinionated, minimalist web framowork for Node.js
  軽量フレームワーク。
###### 4.x API
####### express()
- Creates an Express aplication.
  express() function is a top-level function exported by the express module.
- Usage
  var express = require('express');
  var app = express();
######## Methods
######### express.static(root, [options])
- only built-in midleware function in Express.
  It serves static files and is based on serve-static.
######### express.Router([options])
- Creates a new router object
- Usage
  var router = express.Router([options]);
####### Application
- The app object convertionally denotes the Express application.
  Create it by calling the top-level express() function exported by the Express module
######## Properties
######## Events
######## Methods
######### app.get(name)
######### app.get(path, callback [,callback ....])
- Routes HTTP GET requests to the specified path with specified callback functions.
######### app.listen(port, [hostname], [backlog], [callback])
- Binds and listens for connections on the specified host and port.
####### Request
######## Properties
######## Methods
####### Response
######## Properties
######## Methods
####### Router
######## Methods
###### License
- Apache License, version 2.0
###### Link
- [[http://expressjs.com/][Express]]
##### hexo
- A fast, simple & powerful blog framework
- https://hexo.io/
##### nodegrind
- Profile nodejs applications with kcachegrind
- https://www.npmjs.com/package/nodegrind
##### Socket.io
#### yarn
#### Babel
#### React
##### Link
- [[https://facebook.github.io/react/docs/getting-started-ja-JP.html][QUICK START(日本語)]]
- [[https://facebook.github.io/react/docs/getting-started-ja-JP.html][始めてみましょう - React]]
#### AngularJS
##### Link
- [[https://angularjs.org/][AngularJS]]
- [[http://js.studio-kingdom.com/angularjs/guide/introduction][AngularJS入門 - js STUDIO]]
#### Electron
#### Vue.js
##### Link
- http://kakakakakku.hatenablog.com/entry/2018/02/18/113426
#### Lint
##### ESLint
- Pluggable linting utility
###### Link
- [[http://eslint.org/][ESLint]]
##### JSLint
###### Directives
####### /*global*/
####### /*Jslint*/
######## bitwise
######## browser
- Assume a browser
  - true if the standard browser globals should be predefined.
  - document, history, clearIntervalなどのブラウザキーワードの許可。
######## couch
######## devel
- Assume in development
  - true if browser globlas that are useful in development should be predefined.
  - devel, alertなどの開発キーワードの許可
######## es6
######## eval
######## for
######## fudge
######## maxerr
######## maxlen
######## multivar
######## node
######## single
######## this
######## white
####### /*property*/
###### Link
- [[http://www.jslint.com/][JSLint]]
- [[http://www.jslint.com/help.html][Help - JSLint]]
##### JSHint
### Classification 分類
#### MVC
- Backbone.js
#### MVVM
- AngularJS
- Vue.js

#### Virtual DOM
##### About
- 
  [[http://qiita.com/mizchi/items/4d25bc26def1719d52e6][なぜ仮想DOMという概念が俺達の魂を震えさせるのか - Qiita]]
##### React
##### Flux
#### DOM操作
- jQuery

#### テンプレートエンジン
- Underscore.js

#### Webグラフィックス
- three.js
- D3.js

#### altJS
##### CoffeeScript
##### TypeScript
##### Dart
##### Haxe
##### JSX
- 
  DeNAによって開発された。

##### Scala.js
##### Link
- [[http://pepabo.github.io/docs/frontend/standard/javascript-and-altjs.html][JavaScriptとaltJS - pepabo.github.io]]

#### ServerSide
- Node.js
- Rhino

#### Transpile
##### Babel
- 
  ECMAScript2015(ES6)やECMAScript7で書かれたコードを、
  一般的なブラウザがサポートしているEcmaScript5の形式に出力する。

- 
  [[https://html5experts.jp/kyo_ago/16979/][Babelで始める！モダンJavaScript開発 - HTML5 Experts.js]]

#### Package Management
- npm
- bower
  ブラウザ環境のためのパッケージ管理ツール。ブラウザ版npmのようなもの。
#### Module system
- Browserify
- RequireJS
- WebPack
  CommonJSとAMDの両方のスタイルを同時にサポートするのが特徴。
#### Test
- QUnit
- Jasmine

#### WebComponents
##### About
- [[https://www.w3.org/standards/techs/components#w3c_all][WEB COMPONENTS CURRENT STATUS - W3C]]
- [[http://postd.cc/the-state-of-web-components/][Web Componentsの現状 - POSTD]]
- [[http://www.h2.dion.ne.jp/~defghi/webc/webc.htm][Web Copmonetsの基本的な使い方・まとめ]]
- [[http://www.h2.dion.ne.jp/~defghi/webc/webc.htm][Web開発者に革命をもたらす!「Web Components」超入門 - LIG.inc]]
### Link
- [[http://iwasiman.hatenablog.com/entry/2018/04/23/200000][【JavaScript】３大フレームワーク Angular, React, Vue.jsを比べてみよう (2018年4月) - Rのつく財団入り口]]
## Coding Standard
### SPA/mmikowski
- [[https://github.com/mmikowski/spa/blob/master/js-code-standard.pdf][JavaScript code standard]]
## Glossary
## Reverse lookup
### 全置換を行う
- replaceを行うと単に最初の値を置換する。
- 1. 正規表現でgタグを使う。
  - "a b c".replace(/ /g, '-');
- 2. splictしてjoinする。
  - "a b c".split(' ').join('-');
- http://marycore.jp/prog/js/replace-all/
### 匿名関数の即時実行
- 
  (function(){
    //関数
  })();

#### その他の記号
- ()で囲まず、!,+,-,~などでも実行可能。
  !function(){console.log("do")}();など。
  https://qiita.com/ukiuni@github/items/5f3d8620187905aea3d4
## Memo
### API仕様
#### CommonJS
- サーバサイドを開発するために生まれた標準APIの仕様で、元はServerJSという名前だった。
  その後他の分野に適用可能と考えCommonJSに改めた。
  モジュール機能が定義されており、require関数を使い、exportsとmoduleオブジェクトを利用する。
#### AMD
- Asynchronous Module Definition
  モジュールの非同期定義に関するAPI仕様。
  モジュールとそのモジュールに依存する他のモジュールの両方を非同期に読み込めるようモジュール定義がされている。
  元々はCommonJSで策定が進められていたが、後に切り離された。
#### UMD
- Universal Module Definition
  CommonJSとAMDの両方を含めたモジュール定義で、このフォーマットによりクライアントとサーバの両方の環境で動作するモジュールを定義できる。
### 標準スクリプト言語の指定
- 
  HTML4.01までは、以下の記述によりonclickなどで使われる標準のスクリプト言語指定が推奨されていたが、
  HTML5ではデフォルトがjavascriptとなり、設定不要に。
  <meta http-equiv="Content-Script-Type" content="text/javascript">

### 変換
- 
  int.toString(2)  // 2進数へ変換
  int.toString(16) // 16進数へ変換
  parseInt(bin,2)  // 2進⇒10進数へ変換
  parseInt(hex,16) // 16進⇒10進数へ変換

### Math
- 
  Math.random  // 0以上1未満の乱数を取得。
  ex:
      Math.floor(Math.random * 10) // 0以上10未満の自然数を取得
      Math.ceil(Math.random * 10)  // 0以上10以下の自然数を取得、気持ち0含まない。

  Math.pow(x,y) // xのyべき乗

### 条件付コメント
- 
  IEのバージョン5からバージョン9まででサポートされている構文。
  ex) <!--[if lt IE 9]>
  上記はIEのバージョンが9より小さい場合に、コメント内部を実行する条件。

### トラッキングコード
- 
  [[http://web-tan.forum.impressrd.jp/l/6342][Googleアナリティクスとは／衣袋教授のGoogleアナリティクス入門講座 コーナーの記事一覧 - Web担当者Forum]]

### Modal Window モーダル（用語）
- 
  何らかのウインドウの子ウィンドウとして生成され、
  ユーザーがそれに対して適切に応答しない限り、制御を親ウィンドウに戻さないユーザインターフェイス設計になっているもの。
  
### ブラウザ上でのJavaScriptの簡単な実行方法
- 管理者ツールのconsoleを利用する
  管理者ツールを立ち上げて、consoleを利用する。
  
### プロトタイプチェーン、スコープチェーン
- プロパティ（メソッド）など、オブジェクトの所有する値はプロトタイプチェーン、
  変数（関数？）などはスコープチェーンで解決するのではないか、と思われる。
### 「型」を取得する
- typeof <object>
- toString.call(<object>);
- <object>.constructor
- https://qiita.com/south37/items/c8d20a069fcbfe4fce85
### ==と===の違い
- == : 等価演算子
  数値と文字列を比較する場合、文字列は数値に変換される。
- === : 厳密等価演算子
  オペランド同士が肩を変換することなく比較される
- https://qiita.com/PianoScoreJP/items/e43d70ec188c6fed73ed
### strictモード
- "use strict";
- EMCAScript 5以降。厳格モード。
  エラーでないが落とし穴になる事柄をエラーに、また最適化を困難にする誤りを修正する。
- strict/not strictの違い
  - 構文エラー
  - 新しいランタイムエラー
    - 日宣言変数への値設定
    - 設定不可能なプロパティの削除
    - ポイズン引数と関数プロパティ
  - 意味的な違い
    - 関数呼び出しでのthin
    - argumentsが名前付きの関数の引数をエイリアスしない
    - evalへの変更

- https://developer.mozilla.org/ja/docs/Web/JavaScript/Strict_mode
- https://developer.mozilla.org/ja/docs/Web/JavaScript/Strict_mode/Transitioning_to_strict_mode
### コンストラクタ
- newをつけて関数を呼び出す
- newをつけた場合、暗黙的に以下のコードが追加される。
  - var this = {};
  - return this;
- 明示的に記述する場合は以下
  - var self = {};
    self.name = name;
    self.bark = function() {...};
    return self;
  - 明示的にreturnをしているため、thisの暗黙のルールは適用されなくなる。
- コンストラクタはただの関数。newをつけずに実行すると、関数のため内部のthisはグローバルオブジェクトをさす。
  そのため、グローバルスコープに変数などが定義されてしまう。
- コンストラクタ呼び出しを期待する場合、最初の文字を大文字で書くのが慣例。
  - MyObjcet()、など。

- [[https://qiita.com/takeharu/items/010752b1427773558f7c][JavaScriptのクラス？コンストラクタ？？ @takeharu - Qiita]]
- [[https://qiita.com/takeharu/items/9935ce476a17d6258e27][JavaScriptの「this」は「4種類」？？ @takeharu - Qiita]]
## Link
- [[http://www.ecma-international.org/publications/standards/Ecma-262.htm][Standard ECMA-262 - ecma INTERNATIONAL]]
- [[https://dom.spec.whatwg.org/#interface-document][DOM - Living Standard]]

- MDN
  - [[https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide][JavaScript Guide - MDN]]
  - [[https://developer.mozilla.org/ja/docs/Web/JavaScript/Guide][JavaScriptガイド - MDN]]
  − [[https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference][JavaScript reference - MDN]] 
  - [[https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference][JavaScriptリファレンス - MDN]]
  - [[https://developer.mozilla.org/ja/docs/Web/JavaScript/JavaScript_technologies_overview][JavaScript技術概説 - MDN]]
  - [[https://developer.mozilla.org/ja/docs/Web/API][Web APIインターフェース - MDN]]

- [[http://speakingjs.com/][Speaking JavaScript: An In-Depth Guide for Programmers]]

- [[http://qiita.com/mizchi/items/3bbb3f466a3b5011b509][春からはじめるモダンJavaScript / ES2015 - Qiita]]
- [[http://www.slideshare.net/yuka2py/javascript-23768378][最強オブジェクト指向言語 JavaScript 再入門！ - SlideShare]]
- [[http://azu.github.io/slide/nodejs-es6/how-to-learn.html][どうやってECMAScrit6を学び始めるか]]

- [[https://postd.cc/how-to-become-a-great-javascript-developer/][優秀なJavaScriptの開発者になるための5か条 - POSTD]]

- [[https://gist.github.com/azu/027859e08e284cb8dfe7][JavaScriptのレベル別書籍のまとめ - azu/js.md]]
  - 初心者
    - 開眼！JavaScript
  - 中級者
    - Speaking JavaScript
    - Eloquent JavaScript
    - JavaScript Pattern
  - 上級者
    - O'Reilly JavaScript
    - Exploring ES6
    - You Don't Know JS
