# Document Object Model, DOM
- W3Cから勧告されているHTML文書やXML文書をアプリケーションから利用するためのAPI。
  データをツリー構造として扱えるが、通常の場合対象文書を全て読み込んでからの扱いを前提とするため、
  動作速度が遅かったり、メモリー使用量が大きくなる、などの欠点がある。
  W3CではAPI仕様を定義しているのみ。
## Specification
### W3C
#### Document Object Model (DOM) Level 1
- https://www.w3.org/TR/REC-DOM-Level-1/
##### Document Object Model (Core) Level 1
###### Overview of the DOM Core Interfaces
####### The DOM Structure Model
######## Node Type and Hierarchy
######### Document
- Element, ProcessingInstruction, Comment, DocumentType
######### DocumentFragment
- Element, ProcessingInstruction, Comment, Text
######### DocumentType
- no children
######### EntityReference
- Element, ProcessingInstruction, Comment, Text, CDATASection, EntityReference
######### Element
- Element, ProcessingInstruction, CDATASection, EntityReference
######### Attr
- Text, EntityReference
######### ProcessingInstruction
- no children
######### Comment
- no children
######### Text
- no children
######### CDATASection
- no children
######### Entity
- Element, ProcessingInstruction, Comment, Text, CDATASection, EntityReference
######### Notation
- no children
######## Memory Management
######## Naming Conventions
######## Inheritance vs Flattened View of the API
######## The DOMString type
######## Case sensitivity in the DOM
####### Fundamental Interfaces
######## Exceptions
######### DOMException
######## Interfaces
######### DOMImplementation
######### DocumentFragment
######### Document
######### Node
######### NodeList
######### NamedNodeMap
######### CharacterData
######### Attr
######### Element
######### Text
######### Comment
####### Extended Interfaces
######## Interfaces
######### CDATASection
######### DocumentType
######### Notation
######### Entity
######### EntityReference
######### ProcessingInstruction
##### Document Object Model (HTML) Level 1
###### Introduction
###### HTML Application of Core DOM
####### Naming Conventions
###### Miscellaneaus Object Definitions
####### Interfaces
######## HTMLCollection
###### Objects related to HTML documents
####### Interfaces
######## HTMLDocument
###### HTML Elements
####### Propety Attributes
####### Naming Exceptions
####### Exposing Element Tye Names
####### The HTML Element interface
######## Interfaces
######### HTMLElement
########## Attributes
########### className
########### dir
########### id
########### lang
########### title
########## Note
########### style
- The style attribute of an HTML element is accessible throuph the "ElementCSSInlineStyle" interface
  which is defined in the CSS module.
