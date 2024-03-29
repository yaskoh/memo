# Ruby
## Reference Manual
### Ruby言語仕様
#### オブジェクト
##### クラス
###### 定義
- class式
  クラスを定義するにはcalss式を使う。
  クラス名はClassオブジェクトを参照する定数であり、大文字から始める必要がある。

- 継承
  "<"に続けて他のクラスを指定すると、クラスを継承する。
  多重継承は不可。
  ex) class Test < Range

- インスタンスメソッド
  クラス内にdef式を書くとインスタンスメソッドとなる。

- クラスメソッド
  クラスメソッドは、クラス全体に属するメソッド。C++やJava, C#のstaticメソッドのようなもの。
  インスタンスを介することなく直接クラスから呼ぶことができる。
  クラス名あるいはselfをつけてメソッドを定義する。
  クラスオブジェクトの特異メソッド。
  ex)
    class Test
      def Test.print(x); p x end
      def self.print(x); p x end  # どちらもクラスメソッドとなる
    end

- インスタンス化
  クラスメソッドnewを使って初期化する。引数はインスタンスメソッドinitializeに渡る。
  initializeはインスタンスを構築した直後に自動で呼ばれる。

- 属性
  オブジェクトに属していて、取得・設定が可能な値のこと。
  - 定義
    Class#attr_accessorは属性メソッドを定義するメソッド。
    0個以上の文字列またはシンボルを受け取って、その名前の属性を定義する。
    getterとsetterを自動で作成してくれるようなもの。
    ex)
      attr_accessor :since, :until
      =>
      def since; return @since end
      def since=(value); @since = value end
      def until ...

    - attr_writer, attr_reader
      attr_writerは書き込み専用の属性を作成する。
      attr_readerは読み取り専用の属性を作成する。

- クラス定義の追加
  既存のクラスに対してclass定義式を記述すれば、暮らす定義をいつでも変更できる。
  上書きを禁止したい場合、Calss#freezeメソッドを使うと変更が禁止できる。

- スーパークラスの呼び出し
  super式を使うと親クラスの同名メソッドを呼び出せる。
  引数を渡さずsuperとだけ記述すると、現在のメソッドの引数をそのまま受け渡す。
  引数を一つも渡したくない場合は、super()と記述する。

###### 特異クラス
- 
  ある特定のインスタンスのためだけにあるクラス。
  class式においてクラス名の代わりに「<< (オブジェクト)」と記述する。
  このクラス式を評価したときから、元の(オブジェクト)は特異クラスに属することになる。
  ex)
    CR = Object.new
    class << CR
     def ...

- メタクラス
  特異クラスはクラスのクラスとなるので、メタクラスと呼ばれる。
  一般に、「Classオブジェクトの特異クラス」がメタクラス。

##### モジュール
###### Mix-in
- 
  クラスの多重継承は弊害が大きいので禁止するが、
  その代わりにModuleを複数継承できるようにすることで柔軟な対応が行える。
  Moduleを継承することをincludeする、という。
  モジュールはインスタンス化できない。
  ancestorsメソッドで継承したモジュールやクラスが確認できる。

###### 名前空間
- 
  名前の衝突を避けるため、Rubyではモジュールを使う習慣がある。
  ex)
    class Service; end
    module Library
      class Service; end
    end
    ::Service            #=>トップレベルのService
    Library::Service     #=>Libraryモジュールに属しているService

##### メソッド
###### 呼び出し
- メソッド呼び出しの形式
  メソッド呼び出しはレシーバ、メソッド名、引数の順番に並べる。下のどちらの方式でも良い。
  ex) a.some_method(1, "str")
      a::some_method(1, "str")

- 括弧の省略
  引数と括る括弧は、曖昧さを生まない限り省略可能。

- メソッドチェーン
  戻り値に対して連続してメソッドを呼ぶこと。
  ex) str.gsub(/&/, '&amp;').gsub(/</, '&lt;').gsub(/>/, '&gt;')

- レシーバの省略
  レシーバを章楽すると、デフォルトのレシーバselfに対してメソッドを呼び出すことになる。
  また、privateメソッドは常にレシーバ省略形式で呼び出す必要がある。
  
  レシーバ省略した引数を持たないメソッドは、ローカル変数と見分けがつかない場合があるが、
  その場合はローカル変数が優先される。

- 関数的メソッド
  レシーバに含まれる情報を利用しないため、非オブジェクト指向的な関数やサブルーチンと似たような形式のもの。

- 呼び出し時の探索
  1. 特異メソッド
  2. 属するクラスのインスタンスメソッド
  3. includeしたモジュールのインスタンスメソッド
  4. 1-3で見つからない場合、親クラスに遡ってインスタンスメソッドを探す。
  5. クラス最上位まで見つからなかった場合、Object#method_missingを呼び出し、NoMethodError例外を発生させる。

- オーバーロード
  引数の数や型によるオーバーロードは行われず、単純にメソッド名のみで行われる。
  代替手段として、可変長引数で引数を受け、その長さによって挙動を変えることが行われている。

###### 定義
- def
  メソッド定義にはdef式を用いる。
  一般にはメソッド内で最後に評価された式の値が戻り値となる。
- return
  明示的に戻り値を返す際にreturnを使う。
  返り値を省略した場合はnilが返る。
  
  カンマ区切りで多値を返すこともできる。
  各々の式を評価した結果が配列で帰るので、受け取り側では多重代入のように多値として受け取ることができる。

- デフォルト値
  デフォルト値を引数に指定可能。デフォルト値を持つ仮引数は省略可能。

- 可変長引数
  引数に*をつけておくと、余った実引数を配列にまとめ仮引数に割り当ててくれる。

###### ブロック付きメソッド
- ブロック付きメソッドの用途
  1. ループの抽象化
  2. ブロックへの機能付加
  3. コールバック関数・イベントハンドラ

- クロージャ
  ブロックはクロージャであり、自由変数はブロックの外部環境に従う。
  ブロックが参照している外部環境は、ブロックが存在する限り保存されている。

- ブロック引数、ブロックローカル変数
  ブロック引数は外側のローカル変数とは独立している。同名のローカル変数とは互いに影響しない。
  ブロック引数に続けて任意のブロックローカル変数を宣言できる。
  ブロックローカル変数は、変数を利用する前に宣言する必要がある唯一の箇所。

  ex) [1, 2, 3].each do |i; a, b|  #iがブロック引数、a, bがブロックローカル変数

- ブロック付きメソッドの定義
  yield式は、メソッド内から呼び出し側のブロックをコールバックする。
  0個以上の式をとり、それらの式の値をブロック呼び出し時のブロック引数として渡す。
  
  Rubyの標準ライブラリは、ブロックをつけずにイテレータを呼び出すとEmuratorをオブジェクトを返す。
  ユーザ定義関数でも同様の挙動を求める場合、明示的に実装をしないといけない。
  ex) 
    def foo_bar_baz
      return enum_for(:foo_bar_baz) unless block_given?
      ...

- Proc
  ブロックをオブジェクトとして扱うことができる。
  仮引数リストの最後に&で修飾された引数をおくと、この引数に呼び出し側のブロックを表すProcオブジェクトが格納される。
  callで実行する。
  
  また、Procオブジェクトをブロックの代わりにブロック付きメソッドに渡すこともできる。
  &で修飾して引数リストの末尾におく。

###### アクセス権限
- 
  デフォルトではclass式の中で定義されたメソッドはpublic。
  トップレベルで定義されたメソッドはprivate。

- 権限
  |-----------+------------------------------------------------------------------------------|
  | 名前      | 説明                                                                         |
  |-----------+------------------------------------------------------------------------------|
  | public    | どこからでも呼び出すことができる。                                           |
  | protected | そのクラスまたはサブクラスのインスタンスメソッドからのみ呼び出すことができる |
  | private   | レシーバ省略形式でしか呼び出せない。従ってselfに対してのみ呼び出せる。       |
  |-----------+------------------------------------------------------------------------------|

