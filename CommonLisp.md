# CommonLisp
## Implementations
### Steel Bank Common Lisp

#### Link
- [[http://sbcl.org/][Steel Bank Common Lisp]]

### Clozure CL

#### Link
- [[http://ccl.clozure.com/docs/ccl.html][Documentation]]

## Functions
### setf, steq
- 
  データをセットする。CommonLispではsetfが推奨されている。
  複数の変数に対し値の割り当てが可能。

- 配列への代入
  arefと組み合わせる。
  ex) (setf (aref a 1 2) 10) (配列aの2行3列目に代入)

- 属性リスト
  ex) (setf (get '太郎 'height) 180)
      (setf (get '太郎 'weight) 80) 

### ', quote
- 
  引数を評価しないようにするための関数。
  引用符は関数quoteの省略形で、'xは(quote x)と同じ。

### first, rest, car, cdr
- 
  first(car)はリストの第1要素を取り出し、
  rest(cdr)は先頭要素を除いたリストを返す。
  CommonLispではfirstとrestの使用が推奨されている。

- 
  carやcdrを組み合わせてcadr, caddr, caarなども使える。
  CommonLispでは、cadrはsecond, caddrはthird等を使うとよい。
  tenthまでは用意されている。

### cons
- 
  リストの先頭にデータを付け加える。
  ex) (cons 'a '(b c)) => (a b c)

### list
- 
  引数を要素とする新しいリストを返す。
  ex) (list 'a 'b '(c d)) => (a b (c d))

### append
- 
  リスト同士を接続する。
  そのため、listと異なり引数はリストでなければいけない。
  ex) (append '(a b) '(c d)) => (a b c d)

### defun
- 
  関数定義をする。
  (defun 関数名 (仮引数名 ...) 処理1 ... 処理M)

### read
- 
  データを読み込んでS式に変換して返す。
  データを読み込むだけで、S式の評価は行わない。

- ストリームの場合
  read 入力ストリーム eof-err eof-value
  eof-err   : ファイルの終了を検出した場合の処理指定
  eof-value : ファイルの終了を検出した場合の返り値

  eof-errを省略したりnil以外の値を指定するとファイル終了時にエラーが発生する。
  eof-errにnilを指定した場合、ファイルが終了するとeof-valueに設定した値を返す。
  eof-valueが省略された場合はnilを返す。

### print, prin1, princ
- print
  エスケープコードをつかって印字される。
  たとえば、文字列は""でくくられる。
  改行してからデータを出力し、最後に空白文字をひとつ付ける。

  ストリームの場合、print data 出力ストリームと指定する。

- prin1
  printと異なり改行と空白文字を付加しない。

- princ
  エスケープコードを使わないで出力する。

### terpri
- 
  改行が出力される。
  terminal printの略。
  
### format
- 
  format 出力ストリーム 書式文字列 S式 ...

  第1引数出力ストリームにtが指定された場合は標準出力へ出力される。
  nilが指定された場合は、ストリームに出力せず変換結果を文字列にして返す。
  
  第2引数書式文字列で、文字列の途中にチルダ~が表れると、
  その後ろの文字を変換指示子として理解し、引数のS式をその指示にしたがって表示する。
  また、チルダと変換指示子の間に前置パラメータやコロン修飾子、アットマーク修飾子を指定できる。

- 変換指示子
  ~D : 10進数
  ~X : 16進数
  ~O : 8進数
  ~B : 2進数
  ~R : N進数（指定された基数で表示する）
  ~A : 任意のS式を出力する。princと同じ形式。
  ~S : print1と同じ形式。
  ~% : 改行
  ~~ : チルダ
  
- 前置パラメータ
  数字をおくと、フィールド幅を設定できる。
  ex) *format t "[~4D]" 10)
      ⇒ [  10]
  複数の前置記号をおく場合は、カンマ(,)で区切る。
  クォート(')は前置パラメータを文字として指定するときに用いる。
  ex) (format t "[~4,'aD]" 10)
      ⇒ [aa10]
  引数としてVを指定すると、引数の値が前置パラメータとして用いられる。
  'Vとすると、V埋めとなるのでクォートはいらない。
  ex) (dotimes (x 4)
          (format t "~V,VD~%" (+ 4 x) (elt "abcd" x) 10))
      ⇒ aa10
         bbb10
         cccc10
         ddddd10
- @修飾子
  符号が表示される。
- :修飾子
  3桁ごとにカンマが表示される

#### formatの便利機能
- 
  普通使わないかもしれないが。。。