####### Object definitions
######## Interfaces
######### HTMLHtmlElement
######### HTMLHeadElement
######### HTMLLinkElement
######### HTMLTitleElement
######### HTMLMetaElement
######### HTMLBaseElement
######### HTMLIsIndexElement
######### HTMLStyleElement
######### HTMLBodyElement
######### HTMLFormElement
######### HTMLSelectElement
######### HTMLOptGroupElement
######### HTMLOptionElement
######### HTMLInputElement
######### HTMLTextAreaElement
######### HTMLButtonElement
######### HTMLLabelElement
######### HTMLFieldSetElement
######### HTMLLegendElement
######### HTMLUListElement
######### HTMLOListElement
######### HTMLDListElement
######### HTMLDirectoryElement
######### HTMLMenuElement
######### HTMLLIElement
######### HTMLBlockquoteElement
######### HTMLDivElement
######### HTMLParagraphElement
######### HTMLHeadingElement
######### HTMLQuoteElement
######### HTMLPreElement
######### HTMLBRElement
######### HTMLBaseFontElement
######### HTMLFontElement
######### HTMLHRElement
######### HTMLModElement
######### HTMLAnchorElement
######### HTMLImageElement
########## Attributes
########### align
########### alt
########### border
########### height
########### hspace
########### isMap
########### longDesc
########### name
########### src
########### useMap
########### vspace
########### width
######### HTMLObjectElement
######### HTMLParamElement
######### HTMLAppletElement
######### HTMLMapElement
######### HTMLAreaElement
######### HTMLScriptElement
######### HTMLTableElement
######### HTMLTableCaptionElement
######### HTMLTableColElement
######### HTMLTableSectionElement
######### HTMLTableRowElement
######### HTMLTableCellElement
######### HTMLFrameSetElement
######### HTMLFrameElement
######### HTMLIFrameElement
#### Document Object Model (DOM) Level 2
##### Document Object Model (DOM) Level 2 Core Specification
- https://www.w3.org/TR/DOM-Level-2-Core/
- XML 1.0を扱う基本メソッドと、名前空間に関する拡張
###### Document Object Model Core
####### Overview of the DOM Core Interfaces
######## The DOM Structure Model
######## Memory Management
######## Naming Conventions
######## Inheritance vs. Flattened Views of the API
######## The DOMString type
######### Type Definition
########## DOMString
########## DOMTimeStamp
######## The DOMTimeStamp type
######## String comparisons in the DOM
######## XML Namespaces
####### Fundamental Interfaces
######## Exceptions
######### DOMException
######## Interfaces
######### DOMImplementation
######### DocumentFragment
######### Document
######### Node
######### NodeList
######### NamedNodeMap
######### CharacterData
######### Attr
######### Element
######### Text
######### Comment
####### Extended Interfaces
######## Interfaces
######### CDATASection
######### DocumentType
######### Notation
######### Entity
######### EntityReference
######### ProcessingInstruction
###### Appendx A: Changes
##### Document Object Model (DOM) Level 2 HTML Specification
- https://www.w3.org/TR/DOM-Level-2-HTML/
- HTML 4.0xに関する拡張と、XHTML 1.0のサポート
###### Document Object Model HTML
####### Introduction
####### HTML Application of Core DOM
####### XHTML and the HTML DOM
####### Miscellaneaus Object Definitions
######## Interfaces
######### HTMLCollection
######### HTMLOptionsCollection
- introduced in DOM Level2
####### Object related to HTML documents
######## Interfaces
######### HTMLDocument
####### HTML Elements
######## Property Attributes
######## Naming Exceptions
######## Exposing Element Type Names
######## The HTML Element interfaces
######### Interfaces
########## HTMLElement
######## Object definitions
######### Interfaces
########## HTMLHtmlElement
########## HTMLHeadElement
########## HTMLLinkElement
########## HTMLTitleElement
########## HTMLMetaElement
########## HTMLBaseElement
########## HTMLIsIndexElement
########## HTMLStyleElement
########## HTMLBodyElement
########## HTMLFormElement
########## HTMLSelectElement
########## HTMLOptGroupElement
########## HTMLOptionElement
########## HTMLInputElement
########## HTMLTextAreaElement
########## HTMLButtonElement
########## HTMLLabelElement
########## HTMLFieldSetElement
########## HTMLLegendElement
########## HTMLUListElement
########## HTMLOListElement
########## HTMLDListElement
########## HTMLDirectoryElement
########## HTMLMenuElement
########## HTMLLIElement
########## HTMLDivElement
########## HTMLParagraphElement
########## HTMLHeadingElement
########## HTMLQuoteElement
########## HTMLPreElement
########## HTMLBRElement
########## HTMLBaseFontElement
########## HTMLFontElement
########## HTMLHRElement
########## HTMLModElement
########## HTMLAnchorElement
########## HTMLImageElement
########## HTMLObjectElement
########## HTMLParamElement
########## HTMLAppletElement
########## HTMLMapElement
########## HTMLAreaElement
########## HTMLScriptElement
########## HTMLTableElement
########## HTMLTableCaptionElement
########## HTMLTableColElement
########## HTMLTableSectionElement
########## HTMLTableRowElement
########## HTMLTableCellElement
########## HTMLFrameSetElement
########## HTMLFrameElement
########## HTMLIFrameElement
##### Document Object Model (DOM) Level 2 Views Specification
##### Document Object Model (DOM) Level 2 Style Specification
- https://www.w3.org/TR/DOM-Level-2-Style/
- スタイルシート(CSS及びCSS Level2)に関する拡張
###### Document Object Model Style Sheets
####### Style Sheet Interfaces
######## Interfaces
######### StyleSheet
######### StyleSheetList
######### MediaList
####### Document Extensions
######## Interfaces
######### LinkStyle
######### DocumentStyle
####### Association between a style sheet and a document
###### Document Object Model CSS
####### CSS Fundamental Interfaces
######## Interfaces
######### CSSStyleSheet
######### CSSRuleList
######### CSSRule
######### CSSStyleRule
######### CSSMediaRule
######### CSSFontFaceRule
######### CSSPageRule
######### CSSImportRule
######### CSSCharasetRule
######### CSSUnknownRule
######### CSSStyleDeclaration
########## Attributes
########### cssText
########### length
########### parantRule
########## Methods
########### getPropertyCSSValue
########### getPropertyPriority
########### getPropertyValue
########### item
########### removeProperty
########### setProperty
######### CSSValue
######### CSSPrimitiveValue
######### CSSValueList
######### RGBColor
######### Rect
######### Counter
####### Override and computed style sheet
######## Interfaces
######### ViewCSS
######### DocumentCSS
####### Style sheet creation
######## Interfaces
######### DOMImplementationCSS
####### Element with CSS inline style
######## Interfaces
######### ElementCSSInlineStyle
- This represents the contens of the STYLE attribute for HTML elements.
########## Attributes
########### style
- type of CSSStyleDeclaration, readonly
######### Extended Interface
########## Interfaces
########### CSS2Properties
- The CSS2Properties interface represents a convenience mechanism 
  for retrieving and setting properties within a "CSSStyleDeclaration".
