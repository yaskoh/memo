# XML
## XML
### Specification
#### XML 1.0
##### Link
- [[https://www.w3.org/TR/xml/][Extensible Markup Language (XML) 1.0 (Fifth Edition) - W3C]]
#### XML 1.1
##### Link
- [[https://www.w3.org/TR/xml11/][Extensible Markup Language (XML) 1.1 (Second Edition) - W3C]]
### XML Memo
#### XML Declaration / XML宣言
- XML宣言を必ず先頭に書かないといけない。宣言以前にはコメントも書いてはいけない。
- 例
  <? xml version="1.0" encoding="UTF-8" standalone="yes|no" ?>
##### Attributes 項目
###### version バージョン属性
- 必須。1.0もしくは1.1。
###### encoding エンコーディング属性
- 省略可。省略した場合はUTF-8かUTF-16と見なされる。
- 方式
  - UTF-8
  - UTF-16
  - Shift_JIS
  - EUC
###### standalone スタンドアロン属性
- 省略可。省略した場合、"no"と同じ動きとなる。
#### Comment / コメント
- "<!--"から"-->"までの間の文章がコメントとなる。
  XML宣言より前、タグの内部には記述できない。
  また、コメント内にハイフンを2つつなげて記述できない。
#### Element / 要素
- 内容あり
  <要素名>内容</要素名>
- 内容なし
  <要素名 />
#### Attribute / 属性
- 要素の開始タグ内に、[属性],[=],[属性地]という形で記述する。
#### Data structure / データ構造
- ツリー構造を取る。
#### Form
##### well-formed XML document / 整形式XML文書
- XML宣言
- XMLインスタンス
##### valid XML document / 妥当なXML文書
- XML宣言
- DTD
- XMLインスタンス

- well-formed + DTDも満たしたもの。大枠のXMLとしての枠だけでなく、独自定義した制限も満たしたもの。

#### 予約語
##### SGML
- SGMLからの予約語は大文字で表記されている
###### #FIXED
###### #IMPLIED
###### #PCDATA
###### #REQUIRED
###### ANY
###### ATTLIST
###### CDATA
###### DOCTYPE
###### ELEMENT
###### EMPTY
###### ENTITY
###### ENTITIES
###### ID
###### IDREF
###### IDREFS
###### IGNORE
###### INCLUDE
###### NDATA
###### NMTOKEN
###### NMTOKENS
###### NOTATION
###### PUBLIC
###### SYSTEM
##### XML
###### encoding
###### standalone
###### version
###### xml
###### xml:lang
###### xml:space
#### Processing Interaction, PI 処理命令
- <? ~ ?>で囲まれた内容。
  処理アプリケーションに対して、XML文書からの命令を示すもの。
##### xml
- xml宣言
##### xml-stylesheet
- xsltスタイルシートとの紐付
  ex) <?xml-stylesheet type="text/xsl" href="books.xsl" ?>
###### Attributes
####### type
- stylesheetの形式を表す。必須。
- values
  - text/xsl : XSLTスタイルシート
  - text/css : CSS
####### href
- stylesheetを格納した場所を指定する。必須。
#### Rules
- 唯一のルート要素を持つ。
- 開始タグで始まり、終了タグでをある必要がある。
- 全要素は正しくネストされる必要がある。
- 各要素の大文字/小文字は区別される。
- 属性値はダブルクォーテーションで囲まれなければならない
## Namespace in XML / XML名前空間
- <要素名 XMLNS="名前空間URL">
  プリフィックスのついていない要素は全て上記の名前空間に属する。
- <要素名 XMLNS:プリフィックス="名前空間URL">
  プリフィックスで、使用している名前空間を識別する。
### Link
- [[https://www.w3.org/TR/REC-xml-names/][Namespaces in XML 1.0 (Third Edition) - W3C]]
## XML Schema
- XML文書の論理的構造を定義するために開発されたスキーマ言語のひとつ。
  DTDがXMLで使いにくい面があったため、1998/11にW3Cが策定開始。
  DTDよりもXMLに適したスキーマ言語となっているが、標準化が難航、複雑な仕様となっている。
### Elements
- xsdは便宜上の名前
#### xsd
## DSDL
- Document Schema Definition Language / 文書スキーマ定義言語
### RELAX NG / リラクシング
- RELAX Next Generation
- 正規文法に基づく妥当性検証
- XMLのスキーマ言語のひとつ。XML文書の構造と内容のパターンを定義する。
### Schematron / スキマトロン
- 規則に基づく検証
### NVDL
- 名前空間に基づく検証委譲言語
### DTD
- Document Type Definition
  XMLの記述の決まりを定義するもの。
  SGMLのスキーマ言語として開発された。
- 名前空間の解決が行えない、XMLと定義がかけ離れている、などの理由により、扱いにくくなっている。
  代わりとして主にXML Schemaの利用が考えられている。
#### マークアップ宣言
##### 要素タイプ宣言
##### 属性タイプ宣言
##### エンティティ宣言
##### 記法宣言
#### Link
- http://www.webword.jp/xml/dtd/index3.html

#### PCDATA
- Parsed Character Data
  data difinition that originated in SGML, and is used also in XML DTD to designate mixed content XML elements.
  
#### CDATA
- Character Data
  the data in between these tags includes data that could be interpreted as XML markup, but shuould not be.
## XSL
### XSLT, XSL Transformations
- XML文書の変換用言語。
  この文書自体もXML文書である。
#### Version 1.0
##### Elements
- xsl、は便宜上のネームスペース
###### xsl:stylesheet
- xsltのルート要素。
####### Attributes
######## xmlns:xsl
- "http://www.w3.org/1999/XSL/Transform"
######## version
- "1.0"
###### xsl:template
- XML文書に対して適用される一連のスタイル規則を定義する。
###### xsl:output
- 出力後の形式を明示的に宣言するためのもの。必須ではない。
####### Attributes
######## method
- 出力形式を指定。デフォルトはhtml。
- values
  - xml
  - html
  - text
######## encoding
- 文字コードを指定。
- ex)
  - encoding="Shift_JIS"
######## version
######## indent
- インデントの有無を指定
- values
  - yes / no
######## media-type
- MIMEタイプを指定
- ex)
  - text/html
###### xsl:text
- 固定の文字列を出力。
  基本的には省略可能。
- ex)
  <th><xsl:text>ISBNコード</xsl:text></th>
  ⇒<th>ISBNコード</th>でもOK。
####### Attributes
######## disable-output-escaping
- エスケープ文字を展開するかどうかを指定。
  yesの場合、"&lt" -> "<"に展開する。
- values
  - yes / no
###### xsl:value-of
- select属性で指定された要素/属性の内容を取得し出力する。
####### Attributes
######## select
#### Version 2.0
### XSL-FO
## SGML
- Standard Generalized Markup Language
- SGMLを元にXML、HTMLが開発された。
## Memo
### Spec
#### XQuery
- XMLデータ問合せのための言語であり、チューリング完全な関数型言語でもある。
  QUiltと呼ばれる言語をベースに設計されているが、他にも各種言語の影響を受けている。
- XQuery 1.0はXPath 2.0の拡張。
#### XPath, XML Path Language
- XMLに準拠した文書の特定の部分を指定する言語構文。
##### XPath 1.0
##### XPath 2.0
##### XPath 3.0
#### XML Database
### インデント整形
- Emcasでの整形
  M-x sgml-pretty-print
  http://d.hatena.ne.jp/lottz/20090509/1241859201
- tidy (CUI)
  http://takuya-1st.hatenablog.jp/entry/20110830/1314704820
- xmllint
  xmllint --format name.xml
- xmlstarlet(xml)
  xmltartlet fo name.xml
  http://torotoki.hatenablog.com/entry/2013/02/25/003615
  
## Link
