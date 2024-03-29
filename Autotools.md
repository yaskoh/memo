# Autotools

- 
  autoconf, automake, libtoolといったツールの総称。
  主に上記3つのツールで構成されている。


- autotoolsによる環境構築
  1. makefile.amの作成・編集をする
  2. configure.acを作成・編集する
  3. autoheaderコマンドを実行する(プリプロセッサ陽ヘッダファイル雛形の生成)
  4. aclocalコマンドを実行する(automake用m4マクロの生成)
  5. automakeコマンドを実行する(makefile.inの生成)
  6. autoconfコマンドを実行する(configureスクリプトの生成)

## tools

### autoconf
- 
  開発環境の定義を記述したファイル"configure.ac"から"configure"スクリプトを生成するためのツール。
  以前は"configure.in"から作成していたが、最近は"configure.ac"となっている。

### automake
- 
  "Makefile.am"から"Makefile.in"ファイルを生成するツール。
  "Makefile.am"ファイルには、プログラムとソースコードの関係などを記述する。
  "Makefile.in"はMakefileのテンプレートとなる。

### libtool
- 
  システムに依存するライブラリを自動で構築するためのツール。


## command

### make

- install, uninstall
  ビルドされた実行ファイルやライブラリが適切なディレクトリへインストールされる。
  uninstallも自動で生成されるため、ファイルを簡単に削除可能。

- clean, disclean
  cleanはmakeで生成されたファイルを削除するためのmakeターゲット。
  discleanは、cleanに比べてconfigureで生成されたファイルも削除する。

- dist
  tar.gz形式のソースパッケージを作成する。
  その他パッケージを作成するためのmakeターゲットも用意されている。
  make dist-bzip2, make dist-xz, make dist-zipなど。


## file

### configure.ac
- 
  configureの雛形。自分で書く。
  autoscanして、configure.scanを作成、リネームしてconfigure.acを作成。

### Makefile.am
- 
  Makefileの雛形のMakefile.inの雛形。自分で書く。
  ライセンスをGPL以外にしたい場合は"AUTOMAKE_OPTIONS = foreign"と書いておく。

## memo

### Link

[[http://capm-network.com/?tag=autotools][Capm Network - autotools]]
[[http://loto.sourceforge.net/feram/Autotools-memo.ja.html][Autotoolsについてのメモ]]
