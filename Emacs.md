# Emacs
## Documents
### The Emacs Editor
- https://www.gnu.org/software/emacs/manual/html_node/emacs/index.html
#### Intro
#### Important General Concepts
##### Screen
##### User Input
##### Keys
##### Commands
##### Entering Emacs
##### Exiting
#### Fundamental Editing Commands
#### Important Text-Changing Commands
##### Search / 15 Searching and Replacement
###### Replace / 15.10 Replacement Commands
####### Regexp Replace / 15.10.2 Regexp Replacement
- \, : using Lisp expressions to calculate
- \& : stands for the entire match being replaced.
- \"d" : ("d" is digit, like 1, 2...) stands for whatever matched the "d"th parenthesized grouping grouping in regexp
- \# : refers to the count of replacements already made in this command, as a decimal number
- \? : replacement by hand each time
#### Major Structures of Emacs
#### Advanced Features
#### Recovery from Problems
#### Appendicies
### Emacs Lisp
- [[file:EmacsLisp.org][EmacsLisp.org]]
  (- https://www.gnu.org/software/emacs/manual/html_node/elisp/index.html)
## Packages
- [[file:Emacs_Packages.org][Emacs_Packages.org]]
## Language Settings
### Common Lisp
### Go
- [[https://www.emacswiki.org/emacs/GoLangMode][Go Lang Mode - EmacsWiki]]
- [[http://unknownplace.org/archives/golang-editing-with-emacs.html][EmacsでのGo言語編集環境 - unknownplace.org]]
## Functions
- 使いやすさのために、パッケージを超えてまとめる必要があれば行う。
  厳密なものはPackagesへ移行中
### File
#### dired
#### find-file
- C-x C-f
#### load-file
### Buffer
#### kill-buffer
- C-k
#### save-buffer
- C-x C-s
#### save-buffers-kill-terminal
#### switch-to-buffer
- C-x b
#### list-buffers
- C-x C-b
#### write-buffer
- C-x C-w
### Window
#### delete-window
#### delete-other-window
#### split-window-vertically
#### split-window-horizontally
### Moving Point
#### forward-char
- (C-f), C-t
#### backward-char
- C-b
#### previous-line
#### next-line
#### forward-word
#### backward-word
#### beginning-of-line
- C-a
#### end-of-line
- C-e
#### forward-sentence
- M-e
#### backward-sentence
- M-a
#### scroll-up
- C-v
#### scroll-down
- M-v
#### forward-page
- C-x ]
#### backward-page
- C-x [
#### goto-line
- M-g
### Editing
#### delete-char
- C-d
#### delete-backward-char
- C-h
#### kill-word
- M-d
#### kill-line
- C-k
#### yank
- C-y
#### kill-region
- C-w
#### set-mark-command
- C-Space
#### universal argument
- C-u
  次に入力するコマンドを4回実行する
#### quoted-insert
### Search
#### isearh-forward
- C-s
#### isearch-backward
- C-r
#### isearch-yank-word
- C-s C-w
#### re-search-forward
- C-M-s
#### re-search-backward
- C-M-r
#### query-replace-regexp
- C-M-%
##### Reply
- y
  replace on match
- n
  skip to next
- RET / q
  exit
- . (period)
  replace one match and exit
- , (comma)
  replace but not move point
- C-r
  enter recursive edit (C-M-c to get out again)
- C-w
  delete match and recursive edit
- C-l
  clear the screen, redisplay, and offer same replacement again
- !
  replace all remaining matches
- ^
  to move point back to previous match
- E
  to edit the replacement string
- Y
  (Multi-buffer)replace all remaining matches in all remaining buffers with no more questions.
- N
  (Multi-buffer)skip to the next buffer ithout replacing remaining matches in the current buffer.
### Macro
#### start-kbd-macro
- C-x (, <F3>
#### end-kbd-macro
- C-x ), <F4>
#### call-last-kbd-macro
- C-x e
#### kbd-macro-query
- C-x q
#### edit-kdb-macro
- C-x C-k e
#### name-last-kbd-macro
- C-x C-k n
#### insert-kbd-maccro
#### apply-macro-to-region-lines
### Shell
#### shell
#### term
#### eshell

## Features
### Help
### Register
### Regular Expression
- https://www.emacswiki.org/emacs/RegularExpression

#### Operation
- Lispリーダと正規処理表現処理器の二段階で読み込まれるため、
  正規表現を文字列として渡すには、\\と2つ重ねて記述する必要がある。
- 
  "\\b" -> (Lispリーダ, \\⇒\) -> "\b" -> (正規表現処理機, \b)
#### Syntax
##### Special Characters
- special : . * + ? ^ $ \ [
- between brackets : ] - ^

###### normal
####### .
- any character (but new line)
####### *
####### +
####### ?
####### ^
####### $
####### [...]
- どれか1つにマッチする。
####### [^..]
####### [a-z]
####### \
- prevents interpretation of following special char
####### \|
####### \w
- word constituent
####### \b
- word boundary
####### \sc
- character with c syntax (e.g. \s- for whitespace char)
####### \( \)
####### \< \>
- start/end of word
####### \_< \_>
- start/end of symbol
####### \` \'
- start/end of buffer/string
####### \1
- string matched by the first group
####### \n
- string matched by the nth group
####### \{3\}
####### \{3,\}
####### \{3,6\}
####### \=
- match succeeds if it is located at poit
###### non-greedy
####### *?
####### +?
####### ??
###### not match
####### \W
- not word
####### \B
- not word boundary
####### \Sc
###### category
- 
  Use "C-u C-x =" to display the category of the character under the cursor.

####### \ca
- ascii character
####### \Ca
- non-ascii character (newline included)
####### \cl
- latin character
####### cg
- greek character
###### syntax class
- see the syntax table by typing C-h s (but I have changed the key binding of help.)
####### \s-
####### \sw
####### \s_
####### \s.
####### \s(
####### \s)
####### \s"
####### \s\
####### \s/
####### \s$
####### \s'
####### \s<
####### \s>
####### \s!
####### \s|
###### syntax class between bracket
####### [:digit:]
####### [:alpha:]
####### [:alnum:]
####### [:alnum:]
####### [:upper:]
####### [:space:]
####### [:xdigit:]
####### [:cntrl:]
####### [:ascii:]
### Keyboard Macros
- start
 C-x (
- end
  C-x )
- execute (most recent)
  C-x e
- execute, then start recording
  C-u C-x (
## Structure
### Screen
#### Point
#### Echo Area
#### Mode Line
#### Menu Bar
### Files
### Buffers
### Windows
### Frames
### International
## Command line
### Options
#### -d display, --display=display
#### -t device, --terminal=device
#### -nw, --no-windows
#### -batch, --batch
#### -q, --no-init-file
- 個人の初期化ファイルをロードしない
#### --no-site-file
#### -u user, --user=user
#### --debug-init
#### --unibyte
#### --multibyte
## Glossary
### alist
- Assosiation List
### Special Forms
- A special form is a primitive function specially marked so that its argumets are not all evaluated.
  
### SEXP
- S-expression, S式
### バッファーローカル変数
- バッファーごとに別の値を取れる変数。
  make-local-variable関数を使うと、通常の変数をバファーローカルにできる。
## Memo
### ToDo
- emacs-lisp
  - elisp講座
  - るびきちlisp
  - manual読む
  - macro (on lisp)
- autoload, package.el, eval-after-load
  http://keens.github.io/blog/2013/12/13/dot-emacs-clean-up/
- eshell周り
- etc
  - magit, trump
  - 有用パッケージ探す、入れる

### 変数設定
- defconst, defvar, setq, defcustom
  defcostomは無条件に変数を初期化するが、defvarは変数が空である場合のみ初期化する。
  変数の使い方を制限することはしないため、主には好みの問題。
  ユーザカスタマイズを目的とする変数を宣言するにはdefcustomを使う。
### shells on emacs
#### shell
- M-x shell
  標準シェル。
  タブ補完などが効かない。

#### ansi-term(term)
- M-x term (M-x ansi-term)
  
#### eshell
- M-x eshell
  
#### multi-term
- 
  別途インストールが必要。
### defcustom カスタマイズ定義
- 
  https://www.gnu.org/software/emacs/manual/html_node/eintr/defcustom.html
  http://www.bookshelf.jp/texi/elisp-manual-20-2.5-jp/elisp_14.html
### advice アドバイス
- 関数の既存の定義に追加ができる。
  各関数は、個別に定義した複数のアドバイス断片を持ち、明示的に有効・無効にできる。
  
  本来の処理の前後に処理を追加するもの。

#### advice.el
- 旧advice.elでは、defadviceにbefore, after, aroundを指定して追加をし、
  ad-activate/ad-deactivateで有効化/無効化できる。
  ad-do-itやad-return-valueなどを駆使して利用する。

  https://www.gnu.org/software/emacs/manual/html_node/elisp/Advising-Functions.html#Advising-Functions
  http://www.bookshelf.jp/texi/elisp-manual-20-2.5-jp/elisp_17.html

#### nadvice.el
- advice-addとadvice-removeを使う。
  aroundでは、元の関数が引数として渡されるため、ad-do-itの代わりにapplyを使えばよい。
  また、ad-return-valueを設定せずともそのままアドバイス関数の返り値が関数の返り値となる。

- アドバイス
  - :before
  - :after
  - :around
  - :override
  - :filter-return
  - :filter-args
  - :before-while
  - :before-until
  - :after-while
  - :after-until

    http://emacs.rubikitch.com/nadvice/
### backquote バッククォート
- 基本的にはquoteと同じ。
  - ,
    内側にある特別な印","は、値が定数でないことを表す。バッククォートはリスト構造の中の","を評価し値で置き換える。
  - ,@ (splice)
    評価結果を結果となるリストに繋ぎ合わせる(splice)。結果となるリストの他の要素と同じレベルとなる。
    
- http://www.bookshelf.jp/texi/elisp-manual-20-2.5-jp/elisp_13.html#SEC176
### Major Mode作成手順
- [[http://www.bookshelf.jp/texi/elisp-manual-20-2.5-jp/elisp_23.html][22. メジャーモードとマイナーモード - GNU Emacs Lispリファレンスマニュアル (2.5/20.3 日本語)]]
#### 例1
- モード用のキーマップを作る
  - make-sparse-keyで空のキーマップを作る
  - define-keyでキーと関数を指定
- major-mode 用のコマンドを作る
  - 変数 major-mode にそのモードを表すシンボルを設定
  - 変数 mode-name にそのモードの名前を設定
  - 'use-local-map' でモード用のキーマップを設定

#### 例2 (やさしいEmacs-Lisp講座 / 本)
- モード名を設定する
  (setq major-mode 'my-mode)
  (setq mode-name "まいもーど")
- 使用するキーマップを設定する
  (setq my-local-map (make-sparse-keymap))
  (define-key my-local-map "h" 'backward-char)
- 動作に必要な変数を設定する
  (use-local-map my-local-map)
- 必要な関数を定義する

#### 継承
- define-derived-modeを利用する。
#### マイナーモード
- define-minor-modeを利用する
##### Minor-modeの挙動
- [[http://www.kaichan.info/blog/2013-02-10-minor-mode-behavior.html][define-minor-mode で定義されたマイナーモードの挙動 - 備忘録]]
### Keymap
- order
  1. the keymap specified by the "keymap" property
  2. the keymaps of enabled minor modes
  3. the current buffer's local keymap
  4. the global keymap
  [[https://www.gnu.org/software/emacs/manual/html_node/elisp/Active-Keymaps.html#Active-Keymaps][21.7 Active Keymaps - Emacs Lisp (Emacs version 25.1)]]
- order
  1. overriding-terminal-local-map : terminal
  2. overriding-local-map : major/minor-mode
  3. text-property 'keymap : text
  4. emulation-mode-map-alists : minor-mode
  5. minor-mode-overriding-map-alist : major-mode
  6. minor-mode-map-alist : minor-mode
  7. local-map (major-mode-map) : major-mode
  8. global-map : global
  9. local-function-key-map : file
  [[http://emacs.g.hatena.ne.jp/kiwanami/20110606/1307385847][キーマップの lookup 順序について - はてなグループEmacs@kiwanami]]
### キー設定
#### Alias
- C-m : "RET"
- C-i : "TAB"
- C-[ : "ESC"
#### Key Sequence指定
##### string
- ex: "\C-xa"
##### vector
- ex: [?\C-x ?a]
##### kbd
- ex: (kbd "C-x a")  ; => "\^Xa"
##### Link
- [[http://d.hatena.ne.jp/tama_sh/20110206/1296976730][emacsでのキー入力の表現方法 - My Emaps]]
- [[http://ergoemacs.org/emacs/keyboard_shortcuts.html][Emacs: How to Define Keys]]
#### <return> and RET
- "<return>" is the Return key while emacs runs in a graphical user interface.
- "RET" is the Return key while emacs runs in a terminal.
  "RET" is also equivalent to "C-m"
- [[http://ergoemacs.org/emacs/emacs_key_notation_return_vs_RET.html][Emacs's Key Notation: What's the difference between "<return>" and "RET"?]]

#### remap
- あるコマンドに割り当てられているキー、という形でキー指定が可能。
  既存のキーを拡張したコマンドを当てる場合などに有用。
  ex) (add-hook 'c++-mode-hook '(lambda () (local-set-key [remap newline] 'newline-and-indent)))
  
#### Key macro
- キー設定関数で、コマンドの代わりにキーを指定することもできる。
  ex) (global-set-key "\C-l" "\C-f")
  C-lを押すとC-fのキーが押されたこととなる。
#### keyboard-translate
- モードに関係なくキー変換を行うことができる。
  引数はベクター表記の中の文字。低次元層に働く関数なので、結構強力。
  ex) (keyboard-translat ?\C-l ?\C-f)
#### Link
- [[http://ergoemacs.org/emacs/emacs_keys_index.html][Emacs Keybinding, Keyboard, Articles Index]]
  
### Literal リテラル
#### 数値リテラル
##### 数値 1234
##### 小数 3.14
##### 文字コード ?a
- aの文字コード
##### 8進数 ?\12
- 8進数表記の整数
##### 16進数 ?\x12
- 16進数表記の整数
##### NN進数 #NNr
- NN進数
  ex: #5r40→20, #30remacs→11943388
### 置換時の改行
- 
  ^J(C-q C-j)
### Windowsバイナリ
- 
  公式バイナリは、日本語入力時にIMEが使えなくて不便(24.5時点)
- NTEmacsバイナリ（パッチ付）
  2016/4/19時点ではこの簡易版パッチのものを使っている。
  [[http://cha.la.coocan.jp/doc/NTEmacs.html][NTEmacs / Emacs for Windows]]
- Gnu pack
  [[http://d.hatena.ne.jp/ksugita0510/][gnupackの開発メモ]]

### Macのbackslash
- 
  Mac上では、¥はbackslashと同一でなく、YEN SIGN(UTF8 0xC2 0xA5)、となってしまう。
  \(ASCII 0x5c)をemacs上で出すことは難しいので、keymapに設定すると良い。
  ちなみにemacs以外のMac上の画面では、Option+¥で\が入力可能。

  ->mac上IMEで、デフォルトを\とするか¥とするか選択できた。

- 
  http://qiita.com/aKenjiKato/items/4ac7d9b100bdce0b8920
  http://www.glamenv-septzen.net/view/1119

### 数値のビット幅
- 
  (expt 2 n)で扱える最大のnがビット幅。超えると0が帰ってくる。
  手持ちのemacsは64bit版のため、60で正、61で負の値が返ってきたあと、62以降は0となる。

### 並び替え
- org-sort(C-c ^)
### インデント
- C-M-\, indent-region
### TeXの設定
- MacでTeXを使うために、PATH及びexec-pathを設定する必要がある。
  [[http://emacs.stackexchange.com/questions/18534/orgmode-mac-el-capitan-cant-find-latex][Orgmode + Mac (el capitan): can't find latex - (emacs)]]
### 検索機能
- [[http://dev.ariel-networks.com/articles/emacs/part1/][「Emacsのトラノマキ」 連載第一回 「Emacsの検索機能を使いこなす」 - ありえるえりあ]]

- M-x grep
- lgrep
- rgrep
- grep-find

#### Windowsでのgrep/find
- Windowsでうまくgrepができない/結果がヒットしない
- [[https://www.emacswiki.org/emacs/GrepMode][Grep Mode - EmacsWiki]]

### Debug デバッグ
#### print(message)
- message関数を使う。
  sit-forやy-or-n-pも利用
#### backtrace
- (setq debug-on-error t)
  事前にdebug-on-errorをtにしておく必要がある。
  backtraceバッファでeを押すとその時点での変数の値を評価できる。
#### edebug
- C-u C-M-x(edebug-defun)を評価したい関数に対して適用して、その後関数を実行する。
#### Link
- [[http://dev.ariel-networks.com/articles/software-design-200802/elisp-debug/][Emacs Lisp デバッグ - ありえるえりあ]]
- [[http://d.hatena.ne.jp/rubikitch/20101116/edebug][Emacs Lispのソースコードデバッガ edebug を使う]]
- [[http://www.bookshelf.jp/texi/emacs-lisp-intro-jp/eintro_19.html][17.デバッグ]]
### server is unsafe
- directoryの所有者をAdministratorから利用ユーザに変更する。
  http://stackoverflow.com/questions/885793/emacs-error-when-calling-server-start
### 読み込み・保存が重い場合
#### vc処理を無効化
- (setq vc-handled-backends nil)
  https://www.rainyman.net/nest/?p=1117
### 折り返し表示の変更
- 関数"toggle-truncate-lines"で切り替えられる。
  制御自体は変数"truncate-lines"で行う。
### コメントアウト/解除
- コメントアウト
  - C-c C-c : comment-region
  - M-; : comment-dwim
- コメント解除
  - uncomment-region
- トグル
  - comment-or-uncomment-region
### 連番
- C-u C-x r N
  https://qiita.com/kwappa/items/639b40ef0e18170edf43
- (reg-exp) \,(1+ \#)
  http://lambda1.blogspot.com/2012/04/emacs-emacs-replace-regexp-m-x-replace.html
### Emacs Client
- WindowsのGUIでEmacsを使う場合、emacsclientwを使うとよい。
  規定のプログラムとして指定すると、ダブルクリックですでに開いているemacsの上でファイルが開いてくれる。
- CUIだとemacsclientをemacs serverと組み合わせることになるはず。
### WindowsでEmacsを使う
- いつも通りEmacsのzip回答やインストーラ実行を試みると、作成元不明のためセキュリティ的にインストールできなかった。
  そのため、scoopを使ってインストールを実行。
- [[https://emacs-jp.github.io/tips/emacs-for-windows][GNU Emacs for Windows再入門 - Emacs JP]]
  - ・管理者ユーザで接続、ポリシーを変更
    Set-ExecutionPolicy RemoteSigned -scope CurrentUser
    ・scoopのインストール
    Invoke-Expression (New-Object System.Net.WebClient).DownloadString('https://get.scoop.sh')
    ・bucketの追加に先立ってgitが必要
    scoop install git
    ・bucketを追加
    scoop bucket add extras
    ・scoopをupdate
    scoop update
    ・emacsのインストール
    scoop install emacs

### 変数を確認する。
- M-x describe-variables RET "vars-to-see"

## Error対応
### 28.1へのバージョンアップ / 2022/5
#### Cannot find libgccjit
- リンク
- https://misohena.jp/blog/2022-04-06-use-native-compilation-on-emacs-28-1-for-windows.html
- https://misohena.jp/blog/2022-04-11-use-native-compilation-on-emacs-28-1-for-windows-2.html

- やったこと
  - scoopでmsys2導入
  - msys2でpacman -S mingw-w64-x86_64-libgccjitでlibgccjitを導入
  - emacsのbinフォルダにlibgccjit、その他必要なリンクファイルをlib/gccフォルダを作って配置。

#### Cannot open load file, ~~ build/initloader/initloader

## Link
### Manual
- [[https://www.gnu.org/software/emacs/][GNU Emacs]]
- [[http://www.gnu.org/software/emacs/manual/html_mono/emacs.html][GNU Emacs manual]]
- [[https://ayatakesi.github.io/][emacs 日本語マニュアル]]
- [[https://www.emacswiki.org/emacs/SiteMap][EmacsWiki]]
- [[http://d.hatena.ne.jp/o0cocoron0o/20100424/1272116442][Emacs 基本コマンド一覧 - Cocoron's memo]]
- [[http://emacsrocks.com/][emacsrocks]]

- [[http://yohshiy.blog.fc2.com/blog-category-30.html][Top - 環境設定のための Emacs Lisp 入門 - プログラマーズ雑記帳]]

### Tutorial
- [[http://ergoemacs.org/emacs/emacs.html][Practical Emacs Tutorial - Practial Emacs Quick Start]]
### Settings
- [[https://github.com/kawabata/dotfiles/blob/master/.emacs.d/init.el][dotfiles/.emacs.d/init.el (kawabata/dotfiles) - github]]
- [[http://www.clear-code.com/blog/2012/3/20.html][Emacs実践入門 - おすすめEmacs設定2012 - ククログ]]
- [[http://yohshiy.blog.fc2.com/blog-entry-324.html][Emacs のおすすめ基本設定 - プログラマーズ雑記帳]]
- [[http://dev.classmethod.jp/devenv/emacs-settings/][あまり有名でないEmacsのオススメ設定 - Developers.IO]]
- [[http://th.nao.ac.jp/MEMBER/zenitani/elisp-j.html][Emacs Lisp TIPS]]

### Startup
- [[https://gist.github.com/zk-phi/9935048][setup.el で安全・爆速な init.el を書く - zk-phi/setup_description_ja.org]]

