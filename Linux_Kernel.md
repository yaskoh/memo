# Linux Kernel
## Directory
### Documentation
### arch
- CPUアーキテクチャ依存部
### drivers
- デバイスドライバ
### fs
- ファイルシステム
### include
- ヘッダファイル
### kernel
- カーネル基本機能
#### sched
- プロセススケジューラ
#### time
- 時計
## mm
- メモリ管理
#### page_alloc.c
- Manages the free list, the system allocates free pages.
  
## Functions
### Memory Management メモリ管理
#### Buddy System
- 
  実メモリの割り当てアルゴリズム。
  2のべき乗の大きさのメモリブロックを保持し、割り当て時は必要な最小のメモリ・ブロックを割り当てる。
  なければもう一つ大きなオーダーのブロックを取得し、半分に分割して返す。
  利用状況は/proc/buddyinfoを確認する。

- [[http://www.coins.tsukuba.ac.jp/~yas/coins/os2-2011/2012-01-17/][メモリ管理、Buddyシステム、kmalloc、スラブアロケータ - 新城靖 筑波大学]]
- [[http://taksatou.blogspot.jp/2009/12/linux.html][Linuxのメモリ管理について - taksatouの日記]]

#### Slab allocator
- slub
  2.6.22でアロケータの実装として新しく「SLUB The unqueued slab allocator」(SLUB)が導入され、2.6.23-rc1でデフォルトになった。
  SLABアロケータはSLAB, SLUB, SLOBの中から選べるようになっている。
  （SLOBは組み込み(CONFIG_EMBEDDED)の場合にだけ選択できるシンプルで小さいアロケータ。）
  [[http://www.atmarkit.co.jp/flinux/rensai/watch2007/watch09b.html][9月版 ユーザー空間でのデバイスドライバ作成に道開ける - Linux Kernel Watch / @IT]]

- 
  SLABはメモリ割り当て時に、部分的に使用中のページがあればそこから優先的にメモリを割り当てる。
  メモリ確保と開放が交互に動いている状況では無駄な領域はほとんど発生しない。
  メモリ確保・メモリ解放が非常にたくさん連続して発生すると、部分的に使用中のメモリが大量にできることがある。

- 
  同じ大きさの構造体を割り当てる時に使う。
  良く使われるオブジェクトはすぐに開放される傾向があるため、その性質を生かすために「キャッシュ」する。
  1つのスラブは、ヘッダと複数のオブジェクトから構成される。
  1スラブが1つのページフレームに収まるようにすることが多いが、複数のページフレームにまたがることもある。
  
- 
  バディシステムから確保したメモリを、キャッシュと呼ばれる同じ種類のオブジェクトの集合に分割する。
  ここでいうキャッシュとは、バディシステムから確保された連続した物理ページの集まりで、
  キャッシュに対して割り当てられたオブジェクトの入れ物をスラブという。
  利用状況は/proc/slabinfoを確認する。
  
##### SLAB
- 
  ページサイズ未満のメモリを管理する方法。
  一つのページ内に複数のslabを確保する。

#### Fragmentation
- [[http://www.atmarkit.co.jp/flinux/rensai/watch2008/watchmema.html][Linuxメモリ管理の最先端を探る - Linux Kernel Watch 番外編 / @IT]]
##### Lumpy Reclaim
- 
  2.6.23でマージされた機能。フラグメントした後の対処方法。
  ページフレーム回収の契機となったメモリ確保要求のサイズがある閾値（現在はページサイズの8倍）を超えた場合、
  破棄されることになったページフレームの物理アドレスと隣接した物理アドレスを持つキャッシュページを、ページのアクセス率に関係なく無理やり回収する。

##### Anti Fragmentation
- 
  フラグメントを起こしにくい割り当て方式。2.6.24でマージされた。
  複数のページが必要なときに連続領域が確保できない「外部断片化」という問題に対する対処。
  カーネルで使われるメモリで短命なものと長名なものがあるので、メモリ確保要求を用途ごとに分別し、似たような用途のページが物理アドレス的に近くなるように割り当てる。
  メモリを「UNMOVABLE」「RECLAIMABLE」「MOVABLE」「RESERVE」の4種類に分類する。
  - UNMOVABLE : カーネルが内部的に使うメモリ、アドレスをポインタとして保持しているので移動しない。長命。
  - RECLAIMABLE : ページキャッシュ・inodeキャッシュなどのキャッシュ類、どちらかというと短命。
  - MOVABLE : ユーザプロセス用のメモリ、短命。
  - RESERVE : 空きメモリが逼迫しない限り使われない虎の子メモリ。

##### Slab Defragmentation
- 
  ページ内部で未使用領域が増えてしまう「内部断片化」に対する改善。
  SLABのフラグメント率を監視し、あるフラグメント率（デフォルト30％）を超えたら、
  メモリ不足時の改修処理の延長でデフラグルーチンが作動し、その結果空いたページを解放する仕組み。
  SLUBにしか実装されていない。
  またSLUBは断片化が発生しにくいよう考慮されているため、通常はフラグメントがそこまで進むこともなく、
  一般的なワークロードでは性能オーバーヘッドも発生しない。

#### Cache
##### Page / Buffer Cache
- 違い
  ページキャッシュは、ファイルI/Oを最適化するために、ファイルのページをキャッシュする。
  バッファキャッシュは、ブロックI/Oを最適化するために、ディスクブロックをキャッシュする。
  
  Linuxカーネル2.4より前では、2つのキャッシュは明白に違うもので、ファイルはページキャッシュ、ディスクブロックはバッファキャッシュに乗せられていた。
  ほとんどのファイルがディスク上のファイルシステムによって扱われているとすると、データは両方のキャッシュそれぞれで扱われる。
  
  カーネル2.4以降は、VMサブシステムがI/Oをつかさどるようになり、キャッシュされたデータが両方の形を取る場合、バッファキャッシュは単純にページキャッシュを指し示す。
  つまり、データは1つだけがメモリにキャッシュされていることになる。

  メタデータやrowブロックI/Oなどは、もっぱらバッファキャッシュによって取り扱われる。

  http://b.l0g.jp/linux/buffercache-and-page-cache/

##### inodeキャッシュ
- 
  ファイルのメタデータをキャッシュする。slabを使う場合が多い。

##### dentryキャッシュ
- 
  ファイルのパス名をキャッシュする。slabを使う場合が多い。

#### Memo
- [[http://sandragon.hatenablog.com/entry/2014/06/14/235825][Linuxにおけるメモリ管理 - MogLog]]
- [[http://d.hatena.ne.jp/naoya/20070521/1179754203][Linuxのページキャッシュ - naoyaのはてなダイアリー]]

## Reading_Memo
### mm
#### page_alloc.c
##### __alloc_pages_nodemask()
- "This is the 'heart' of the zoned buddy allocator."
  

##### __alloc_pages_slowpath()


- nopage:
  pageがない場合に"warn_alloc_failed()"を呼ぶ
##### warn_alloc_failed()
- 
  
## Link
- [[https://www.kernel.org/][The Linux Kernel Archive]]
- [[http://www.tux.org/lkml/][The linux-kernel mailing list FAQ]]
- [[https://lkml.org/][LKML.org - Linux Kernel Mailing List]]
- [[http://lxr.free-electrons.com/][Linux Cross Reference]]
- [[https://linuxjf.osdn.jp/JFdocs/The-Linux-Kernel.html#toc4][The Linux Kernel / David A Rusling (JP Project, 2000)]]
- [[http://itpro.nikkeibp.co.jp/article/COLUMN/20080501/300463/][Linuxカーネルの基本機能 - ITpro]]
- [[http://itpro.nikkeibp.co.jp/article/COLUMN/20071023/285284/][はじめてのカーネル・ソース - ITpro]]
- [[http://osdn.co.jp/event/pdf/LW2001Fall_takahashi.pdf][Linuxカーネルの歩き方(pdf)]]
- [[https://yakst.com/ja/posts/156][Linuxカーネルハッカーになる4つの方法 - Yakst]]
  - 方法1:自分のOSを書く
  - 方法2:カーネルモジュールを書く
  - 方法3:Linuxインターン湿布に参加する
  - 方法4:カーネルコードを読む

