# Excel
## Functions 関数
### 互換性関数
- より精度が高く、適切な名前を持つ新しい関数に置き換えられている。
#### (obsolete)FLOOR
### キューブ関数
### データベース関数
### 日付と時刻の関数
#### DATE
- 
  =DATE(年,月,日)
#### DATEDIF
- 
  2つの日付間の日数、月数、年数を計算する。
  Lotus 1-2-3との互換性を維持するために用意されている。
- Format
  DATEDIF(開始日,終了日,単位)
  - 単位 : "Y","M","D","MD","YM","YD"
- 例
  =DATEDIF(2001/01/01,2003/01/01,"D")

#### DATEVALUE
#### DAY
- シリアル値を日付に変換する
#### DAYS
- 2つの日付間の日数を返す
#### DAYS360
#### EDATE
- 開始日から起算して、指定した月数だけ前または後の日付に対応するシリアル値を返す。
#### EOMONTH
- 開始日から起算して、指定した月数だけ前または後の月の最終日に対応するシリアル値を返す。
- EOMONTH(開始日、月)
#### HOUR
#### MINUTE
#### MONTH
#### NOW
#### SECOND
#### TIME
#### TODAY
#### WEEKDAY
- 
  与えられたシリアル値(日付)に対し、何曜日を表しているかを表す数字を返す。
  =weekday(シリアル値,種類)
  
- 返り値の種類
  |--------------------+------------------|
  |        2つ目の引数 | 値と曜日の関係   |
  |--------------------+------------------|
  | 1 又は省略した場合 | 1(日曜)～7(土曜) |
  |                  2 | 1(月曜)～7(日曜) |
  |                  3 | 0(月曜)～6(日曜) |
  |--------------------+------------------|

#### WORKDAY
- 
  開始日から起算して、指定された稼働日数だけ前または後の日付に対応する値を返す。

- 書式
  WORKDAY(開始日, 日数, [祝日])

#### YEAR
### エンジニアリング関数
### 財務関数
### 情報関数
#### CELL
- セルの書式、位置、内容についての情報を返す。
- 書式
  CELL(検査の種類,[対象範囲])
  - 検査の種類
    - 
      |---------------+----------------------------------------------|
      | 検査の種類    | 戻り値                                       |
      |---------------+----------------------------------------------|
      | "address"     | 対象範囲の左上隅にあるセルの参照を表す文字列 |
      | "col"         | 対象範囲の左上隅にあるセルの列番号           |
      | "color"       |                                              |
      | "contents"    | 対象範囲の左上にあるセルの値（数式でない）   |
      | "filename"    | 対象範囲を含むファイルのフルパス名（文字列） |
      | "format"      |                                              |
      | "parentheses" |                                              |
      | "prefix"      |                                              |
      | "protect"     |                                              |
      | "row"         |                                              |
      | "type"        |                                              |
      | "width"       |                                              |
      |---------------+----------------------------------------------|
      
#### ERROR.TYPE
#### INFO
- 現在の操作環境についての情報を返す。
  ※Excel Onlineでは使用不可。
- 書式 :
  INFO(検査の種類)
  - 検査の種類
    必ず指定する。情報の種類を文字列で指定する。
    - 
      |-------------+---------------------------------------------------------------------------------------------|
      | 検査の種類  | 戻り値                                                                                      |
      |-------------+---------------------------------------------------------------------------------------------|
      | "directory" | カレントディレクトリのパス名                                                                |
      | "numfile"   | 開かれているワークシートの枚数                                                              |
      | "origin"    | 現在ウィンドウに表示されてる範囲の左上隅の絶対セル参照が"$A:"で始まる文字列として返される。 |
      | "osversion" | 現在使用されているオペレーティングシステムのバージョン                                      |
      | "recalc"    | 現在設定されている再計算のモード（"Automatic/自動"または"Manual/手動"）                     |
      | "release"   | Excelのバージョン                                                                           |
      | "system"    | 操作環境の名前。Macの場合"mac"、Windowsの場合"pcdos"                                                       |
      |-------------+---------------------------------------------------------------------------------------------|
    