- メソッド
  public, protected, privateというメソッドが各権限に対応。
  引数を付けずにpublicメソッドを呼ぶと、それ以降に定義されるメソッドがpublicになるよう設定される。
  インスタンスメソッド名を文字列または引数で渡すと、そのメソッドはpublicとなる。
  protected, privateも同様。

###### 特異メソッド
- 
  クラスではなくインスタンスに直接所属するメソッド。
  英訳はsingleton method。
  実装上は、特異クラスのインスタンスメソッド。
  
  ex)
    message = "Hello"
    def message.build_greeting(target)
      "#{self}, #{target}."
    end
    message.bulid_greeting("world")       #=> Hello, world

#### 文法、構文、要素
##### リテラル
- 
  数字の1や文字列"hello world"のようにプログラム中に直接記述できる値をリテラルという。

###### 配列
- 
  Arrayクラスで表す。
  配列が保持しているのはオブジェクトへの参照。
  ex) cattle = "yahoo"
      container = [cattle, cattle]
      cattle[2] = 'p'
      p container  #=> ["yapoo", "yapoo"]

####### 構築 
- 
  [](角括弧)で括ると並列が構築される。
  ex) c = [a, b, 3, "string"]

- 初期化
  Array.new(3, Ruby) #=> ["Ruby", "Ruby", "Ruby"]

####### 添字参照
- 
  添字で内容を参照できる。
  ex) c[0] #=> 'a'
  
  - 負の添字
    負の添字も使える。その場合は末尾から逆順に要素を指すこととなる。
    ex) c[-1] ( => cの最後の要素)
  
  - 長さ付き添字
    位置と長さを指定できる。
    最大の長さを指定するので、配列の長さが足りない場合は途中までを返す。
    ex) c[1, 3] ( p c[1, 3] => ["str", 3, "string"] )
  
  - 範囲添字
    添字として範囲オブジェクトを渡すと、番号がその範囲に含まれる要素を取得できる。
    開始位置または終了位置に負の添字も使える。
    ex) c[0..1], c[0...1]

####### 添字代入
    ex) a[4] = 3

####### 配列の比較
    対応する要素が全て同値のとき、且つそのときに限り同値。

####### メソッド例
-
 Array#length
 Array#each
 unshift, shift, push, pop, first, last, reverse
 sort, sort_by, each_with_index, inject

###### ハッシュ
- 
  任意のオブジェクトをキーとして別のオブジェクトに対応づけるコンテナオブジェクト。

####### 構築
- ハッシュロケット記法
  波括弧内にキーと値の対応関係を並べる。
  シンボルにハイフンを利用するためにこちらの記法を使う場合がある。
  ex) 
      test = {
        "CAT" => "Concatenate",
        "LS"  => "List",
        "PWD" => "Print Working Director
      }
- シンボルをキーとする略記
  シンボルをキートする場合、以下の略記法が利用できる。
  ex) params = { rin: 5, kimiko: 7, kayo: nil }
      p params   #=> {:rin => 5, :kimiko => 7, :kayo => nil}
- インスタンス化
  Hash.newに引数を渡すと、引数がデフォルト値となる。

####### 添字演算式
- 
  キーとなるオブジェクトを返して値を返す。一種類の方法しかない。

- 参照
  ex) p book_to_author["Programmnig Ruby"]  #=> "Thomas"
      p book_to_author["Programmnig Perl"]  #=> nil

- 更新
  ex) book_to_author["Ruby in Nutshell"] = ["Flanagan", "Mats"]

- 登録
  ex) book_to_author["The Ruby Way"] = "Fulton"

####### 比較
- 
  すべての対応する要素ペアについて、互いにキーが等しく値が等しいときに同値となる。

####### メソッド例
- 
  Hash#delete
  keys, include?, key?, values, value?, clear

###### 数値
####### クラス
- 
  Numeric ┬ Integer ┬ Fixnum
          │         └ Bignum
          └ Float

####### 整数
######## Integer
- 
  Integerクラスのサブクラスに、FixnumとBignumがある。
  Fixnumは内部的に固定長で実装されている整数で、小さな整数を効率的に処理可能。
  Bignumは多売長整数で、任意に大きな整数を表すことができる。Fixnumで格納できない場合は自動的にBignumとなる。

######## 基数
- 
  先頭記号を付けることで10進数以外のリテラルを表現できる。
  
  |------------------+--------|
  | 先頭記号         | 基数   |
  |------------------+--------|
  | 0x, 0X           | 16進数 |
  | 0d, 0D, 記号なし | 10進数 |
  | 0o, 0O, 0        | 8進数  |
  | 0b, 0B           | 2進数  |
  |------------------+--------|

####### 浮動小数点数
- 
  Floatクラス。

######## 浮動小数点の精度を表す定数
- 
  |------------+---------------------------------------------------+----------------------|
  | 定数名     | 意味                                              |                   例 |
  |------------+---------------------------------------------------+----------------------|
  | DIG        | floatが表現できる最大の10進数桁数                 |                   15 |
  | EPSILON    | 1.0 + Float::EPSILON != 1.0となるような最小の数   |  2.2044604925031e-16 |
  | MANT_DIG   | 仮数部のFloat::RADIX進法における桁数              |                   53 |
  | MAX        | Floatが取りうる最大の値                           | 1.79769313486232e308 |
  | MIN        | Floatが取りうる最小の値                           | 2.2250738585072e-308 |
  | MAX_10_EXP | Floatが取りうる最大の10進の指数                   |                  308 |
  | MIN_10_EXP | Floatが取りうる最小の10進の指数                   |                 -307 |
  | MAX_EXP    | Floatが取りうる最大のFloat::RADIX進法における指数 |                 1024 |
  | MIN_EXP    | Floatが取りうる最小のFloat::RADIX進法における指数 |                -1021 |
  | RADIX      | Floatの内部表現における基数                       |                    2 |
  |------------+---------------------------------------------------+----------------------|

######## 特殊な浮動小数点値
- Infinity
  正の無限大。1.0/0.0の結果など。
- -Infinity
  負の無限大。-1.0/0.0の結果など。
- 非数(NaN)
  0.0/0.0の結果など。どんな数とも等しくなく、自分自身とも同値でない。

####### 数値演算
- /
  除算
- %
  剰余
- -
  符号操作
- divmod(n)
  整除と剰余を同時に計算する。
  ex) -7.divmod(2) #=> [-4, 1]
- abs
  ex) -3.141.abs   #=> 3.141
- ceil
  小数部繰り上げ
  ex) 0.5772       #=> 1

- メソッド
  times, upto, downto, step

####### その他の数値・代数系クラス
- 
  標準添付されているライブラリにも各種の数値型が存在する。
- rational
  有理数クラスRationalを提供する。
- complex
  複素数クラスComplexを提供する。
- bigdecimal
  可変長の10進浮動小数点数クラスBigDecimalを提供する。
- matrix
  行列クラスMatrixおよびベクトルクラスVectorを提供する。

###### 文字列
- 
  ダブルクォートと異なり、シングルクォートは文字列の式展開を行わない。

####### memo
      ・バックスラッシュ記法
          ""はバックスラッシュ記法を使える、''は使えない。
      ・パーセント記法
          バックスラッシュのエスケープが毎度毎度面倒な時とかに使うらしい。
          %Qは式展開やバックスラッシュ記法を使えるが、%qは使えない。
          ex: str = %q("Ruby", "HTML", "JavaScript", "Rails")
      ・ヒアドキュメント
          開始と終了のラベルとしてキーワードを決め、
          その範囲を文字列オブジェクトとして扱う機能。
          ex:
              print <<EOS
              foo
              bar
              baz
              EOS
              #=>foobarbaz
      メソッド
          +, <<, concat, size, length, empty?, [], split, chomp,
          upcase, downcase, capitalize, swapcase

