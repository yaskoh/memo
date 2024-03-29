# Emacs-Lisp
## Manual
### Introduction
#### Caveats
#### Lisp History
#### Conventions
##### Some Terms
##### nil and t
##### Evaluation Notation
##### Printing Notation
##### Error Messages
##### Buffer Text Notation
##### Format of Descriptions
###### A Sample Function Description
###### A Sample Variable Description
#### Version Info
#### Acknowledgements
### Lisp Data Types
#### Printed Representation
- Objects are printed in hash notation, #< and >.
  Hash notation cannot be read, so the Lisp reader signals the error "invalid-read-sytax" whenever it encounters '#<'.
#### Comments
- ; Semicolon
  Semicolon starts a comment if it is not within a string or character contant.
#### Programming Tyes
##### Integer Type
- Numbers without fractional parts
  The range of values for an integer depends on the machine.
  The minimum range is -536,870,912 to 536,870,911 (30 bits; -2**29 to 2**29-1) but many machines provide a wider range.
##### Floating-Point Type
- Numbers with fractional parts and with a large range.
##### Character Type
- The representation of letters, numbers and control characters
###### Basic Char Syntax
###### General Escape Syntax
###### Ctl-Char Syntax
###### Meta-Char Syntax
###### Other Char Bits
##### Symbol Type
- A multi-use object that refers to a function, variable, or property list, and has a unique indentity.
##### Sequence Type
- Both lists and arrays are classified as sequences.
##### Cons Cell Type
- Cons cells, and lists (wihch are made from cons cells).
###### Box Diagrams
###### Dotted Pair Notation
###### Association List Type
##### Array Type
- Arrays include strings and vectors.
##### String Type
###### Syntax for Strings
###### Non-ASCII in Strings
###### Nonprinting Characters
###### Text Props and Strings
##### Char-Table Type
##### Bool-Vector Type
##### Hash Table Type
##### Function Type
##### Macro Type
##### Primitive Function Type
##### Byte-Code Type
##### Autoload Type
##### Finalizer Type
#### Editing Types
##### Buffer Type
- The basic object of editing
##### Marker Type
- A position in a buffer
- バッファ中の任意の文字に対して一を示す標識をつけることができる。
  整数と同じように利用することができる。
  マーク(C-@)もマーカーの一種。
##### Window Type
- Buffers are displayed in windows
##### Frame Type
- Windows subdivide frames
##### Terminal Type
- A terminal device displays frames
##### Window Configuration Type
- Recording the way a frame is subdivided.
##### Frame Configuration Type
- Recording the status of all frames
##### Process Type
- A subprocess of Emacs running on the underlying OS
##### Stream Type
- Receive or send characters.
##### Keymap Type
- What function a keeystroke invokes
##### Overlay Type
- How an overlay is represented
##### Font Type
- Fonts for displaying text
#### Circular Objects
- '#n=' and '#n#'
  