#### ISBLANK
- 対象が空白セルを参照するときにTRUEを返す
#### ISERR
- 対象が#N/A以外のエラー値の時にTRUEを返す
#### ISERROR
- 対象が任意のエラー値の時にTRUEを返す
#### ISEVEN
#### ISFORMULA
#### ISNA
- 対象がエラー値#N/Aの時にTRUEを返す。
#### ISNONTEXT
#### ISNUMBER
#### ISODD
#### ISREF
#### ISTEXT
#### N
- 値を数値に変換する
#### NA
- セルの値をエラー値「#N/A」とする。
- 書式
  NA()
#### SHEET
- 参照されるシートのシート番号を返す
- 書式 :
  SHEET(値)
  - 値 :
    省略可能。省略すると、この関数を含むシートの番号が返される。
#### SHEETS
- 書式 :
  SHEETS(範囲)
  - 範囲 : 
    省略可能。省略した場合、この関数を含むブックのシート数が返される。
- 参照内のシート数を返す。2013より。
#### TYPE
- データ型を表す数値を返す。2013より。
### 論理関数
#### AND
- 
  すべての引数がTRUEのときにTRUEを返す
#### FALSE
- 
  論理値FALSEを返す
#### IF
- 
  
#### IFERROR
#### IFNA
- 
  式が#N/Aに解決される場合、指定した値を返す。
#### IFS
- 
  1つまたは複数の条件が満たされるかどうかチェックして、最初のTRUE条件に対応する値を返す。
#### NOT
- 
  引数の論理値(TRUEまたはFALSE)を逆にして返す。
#### OR
#### SWITCH
#### TRUE
#### XOR
- 
  排他的論理和を計算する。
### 検索/行列関数
#### ADDRESS
- 書式
  ADDRESS(行番号,列番号,[参照の方],[a1],[シート名])
- 行番号と列番号を指定して、ワークシート内のセルのアドレスを取得できる。
#### AREAS
#### CHOOSE
- 
  一つ目の引数に入力された数値に応じて、第二引数以降のいずれかを返り値として返す関数。
  =choose(条件となる数値,値1,値2,...)
  条件となる数値が1の場合値1、2の場合値2、...が返る。
  29以下までしか定義できない。
#### COLUMN
#### COLUMNS
#### FORMULATEXT
#### GETPIVOTDATA
#### HLOOPUP
#### HYPERLINK
#### INDEX
- INDEX(array,row_num,[column_num])
- INDEX(reference,row_num,[column_num],[area_num])
#### INDIRECT
- INDIRECT(参照文字列,[参照形式])
- 指定される文字列への参照を返す。
#### LOOKUP
#### MATCH
- MATCH(検査値,検査範囲,[照合の型])
  セル範囲で指定した項目を検索し、その範囲内の項目の相対的な位置を返す。
#### OFFSET
- OFFSET(基準,行数,列数,[高さ],[幅])
- セルまたはセル範囲から指定された行数と列数だけシフトした位置にあるセル範囲の参照を返す。
#### ROW
#### ROWS
#### RTD
#### TRANSPOSE
#### VLOOKUP
- VLOOKUP(検索値,範囲,列番号[,検索方法])
  
- 検索方法
  FALSE, 0と入力すると、完全一致するデータのみを探す。
  TRUE, 1, 省略した場合は検索地未満の最大値が返される。（昇順に並んでいない場合適切に帰らない）
### 数学/三角関数
#### CEILING
#### CEILING.MATH
- 指定された基準値の倍数のうち、最も近い値に数値を切り上げる。
#### FLOOR.MATH
- 指定された基準値の倍数のうち、最も近い値に数値を切り捨てる。
#### MOD
- 数値を除算したときの剰余を返す
#### POWER
- 数値のべき乗を返す
#### ROUND
- 数値を四捨五入して指定された桁数にする
#### ROUNDDOWN
- 指定された桁数で切り捨てる
#### ROUNDUP
- 指定された桁数で切り上げる
#### SUM
#### SUMIF
- SUMIF(範囲,検索条件,[合計範囲])
  指定された検索条件に一致するセルの値を合計する
- Ex
  - =SUMIF(A1:A10,"=1",B1:B10)
    A列が1であれば、Bを足し合わせる。
  
#### SUMIFS
- SUMIFS(合計範囲,条件範囲1,条件1[,条件範囲2,条件2]...)
  セル範囲内で、複数の検索条件を満たすセルの値を合計する。