###### 正規表現リテラル
####### memo
        /check/ =~ "original"
        %rでも正規表現オブジェクト作成可能
        String#sub(gsub)メソッド

###### シンボル

###### 範囲オブジェクト
####### memo
        Rangeクラス
        1..5は終端を含む。(1,2,3,4,5)
        1...5は終端を含まない。(1,2,3,4)

##### 変数
- 
  変数が保持するのはオブジェクトへの参照。

- 種類
  |------------------+--------------------------+------------------------+--------------------|
  | 種類             | 先頭文字                 | デフォルト値           | 名前の例           |
  |------------------+--------------------------+------------------------+--------------------|
  | ローカル変数     | 小文字またはアンダーバー | 参照する前に代入が必要 | local_variable     |
  | インスタンス変数 | @                        | nil                    | @instance_variable |
  | クラス変数       | @@                       | 参照する前に代入が必要 | @@class_variable   |
  | グローバル変数   | $                        | nil                    | $global_variable   |
  | 定数             | 大文字                   | 参照する前に代入が必要 | CONSTANT_VALUE     |
  |------------------+--------------------------+------------------------+--------------------|

- 変数名の規則
  先頭文字以外は、ASCII記号の除く任意の印刷可能文字か、アンダースコア(_)を利用可能。
  大文字小文字は区別される。
  慣習的には単語をアンダースコアで区切る。

###### ローカル変数
- 
  local variable
  start with '_' or small alphabet

###### インスタンス変数
- 
  @で始まる値。個々のオブジェクトで固有の値を持つ。
  所属しているオブジェクト外部からはアクセスできない。

###### クラス変数
- 
  クラスと子孫クラス、及びそれらクラスの全てのインスタンス間で共有される変数。

###### グローバル変数
- 
  - 組み込み変数
    $stdout, $:, $1など、ruby処理系それ自体の状態や、挙動を制御するためのフラグを保持する、
    組み込み変数と呼ばれる特殊なグローバル変数がある。

###### 定数
- 
  constant
  マジックナンバーなどに名前をつけるために使う。
  特定のクラスやモジュールに所属するが、クラス定義に含まれない定数はObjectクラスに所属する。

  start with initialized alphabet

- 二重コロン
  二重コロン記法で定数へアクセスできる。
  クラスMに属する定数Kへは、M::Kでアクセス可能。
　　　　　　　　　　　　　  クラス名やモジュール名も単なる定数なので、同様にアクセス可能。

###### 擬似変数
- 
  小文字またはアンダースコアで始まっているが、Ruby処理系が設定するオブジェクトを参照しており、
  ユーザが値を代入することはできない。
  nil, true, false, self, __FILE__, __LINE__, __ENCODING__の7つ。

####### nil
- 
  値がないことを特殊なオブジェクト。
  NilClass唯一のインスタンス。

####### true
- 
  代表的な真の値。
  nilとfalseは偽となり、それ以外は真となるが、その中でもtrueは真の代表格。

####### false
- 
   代表的な偽の値。

####### self
- 
  「現在の」オブジェクトを表す。
  インスタンスメソッドの中ではメッセージの受け手がself。
  クラスメソッドにおいてはクラスを、ファイルのトップレベルにおいては通称mainと呼ばれる特別なObjectを参照する。

####### __FILE__
- 
  その場所のソースファイル名。

####### __LINE
- 
  その場所の行番号。

####### __ENCODING__
- 
  その場所のソースファイルのエンコーディングを保持している。
  Ruby1.9で導入。


###### 予約語
- 
  BEGIN    class    ensure   nil      self     when
  END      def      false    not      super    while
  alias    defined? for      or       then     yield
  and      do       if       redo     true
  begin    else     in       rescue   undef
  break    eslif    module   retry    unless
  case     end      next     return   until

##### 演算子
- 
  再定義可能な演算子はオブジェクトによって意味が変わる。
  以下は代表的な意味。

- 演算子（優先順位）
  |---------------------+----------------------------------------------------------------|
  | 演算子              | 意味                                                           |
  |---------------------+----------------------------------------------------------------|
  | ::                  | スコープ解決                                                   |
  | []                  | 添字                                                           |
  | + ! ~               | 正負号、論理否定、ビット反転                                   |
  | **                  | べき乗                                                         |
  | -(単項)             | 負符号                                                         |
  | * / %               | 乗算、除算、剰余                                               |
  | + -                 | 加算、減算                                                     |
  | << >>               | 左ビットシフト/データ出力、右ビットシフト/データ入力           |
  | &                   | ビット積(AND)                                                  |
  | l(パイプ) ^         | ビット和(OR)、排他的ビット和                                   |
  | > >= < <=           | 大小比較                                                       |
  | <=> == === != =~ !~ | 比較、同値、case同値、非同値、パターンマッチ、パターン非マッチ |
  | &&                  | 論理積(AND)                                                    |
  | ll(パイプ)          | 論理和(OR)                                                     |
  | .. ...              | 範囲生成                                                       |
  | ? :                 | 条件演算子                                                     |
  | = += -= []=など     | 代入                                                           |
  | not                 | 論理否定                                                       |
  | and or              | 論理積、論理和                                                 |
  |---------------------+----------------------------------------------------------------|

- 再定義
  演算子は大抵はメソッドシンタックスシュガーなので、クラスごとに再定義可能。

  - 再定義可能な演算子
    | ^ & <=> == === =~ > >= < <= << >> + - * / % ** ~ +@ -@ [] []=
    正符号・負符号は加算・減算と区別するため+@, -@と記す。

  - 再定義不可能な演算子
    = ?: .. ... ! not && and || or ::

###### 自己代入演算子
- 
  += -= *= /= %= **= <<= >>= |= &= ^= &&= ||=
  2項演算子と代入を組み合わせた式に投下。
  再定義できないが、二項演算子を再定義するとそれに合わせて変更される。

###### 否定演算子
- 
  != !~
  Ruby1.9では再定義可能にはなった。

###### 代入
- 
  代入式の値は代入された値そのものになるので、a = b = c = 1のように繋げてまとめて代入可能。

- 多重代入
  a, b, c = 1, 2, 3 という形で代入可能。
  意味としては、a = 1; b = 2; c = 3とほとんど一緒だが、評価順序は少し違う。
  代入が行われるより先に計算が行われるため、a, b = b, aで入れ替えが可能。

- 多値代入
  *を変数につけると、多値を配列にまとめてくれる。
  ex) a, *b = 1, 2, 3, 4, 5
      p b   #=>  [2, 3, 4, 5]

  また、*が代入の右辺に出現すると配列を多値に転回してくれる。
  ex) array = [1, 2, 3]; a, b, c = *array;
      p a  #=> 1; p b  #=> 2; p c  #=> 3

###### 論理演算子
- 
  再定義不可能。

- 論理和・論理積演算子
  trueやfalseでなくオペランドのいずれかを返す。
  ex) nil || 50  #=> 50
  また、短絡評価を行う。

- 初期化イディオム
  @a ||= generate_default_value のような式を評価すると、
  @aがtrueなら何もせず、偽ならgenerate_default_valueメソッドを呼んでその戻り値でaを初期化する。

###### 範囲演算子
- 
  オペランドを両端とするRangeオブジェクトを生成する。
  a .. bはbが含まれる。 a ... bはbが含まれない。
  
###### 条件演算子
- 
  a ? b : c
  aが真のときにはbに評価され、aが偽のときにcが評価される。
  Rubyのif式は値をもつので、条件演算子はif式の別の書き方にすぎない。
  var = a ? b : c と var = if a then b else c end は同じ。
  
##### 制御式
- 
  一般的な言語のように「制御文」でなく、値を返すため「制御式」と呼んでいる。
  thought = if sample.color == "green" then "danger" else "undefined" end、のような書き方をよくする。

###### if
- 
  条件が満たされたときだけthen節を実行する制御構造。
  実行された節の最後の式の値が返る。

