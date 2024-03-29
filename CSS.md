# CSS
## Specification
### About
#### CSS Snapshot 2010
- Completed
#### CSS Snapshot 2015
- Stable
##### Definition
##### W3C Process
- Working Draft, WD
- Candidate Recommendation, CR
- Reccomendation, REC
##### Link
- [[https://momdo.github.io/css-2015/][CSS Snapshot 2015 日本語訳]]
#### CSS Snapshot
- [[https://www.w3.org/TR/CSS][CSS Snapshot - W3C]]
- [[https://www.w3.org/standards/techs/css#w3c_all][CSS CURRENT STATUS - W3C]]
### CSS 1
#### Completed
##### CSS Level 1
#### Testing
##### CSS Shapes Level 1
##### CSS Masking Level 1
##### Compositing and Blending Level 1
##### Geometry Interfaces Module Level 1
#### Refining
##### CSS Will Change Level 1
- CR
### CSS 2.1/2.2
#### Completed
##### CSS Level 2 Revison 1
###### Syntax and basic data types
###### Selectors
####### Pattern matching
####### Pseudo-elements and pseudo-class
####### Pseudo-class
######## :first-child
######## :link, :visited
- :link : links that have not yet been visited
- :visited : the link having been visited by the user.
######## :hover, :active, :focus
- :hover : while the user designates an element, but does not activate it.
  ポインタデバイスを重ねたとき
- :active : while an element is being activated by the user.
  クリックされてから話されるまでの間
- :focus : while an element has the focus.
  テキストエリアなどが選択されているとき
######## :lang

####### Pseudo-elements
######## :first-line
######## :first-letter
######## :before, :after
###### Assigning property values, Cascading, and Inheritance
###### Media types
###### Box model
####### Margin properties
######## <margin-width> value
- <length>
- <percentage>
- auto
######## margin-top, margin-bottom
######### Def
- Value: <margin-width> | inherit
######## margin-right, margin-left
######### Def
- Value: <margin-width> | inherit
######## margin
######### Def
- Value: <margin-width>{1,4} | inherit
####### Padding properites
######## <padding-width> value
- <length>
- <percentage>
######## padding-top, padding-right, padding-bottom, padding-left
######### Def
- Value: <padding-width> | inherit
######## padding
######### Def
- Value: <padding-width>{1,4} | inherit
####### Border properties
######## Border width
######### <border-width> value
- thin
- medium
- thick
- <length>
######### border-top-width, border-right-width, border-bottom-width, border-left-width
########## Def
- Value: <border-width> | inherit
######### border-width
- Value: <border-width>{1,4} | inherit
######## Border color
######### border-top-color, border-right-color, border-bottom-color, border-left-color
######### border-color
########## Def
- Value: [<color> | transparent]{1,4} | inherit
######## Border style
######### <border-style> value
- none
- hidden
- dotted
- dashed
- solid
- double
- groove : the border looks as though it were carved into the canvas.
- ridge : the opposite of 'groove'
- inset : the border makes the box look as though it were embedded in the canvas.
- outset
######### border-top-style, border-right-style, border-bottom-style, border-left-style
########## Def
- Value: <border-style> | inherit
######### border-style
########## Def
- Value: <border-style>{1,4} | inherit
######## Border shorthand properties
######### border-top, border-right, border-bottom, border-left
######### border
########## Def
- Value: [ <border-width> || <border-style> || <'border-top-color'> | inherit
###### Visual formatting model
####### Controlling box generation
######## display
######### Def
- Value :
  inline | block | list-item | inline-block | table |
  inline-table | table-row-group | table-header-group |
  table-footer-group | table-row | table-column-group | table-column |
  table-cell | table-caption | none | inherit
  
######### Property values
####### Floats
######## float
######### Def
- Value: left | right | none | inherit
######### Property values
########## left
- generates a block box that is floated to the left.
########## right
- similar to 'left', except the box is floated to the right.
########## none
- The box is not floated.
######## clear
- indicates which sides of an element's box(es) mey not be adjacent to an earlier floating box.
- floatプロパティで指定された要素に対する回り込みを解除する際に使用する。
######### Def
- Value : none | left | right | both | inherit
####### Relationships between 'display', 'position', and 'float'
- The three properties that affect box generation and layout interact as follows.
  1. If 'display' has the value 'none', then 'position' and 'float' do not apply.
     In this case, the element generates no box.
  2. If 'position' has the value 'absolute' or 'fixed', the box is absolutely positioned,
     the computed value of 'float' is 'none'
  3. If 'float' has a value other than 'none', the box is floated

###### Visual effects
####### Overflow and clipping
######## overflow
- ボックスの範囲内に内容が入りきらない場合に、はみ出た部分の表示の仕方を指定する。
######### Def
- Value: visible | hidden | scroll | auto | inherit
######### Porpety values
########## visible
- indicateing that content is not clipped, i.e., it may be rendered outside the block box.
########## hidden
- indicating the content is clipped 
  and that no scrolling user interface should be provided to view the content outside the clipping region.
########## scroll
- the content is clipped and that if the user agent uses a scrolling mechanism that is visible on the screen
########## auto
######## clip
- ボックスの切り抜き表示を行う
###### Generated content, automatic numbering, and lists
####### Lists
######## list-style-type
######### Def
- Value:
  disc | circle | square | decial | decimal-leading-zero |
  lower-roman | upper-roman | lower-greek | lower-latin | upper-latin |
  armenian | georgian | lower-alpha | upper-alpha | none | inherit
- Initial: disc
######### Values
########## Glyphs
########### disc
########### circle
########### square
########## Numbering
########### decimal
########### decimal-leading-zero
########### lower-roman
########### upper-roman
########### georgian
########### armenian
########## Alphabetic
########### lower-latin, lower-alpha
########### upper-latin, upper-alpha
########### lower-greek
######## list-style-image
######## list-style-position
######## list-style
###### Paged media
###### Colors and Backgrounds
###### Fonts
####### font-family
- prioritized list of font family names and/or generic family names.
- defines the font to be used.
######## Def
- Value: [[ <family-name> | <generic-family> ][, <family-name> | <generic-family>]* ] | inherit
- Initial: depends on user agent
- INherited: yes
- Media: visual
######## Ex
- body { font-family: Gill, Helvetica, sans-serif }
######## Generic font families
- serif
- sans-serif
- cursive
- fantasy
- monospace
####### font-style
####### font-variant
####### font-weight
####### font-size
- the text size to be used.
- corresponding to the em square, a concept used in typography.
######## Def
- Value:
  <absolute-size> | <relative-size> | <length> | <percentage> | inherit
######### absolute-size
- xx-small
- x-small
- small
- medium
- large
- x-larg
- xx-large
######### relative-size
- larger
- smaller
####### font
- Shorthand font property
###### Text
###### Tables
####### Borders
######## border-cllapse
- 隣接するボーダーを重ねて表示するか話して表示するか設定する。
######### Def
- Value: collapse | separate | inherit

######## border-spacing
######### Def
- Value: <length> <length>? | inherit
######## empty-cells
######### Def
- Value: show | hide | inherit
###### User interfaces
###### Link
- [[https://www.w3.org/TR/CSS2/][Cascading Style Sheets Level 2 Revision 1 (CSS 2.1) Specification - W3C]]
- [[http://momdo.s35.xrea.com/web-html-test/spec/CSS21/cover.html][Cascading Style Sheets Level 2 Revision 1 (CSS 2.1) Specification 日本語訳 - W3C]]
#### Testing
#### Refining
##### CSS Cascaing Variables
- CR
##### CSS Level 2 Revision 2
###### Syntax and basic data types
###### Selectors
###### Assigning property values, Cascading, and Inheritance
###### Media types
###### Box model
###### Visual formatting model
###### Visual effects
###### Generated content, automatic numbering, and lists
###### Paged media
###### Colors and Backgrounds
###### Fonts
###### Text
###### Tables
###### User interfaces
###### Link
- [[https://www.w3.org/TR/CSS22/][Cascading Style Sheets Level 2 Revision 2 (CSS 2.2) Specification - W3C]]
- [[https://momdo.github.io/css2/Overview.html][Cascading Style Sheets Level 2 Revision 2 (CSS 2.2) Specification 日本語訳 - W3C]]
### CSS 3
#### Completed
##### Standards
###### CSS Color Module Level3
- REC 2011/6/7
####### Link
- [[http://standards.mitsue.co.jp/resources/w3c/TR/css3-color/][CSS カラーモジュール Level 3 - W3C]]
###### CSS Namespaces Module Level 3
- REC 2011/9/29
###### Selectors Level 3
- REC 2011/9/29

###### Media Queries
- REC 2011/6/19
###### CSS Style Attributes
- REC 2013/11/7

#### Drafts
##### PR / Proposed Recommendations
###### CSS Backgrounds and Borders Level 3
###### CSS Conditional Rules Level 3
###### CSS Multi-column Layout
###### CSS Values and Units Level 3
###### CSS Cascading and Inheritance Level 3
##### CR / Candidate Reccomendations
###### CSS Image Values and Replaced Content Level 3
###### CSS Speech
###### CSS Flexible Box Layout
- https://www.w3.org/TR/css-flexbox-1/
###### CSS Text Decoration Module Level 3
###### CSS Fonts Level 3
###### CSS Writing Modes Level 3
###### CSS Counter Styles Level 3
###### CSS Fragmentation Level 3
###### CSS Syntax Level 3
###### CSS Basic User Interface Level 3
##### WD / Other Working Drafts
###### CSS Text Module Level 3
####### Spec
- https://drafts.csswg.org/css-text-3/
- https://www.w3.org/TR/css-text-3/
######## 1.Introduction
######## 2.Transforming Text
######## 3.White Space and Wrapping
######## 4.White Space Processing Details
######## 5.Line Breaking and Word Boundaries
######### 5.2 Breaking Rules for Letters: 'word-break' property
########## word-break
- Name: word-break
- Value: normal | keep-all | break-all
########### Values
############ normal
- デフォルトの改行ルール
############ break-all
- CJK以外のテキストは単語中での改行禁止
############ keep-all
- CJKテキストの改行を許可しない。CJK以外はデフォルト挙動
############ break-word
- To prevent overflow, normally unbreakable words may be broken at arbitrary points
######## 6.Breaking Within Words
######### 6.2 Overflow Wrapping: the 'overflow-wrap'/'word-wrap' property
########## 'overflow-wrap' / 'word-wrap'
########### Values
############ normal
- Lines may break only at allowed break points.
############ break-word
- 
############ break-spaces

######## 7.Alignment and Justification
######## 8.Spacing
######## 9.Edge Effects
####### Memo
######## word-break, overflow-wrap/word-wrap
- overflow-wrap/word-wrap: 単語の途中で改行するかどうか
  https://developer.mozilla.org/en-US/docs/Web/CSS/overflow-wrap
- word-break: 行の途中で改行するかどうか
  https://developer.mozilla.org/en-US/docs/Web/CSS/word-break
### CSS 4
#### Testing
##### CSS Cascading and Inheritance Level 4
###### Importing Style Sheets
###### Shorthand Properties
###### Value Processing
####### Declared Values
####### Cascaded Values
####### Specified Values
####### Computed Values
####### Used Values
####### Actual Values
###### Filtering
###### Cascading
###### Defaulting
####### Initial Values
####### Inheritance
####### Explicit Defaulting
######## initial : Resetting a Property
######## inherit : Explicit Inheritance
######## unset : Erasing All Declarations
######## revert : Rolling Back The Cascade
- user-agent origin
- user origin
- author origin
###### Changes
## Functions(tmp)
### transforms
- https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Transforms
- Specification: CSS Transforms Level 1 (WD)
  https://drafts.csswg.org/css-transforms/
#### Properties
##### rotate
##### scale
##### transform
## Properties
### Foundamentals
#### box
##### size
- ex)
  div {
    width:100px;
    height:100px;
  }

###### width
###### height
###### max-width
###### min-width
###### max-height
###### min-height

##### background
###### background-color
- 
  div {
    background-color:red;
  }

###### background-image
- 
  div {
    background-image:url(image.png);
  }

##### border, padding, margin
###### padding
- 
  枠線と中身の間隔

###### border
- 
  枠線と中身の間隔

####### border
- 上下左右の枠線
####### border-left
- 左側の枠線
####### border-right
- 右側の枠線
####### border-top
- 上側の枠線
####### border-bottom
- 下側の枠線

###### margin
- 
  枠線の外側の外側の余白

###### value
####### 太さ
- 数値, thin, medium, thick
####### 色
####### スタイル
- none, dotted, dashed, solid, double groove, ridge, inset, outset

###### ex
- 
  margin:10px; /* (上下左右) */
  margin:10px 20px; /* (上下) (左右) */
  margin:10px 20px 30px; /* (上) (左右) (下) */
  margin:10px 20px; /* (上) (右) (下) (左) */

##### display
###### none
- 非表示
###### inline
- インライン要素
  高さや幅を指定できない。
###### block
- ブロック要素
###### inline-block
- インラインに入れるブロック要素
  高さと幅が指定された上で、インライン要素のように横並びになる。

##### placement
###### float
- ボックスを左か右に寄せるためのプロパティ。
###### position
- ボックスの配置方法を指定できる。

####### property
- static
  初期位置
- relative
  初期位置を基準とした相対位置
- absolute
  親要素を基準とした絶対位置
- fixed
  絶対位置・固定

####### 例
- 
  div {
    position:relative;
    top:20px;
    left:20px;
  }

#### text
##### color
- ex
  p {
    color:#ffffff;
  }
  
##### font-size
- ex
  p {
    font-size:13px;
  }

##### font-weight
- properties
  - normal
  - bold
  - 100~900

- ex
  p {
    font-weight:bold;
  }
  
##### font-family
− font-family

- ex
  p {
    font-family: "MS Pゴシック";
  }

##### text-align
- text-align
  - left
  - center
  - right

- ex)
  p {
    text-align: center;
  }

#### action
##### hover
- on mouse
  
- ex
  div:hover {
    background:red;
  }

##### active
- on click
  
- ex
  div:active {
    background:red;
  }

#### class, id
- class
  classは、スペースを開けて指定することで複数のクラスを指定することが出来る。
  ex) <div class="one two three">
  
### Reference
#### Color, Background
##### color
- text color
##### background
##### background-attachment
##### background-color
##### background-image
- url("url")
- none
  not useing images. default value.

##### background-position
##### background-size
- auto
  default value.
  calculate automatically

- contain
  keep aspect ratio, maximum size including the area.

- cover
  keep aspect ratio, minimum size covering the area.
  
- (length)
  ex) 10px 10px
  
- (parcentage)
  ex) 50% auto

#### Font
##### font
##### font-style
##### font-variant
##### font-weight
##### font-size
##### font-family
- フォントの種類
- 複数フォントをカンマ区切りで書く。前に書かれたフォントが優先される。
  日本語フォントよりも英語フォントを先に書く。
###### Values
####### 総称フォントファミリー
######## sans-serif : ゴシック体
######## serif : 明朝体
######## cursive : 筆記体系
######## fantasy : 装飾系
######## monospace : 等幅系
####### font
- なんでも使える。スペースが入っている場合はダブルクォートで囲む。
  OSに
######## verdana
######## courier
##### font-size-adjust
##### font-stretch
#### Text
##### line-height
- 行の高さを指定する

- value
  - normal
  - 数値に単位をつけて指定
  - 数値のみで指定
  - %で指定

##### text-align
- 行揃えの位置・均等割付を指定する

- value
  - left
  - right
  - center
  - justify

##### white-space
- ソース中のスペース・タブ・改行の表示の仕方を指定する

##### letter-spacing
- 文字の間隔を指定する

- value
  - normal
    標準の間隔にする。初期値。
  - 数値指定

##### word-spacing
- 単語の間隔を指定する。

#### Width, Height
##### width
##### max-width
##### min-width
##### height
##### max-height
##### min-height
#### Margin, Padding
##### margin
- auto
  same width of both side margin.
  only effect to each side, not to top and bottom.
  need to set "width" properties.
  
##### margin-top
##### margin-bottom
##### margin-left
##### margin-right
##### padding
##### padding-top
##### padding-bottom
##### padding-left
##### padding-right
#### Border
##### border
##### border-color
##### border-style
##### border-width
##### border-top
##### border-top-color
##### border-top-style
##### border-top-width
##### border-bottom
##### border-bottom-color
##### border-bottom-style
##### border-bottom-width
##### border-left
##### border-left-color
##### border-left-sytle
##### border-left-width
##### border-right
##### border-right-color
##### border-right-style
##### border-rightwidth
#### Display, Location
##### overflow
##### position
- 
  ボックスの配置方法が、相対位置か絶対位置かを指定する。
  実際の表示位置指定は、top, bottom, left, rightを併用する。

- value
  - static（初期値）
    配置位置を指定せず、top, bottom等は適用されない。
  - relative
    相対位置の配置となる。staticの位置が基準位置となる。
  - absolute
    絶対位置への配置となる。
    親ボックスイにstatic以外の位置が指定されている場合、親ボックスの左上が基準となる。
  - fixed
    絶対位置への配置となるが、スクロールしても位置が固定されたままとなる。

##### top
##### bottom
##### left
##### right
##### display
- 要素の表示形式（ブロック・インライン）を指定する

- value
  - inline
    インラインボックスを生成する（初期値）
  - block
  - list-item
  - inline-block
  - table
  - none
  - inherit

##### float
- 左または右に寄せて配置する
##### clear
- 回り込みを解除する
##### z-index
- 重なりの順序を指定する

- value
  - auto(初期値)
    親要素と同じ階層となる。
  - 整数値
    0を基準として、大きいものほど上になる。

##### visibility
- ボックスの表示・非表示を指定する
#### Table
##### table-layout
##### caption-side
##### border-collapse
- セルのボーダーの表示の仕方を指定する。

- value
  - collapse
    セルのボーダーを重ねて表示する。
  - separate
    セルのボーダーを間隔を開けて表示する。
    テーブル全体の線と、セルごとの線が離れて表示される。

#### List
#### Insert, Quote
#### Outline
#### Cursor
##### cursor
- カーソルの形状を指定する
  
- value
  - auto
    ブラウザが自動的に選択したカーソル
  - default
    矢印形など利用環境の標準カーソル
  - pointer
    リンクカーソル
  - crosshair
    十字カーソル
  - move
    移動カーソル
  - text
    テキスト編集カーソル
  - wait
    待機・処理中カーソル
#### Print
#### Filter
#### Sound
### CSS3 Modules
#### Backgrounds and Borders
##### Background
###### background-clip
###### background-size
##### Rounded corners
###### border-radius
- 角丸をまとめて指定する。

- value
  - 水平方向左上 右上 右下 左下 / 垂直方向左上 右上 右下 左下
    ex) border-radius: 100px 25px 50px 50px / 50px 25px 50px 25px

##### Box Display
###### box-shadow
- ボックスに影をつける
  影は2~4つの長さの値で定義される。任意で色、insetキーワードを指定できる。

- format
  - 1. 水平方向の影のオフセット距離
  - 2. 垂直方向の影のオフセット距離
  - 3. ぼかし距離
  - 4. 広がり距離

  - 色：影の色を指定する。
  - insetキーワード: 外側から内側の影に変更される。

- value
  - none(初期値)
    影をつけない
  - 上記フォーマットの羅列

- ex
  box-shadow: 10px 10px 10px 10px rgba(0,0,0,0.4) inset;

#### 2D 3D Transforms
#### Transitions
##### transition
- transition効果（時間的変化）をまとめて指定する。以下の順で指定。
  - transition-property
  - transition-duration
  - transition-timing-function
  - transition-delay
##### transition-property
- transition効果を適用するCSSプロパティ名を指定する
  初期値はall。
  
- value
  - all
  - none
  - 変化させるプロパティ名のリストをカンマ区切りで指定。

##### transition-duration
- 変化に掛かる時間を指定する
  初期値は0

##### transition-timing-function
- 変化のタイミング・進行割合を指定する

- value
  - ease（初期値）
    開始と終了を滑らかにする。cubic-bezier(0.25, 0.1, 0.25, 1.0)を指定したのと同じ。
  - linear
    一定。cubic-bezier(0.0, 0.0, 1.0, 1.0)と同じ
  - ease-in
    ゆっくり始まる。cubic-bezier(0.42, 0, 1.0, 1.0)を指定したのと同じ。
  - ease-out
    ゆっくり終わる。cubic-bezier(0, 0, 0.58, 1.0)を指定したのと同じ。
  - cubic-bezier(x1, y1, x2, y2)
    3次ベジェ曲線のP1とP2を指定。

##### transition-delay
- 変化がいつ始まるかを指定する

- value
  - 時間
    変化が始まる時間を指定。

#### Animations
#### Color
##### opacity
- 
  set transparency
  要素の透明度を指定。
  
- value
  - 0.0(完全に透明)〜1.0(完全に不透明)
    初期値は1。
  - inherit
    継承する

##### rgba
- RGBAカラーモデルで色を指定する。
  red/green/blue/alpha。alphaは透明度。
  RGBは0-225, alphaは0(完全に透明)~1(完全に不透明)
  
- ex
  p.sample {background-color: rgba(0,0,255,0.5);}
  
#### Basic User Interface
##### box-sizing
- 
  ボックスの算出方法を指定する際に使用する。

- value
  - content-box
    パディングとボーダーを幅と高さに含めない（初期値）
  - border-box
    パディングとボーダーを幅と高さに含める。
    すべての要素に指定することが推奨されている。
  - inherit
    親要素の値を継承する
## Selecter
### 全称セレクタ
- 
  アスタリスク(*)を記述してすべての要素を対象にスタイルを適用する。

### タイプセレクタ
- 
  要素名を使った指定は、要素をそのまま記載すればよい。
  ex) p { color: red; }

### クラスセレクタ
- 
  クラス名はピリオド(.)に続けて記述する。
  ex) .example { color: red; }
  要素名に続けて指定する方法もある。

### IDセレクタ
- 
  IDを使った指定では、ハッシュ(#)に続けて記述する。
  ex) #example { color: red; }
  要素名に続けて指定する方法もある。

### 属性セレクタ
- 
  要素名に続けて[]を記述して、属性名や属性値を指定する。
  
  |-------------------+----------------------------------------------------------------------------------|
  | 属性セレクタ      | 説明                                                                             |
  |-------------------+----------------------------------------------------------------------------------|
  | [属性名]          | 属性名が一致する要素に適用される                                                 |
  | [属性名="属性値"  | 属性名と属性値が一致する要素に適用される                                         |
  | [属性名~="属性値" | 属性名と属性値が一致する要素に適用される(スペースで区切られた複数の属性値に対応) |
  | [属性名l="属性値" | 属性名と属性値が一致する要素に適用される(ハイフンで区切られた属性値に対応)       |
  |-------------------+----------------------------------------------------------------------------------|

### その他セレクタ
- 複数セレクタ
  セレクタをカンマで区切ると、複数のセレクタに同じスタイルを適用できる。
  ex) h2, p { color: blue; }
  
- 子孫セレクタ
  あるセレクタ配下の全ての子孫セレクタを対象にスタイルを適用する。
  ex) p strong { background-color: #3399FF; }

- 子セレクタ
  あるセレクタ直下の子セレクタを対象にスタイルを適用する。
  ex) p > strong { background-color: #3399FF; }

- 隣接セレクタ
  隣接する要素を対象にスタイルを適用する。
  ex) h2 + p { color: #0000FF; }

### 擬似クラス
#### :link
#### :visited
#### :hover
- カーソルがのっている要素にスタイルを適用する。

#### :active
- クリック中の要素にスタイルを適用する

#### :focus
#### :lang
#### :first-child
#### :first-line
#### :first-letter
#### :before
#### :after
### 擬似要素

## SASS
- SCSSというフォーマットに対応。
  ネスト、変数の使用、ミックスインに対応。

### ネスト
- 共通のパターンがある場合にネスト可能。(子孫セレクタのみ？)
  ex)
    .center {
      text-align: center;
    }
    .center h1 {
      margin-bottom: 10px;
    }
    ⇒
    .center {
      text-align: center;
      h1 {
        margin-bottom: 10px;
      }
    }

- 親属性を参照する必要がある場合は&を使う。
  ex)
    #logo {
      float: left;
      ...
    }
    #logo:hover {
      color: #fff;
      ...
    }
    ⇒
    #logo {
      float: left;
      ...
      &:hover {
        color: #fff;
        ...
      }
    }

### 変数 
- 
  ドルマーク($)を使って変数を定義できる。
  （ちなみにLESSでは@マークを使っている。）

### Link
- [[http://sass-lang.com/documentation/file.SASS_REFERENCE.html][SASS_REFERENCE]]
## Memo
### CSS Levels
#### CSS Level 1
- 1996/12勧告。
#### CSS Level 2
- 1998/5勧告
  CSS1の上位互換。幾つかの概念の追加・拡大・改定が行われた。
  実施素敵にCSS2.1に仕様としての役割を委ねた形になっている。
  CSS2は管理されておらず、CSS2.1を基にするよう奨励されている。
#### CSS Level 2.1
- 2011/6勧告。
  CSS2の改訂版。CSS2の定義が不明瞭で各ユーザーエージェントに非互換が生じたため、
  曖昧な記述を明確にするための改定が行われた。
  ベンダは2002年ごろからCSS2.1を基本仕様と見なしている。
#### CSS Level 2.2
#### CSS Level 3
- CSS Level 3 uses CSS2.1 spec as its core, and builds on Level 2 module by module.
  Each module adds functionality and/or replaces part of the CSS 2.1 spec.
#### CSS Level 4
- CSS Level 4 and beyond
  There is no CSS Level 4.
  CSS as the language has no longer levels, and independent modules can reach level 4 or beyond.
### 記述箇所
- 上のものから順に優先的に適用される。
  同じ箇所に書いた場合、下に書いたものが優先される。
#### 1. Inline / HTMLタグに埋め込む
- by using the style attribute in HTML elements
- 
  <p style="color:red;">あいうえお</p>

#### 2. Internal / HTMLファイル内に埋め込む
- by using a <style> element in the <head> section
- 
  <head>
    <style>
      div {background: red;}
      h1  {color: blue;}
    </style>
  </head>

#### 3. External / CSSファイルに記述
- by using an external CSS file
- ex
  - html side
    <head>
      <link rel="stylesheet" href="styles.css">
    </head>
  - css side
    div {
      background-color: red;
    }
    h1 {
      color: blue;
    }

### Comment
- 
  /* ... */ でコメントアウトできる。

### Media Query メディアクエリ
- CSS3の機能。
  メディアタイプとメディア特性を利用して、スタイルシートの適応条件を決定する式。

- link要素として指定する場合
  <link rel="stylesheet" href="small.css" media="screen and (max-width:480px)">
  <link rel="stylesheet" href="medium.css" media="screen and (min-width:480px) and (max-width:1024px)">
  <link rel="stylesheet" href="wide.css" media="screen and (min-width:1024px)">

- スタイルシートに指定する場合
  @media screen and (max-width:780px) { 
    /* 780以下の場合 */
  }
  @media screen and (min-width:780px) and ( max-width:1024px) {
    /* 780以上1024の場合*/
  }
  @media screen and (min-width:1024px) {
    /* 1024以上の場合 */
  }

- Media features
  

- Link
  [[https://www.w3.org/TR/css3-mediaqueries/][Media Queries - W3C]]
  
### ベンダープレフィックス
- ブラウザベンダーが独自の拡張機能を実装するとき、または草案段階の仕様を先行実装する場合に付ける識別子のこと。
- [[http://scene-live.com/page.php?page=43][【CSS3】ベンダープレフィックスとは？ - SCENE LIVE]]

#### -ms- (Internet Explorer)
#### -webkit- (Google Chrome, Safari)
#### -moz- (Firefox)
#### -o- (Opera)
### floatの処理
#### clearプロパティを使う
- margin-topが効かない、などのデメリットあり。
  （実際は効いていないわけではなく、フロートした子要素を無視してマージンを付けている）
#### clearfixを行う
- clearfixという解除用クラスを親要素に与え、子要素のfloatを解除する。
- 例
.clearfix:after {
    content: ".";
    display: block;
    height: 0;
    clear: both;
    visibility: hidden;
}

.clearfix {display: inline-table;}

#### overflowを利用する
- overflow(auto/hiddenなど)を利用することで、
#### Link
- [[http://taneppa.net/float/][CSSの【float】についてちょっと本気出して説明してみた。 - Taneppa!]]

### Variable Units / 変数単位
- [[https://coliss.com/articles/build-websites/operation/css/the-future-of-css-variable-units.html][CSSは確実に進化している！ 新機能、単位を変数として利用できる「Variable Units（変数単位）」 - coliss]]
- css-variables-2の仕様、まだ開発途中。

## Link
### 仕様系
- [[https://www.w3.org/Style/CSS/][Cascading Style Sheets home page - W3C]]
- [[https://www.w3.org/Style/CSS/read][Understanding the CSS Specifications - W3C]]

- [[https://www.w3.org/TR/CSS/#css][CSS Snapshot - W3C]]
- [[https://www.w3.org/Style/CSS/specs.en.html][Descriptions of all CSS specifications - W3C]]

- [[http://momdo.s35.xrea.com/web-html-test/CSS3-ja/][CSS3の日本語訳集]]
- [[http://www.htmq.com/style/index.shtml][スタイルシートリファレンス（目的別） - HTMLクイックリファレンス]]
- [[http://www.htmq.com/css3/index.shtml][CSS3リファレンス - HTMLクイックリファレンス]]

*** その他
- [[https://speakerdeck.com/tonkotsuboy_com/2022nian-falsemodancssgai][2022年のモダンCSS改 - tonkotsuboy_com - speakerdeck]]