- Ex
  - =SUMIFS(C1:C10,A1:A10,"<100",B1:B10,
#### SUMPRODUCT
- SUMPRODUCT(配列1,[配列2,[配列3,...]])
  指定された配列で対応する要素の積を合計する。
### 統計関数
#### COUNT
- COUNT(範囲)
  数値データのセルを数える
#### COUNTA
- COUNTA(範囲)
  未入力セル以外を数える。
#### COUNTBLANK
- COUNTBLANK(範囲)
  空白のセルを数える
#### COUNTIF
- COUNTIF(範囲,検索条件)
  検索条件に合うセルを数える。
#### COUNTIFS
- COUNTIF(範囲1,検索条件1,範囲2,検索条件2,...)
  複数条件を設定してcountを行うことができる。
### 文字列関数
#### CHAR
- CHAR(数値)
- 数値で指定された文字を返す。
- ex
  =CHAR(65) ⇒ A
  =CHAR(33) ⇒ !
#### CODE
- CODE(文字列)
- テキスト文字列内の先頭文字の数値コードを返す。
- ex
  =CODE("A") ⇒ 65
  =CODE("!") ⇒ 33
#### EXACT
- 2つのテキスト文字列を比較し、同じであればTRUE、それ以外の場合はFALSEを返す。
- IFの場合、AaaAaとaaaaaは同じと判断されるが、EXACTを使うと別物と判断してくれる。
- ex
  EXACT(text1, text2)

#### FIND, FINDB
- FIND(検索文字列, 対象, [開始位置])
  指定された文字列を他の文字列の中で検索し、最初に現れる位置を左端から数え、その番号を返す。
  FIND関数は1バイト文字セットを使う言語での使用を意図したもので、FINDB関数は2バイト文字セットを使う言語での使用を前提としている。
  - FIND関数では、規定言語の設定に関係なく、1バイト文字も2バイト文字も、各文字が常に1つとして数えられる。
  - FINDB関数では、DBCSをサポートする言語のへ週を有効にした後でその言語を規定の言語として設定した場合に、各2バイト文字が2つとして数えられる。
    それ以外の場合は各文字は1つとして数えられる。

- 例
  =LEFT(A1,FIND("(",A1)-1)

#### LEFT, LEFTB
- 先頭から指定された文字数の文字を返す
#### LEN, LENB
- 
  セルの文字数を数える。
  [[https://support.office.com/ja-jp/article/%E3%82%BB%E3%83%AB%E5%86%85%E3%81%AE%E6%96%87%E5%AD%97%E6%95%B0%E3%82%92%E6%95%B0%E3%81%88%E3%82%8B-1be151d7-5b8f-4186-87b9-7b0318583163][セル内の文字数を数える - Office]]

#### LOWER
- LOWER(文字列)
  文字を小文字に変換する
#### MID, MIDB
- 書式
  MID(文字列、開始位置、文字数）

- 
  "文字列"の"開始位置"から"文字数"分だけ文字を取得する。

#### PROPER
- PROPER(文字列)
  先頭の文字、および記号の次の文字を大文字に変換、その他を小文字とする。
#### REPLACE, REPLACEB
#### RIGHT, RIGHTB
#### SEARCH, SEARCHB
#### SUBSTITUTE
- 書式
  SUBSTITUTE(対象文字列、検索文字、置き換え文字、[置換対象])

- 
  "対象文字列"中の"検索文字"を"置き換え文字"に変換する。
  "置換対象"は、複数の検索文字がヒットする場合、左から何番目を置き換えるか指定する。

#### T
- 引数を文字列に変換する
#### TEXT
- TEXT(書式設定する値, "適用する表示形式コード")
  数値を書式設定した文字列に変換する
##### 表示形式
- https://dekiru.net/article/4509/
#### TRIM
- 文字列から余分なスペースを削除する
#### UPPER
- UPPER(文字列)
  文字を大文字に変換する
#### VALUE
- 文字列を数値に変換する
### アドインでインストールされるユーザー定義関数
### Web関数
### 未掲載分
#### LAMBDA
- [[https://forest.watch.impress.co.jp/docs/news/1387035.html][Excelの新関数「LAMBDA」（ラムダ）が一般提供開始 ～Excel数式が本格的なプログラミング言語に - 窓の杜]]
- ヘルパー関数
  - MAP, REDUCE, SCAN, MAKEARRAY, BYROW, BYCOL, ISOMITTED
  
### Link
- [[https://support.office.com/ja-jp/article/Excel-%E9%96%A2%E6%95%B0-%E3%82%A2%E3%83%AB%E3%83%95%E3%82%A1%E3%83%99%E3%83%83%E3%83%88%E9%A0%86-b3944572-255d-4efb-bb96-c6d90033e188][Excel関数（アルファベット順） - Office]]
- [[https://support.office.com/ja-jp/article/Excel-%E9%96%A2%E6%95%B0-%E6%A9%9F%E8%83%BD%E5%88%A5-5f91f4e9-7b42-46d2-9bd1-63f26a86c0eb][Excel関数（機能別） - Office]]
## Shortcuts ショートカット
### Frequently used
#### 指定セルへジャンプ(Ctrl+G)
- 
  Ctrl+Gでジャンプ用のサブウィンドウが開く。
  "E25"とか指定するとジャンプできる。

#### 上のセルコピペ(Ctrl+D)
- Ctrl+Dで上のセルを下方向へコピー。Down。
#### 左のセルコピぺ(Ctrl+R)
- Ctrl+Rで左のセルを右方向へコピー。Right。
#### 最後のコマンド・操作を繰り返す(Ctrl+Y)
#### 行列、セルの挿入(Ctrl+"+")
#### 行列、セルの削除(Ctrl+"-")
- セルを削除
#### 右クリックメニューを出す(Shift+F10)

#### フィルタのつけ外し(Ctrl+Shift+L)
#### テーブルを作成(Ctrl+L)
#### 太字に変更(Ctrl+B or Ctrl+2)
#### 斜体に変更(Ctrl+I or Ctrl+3)
#### 名前を付けて保存(F12)
#### 形式を指定して貼り付け(Ctrl+Alt+V or Alt,E,S)
#### エクセル内のファイル切替(Ctrl+Tab)
#### 処理を繰り返す？(Ctrl+Y)
### Operations
#### 各種画面を開く
##### セルの書式設定ダイアログの表示(Ctrl+1)
##### 検索画面の表示(Ctrl+F)
##### 置換画面の表示(Ctrl+H)
#### データ表示設定
##### 通貨表示(Ctrl+Shift+$)
##### パーセント(Ctrl+Shift+%)
##### 日付(Ctrl+Shift+#)
##### 桁区切り(Ctrl+Shift+!)
##### 標準形式？(Ctrl+Shift+^)
#### 罫線
##### 選択したセルの外枠に罫線を設定(Ctrl+Shift+&)
##### 選択したセルの外枠に罫線を削除(Ctrl+Shift+_)
#### 日時入力
##### 現在の日付を入力(Ctrl+:)
##### 現在の時刻を入力(Ctrl+;)
### Ribbon
#### Earlier Ver.
##### Paste Special(Alt,E,S or Ctrl+Alt+V)
###### 関数貼り付け(Alt,E,S,F)
###### 値貼り付け(Alt,E,S,V)
- 
  値貼り付けを行う。
  Alt,E,Sで特別な方法で貼り付け。Vで方法としてValueを選択してくれる。
###### フォーマット貼り付け(Alt,E,S,T)
##### オートフィル(Alt,E,I,S)
- 
  オートフィル。連番を振れる。

##### オートフィルタ設定(Alt,D,F,F)

##### オートフィルタ設定解除(Alt,D,F,S)
##### ワークシート名の変更(Alt,O,H,R)
#### FILE(F)
##### Open(Alt,F,O)
- 旧:Ctrl+O
##### Print (Alt,F,P)
- 旧:Ctrl+P
#### HOME(H)
##### Clipboard
###### Clipboard
##### Font
###### Font
##### Alignment
###### Alignment
##### Number
###### Number
##### Styles
###### Conditional Formatting(Alt,H,L)
##### Cells
##### Editing
###### Find & Select(Alt,H,FD)
####### Find(F)
####### Replace(R)
####### Go To(G)
####### Go To Special... (Alt,H,FD,S)
######## Comments(c)
######## Constans(o)
######## Formulas(f)
######## Blanks(k)
######## Current region(r)
######## Current array(a)
######## Objects(b)
#### INSERT(N)
#### PAGE LAYOUT(P)
#### FORMULA(M)
##### オートフィルタ設定(Alt,A,T)
#### DATA(A)
##### グループ化(Alt,A,G,G)
#### REVIEW(R)
#### VIEW(W)
##### Freeze Panes(Alt,W,F)
###### Freeze/Unfreeze Panes(Alt,W,F,F)
##### Gridlinesの表示・非表示(Alt,W,VG)
##### 新規ウィンドウ生成(Alt,W,N)
#### DEVELOPER(L)
#### LOAD TEST(Y1)
#### Tools
##### TABLE TOOLS
###### DESIGN(JT)
####### Convert to Range / 範囲に変換 (Alt,JT,G)
##### DRAWING TOOLS
###### FORMAT(JD)
####### Insert Shapes
######## Edit Shape(Alt,JD,E)
######### Change Shape(Alt,JD,E,N)
####### Shape Styles
####### WordArt Styles
####### Arrange
####### Size
##### グラフ
##### ピボットテーブル
### Link
- [[https://support.office.com/en-us/article/Excel-keyboard-shortcuts-and-function-keys-1798d9d5-842a-42b8-9c99-9b7213f0040f][Excel keyboard shortcuts and function keys - Office]]
- [[https://support.office.com/ja-jp/article/Excel-%E3%82%AD%E3%83%BC%E3%83%9C%E3%83%BC%E3%83%89-%E3%82%B7%E3%83%A7%E3%83%BC%E3%83%88%E3%82%AB%E3%83%83%E3%83%88-%E3%83%95%E3%82%A1%E3%83%B3%E3%82%AF%E3%82%B7%E3%83%A7%E3%83%B3-%E3%82%AD%E3%83%BC-1798d9d5-842a-42b8-9c99-9b7213f0040f][Excel キーボード ショートカット - ファンクション キー - Office]]

- [[http://matome.naver.jp/odai/2134702837577488501][Excelで役立つ10のショートカットキー]]
- [[http://excel-hack.com/beginner/shortcutkey-list/][覚えると便利！124個のExcelショートカットキー一覧表 - Excel Hack]]
- [[https://liginc.co.jp/life/useful-info/162348][エクセル（Excel）の便利なショートカットキーまとめ - LIG INC.]]

- [[https://exceljet.net/keyboard-shortcuts][222 Excel keyboard shortcuts for PC and Mac - EXCELJET]]
- [[https://exceljet.net/the-54-excel-shortcuts-you-really-should-know][The 54 Excel shortcuts you really should know - EXCELJET]]

## データベース機能
### テーブル
- 変換
  挿入/INSERTタブのテーブルを選択する。

- 利点
  - 自動的に1行おきの色違いになる
  - 自動的にフィルタが有効となる
  - 集計行を簡単に追加可能
  - スクロールしても先頭行が見える
  - 上記をDESIGNタブで制御できる

### ピボットテーブル
- 
  「クロス集計」を行う機能。
  
## VBA
- [[file:./VBA.org][VBA.org]]
## Addin
### RelaxTools
- [[https://github.com/RelaxTools/RelaxTools-Addin/releases][RelaxTools - GitHub]]
## Memo
### マクロのパスワード解除
- 最新のExcelでは利用できなそう。stirlingで無理矢理書き換える方法。
  http://tristore.net/?p=238
### シート名を取得する（パス、ファイル名の取得も可）
- cell("filename")を使うと、フルパス、ファイル名、シート名が取得できる。
  =RIGHT(CELL("filename",A1),LEN(CELL("filename",A1))-FIND("]",CELL("filename",A1)))

### シート番号を取得する
- SHEET関数を利用する
  =SHEET(シート名)
### 曜日を表示する
- 
  セルの書式設定でフォーマットで、aaa, aaaa, ddd, dddd等で曜日の表示が可能。
  また、他セルの場合chooseとweekdayの組み合わせで曜日を表示することなども可能。
  ex) =choose(weekday(A1),"日曜日","月曜日","火曜日","水曜日","木曜日","金曜日","土曜日")
      =text(A1,"aaaa")

### 曜日を条件付き書式で色付けする
- 新しい書式ルールを作成する際に、「数式を使用して、書式設定するセルを決定 / Use a formula to determine which cells to format」を選択。
  数式として"=workday(A3※選択した項目の最初のセルを選択。また、絶対参照とはしない)=1※日曜日の場合"とする。
  [[https://forest.watch.impress.co.jp/docs/serial/exceltips/1059891.html][【Excel】「土曜は青、日曜は赤」予定表の曜日を色分けしたい！　エクセルで日付を見やすく書式設定するテク - 窓の杜]]
### 複数のセル選択後、選択解除
- 
  Tabキーで選択場所を移し、Shift+↑/↓を操作することで、
  選択範囲の拡大/縮小を行うことができる。
  それにより一度選択した範囲を外すことができる。
  [[http://oshiete.goo.ne.jp/qa/256213.html][エクセルで複数のセル選択をした後、選択したセルの１つを選択解除したい - 教えて!goo]]
  ;
### シートのコピー
- 
  Ctrlを押しながら、シートをドラッグするとコピーができる。
  [[http://detail.chiebukuro.yahoo.co.jp/qa/question_detail/q1443247924][エクセルで作成したシートのコピーを一度に複数作る - yahoo!知恵袋]]

### 各種特殊文字の置換
- 改行コード
  Ctrl+J

### グループ化
- 
  Dataタブの配下に、グループ化の設定ができる。
  [Alt]+[Shift]+[→]でグループ化、[Alt]+[Shift]+[←]でグループ解除ができる。
### グループ化、折りたたみ
- 項目をグループ化することで、ワンタッチで折りたたみ/展開を行えるようになる。
  Data -> Group -> Group (Alt, A, G, G)

### スクロールロック
- 
  カーソルキーで画面がスクロールしてしまう場合は、Scroll Lockとなっている。

### 数式を使って文字型の数字を数値として扱う方法
- 
  =数式*1とすると、文字列が数字に変換される。
  [[https://love-guava.com/excel-string-numerical-value-change/][Excel（エクセル）で文字列と数値を変換する方法。知っとくと地味に便利ですよ！ - ラブグアバ]]
### 再計算を自動で行わない
- 
  数式->計算方法の設定->手動、を選択。
  Select FORMULAS->Calculation Options->Manual
  [[http://ameblo.jp/sugoikaizen/entry-12031805139.html][Excelがいちいち再計算で止まってしまう現象を止める方法 - エクセルセミナー研修のすごい改善～Excel社員研修と業務効率化]]

### 高速vlookup
- 
  大体以下のような感じ。
  =IF(INDEX(Sheet1!$A$2:$A$200001,MATCH($A2,Sheet1!$A$2:$A$200001,1),1)=$A2,VLOOKUP($A2,Sheet1!$A$2:$B$200001,2,TRUE),NA())
  INDEX,MATCHをTRUEで近似値で行い、それが元値と一致した場合のみvlookupで近似値計算。
  近似値計算の方が早いため。ただし対象を昇順に並べておく必要あり。
  別にINDEX, MATCHを二回やってもよいと思われる。

  [[http://excel-ubara.com/excel3/EXCEL019.html][【奥義】大量データでの高速VLOOKUP - エクセルの神髄]]

### 複数条件のvlookup
#### 配列数式とMATCHを利用
- MATCH(1,(検索範囲1=検索値1)*(検索範囲2=検索値2)*...,0)
  MATCHで返ってくる値を元にINDEXで値を表示させることで、vlookupと同様の動きとなる。
##### Link
- [[http://azwoo.hatenablog.com/entry/2015/11/28/010834][【簡単】vlookup 複数条件は不可 でもすぐにできる代替手段！（MATCH関数・INDEX関数を使う） - "Diary" インターネットさんへの恩返し]]
- [[http://www.exceltactics.com/vlookup-multiple-criteria-using-index-match/][How to VLOOKUP with Multiple Criteria Using INDEX and MATCH - ExcelTactics]]
#### SUMPRODUCTを利用
- SUMPRODUCT((検索範囲1=検索値1)*(検索範囲2=検索値2)*...*ROW(検索範囲))
  ROWをかけることで、値が1の場合(全ての条件がTrueの場合)に行番号が返ってくる。
  ただし複数MATCHする場合は、MATCHしたすべての行番号が足し合わせた値が返ってくるので注意。
  また、vlookupと同様の動きをするには、戻り値を使ってINDEX関数を適用する必要あり。
##### Link
- [[http://hamachan.info/win8/excel/sumproduct.html][3つの条件を満たす値を求めるには - 初心者のためのOffice講座]]
#### 結合した文字列の比較を行う（単純な方法、追加セルが必要）
### シート名の変更
- ショートカット : Alt,O,H,R
- シートをダブルクリック
### ワークシートの再表示(unhide)
- 
  基本的に大したショートカットもない。
  Alt->H->O->U->Hでメニューバーをたどることはできる。
  （Home, Format, Hide & Unhide, Unhide sheet)

- 一括再表示
  VBAを使う。
  - 例)
    For Each Sh In ActiveWorkbook.Sheets
        Sh.Visible = True
    Next Sh
### セルの参照を文字列で作成
- INDIRECT関数を使う。
  =INDIRECT(A4&"!B3")などとして使う。
  A4にあるシート名の、B3セルの参照が取得できる。
### 日時のシリアル値
- Excelでは、時刻・時間をシリアル値という値で処理する。
  1日(24h)を1.0で表し、0:00:00-23:59:59までが0~0.99999999の範囲の値となる。
- 1900年1月1日からの経過日数を表す。
- http://www.excel.studio-kazu.jp/tips/0049/
### 日付表示
#### 24h以上の日付を表示する場合
- [h]を使う。[h]:mm:ssなど。
### Array Formula / 配列数式
- 数式入力時に「Ctrl + Shift + Enter」で確定させる。
  配列(複数セル)を対象に、1つの数式を作成する式。
  式がbraket{}で囲まれるが、キーボードから入力しても配列数式とはみなされない。
  
#### 配列入力
- 複数範囲を選択して、braket{}で囲んだ値を入力する。
  comman,はセルの終わり、semicolon;は行の終わりを表す。
  ex) ={2,3,"a";4,5,"b"}
      ->
      | 2 | 3 | a |
      | 4 | 5 | b |
#### 配列計算
- 複数セルを配列として計算可能。
  結果的に複数セルに入力をする場合、その数分のセルを選択しておき、出力数と揃える必要あり。
  1つのセルに出力する場合、範囲や配列を引数として取れる関数でまとめた上で出力する必要がある。
  どちらにせよ、配列を配列のまま計算することが可能となる。
#### Link
- [[https://support.office.com/ja-jp/article/%E9%85%8D%E5%88%97%E6%95%B0%E5%BC%8F%E3%81%AE%E3%82%AC%E3%82%A4%E3%83%89%E3%83%A9%E3%82%A4%E3%83%B3%E3%81%A8%E4%BE%8B-3be0c791-3f89-4644-a062-8e6e9ecee523][配列数式のガイドラインと例 - Office]]
- http://office-qa.com/Excel/ex69.htm

### 複数のオブジェクトを選択
- 範囲を選ぶ場合
  - HOME -> Find & Select -> Select Objects
    マウスで範囲を選択すればよい
- 全てを選択する場合
  - HOME -> Find & Select -> Go To... -> Special... -> Objects
    該当ページのオブジェクトが全て選択される。
### クイックアクセスツールバー
- 良く使う機能を、エクセルの上部枠に設定可能。
### パディング
- フォーマットは"TEXT"関数で行う。
- 例 : 0パディング
  =TEXT(A1,"0000")
### 書式のユーザー設定
- @"様"などと書式設定を入力すると、〜様、となる。
  https://kokodane.com/tec1_12.htm
### アルファベットの大文字・小文字を区別して判定する
- EXACT関数を利用する。
  http://www.relief.jp/docs/002927.html
### Excelで、桁数が多い数字を入力すると最後の桁がゼロとなる
- IEEE 754仕様に準拠しているため、15桁目以降の数値は0となる。
  回避したければ、文字列として扱う必要がある。文字列は32,767文字まで入力可、1,024文字までが表示される。
### 条件付き書式設定自体はコピーせず、設定後の書式のみをコピーしてくる
- コピーしたあと、ホーム->クリップボードにに存在する内容を貼り付けると、「条件付き」は除かれ、結果の「書式」のみが反映される。
  [[https://dekiru.net/article/16416/][【エクセル時短】条件付き書式の「書式」だけ残すには？ 文字やセルの色を固定してコピーするワザ - できるネット]]
## Link
- [[https://www.youtube.com/watch?v=0nbkaYsR94c][You Suck at Excel with Joel Spolsky - YouTube]]
- [[https://www.maxmasnick.com/2015/09/15/excel/][Notes from "You Suck at Excel" with Joel Spolsky - MAX MASNICK, PhD]]

- [[https://qiita.com/matarillo/items/549493f6bb7e36c99443][サーバサイドでExcelブックを生成するいくつかの方法 - Qiita]]