- else

- elsif

- if修飾子
  do_something if condition
  上記の構文で、簡単なif文を記述できる。

- unless
  条件が偽であるときに被制御式を評価する制御構造。
  ifと同様elseは続けられるが、elsunlessはない。
  unless修飾子は存在する。

###### case

####### その1
- 
  多値分岐を提供する。
  まずvalueが評価され、その後when節に書かれている基準値が比較される。
  カンマで区切って複数記述することも可能。

  ex) 
    case value
    when 1 then
      do_something1  # valueが1の場合
    when 2, 3 then
      do_something2  # valueが2、3の場合
    when 4           # thenは省略可能
      do_something3
    when *array      # 配列展開も可能
      do_something4
    else
      do_something_other
    end

- 範囲分岐
  厳密な同値判断でないので、下のような範囲分岐も可能。

  ex)
    value = 3
    case value
    when 0      then '0'
    when 1..9   then '1けた'
    when 10..99 then '2けた'
    end

- 正規表現による分岐
  正規表現を利用した分岐も可能。
  ex)
    value = "3"
    case value 
    when '0'         then '0'
    when /\A\d\Z/    then '1けた'
    when /\A\d{2}\Z/ then '2けた'
    else                  'それ以外'
    end

- case比較演算子
  case式を評価する際は、通常の同値演算子==と異なり===演算子が用いられる。
  ===は==よりももう少し緩く一致性を判定する演算子。

####### その2
- 
  if節と酷似した形式。最初に評価する値が存在しない。
  ex)
    case
    when number.prime?  then process_prime(number)
    when number.fermat? then process_carmichel(number)
    when number.odd?    then process_odd_composite(number)
    else                     process_even_composite(number)
    end

###### while
- 
  条件が成立している間だけ被制御部を繰り返し実行する。
  nilを返す。
  doは省略可能。ちなみにブロック付きメソッド呼び出しのdoは省略不可。
  ex)
    while condition do
      do_something
    end

- 後置while
  1回目は条件式を評価せず被制御部を実行する。
  ex)
    begin
      do_something
    end while condition

- while修飾子
  条件式が真である間だけ修飾された式を繰り返し評価する。
  ex) do_something while condition

- until
  条件式が成立するまで日制御式を繰り返し実行する。
  後置、修飾子としての使用も可能。

###### for
- 
  配列などの要素に対して非制御部を繰り返し実行する。
  doは省略可能。
  ex)
    for i in [1, 2, 3] do
      puts i
    end

  for式は内部でeachイテレータを呼んでいるので、以下と変わらない。
  ex) 
    [1, 2, 3].each do |i|
      puts i
    end

  要素が多値の場合は多値代入に準ずる。これもeachと同じ。
  ex)
    for name, num in [['Jan', 1], ['Feb', 2]]
      puts "#{name}は#{num}月 "
    end

###### イテレータ
####### loop
- 
  無限ループを提供するイテレータ。
  脱出式を用いる必要がある。
  ex)
    loop do
      puts "looping"
    end

####### times
- 
  Integerクラスのtimesメソッドは、Integerオブジェクトが表す回数だけブロックを実行する。
  ex)
    3.times{ puts "Yahoo" }
    3.times{|i| puts i}

####### upto, downto
- 
  カウントアップする場合に使う。カウントダウンはdowntoメソッド。
  ex) 1.upto(3) do |i| puts i end

###### 脱出
- 
  while, until, for, イテレータから抜け出したいときに使う。

- break
  現在の繰り返し構造から脱出する。
  入れ子になっている場合は最も内側から脱出する。
  また、breakには引数をつけることができ、脱出したときの値となる。

- next
  最も内側の繰り返し構造の残りの部分をスキップして、次回の繰り返しにジャンプする。

- redo
  今回の繰り返しをもう一度初めからやり直す。
  繰り返し条件が成立しているかどうかはチェックされない。
  
###### 例外処理
- 
  begin, endで囲んだ範囲内で例外が発生した場合、対応するrescue節へ移動する。
  rescue節、else節、ensure節は不要であれば省略可能。

  ex)
    begin
      do_something
    rescue ArgumentError => error then  #then節は省略可能
      puts error.message
    rescue TypeError                    #例外補足変数は省略可能
      do_something_with_error
    rescue => another_error             #クラスは省略可能
      puts another_error.message
    else
      puts "例外なし"
    ensure
      puts "ensure節"
    end

- rescue
  処理対象とする例外の種類を指定可能。
  クラス指定を省略するとStandardErrorを指定したこととなる。
  例外オブジェクトを細くする必要がなければ => errorという補足変数部分は省略可能。

- else
  例外が一切発生しなかった場合に実行する節。

- ensure
  例外が発生しようがしまいが必ず実行される節。

- rescue修飾子
  ex) do_something rescue error_handling
  上記のdo_somethingを実行中に例外が発生するとerror_handlingを実行する。
  例外クラスを指定したり、例外オブジェクトを補足したりはできない。
  ただし、そのスレッドで最後に発生した例外は変数$!を通して参照可能。

- raise
  ユーザが明示的に例外を発生させる。
  エラーメッセージ及び例外クラスは省略可能。
  例外クラスを省略するとRuntimeErrorを発生させる。
  
  ex) raise ArgumentError, 'message'
  上記は以下と等価。
  ex) error = ArgumentError.new('message')
      raise error

###### 大域脱出
- 
  catchとthrowを使って深い入れ子になった繰り返しから外側へ脱出できる。
  throwの引数にシンボルまたは文字列を渡し、catchを識別する。
  throwで大域脱出を行うと、同じ識別名を持つcatchに至るまでスタックをさかのぼる。
  対応するcatchが見当たらない場合はArgumentErrorを発生します。

  ex)
    catch(:exit) {
      loop do
        loop do
          throw :exit
        end
      end
    }
    #ここに脱出する

##### セキュリティモデル
- 
  オブジェクトの汚染とセーフレベルという仕組みがある。

###### 汚染
- 
  1. 信用できない入力をもとに作られたオブジェクトを「汚染されている」と見なし、
     「危険な操作」の引数として使えないようにする。
  2. 信用しているオブジェクト（汚染されていないオブジェクト）を信用できないプログラムから守る、という使い方。

- メソッド
  - Object#taint
    オブジェクトを汚染する
  - Object#tainted?
    オブジェクトが汚染されている場合に真を返す
  - Object#untaint
    オブジェクトの汚染を取り除く

###### セーフレベル
- 
  各スレッドは固有の「セーフレベル」を持っている。
  セーフレベルが高くなるほど、行える操作は制限される。
  スレッドローカル変数$SAFEで設定します。

- レベル0
  デフォルトのセーフレベル
- レベル1
  信用しているプログラムで信用できないデータを処理するためのレベル。
  CGI等でユーザからの入力を処理するのに適している。
- レベル2
  レベル1の制限に加え、いくつかの操作が禁止される。
- レベル3
  生成される全てのオブジェクトが汚染される。
- レベル4
  廃止された。

#### メタプログラミング
##### メタ情報に関するメソッド
- 
  |------------------------------------------------+-------------------------------|
  | 説明                                           | メソッド                      |
  |------------------------------------------------+-------------------------------|
  | クラスのメソッドの一覧を得る                   | Module#instance_methods       |
  | オブジェクトのメソッドの一覧を得る             | Object#methods                |
  | オブジェクトのインスタンス変数の一覧を得る     | Object#instance_variables     |
  | グローバル変数の一覧を得る                     | global_variables              |
  | ローカル変数の一覧を得る                       | local_variables               |
  | クラス/モジュール定数の一覧を得る              | Module#constants              |
  | クラス/モジュールのネスト情報を得る            | Module.nesting                |
  | 継承/インクルード構造を得る                    | Module#include_modules,       |
  |                                                | Class#superclass              |
  | 現在割り当てられている全てのオブジェクトを得る | ObjectSpace#each_object       |
  | 各変数/定数の値を操作する                      | remove_instance_variablesなど |
  | 各変数/定数の値を得る                          | Module#const_getなど          |
  | 定数を追加する                                 | Module#const_set              |
  | クラスのメソッドに別名を付ける                 | Module#alias_method           |
  | クラスのメソッドを定義する                     | Module#define_method          |
  | クラスのメソッドを削除する                     | Module#remove_method          |
  | クラスのメソッドを未定義化する                 | Module#undef_method           |
  |------------------------------------------------+-------------------------------|
  (Rubyアプリケーションプログラミング)