- ~(str~)
  英大文字小文字変換を行う。間に挟まれた書式文字列が処理され、その結果の文字列が変換される。
  - ~(
    英大文字を小文字に変換する。
  - ~:@(
    英小文字を大文字に変換する。
  - ~:(
    すべての単語の先頭文字を大文字にする。
  - ~@(
    先頭の単語だけcapitalizeし、残りを小文字にする。

- ~[str0~;str1~; ...~;strn~:;default~]
  ~[と~]の間に挟まれた書式文字列をひとつ選択して実行する。
  引数の値が0であればstr0が、nであればn番目のstrnが選択される。
  範囲外であればdefaultが選択される。

 ~:[false~;true]
  引数がnilであればfalseを選択し、そうでなければtrueを選択する。

  ~@[true]は引数がnilでなければtrueを選択する。

  ~と[との間に#を用いると、#がまだ処理されていない引数の個数をあらわすため、
  引数によって出力を変更することができる。
  ex) (format t "~#[none;bar~A~;bar~A_~A~:;bar_many~] 10)
      ⇒ bar10
      (format t "~#[none;bar~A~;bar~A_~A~:;bar_many~] 10 100)
      ⇒ bar10_100
      (format t "~#[none;bar~A~;bar~A_~A~:;bar_many~] 10 100 1000)
      ⇒ bar_many

- ~{str~}
  strを繰り返す。引数はリストでなければならない。

  ~と{の間に繰り返しの回数を指定できる。
  ex) (format nil "~2{ <~A, ~A> ~}" '(a 1 b 2 c 3))
      ⇒ " <a, 1> <b, 2> "

  ~:{とすると、入れ子になったリストを用いることができる。
  ex) (format nil "~2{ <~A, ~A> ~}" '((a 1) (b 2) (c 3)))
      ⇒ " <a, 1> <b, 2> <c, 3> "

  ~@{は引数にリストを用いるのでなく、残りの引数をすべて繰り返しに適用する。
  ex) (format nil "~4@{ ~A,~} ~4D" 1 2 3 4 5)

  ~:@{str~}は、~@{のように残りの引数が用いられるが、~:{のようにリストでなければならない。
  ex) (format nil "~:@{ <~A,~A> ~}" '(a 1) '(b 2) '(c 3))
      ⇒ " <a, 1> <b, 2> <c, 3>

- ~*
  次の引数を無視する。
  ~n*のように整数値nが指定された場合はn個の引数を無視する。
  ~:*は処理した引数を元に戻す。つまり直前に処理した引数が再び処理される。
  ~n:*はn個の引数が元に戻される。

### eval
- 
  S式を評価する。

### let, let*
- 
  レキシカルスコープを宣言してS式を実行する。
  (let ((変数１ 初期値１)
        (変数２ 初期値２)
        ...
        (変数Ｍ 初期値Ｍ))
       Ｓ式１
       ...
       Ｓ式Ｍ)

- let*
  let*はletと同様レキシカル変数を定義するが、変数の初期化が逐次的に行われる。
  つまり、先に初期化された変数の値を参照することが出来る。

### progn
- 
  与えられたS式を順番に実行し、最後に評価した値を返す。
  ifのthen節やelse節は複数のS式を受け付けないので、prognを使うと便利。

- prog1, prog2
  prog1は最初に評価したS式の値が返り値となる。
  同様にprog2は2番目に評価したS式の値が返り値となる。

### make-array
- 
  (make-array dimensions)
  dimensionsの数字で要素の数が、引数の数で次元が決まる。
  ex) (make-array '(2 3 4))
      => (((nil nil nil nil) (nil nil nil nil) (nil nil nil nil))
          ((nil nil nil nil) (nil nil nil nil) (nil nil nil nil)))

- :initial-element
  各要素の初期値を設定するキーワード。
- :initial-contens
  各要素の初期値を個別に設定する。
- :fill-pointer
  0からベクタのサイズまでの整数値とtを指定できる。
  tをしていするとベクタの最大サイズとなる。
- :adjustable
  ベクタの大きさを動的に変更できるように設定する。

### aref
- 
  (aref array subscripts ...)
  subscripts(添え字)部分の値をarrayから取り出す。

### vector-push, vector-pop
- 
  (vector-push item vector)
  vectorにitemをプッシュする。
  スタックが満杯のときはnilを返す。

  (vector-pop vector)
  vectorからitemをポップする。

- 
  make-arrayする際に、fill-pointerキーワードを0以外に設定しておく必要あり。

### vector-push-extend
- 
  (vector-push-extend item vector &optional extension)
  ベクタを拡張するvector-push。extensionはベクタに追加する要素の個数を指定する。
  make-arrayでキーワード:adjustableにnil以外の値を設定しておく必要がある。

### 数値計算
#### float
- 
  整数や分数を浮動小数点数に変換する。
  ex) (float 1/3) => 0.33333333

#### floor

#### ceiling

#### truncate
- 
  小数点以下を切り捨てる

#### round
- 
  近いほうの整数に丸める。
  ちょうど0.5の場合には偶数方向に丸める。

#### 1+, 1-
- 
  1+は引数に1を加え、1-は引数から1を引く。

#### incf, decf
- 
  インクリメント/デクリメントした値をセットする。

  (incf a)   ≡ (setf a (1+ a))
  (incf a n) ≡ (setf a (+ a n))
  (decf a)   ≡ (setf a (1- a))
  (decf a n) ≡ (setf a (- a n))

#### gcd, lcm
- 
  gcdはすべての引数の最大公約数を返す。
  lcmはすべての引数の最小公倍数を返す。

  ex) (gcd 63 42 35) => 7
      (lcm 1 2 3 4 5) => 60

### 条件分岐
#### equal
- 
  2つの引数が同じ値か調べる。
  類似の関数は eq < eql < equal < equalp の順で条件がゆるくなる。

  ex) (equal (+ 1 2 3) 7)       => t
      (equal 4 4.0)             => nil ;型が違うとダメ
      (equal '(a b c) '(a b c)) => t

#### eq
- 
  2つの引数がまったく同じかどうか調べる。
  コンピュータのメモリ番地を調べる。。
  ex) (eq 'a 'a)       => t
      (eq 1d100 1d100) => nil

#### eql
- 
  同じ型で同じ値の数値や、同じ値の文字であれば真。

#### equalp
- 
  型が違っても同じ値の数値、文字や文字列では英大小文字を区別しない、
  equalpを満たすリストや配列であれば真を返す。

#### not
- 
  否定。引数がnilならtを返し、それ以外ならnilを返す。

#### if
- 
  (if <条件部> <then節> <else節>)
  条件部を評価し、その結果が真ならばthenを評価する。
  条件部が偽ならばelse節を評価する。else節は省略できる。

#### when, unles
- when
  (when test S式1 S式2 S式3 ...)
  whenは最初にtestを評価し、その結果がnilであればその後ろのS式を評価せずnilを返す。
  そうでなければ、S式を順番に評価し、最後のS式の結果を返す。
- unless
  whenの逆。testが偽のときにS式を順番に評価する。
  (unless test S式1 ...) ≡ (when (not test) S式1 ...)

#### cond
- 
  (cond ( 条件部A S式A1 S式A2 ...)
        ( 条件部B S式B1 S式B2 ...)
              ...
        ( 条件部M S式M1 S式M2 ...)
        ( t       S式T1 S式T2 ...))

  複数の節を引数として受け取る。
  各節の先頭には条件をチェックする述語があり、
  条件が成立した場合、残りのS式を評価する。
  条件が不成立であれば、次の節に移る。
  一番最後に評価されたS式の返り値がcondの返り値となる。
  

#### evenp, oddp
- 
  evenpは引数が偶数であればtを返す。
  oddpは引数が奇数であればtを返す。

#### 数値比較

##### = 
- 
  (= N1 N2 N3 ... )
  引数がすべて等しければt、それ以外であればnil
  equalでは数値の型が違うとnilとなったが、
  =では引数の方を区別せず等しいかどうか調べることができる。

##### /=
- 
  (/= N1 N2 N3 ... )
  引数がすべて等しくなければt、それ以外はnil

##### <, >, <=, >=
- 
  (< N1 N2 N3 ... )
  引数が左から単調増加していればt、それ以外であればnil。
  その他も

#### データ型を調べる述語

##### atom
- 
  アトムか？
  リストに対してはnilを返すが、空リスト/nilに対してはtを返す。

##### numberp
- 
  数値か？

##### integerp
- 
  整数か？

##### floatp
- 
  浮動小数点数か？

##### symbolp
- 
  シンボルか？

##### stringp
- 
  文字列か？

##### listp
- 
  リストか？
  nilはt。( (listp nil) => t)

##### consp
- 
  コンスセルか？
  nilは偽と判断される。


##### typep
- 
  型指定子を使ってデータ型を調べる。
  ex) (typep '(a b c) 'list) => t
      (typep '100 'float)    => nil

##### type-of
- 
  引数のデータ型を型指定子で返す。
  ex) (type-of '(a b c)) => cons
      (type-of "abcdef") => simple-string

### mapcar
- 
  渡された関数をリストの各要素に適用して、その結果をリストに格納して返す。
  (mapcar #'* '(1 2 3 4 5) '(10 20 30 40 50)) => (10 40 90 160 250)

### #', function
- 
  functionは特殊形式で、シンボルに格納されている関数を取り出す働きをする。
  「#'+」であれば「(function +)」の省略形。

### apply
- 
  (apply function args-list)
  最初の引数funcを第2引数に適用して、その結果を返す。
  第2引数はリストの必要あり。
  ex) (apply #'+ 4 5 6 '(1 2 3)) => 21

### funcall
- 
  (funcall func args ...)
  最初の引数funcを残りの引数argsに適用し、結果を返す。

### lambda
- 
  構文自体はdefunと同じ。
  無名関数。
  (lambda
      (<仮引数名> ... )
          処理1
          処理2
          ...
          処理M)

### char
- 
  char string index
  文字列stringからindexの位置の文字を取り出す。

### char-code, code-char
- char-code
  文字を整数値に変換する。

- code-char
  整数値を文字に変換する。

### 列関数
- 列関数の主なキーワード
  |------------------+--------------------------------------|
  | キーワード       | 機能                                 |
  |------------------+--------------------------------------|
  | :start, :end     | 始点と終点を指定                     |
  | :test, :test-not | 述語の指定                           |
  | :key             | 比較するときのキーにアクセスする関数 |
  | :count           | 個数の制限                           |
  | :from-end        | 列の後ろから処理を行う               |
  |------------------+--------------------------------------|

#### elt
- 
  elt sequence index
  index番目の要素を返す

#### subseq
- 
  subseq sequence start [end]
  startからendまでの部分列を取り出す。endを省略すると最後尾までが範囲となる。

#### copy-seq
- 
  copy-seq sequence
  列のコピー((subseq sequence 0)と同じ)

#### length
- 
  length sequence
  列の長さを返す

#### reverse
- 
  reverse sequence
  要素を逆順にした新しい列を返す

#### make-sequence
- 
  make-sequence type size
  型がtypeで長さがsizeの列型データを生成する
  :initial-elementを指定するとその値で初期化される。

#### 列の探索
- 
  |-------------------------------------+-------------------------------------|
  | 関数名                              | 機能                                |
  |-------------------------------------+-------------------------------------|
  | find item sequence                  | itemと等しい最初の要素を返す        |
  | find-if predicate sequence          | predicateが真となる最初の要素を返す |
  | find-if-not predicate sequence      | predicateが偽となる最初の要素を返す |
  | position item sequence              | itemと等しい最初の位置を返す        |
  | position -if predicate sequence     | predicateが真となる最初の位置を返す |
  | position -if-not predicate sequence | predicateが偽となる最初の位置を返す |
  | count item sequence                 | itemと等しい要素の個数を返す        |
  | count-if predicate sequence         | predicateが真となる要素の個数を返す |
  | count-if-not predicate sequence     | predicateが偽となる要素の個数を返す |
  |-------------------------------------+-------------------------------------|

#### 列の修正
- 
  |----------------------------------+------------------------------------------|
  | 関数名                           | 機能                                     |
  |----------------------------------+------------------------------------------|
  | remove item sequence             | itemと等しい要素を取り除く               |
  | remove-if predicate sequence     | predicateが真となる要素を取り除く        |
  | remove-if-not predicate sequence | predicateが偽となる要素を取り除く        |
  | remove item sequence             | oldと等しい要素をnewに置き換える         |
  | remove-if predicate sequence     | predicateが真となる要素をnewに置き換える |
  | remove-if-not predicate sequence | predicateが偽となる要素をnewに置き換える |
  | fill sequence item               | 列の要素をitemで置き換える               |
  | remove-duplicates sequence       | 列の重複した要素を取り除く               |
  |----------------------------------+------------------------------------------|

- 
  fillは破壊的。他にdelete、nsubstituteなども同様。

- :count
  処理する要素の個数を指定する。

- :from-end
  後ろから処理する。

- remove-duplicates
  等しい要素が複数ある場合、最後の要素だけが残る。
  :from-endをtとしておくと、一番前の要素だけが残ることとなる。
  delete-duplicatesを用いると破壊的な処理となる。

#### マッピング
- 
  |----------------------------------------+--------------------------------------------------|
  | 関数名                                 | 機能                                             |
  |----------------------------------------+--------------------------------------------------|
  | map result-type func sequences ...     | 列の要素にfuncを適用し結果を列に格納して返す     |
  | map-into result-seq func sequences ... | 列の要素にfuncを適用し結果をresult-seqに代入する |
  |----------------------------------------+--------------------------------------------------|

#### 列の連結
##### concatenate
- 
  concatenate result-type sequences ...
  引数を連結した結果をresult-typeで指定した列で返す。
  result-typeには普通list, string, vectorのどれかを指定する。

#### 縮約
##### reduce
- 
  reduce function sequence
  sequenceの各要素に対して、関数を左側の2項から順次適用していく。
  :from-back tの場合は右側から順次適用する。
  


##### find

#### ソートとマージ
- 
  |-----------------------------+------------------------|
  | 関数名                      | 機能                   |
  |-----------------------------+------------------------|
  | sort sequence predicate     | sequenceをソートする   |
  | merge result-type seq1 seq2 | seq1とseq2をマージする |
  |-----------------------------+------------------------|

- sort
  ex) (sort '(1 4 2 5 3 8 7 6) #'<)
        => (1 2 3 4 5 6 7 8)

- merge
  ソート済みの列をマージするのが本来。
  ex) (merge 'list '(1 3 5 2 4) '(2 4 6 1 3) #'<)
        => (1 2 3 4 5 2 4 6 1 3)

#### 列の破壊的修正

- 
  |-------------------------------------+------------------------------------------|
  | 関数名                              | 機能                                     |
  |-------------------------------------+------------------------------------------|
  | nreverse sequence                   | 要素を逆順にした列を返す                 |
  | replace seq1 seq2                   | 列seq1を列seq2の要素に置き換える         |
  | delete item sequence                | itemと等しい要素を取り除く               |
  | delete-if predicate sequence        | predicateが真となる要素を取り除く        |
  | delete-if-not predicate sequence    | predicateが偽となる要素を取り除く        |
  | nsubstitute new old sequence        | oldと等しい要素をnewに置き換える         |
  | nsubstitute-if new old sequence     | predicateが真となる要素をnewに置き換える |
  | nsubstitute-if-not new old sequence | predicateが真となる要素をoldに置き換える |
  |-------------------------------------+------------------------------------------|

- nreverse
  (nreverse a)を評価しても変数aの値が逆順になることは保証されていない。
  リストを逆順にするには、(setq a (nreverse a))のように返り値を変数に代入する。
  配列や文字列では変数の値も逆順になる。

### ファイル入出力
#### open
- 
  ファイルをオープンする

- if-exists
  既に同じ名前のファイルが存在している場合、:if-existsを使って動作を指定可能。
  :directionが:outputまたは:io(input/output両用)の場合に有効。
  省略した場合は:errorか:new-versionとなる。

  - キーワード
    :error
        エラーを発する。filenameのバージョン要素が:newestでない場合の規定値。
    :new-version
        同一のファイル名を持ち、より大きいバージョン番号を持つ、新しいファイルを生成する。
        filenameのバージョンが:newestの場合の規定値。
    :rename
    :rename-and-delete
    :overwrite
    :append
    :supersede
    nil

- if-does-not-exists
  ファイルが存在していないときの動作を指定する。

  - キーワード
    :error
        ファイルが存在していない場合にエラーとする。
        :directionに:inputを指定している場合や、:if-existsに:overwriteや:appendを指定する場合の規定値。
    :create
        新しいファイルを生成する。
        :directionが:outputまたは:ioで、:if-existsが:overwrite:appendでもない場合の規定値。
    nil
        ファイルをオープンしない。


#### close
- 
  オープンしたファイルをクローズする

#### read-line, read-char
- read-line
  ストリームから文字を読み込み、改行文字までのデータを文字列として返す。
  改行文字は文字列に含まれない。

- read-char
  ストリームより1文字読み込み、それを文字型データとして返す。

- 
  readと同様、ファイル終了時の動作を指定できる。

### リスト操作
#### リスト探索 member
- 
  |------------------------------+-------------------------------------|
  | 関数名                       | 機能                                |
  |------------------------------+-------------------------------------|
  | member item list             | itemと等しい最初の要素を探す        |
  | member-if predicate list     | predicateが真となる最初の要素を探す |
  | member-if-not predicate list | predicateが偽となる最初の要素を探す |
  |------------------------------+-------------------------------------|

  member関数はitemを見つけた場合はitem以降のリストを返す。member-if, -if-notも同じ。
  この点がfindやpositionと異なる。
  :key、:test、:test-notも指定できる。

#### リスト置換 subst
- 
  |---------------------------------+------------------------------------------|
  | 関数名                          | 機能                                     |
  |---------------------------------+------------------------------------------|
  | subst new old tree              | oldと等しい要素をnewに置き換える         |
  | subst-if new predicate tree     | predicateが真となる要素をnewに置き換える |
  | subst-if-not new predicate tree | predicateが偽となる要素をnewに置き換える |
  |---------------------------------+------------------------------------------|

#### 連想リスト
##### assoc
- 
  |-------------------------------+-------------------------------|
  | 関数名                        | 機能                          |
  |-------------------------------+-------------------------------|
  | assoc item a-list             | itemと等しいキーを探す        |
  | assoc-if predicate a-list     | predicateが真となるキーを探す |
  | assoc-if-not predicate a-list | predicateが偽となるキーを探す |
  |-------------------------------+-------------------------------|

  a-listからitemを等しい(eql)キーを探す。見つからない場合はnilを返す。
  assocはデータを返すのでなくドット対を返す。
  findの:keyにcarを指定した場合と動作はほとんど同じだが、nilの扱いが少し異なる。
  はだかのnilがあった場合、carをとってもnilであり、findでは引っかかるが、
  assocではひっかからない。
  ex) (find nil '((a . b) nil (c . d) (nil . e)) :key #'car)
      => nil
       (assoc nil '((a . b) nil (c . d) (nil . e)))
      => (nil . e)

##### rassoc
- 
  |--------------------------------+---------------------------------|
  | 関数名                         | 機能                            |
  |--------------------------------+---------------------------------|
  | rassoc item a-list             | itemと等しいデータを探す        |
  | rassoc-if predicate a-list     | predicateが真となるデータを探す |
  | rassoc-if-not predicate a-list | predicateが偽となるデータを探す |
  |--------------------------------+---------------------------------|

  assocはキーを探索するが、データを探索する関数がrassoc。

##### acons
- 
  acons key data a-list
  連想リストにデータを追加する。consでも出来るが、aconsが便利。
  (cons (cons key data) a-list)と同じ。
  
##### pairlis
- 
  pairlis key-list data-list &optional a-list
  ex) (pairlis '(a b c d) '(1 2 3 4))
      => ((d . 4) (c . 3) (b . 2) (a . 1))

##### sublis
- 
  sublis a-list tree
  a-listのキーに等しいtreeの部分を、キーに対応するデータに置き換える。
  ex) (sublis '((a . 1) (b . 2)) '(a b c (a b c . a) d . b))
      => (1 2 c (1 2 c . 1) d . 2)

#### endp
- 
  リストの終端を検査する述語。
  コンスセルに対しては偽、nilに対しては真を返す。
  それ以外のデータはエラーとなる。

#### nth
- 
  (nth 3 '(a b c d )) => d
  リストのn番目の要素を返す。
  列関数同様先頭要素が0番目となる。
  nがリストより大きい場合はnilを返す。

#### nthcdr
- 
  nthcdr n list
  listに対してn回だけcdrを適用する。
  nは非負の整数である必要がある。

#### last
- 
  last list &optional (n 1)
  リストの最後からn個のコンスセルを返す。空リストの場合はnilを返す。
  ex) (last '(a b c d))     => (d)
      (last '(a b c d . e)) => (d . e)
      (last '(a b c d) 2)   => (c d)

#### butlast
- 
  butlast list &optional (n 1)
  n個のコンスセルをリストの最後尾から除く。
  ex) (butlast '(a b c d . e) 2 ) => (a b)

#### make-list
- 
  make-list size &key :initial-element
  要素がsize個のリストを作成する。
  :initial-elementが指定されると、その値に初期化される。

#### copy-list, copy-tree
- 
  copy-list list
  copy-tree object
  copy-listはリストのトップレベルをコピーして返す。
  copy-treeはリストの木構造をコピーして返す。

#### リストの破壊的操作
##### rplaca, rplacd
- rplaca
  (rplaca cell object)
  cellのCAR部をobjectに直接書き換える。

- rpalcd
  (rplacd cell object)
  cellのCDR部をobjectに直接書き換える。

- setf
  リストの書き換えはsetfで行えるため、
  とくに上記の関数を使う必要はない。
  ex) (setf (car z) 'd) => (d b c)

##### nconc
- 
  (nconc &rest lists)
  引数のリストをつなぎ合わせたリストを返す。
  appendはコピーしたリストを返すが、nconcはCDR部を書き換える破壊的な操作。

### 属性リスト操作
#### get
- 
  get symbol key &optional default
  属性リストから属性名keyの属性値を返す。
  見つからない場合はdefaultを返す。
  defaultが場合はnilを返す。

#### remprop
- 
  remprop symbol key
  symbolの属性リストから属性名keyを削除する。
  keyが見つからない場合はnilを返す。
  keyを見つけて削除したらnil以外の値を返す。

#### symbol-plist
- 
  symbol-plist symbol
  symbolにセットされた属性リストを返す。

### ramdom
- 
  ramdom integer &optional state
  0以上integer未満の整数を返す。
  シードはrandom-state型のデータとして扱う。
  
### make-random-state
- 
  make-random-state &optional state
  random-state型のstateを生成する。
  引数stateを省略するかnilの場合、*random-state*のコピーを返す。
  stateがtの場合は、何らかの方法を用いてランダムに初期化されたrandom-state型のデータを返す。

### defmacro
- 
  (defmacro マクロ名 (仮引数 ...) S式 ...)
  マクロを定義する。構文はdefunと同様。
  下記の点がマクロの特徴。
  1. 引数は評価されない
  2. S式を順番に評価し、一番最後の評価結果を再度評価して、その結果を返す。

- 分配
  ラムダリストを入れ子にすることができる、
  ただし呼び出し時はそのラムダリストと同じリスト構造を与えなければいけない。

### macroexpand, macroexpand-1
- 
  (macroexpand form &optional env)
  (macroexpand-1 form &optional env)
  macroexpand-1は1回だけマクロを展開する。
  macroexpandは最後まで展開する。

### `(バッククォート)
- 
  バッククォートはクォートと同様引数の評価を行わない。
  だが、コンマ(,)で始まるS式があると、そのS式を評価した値で置き換えられる。
  ex) (setq var 'pen)   => pen
      `(this is a ,var) => (this is a pen)
  ,@を使うと、リストをはずした値と置き換わる。
  値がリストでなければエラーとなる。

### 集合としてのリスト操作
- 
  |------------------------------+------------------------------------------------------------------|
  | 関数名                       | 機能                                                             |
  |------------------------------+------------------------------------------------------------------|
  | union list1 list2            | list1とlist2の和を求める                                         |
  | intersection list1 list2     | list1とlist2の積を求める                                         |
  | set-difference list1 list2   | list2に現れないlist1の要素をリストにして返す                     |
  | set-exclusive-or list1 list2 | list1とlist2の両方にちょうど１つだけ現れる要素をリストにして返す |
  | subsetp list1 list2          | list1の要素がすべてlist2に含まれていれば真を返す                 |
  |------------------------------+------------------------------------------------------------------|

  :key, :test, :test-notを使うことができる。

### defstruct
- 
  (defstruct 構造体名
      (スロット名 デフォルト値)
       ...
      (スロット名 デフォルト値))

  スロットとは、構造体で定義した変数のこと。

  defstructは構造体の定義のほかに、次の関数を生成する。
  - make-構造体名   : 定義したデータを作るコンストラクタ
  - 構造体名-変数名 : スロットの値をリードするアクセス関数
    - スロットへの書き込みはsetfとアクセス関数で行うことが出来る。
  - copy-構造体名   : データをコピーする関数
  - 構造体名-p      : データ型を判定する述語

- オプション
  (defstruct (name (option1 data1) (option2 data2) ...) ...)

  |--------------+------------------------------------|
  | オプション名 | 機能                               |
  |--------------+------------------------------------|
  | :conc-name   | アクセス関数の前に付ける名前を指定 |
  | :constructor | コンストラクタ関数の名前を指定     |
  | :copier      | コピー関数の名前を指定             |
  | :predicate   | 型を判定する述語の名前を指定       |
  | :include     | 既存の構造体を取り込む             |
  |--------------+------------------------------------|

  includeした場合でもデフォルト値は変更できる。

- :constructorの定義
  次の書式で、標準とは異なるコンストラクタを定義できる。
  (:constructor name arglist)
  ex) (destruct (foo (:constructor create-foo (a b))) a b)
  
  複数回用いることが出来るため、異なるコンストラクタを生成できる。
  arglistの中で&key, &optional, &rest, &auxを使用可能。
  
  CLISP(ver2.44)とSBCL(ver1.0.29)はmake-fooを生成しないので注意。

### split-string
- 
  (split-string string separator &optional ignore-empty char-bag)
  文字列stringを区切り文字separatorで分割し、リストに格納して返す。
  separatorに文字列を与えると、文字列の文字が区切り文字に指定される。

### 文字列の比較
- 
  (string=  string1 string2)
  (string<  string1 string2)
  (string>  string1 string2)
  (string<= string1 string2)
  (string>= string1 string2)
  (string/= string1 string2)

  英大文字小文字を区別して比較する。
  条件を満たした場合、string=はt、それ以外は条件を満たす最初の文字位置を返す。
  条件を満たさない場合はnilを返す。

- 
  (string-equal        string1 string2)
  (string-lessp        string1 string2)
  (string-greaterp     string1 string2)
  (string-not-greaterp string1 string2)
  (string-not-lessp    string1 string2)
  (string-not-equal    string1 string2)

  英大文字小文字を区別しない。

- 
  :start1, :end1, :start2, :end2を指定できる。
  引数にシンボルを与えると、シンボルを文字列に変換してから比較を行う。

### defvar
- 
  (defvar symbol [initial-value [doc-string]])
  defvarはシンボルsymbolをスペシャル変数として宣言する。
  initial-valueとdoc-stringは省略可能。initial-valueを設定するとその値に初期化される。
  doc-stringには、変数の意味を説明する文字列を与えられる。

  また、defvarでスペシャル変数を宣言すると、その変数はダイナミックスコープで管理される。

### defconstant
- 
  (defconstant symbol value)
  スペシャル変数で定数を定義する。

### block
- 
  (block name S式 ...)
  S式を左から右へ順番に評価し、最後に評価されたS式を返す。
  S式の評価中にnameと同じシンボルを指定したreturn-fromが評価されると、
  それ以降のS式の評価を中止してreturn-fromが評価した値をblockの評価値として返す。

### return-from
- 
  (return-from name [result])
  引数nameは評価されずシンボルでなければいけない。
  return-fromはresultの評価結果を返す。resultが省略された場合はnilを返す。

  blockのnameにnilを用いた場合、return-fromだけでなくreturnでも脱出できる。
  doやwhileなどからreturnで脱出できるのはblock nil内で定義されているから。
  また、nameの有効範囲はレキシカルスコープ。

  defunで定義された関数には暗黙の内に関数名と同じ名前のblockがおかれており、
  return-fromで関数名を指定すると繰り返しの中にいても抜け出せる。

### tagbody, go
- tagbody
  (tagbody name-or-form ... )
  tagbodyはgoのラベルとして使用されるシンボル(name)と、評価されるフォーム(S式のこと)からなる。
  nameは評価されない。formを順番に評価し、最後まで評価するとnilを返す。
  内部でgoが評価された場合、goで指定されたnameに分岐しそこから評価を続ける。

- go
  (go name)
  tagbody内で使用され、実行の制御のnameでラベル付けされた場所へ移す。
  nameはシンボルでなくてはいけない。goでジャンプできる有効範囲はレキシカルスコープ。

### catch, throw
- 
  (catch tag-name S式)
  (throw tag-name result)
  catchとthrowを使って評価中の関数から他の関数へ制御を移すことが出来る。これを大域脱出(global exit)という。
  catchとthrowは特殊形式で、catchが受け手でthrowが投げ手。

  catchは最初にtag-nameを評価する。評価結果はシンボルでなければならない。
  throwはtag-nameを評価し、それと同じシンボルを持つcatchを探し、
  resultを評価した結果を持って見つけたcatchへジャンプする。

### unwind-protect
- 
  (unwind-protect protected-form cleanup-form ...)
  protected-formを評価した後cleanup-formを評価する。
  protected-formの評価中にエラーや大域脱出などで処理が中断されても、
  cleanup-formは必ず評価される。
  cleanup-formは複数のS式を指定できる。
  proteced-formの評価結果がunwind-protectの返り値となる。

### labels
- 
  (labels
    ((func1 (args ...) body1)
     (func2 (args ...) body2)
     ...)
    labels-body)

  最初に関数を定義して、labels-bodyを評価する。
  関数は複数定義できるが、呼び出すことが出来るのはlabels-bodyの中だけ。

### symbol-list
- 
  (symbol-value symbol)
  引数symbolの値を返す。
  最もローカルなバインディングか、バインドされていない場合はグローバル値を返す。

### symbol-value
- 
  シンボルを引数に取り、対応するスペシャル関数を返す
  
### symbol-function
- 
  グローバル関数に対し、対応する値を返す。
  
## Macros
### and, or
- and
  andは複数の述語を「～かつ～」で結ぶ働きをする。
  S式を左から順番に評価し、評価結果がnilであれば、残りのＳ式を評価せずnilを返す。
  最後までS式がnilでなければ、最後のS式の評価結果を返す。
- or
  orは複数の述語を「～または～」で結ぶ働きをする。
  S式の評価がnil以外の場合に、、残りのS式を評価せずその結果を返す。
  すべての結果がnilの場合はnilを返す。

### case
- (case keyform {normal-clause}* [otherwise-clause] => result*
  
### dotimes
- 
  (dotimes (var limit result) S式 ...)
  dotimesは最初にlimitを評価し、0からlimitまでが順次varに代入されS式を評価する
  varはレキシカル変数として扱われ、dotimesが評価されている間だけ有効。
  最後にresultが評価され、その値がdotimesの返り値と成る。
  resultが省略された場合はnilを返す。
  
### dolist
- 
  (dolist (var init-form result) S式 ...)
  init-formとしてリストをとり、リストの要素がvarに代入されてS式が評価される。
  リストの要素がなくなったらresultを評価し、その値がdolistの返り値となる。

### loop
- 
  与えられたS式をずっと繰り返し評価する。
  繰り返しから抜けるためにはreturnを使う。

### return
- 
  引数をひとつ与えることが出来る。
  returnが評価されると繰り返しが中断され、与えられた引数が評価され繰り返しの返り値となる。
  引数が省略された場合はnilが返り値となる。

### do
- 
  (do ((var [init-form [step-form]]) ...) (end-test [result]) S式 ... )
  1. 変数varをinit-formの評価結果に初期化。init-formがない場合はnil。
  2. end-testを評価し、結果が真であれば繰り返しを終了する。
     resultを評価し、その結果がdoの返り値となる。resultがない場合はnilを返す。
  3. 本体のS式を順番に評価する。
  4. 変数varの値をstep-formの評価結果に更新する。step-formがない場合は何もしない。
  5. 2から4までを繰り返す。

### push, pop
- push
  push item place
  pushは変数placeに格納されているリストの先頭にitemを追加し、その結果を返す。
- pop
  pop place
  popは変数placeに格納されているリストの先頭要素を返し、
  先頭要素を取り除いたリストをplaceにセットする。

### with-open-file
- 定義
  (with-open-file (変数
                   ファイル名
                   :direction [:input or :output])
     ... )

- 
  openとcloseをおこなってくれるマクロ。
  :directionで指定した方向でオープンし、生成したストリームを変数にセットする。
  変数は局所変数として扱われ、with-open-fileが実行されている間だけ有効。
  S式を順番に評価し、with-open-fileの実行が終了すると自動的にファイルがクローズされる。
## Memo
### Lispのデータ構造
- 
  S式 ─┬─ アトム─┬─ 整数値
        │           │
        │           ├─ 文字列
        │           │
        │           ├─ シンボル
        │           │
        │           ├─ ...
        │
        └─ リスト

### list
- 
  括弧でくくられたもの

### cons cell
- 
  1つのコンスセルには、データを格納するCARと、連結部のCDRがある。

### atom
- 
  リストでない要素。

### シンボル
- 
  名前、関数定義、変数、属性リストが格納されている。

  シンボルは、関数と変数の値を別々に格納しているため、
  関数を変数から引っ張りして使うには、funcall等を使う必要がある。

### 真偽値
- t
  真を意味するシンボル
- nil
  偽を意味するシンボル。()をも意味する。
- 真偽判定
  Lispでは、nil以外のデータを真、nilを偽と判定する。

### ドット対 dotted pair
- ドット対
  cdr部にデータが入っているペアをドット対という。
  構造がドットで表現される。
  ex) (a . b)

- ドットリスト dotted list
  終端がnil以外のアトムのリスト。
  ex) (a b c . d) ≡ (a . (b . (c . d)))

### 数
#### 整数
- 
  CommonLispの場合、整数の大きさに制限はない。
  ただし、その処理系で効率よく表せる整数をfixnum、それ以外をbignumという。
  fixnumの範囲は処理系依存だが、most-negative-fixnumとmost-positive-fixnumで確認できる。

- 10進数以外の表記
  #nnrdddd または #nnRdddd, nnが基数(2-32)を表す。
  よく使うものは省略形がある。
  - 2進 : #b
  - 8進 : #o
  - 16進 : #x

  ex) #4r123 => 27
      #b1010 => 10
      #o1234 => 668
      #xabcd => 43981

#### 分数

- 
  分数は、二つの整数を/で区切って表す。
  また、4/6や3/12、4/2等の約分文できるものは約分される。
  ex) 1/2, 4/6 => 2/3, 10/5 => 2

#### 浮動小数点数
- 
  処理系によって複数の種類を持つことが出来る。
  CommonLispでは以下の値が推奨されている。
  
  |----------------------+----------+--------------------+------------|
  | 形式                 | 最小精度 | 最小の指数の大きさ | 指数マーカ |
  |----------------------+----------+--------------------+------------|
  | 小精度(short-float)  | 13ビット | 5ビット            | s, S       |
  | 単精度(single-float) | 24ビット | 8ビット            | f, F       |
  | 倍精度(double-float) | 50ビット | 8ビット            | d, D       |
  | 長精度(long-float)   | 50ビット | 8ビット            | l, L       |
  |----------------------+----------+--------------------+------------|

#### 複素数
- 
  #Cの後ろに実部と虚部のリストをつけて表す。
  ex) #C(5 -3)
      #C(1.2 2/3)

### 変数のスコープ
- レキシカル変数(Lexical variable)、局所変数
  関数の内部だけ保存されるような変数。
  関数の仮引数、およびletで定義された変数はレキシカル変数となる。

- スペシャル変数(Special variable)、グローバル変数
  一時的でない変数。レキシカル変数がなければ使われる。
  スペシャル変数は*で囲む慣習がある。*x*など。

- Common Lispのスコープ
  伝統的なLispはダイナミックスコープだが、Common Lispはレキシカルスコープ。
  ちなみにSchemeはレキシカルスコープ、Emacs Lispはダイナミックスコープ。

- レキシカルスコープ
  関数foo1からfooを呼んだとしても、関数fooからfoo1へはアクセスできない。
  ただし、関数内で定義されたラムダ式については、範囲内のレキシカル変数にアクセスできる。

- ダイナミックスコープ
  関数foo1で定義された変数xは、foo1の実行が終了するまで存在し、
  foo1から呼ばれた関数ならばどこからでもアクセスできる。
  defvarで宣言した変数は、ダイナミックスコープとして管理される。

### 型指定子
- number  : 数値
- integer : 整数
- float   : 浮動小数点数
- symbol  : シンボル
- string  : 文字列
- list    : リスト
- cons    : コンスセル

- 
  （listとconsは、関数のほかに型指定子としての役割も持っている。）

### keyword
- 
  コロンから始まる引数を"キーワード"という。
  キーワードの次にキーワード引数をとる。

### 列
- 
  Common Lispはリスト(list)、文字列(string)、ベクタ(vector)を列(sequence)として統一的に扱うことが出来る。

### 配列
- 
  make-arrayを使って生成する。
  特に1次元の配列をベクタ(vector)といい、#(...)で表示される。

### 文字
- 
  文字列から取り出した要素は文字(character)として扱われる。
  #\に続けて文字自身を書いて表す。

- #\LFD
  改行を表す文字。
  整数値だと#x0a。

### ラムダリストキーワード
- 
  |--------------+----------------------------------|
  | キーワード名 | 機能                             |
  |--------------+----------------------------------|
  | &optional    | 引数のデフォルト値を設定         |
  | &rest        | 引数をリストにまとめて関数へ渡す |
  | &key         | キーワードの設定                 |
  | &aux         | 補助変数の指定                   |
  |--------------+----------------------------------|

- 
  同時に使う場合、引数の後ろに&optional、その後で&rest、
  最後に&keyと&auxを定義するようにする。

#### &optional
- 
  省略された場合にデフォルト値を設定する。
  (パラメータ デフォルト値)で設定。

#### &rest
- 
  複数個のパラメータを1つのシンボルで受ける。

#### &key
- 
  キーワードを設定できる。
  デフォルト値も設定できるので、
  複数個のオプションパラメータを使う場合キーワードにすると便利。

#### &aux
- 
  どの実引数にもマッチせず、
  let*でレキシカル変数を定義することと同じ働きをする。

### 連想リスト
- 
  ((a . b) (c . d) (e . f) (g . h))
  a, c, e, gがキーで、b, d, f, hがデータと成る。

### 属性リスト
- 
  (key1 data1 key2 data2 ... )
  上記のように、キーとなるシンボル（属性名）とデータ（属性値）が交互に配置されたリスト。
  setfで設定、getで取得、rempropで削除する。

### 構造体
- 
  ユーザが既存のデータ型を組み合わせて、新しいデータ型を定義する機能。
  defstructを使って定義する。

### 循環リスト
- 
  #n=によりLispデータにラベルを付けられる。nは整数値。
  #n#でそのデータを参照できる。
  #1=(a b c . #1#) という形で循環リストを作成できる。

  printなどで循環リストを表示すると停止しなくなるが、
  *print-circle*の値を真にするとprintでも循環リストを表示できる。

### クロージャ
- 
  クロージャは関数だけでなく、そのときに有効なレキシカル変数とその値も取り出して保存する。
  環境(environment)とは、有効なレキシカル変数が収められた連想リストのようなもの。
  クロージャを評価するときは、取り出した関数をこの「環境」で評価する。
  functionの返り値。

### 名前空間
- 
  変数と関数で異なった名前空間がある。
  関数呼び出しの先頭か#'の次に来ると関数への参照、
  それ以外では変数名と見なされる。

### 関数
- 関数は普通のデータオブジェクトなので、変数が値として保持できる。
  ex)
  (setq x #'append)
  (eq (symbol-value 'x) (symbol-function 'append))
  ⇒T

## Link
- [[http://www.lispworks.com/documentation/HyperSpec/Front/index.htm][Common Lisp Hyper Spec - LispWorks]]
- [[http://ep.yimg.com/ty/cdn/paulgraham/onlisp.pdf][On Lisp(PDF)]]
- [[http://modern-cl.blogspot.jp/][Modern Common Lisp (Ariel Labs)]]
- [[http://www.geocities.co.jp/SiliconValley-Oakland/1680/xyzzy_lisp.html][xyzzy Lisp Programming - M.Hiroi's Home Page]]