############ Attributes
############# azimuth
############# background
############# backgroundAttachment
############# backgroundColor
############# border
############# color
############# fontSize
- type DOMString
##### Document Object Model (DOM) Level 2 Events Specification
##### Document Object Model (DOM) Level 2 Traversal Specification
#### Document Object Model (DOM) Level 3
##### Document Object Model (DOM) Level 3 Core Specification
- https://www.w3.org/TR/DOM-Level-3-Core/
###### Document Object Model Core
### WHATWG
#### DOM Living Standard
- https://dom.spec.whatwg.org/
- DOM defines a platform-neutral model for events, aborting activities, and node trees.
##### Goals
##### Infrastructure
##### Events
###### Interface 'Event'
###### Interface 'CustomEvent'
###### Interface 'EventTarget'
##### Abrting ongoing activities
###### Interface AbortController
###### Interface AbortSignal
##### Nodes
###### Introduction to "The DOM"
###### Node tree
####### Document tree
####### Shadow tree
####### Mutation algorithms
####### Mixin 'NonElementParentNode'
######## Methods
######### getElementByID
- returns the first element, in tree order, whose ID is elementId, and null if there is no such element otherwise.
####### Mixin 'DocumentOrShadowRoot'
####### Mixin 'ParentNode'
####### Mixin 'NonDocumentTypeChildNode'
####### Mixin 'ChildNode'
####### Mixin 'Slotable'
####### Old-style collections: NodeList and HTMLCollection
######## Interface 'NodeList'
######## Interface 'HTMLCollection'
###### Mutation observers
####### Interface 'MutationObserver'
####### Interface 'MutationRecord'
###### Interface 'Node'
####### Attributes
######## textContent
- attribute DOMString? textContent
####### Methods
###### Interface 'Document'
####### Interface 'DOMImplementation'
###### Interface 'DocumentType'
###### Interface 'DocumentFragment'
###### Interface 'ShadowRoot'
###### Interface 'Element'
####### Attributes
######## namespaceURI
######## prefix
######## localName
######## tagName
######## id
######## className
######## classList
######## slot
######## attributes
####### Methods
######## hasAttribute()
######## getAttributeNames()
######## getAttribute(qualifiedName)
######## getAttributeNS(namespace, localName)
######## setAttribute(qualifiedName, value)
######## setAttributeNS(namespace, qualifiedName, value)
######## removeAttribute()
######## removeAttributeNS
######## getAttributeNode
######## getAttributeNodeNS
######## setAttributeNode
######## setAttributeNodeNS
######## romevoAttributeNodeNS
####### Interface 'NamedNodeMap'
####### Interface 'Attr'
###### Interface 'CharacterData'
###### Interface 'Text'
###### Interface 'CDATASection'
###### Interface 'ProcessingInstruction'
###### Interface 'Comment'
##### Ranges
###### Introduction to "DOM Ranges"
###### Interface 'Range'
##### Traversal
###### Interface 'NodeIterator'
###### Interface 'TreeWalker'
###### Interface 'NodeFilter'
##### Sets
###### Interface 'DOMTokenList'
##### Historical
###### DOM Events
###### DOM Core
###### DOM Range
###### DOM Traversal
### MDN
#### Web API Interfaces
- https://developer.mozilla.org/ja/docs/Web/API
##### DOM References
- https://developer.mozilla.org/ja/docs/DOM/DOM_Reference
###### DOM Interface
####### Attr
####### CharacterData
####### Comment
####### CustomEvent
####### Document
####### DocumentFragment
####### DOMError
####### DOMException
####### DOMString
####### DOMTimeStamp
####### DOMStringList
####### Element
####### Event
####### EventTarget
####### HTMLCollection
####### MutationObserver
####### MutationRecord
####### Node
####### NodeIterator
####### NodeList
####### ParentNode
####### Range
####### Text
####### URL
####### Window
######## Properties
######## Methods
######### setInterval()
- https://developer.mozilla.org/ja/docs/Web/API/Window/setInterval
- WindowOrWorkerGlobalScope.setInterval()
- 一定の遅延間隔を置いて関数やコードスニペットを繰り返し呼び出す。
########## Syntax
########### Arguments
########### Return value
######## Events
####### Worker
###### HTML Interface
####### HTML element IFs
####### Other HTML IFs
###### SVG Interfaces
####### SVG element IFs
####### SVG Data type IFs
######## Static
######## Animation
####### SMIL
####### Other SVG IFs
## DOM Level
- Levelが上がるほど高機能となる
### DOM Level 1
#### About
- 1998/10/1にW3Cから勧告されている。
- 
  |--------------------------------+------+--------------------------------------------|
  | 仕様                           | 規格 | 説明                                       |
  |--------------------------------+------+--------------------------------------------|
  | DOM Level 1 Core Specification | Core | DOMの基本機能及びXML文書用の機能を定義する |
  |                                | HTML | HTML文書用の機能を定義する                 |
  |--------------------------------+------+--------------------------------------------|
  