##### eval族
- 
  (Rubyアプリケーションプログラミング)
  - eval
  - instance_eval
  - module_eval, class_eval

##### フック
- 
  (Rubyアプリケーションプログラミング)
  |--------------------------------------+-------------------------------|
  | 説明                                 | メソッド                      |
  |--------------------------------------+-------------------------------|
  | 継承をフックする                     | Class#inherited               |
  | インクルードをフックする             | Module#append_features        |
  | メソッド定義をフックする             | Module#method_added           |
  | 特異メソッド定義をフックする         | Object#singleton_method_added |
  | 未定義メソッドの呼び出しをフックする | Object#method_missing         |
  | グローバル変数への代入をフックする   | trace_var                     |
  |--------------------------------------+-------------------------------|
  
#### ライブラリ
- https://docs.ruby-lang.org/ja/latest/library/index.html
##### 組み込みライブラリ
- Ruby本体に組み込まれているライブラリ。
  このライブラリのクラスやモジュールは、requireを書かなくても使うことが出来る。

###### クラス

####### BasicObject
- 要約
  特殊な用途のために意図的にほとんど何も定義されていないクラス。
  Ruby 1.9以降で導入された。
######## Inheritance
- BasicObject
######## Instance Method
######## Private Method
######### List
- 
  method_missing singleton_method_added singleton_method_removed singleton_method_undefined
######### method_missing
- method_missing(name, *args) -> object
  呼び出されたメソッドが定義されていなかった場合にこのメソッドを呼び出す。
  呼び出しに失敗したメソッドの名前(Symbol)がnameに、そのときの引数がargsに格納される。
  デフォルトではNoMethodErrorを発生させる。

####### Object
- 要約
  全てのクラスのスーパークラス。オブジェクトの一般的な振る舞いを定義する。
######## Inheritance
- 
  Object < Kernel < BasicObject
######## Instance Method
######### send
- send(name, *args) -> object
  send(name, *args){...} -> object
  (__send__も同様)

  オブジェクトのメソッドnameを、argsを引数にして呼び出す。
  sendが再定義された場合に備え別名__send__も用意されているので、ライブラリ等ではこちらを使うべき。
  メソッドの呼び出し制限にかかわらず任意のメソッドを呼び出せる。

####### Class
- 要約
  クラスのクラス。多くの機能はモジュールからModuleから継承されている。
######## Inheritance
- 
  Class < Module  < Object < Kernel < BasicObject
######## InstanceMethod
######### new
- 
  new(*args, &block) -> object
  自身のインスタンスを生成して返す。
######### superclass
- 
  superclass -> Class | nil
  自身のスーパークラスを返す。

####### Module
- 要約
  モジュールクラス。
######## Inheritance
- 
  Module < Object < Kernel < BasicObject
######## InstanceMethod
######### list
- 
  < <= <=> === > >= ancestors autoload autoload? class_eval module_eval class_variable_defined? class_variables
  const_defined? const_get const_missing const_set constants include? include_modules inspect name to_s instance_method
  instance_methods method_defined? prepend private_class_method private_instance_methods private_method_defined?
  protected_instance_metohds protected_method_defined? public_class_method public_instance_method public_instance_methods
  public_method_defined? remove_class_variable

######### ancestors
- ancestors -> [Class, Module]
  クラス、モジュールのスーパークラスとインクルードしているモジュールを優先順位順に配列に格納して返す。
####### Array
- 
  配列を表すオブジェクトを提供する。

######## Inheritance
- Array < Enumerable < Object < Kernel < BasicObject

######## ClassMethod
######### []
######### new

######## InstanceMethod
######### +
- 
  配列を連結
######### <<
- 
  末尾に要素を追加
######### []
######### []=
######### length
######### empty?
######### include?
######### select
######### collect

####### Hash
- 
  ハッシュテーブルのクラス。
######## Inheritance
- Hash < Enumerable < Object < Kernel < BasicObject
####### Enumerator
- 
  each以外のメソッドにもEnumerableの機能を提供するためのラッパークラス。
######## Inheritance
- Enumerator < Enumerable < Object < Kernel < BasicObject
  
####### Dir
- 要約
  ディレクトリの操作を行うためのクラス
######## Inheritance
- 
  Dir < Enumerable < Object < Kernel < BasicObject
######## SingletonMethod
######### List
- 
  [] glob chdir chroot delete rmdir unlink entries exist? exists? foreach getwd pwd home mkdir new open
######### glob
- 
  glob(pattern, flags = 0) -> [String]
  ワイルドカードの展開を行い、パターンにマッチするファイル名を文字列の配列として返す。
  パターンにマッチするファイルがない場合は空の配列を返す。
  - ワイルドカード
    - * : 空文字列を含む任意の文字列と一致
    - ? : 任意の一文字と一致
    - [] : かぎカッコ内のいずれかの文字と一致。
           -でつながれた文字は範囲を表す。
           最初の文字が^である場合は含まれない文字と一致。同様に!も使える。
    - {} : コンマで区切られた文字列の組み合わせに展開する。
           {foo, bar{foo,bar}}はfoo, barfoo, barbarにマッチする。
    - **/ : ワイルドカード*/の0回以上の繰り返しを意味し、ディレクトリを再帰的にたどってマッチを行う。
            foo/**/barは、foo/bar, foo/*/bar, foo/*/*/bar, ... とマッチする。
######## InstanceMethod
######### List
- 
  close each inspect path to_path pos tell pos= seek read rewind

####### Proc
- 
  ブロックをコンテキストとともにオブジェクト化した手続きオブジェクト。
######## Inheritance
- 
  Proc < Object < Kernel < BasicObject
######## SingletenMethod
######### List
- 
  new
######## InstanceMethod
######### List
- 
  === [] call yield arity binding curry hash inspect to_s lambda? parameters source_location to_proc

####### String
- 
  文字列クラス
######## Inheritance
- String < Comparable < Object < Kernel < BasicObject
######## InstanceMethod
######### chomp
- chopm(rs=$/) -> String
  selfの末尾からrsで指定する改行コードを取り除いた文字列を生成して返す。

###### モジュール

####### Kernel
- 要約
  全てのクラスから参照できるメソッドを定義しているモジュール。
  トップレベルのメソッドの再定義に対応するため、Objectクラスのメソッドは実際にはこのモジュールで定義されている。
######## Inheritance
- 
  Kernel
######## ModuleFunction
######### gets
- gets(rs=$/) -> String | nil
  ARGFから一行読み込んで、それを返す。行の区切りは引数rsで指定した文字列となる。

######### chomp
- chomp(rs=$/) -> String
  $_.chompとほぼ同じ。置換が発生した時は、$_の内容を置き換える点が異なる。

######### lambda
- 
  Procを返す。Proc.newと似ているが、いくつかの場面で挙動が違う。
  return時の挙動や引数チェックなど。
  lambdaの方がよりメソッドに近い動きをし、厳密。

######### proc
- 
  Proc.newと同じ。

####### Comparable
- 
  比較演算を許すクラスのためのMix-in。

####### Enumerable
- 
  繰り返しを行うクラスのためのMix-in。
  メソッドが全てeachを用いて定義されているので、インクルードするクラスにeachを定義する必要がある。

