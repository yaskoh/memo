# Character Encoding
## ASCII
### Escape
## Shift JIS
### Code page 932, CP932
### Shift_JISX0213
### Memo
#### 日本語の抜出
- UTF-8でも通用するかは不明だが、少なくともSJISは理に適っていそう。
  以下を正規表現対象として抽出する。
  '[亜-熙ぁ-んァ-ヶ]'

- [[http://qiita.com/sue738/items/3118b2bd1473e2de5bdf][複数ファイルから日本語を含むファイルを抽出する - Qiita]]

### Link
- [[https://charset.uic.jp/show/cp932/][文字コード表]]
## Unicode
- Unicodeは文字集合（表現したい文字の集まり）、
  UTF-8などは符号化方式（文字の表現方法）
### Code Point / Code Position コードポイント
- 
  個々の文字に対して、文字集合内での符号位置が決められており、これをコードポイントという。
  実際の符号化されたバイトとは異なる。
  
  ex) 丈は、UnicodeのコードポイントはU+2000B。
      UTF-8 : [F0 A0 80 8B], UTF-16 : [D840DC0B], UTF-32 : [0002000B]

### Surrogate Pairs サロゲートペア
### 基底文字、結合文字
- Base Character

- Combining Character 結合文字
  結合文字は普通単独では用いない。
  直前の基底文字でzero width joinerでもzero width nonjoinerでもないものに依存する。

### Character Encoding Scheme
- エンコード（符号化）方式
#### UTF-8
- [[https://tools.ietf.org/html/rfc3629][UTF-8, a transformation format of ISO 10646 (RFC3629)]]
##### Memo
###### BOM付
- Byte Order Markは、先頭3バイトが0xEF 0xBB 0xBF
#### UTF-16
##### Memo
###### BOM
- BOMは基本必須。BEかLEかを見分けるのに使う。
  BE : 0xFE 0xFF
  LE : 0xFF 0xFE
  
#### UTF-32
### Normalization
- [[http://nomenclator.la.coocan.jp/unicode/normalization.htm][Unicode正規化とは]]
- [[http://www.sakito.com/2010/05/mac-os-x-normalization.html][Mac OS X におけるファイル名に関するメモ(NFC, NFD等) - 技術的生存報告記]]
## EUC-JP
## EBCDIC
## Link
- [[http://ash.jp/code/unitbl21.htm][Unicode対応 文字コード表]]
