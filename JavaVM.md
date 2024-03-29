# Java Virtual Machine
## Specification
### 1.8
#### Instruction Set
##### Instructions
###### aconst_null
- Operation
  Push null
- Description
  Push the null object reference onto the operand stack.
###### astore
- Operation
  Store reference into local variable
- Description

###### getstatic
#### Link
- [[https://docs.oracle.com/javase/specs/jvms/se8/html/index.html][The Javaﾂｮ Virtual Machine Specification Java SE 8 Edition - ORACLE]]
## Java HotSpot VM Options
- http://www.oracle.com/technetwork/java/javase/tech/vmoptions-jsp-140102.html
### Behavioral Options
#### -XX:+ScavengeBeforeFullGC
#### -XX:-UseConcMarkSweepGC
#### -XX:-UseParallelGC
#### -XX:-UseSerialGC
### Garbage First (G1) Garbage Collection Options
#### -XX:+UseG1GC
#### -XX:NewRatio=n
#### -XX:MaxTenuringThreshold=n
#### -XX:ParallelGCThreads=n
### Performance Options
#### -XX:MaxNewSize=size
#### -XX:MaxNewRatio=n
#### -XX:SurvivorRatio=n
- Ratio of old/new generation sizes.
### Debugging Options
## Glossary
### 実装系
#### HotSpot VM
- HotSpot : Oracleが提供されているJava仮想マシンで使われている高速化のための技術の名称。
  元々Sun Microsystemsが開発していた。
- HotSpotコンパイラを搭載する。アプリケーションにおいて最も実行頻度の高い部分のみコンパイルする。
- http://www.oracle.com/technetwork/java/javase/tech/index-jsp-136373.html
#### Classic JVM
- JITコンパイラ
#### JRockit
- BEA

#### Apache Harmony
- Apacheソフトウェア財団にて開発していたJavaっ実装。
  2011/11/3にOpenJDKに集約される形で開発終了。
#### JBlend
## Memo
### Memory
- https://qiita.com/opengl-8080/items/64152ee9965441f7667b
#### Structure
##### Heap
- Javaプログラムが使う領域。
  プログラム上で生成したオブジェクトはヒープ領域に配置される。
- 一般には、ヒープはプログラムが動くために確保されたメモリ領域を指す。
  Javaでヒープ、という場合はJVM上で動くJavaプログラムのためのメモリ領域。
  対してCヒープ、という場合は、JVM文脈ではネイティブ領域のこと。
###### Young / New
- 生成されて時間の短いオブジェクトが配置される
####### Eden
####### Survivor(1,2)
###### Old / Tenured
- Promotion : MaxTenuringThreshold以上移動した場合、Minor GCでSurvivorから移ってくる。
##### Native
- JVMが動くのに必要なメモリやスレッドのスタックを管理するのに使用される
- [[https://qiita.com/opengl-8080/items/64152ee9965441f7667b][OutOfMemoryErrorの調べ方 - Qiita]]
###### Metaspace
- Java8から採用された、Permanent領域に代わるメモリ領域。
##### Stack
##### Permanent(-Java7, Obsolete)
- クラスやメソッドのメタ情報など、静的な情報が格納される。
- ヒープ領域でもネイティブ領域でもない領域。
- Java8で廃止され、Metaspace(Native領域)が追加された。
#### Tool
##### jcmd
- コマンド一覧の表示
  jcmd 0 help
- コマンドのヘルプを確認
  jcmd 0 help GC.heap_dump
##### jmap (-Java6)
##### jconsole
- JVMの詳細なメモリ状況をリアルタイムで確認できるツール。
##### jstat
- JDKに付属しているツール。
  JVMの統計上をモニターできる。試験的なもので、サポート対象外らしい。
##### HeapStats
##### jvisualvm
- JVMの状態をリアルタイムにGUIで分析するためのツール。
###### Memo
####### サンプラ・プロファイラの違い
##### Eclipse Memory Analyzer Tool
#### Link
- http://www.atmarkit.co.jp/ait/articles/1005/13/news095.html
### Gavage Collection
#### HotSpot JVM GCs
##### Serial GC
- アプリケーションとガベージコレクションのスレッドが交互に実行される（パラレルと同様）
- ガベージコレクション用のスレッドが１つだけしか使用されない。
- シングルコアマシンのデフォルト。
##### Parallel GC
- アプリケーションとガベージコレクションのスレッドが交互に実行される（シリアルと同様）
- ガベージコレクション用のスレッドが複数使用される。
- マルチコアマシンのデフォルト。
##### Concurrent Mark & Sweep GC / CMS
- CMS GC, Concurrent GCなど。
- シリアル・パラレルGCと異なり、アプリケーションと同時に動く(Concurrent)
- ゴミじゃない領域をMarkし、Sweepして再利用可能に。
- コンパクションがなく断片化が生じる
- HotSpotVMの場合、世代別ヒープ管理、STWを伴うGC、フェーズがある、CMSで改修失敗の場合Full GC
- http://cco.hatenablog.jp/entry/2014/12/01/162240
##### Garbage First GC / G1GC
#### Type
##### Minor Garbage Collection
- Parallel Copy GC (Scavenge GC)
- Young領域がいっぱいになったときに実行される
- アプリケーションを止める(Stop-The-World)
- Promotion条件はMaxTenuringThreshold
##### Major Garbage Collection
- Old領域が一杯になった時に実行されるGC。
- Concurrent GCが使われる
- 発生条件はCMSInitiatingOccupancyFraction、ヒープ占有速度の統計判断など。
- http://cco.hatenablog.jp/entry/2014/12/01/162240
##### Full Garbage Collection
- Mark & Sweep GCが使われる
- 発生条件：
  - 断片化で割り当て不可(promotion failed)
  - 回収が間に合わない(concurrent mode failure)
#### Method
##### Scavenge GC / Copy GC
- 世代別GCで実行される手法の一つ。
- マイナーGCで使用される。
- 早い、メモリ断片化なし
- Stop the Worldの時間は短い。
- Edenが一杯になったら、Young / New領域を対象に実行される。
  使用中のオブジェクトはSurvivor / Toへ移動、不要なオブジェクトは破棄される。
- 実行される度にSurvivorのTo/Fromが入れ替わり実行される。
  MaxTenuringThresholdを超過したらOldへ移る。
##### Concurrent Mark & Sweep GC
- See 'HotSpot JVM GCs'
##### Mark & Sweep GC
- フルガベージコレクションで使用される
#### Parameter
- http://nekop.hatenablog.com/entry/20140327/1395886237
#### Memo
- https://docs.oracle.com/javase/jp/8/docs/technotes/guides/vm/gctuning/toc.html
### Performance
- https://www.ibm.com/developerworks/jp/java/library/j-jtp12214/index.html
## Link
- [[http://gihyo.jp/dev/serial/01/jvm-arc][Javaはどのように動くのか～図解でわかるJVMの仕組み - gihyo.jp]]
