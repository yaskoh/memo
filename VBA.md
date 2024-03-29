# VBA
## Language
- [[https://msdn.microsoft.com/en-us/library/office/gg264383.aspx][Visual Basic for Applications language reference for Office 2013 - Dev Center]]
- [[https://msdn.microsoft.com/ja-jp/library/office/gg264383.aspx][Office VBA 言語リファレンス - Dev Center]]

### Constants
#### Calender Constants
#### CallType Constants
#### Color Constants
#### Comparison Constants
#### Compiler Constants
#### Data Constants
#### Date Format Constants
#### Dir, GetAttr, SetAttr Constants
#### DriveType Constants
#### File Attribute Constants
#### File Input/Output Constants
#### Form Constants
#### IMEStatus Constants
#### Keycode Constants
#### Miscellaneous Constants
#### MsgBox Constants
#### QueryClose Constants
#### Shell Constants
#### SpecialFolder Constants
#### StrConv Constants
#### System Color Constants
#### Tristate Constants
#### VarType Constants
#### Visual Basic Constants
### DataType
#### Byte
#### Boolean
#### Integer
#### Long
#### LongLong
#### LongPtr
#### Single
#### Double
#### Currency
#### Decimal
#### Data
#### Object
#### String(可変長)
#### String(固定長)
#### Variant(数値)
#### Variant(文字)
### Directive
#### #Const
#### #If...Then...#Else
  
### Error Messages

### Events
### Functions / 関数
- [[https://msdn.microsoft.com/en-us/vba/language-reference-vba/articles/functions-visual-basic-for-applications][Functions (Visual Basic for Applications) - Dev Center]]
- [[http://officetanaka.net/excel/vba/function/index.htm][VBAの関数 - officeTANAKA]]
  （Application毎に違いがあれば移行する）

#### MsgBox
- MsgBox(prompt [,bottuns] [,title] [,helpfile,context])
  - prompt : 表示するメッセージを指定
  - button : ボタンの種類やタイプなどを指定する
  - title : タイトルバーに表示する文字列を指定する。
  - helpfile : [ヘルプ]ボタンから開くヘルプファイルを指定する。
- 
  ダイアログボックスにメッセージとボタンを表示し、どのボタンが押されたかを示す整数型の数値を返す。

##### buttons
- 
  |--------------------+------+----------------------------------------------------------------------------------------------------------------------------|
  | 定数               |   値 | 内容                                                                                                                       |
  |--------------------+------+----------------------------------------------------------------------------------------------------------------------------|
  | vbOKOnly           |    0 | [OK]ボタンのみを表示します                                                                                                 |
  | vbOKCancel         |    1 | [OK]ボタンと[キャンセル]ボタンを表示します                                                                                 |
  | vbAbortRetryIgnore |    2 | [中止]、[再試行]、および[無視]の３つのボタンを表示します                                                                   |
  | vbYesNoCancel      |    3 | [はい]、[いいえ]、および[キャンセル]の３つのボタンを表示します                                                             |
  | vbYesNo            |    4 | [はい]ボタンと[いいえ]ボタンを表示します                                                                                   |
  | vbRetryCancel      |    5 | [再試行]ボタンと[キャンセル]ボタンを表示します                                                                             |
  | vbCritical         |   16 | 警告メッセージアイコンを表示します                                                                                         |
  | vbQuestion         |   32 | 問い合わせメッセージアイコンを表示します                                                                                   |
  | vbExclamation      |   48 | 注意メッセージアイコンを表示します                                                                                         |
  | vbInformation      |   64 | 情報メッセージアイコンを表示します                                                                                         |
  | vbDefaultButton1   |    0 | 第1ボタンを標準ボタンにします                                                                                              |
  | vbDefaultButton2   |  256 | 第2ボタンを標準ボタンにします                                                                                              |
  | vbDefaultButton3   |  512 | 第3ボタンを標準ボタンにします                                                                                              |
  | vbDefaultButton4   |  768 | 第4ボタンを標準ボタンにします                                                                                              |
  | vbApplicationModal |    0 | アプリケーションモーダルに設定します。メッセージボックスに応答するまで、現在選択中のアプリケーションの実行を継続できません |
  | vbSystemModal      | 4096 | システムモーダルに設定します。メッセージボックスに応答するまで、すべてのアプリケーションが中断されます                     |
  |--------------------+------+----------------------------------------------------------------------------------------------------------------------------|

##### return value
- 
  |----------+----+------------------------------|
  | 定数     | 値 | 説明                         |
  |----------+----+------------------------------|
  | vbOK     |  1 | [OK]ボタンが押された         |
  | vbCancel |  2 | [キャンセル]ボタンが押された |
  | vbAbort  |  3 | [中止]ボタンが押された       |
  | vbRetry  |  4 | [再試行]ボタンが押された     |
  | vbIgnore |  5 | [無視]ボタンが押された       |
  | vbYes    |  6 | [はい]ボタンが押された       |
  | vbNo     |  7 | [いいえ]ボタンが押された     |
  |----------+----+------------------------------|

#### Right
- Right(string,length)
  - string : 元の文字列
  - length : 抜き出す文字数

- 
  string文字列の右端から、length分文字列を取得し返す。

#### Mid
- 

#### StrConv
- 用法
  StrConv(string, conversion)

- conversion
  |--------------+----+----------------------------|
  | 定数         | 値 | 内容                       |
  |--------------+----+----------------------------|
  | vpUpperCase  |  1 | 大文字に変換               |
  | vbLowerCase  |  2 | 小文字に変換               |
  | vbProperCase |  3 | 各文字の先頭を大文字に変換 |
  | vbWide       |  4 | 半角文字を全角に変換       |
  | vbNarrow     |  8 | 全角文字を半角に変換       |
  |--------------+----+----------------------------|
  
- 
  "string"で指定した文字列に、conversionで指定した変換を行う。
### Keywords
### Methods
### Objects
- [[https://msdn.microsoft.com/en-us/vba/language-reference-vba/articles/objects-visual-basic-for-applications][Objects (Visual Basic for Applications) - Dev Center]]
#### Collection
#### Debug
#### Dictionary
#### Drive
#### Drives Collection
#### Err
#### File
#### Files Collection
#### FileSystemObject
#### Folder
#### Folders Collection
#### TextStream
#### UserForm
### Operators
#### 算術演算子
##### ^
##### *
##### /
##### \
##### Mod
##### +
##### -
#### 比較演算子
##### ComparisonOperator
###### <
###### <=
###### >
###### >=
###### =
###### <>
##### Is
##### Like
#### 連結演算子
##### &
##### +
#### 論理演算子
##### AND
##### Eqv
##### Imp
##### Not
##### OR
##### Xor
#### =
- 代入演算子
#### AddressOf
- 指定されたプロシージャのアドレスを渡す単項演算子。
### Properties
### Statements
- [[https://msdn.microsoft.com/ja-jp/library/office/jj692812.aspx][ステートメント - Visual Basic 言語リファレンス - Dev Center]]
- [[https://msdn.microsoft.com/en-us/vba/language-reference-vba/articles/statements][Statements - Language Reference VBA - Dev Center]]
#### AppActivate
#### Beep
#### Call
- 
  他のSubプロシージャやFunctionプロシージャなどを呼び出して制御を渡す。

  下記にプロシージャに関して、幾つかの使用規則を記す。
  1. 通常のSubプロシージャは、Callステートメントを省略することも可能。
     ex) ○:Call myFunction(123)
         ○:myFunction 123
  2. Callを省略する場合、引数を括弧で囲まない。Callを使う場合は囲む。
     ex) ×:myFunction(123)
         ○:myFunction 123
         ○:Call myFunction(123)
         ×:Call myFunction 123
  3. Callでは返り値を受け取れない。
     ex) ×:rc = Call myFunction(123)
  4. 返り値を受け取る場合、Callを使わないが、括弧は必要となる。
     ex) ×:rc = myFunction 123
         ○:rc = myFunction(123)
#### ChDir
#### ChDrive
#### Close
#### Const
#### Date
#### Declare
#### DeleteSetting
#### Dim
- 
  変数を宣言する

#### Do ... Loop
- About
  条件がTrueの間、一連のステートメントを繰り返し実行する。

- Statement
  - Do [{While | Until} condition]
    [statements]
    [Exit Do]
    [statements]
    Loop
  - Do
    [statements]
    [Exit Do]
    [statements]
    Loop [{While | Until} condition]

#### End
- 
  プロシージャまたはブロックを終了する

#### Enum
#### Erase
#### Error
#### Event
#### Exit
#### FileCopy
#### For Each ... Next
- 
  コレクションや配列の各要素に対してstatementsを実行する。

#### For ... Next
- About
  引数startで指定した値から、引数endで指定した値までstatementを繰り返す

- Statement
  For counter = start To end [Step step]
  [statements]
  [Exit For]
  [statements]
  Next [counter]
  
#### Function
- 
  Functionプロシージャ（戻り値あり）を作成する

#### Get
#### GoSub
#### GoTo
#### If ... Then ... ElseIf ... Else
- 
  条件を評価して、条件付きの実行を行うステートメント
  If ... Thenで始まり、End Ifで終わる。
  ElseIf, Elseも使用可能。

- 例
    If a < 5 Then
        MsgBox a & "は５より小さい"
    ElseIf a = 5 Then
        MsgBox a & "は５です"
    Else
        MsgBox a & "は５より大きい"
    End If

#### Implements
#### Input #
#### Private
- 
  プライベート変数を宣言する。プライベート変数は、宣言されたモジュール内のみ参照できる。

#### Seek
#### Select
#### SendKeys
#### Set

#### SetAttr
#### Static
#### Stop
#### Sub
- 
  Subプロシージャを作成する。

#### Time
#### Type
#### Unload
#### While...Wend

#### Width #
#### With
- 

#### Write #
### Link
## Applications
### Excel
#### About
##### Object Model
- 
  主なものは、Application、Workbook、Worksheet、Range。
  
#### Property
##### Format
##### Value
#### Object
- [[https://msdn.microsoft.com/ja-jp/library/ff194068.aspx][オブジェクトモデル (Excel VBA リファレンス)]]
- [[http://www.vba-ie.net/object/index.html][ExcelのVBAで利用したオブジェクト一覧 - VBAのIE制御入門]]

##### Application
- 
  Excelアプリケーション全体を表す。

###### Properties
####### ActiveSheet Property

####### ActiveWorkbook Property

####### ThisWorkbook Property
- 在実行中のマクロコードが記述されているブックを返す。
##### ListObject
###### Methods
###### Properties
####### Name
- ListObjectオブジェクトの名前を表す文字列の値を取得または設定する。
##### ListObjects
##### Range
- セル、行、列、1つ以上のセル範囲を含む選択範囲、または3-D範囲を表す。
- [[https://msdn.microsoft.com/ja-jp/library/ff197454.aspx][Rangeメンバー(Excel) - Developer Network]]
###### Methods
####### Insert
- 
  ワークシートまたはマクロシートの指定された範囲に、空白のセルまたはセル範囲を挿入する。
  指定された範囲にあったセルはシフトされる。

###### Properties
####### Text
- 
  オブジェクトのテキストを取得または設定する。値の取得のみ可能。文字列型を使用する。

####### Value
- Value(RangeValueDataType)
  指定されたセル範囲の値を表すバリアント型(Variant)の値を設定する。値の取得および設定が可能。

##### Workbook
###### Properties
####### Path
- ブック/ファイルへの完全なパスを表す文字列型(String)の値を取得する。
##### Workbooks(Collection)

##### Worksheet
###### Events
###### Methods
###### Properties
####### Cells
- Cells
  ワークシートのすべてのセルを表すRangeオブジェクトを返す。
####### Columns
- 
  作業中のワークシートのすべての列を表すRangeオブジェクトを返す。
  
####### ListObjects
- ListObjects
  ワークシート内に複数あるListObjectオブジェクトから成る1つのコレクションを返す。
####### Range
- Range(Cell1, Cell2)
  セルまたはセル範囲を表すRangneオブジェクトを返す。

##### Worksheets(Collection)

### Powerpoint
#### Object Model
- [[https://msdn.microsoft.com/ja-jp/library/ff743835.aspx][オブジェクトモデル (PowerPoint VBA リファレンス) - Developer Network]]

##### Application Object
- PowerPointアプリケーション全体。
  ActivePresentationやWindowsなどの、最上位レベルのオブジェクトを取得するプロパティや、
  アプリケーション全体に適用される設定やオプションが含まれる。
- PowerPointから実行されるコードを記述する場合、Applicationオブジェクトのプロパティである
  ActivePresentation, ActiveWindow, AddIns, Presentations, SlideShowWindows, およびWindowsは修飾子なしで使用可能。
  
###### Properties
####### ActivePresentation
- 作業中のウィンドウで開かれているプレゼンテーションを表すPresentationオブジェクトを取得する。
- 例
  - Application.ApctivePresentation.SaveAs MyPath
    "MyPath"に示されたパス・ファイル名で現在のプレゼンテーションを保存する。
####### ActiveWindow Property
- 作業中のスライドウィンドウを表すDocumentWindowオブジェクトを取得する。取得のみ可能。
  
####### Presentations Property
- 開いているすべてのプレゼンテーションを表すPresentationsコレクションを取得する。
  値の取得のみ可能。

- 構文
  式.Presentations
  戻り値 : Presentations

###### Methods
##### DocumentWindow Object
- ドキュメントウィンドウを返す。DocumentWindowsコレクションのメンバ。
  すべての開いているドキュメントウィンドウが含まれる。

- 現在実行中のプレゼンテーションはPresentationプロパティを使用する。
  選択内容を取得するにはSelectionプロパティを使用する。
  指定したウィンドウの表示モードを取得するにはViewプロパティを取得する。

###### Properties
####### Selection
####### View
- 表示モードを表すViewオブジェクトを取得する。
##### Presentation Object
- プレゼンテーションを表す。
  Presentationsコレクションのメンバ。
- 例
  - Presentatons("Sample Presentation").Slides.Add 1,1
    ファイル名"Sample Presentation"の先頭にスライドを追加する。
  - ActivePresentation.Save
    作業中のプレゼンテーションを保存する。
##### Presentations Object
- Presentationオブジェクトのコレクション。
  Presentaniosコレクションを取得するには、Presentationsプロパティを使用する。
##### Shapes Object
- 指定したスライドのすべてのShapeオブジェクトのコレクション。
###### Methods
####### Paste
- 構文
  式.Paste
  戻り値 : ShapeRange
##### Slide Object
- スライドを表す。Slidesコレクションには、プレゼンテーションのすべてのSlideオブジェクトが含まれる。
###### Properties
###### Methods
####### MoveTo Method
- 指定したオブジェクトを同じコレクション内の場所に移動し、他のアイテムの番号を振りなおす。
- 構文
  式.MoveTo(toPos)
- ToPos : 移動先のインデックス位置。
- 例
  - ActivePresentation.Slides(2).MoveTo toPos:=1
    スライド2をスライド1へ移動する。

##### Slides Object
##### View Object
- 指定したスライドウィンドウの現在編集中の表示モードを表す。
###### Methods
####### GotoSlide
- 指定したスライドに切り替える。
- 構文
  式.GotoSlide(Index)
#### Memo
##### スライド番号を指定してジャンプ
- ActiveWindow.View.GotoSlide Index:=Int(2)
- SlideShowWindows(1).View.GotoSlide 3
  http://www.relief.jp/itnote/archives/powerpoint-vba-goto-slide.php

##### スライド数を取得
- ActivePresentation.Slides.Count

##### スライドを順番にループ
- For i = 1 To ActivePresentation.Slides.Count
      Operation
  Next

- For Each sld In ActivePresentation.Slieds
      Operation
  Next
- 
  http://okwave.jp/qa/q8684138.html

#### Link
- [[https://msdn.microsoft.com/ja-jp/library/ee861525.aspx][PowerPoint VBAリファレンス - Developer Network]]

### Outlook
## IDE
### Immediate Window
- 使い方
  ?に続けて確認したい式を書く。
  ?EOF(1) など。
  [[https://tonari-it.com/vba-immediate-command-input/][【エクセルVBA】イミディエイトウィンドウはコマンド入力画面として使うと超便利 - いつも隣にITのお仕事]]
## Memo
### ByValとByRef
- 
  何もつけない場合、ByRef(参照渡し)として定義されている。
  値渡しをしたい場合は明示的にByVal、としなくてはならない。
  出来る限りつけておくのが良い。

### subとfunction
- 
  functionは戻り値を返す。subはsubroutineの略で戻り値は返さない。

### 複数の値をプロシージャに渡す
- 
  複数の値を引数として渡す場合は、以下のどちらかの対応が必要。
  - Callステートメントをつける
  - 括弧を除いて平文で渡す
  
  括弧は、引数の演算処理のためのものなので、複数引数には対応していない、とのこと。
  ちなみに以下は正常となる。
  ex) MsgBox ("お元気ですか？"+"これでよろしいですか？"), vbOKOnly
  - [[http://www.atmarkit.co.jp/ait/articles/1503/17/news039.html][コンパイルエラーにならない関数の使い方 - @IT]]
  
### 代入
- 
  オブジェクトに値を代入するときは、Set A = B、という形で"Set"が必要。
  値であれば、A = Bとすると代入できる。

### GUIDの作成
- 
  Mid$(CreateObject("Scriptlet.TypeLib").GUID, 2, 36)
  [[http://maeda0414.blog.fc2.com/blog-entry-26.html][Execl VBAでGUIDを作成する]]

### 配列
- 
  変数名の後に括弧()を付けると配列として扱うことができる。

  要素数を指定しないで動的配列として扱うこともできるが、
  要素数が決まらない場合は要素にアクセスが出来ない。
  ReDimを行い要素数を確定させるが、その際に要素のデータは削除されてしまう。
  Preserveキーワードを付けると、格納さえれているデータを保持したまま配列の要素数を再定義可能。
  [[http://officetanaka.net/excel/vba/variable/08.htm][動的配列 - Office TANAKA]]
  
### Error
#### オートメーションエラー(440)
- CreateObjectしたIEオブジェクトを生成、操作、終了、破棄して何度も呼び出すと起こる場合がある。
  1つを使いまわす場合には問題ない。
  
  本来あるはずのオブジェクトが掴めない、ということらしい。
  ステップ実行であれば問題なく実行される場合が多い。

- Excelアドインの「分析ツール(FUNCRES.XLAM)」を停止することで解決する場合もあるらしい。
  http://excelfactory.net/excelboard/excelvba/excel.cgi?mode=all&namber=175963&rev=0
### IE操作
- ライブラリ参照設定
  - Tools -> References...
    - Microsoft HTML Object Library
    - Microsoft Internet Controls
### Glossary
#### VBE
- Visual Basic Editor
## tmp
### EOF(fileNo)
### Line Input #fileNo, buf
### FreeList
- 使用可能なファイル番号を整数で返す。
## Link
- https://www.vba-ie.net/

- VBA/IE操作のreferenceが見つからない。。。
  [[https://msdn.microsoft.com/en-us/library/aa296861(v=office.11).aspx]]
  