####### Instance Method
######## inject
- 
  リストの畳み込み演算を行う。
  初期値initとselfの最初の要素を引数に、ブロックを実行する。
  2回目以降は、前のブロックの実行結果とselfの次の要素を引数に、順次ブロックを実行する。

###### オブジェクト
###### 例外クラス
##### CUI
##### 文字コード
##### ファイルフォーマット
###### rexml
- Pure RubyのXMLパーサ
####### rexml/document
- DOBスタイルのXMLパーサ。
  REXML::Document.newでXML文書からDOMツリーを構築し、
  ツリーのノードの各メソッドで文書の内容にアクセスする。
- [[http://www.germane-software.com/software/rexml/docs/tutorial.html][REXML Tutorial]] <- これが良い感じ。

######## Elements
- 継承リスト
  REXML:Elements < Enumerable < Object < Kernel < BasicObject
- 要約
  要素の集合を現すクラス。XPathによる探索をサポートする。
  REXML::Element#elementsはこのオブジェクトを返す。
  XPathで相対パスを指定した場合、このレシーバが基準要素となる。


######## XPath
- 継承リスト
  REXML:XPath < REXML:Functions < Object < Kernel < BasicObject
- 要約
  XPathを取り扱うためのクラス。
  インスタンスは使わずにクラスメソッドのみを使う。
- 特異メソッド
  - 一覧
    each first match
  - each(element, path = nil, namespaces = {}, variables = {}) {|e| ...} -> ()
    elementのpathで指定したXPath文字列にマッチする各ノードに対してブロックを呼び出す。
    ex) REXML::XPath.each(doc, "/root/a/b"){|e| p e.text}
        docというXMLDocumentから、/root/a/bを順次抜き出し、その要素を出力する。
  - first(element, path = nil, namespace = {}, variables = {}) -> Node | nil
    elementのpathで指定したXPath文字列にマッチする最初のノードを返す。
  - match(element, path = nil, namespaces = {}, variables = {}) -> [Node]

##### ネットワーク
###### webrick
- 汎用HTTPサーバフレームワーク。
#### C API
## Rubyソースコード完全解説
- http://i.loveruby.net/ja/rhg/book/
### ruby言語ミニマム
- rubyでは全てがオブジェクトで、Javaのintやlongのような基本型(primitive)はない。
- 配列
    [1,2,3]
- ハッシュテーブル
    {"key1"=>"value", "key2"=>"value2"}
- ローカル変数
    小文字から始まる
- 定数
    大文字から始まる
- インスタンス変数
    @から始まる
- 制御
    ifとwhile
- boolean
    falseとnilのみが偽、他は0や空文字も真。
- クラス
    「Stringのupcaseメソッド」→「String#upcase」
    「Object.new」はクラスオブジェクトObjectそれ自体に対して呼ぶメソッドnew、の意味。
    クラスの中にinitializeというメソッドを定義しておくと、newした際に呼んでくれる(newの仕様)
    継承は以下のように書く
       class C < SuperClassName
       end
    省略した場合はObjectがスーパークラスとなる。
    すべてのクラスはObjectクラスを直接または間接に継承する。
- メソッド
    self: 自分自身が誰か、という情報
    自分自身を呼ぶときはself（receiver）を省略できる。
    self.real_my_p(obj)→real_my_p(obj)
- モジュール
    スーパークラスを指定できず、インスタンスも作れないクラス。
    他のクラスにインクルードして使う。
    スーパークラスは継承できないが他のモジュールはインクルードできる。
    クラスとモジュールで同名のメソッドが存在した場合、モジュールが使用される。つまりモジュールの方が近い。

## メタプログラミングRuby
### Object Model
#### インスタンスの中身
- 
  インスタンス内にあるのはインスタンス変数と、クラスへの参照。メソッドは存在しない。
  メソッドはクラスに存在する。
  そのため、同じクラスのインスタンスでもインスタンス変数を共有しない。

#### インスタンスメソッド
- 
  インスタンスによって参照される、クラス内に保持しているメソッドを、インスタンスメソッドと呼ぶ。
  クラスメソッドは、クラス自体に静的に存在しているメソッドなので、それと区別する目的。
  同じメソッドを、クラスに着目しているときはインスタンスメソッド、インスタンスに着目しているときは単にメソッドと呼べばよい。

#### クラス間の関係
- 
  自作クラスはClassクラスのclassで、Objectクラスをスーパークラスに持つ。
  classは（おそらく）類別で、どの種類のものかを表し、そのオブジェクトはclassのインスタンス、という扱いになる。
  レベルが一段低くなる感じで、実装、という感じか。classの方は一段抽象化された設計図のようなもの、という感じ。
  スーパークラスは、継承関係にある関係。is-aだったり、has-aだったり。設計図の中でも上位のまとまった関係、という感じ。
  これも抽象化されたもの、とも言えるので、差が難しいが、class関係が具象-抽象、superclass関係が詳細-抽象、程度の関係だろうか。

#### 定数のパス
- 
  定数に対して、::（コロン2つ）を使ってアクセスできる。
  ::から始めると絶対パスによるアクセスとなる。

#### オブジェクトとクラス
- 
  オブジェクトとは、インスタンス変数の集まりにクラスへのリンクがついたもの。
  メソッドはオブジェクトではなくオブジェクトのクラスに住んでいる。
  クラスとは、オブジェクト（Classクラスのインスタンス）にインスタンスメソッドの一覧とスーパークラスへのリンクがついたもの。

#### ネームスペース
- 
  モジュールを使って実現する。
  例えばRakeモジュールのTaskクラスはRake::Taskでアクセスする。

#### Rubyのメソッド呼び出し時の挙動
- 
  1. メソッド探索
  2. メソッド実行

- メソッド探索
  
#### インクルードクラス
- 
  モジュールをクラス等にインクルードすると、無名クラスを作ってモジュールをラップし、継承チェーンに挿入する。
  無名クラスはインクルードするクラスの真上に入る。
  プロキシクラスとも。

  superclassはインクルードクラスが存在しないように振る舞い、通常のRubyコードはインクルードクラスにアクセスできない。

#### self
- 
  カレントオブジェクト。
  selfの役割を担うオブジェクトは複数同時に存在しない。
  メソッドを呼び出すときは、レシーバがselfとなる。
  その時点で、すべてのインスタンス変数はselfのインスタンス変数となる。
  レシーバを明示せず呼び出すと、すべてselfに対するメソッド呼び出しとなる。
  他のオブジェクトを明示してオブジェクトを呼び出すと、そのオブジェクトがselfとなる。

  クラスの定義やモジュール定義の中では、selfはクラスやモジュールとなる。

#### main
- 
  Rubyを開始すると、mainと呼ばれるオブジェクトの内部にいる。

### Method
#### 動的ディスパッチ
- 
  実行時に呼び出すメソッドを直前に決められる。
  Rubyではsendを使って実現する。
  ディスパッチ、とは"振り分け"を意味する。

#### シンボルと文字列の変換
- 文字列からシンボル
  String#to_sym()
  String#intern()

- シンボルから文字列
  Symbol#to_s()
  Symbol#id2name()

#### DelegateClass
- 
  新しいClassオブジェクトを生成して返すミミックメソッド。
  そのクラスにはmethod_missing()が定義されていて、ラップしたオブジェクトに呼び出しを転送する。

#### ブランクスレート
- 
  継承したメソッドをすべて削除した状態。空白の石盤の意らしい。
  Ruby1.9では、BasicObjectを直接継承したクラスは自動的にブランクスレートとなる。

### Block
#### ブロック
- 
  コードと束縛の集まり。
  束縛とは、オブジェクトに紐づけられた名前で、環境とも。
  ブロックを定義すると、その時その場所にある束縛を取得する。

#### スコープゲート
- 
  プログラムがスコープを変えて、新しいスコープをオープンする場所は以下の3つ。
  - クラス定義 class end
  - モジュール定義 module end
  - メソッド呼び出し (def end)

#### フラットスコープ
- 
  Class.newやModule.new、define_methodなどを使って変数を共有することが出来る。
  スコープのフラット化、フラットスコープなどと呼ぶ。

#### 共有スコープ
- 
  フラットスコープで複数のメソッドを定義すると、メソッド間で束縛を共有できる。
  これを共有スコープと呼ぶ。

#### 呼び出し可能オブジェクト
- 
  コードを保管して、あとで呼び出すことができる方式は、以下のものがある。
  - ブロック : 定義されたスコープで評価される。（オブジェクトではない）
  - Proc : Procクラスのオブジェクト。ブロックがオブジェクトになったもの。定義されたスコープで評価される。
  - lambda : Procの変形。Procクラスのオブジェクトだが、挙動が少し異なる。上記同様クロージャ。
  - メソッド : オブジェクトにひもづけられ、オブジェクトのスコープで評価される。

##### Proc
- 
  ブロックをオブジェクトにしたもの。
  Proc.new()にブロックを渡し生成し、Proc#call()を呼び出して評価する。
  lambda(), proc()という2つのカーネルメソッドを使ってもProcに変換できる。
  
  lambdaで作られたProcオブジェクトはlambdaと呼ばれ、Procと微妙に異なる。

- &修飾子
  &を使うことで、Procからブロックへの変換、ブロックからProcへの変換が可能。
  仮引数につけるとブロック→Procに、実引数に付けるとProc→ブロックに、なるのかな、と予想。

##### Procとlambdaの違い
- return
  lambdaでは、returnは単にlambdaから戻るだけ。
  Procでは、Procから戻るのではなく、Procが定義されたスコープから戻る。

- arity(項数)
  lambdaでは、引数の数に対して厳格で、多すぎたり少なすぎるとArgumentErrorとなる。
  Procでは、多い場合は多い分を切り落とし、少ない場合は足りない変数にnilを割り当てる。

- 選択
  lambdaの方が厳格で、methodに近い動きをするので、特別にProcが必要でない場合lambdaを選ぶ場合が多い、とのこと。

###### Method
- 
  Object#method()でメソッドをMethodオブジェクトとして取得し、あとでMethod#call()を使って実行できる。
  lambdaは定義されたスコープ内で評価されるが、Methodオブジェクトは属するオブジェクトのスコープで評価される。
  オブジェクトからメソッドを引き離すには、Method#unbind()を使う。

### Class Definition
#### カレントクラス
- 
  selfがクラスでない場合、カレントクラスはselfのクラスとなる。
  Rubyインタプリタは常にカレントクラスを持つ。

#### class_evalとinstance_eval
- 
  instance_evalはselfに変更を加えるのみ（特異クラスの変更も行う）。
  class_evalはselfとカレントクラスに変更を加える。

#### クラスインスタンス変数
- 
  クラスに定義されたインスタンス変数。
  クラス変数とは別物。

#### クラスマクロ
- 
  attr_accessor()のようなメソッドはクラスマクロと呼ばれる。
  キーワードのように見えるが、定義の中で使える単なるクラスメソッド。

#### 特異クラス
- 
  特別なクラス。
  インスタンスを1つしか持てない(そのためシングルトンクラスとも呼ばれる)。
  特異メソッドを保持する。
  英語圏ではeigenclassがsingleton class同様使われることがあるらしい。

  下記のような構文で特異クラスのスコープに入れる。
  class << an_object
    # some code
  end

  オブジェクトの特異クラスは、継承チェーンにおいて通常のクラスの下に入る。
  つまり、Cクラスのインスタンスobjの特異クラス#objは、Cをスーパークラスに持つ。

  特異クラスのスーパークラスは、スーパークラスの特異クラスとなる。
  DのスーパークラスがC、D,Cの特異クラスをそれぞれ#D,#Cとすると、
  #Dのスーパークラスは#Cとなる。

#### Rubyのオブジェクトモデル
- 
  1. オブジェクトは1種類しかない。通常のオブジェクトかモジュールとなる。
  2. モジュールは1種類しかない。通常のモジュール、クラス、特異クラス、プロキシクラスのいずれかとなる。
  3. メソッドは1種類しかない。メソッドはモジュール（大半はクラス）に住んでいる。
  4. すべてのオブジェクトは、クラスも含め「本物のクラス」を持っている。それは通常のクラスか特異クラスになる。
  5. すべてのクラスはスーパークラスを持っている。ただしBasicObjectにスーパークラスはない。
  6. オブジェクトの特異クラスのスーパークラスは、オブジェクトのクラスである。クラスの特異クラスのスーパークラスはクラスのスーパークラスの特異クラスである。
  7. メソッドを呼び出すとき、Rubyはレシーバの本物のクラスに向かって「右へ」進み、継承チェーンを「上へ」進む。

#### メソッドの再定義
- 
  メソッドの再定義は、元のメソッドを変更するのでなく、新しいメソッドを定義して、元のメソッドの名前を付けている。

#### アラウンドエイリアス
- 
  1. メソッドにエイリアスをつける
  2. 新しいメソッドを定義する
  3. 新しいメソッドから古いメソッドを呼び出す

### Coding Code
#### 文字列とブロック
- 
  instance_eval()とclass_eval()も、eval()と同様に文字列を受け取れる。
  ブロックと同様にコード文字列は評価される。
  ただし、コード文字列にはセキュリティの問題などもあるため、出来るだけブロックを使う方が良い。

#### ヒアドキュメント
- 
  "<<"と終端を表す識別子を使用して、複数行のテキストを記述する。

#### クラス拡張ミックスイン
- 
  クラス拡張とフックメソッドを組み合わせてクラスメソッドをミックスインする。

  1. モージュルを定義する。MyMixinとする。
  2. MyMixinの内部モジュール（通常ClassMethodsという名前）を定義して、メソッドをいくつか定義する。
     これが最終的にクラスメソッドとなる。
  3. MyMixin#included()をオーバーライドして、includerにClassMethodsをextend()する。

### Command
#### Object#class
- 
  クラスを返す。

#### Object#instance_variables()
- 
  インスタンス変数の一覧を確認する。

#### Object#methods()
- 
  メソッドの一覧を確認する。

#### superclass()
- 
  スーパークラスを返す。

#### Module.constants()
- 
  現在のプログラムのトップレベルにある全ての定数を返す。
  クラス名も含まれる。
  クラスメソッド。
  
#### Module#constants()
- 
  現在のスコープにある全ての定数を返す。
  インスタンスメソッド。

#### load
- 
  コードを実行するために読み込む。
  2番目の引数にtrueをすると、無名モジュールを作成しネームスペースとして使うことで、環境を汚染しないようにする。
  使用後に無名モジュールを廃棄する。

#### require
- 
  ライブラリを読み込むために使う。
  そのため、load()とは異なり2番目の引数はない。

#### ancestors()
- 
  継承チェーンを表示する

#### private_instance_methods
- 
  プライベートインスタンスメソッドを表示する。のだと思う。

#### public_instance_methods
- 
  publicメソッドを表示する。


#### send()
- 
  メソッドを呼び出す。
  メソッド名には文字列またはシンボルが使えるが、シンボルの方が適当とされる。
  パブリックメソッドも呼び出せるので、使い方には注意。

#### public_send()
- 
  send()とは異なり、publicメソッドは呼び出せない。
  protecedなメソッドは、同じクラスのインスタンスメソッドの中でなら呼び出せる。

#### Module#define_method()
- 
  メソッドをその場で定義できる。
  メソッド名とブロックを渡す必要があり、ブロックがメソッドの本体となる。

  ex) class MyClass
        define_method :my_method do |my_arg|
          my_arg * 3
        end
      end

  スコープを変更せず定義するために使用することもできる。

