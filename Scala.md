# Scala
## Grammer
## tool
### sbt
#### About
- 
  sbt is "Simple Build Tool"
  sbt is a build tool for Scala, Java, and more.
  
#### Directory Structure
- sbt-sample/
  - src/
    - main/
      - resources/ # files to include in main jar here
      - scara/ # main Scala sources
      - java/ # main Java sources
    - test/
      - resources/ # files to include in test jar here
      - scara/ # test Scala sources
      - java/ # test Java sources
  - lib/
  - bulid.sbt # bulid file

- 
  Mavenと同じディレクトリ構造

##### build.sbt
- ビルド定義
  
##### build.properties
- バージョン設定
#### Command
##### sbt
- 
  sbt will find the following automatically:
  - Sources in the base directory
  - Sources in src/main/scala and src/main/java
  - Tests in src/test/scala and src/test/java
  - Data files in src/main/resources and src/test/resources
  - jars in lib

- Interactive modes
  Running sbt with no command line arguments starts it in iteractive mode.

- Batch mode
  run sbt in batch mode, specifying a space-separated list of sbt commands as argumets.
  - ex) sbt clean compile "testOnly TestA TestB"

##### Common commands
###### console
- 
  start REPL

###### clean
- 
  targetディレクトリにある、すべての生成されたファイルを削除する

###### compile
- 
  (/src/main/{scala,java}にある)メインのソースをコンパイルする

###### run <arguments>*
- 
  実行する
###### test
- 
  すべてのテストをコンパイルし実行する

###### console
- 
  コンパイル済みのソースと依存ライブラリにクラスパスを通して、Scalaインタタプリタを開始する。
  sbtに戻るにはCtrl-D, Ctrl-Z, :quitなどと実行する。

###### package
- 
  src/main/resources内のファイルとsrc/main/{scala,java}からコンパイルされたクラスファイルを含むjarを作る

###### help <command>
- 
  指定されたコマンドの詳細なヘルプを表示する。
  <command>が指定されない場合はすべてのコマンドの簡単な説明を表示する

###### reload
- 
  ビルド定義(build.sbt, project/*.scala, project/*.sbt)を再読み込みする。

##### History
- 
  "!"から始まるコマンド。mac上でうまく実行できなかったので略。

#### Setting
#### Link
- 
  [[https://github.com/sbt/sbt][sbt / sbt - github]]
  [[http://www.scala-sbt.org/][scala-sbt.org]]
## Link
- [[http://docs.scala-lang.org/tutorials/][Tutorials - Scala Documentation]]