#### Type Predicates
##### Predicates
- atom
#### Equality Predicates
### Numbers
#### Integer Basics
#### Float Basics
#### Predicates on Numbers
#### Comparison of Numbers
#### Numeric Conversions
#### Numeric Conversions
#### Arithmetic Operations
#### Rounding Operations
#### Bitwise Operations
#### Math Functions
#### Random Numbers
### Strings and Characters
#### String Basics
#### Predicates for Strings
#### Creating Strings
#### Modifying Strings
#### Text Comparision
#### String Conversion
#### Formatting Strings
#### Case Conversion
#### Case Tables
### Lists
#### Cons Cells
#### List-related Predicates
#### List Elements
#### Building Lists
#### List Variables
#### Modifying Lists
##### Setcar
##### Setcdr
##### Rearrangement
#### Sets And Lists
#### Association Lists
#### Property Lists
##### Plists and Alists
##### Plist Access
### Sequences Arrays Vectors
#### Sequence Functions
#### Arrays
#### Array Functions
#### Vectors
#### Vector Functions
#### Char-Tables
#### Bool-Vectors
#### Rings
### Hash Tables
#### Creating Hash
#### Hash Access
#### Defining Hash
#### Other Hash
### Symbols
#### Symbol Components
#### Definitions
#### Creating Symbols
#### Symbol Properties
##### Symbol Plists
##### Standard Properties
### Evaluation
#### Intro Eval
#### Forms
##### Self-Evaluating forms
##### Symbol Forms
##### Classifying Lits
##### Function Indirection
##### Function Forms
##### Macro Forms
##### Special Forms
##### Autoloading
#### Quoting
#### Backquote
#### Eval
### Control Structures
#### Sequencing
#### Conditionals
##### Pattern matching case statement
#### Combining Conditions
#### Iteration
#### Generators
#### Nonlocal Exists
##### Catch and Throw
##### Examples of Catch
##### Errors
###### Signaling Errors
###### Processing of Errors
###### Handling Errors
###### Error Symbols
##### Cleanups
### Variables
### Functions
### Macros
### Customization
### Loading
### Byte Compilation
### Debugging
### Read and Print
### Minibuffers
### 20. Command Loop
#### 20.1 Command Overview
#### 20.12 Prefix Command Arguments
##### Function: prefix-numeric-value arg
##### Variable: current-prefix-arg
- This variable holds the raw prefix argument for the current command.
### Keymaps
### Modes
### Documentation
### Files
### Backups and Auto-Saving
### Buffers
### Windows
### Frames
### Positions
### Markers
### Text
### Non-ASCII Characters
### Searching and Matching
### Syntax Tables
### Abbrevs
### Processes
### Display
### System Interface
### Packaging
### Appendices
#### Antinews
#### GNUE Free Documentation License
#### GPL
#### Tips
#### GNU Emacs Internals
#### Standard Errors
#### Standard Keymaps
#### Standard Hooks
## Syntax
### Functions
#### C source code
##### built-in function
###### Etc
####### eq
- (eq OBJ1 OBJ2)
  Return t if the two args are the same Lisp object.

####### set
- (set SYMBOL NEWBAL)
  Set SYMBOL's value to NEWVAL, and return NEWVAL.

####### eval-buffer
- (eval-buffer &optional BUFFER PRINTFLAG FILENAME UNIBYTE DO-ALLOW-PRINT)
  Execute the current buffer as Lisp code.