#### Object#method_missing()
- 
  継承チェーンでメソッドが見つからなかった場合に実行される処理。
  BasicObjectで定義されている。

#### Module#const_missing()
- 
  存在しない定数を参照したとき、Rubyはその定数名をシンボルとしてconst_missing()にわたす。

#### undef_method()
- 
  継承したメソッド含め、すべてのメソッドを削除する。

#### remove_method()
- 
  レシーバのメソッドは削除するが、継承したメソッドはそのままにする。
  

#### Kernel#block_given?
- 
  ブロックの有無を確認できる。

#### Kernel#local_variables()
- 
  ローカル変数を取得する

#### Class.new()
- 
  class定義をメソッドとして行う。
  スコープのフラット化を意図して使用することもある。

#### Object#instance_eval()
- 
  オブジェクトのコンテキストでブロックを評価する。
  渡したブロックをコンテキスト探査機と呼ぶ。

#### instance_exec()
- 
  ブロックに引数を渡しつつ、instance_eval()と似た挙動をする。

#### Proc.new()
- 
  Procを生成する。
  ブロックを渡す。

#### Proc#call()
- 
  Procで定義したブロックを呼び出す。

#### Proc#lambda?()
- 
  Procがlambdaの場合にtrueを返す。

#### Object#method()
- 
  メソッドをMethodオブジェクトとして取得できる。
  ex) object = MyClass.new(1)
      m = object.method :my_method
      m.call

