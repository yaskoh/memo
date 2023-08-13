# Web Service
## About
- a standardized way of integrating web-based applications
  using the XML, SOAP, WSDL and UDDI open standards over an Internet protocol backbone.
## Techonologies
### WSDL
- Web Services Description Language
  ウィズダル
- SOAPによるXML Webサービスのインターフェースを記述するインターフェース言語。
#### Version 1.1
##### Structure
###### definitions
####### Abstract Section
######## types
######## message
######## portType
######### operation
########## input
########## output
####### Concreate Section
######## binding
######## service
######### port
##### Elements
- wsdl、は便宜上の名前空間接頭辞。
###### wsdl:definitions
- root要素。
  WSDL、SOAP、XSD(XML Schema Definition)の3種類のネームスペースを指定する必要がある。
  また、TNS(TargetNamespace)を指定する必要がある。
- 少なくとも、一つのportTypeが必要。
####### Attributes
######## name
- 限定していないが、実際はWSDL文書によってインターフェースを記述しているWebサービス名を指定数rことが多い。
######## targetNamespace
- 対象名前空間URIを明示するために利用する。
######## namespaces
- 各種のネームスペースを設定する必要がある。
  （付与名は例）
######### wsdl
- WSDL
  xmlns:wsdl="http://schemas.xmlsoap.org/wsdl/"
######### soap
- SOAPバインディング
  xmlns:soap=http://schemas.xmlsoap.org/wsdl/soap/
######### soapenv
- SOAP1.1のエンベロープ名前空間
  http://schemas.xmlsoap.org/soap/envelope/
######### soapenc
- http://schemas.xmlsoap.org/soap/encoding/
######### tns
######### xsd
- http://www.w3.org/2001/XMLSchema
######### xsi
- http://www.w3.org/2001/XMLSchema-instance
###### wsdl:types
- メッセージのフォーマットを定義する際に使用する型を、抽象的に定義する。
###### wsdl:message
- Webサービスで使用するメッセージのフォーマットを抽象的に定義する。
  wsdl:typesで定義した型を使用する。
###### wsdl:portType
- サービスの単位。関連する操作をひとまとめにした抽象的なポート。
####### Attribuets
######## name
###### wsdl:binding
- wsdl:portType要素で定義されたポートタイプ内の個々の抽象的な操作に、具体的な通信プロトコルをバインドする。
###### wsdl:service
- wsdl:port要素で定義したポートのうち、関連するポートをひとまとめにしたサービスを定義する。
###### wsdl:import
###### wsdl:part
###### wsdl:operation
- 操作を抽象的に定義する。。
  wsdl:message要素で定義されたフォーマットを割り当てる。
####### Attributes
######## name
###### wsdl:port
- wsdl:biding要素で定義されたバインディングに、通信エンドポイントのネットワークアドレスをバインドして具体的なポートを定義する。
##### Link
- [[https://www.w3.org/TR/wsdl][Web Services Description Language (WSDL) 1.1 - W3C]]
#### Version 2.0
##### Structure
###### definitions
####### Abstract Section
######## types
######## interface
######### operation
########## input
########## output
####### Concreate Section
######## binding
######## service
######### endpoint
### SOAP
#### Structure
##### Protocol Binding Header
- 実装するトランスポートプロトコルに依存するヘッダ。
  続くメッセージがSOAPであることを記述。
  httpの場合、Content-Type: application/soap+xml、となる。
##### SOAP Envelope
- SOAPメッセージの外枠。
  名前空間には、SOAPの要素・属性の名前空間URIを与える。
###### Namespace
####### Version 1.1
- http://www.w3.org/2003/05/soap-envelope
####### Version 1.2
- http://schemas.xmlsoap.org/soap/envelope/
##### SOAP Header
- 省略可能。
  SOAP本体に記述された情報をだれ（どのサーバ）に渡し、どのように処理すべきか、といった情報が記述される。
##### SOAP Body / SOAP本体
- 必須項目。メッセージの本文が記述される。実際に交換されるXMLデータが入る。
  名前空間には、見積依頼サービス固有の要素・属性を与える。
#### Glossary
##### SOAPフォルト
- エラー情報。呼び出し元に返すことができる。
###### SOAP 1.1
- faultcode : 違反コードを記述する
- faultstring : 人間が読めるエラー解説を記述する
- faultactor : エラー発生元のURIを記述する
- detail : SOAP本体に関係するアプリケーション固有のエラー情報を記述する。
###### SOAP 1.2
- Code : 違反コードを記述する
- Reason : 人間が読めるエラー解説を記述する
- Node : エラー発生元のURIを記述する
- Role : エラー発生時点でのノードの役割を示すURIを記述する。
- Detail : SOAP本体に関係するアプリケーション固有のエラー情報を記述する。
#### Link
- [[https://www.w3.org/TR/soap/][Latest SOAP versions - W3C]]
### UDDI
- Universal Description, Descovery and Integration
  Webサービス用の検索システム。
  現在では殆どのUDIレジストリは公開を停止している。
### REST
#### Link
- [[http://www.xfront.com/REST-Web-Services.html][Buliding Web Services the Rest Waay]]
## Specifications
### WS-I
#### WS-I Profile
- 一連のWebサービス仕様。
  相互運用と実装のガイドラインを備える。
##### WS-I Basic Profile
###### Version 1.0
- released in early 2004.
####### Link
- [[http://www.ws-i.org/Profiles/Basic/2003-08/BasicProfile-1.0a-ja.html][Basic Profile Version 1.0a / Cover Page for the Japanese TranslatioFinal Specification - WS-I]]
###### Version 1.1
- published in 2006.
  new profile called SSBP(Simple Soap Binding Profile)
###### Version 1.2
- finalized in November 2010.
  main new features are MTOM binary attachements and WS-Addressing support.
###### Version 2.0
- published in November 2010.
  using SOAP 1.2, UDDI 2 and WS-Addressing.
##### WS-I Basic Security Profile
###### Version 1.0
###### Versior 1.1
##### Attachements
###### Version 1.0
##### Simple Soap Binding Profile
###### Version 1.0
#### WS-I test tools
### WS-Security
- Webサービスにセキュリティを適用する手段を提供する通信プロトコル。
#### Version
##### 1.0
- 2004/4/19 公開
##### 1.1
- 2006/2/17 公開
### WS-Addressing
- Webサービスがアドレス指定情報をやりとりするための転送手段から独立した機構の仕様。
## Framework
### Axis
#### Apache Axis2
- [[file:./ApacheAxis2.org][ApacheAxis2.org]]
### Apache CXF
#### Link
- [[http://cxf.apache.org/][Apache CXF]]
### Metro
#### Link
- [[https://metro.java.net/][Metro]]
## Glossary
### WS-I
- Web Services Interoperability
  Webサービス仕様の相互運用を促進することを目的として結成された業界団体。
### NQS
- Network Queuing System
## Link
- [[https://www.w3.org/2002/ws/arch/][Web Services Architecture Working Group - W3C]]
- [[http://www.ws-i.org/][WS-I]]

- http://jpn.nec.com/websam/jobcenter/download/manual/JB_QUICK_12_6.pdf
- [[http://jpn.nec.com/websam/jobcenter/trial.html][WebSAM JobCenter - 試用版 - NEC]]