####### put
- (put SYMBOL PROPNAME VALUE)
  Store SYMBOL's PROPNAME property with value VALUE.
  It can be retrieved with `(get SYMBOL PROPNAME)'.
####### defconst
- (defconst SYMBOL INITVALUE [DOCSTRING])
  Define SYMBOL as a constant variable.
  This declares that neither programs nor users should ever change the value.
  
####### defvar
- (defvar SYMBOL &optional INITVALUE DOCSTRING)
  Define SYMBOL as a variable, and return SYMBOL.
  setqと異なり、値が代入されるのはシンボルが未定義の時のみ。
  eval-defun(C-M-x)で評価することで、新しい値に定義し直すことが可能。

####### format
- (format STRING &rest OBJECTS)
  Format a string out of a format-string and arguments.
  The first argument is a format control string.
  The other arguments are substituted into it to make the result, a string.

####### funcall
- (funcall FUNCTION &rest ARGUMENTS)
  Call first argument as a function, passing remaining arguments to it.

####### message
- (message FORMAT-STRING &rest ARGS)
  Display a message at the bottom of the screen.

####### null
- (null OBJCET)
  Return t if OBJECT in nil.

####### require
- (require FEATURE &optional FILENAME NOERROR)
  If feature FEATURE is not loaded, load it from FILENAME.
  If FEATURE is not a member of the list "features", then the feature loaded; so load the file FILENAME.

####### provide
- (provide FEATURE &optional SUBFEATURES)
  Announce that FEATURE is a feature of the current Emacs.
  The optional argument SUBFEATURES should be a list of symbols listing particular subfeatures supported in this version of FEATURE.

####### kill-all-local-variables
- (kill-all-local-variables)
  Switch to Fundamental mode by killing current buffer's local variables.
  Most local variable bindings are eliminated so that the default values become effective once more.
####### standard-syntax-table
- (standard-syntax-table)
  Return the standard syntax table.
####### current-indentation
- (current-indentation)
  Return the indentation of the current line.

####### looking-at
- (looking-at REGEXP)
  Return t if text after point mathes regular expression REGEXP.
  
###### Map
####### use-local-map
- 
  Select KEYMAP as the local keymap.

####### make-sparse-keymap
- (make-sparse-keymap &optional STRING)
  Construct and return a new sparse keymap.
  
  In "mode tutorial",
  "If your keymap will have very few entries, then you may want to consider 'make-sparse-keypap' rather than 'make-keymap'
- 
  空のキーマップを作成。make-key-mapと異なりnilで埋められない（おそらく）。
  ex: (setq my-local-map (make-sparse-keymap))

####### make-key-map
- (make-keymap &optional STRING)
  Construct and return a new keymap, of the form (keymap CHARTABLE .ALIST).
  CHARTABLE is a char-table that holds the bindings for all characters without modifiers.
  All entries in in are initially nil, meaning "command undefined".

####### define-key
- (define-key KEYMAP KEY DEF)
  KEYMAP is a keymap.
  KEY is a string or a vector of symbols and characters.
- 
  キーマップを割り当てる
  (define-key my-local-map "h" 'backward-char)

####### symbol-function
- (symbol-function SYMBOL)
  Return SYMBOL's function definition. Error if that is valid.
- 
  関数の定義を出力する。
  ex: (symbol-funcion 'function)
###### Font
####### set-fontset-font
- (set-fontset-font NAME TARGET FONT-SPEC &optional FRAME ADD)
  Modify fontset NAME to use FONT-SPEC for TARGET cahracters.
  - NAME is a fontset name string, nil for the fontset of FRAME, or t for the default fontset.
  - TARGET maybe:
    - cons : (FROM . TO), where FROM and TO are characters.
    - a script name symbol
    - a charset
    - nil
  - FONT-SPEC may one of these:
    - A font-spec object
    - A cons (FAMILY . REGISTRY)
    - A font name string
    - nil, which explicitly specifies that there's no font for TARGET

###### Number Operand
####### +
####### -
####### *
####### /
####### %, mod
####### 1+
####### 1-
###### Math
####### float
- (float ARG)
  Return the floating point number equal to ARG.
####### round, fround
####### floor, ffloor
####### ceiling, fceiling
####### truncate, ftruncate
####### abs
####### numberp
####### integerp
####### floatp
###### 一般算術関数
random, max, min
sin, cos, tan, asin, acos, atan, expt, sqrt
exp, log, logb, log10 (指数関数、対数関数:底e,2,10）
logand, logior, lognot, logxor（ビット演算:積、和、否定、排他的論理和）
lsh, ash（論理シフト、算術シフト）

###### 相互変換
####### string-to-number
####### string-to-char
####### char-to-string
####### number-to-string
####### format
- (foramt STRING &rest OBJECTS)
  Format a string out of a formt-string and arguments.

- 
  %s(文字列), %d(整数), %o(8進数), %x(16進数), %c(文字コードに対する文字),
  %f(浮動小数点数), %S(S式), %%(%自身)

###### 文字列操作
####### concat
####### substring
- 
  (substring 文字列 開始位置 &optional 終了位置)

####### upcase, downcase
####### make-string
####### stringp, string=, string<
###### 便利
####### current-time-string
- (current-time-string &optional SPECIFIED-TIME)
  Return the current local time, as a human-readable string.
- 
  現在の日付時刻を「Fri Apr 08 10:16:00 2016」の形式の文字列で返す。

####### message
- 
  ミニバッファにメッセージを表示する。

####### this-command-keys
- 
  現在評価されている関数が起動するきっかけとなったキーコマンドを返す。

####### sleep-for
- 
  指定秒数だけ一時停止する。

####### sit-for
- 
  画面を書き直し、指定秒数だけ一時停止する。

####### ding

###### Hook
####### run-hooks
- (run-hooks &rest HOOKS)
  Run each hooks in HOOKS.
  Each argument should be a symbol, ahook variable.
  These symbols are processed in the order specified.
  If a hook symbol has a non-nil value, that value may be a function or a list of functions to be called to run the hook.
##### Interactive
###### goto-char
- (goto-char POSITION)
  Set point to POSITION, a number or marker.

#### byte-run
##### defun (macro)
- (defun NAME ARGLIST &optional DOCSTRING DECL &rest BODY)
  Define NAME as a function
- 
  関数定義
  (defun 関数名 (引数リスト *&optional, &rest)
     "説明文章"
     定義本体)
##### defmacro(macro)
- (defmacro NAME ARGLIST &optional DOCSTRING DECL &rest BODY)
  Define NAME as a macro.
  When the macro is called, as in (NAME ARGS...), the function (lambda ARGLIST BODY...) is applied to the list ARGS... as it appears in the expression,
  and the result should be a form to be evaluated instead of the original.

#### custom
##### defcustom(macro)
- (defcustom SYMBOL STANDARD DOC &rest ARGS)
  Declare SYMBOL as a customizable variable.
  SYMBOL is the variable name; it should not be quoted.
  STANDARD is an expression specifying the variable's standard value.
  It should not be quoted.

##### defgroup(macro)
- (defgroup SYMBOL MEMBERS DOC &rest ARGS)
  Declare SYMBOL as a customization group containing MEMBERS.
  SYMBOL does not need to be quoted.

#### eval
##### throw
- (throw TAG VALUE)
  Throw to the catch for TAG and return VALUE from it.
  Both TAG and VALUE are evalled.

- 
  throwされた場合にcatch式の評価がその値でただちに行われ、catch式を抜ける。

#### faces
##### set-face-attribute
- (set-face-attribute FACE FRAME &rest ARGS)
  Set attributes of FACE on FRAME from ARGS
  This function ovreries the face attributes specified by "FACE"'s face spec.
#### file
##### find-file
- find-file FILENAME &optional WILDCARDS)
  Edit file FILENAME.
  Switch to a buffer visiting file FILENAME, creating one if none already exists.
#### regexp-opt
##### regexp-opt
- (regexp-opt STRINGS &optional PAREN)
  Return a regexp to match a string in the list STRINGS.
  Each string should be unique in STRINGS and should not contain any regexps, quoted or not.

#### nadvice
##### remove-function
#### subr
##### error
- (error STRING &rest ARGS)
  Signal an error, making error emssage by passing all args to "format"
  In Emacs, the convention is that error messages start with a capital letter but *do not* end with period.
- 
  関数の評価をやめてコマンドループへ戻る。
##### when(macro)
- (when COND BODY...)
  If COND yields non-nil, do BODY, else return nil.
##### unless(macro)
- (unless COND BODY...)
  If COND yields nil, do BODY, else return nil.
  When COND yields nil, eval BODY forms sequentially and return value of last one, or nil if there are none.

##### add-hook
- (add-hook HOOK FUNCTION &optional APPEND LOCAL)
  Add to the value of HOOK the function FUNCTION.
  FUNCTION is not added if already present.
  FUNCTION is added (if necessary) at the beginning of the hook list 
  unless the optional argument APPEND is non-nil, in which case FUNCTION is added at the end.

- 
  
##### remove-hook
- (remove-hook HOOK FUNCTION &optional LOCAL)
  Remove from the value of HOOK the function FUNCTION.
  HOOK should be a symbol, and FUNCTION may be any valid function.
  If FUNCTION isn't the value of HOOK, or, if FUNCTION doesn't appear in the list of hooks to run in HOOK,then nothing is done.
##### add-to-list
- (add-to-list LIST-VAR ELEMENT &optional APPEND COMPARE-FN)
  This function has a compiler macro.
  Add ELEMENT to the value of LIST-VAR if it isn't htere yet.
  
##### not(alias)
- (not OBJECT)
  Return t if OBJECT is nil.
  alias for 'null'

#### sort
##### sort-lines
- (sort-lines REVERSE BEG END)
  Sort lines in region alphabetically
#### 移動系
・移動系
bobp, eobp
    beginning(end) of buffer
bolp, eolp
    beginning(end) of line
forward-char, backward-char
    １文字前方（後方）に進める
forward-line, next-line
    forward-lineは次の行の先頭に、
    next-lineは次の行のできる限り同じカラムになるように動かす
forward-sexp, backward-sexp
    S式(S-expression)
    M-C-f, M-C-b
point
mark
region-beginning, region-end
point-min, point-max
goto-char
save-excursion
    処理から抜けると、処理開始位置に戻ってくる
goto-line
count-lines
move-to-window-line
    画面上の指定行に移動する。つまり画面上で何行目、という位置に飛ぶ。
beginning-of-line, end-of-line
move-to-column
    桁位置の移動。
current-column

・検索移動系
search-forward, search-backward
    (search-forward 文字列 &optional 限界 エラー回避 回数)
word-search-forward, word-search-backward
    単語単位の検索、例えば"TeX"を検索した場合"LaTeX"は含まれない。
match-beginning, match-end
    マッチした文字列の先頭（終端）のポイント位置を得ることができる。
    正規表現と合わせて利用した場合、グループ番号を指定することで
skip-chars-forward, skip-chars-backward
    (skip-chars-forward "文字列" &optional 限界)
    列挙した文字列群をスキップする。

#### 正規表現
・メタキャラクター
    .[]?*+^$\
・\表現
    \(\), \|, \数字, \<\>, \w \W, \sC \SC

・正規表現検索
re-search-forward(backward)
    (re-search-forward 正規表現 &optional 限界 エラー回避 回数)
    正規表現にマッチする文字列を順(逆)方向に検索する。
string-match
    (string-match 正規表現 文字列 &optional 開始位置)
    "文字列"中に"正規表現"にマッチする部分があるか照合する。
    マッチする部分があった場合マッチする位置を返す。なかったらnil。
looking-at
    (looking-at 正規表現)
    ポイント位置からの文字列が指定した正規表現にマッチするか照合する。
char-after, char-before
    (char-after &optional ポイント値)
    "ポイント値"で指定した位置の文字コードを返す。
following-char, preceding-char
    現在のポイント位置（ポイント位置の直前）の文字コードを返す。
    ポイント値を省略した場合のchar-after(before)と同様の動き。
match-string, match-string-no-properties
    直前の検索で見つかったグループ番号の文字列を返す。
buffer-substring, buffer-substring-no-properties
    (buffer-substring 開始 終了)
save-match-data
    (save-match-data 本体)
    match-dataの内容を保存して"本体"を評価した後で、match-dataの内容を復帰する。

#### 編集系
・削除
(kill-はkill-ringに値が設定されるため、基本的にはプログラム中で使わない。)
delete-char(delete-backward-char)
    (delete-char 文字数 &optional killフラグ)
delete-region
    (delete-region 開始位置 終了位置)
kill-region
kill-line
erase-buffer
・挿入
insert-char
    (insert-char 文字 個数)
    "文字"を"個数"だけ挿入する。
self-insert-command
    押したキーそのものを挿入する。個数指定必要。
・置換
replace-match
    (replace-match 新文字列 &optional 大文字小文字固定 リテラル) 
    直前の検索関数でマッチした部分全体を新しい文字列に置き換える。
#### Hooks
##### run-hooks
##### run-hook-with-args
##### add-hook
##### remove-hook
##### make-local-hook
### Variables
#### C source code
##### features
##### default-tab-width
- 
  *** This variable is obsolete since 23.2. use 'tab-width' instead. ***

##### tab-width
- 
  Distance between tab stops, in columns.
  Automatically bocomes buffer-local when set.
  
#### files
##### auto-mode-alist
- 
  Alist of filename patterns vs corresponding major mode functions.
  Each element looks like (REGEXP . FUNCTION) or (REGEXP FUNCTION NON-NIL).
- 
  モードと拡張子の組、拡張子によって自動でモードを設定する。

#### font-lock
##### font-lock-builtin-face
##### font-lock-variable-name-face
##### font-lock-keyword-face
##### font-lock-constant-face
#### tmp
##### debug
      debug-on-error
      tになっている場合、backtraceを取得する。
### Comment
- ;
  重ねることでレベルを表すことをよく行う。
### EasyWay
#### Print
##### message
#### Var
- 
  変数は宣言をしなくても使えるが、defvarで変数宣言することでバイトコンパイラが文句を言わない。

##### defvar
- 初期化
  (defvar foo 1)
##### setq
- 数を代入
  (setq bar 10)
##### let
- ローカル変数
  ただしダイナミックスコープ
##### let*
- 直前のローカル変数代入の影響を受ける
- 例
  (let ((x (+ x 3))
        (y (+ x 2)))  ; 同時にバインドされるので、xは1
    (+ x y))          ; =>7
  (let* ((x (+ x 3))
         (y (+ x 2))) ; xは4となる
    (+ x y))          ; =>10
  
#### Comment
- ;
  セミコロンの数で使い分ける。
- 例
  - ;;;;
    主要な部分のヘッダ
  - ;;;
    関数定義の外側
  - ;;
    コメント、字下げに揃える
  - ;
    末尾の一言コメントなど

### Literal
- 整数 : 1234
- 小数 : 3.14
- 文字コード : ?c
- 8進表記 : ?\12
- 16進表記 : ?\x12
- N進表記 : #Nr44
  ただし36進まで。
  ex) #5r12 -> 5進の12(7)
      #12rAB -> 12進のAB(131
)
#### Meta character
##### \a
- ベル
##### \b
- バックスペース
##### \e
- ECS(1Bh)
##### \f
- フォームフィールド(C-l)
##### \n
- 改行(C-j)
##### \r
- 復帰(C-m)
##### \t
- タブ(C-i)
##### \001
- 8進数表記の文字コード
##### \C-a
- \C-を前置して、コントロール文字を表す
##### \M-a
- \M-を前置して、メタ文字を表す
##### \"
- "自身
##### \\
- \自身
### Emacs Lisp基礎文法最速マスター
- http://d.hatena.ne.jp/rubikitch/20100201/elispsyntax
- 
## Keybinds
### C-j : eval-print-last-sexp
### C-x C-e : eval-last-sexp
### C-M-x : eval-defun
### C-u C-M-x : (edebug)
### M-: : eval-expression
### C-x M-: : repeat-complex-command
### M-C-q : インデントを直す(lisp-intreaction)
### load-file
### eval-current-buffer
## Memo
### 関数名末尾のp
- predicate
  yes-or-no, true-or-falseで返す関数には、
  predicateの頭を取ってfunctionpやfunction-pなどとすることが多い。

### キーマップ
- 
  どのモードでも共通のキーマップはグローバルマップに、モード固有の設定はローカルマップに設定。

### インタラクティブ関数
- 
  キーボードで直接呼び出すことができる。
  ex: (interactive "sInput a:\nsInput b:)
      ↑"\n"までが一文で、プロンプトとして出力される。
       一文字目のsが文字列を引数として取ることを表している。

### hook フック
- 
  既存のプログラムから特定の場面で呼び出される関数を収めた変数。
  
#### Normal hook
- 
  引数なしで呼び出される関数のリスト。

#### Abnormal hook
- 
  
### 特殊形式
- 
  一部の引数を評価せずに処理するもの。
  厳密には関数と区別する。

### 名前の衝突の回避
- 
  名前空間が処理系全体で一つしかないので、パッケージを作る際はグローバル変数に必ずパッケージ固有の接頭辞をつけるようにする。

### 動的スコープ
- 
  プログラムのある時点でローカル変数が生まれると、その変数が消滅するまではプログラムのどの地点でもその変数への山椒が有効となる。

### 文字コードの表し方
- ?
  ?aで、aの文字コード97を表す。

### テキストをソートする
- 
  M-x sort-lines。
  C-u M-x sort-linesで逆順にソート。

### vector ベクター
- []を使ってベクター（配列）にアクセスできる。
  ただしキー指定以外ではほとんど使わない。
### Lexical Binding
- To use lexical binding, an Emacs-lisp source file must set a file-variable "lexical-binding" to t in the file header.
  https://www.emacswiki.org/emacs/LexicalBinding
     
## BookMemo_Tmp
### An Introduction to Programming in Emacs Lisp
### Mode tutorial
#### Basic
- set vars
  - hook
    (defvar wpdl-mode-hook nil)
  - keymap
    (defvar wpdl-mode-map
      (let ((map (make-keymap)))
        (define-key map "\C-j" 'newline-and-indent)
        map)
      "Keeymap for WPDL major mode")
#### regexp
- regexp-opt
  正規表現を引数から最適化して出力してくれる。
  
#### Link
- http://ichiroc.hatenablog.com/entry/2013/09/10/080525
  
## Link
- [[https://www.gnu.org/software/emacs/manual/elisp.html][GNU Emacs Lisp Reference Manual]]
- [[https://www.gnu.org/software/emacs/manual/eintr.html][An Introduction to Programming in Emacs Lisp]]
- [[http://d.hatena.ne.jp/rubikitch/20100201/elispsyntax][Emacs Lisp基礎文法最速マスター]]

- [[http://d.hatena.ne.jp/kiwanami/20100929/1285716364][Emacs Lisp が「書ける」ようになるまで - 技術日記＠kiwanami]]

### ありえるえりあ
- [[http://dev.ariel-networks.com/articles/workshop/emacs-lisp-basic/][Emacs Lisp勉強会(基礎編)]]
- [[http://dev.ariel-networks.com/Members/sugawara/emacs-lisp-52c95f374f1a-30c330d530a1306830a630a330f330a67de8/view][Emacs Lisp勉強会(バッファとウィンドウ編)]]

- [[http://dev.ariel-networks.com/wp/documents/aritcles/emacs][Software Design連載記事「Emacsのトラノマキ」の原稿]]
- [[http://dev.ariel-networks.com/articles/software-design-200802/][Software Design 2008年2月号 「Emacsマスターへの道」 原稿]]
- [[http://dev.ariel-networks.com/articles/][原稿・資料]]

