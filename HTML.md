# HTML
## HTML5
### Specification
#### Common infrastructure 共通インフラ
- 適合クラス、アルゴリズム、定義、および残りの使用の共通部分
##### Common microsyntaxes
###### Common parser idioms
###### Boolean attributes
###### Keywords and enumerated attributes
###### Number
####### Signed integers
####### Non-negative integers
####### Floating-point numbers
####### Percentages and lengths
####### Lists of integers
####### Lists of dimensions
###### Dates and times
####### Months
####### Dates
####### Yearless dates
####### Times
####### Floating dates and times
####### Time zones
####### Global dates and times
####### Weeks
####### Durations
####### Vaguer moments in time
###### Colors
####### Color Name
- using color name, like "Aqua", "Blue", "Ivory", etc.
  [[https://www.w3schools.com/colors/colors_names.asp][Color Names Supported by All Browsers - w3schools.com]]
####### RGB Value
- like rgb(255,0,0) -> Red
####### Hex Value
- like #FF0000 -> Red
###### Space-separated tokens
###### Comma-separated tokens
###### References
###### Media queries
#### Semantics, structure, and APIs of HTML documents
##### Documents
- 
  HTMLユーザエージェントにおいてすべてのXMLおよびHTML文書は、Documentオブジェクトによって表される。
  
###### Document Object
##### Elements
###### Semantics
###### Elements in the DOM
###### HTML element constructors
###### Element definitions
####### Attributes
###### Content models
####### The "nothing" content mobel
####### Kinds of content
######## Metadata content
- Elements
  - base, link, meta, noscript, script, style, template, title
- About
  - Metadata content is content that sets up the presentation or behavior of the rest of the content,
    or that sets up the relationship of the document with other documents, or that conveys other "out of band" information.
  - 見栄えまたは後のコンテンツの振る舞いを設定する、または他の文書との関係を設定する、または他の"帯域外の"情報を運搬するコンテンツ。
######## Flow content
- Elements
  - a, abbr, address, area(map要素の子孫の場合), article, aside, audio, b, bdi, bdo, blockquote,
    br, button, canvas, cite, code, data, datalist, del, dfn, div, dl, em, embed, fieldset, figure, footer, form,
    h1, h2, h3, h4, h5, h6, header, hr, i, iframe, img, input, ins, kbd, keygen, label, main, map, mark,
    math, meter, nav, noscript, object, ol, output, p, pre, progress, q, ruby, s, samp, script, section,
    select, small, span, strong, sub, sup, svg, table, template, textarea, time, u, ul, var, video, wbr, Text
- About
  - Most elements that are used in the body of documents and applications are categorized as flow content.
  - 文書及びアプリケーションのbodyで使用される多くの要素。
######## Sectioning content
- Elements
  - article, aside, nav, section
- About
  - Sectioning content is content that defines the scope of headings and footers.
  - 見出しおよびフッターの範囲を定義するコンテンツ。
######## Heading content
- Elements
  - h1, h2, h3, h4, h5, h6
- 
  セッションのヘッダーを定義する。
######## Phrasing content
- Elements
  - a, abbr, area(map要素の子孫の場合), audio, b, bdi, bdo, br, button, canvas, cite, code, data,
    datalist, del, dfn, em, embed, i, iframe, img, input, ins, kbd, keygen, label, map, mark, math, meter,
    noscript, object, output, progress, q, ruby, s, samp, script, select, small, span, strong, sub, sup, svg,
    template, textarea, time, u, var, video, wbr, Text
- 
  文書のテキストおよび段落内レベルでそのテキストをマークアップする要素。

######## Embedded content
- Elements
  - audio, canvas, embed, iframe, img, math, object, svg, video
- 
  他のリソースから文書に取り込むコンテンツか、文書へ挿入される他の語彙由来のコンテンツ。
  
######## Interactive content
- Elements
  - a, audio(controls属性が存在する場合), button, embed, iframe, img(usemap属性が存在する場合), 
    input(type属性がhidden状態でない場合), keygen, label, object(usemap属性が存在する場合),
    select, textarea, video(controls属性が存在する場合)
- 
  ユーザーとの交流を意図するコンテンツ。
######## Palpable content
- Elements
  - a, abbr, address, article, aside, audio(control属性が存在する場合), b, bdi, bdo, blockquote,
    button, canvas, cite, code, data, dfn, div, dl(要素の子が少なくとも1つの名前-値グループを含む場合),
    em, embed, fieldset, figure, footer, form, h1, h2, h3, h4, h5, h6, header, i, iframe, img,
    input(type属性がhidden状態でない場合), ins, kdb, keygen, label, main, map, mark, math,
    meter, nav, object, ol(要素の子が少なくとも1つli要素を含む場合), output, p, pre, progress, q,
    ruby, s, samp, section, select, small, span, strong, sub, sup, svg, table, textarea, time, u, 
    ul(要素の少なくとも1つli要素を含む場合), var, video, 要素内の空白文字でないText
- About
  - As a general rule, elements whose content model allaws any flow content or phrasing content should have at least one node in its contents
    that palpable content and that does not hav the hidden attribute specified.
  - 「明白・明瞭な」コンテンツ、という意味。
    フローコンテンツかフレージングコンテンツは、パルパブルコンテンツを内容に持つべきである、
######## Script-supporting elements
- Elements
  - script, template
- About
  - Script-supporting elements are those that do not represent anything themselves, but are used to support scripts, e.ge to provide functionality for the user.
  - 自分自身で何も表さない（レンダリングされない）が、たとえばユーザに機能を提供するために、スクリプトをサポートするために使用される。
  
######## Etc
######### Sectioning root
###### Global attributes
####### Common attributes
######## accesskey
######## contenteditable
######## dir
######## draggable
######## hidden
######## is
######## itemid
######## itemprop
######## itemref
######## itemscope
######## itemtype
######## lang (xml:lang?)
- 
  要素のコンテンツに対する基本言語およびテキストを含むあらゆる要素の属性に対して指定する。
  その値は妥当なBCP47言語タグまたは空も次である必要がある。

######## spellcheck
######## style
######## tabindex
######## title
- 要素に関するアドバイザリー情報を表すテキストを包含する。
######## traslate
####### Event handler content attributes 
######## onabort
######## onauxclick
######## onblur
######## oncancel
######## oncanplay
######## oncanplaythrough
######## onchange
######## onclick
######## onclose
######## oncontextmenu
######## oncuechange
######## ondblclick
######## ondrag
######## ondragend
######## ondragenter
######## ondragexit
######## ondragleave
######## ondragover
######## ondragstart
######## ondrop
######## ondurationchange
######## onemptied
######## onended
######## onerror
######## onfocus
######## oninput
######## oninvalid
######## onkeydown
######## onkeypress
######## onkeyup
######## onload
######## onloadeddata
######## onloadedmetadata
######## onloaend
######## onloastart
######## onmousedown
######## onmouseenter
######## onmouseleave
######## onmousemove
######## onmouseout
######## onmouseover
######## onmouseup
######## onwheel
######## onpause
######## onplay
######## onplaying
######## onprogress
######## onratechange
######## onreset
######## onressize
######## onscroll
######## onsecuritypolicyviolation
######## onseeked
######## onseeking
######## onselect
######## onstalled
######## onsubmit
######## onsuspend
######## ontimeupdate
######## ontoggle
######## onvolumechange
######## onwaiting
####### Custom data attributes
######## data-* (Embedding custom non-visible data with the data-* attributes)
####### old?
######## id
######## xml:base
###### WAI-ARIA
- 
  ARIA
  詳細については別ドキュメント等参照。
####### ARIA Role Attrilubet
- 
  すべてのHTML要素はARIA roleが指定された属性を持って良い。
####### ARIA State and Property Attribute
- 
  すべてのHTML要素は、ARIAステートおよびプロパティー属性を指定させても良い。
#### HTML elements
##### Root element
###### html
- html element represents the root.
- 
  HTML文書のルートを表す。
  ルートのhtml要素にlang属性を指定することが推奨される。
####### Def
- 
  - Category : なし
  - Contexts
    As the root element of a document.
  - Contents model : 
    head要素、続いてbody要素
  - Content attributes :
    グローバル属性
    manifest : アプリケーションキャッシュマニフェスト
  - Tag omission
  - Allowed ARIA role
  - Allowed ARIA state and property

##### Document metadata
###### base
- 相対URLを解決する目的で文書の規定URLを指定、および次に続くハイパーリンクのためにデフォルトでブラウジングコンテキストの名前の指定を許可する。
  href属性またはtarget属性のいずれか、あるいはその両方を持たなければならない。

####### Def
- Category : Metadata
- Contexts : 他のbase要素を含まないhead要素内
- Contents model : 空
- Content attributes :
  グローバル属性
  href : 文書基底URL
  target : ハイパーリンクナビゲーションおよびフォーム送信に対するブラウジングコンテキスト
- Tag omission : 終了タグなし
  
###### head
- 
  Documentに関するメタデータの集まり。
####### Def
- Category : None なし
- Content attributes:
  - Global attributes
 
###### link
- 著者が文書を他のリソースとリンクするのを可能にする。
  リンクの宛先はhref属性によって与えられ、これは存在し、妥当なURLを含まなければならない。
  また、rel属性を持たなければならない。
####### Def
- Category :
  - Metadata
  - flow content (If the element is allowed in the body)
  - phrasing content (If the element is allowed in the body)
- Contexts :
  - メタデータが期待される場所
  - head要素の子であるnoscript要素内。
- Content attributes :
  - Global attributes グローバル属性
  - href : ハイパーリンクのアドレス
  - crossorigin : 要素がcrossorigin要求を処理する方法
  - rel : ハイパーリンクと宛先のリソースを含む文書の関係
    ex) stylesheet
  - media : 受け入れ可能なメディア
  - nonce
  - integrity
  - hreflang
  - type
  - referrrerpolicy
  - sizes
  - as
  - scope
  - updateviacach
  - workertype
  - color

####### Attributes
######## rel
- rel's supported tokens are the keywords defined in HTML link types.
###### meta
- This element includes the the global attributes.
  itemprop must not be set when one of the name, http-equiv or charset is already used.
- 
  title, base, link, style, script要素を用いて表現できない様々な種類のメタデータを表す。
  name、http-equiv、charset属性のうち1つを正確に指定しなければならない。

####### Def
- 
  - Category : Metadata
  - Contexts :
    - charset属性が存在する場合、またはhttp-equivの属性がエンコード宣言状態にある場合 : head要素内
    - http-equiv属性が存在するが、エンコード宣言状態でない場合 : head要素内、もしくはhead要素配下noscript要素内
    - name属性が存在する場合 : メタデータコンテンツが期待される場所
  - Content attributes :
    - グローバル属性
    - name : メタデータ名
    - http-equiv : プラグマディレクティブ
    - content : 要素の値
    - charset : 文字エンコーディング宣言
  - Tag omission :
    終了タグなし
####### Attributes
######## content
- giving the value associated with the "http-equiv" or "name".
######## name
- document-level metadata.
######### Standard metadata names
########## application-name
########## author
########## description
########## generator
########## keywords
########## referrer
########### content value
- no-referrer
- origin
- no-referrer-when-downgrade
- origin-when-crossorigin
- unsafe-URL
########## theme-color
######### Other metadata names
########## creator
########## googlebot
########## publisher
########## robots
########### content value
- index
- noindex
- follow
- nofollow
- noodp
- noarchive
- nosnippet
- noimageindex
- noydir
- nocache
########## slurp
########## viewport
- you should include the "viewport" element in all your web pages
- 初期サイズに関する助言を与えられる。
########### content value
############ width
############ height
############ initial-scale
############ maximum-scale
############ minimum-scale
############ user-scalable
########### Link
- [[https://drafts.csswg.org/css-device-adapt/#viewport-meta][Viewport <META> element - CSS Device Adaptation Module Level 1]]
- http://qiita.com/ryounagaoka/items/045b2808a5ed43f96607
- http://blog.ousaan.com/index.cgi/links/20130925.html
######## http-equiv
- a pragma directive, i.e. information normally given by the web server about how the web page should be served.
  When the http-equiv attribute is specified, the element is pragma directive.
- プラグマの値は"content"を利用する。
######### content-language / Content-Language
- this pragma sets the pragma-set default lanugage.
######### content-type / Encoding declaration
- The Encoding declaration state is just an alternative form of setting charset attribute
######### default-style / Default style
######### refresh / Refresh
######### set-cookie / Cookie setter
######### x-ua-compatible / X-UA-Compatible
- IEに互換表示をさせない。
  ex) <meta http-equiv="X-UA-Compatible" content="IE=edge">
######### Content-Security-Policy / Conetnt security policy
######## charset
- a charset declaration
######## itemprop
- user-defined metadata
###### style
####### Def
- Category : Metadata
- Contexts :
  - メタデータコンテンツが期待される場所
  - head要素配下のnoscript要素内
- Contents model : type属性の値に依存。
- Content attributes :
  - グローバル属性
  - media : 受け入れ可能なメディア
  - type : 埋め込みリソースタイプ
  - title : 特別なセマンティックを持つ。代替スタイルシート設定名
- Tag omission:
  省略不可

###### title
- 文書のタイトルまたは名前を表す。
- defines the title of the document, and is required in all HTML/XHTML documents.

####### Def
- Category : Metadata
- Contexts : 他のtitle要素を含まないhead要素内。
- Content attributes : Global attributes
- Tag omission : どちらも省略不可

##### Sections
###### body
###### article
- Defines an independent self-contained article
- その部分だけを取り出した場合に独立したコンテンツとして成り立つ際に利用する。
####### Def
- Categories:
  - Flow content
  - Sectioning content
  - Palpable content
- Content attributes:
  - Global attributes
###### section
- Defines a section in a document
####### Def
- Categories:
  - Flow content
  - Sectioning content
  - Palpable content
- Content attributes:
  - Global attributes
###### nav
- Defines a container for navigation links
- ナビゲーションであることを示す際に使用する。
####### Def
- Categories:
  - Flow content
  - Sectioning content
  - Palpable content
- Content attributes:
  - Global attributes
###### aside
- Defines content aside from the content (like a slidebar)
####### Def
- Categories:
  - Flow content
  - Sectioning content
  - Palpable content
- Content attributes:
  - Global attributes
###### h#(1-6)
###### hgroup
###### header
- Defines a header for a document or a section
####### Def
- Categories:
  - Flow content
  - Palpable content
- Content attributes:
  - Global attributes
###### footer
- Defines a footer for a document or a section
####### Def
- Categories:
  - Flow conetnt
  - Palpable content
- Content attributes:
  - Global attributes
###### address
####### Def
- Categories
  - Flow content
  - Palpable content
- Content attributes:
  - Global attributes
##### Grouping content / Text content
- organization blocks or sections of content placed between the openining of <body> and cloning </body> tags.
###### p
###### hr
###### pre
- The HTML <pre> elemest represens preformatted text.
  Text within this element is typically displayed in a non-proportional ("monospace") font exactly as it is laid out in the file.
####### Def
- Categories:
  - Flow content
  - Palpable content
- Content attributes:
  - Global attributes
###### blockquote
- quoted from another source.
###### ol
####### Def
- Categories:
  - Flow content
  - Palpable content (If including li element)
- Content attributes:
  - Global attributes
  - reversed : Number the list backwards
  - start : Starting value of the list
  - type : Kind of list marker
####### "type" keyword
- 1 : decimal
- a : lower-alpha
- A : upper-alpha
- i : lower-roman
- I : upper-roman
###### ul
####### Def
- Categories
  - Flow content
  - Palpable content (If including li)
- Content attributes
  - Global attributes
###### menu
###### li
####### Def
- Categories:
  - None
- Content attributes:
  - Global attributes
  - value : Ordinal value of the list item
    (If not a child of an "ul" or "menu" element)
###### dl
- description list
####### Def
- Categories:
  - Flow content
  - Palpable conetnt (if including name-value group)
- Content attributes:
  - Global attributes
###### dt
- defines the "term"(name)
####### Def
- Categories:
  - None
- Content attributes:
  - Global attributes
###### dd
- describes each term
####### Def
- Categories:
  - None
- Content attributes:
  - Global attributes
###### figure
###### figcaption
###### main
###### div
- having no special meaning at all. 
  It can be used with the class, lang, and title attributes 
  to mark up semantics common to a group of consecutive elements.
####### Def
- Categories:
  - Flow content
  - Palpable content
- Content attributes:
  - Global attributes
##### Text-level semantics / Inline text smantics
###### a
####### Def
- Categories:
  - Flow content
  - Phrasing content
  - Interactive content (If the element has an "href" attribute)
  - Palpable content
- Content attributes:
  - Global attributes
  - href : Address of the hyperlink
  - target : Browsing context for hyperlink navigation
  - download : Whether to download the resource instead of navigating to it, and its file name if so
  - ping : URLs to ping
  - rel : Relationship between the location in the document containing the hyperlink and the destination resource
  - hreflang
  - type
  - referrerpolicy
###### abbr
- defines abbreviation or acronym
- ex
  - <abbr title="World Health Organization">WHO</abbr>
####### Def
- Categories
  - Flow content
  - Phrasing content
  - Palpable content
- Content attributes
  - Global attributes
  - title : special semantics on this element: Full term or expansion of abbreviation.
###### adat
###### b
- bold
###### bdi
- bi-directional override.
  this element is used to override the current text direction.
  normally word flows right to left.
###### bdo
###### br
###### cite
- defines the title of work.
  usually display in italic.
####### Def
- Categories:
  - Flow content
  - Phrasing content
  - Palpable content
- Content model:
  - Phrasing content
- Content attribuets:
  - Global attributes
###### code
- represents a fragment of computer code.
####### Def
- Categories:
  - Flow content
  - Phrasing content
  - Palpable content
- Content attributes:
  - Global attributes
###### dfn
###### em
- emphasize
###### i
- italic
###### kbd
- represents user input (typically keiboard input)
####### Def
- Categories:
  - Flow content
  - Phrasing content
  - Palpable content
- Content attributes:
  - Global attributes
###### mark
- marked, or highlighted
###### q
- sohrt quotation.
###### rb
###### rp
###### rt
###### rtc
###### ruby
###### s
###### samp
- The samp element represents sample or quoted output
  from another program or computing system.
####### Def
- Categories:
  - Flow content
  - Phrasing content
  - Palpable content
- Content attributes:
  - Global attributes
###### small
###### span
- not mean anything on its own, but can be useful when used together with the global attributes.
####### Def
- Categories:
  - Flow content
  - Phrasing content
  - Palpable content
- Content attributes:
  - Global attributes
###### strong
- strong text
###### sub, sup
- 下付き、上付き
###### time
###### u
###### var
- represents a variable
  The variable could be a variable in a mathematical expression or a variable in programming context
####### Def
- Categories:
  - Flow content
  - Phrasing content
  - Palpable content
- Content attributes:
  - Global attributes
###### wbr
##### Edits / Demarcating edits
###### ins
- inserted text.
- 下線がつく場合が多いか
###### del
- deleted text
- 打消し線がつく場合が多いか
##### Embedded content / Image and multimedia
###### picture
###### source
###### img
####### Def
- Categories:
  - Flow content
  - Phrasing content
  - Embedded content
  - Form-associated element
- Contexits in which this element can be used: Where embedded content is expected
- Content model:
  Nothing
- Tag omission in text/html:
  No end tag.
- Content attributes:
  - Global attributes
  - alt : Replacement text for use when images are not available
  - src : Address of the resource
  - srcset
  - sizes : Image sizes for different page layouts
  - crossorigin
  - usemap
  - ismap
  - width : Horizon dimension
  - height : Vertical dimension
  - referrerpolicy
####### Memo
######## Use "style" attribute, not "width" and "height"
- suggesting to use style="width: 120px; height: 120px;"
  rather than "width=120 height=120".
  latter can prevents internal or external styles sheets from changing the original size of images.
###### iframe
- The ifram element represents a nested browsing content.
- ネストされたブラウジングコンテキストを表す。
####### Def
- Category :
  - Flow
  - Phrasing
  - Embedded
  - Interactive
  - Pulpable
- Contexts : Embeddedが期待される場所
- Contents model :
  文で与えられる要件に適合しているテキスト
- Content attributes :
  - Global attributes
  - src : リソースのアドレス
  - srcdoc : iframe内で描画する文書
  - name : ネストされたブラウジングコンテキスト名
  - sandbox : ネストされたコンテンツのセキュリティールール
  - allawfullscreen
  - allawpaymentrequest
  - allawusermedia
  - width : 横
  - height : 縦
  - referrerpolicy
- Tag omission
  省略不可
####### Memo
######## aのtargetとして使用
- aのtargetとしてiframeを設定できる。
- 例
  <iframe src="demo_iframe.htm" name="iframe_a"></iframe>
  <p><a href="https://www.w3schools.com" target="iframe_a">W3Schools.com</a></p>
###### embed
###### object
###### param

###### video
###### audio
###### track

###### map
- Defining an image-map.
  An image-map is an image with clickable areas.
  tha name of the <map> tag is associated with the <img>'s usemap attribute
  and creates a relationship between the image and the map.
####### Def
- Categories:
  - Flow content
  - Pharasing content
  - Palpable content
- Content attributes
  - Global attributes
  - name : Name of image map to refernce from the use map attribute

###### area
- Defiens a clickable area inside an image-map
####### Def
- Categories
  - Flow content
  - Phrasing content
- Content attributes
  - Global attributes
  - alt : Replacement text for use when images are not available
  - coords
  - shape
  - href
  - target
  - download
  - ping
  - rel
  - refererpolicy

##### Links
###### Link types
####### alternate
####### author
####### bookmark
####### canonical
####### dns-prefetch
####### external
####### help
####### icon
####### license
####### nofollow
####### noopener
####### noreferrer
####### pingback
####### preconnect
####### prefetch
####### preload
####### search
####### serviceworker
####### stylesheet
####### tag
####### sequential type
######## next
######## prev
##### Tabular data / Table contents
###### table
####### Def
- Categories:
  - Flow content
  - Palpable content
- Content attributes:
  - Global attributes
###### caption
####### Def
- Categories
  - None
- Content attributes
  - Global attributes
###### colgroup
###### col
###### tdoby
###### thead
###### tfoot
###### tr
###### td
####### Def
- Categories
  - Sectioning root
- Content attributes
  - Global attribuets
  - colspan : Number of columns that tha cell is to span
  - rowspan : Number of rows that the cell is to span
  - headers : The header cells for this cell
###### th
####### Def
- Categories
  - None
- Content attributes
  - Global attributes
  - colspan
  - rowspan
  - headers
  - scope
  - abbr
##### Forms
###### form
- defines a form that is used to collect user input.
- 処理のためにサーバーに送信できる編集可能な値を表すことができる一部。
####### Def
- Category:
  - Flow
  - Palpable
- Contents model : フローコンテンツ、ただしform要素の子孫を除く。
- Content attributes :
  - グローバル属性
  - accept-charset : フォーム送信に使用する文字エンコーディング
  - action : フォーム送信に使用するURL
  - autocomplete : フォーム内のコントロールのオートフィル機能に対するデフォルト設定
  - encrypt : フォーム送信に使用する文字円コーディングを設定するフォームデータ
  - method : フォーム送信に使用するHTTPメソッド(GET, POSTなど)
  - name : Name of form to use in the document.forms API
  - novalidate
  - target : フォーム送信に対するブラウジングコンテキスト
- Tag omission : 省略不可

###### label
- represents a caption in a user interface.
- フォーム属性とラベルを関連付けることができる
####### Def
- Categories:
  - Flow content
  - Phrasing content
  - Interactive conetnt
  - Palpable conetnt
- Content attriutes:
  - Global attributes
  - for : Associate the label with form control
###### input
- most important form element.
  can be displayed in several ways, depending on "type" attribute.

- The input element represents a typed data field, usually with a form control to allow the user to edit the data.
  The "type" attribute controls the data type (and associated control) of the element.
  each element must have a "name" field.
####### Def
- Category : 
  - フローコンテンツ
  - フレージングコンテンツ
  - type属性がHiddenでない場合 : 
    - インタラクティブコンテンツ
    - 記載、ラベル付可能、送信可能、
  - type属性がHiddenである場合 :
- Content attributes :
  - グローバル属性 :
  - accept
  - alt
  - autocomplete
  - autofocus
  - checked
  - dirname
  - disabled : フォームコントロールが無効であるかどうか
  - form : form要素とコントロールを関連付ける
  - formaction
  - formenctype
  - formmethod
  - formtarget
  - height
  - inputmode
  - list
  - max
  - maxlength
  - min
  - minlength
  - multiple
  - name : フォーム送信およびform.elements APIで使用するフォームコントロール名
  - pattern
  - placeholder
  - readonly
  - required
  - size : コントロールのサイズ
  - src
  - step
  - type : フォームコントロールの種類
  - value : フォームコントロールの値
  - width
  - title: having special semantics
- Tag omission :
  - 終了タグなし

####### Attributes
######## Type
######### Hidden
- type=hidden
- An orbitrary string
######### Text
- type=text
- Text with no line breaks,
  text control type
######### Search
- type=search
- Text with no line breaks,
  search control type
######### Telephone
- type=tel
######### URL
- type=url
######### E-mail
- type=email
######### Password
- type=password
######### Date
- type=date
######### Time
- type=time
######### Number
- type=number
######### Range
- type=range
######### Color
- type=color
######### Checkbox
- type=checkbox
######### Radio Button
- type=radio
######### File Upload
- type=file
######### Submit Button
- type=submit
######### Image Button
- type=image
######### Reset Button
- type=reset
######### Button
- type=button
######## Common
######### autocomplete
########## Values
########### off
########### on
########### name
########### honorific-prefix
########### given-name
########### additional-name
########### family-name
######### maxlength
######### minlength
######### size
######### readonly
######### required
######### multiple
######### pattern
######### min
######### max
######### step
######### list
######### placeholder
###### button
####### Def
- Categories:
  - Flow content
  - Phrasing content
  - Interactive conetnt
  - Listed, labelable, and sumbittable form-associated element
  - Palpable content
- Content attributes:
  - Global attributes
  - autofocus
  - disabled
  - form
  - formaction
  - formenctype
  - formmethod
  - formnovalidate
  - formtarget
  - name
  - type
  - value : Value to be used for form submission
###### select
- represents a control for selecting amongst a set of options.
- defines a drop-down list
####### Def
- Categories:
  - Flow content
  - Phrasing content
  - Interactive centent
  - Listed, labelable, submittable, and resettable form-associated elemnt
  - Palpable content
- Content attributes:
  - Global attributes
  - autocomplete
  - autofocus
  - disabled
  - form
  - multiple
  - name
  - required
  - size
###### datalist
- The datalist element represents a set of option elements that represent predefined options for other controls.
  new in HTML5
- selectのようなdropdownリストを、別箇所で定義して適用できる。元アイテムのlist属性とdatalistのid属性を揃える。
####### Def
- Categories:
  - Flow content
  - Phrasing content
- Content attributes:
  - Global attributes
###### optgroup
- The optgroup element represents a group of option elements with a common label.
####### Def
- Categories:
  - None
- Contexts in which this element can be used:
  - As a child of a select element.
- Content attributes:
  - Global attributes
  - disabled
  - label: User-visible label
###### option
- The option element represents an option in a select element or as part of a list of suggestions in a datalist element.
####### Def
- Categories:
  - None
- Contexts in which this element can be used:
  - As a child of a select element.
  - As a child of a datalist element.
  - As a child of a optgroup element.
- Content attributes:
  - Global attributes
  - disabled
  - label: User-visible label
  - selected: Whether the option is selected by default
  - value: Value to be used for form submission
###### textarea
- srepresents a multiline plain text edit control for the element's raw value.
####### Def
- Category :
  - Flow
  - Phrasing
  - Interactive
  - 記載、ラベル付可能、送信可能、リセット可能、および再関連付け可能フォーム関連要素
  - Palpable
- Contexts : フレージングコンテンツが期待される場所
- Contents model : Text
- Tag omissions : 省略不可
- Content attributes :
  - グローバル属性
  - autocomplete
  - autofocus
  - cols : 行あたりの最大文字数
  - dirname
  - disabled
  - form
  - inputmode
  - maxlength
  - minlength
  - name : フォーム送信およびform.elements APIで使用するフォームコントロール名
  - placeholder
  - readonly
  - required
  - rows : 表示する行数
  - wrap
###### output
- represents the result of a calculation (like one performed by a script).
  new in HTML5
- 何らかの計算やユーザによるアクションの結果を表す
####### Def
- Categories:
  - Flow content
  - Phrasing conetnt
  - Listed, labelable, and resettable form-associated element
  - Palpable conetnt
- Content attributes:
  - Global attributes
  - for : 
    Specifies controls from which the output was calculated
    計算の入力値を与える（或いは計算値に影響を与えている）他の要素のidのリスト
  - form
  - name
###### progress
###### meter
###### fieldset
- a set of form controls optionally grouped under a common name.
####### Def
- Categories:
  - Flow content
  - Sectioning root
  - Listed form-associated element
  - Palpable content
- Content attributes:
  - Global attributes
  - disabled
  - form
  - name
###### legend
- a caption for the rest of the contens of the legent element's parent fieldset element, if any.
####### Def
- Categories:
  - None
- Content attributes:
  - Global attributes
###### Obsolete
####### keygen
- providing a secure way to authenticate users.
  new in HTML5, deleted.
- 暗号鍵を生成する。
  フォーム送信時にキーを発行して暗号化する際に使用する。
##### Scripting
###### script
- The script element allows authors to include dynamic script and data blocks in their documents.
####### Def
- Category :
  - Metadata
  - Flow
  - Phrasing
  - Script support
- Contexts :
  - メタデータが期待される場所
  - フレージングコンテンツが期待される場所
  - スクリプトサポート要素が期待される場所
- Contents model :
  - src属性が存在しない場合、type属性の値に依存するが、スクリプトの内容制限に一致しなければならない。
  - src属性が存在する場合、要素は空またはスクリプト文書を含むだけでなくスクリプトの内容制限に一致するかのいずれかでなければならない。
- Content attributes :
  - グローバル属性
  - src : リソースのアドレス
  - type : 埋め込みリソースタイプ
  - charset : 外部スクリプトリソースの文字エンコーディング
    デファルトはtext/javascript。
  - async : 非同期的にスクリプトを実行する
  - defer : スクリプトの実行を延期する
  - crossorigin : 要素がcrossorigin要求を処理する方法

####### Attributes
###### noscript
- used to provide an alternate content for users that disabled scripts in their browser
####### Def
- Categories:
  - Metadata content
  - Flow content
  - Phrasing content
- Content attributes:
  - Global attributes
###### template
###### slot
###### canvas
##### Interactive elements
###### details
- Defines a additional details
####### Def
- 
  - Cagegories
    - Flow content
    - Sectioning root
    - Interactive content
    - Palpable content
###### summary
- Defines a heading for the <details> element
####### Def
- 
  - Categories
    - None
  - Contexts
    - As the first child of a details element.
###### Commands
####### Facets
####### a element
####### button element
####### input element
####### option element
####### accesskey attirubet on legent element
###### dialog
##### Web Components
###### shadow
###### slot
###### template
#### Microdata
#### User interaction
#### Loading Web pages
##### Browsing contexts
###### Browsing context names
####### Keyword
######## _blank
- Opens the linked document in a new window or tab
######## _self
- Opens the linked document in the same window/tab as it wal clikecd
######## _parent
- Opens the linked document in the parent frame
######## _top
- Opens the linked document in the full bofy of the window
#### Web application APIs
##### Scripting
##### The WindowOrWorkerGlobalScope mixin
#### Communication
#### Web workers
#### Web storage
#### HTML syntax
##### Writing HTML documents
###### the DOCTYPE
###### Elements
###### Text
###### Character references
###### CDATA sections
###### Comments
- Comments must have the following format:
  1. The string "<!--".
  2. Optionall, text.
     text must not 
     - start with the ">"
     - start with the string "->"
     - contain the strings "<!--", "-->", or "--!>
     - end with the string "<!-"       
  3. The string "-->"
##### Parsing HTML documents
##### Serializing HTML fragments
##### Parsing HTML fragments
##### Named character references
#### XML syntax
#### Rendering
#### IANA considerations
## WAI-ARIA
- 
### Link
- [[https://www.w3.org/TR/wai-aria/][Accessible Rich Internet Applications (WAI-ARIA) 1.0 - W3C]]
- [[https://rawgit.com/w3c/aria-in-html/master/index.html][Using WAI-ARIA in HTML]]
- [[https://www.w3.org/TR/html-aria/][ARIA in HTML - W3C]]
- [[https://momdo.github.io/html-aria/][ARIA in HTML 日本語訳]]
- [[http://website-usability.info/2014/04/entry_140415.html][WAI-ARIAの基礎知識 - Website Usability Info]]
## Glossary
### WHATWG
- Web Hypertext Application Technology Working Group
  HTMLの開発やその関連技術に興味を持つ人々のコミュニティー。
  Apple, Mozilla, Operaによって設立された。
## Memo
### Suggests
- Use lower case

- Attribute values should always be enclosed in quotes.
  class, id, style, title

### Box Model
#### padding
- 
  Inside area

#### border
- 
  Line

#### margin
- 
  Outside area

### manifest
- 
  アプリケーションキャッシュを有効にするには、ドキュメントのhtmlタグにmanifest属性を含める。
  manifest属性はキャッシュ対象にするすべてのウェブアプリケーションのページに含める必要がある。
  
- 
  [[http://www.html5rocks.com/ja/tutorials/appcache/beginner/][アプリケーション キャッシュ を初めて使う - html5rocks]]

### 言語タグ、BCP 47
- 
  言語タグの構文はIETFの"BCP 47"で定義されている。
  BCPは"Best Current Practice"の略。更新時に番号が変化するRFCに対して永続的な名前を与える。
  最新のRFCはRFC5646。
  
- 
  [[https://www.w3.org/International/questions/qa-choosing-language-tags][Choosing a Language Tag - W3C]]
  [[http://www.rfc-editor.org/rfc/rfc5646.txt][Request for Comments : 5646]]
  [[https://www.w3.org/International/articles/language-tags/index.ja][HTMLとXMLにおける言語タグ - W3C]]

### Path
- to use relative file path (if possible),
  because of not being bound to your current base URL.

### Character Entities
#### Entities
#####   &nbsp; &#160;
- non-breaking space 
##### < &lt; &#60;
- less than 
##### > &gt; &#62;
- greater than
##### & &amp; &#amp;
- ampersand
##### " &quot; &#34;
##### ' &apos; &#39;
##### ￠ &cent; &#162;
#### Link
- https://www.w3.org/TR/html4/sgml/entities.html
- https://www.w3schools.com/html/html_entities.asp
- https://www.w3schools.com/html/html_symbols.asp
- http://w-d-l.net/html__entities/

## Link
- [[https://html.spec.whatwg.org/multipage/][HTML Living Standard]]
- [[https://www.w3.org/TR/html5/][HTML5 - W3C]]
- [[https://momdo.github.io/html5/Overview.html][HTML5日本語訳 - W3C]]
- [[https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/HTML5][HTML5 - MDN]]
- [[https://developer.mozilla.org/ja/docs/Web/HTML/HTML5][HTML5(日本語訳) - MDN]]

- [[https://developer.mozilla.org/en-US/docs/Web/HTML][HTML - Web technology for developers - MDN]]

- [[http://www.htmq.com/html5/index.shtml][HTML5リファレンス - HTMLクイックリファレンス]]

- [[http://jtdan.com/spec/][W3C仕様書などのまとめ【保存版】 - W3C]]
- [[http://alistapart.com/article/readspec][How to Read W3C Specs - A LIST APART]]
