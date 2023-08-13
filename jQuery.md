# jQuery
- fast, small, and feature-rich JavaScript library.
- 容易に記述できるようにするためのJavaScriptライブラリ。

## jQuery
### Fundamentals
- 使い方
  - 
    1. jQueryオブジェクトを作成（セレクタ）
    2. jQueryオブジェクトに対しメソッドを呼び出す（メソッド）
  
  - format
    $('セレクタ').メソッド(引数);

- 読み込み
  - jQueryの読み込み
    headタグにurlを埋め込むのが一般的。
    <script src="https://~jquery.min.js"></script>

  - jQuery Scriptの読み込み
    bodyタグの最後に書くことで、表示速度を速めることをよく行う。
    <script src="myjQueryScripts.js"></script>

- ファイルの書き方
  $(document).ready()の中に処理を書く。
  省略形として、$(function(){});と書いてもよい。
  
  - format
    $(document).ready(function(){
      // write jQuery here
    });
    
    $(function(){
      // write jQuery here
    });

#### Event
- 処理を行うタイミングを指定できる。

- format
  $('セレクタ').イベント名(function(){
    // 処理
  });
  
#### Variables
- 
  変数をvar宣言して使う。頭に$を用いて、jQueryで使うことを分かりやすくする。

- ex)
  var $div = $('div');

#### Method Chain
- 
  連続してオブジェクトにメソッドを適用する。

- ex)
  $('div').css('color', 'red').html('jQuery');

### Selector セレクタ
- 基本的にはCSSと同じ方式。

- id
  #で指定する。

- class
  .で指定する。

- this
  イベントが起こった要素を取得できる。クォートでは囲まない。

### API
#### Ajax
#### CSS
##### .css()
- 
  Get the value of a computed style property for the first element in the set of matched elements
  or set one or more CSS properties for every matched element.

#### Effects
##### Basics
###### fadeIn()
- Display the matched elements by fading them to opaque.

###### fadeOut()
- Hide the matched elements by fading them to trasparent.

###### hide()
- Hide the matched elements.

###### show()
- Display the matched elements.
  表示する

###### slideDown()
- Display the matched elements with a sliding motion.
###### slideUp()
- Hide the matched elements with a sliding motion.

#### Events
##### Mouse Event
###### .click()
- Bind an event handler to the "click" JavaScript event, or trigger that event on an element.

###### .hover()
- 
  Bind one or two handlers to the matched elements, to be executed when the mouse pointer enters and leaves the elemensts.
  2つの引数をとる。1つ目はマウスを乗せたとき、2つ目はマウスを除いた時の挙動。カンマで区切る。
  
- ex)
  $('div').hover(
    function(){
      // on mouse event
    },
    function(){
      // off mouse event
    }
  };

#### Manipulation
##### Class Attribute
###### .addClass()
- 
  Adds the specified class(es) to each element in the set of matched elements.

###### .hasClass()
- 
  Determine whether any of the matched elements are assigned the given class.

###### .removeClass()
- 
  Remove a single class, multiple classes, or all classess from each element in the set of matched elements.

##### DOM Insertion, Inside

###### .html()
- 
  Get the HTML contents of the first element in the set of matched elements or set the HTML contents of every matched element.

###### .text()
- 
  Get he combined text contents of each element in the set of matched elements, 
  including their descendants, or set the text contents of the matched elements.

#### Traversing
##### Tree Traversal
###### .children()
- 
  Get the children of each element in the set of matched elements, optionally filtered by a selector.
  自分の一つ下の子要素までを選択。

###### .find()
- 
  Get the descendants of each element in the current set of matched elements, filtered by a selector, jQuery object, or element.
  自分以下の子孫要素を全て選択。

- ex)
  $('Wrapper').find('a').css('color', 'red');

##### Filtering
###### .eq()
- 
  Reduce the set of matched elements to the one at the specified index.
  
### Memo
#### 読み込む位置
- 最近は体感スピード向上のため、</body>直前で読み込むことが多い模様。

### Link
- [[http://jquery.com/][jQuery]]
## jQuery UI
## jQuery mobile
- a unified, HTML5-based user interface system for all popular mobile device platforms.
## QUnit
## Sizzle
