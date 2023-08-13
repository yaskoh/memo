# Org-Mode
## Document Structure
### 見出し、項目

- 見出しの編集
    |----------------+------------------------------|
    | キー           | 処理                         |
    |----------------+------------------------------|
    | TAB            | 隠す/一段展開/すべて展開     |
    | M-RET          | 同一レベル見出し挿入         |
    | M-UP/DOWN      | 見出しを前/後に移動          |
    | M-RIGHT/LEFT   | 見出しのレベルを増減         |
    | M-S-RIGHT/LEFT | 子孫も含め見出しレベルを増減 |
    | C-uC-uC-uTAB   | すべて展開                   |
    |----------------+------------------------------|

- 項目の編集
    |--------------+----------------------------------|
    | キー         | 処理                             |
    |--------------+----------------------------------|
    | TAB          | 隠す/一段展開/すべて展開         |
    | M-RET        | 同一レベルの新しい項目           |
    | M-UP/DOWN    | 前後に移動                       |
    | M-RIGHT/LEFT | レベルの増減                     |
    | C-cC-c       | 番号付き項目リストの番号付け直し |
    | M-q          | 長い文章を整形                   |
    |--------------+----------------------------------|

    - 項目リスト
        -. 項目
        +. 項目
        1. 番号
        2. 番号

    - 名前付き項目リスト
        - 名前1 :: 内容1
        - 名前2 :: 内容2

    - チェックリスト
        - C-c C-c
          [ ]⇒[X]とチェックが入れられる。同時に見出しの件数も変更される

        - チェックリスト1 [0/2]
            - [ ] チェック項目1
            - [ ] チェック項目2

        - チェックリスト2 [1/2]
            - [ ] チェック項目1
            - [X] チェック項目2

- 表示
    S-TAB あるいは C-u TAB でバッファ全体表示を切り替え。
    OVERVIEW, CONTENTS, SHOW ALL

### Outlines

### Headlines

### Visibility cycling
#### Global and local cycling

#### Initial visibility

#### Catching invisible edits

### Motion
#### C-c C-n (outline-next-visible-heading)
#### C-c C-p
#### C-c C-f
#### C-c C-u
#### C-c C-j

### Structure editing

#### C-c ^ (org-sort)
- 
  Sort same-level entries.
  When there is an active region, all entries in the region will be sorted.
  Otherwise the children of the current headline are sorted.

### Sparse trees

### Plain lists

### Drawers

### Blocks

### Footnotes

### Orgstruct mode

### Org syntax

## Tables
### 表

- 他のモードでも表を編集する
    M-x orgtbl-mode

- '|' でテーブルを作る
    | a | 1 |

- tabで次の行作成 & 自動整形
    | a | 1 |
    | 2 | 3 |

- 「|-」 を入力後tabを押すと、横線が入力される
    |-
    | a | 1 |
    ↓
    |---+---|
    | a | 1 |

- 'C-c -' でも横線挿入
    | a | b | c |
    ↓
    | a | b | c |
    |---+---+---|

- 'M-UP(DOWN, LEFT, RIGHT)'で行列の入れ替え
    | a | b | c |
    |---+---+---|
    | 1 | 2 | 3 |

    | k | l | m |
    |---+---+---|
    | 1 | 4 | 2 |