### DOM Level 2
#### About
- 2000/11/13にW3Cから勧告。
  6つの仕様書、14モジュールが定義されている。
- 特徴 : 名前空間に対応、複数文書館操作に対応、モジュールの追加による大幅な機能強化、妥当性検証は行わない。
- 
  |---------------------------------------------------+----------------+--------------------------------------|
  | 仕様                                              | モジュール     | 説明                                 |
  |---------------------------------------------------+----------------+--------------------------------------|
  | DOM Level 2 Core Specification 1.0                | Core           | DOMの基本機能を定義する              |
  |                                                   | XML            | XML1.0を扱う基本的メソッドを定義する |
  | DOM Level 2 Views Specification 1.0               | Views          | 文書のレンダリング制御機能を定義する |
  | DOM Level 2 Style Specification 1.0               | StyleSheets    |                                      |
  |                                                   | CSS            |                                      |
  |                                                   | CSS2           |                                      |
  | DOM Level 2 Events Specification 1.0              | Events         |                                      |
  |                                                   | UIEvents       |                                      |
  |                                                   | MouseEvents    |                                      |
  |                                                   | MutationEvents |                                      |
  |                                                   | HTMLEvents     |                                      |
  | DOM Level 2 Traversal and Range Specification 1.0 | Range          |                                      |
  |                                                   | Traversal      |                                      |
  | DOM Level 2 HTML Specification 1.0                | HTML           | HTML 4.0に関する拡張、XHTML1.0のサポート |
  |---------------------------------------------------+----------------+--------------------------------------|

### DOM Level 3
#### About
- 読み込みと書き込みに対応し、XML Information Setとの連携も強化された。
- 
  |-----------------------------------------+---------------------------------------------------|
  | 仕様                                    | 説明                                              |
  |-----------------------------------------+---------------------------------------------------|
  | DOM Level 3 Core Specification          | XML 1.0を扱う基本的メソッド、名前空間に関する拡張 |
  | DOM Level 3 Load and Save Specification | DOMツリーの読み書き                               |
  | DOM Level 3 Validation Specification    | DOMツリーに含まれるスキーマ定義の編集             |
  |-----------------------------------------+---------------------------------------------------|

### DOM Level 4
## Memo
### DOM Event
#### Link
- [[https://developer.mozilla.org/ja/docs/Web/API/Event][event - MDN]]
- [[https://www.w3.org/TR/2000/REC-DOM-Level-2-Events-20001113/Overview.html#contents][Document Object Model (DOM) Level 2 Events Specification - W3C]]
- [[https://en.wikipedia.org/wiki/DOM_events][DOM events - Wikipedia]]
## Link
- [[https://dom.spec.whatwg.org][DOM - Living Standard]]
- [[DOM Standard ("DOM4") 日本語訳]]

- [[https://www.w3.org/TR/dom/][W3C DOM4 - W3C]]

- [[http://www.doraneko.org/misc/dom10/19981001/introduction.html][DOMとは何か - 文書オブジェクトモデル(DOM)第1水準 仕様書]]
