# Coding
## Naming Conventions
### CamelCase
- 
  大文字によって単語の区切りを表す表記法。
  Java策定時に、フォントとプリンタによってはアンダースコアが印刷されないバグがあったとかで、
  Camelが使われたとかなんとか。。
  ちなみに先頭文字が大文字なのをPascalCase、2つ目以降が大文字なのをcamelCase、という場合もある。

### snake_case
- 
  アンダースコアで単語の区切りを表す表記法。
## Readable Code
### Key Idea
- コードは理解しやすくなければいけない
- コードは他の人が最短時間で理解できるように書かなければいけない
### 表面
#### Naming
##### Key
- 名前に情報を詰め込む
##### Point
###### 明確な単語を選ぶ
- Key
  気取った言い回しよりも、明確で正確なほうがいい。

- getよりもdownloadなど
- Size()よりもHeight(), NumNodes(), MemoryBytes()
- Stop()も悪くないが、取り消しがきかないならKill()、Resume()できるならPause()
- カラフルな単語を探す
  例）
  |-------+----------------------------------------------------|
  | Word  |                                                    |
  |-------+----------------------------------------------------|
  | send  | deliver, dispatch, announce, distribute, route     |
  | find  | search, extract, locate, recover                   |
  | start | launch, create, begin, open                        |
  | make  | create, set up, build, generate, compose, add, new |
  |-------+----------------------------------------------------|

###### 汎用的な名前を避ける
- tmp, it, retvalのような汎用的な名前を使うときは、それ相応の理由を用意する。
  - 一時的な保管、という意味が一番適切であれば、tmpがふさわしい場合もある。
- ループイテレータにi, j, k, iterなどを使うのは、イテレータだということが分かるので問題ない。
  ただし、複数の情報がある場合（たとえばculb, member, userなどそれぞれをループで回す）、
  club_i, members_i, users_i、もしくはもっと簡単にci, mi, uiなどとしておくとわかりやすい。
  
###### 抽象的な名前よりも具体的な名前を使う

###### 接尾辞や接頭辞を使って情報を追加する
- 名前は短いコメントのようなもの。
- idのフォーマットが大事なら、idでなくhex_idなどとする。
- 値の単位を追加する。delay->delay_secs, size->size_mb, limit->max_kbpsなど。
- その他の重要な情報を追加する。変数の意味を間違えてしまったときに、バグになりそうなところだけに使うのが適切。
  暗号化する必要があるパスワードは、plaintext_password,
  エスケープが必要な文字列はcomment->unescaped_comment,
  urlエンコードされたdataはdata->data_urlencなど。

###### スコープの大きな変数には長い名前をつける
- スコープが小さければ短い名前でいい
- 長い名前は補完すればよい
- BackEndManager->BEManegerなどの省略は、プロジェクト固有のものはダメ。
  良く知られているものは問題ない。eval, doc, strなど。
- 不要な単語を捨てる。ConvertToString()->ToString(), DoServerLoop()->ServerLoop()など

###### 名前のフォーマットで情報を伝える
- プロジェクトで一貫性を持たせて規約を使う。
  
####### Google社のC++フォーマット規格
- ClassName : CamelCase
- variables : lower_separated
- Const var : kConstName
- #define macro : MACRO_NAME
- class member var : offset_ (with _ on the last of word)
##### Technique
- Key : 「他の意味と間違えられることはないだろうか？」と何度も自問自答する
###### 限界値を含めるときはmin, max
###### 範囲を指定するときはfirst, last
###### 包含・排他的範囲にはbegin, end
#### Layout
##### 基本方針
- 読み手が慣れているパターンと一貫性のあるレイアウトを使う
- 似ているコードは似ているように見せる
- 関連するコードをまとめてブロックにする
- 一貫性のあるスタイルは、「正しい」スタイルよりも大切
##### まとめ
- 複数のコードブロックで同じようなことをしている場合、シルエットも同じようなものにする。
- コードの「列」を整理する
- ある場所でA,B,Cと並んでいたものを、別の場所でB,C,Aのように並べてはいけない。
- 空行を使って、大きなブロックを論理的な「段落」に分ける

#### Comment
##### Point
- Key : コメントの目的は、書き手の意図を読み手に知らせることである。
###### コメントすべきで「ない」こと
- コードからすぐわかることをコメントに書かない
  - コメントのためのコメントをしない
- ひどい名前はコメントとをつけずに名前を変える
###### 自分の考えを記録する
- なぜコードが他のやり方でなくこうなっているのか。「監督のコメンタリー」を入れる
- コードの欠陥をTODO:やXXX:などの記法を使って示す
- 定数の値の「背景」
###### 読み手の立場になって考える
- コードを読んだ人が驚くところを予想してコメントを付ける
- 平均的な読み手が驚く動作は文書化しておく
- ファイルやクラスに「全体像」のコメントを書く
- 読み手が細部に捕らわれないように、コードブロックにコメントをつけて概要をまとめる
##### Technique
- Key : コメントは領域に対する情報の比率が高くなければいけない

### 構造

### 再構成
## Memo
### Expression, Statement
#### Expression 式
- 
  combination of one or more explicit values, constants, variables, operators, and functions
  that the programming language interprets and computes to produce another value.
  This process, as for mathematical expressions, is called evaluation.

- 
  評価された値を持つ。

#### Statement 文
- 
  the smallest standalone language that expresses some action to be carried out.
  statement may have internal components(e.g., expression)

- 
  大まかに言えば、一つ以上の式や関数呼び出しで作られる、手続き構造の単位が文。
  if文や代入文など代表例。
  セミコロンまで含めれば、構造の単位となり文だが、中に評価式が含まれる場合がある。
  ex) expression : a + b
      statement  : a + b;
  

*** [[https://speakerdeck.com/twada/quality-and-speed-2022-spring-edition][質とスピード - 和田卓人 - speakerdeck]]
- 技術力のある人はある程度急いで作ったとしても一定以上の品質のコードを書くし、意図的に品質を落としたとしても速度はあまりあがらない。
  逆に、技術力が高くない人が時間をかけて作ったとしてもその人の技術力以上の品質のコードは書けない。
- 短期的にも長期的にも、崩壊したコードを書く方がクリーンなコードを書くよりも常に遅い。
- 私が会った中で最速のプログラマーは、コードを扱いやすいように保つことに特に注意を払っていた。
  コードの品質を高く保っていた「にも関わらず  」速いのではない。コードの品質を高く保っていた「からこそ」速いのだ。
- 質vsスピードという概念は根本的に間違っていると思う。
  大域的には、片方を犠牲にした場合、知らぬうちにもう一つも犠牲にしているということをお忘れなく。
- スピードおよび質とトレードオフなのは教育、成長、多様性への投資
- 説明責任の向きを反転させること。変える理由を説明するのではなく、変えない理由を説明する方向に力学を変える
- テスト容易性と、デプロイ容易性
- 一番重要で一番やっかいなスキルはシステムを設計するための判断力だ。限りなくシンプルなデザインというのはなかなか教えられるものではなく、大方経験を重ねて覚えるものだ。
  この「判断力」は、プログラマーにとって非常に重要なのだが、そう簡単に教えられるものでもない。ぼくが知る限り、判断力をつける一番の方法は、自分で設計したシステムを長い間メンテすることだと思う。