- リージョン選択して、'C-c |'で表に変換
    a,b,c
    1,2,3
    ↓
    | a | b | c |
    | 1 | 2 | 3 |
    (実際は左詰された）

- インポート (M-x org-table-import)
- エクスポート (M-x org-table-export)
    フォーマット:orgtbl-to-tsv(csv, html, latex)

- 主なキーバインド
    |--------------+------------------------|
    | キー         | 処理                   |
    |--------------+------------------------|
    | TAB          | 次の欄へ移動、表を整形 |
    | C-c C-c      | 移動せず表を整形       |
    | C-c -        | 下に横線を挿入         |
    | M-UP/DOWN    | 行の上下移動           |
    | M-RIGHT/LEFT | 列の左右移動           |
    | M-S-UP       | 行を削除               |
    | M-S-DOWN     | 行の挿入               |
    | M-S-LEFT     | 列の削除               |
    | M-S-RIGHT    | 列の挿入               |
    | M-RET        | 入力欄を分割           |
    |--------------+------------------------|

### 表計算

- 必要になったらまた覚える。
    [[http://d.hatena.ne.jp/tamura70/20100206/org]]

- 合計
    C-c +

- ソート
    C-c ^ n(N)

- 行列名表示
    C-c }

    |--------+-------|
    | 新幹線 | 15000 |
    | バス   |   200 |
    | 電車   |   160 |
    |--------+-------|

- 計算式
    行に対する計算式         : C-c = (計算式 ex: $6=vsum($2..$5)
    列に対する計算式         : C-u C-c = 
    再計算:(末尾TBLFMの行で) : C-c C-c     
    |----------+----+----+----+----+-----|
    |          | Q1 | Q2 | Q3 | Q4 | sum |
    |----------+----+----+----+----+-----|
    | パソコン | 30 |  0 | 50 |  0 |  80 |
    | ソフト   |  5 | 15 | 20 |  3 |  43 |
    | 通信     |  2 |  2 |  2 |  2 |   8 |
    |----------+----+----+----+----+-----|
    | 合計     | 37 |    |    |    |  37 |
    |----------+----+----+----+----+-----|
    #+TBLFM: $6=vsum($2..$5)::@5$2=vsum(@2..@4)

    - 関数
        vcount  : 個数
        vsum    : 総和
        vprod   : 総積
        vmax    : 最大値
        vmin    : 最小値
        vmean   : 算術平均
        vgmean  : 幾何平均
        vhmean  : 調和平均
        vsdev   : 標準偏差(N-1)
        vpsdev  : 標準偏差(N)
        war     : 分散
        vmedian : メジアン

## Hyperlinks
### リンク
- ハイパーリンク
    [ [リンク][表示] ]のようにかく（半角スペースは不要）
- リンクとして保存
    C-c l
- リンクをorgに貼り付ける
    C-c C-l
- ハイパーリンクを開く
    C-c C-o

### Link format
- 
  #+BEGIN_SRC
  [[link][description]] or [[link]]
  #+END_SRC

### Internal links

### External links
- links
  - Web : http://www.astro.uva.nl/~dominik
  - File : file:./papers/last.pdf
  - File, Text Search : file:projects.org::some words
  - Mail : mailto:test@mail.com
  - Shell : shell:ls *.org
  - elisp : elisp:org-agenda

- [[shell:ls *.org]]

### Handling links

### Using links outside Org

### Link abbreviations

### Search options

### Custom searches

## ToDo items
### TODOリスト
- TODO 
    見出しにTODOと記述するとTODOリストになる。
    他にDONE, 無印状態がある。
    WAITやSOMEDAYなども、設定すればでるらしい。

    - 状態変更
      C-c C-t, S-RIGHT(LEFT)
          
    - 優先度変更
      S-UP(DOWN)で優先度(A, B, C)の変更が可能。

- タイムスタンプ
    以下の種類がある。
    |---------------------------------+----------------|
    | 例                              | 意味           |
    |---------------------------------+----------------|
    | <2014-08-12 火>                 | 日付           |
    | <2014-08-12 火 18:05>           | 日付と時間     |
    | <2014-08-12 火 18:05-18:10>     | 日付と時間範囲 |
    | <2014-08-12 火>-<2014-08-13 水> | 日付範囲       |
    |---------------------------------+----------------|

    - 非活性化
        <2014-08-12 火>でなく、角括弧で[2014-08-12 火]とすると、
        アジェンダ等に表示されない非活性なタイムスタンプとなる。

    - 日の入力
        C-c .
        <2014-08-12 火>
    - 日時の入力
        C-u C-c .
        <2014-08-12 火 18:10>
    - DEADLINEの設定
        C-c C-d
        ** TODO
           DEADLINE: <2014-08-12 火>
    - SCHEDULEDの設定
        C-c C-s
        ** TODO
           SCHEDULED: <2014-08-12 火>
    - 日の設定/年月日時分の設定
        S-RIGHT(LEFT) / S-UP(DOWN)

## Tags

## Properties and columns

## Dates and times
### 計時
- 計時開始
    C-c C-x C-i
- 計時終了
    C-c C-x C-o
- 計時をキャンセル
    C-c C-x C-x
- 計時中のタスクに移動
    C-c C-x C-j
- 部分木の計時の合計を表示
    C-c C-x C-d
- 計時表示を終了
    C-c C-c

## Capture - Refile - Archive

## Agenda views
### アジェンダ

そのうちやる。
[[http://d.hatena.ne.jp/tamura70/20100208/org]]

## Markup for rich export
### 文字の装飾
- 太字
  *太字*
- 斜体
  /斜体/
- 下線
  _下線付き_
- 取消線
  +取消線+
- コード
  =コード=
- 等幅
  ~等幅~

## Exporting
### 出力
- C-c C-e
  あとは画面の表示に従うと作成できる。

### エクスポートオプション

- エクスポートオプション
    |-----------------+----------------|
    | キーワード      | 説明           |
    |-----------------+----------------|
    | #+TITLE:        | タイトル       |
    | #+AUTHOR:       | 著者名         |
    | #+DATE:         | 日付           |
    | #+EMAIL:        | メールアドレス |
    | #+DESCRIPTION:  | 説明           |
    | #+KEYWORD:      | キーワード     |
    | #+LANGUAGE:     | 言語           |
    | #+OPTIONS:      | オプション     |
    | #+LINK_UP:      | [UP]リンク     |
    | #+LINK_HOME:    | [HOME]リンク   |
    | #+LATEX_HEADER: | LaTeXヘッダ    |
    |-----------------+----------------|

- OPTIONS指定
    |------------+-------------------------------|
    | オプション | 説明                          |
    |------------+-------------------------------|
    | H:         | 見出しの深さ                  |
    | num:       | 章番号のオンオフ              |
    | toc:       | 目次のオンオフ、深さ          |
    | \n:        | 改行保持のオンオフ            |
    | ^:         | TeX風の上付下付記法のオンオフ |
    |------------+-------------------------------|

## Publishing

## Working with source code
### Structuer of code blocks
- format
  #+NAME: <name>
  #+BEGIN_SRC <language> <switches> <header arguments>
    <body>
  #+END_SRC

## Miscellaneaus

## Memo
### Sorting
- 
  org-sort, or "C-c ^".
  その後何を基準にソートするかminibufferで聞かれるので、答える。

### Latex
- Command
  - C-c C-x C-l : 数式画像のインライン表示
  - C-c C-c     : 終了
- 
  [[http://d.hatena.ne.jp/natsutan/20120721/1342838705][Emacsのorg-modeで数式をインライン表示する方法 - ぱたへね]]

### org-modeで図をかく
- [[http://misohena.jp/article/emacs_org_textfigures/][org-modeで図を書けるようにする]]
## Link
- [[http://orgmode.org/org.html][The Org Manual]]
- [[http://d.hatena.ne.jp/tamura70/20100203/org][Emacs org-modeを使ってみる:(1)インストール - 屯遁のパズルとプログラミングの日記]]
