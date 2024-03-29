# Reverse Engineering
## Tools
### Debugger
#### Win
##### x64dbg
###### Link
- https://github.com/x64dbg/x64dbg/wiki

- http://reverseengineeringtips.blogspot.com/2015/01/an-introduction-to-x64dbg.html
##### WinDBG
- https://blog.takanabe.tokyo/2015/06/03/1087/
##### Old
###### Ollydbg
###### Immunity Debugger
#### Linux
#### Multi
##### IDA
- [[file:IDA.org][IDA.org]]
#### Link
- https://stackoverflow.com/questions/47334835/what-are-the-key-differences-between-ida-and-x64dbg#
## Command
- https://qiita.com/rsooo/items/bb91071685f447ce29db
### General
#### file
- ファイルタイプを調べる
#### strings
- 文字列を抜き出す
#### od
- バイナリファイルの16進ダンプ
#### hexdump
- バイナリファイルの16進ダンプ
#### objdump
- バイナリファイルの16進ダンプ
#### vim
- :%!xxd : バイナリ表示にする
- :%!xxd -r : 元に戻す
#### emacs
- M-x hexl-mode
#### dd
- バイナリ編集
  ブロック単位で読み出し、変換するコマンド。
### ELF
#### readelf
#### nm
- シンボルを表示
#### ldd
- ライブラリ一覧
## Documents
### Docs
- https://x64dbg.readthedocs.io/en/latest/what.html
### Wiki
#### Coding Guidelines
#### Color Schemes
## Glossary
### Clean room design / クリーンルーム設計
- リバースエンジニアリングするチームと、そこで得られた情報を元に再実装するチームを隔離することで、
  著作権や企業秘密に抵触することなく、その製品の別実装を得る手法。
## Memo
### 法律上の扱い
- Wikipedia
  原則的には「合法」行為であり、市販品などの秘密保持契約なしで合法的に入手できる製品・文献・情報について、リバースエンジニアリングを行うことに問題はない。
  ただし、解析行為によって得た中身そのものについての情報にもとづき、実装をそのまま真似したクローンを作って商業製品とすることには問題がある。
  従って、解析部門と開発部門を分ける「クリーンルーム手法」により、解析結果の「外側からの情報」だけを元に、再実装を行う。
  
- [[https://www.clairlaw.jp/qa/it/information/post-40.html][Q:当社のライバル会社が、当社の製品を購入して分解してその仕組みを調べ上げ（リバースエンジニアリング）、～ - CLAIR LAW FIRM]]
  - いわゆるリバースエンジニアリング（製品などを分解・解析し、その仕組みを明らかにすること）によって容易に取得できる情報は
    営業秘密にはあたらないので、ライバル会社がこれを利用することは違法ではありません。
    このような場合は事前に、秘密保護のための対策を講じる必要があります。
- [[http://kasiko.me/%E3%83%97%E3%83%AD%E3%82%B0%E3%83%A9%E3%83%A0%E3%83%BB%E3%83%AA%E3%83%90%E3%83%BC%E3%82%B9%E3%82%A8%E3%83%B3%E3%82%B8%E3%83%8B%E3%82%A2%E3%83%AA%E3%83%B3%E3%82%B0%E3%81%AE%E6%B3%95%E5%BE%8B%E5%95%8F/][プログラム・リバースエンジニアリングの法律問題 - kasiko]]
  - 特許法６９条１項
    「特許権の効力は、試験又は研究のためにする特許発明の実施には、及ばない。」
## Link
- [[https://github.com/wtsxDev/reverse-engineering][wtsxDev/reverse-engineering - GitHub]]

- [[http://www.atmarkit.co.jp/ait/articles/1105/17/news129.html][リバースエンジニアリング入門 - @IT]]
- [[http://d.hatena.ne.jp/waidotto/20120820/1345477008][CTFに使用するツール類まとめ - ソースコード置き場]]

- [[https://hp.vector.co.jp/authors/VA028184/][Digital Travesia]]

- [[https://hackmd.io/s/S1kLEr5x#][マルウェア解析に必要な素養]]
  - [[https://hackmd.io/s/HkV9t7chW][マルウェア解析に必要な素養～導入編～]]

- [[http://niiconsulting.com/checkmate/2018/04/reverse-engineering-x64-for-beginners-linux/][Reverse Engineering x64 for Biginners - Linux]]
- [[http://niiconsulting.com/checkmate/2018/04/reverse-engineering-x64-for-beginners-windows/][Reverse Engineering x64 for Biginners - Windows]]