#### Method#call()
- 
  Methodオブジェクトを実行する。

#### Method#unbind()
- 
  メソッドをオブジェクトから引き離す。
  UnboundMethodオブジェクトが帰ってくる。

#### Method#to_proc()
- 
  MethodオブジェクトをProcオブジェクトに変換する。


#### Module#class_eval()
- 
  既存のクラスのコンテキストでブロックを評価する。

#### Module#module_eval()
- 
  class_eval()と似たようなもの。おそらく。

#### singleton_methods
- 
  特異メソッドの一覧を表示する。

#### Module#attr_*()
##### Module#attr_reader()
- 
  読み取り用アクセサを生成する。

##### Module#attr_writer()
- 
  書き込み用アクセサを生成する。
  
##### Module#attr_accessor()
- 
 読み書き両用アクセサを生成する。

#### Object#extend
- 
  クラス拡張とオブジェクト拡張を行う。
  レシーバの特異クラスにモジュールをインクルードするためのショートカット。

#### alias（キーワード）
- 
  aliasキーワードを使うと、メソッドにエイリアス（別名）を付けられる。

#### Module#alias_method()
- 
  aliasと同じ動きをする。


#### Kernel#eval()
- 
  コード文字列を実行して、結果を返す。

#### Kernel#binding()
- 
  Bindingオブジェクトを作成する。
  Bindingオブジェクトはスコープをオブジェクトにまとめたもの。

- TOPLEVEL_BINDING
  トップレベルのスコープが束縛されている。

#### Object#instance_variable_get()
- 
  インスタンス変数を取得する

#### Object#instance_variable_set()
- 
  インスタンス変数を設定する

#### Class#inherited()
- 
  クラスが継承したときに呼ばれる。
  フックメソッドと呼ばれる。

#### Module#included()
- 
  モジュールがミックスインされた際に実行される。

#### Module#extend_object()
#### Module#method_added()
#### Module#method_removed()
#### Module#method_undefined()


#### Kernel#autoload()
- 
  モジュール名とファイル名を受けとり、モジュールを最初に参照したときにファイルを自動的に読み込む。

## Tools ツール
### gem
- パッケージ管理ツール
- frontend to RubyGems, the Ruby package manager
#### Options
##### environment
- バージョンや実行ファイル、パスなどが表示される。

### bundler
- Ruby Dependency Management
- gemでインストールする各ライブラリをまとめて管理し、バージョン差異を揃えるためのもの。
- Gemfilesというファイルにインストールするgemを記述、それを元にbundlerでインストールを行う。
#### Synopsis
- bundle COMMAND [--no-color] [--verbose] [ARGS]
#### Options
#### Bundle commands
##### Primary commands
###### bundle install
###### bundle update
###### bundle package
###### bundle exec
- Execute a script in the context of the current bundle.
###### bundle config
###### bundle help
##### Utilities
###### bundle add
###### bundle binstubs
###### bundle check
###### bundle show
###### bundle outdated
###### bundle console
###### bundle open
###### bundle lock
###### bundle viz
###### bundle init
###### bundle gem
###### bundle platform
###### bundle clean
###### bundle doctor
#### Link
- https://qiita.com/hisonl/items/162f70e612e8e96dba50
### rake
- a make-like build utility for Ruby
#### Synopsis
- rake [-f rakefile] {OPTIONS} TARGETS...
#### Options
##### -m, --multitask
##### -T, --tasks
- get a list of available Rake taskes.
## Libarry(外部)
### Nokogiri
- XMLドキュメントとHTMLドキュメントを扱うためのライブラリ。
  実際はhtml/xml解析ライブラリであるlibxml2のラッパー。
- http://www.nokogiri.org/
### pg
- PostgreSQLにアクセスするためのライブラリ。
### unicorn
- Rack HTTP server for fast client and Unix
- https://bogomips.org/unicorn/
#### Commands
##### unicorn
- Usage : unicorn [ruby options] [unicorn options] [rackup config file]
###### Ruby options
- -e, --eval LINE
###### unicorn options
- -o, --host HOST
- -p, -port PORT
- -E, --env RACK_ENV
- -c, --config-file FILE : Unicorn-specific config file
###### Common options
- -h, --help
- -v, --version
##### unicorn_rails
- ほぼunicornと同様。
###### unicorn options
- --path PATH : Runs rails app mounted at a specific path
## etc

- encoding
  # encoding: utf-8(etc)

- interpolation
  #{} in ""

- array
  %w, %W, %i, %I

- insert, delete(_at)
- unshift, << or push
- shift, pop

- puts
- gets
  .chomp

- print
    文字列を返す。改行文字なし。
- p
    読みやすい形にして出力。
    inspect + puts

- <=>
    宇宙船演算子

### コメント
- 
  コメント行は#から始める。
  複数行は、=begin, =endでコメントとできる。

### 別名
- alias
  別名をつける。別名というか、メソッドのコピーみたいな形になるようで、
  元のメソッドの定義を変更しても、別名をつけたメソッドには反映されない。

### モジュール
- module_function

### ファイル操作等
- 入出力
  組み込み定数：STDIN, STDOUT, STDERR
  グローバル変数：$stdin, $stdout, #stderr
- その他クラス・モジュール名
  IO, File, Dir, FileTest
  OperURI(open-uri.rb), Find(find.rb), Pathname(pathname.rb),
  Tempfile(tempfile.rb), FileUtils(fileutils.rb)

### バージョン体系
- 
  MRIのバージョンは(Major).(Minor).(Teeny)となっていて、
  Minorが偶数のバージョンが安定板、と「初めてのRuby」にはあるが、多分古い。

### 実行モデル
- 
  MRIではソースコード→構文木→実行、という流れだったが、
  1.9では処理効率を上げるため、構文木をバイトコードに変換してから独自の仮想マシン上で実行するようになった。

- 動的性

- 実行時ロード
  requireおよびloadメソッドは、動的にライブラリをロードするメソッド。

### オブジェクト
- アイデンティティを持っている
- メッセージを受け取る
- 内部状態を持つ
(「初めてのRuby」より）

### メソッド名の表記
- Object#InstaneMetohd
  「Stringオブジェクトのインスタンスメソッドeach_byte」を「String#each_byte」と書く
- Class.ClassMethod
  「Timeクラスのクラスメソッドnow」のことを「Time.now」あるいは「Time::now」と表す

### 型付け
- 
  Rubyは強く型付けされた言語なので、原則的には勝手に他の型にかわることはない。
  to_i, to_s, to_f, to_ioなどが用意されている。
### コードブロックの記述
- 
  Rubyプログラマは一般に複数業にわたるコードブロックに対してはdo/endを、
  一行のものにはブレースを使うという規約を採用している。

