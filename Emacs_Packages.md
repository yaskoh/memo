# Emacs Packages
## System Packages
- 24.5時点
  - /emacs/share/emacs/24.5/lisp(win)
### Keybind(Global)
#### special
##### C-c
##### C-h
##### C-x
##### C-u
#### default
##### C-a : beginning-of-line
##### C-b : backward-char
##### C-d : delete-char
##### C-e : end-of-line
##### C-f : forward-char
##### C-g : keyboard-quit
##### C-k : kill-line
##### C-l : recenter-top-bottom
##### C-n : next-line
##### C-p : previous-line
##### C-q : quoted-insert
- 特殊文字の入力
###### C-j : 改行
##### C-r : isearch-backward
##### C-s : isearch-forward
###### C-u C-s : regexp-mode
- C-uに限らず、一つ目の引数を取った場合にregexpに。
###### C-s C-w : isearch-yank-word
##### C-u : universal-argument
##### C-v : scroll-up
##### C-w : kill-region
##### C-y : yank
##### C-[ : backward-page
##### C-] : forward-page
##### C-\ : toggle-input-method
- IME on/off
##### C-Space : set-mark-command
##### C-x b : switch-to-buffer
##### C-x e : call-last-kbd-macro
##### C-x k : kill-buffer
##### C-x ( : start-kbd-macro
##### C-x ) : end-kbd-macro
##### C-x ] : forward-page
##### C-x [ : backward-page
##### C-x 0 : delete-window
##### C-x 1 : delete-other-window
##### C-x 2 : split-window-vertically
##### C-x 3 : split-window-horizontally
##### C-x C-b : list-buffers
##### C-x C-c : save-buffers-kill-terminal
##### C-x C-f : find-file
##### C-x C-k e : edit-kdb-macro
##### C-x C-k n : name-last-kbd-macro
##### C-x C-s : save-buffer
##### C-x C-w : write-buffer
##### C-x C-j : dired
##### C-x RET f : set-bufer-file-coding-system
- Set character code
##### C-M-s : re-search-forward
##### C-M-r : re-search-backward
##### C-M-\ : indent-region
##### C-M-% : query-replace-regexp
##### M-a : backward-sentence
##### M-b : backward-word
##### M-e : forward-sentence
##### M-f : forward-word
##### M-g g : goto-line
##### M-g M-g : goto-line
##### M-g TAB : move-to-column
##### M-l : downcase-word
##### M-v : scroll-down
##### M-x : execute-extended-command
- コマンドを入力して実行

##### M-< : beginning-of-buffer
##### M-> : end-of-buffer
##### M-/ : dabbrev-expand
##### M-: : eval-expression
##### <f1> : (help-command)
##### <help>
###### (help-command)
- help-for-help-internal
###### c KEYS
###### f FUNCTION
- describe-function
  Display documentation for the given function.
###### F COMMAND
- Show the on-line manual's section that describes the command.
###### k KEYS
- Display the full documentation for the key sequence.
###### K KEYS
- Show the on-line manual's section for the command bound to KEYS.
###### m
- Display documentation of current minor modes and current major mode, including their special commands.
###### t
- Tutorial
###### v VARIABLE
- Display hte given variable's documentation and value.
#### edited
##### C-h : delete-backward-char
##### C-j : newline
##### C-m : newline-and-indent
##### C-o : other-window
- 引数を設定した分のウィンドウ数移動する。
  "C-c -1 C-o"とすると一つ戻る。
##### C-t : forward-char
##### C-x o : other-frame
##### C-x ? : help-command
- 
  <f1>を使ってください

##### C-z : undo
##### C-/ : transpose-chars
##### M-t : forward-word
##### M-r : replace-string
##### M-z : transpose-words
#### original
##### C-h : (help-command)
##### C-j
##### C-m
##### C-o
##### C-t
##### C-x o
##### C-z
##### C-/
##### M-t
##### M-r
##### M-z

### C source code
- [[file:Emacs_Packages_Builtin.org][Emacs_Packages_Builtin.org]]
### emacs-lisp\
#### advice
- 再定義なしに挙動を変更する。
  24.4以降ではnadvice.elを使う。

##### Functions
###### ad-activate
###### ad-activate-all
- (ad-activate-all &optional COMPILE)
  Activate all currently advised functions.
- すべての関数を活性化する
###### ad-activate-regexp
- (ad-activate-regexp REGEXP &optional COMPILE)
  Activate functions with an advice name containing a REGEXP match.
###### ad-deactivate
###### ad-deactivate-all
###### ad-disable-advice
###### ad-disable-regexp
###### ad-enable-advice
###### ad-enable-regexp
###### ad-start-advice
###### ad-stop-advice
###### ad-update
- (ad-update FUNCTION &optional COMPILE)
  Update the advised definition of FUNCTION if its advice is active.
###### ad-update-regexp
###### ad-unadvice
- (ad-unadvice FUNCTION)
  Deactivate FUNCTION and then remove all its advice information.
##### Macros
###### defadvice
- (defadvice FUNCTION ARGS &rest BODY)
  Define a piece of advice for FUNCTION (a symbol).
  
- (defadvice FUNCTION (CLASS NAME [POSITION] [ARGLIST] FLAG...)
    [DOCSTRING] [INTERACTIVE-FORM]
    BODY...)

  - FUNCTION ::= Name of the function to be advised.
  - CLASS ::= "before" | "around" | "after" | "activation" | "deactivation"
  - NAME ::= Non-nil symbol that names this piece of advice.
  - POSITION ::=  "first" | "last" | NUMBER.
  - ARGLIST
  - FLAG ::= "protect" | "disable" | "activate" | "compile" | "preactive"
  - DOCSTRING
  - INTERACTIVE-FORM
  - BODY

- Variables : 
  - ad-return-value :
    after, aroundの場合、この値に設定した値が戻り値となる。
  - ad-do-it :
    aroundの場合に元の関数を実行する場所を指定する。
    
#### byte-run
##### Functions
###### eval-when-compile
- (eval-when-compile &rest BODY)
  Like "progn", but evaluates the body at compile time if you're compiling.
##### Macros
###### defmacro
- (defmacro NAME ARGLIST &optional DOCSTRING DECL &rest BODY)
  Define NAME as a macro.
  When the macro is called, as in (NAME ARGS...),
  the function (labmda ARGLIST BODY...) is applied to the list ARGS...
  as it appears in the epxression,
  and the result should be a form to be evaluated instead of the original.
###### defun
- (defun NAME ARGLIST &optional DOCSTRING DECL &rest BODY... )
  Define NAME as function.
  
#### cl
##### Alias
###### loop
- (loop CLAUSE)
  alias for "cl-loop"
##### Functions
###### cl-loop
- (cl-loop CLAUSE...)
  The Common Lisp "loop" macro.
#### derived
##### Functions
###### define-derived-mode
- (define-derived-mode CHILD PARENT NAME &optional DOCSTRING &rest BODY)
  Create a new mode as a variant of an existing mode.
#### easy-mmode
##### Macros
###### define-minor-mode
- (define-minor-mode MODE DOC &optional INIT-VALUE LIGHTER KEYMAP &rest BODY)
  Define a new minor mode MODE.
#### edebug
##### Alias
###### edebug-defun
- (edebug-defun)
  alias for "edebug-eval-top-level-form"
###### eval-defun
- (eval-defun EDEBUG-IT)
  alias for "edebu-eval-defun"
##### Functions
###### edebug
- (edebug &optional ARG-MODE &rest ARGS)
  Replacement for "debug".
###### edebug-eval-defun
- (edebug-eval-defun EDEBUG-IT)
  Evaluate the top-level form containing point, or after point.
  
###### edebug-eval-top-level-form
- (edebug-eval-top-level-form)
  Evaluate the top level form print is in, stepping through with Edebug.
##### Keybind
###### edebug-mode
####### SPC : edebug-step-mode
####### ? : edebug-help
####### a : abort-recursive-edit
####### B : edebug-next-breakpoint
- ポイント位置以降に設定されているブレークポイントに移動する。
####### b : edebug-set-breakpoint
- ポイント位置にブレークポイントを設定する
####### C : edebug-Continue-fast-mode
- 「高速continue mode」に移行する。ブレークポイントでedebugバッファの再表示をしながら評価を継続する
####### c : edebug-continue-mode
- 「continue mode」に移行する。ブレークポイントで1秒ずつ停止しながら評価を継続する。
####### e : edebug-eval-expression
- Edebugの外側の環境でeval-expressionを行う。
####### f : edebug-forward-sexp
- 現在の評価ポイントからS式一つ分評価ポイントを進め、得られた値を身にバッファに表示する
####### G : edebug-Go-nonstop-mode
- 一切のブレークポイントを無視して最後まで評価する
####### g : edebug-go-mode
- 次のブレークポイントまで実行
####### h : edebug-goto-mode
- カーソル位置まで実行
####### i : edebug-step-in
- 直後の関数に入る
####### o : edebug-step-out
- 現在の評価ポイントが属しているS式の最後まで評価する
####### p : edebug-bounce-point
- 現在走行中の関数が指しているバッファを一定時間停止する
####### q : top-level
- edebugを抜ける
####### r : edebug-previous-result
- 最後に評価したものの返却値をミニバッファに再表示する
####### S : edebug-stop
- goモード、continueモード、traceモードで継続実行中のEdebugを止める。
####### t : edebug-trace-mode
- trace modeに移行する。
####### T : edebug-Trace-fast-mode
- 「高速trace mode」に移行する。tと同じだが、1秒間の停止をしない。
####### u : edebug-unset-breakpoint
- ブレークポイントを削除
####### w : edebug-where
- ポイントを現在の評価ポイントに移動する
####### x : edebug-set-conditional-breakpoint
- 条件ブレークを設定する。"Condition:"というプロンプトが出てくるので、条件をS式で入力する。

#### find-func
##### find-function
- (find-function FUNCTION)
  Find the definition of the FUNCTION near point.
- describe-functionと異なり、ソースの関数定義に飛ぶ。

#### lisp
##### Functions
###### backward-sexp (C-M-b, C-M-left)
- (backward-sexp &optional ARG)
  Move backward across one balanced expression (sexp).
###### forward-sexp (C-M-f, C-M-right)
- (forward-sexp &optional ARG)
  Move forward across one balanced expression (sexp).
#### lisp-mode
##### Functions
###### emacs-lisp-mode
- (emacs-lisp-mode)
  major mode for editing Lisp code ot run in Emacs.
###### eval-defun (C-M-x)
- (eval-defun EDEBUG-IT)
  Evaluate the top-level form containing point, or after point.
###### eval-print-last-sexp (C-j)
- (eval-print-last-sexp &optional EVAL-LAST-SEXP-ARG-INTERNAL)
  Evaluate sexp before point; print value into current buffer.
###### eval-last-sexp (C-x C-e)
- (eval-last-sexp EVAL-LAST-SEXP-ARG-INTERNAL)
  Evaluate sexp before point; print value in the echo area.
###### indent-sexp
###### kill-sexp (C-M-k)
- (kill-sexp &optional ARG)
  Kill the sexp (balanced expression) following point.
###### lisp-interaction-mode
- (lisp-interaction-mode)
  Major mode for typing and evaluating Lisp forms.
##### Keybinds
###### tmp
####### C-j : eval-print-last-sexp
####### C-x C-e : eval-last-sexp
####### C-M-x : eval-defun
####### C-M-k : kill-sexp
####### C-M-q : indent-sexp
#### nadvice
##### Functions
###### advice-add
- (advice-add SYMBOL WHERE FUNCTION &option PROPS)
  Like "add-function" but for the function named SYMBOL.
  Contrary to "add-function", this will properly handel tha cases 
  where SYMBOL is defeined as macro, alias, command, ...

- 引数に関数名、場所、アドバイス関数名を取る。

###### advice-remove
- (advice-remove SYMBOL FUNCTION)
  Like "remove-function" but for the function named SYMBOL.
  Contrary to "remove-function", this also works when SYMBOL is a macro
  or an autoload and it preserves "fboundp".

#### package
##### Functions
###### describe-package (C-h P)
- (describe-package PACKAGE)
  Display the full documentation of PACKAGE (a symbol)
  
###### list-packages
- (ilst-packages &option NO-FETTH)
  Display a list of packages.
- 用法
  1. インストールしたいパッケージの上で"i"を押す
  2. 選択し終わったら"x"を押す
###### package-initialize
- (package-initialize &optional NO-ACTIVATE)
  Load Emacs Lisp packages, and activate them.
  The variable "package-load-list" controles which packages to load.
###### package-install
- (package-install PKG)
  install the package PKG.
###### package-refresh-contents
- (package-refresh-contents)
  Download the ELPA archive description if needed.
##### Variables
###### package-load-list
- List of packages for "package-initialize" to load.
###### package-archives
- An alist of archives from which to fetch.
  The default value points to the GNU Emacs package repository.
##### Link
- [[http://emacs-jp.github.io/packages/package-management/package-el.html][package.el - Emacs JP]]

#### re-builder
##### re-builder
- (re-builder)
  Construct a regexp interactively.
##### reb-change-target-buffer (C-c C-b)
- (reb-change-target-buffer BUF)
  Change the target buffer and display it in the target window.
##### reb-quit (C-c C-q)
- (reb-quit)
  Quit the RE Bulider mode.
##### reb-copy (C-c C-w)
- Copy current RE into the kill ring for later insertion.
##### reb-change-syntax (C-c TAB)
- (reb-changne-syntax &optional SYNTAX)
  Changne the syntax used by the RE Bulider.

##### reb-toggle-case (C-c C-c)
##### reb-enter-subexp-mode (C-c C-e)
##### reb-prev-match (C-c C-r)
##### reb-next-match (C-c C-s)
##### reb-force-update (C-c C-u)
##### reb-copy (C-c C-w)
### emmulation\
#### cua-base
##### Functions
###### cua-set-mark / C-SPC, C-@
- (cua-set-mark &optional ARG)
  Set mark at where point is, clear mark, or jump to mark.
### eshell\
#### em-alias
##### Functions
##### Variables
###### eshell-command-aliases-list
- A list of command aliases currently defined by the user.
#### em-hist
##### Variables
###### eshell-hist-ignoredups
- If non-nil, don't add input matching the last on the input ring.
#### em-dirs
##### Functions
###### eshell/pwd
- (eshell/pwd &rest ARGS)
  Change output from "pwd" to be cleaner.
#### em-prompt
##### Variables
###### eshell-prompt-function
- A function that returns the Eshell prompt string.
###### eshell-prompt-regexp
- A regexp which fully matches your eshell prompt.
  it affects how eshell will interpret the lines that arpe passed to it.
#### eshell
##### Functions
###### eshell
- (eshell &optional ARG)
  Create an interactive Eshell buffer.
  A numeric prefix arg (as in `C-u 3 M-x eshell RET') switches to the session with that number.
### international\
#### mule-cmds
##### toggle-input-method (C-\)
- (toggle-input-method &optoinal ARG INTERACTIVE)
  Enable or disable multilingual text input method for the curret buffer.
##### set-language-environment LANGUAGE-NAME)
- (set-language-environment LANGUAGE-NAME)
  Set up multilingual environment for using LANGUAGE-NAME.
### net\
#### eww
- web broweser.
  it is part of the Emacs 24.4.

- [[https://lars.ingebrigtsen.no/2013/06/16/eww/][eww - Random Thoughts]]

#### tramp
- TRAMP(Transparent Remote Access, Multiple Protocols)
  winであまりうまくいっていない
- Link
  [[https://www.emacswiki.org/emacs/TrampMode][Tramp Mode - EmacsWiki]]
  [[http://yo.eki.do/notes/tramp-mode][Emacs:まだターミナルで消耗してるの？ - 葉月夜堂]]

### nxml\
#### nxml-mode
- be included in Emacs 23 and after.
##### Functions
###### nxml-balanced-close-start-tag-block (C-c C-b)
- (nxml-balanced-close-start-tag-block)
  Close the start-tag before point with ">" and insert a balancing end-tag.
- 数行下(block形式)にend-tagでxmlのstart-tagの末尾">"を挿入する
###### nxml-balanced-close-start-tag-inline (C-c C-i)
- (nxml-balanced-close-start-tag-inline)
  Close the start-tag before point with ">" and insert a balancing end-tag.
- 同行にend-tagと、xmlのstart-tagの末尾">"を挿入する。
###### nxml-complete
###### nxml-electric-slash (/)
- (nxml-electric-slash ARG)
  Insert a slash.
###### nxml-finish-element (C-c C-f, C-c /, C-c ])
- (nxml-finish-element)
  Fininsh the current element by inserting an end-tag.
###### nxml-insert-xml-declaration (C-c C-x)
- (nxml-insert-xml-declaration)
  Insert an XML declaration at the beginning of buffer.
- 現在カーソルのあるレベルのエンドタグを挿入
###### nxml-show-all (C-c C-o C-a)
- (nxml-show-all)
  Show all elements in the buffer normally.
###### nxml-hide-all-text-content (C-c C-o C-t)
- (nxml-hide-all-text-content)
  Hide all text content in the buffer.
##### Keybinds
###### C-c / : nxml-finish-element
###### C-c ] : nxml-finish-element
###### C-c C-b : nxml-balanced-close-start-tag-block
###### C-c C-d : nxml-dynamic-markup-word
###### C-c C-f : nxml-finish-element
###### C-c C-i : nxml-balanced-close-start-tag-inline
###### C-c C-x : nxml-insert-xml-declaration
###### C-M-d : nxml-down-element
###### C-M-n : nxml-forward-element
###### C-M-p : nxml-backward-element
###### C-M-u : nxml-backward-up-element
###### C-c C-o C-a : nxml-show-all
###### C-c C-o C-t : nxml-hide-all-text-content
###### tmp
####### C-c C-d : nxml-dynamic-markup-word
####### C-c RET : nxml-split-element
####### C-c C-u : nxml-insert-named-char
####### C-c C-x : nxml-insert-xml-declaration
####### M-h : nxml-mark-paragraph
####### M-{ : nxml-backward-paragraph
####### M-} : nxml-forward-paragraph
####### C-c C-o C-c : nxml-hide-direct-text-content
####### C-c C-o C-d : nxml-hide-subheadings
####### C-c C-o C-e : nxml-show-direct-text-content
####### C-c C-o C-i : nxml-show-direct-subheadings
####### C-c C-o C-k : nxml-show-subheadings
####### C-c C-o C-l : nxml-hide-text-content
####### C-c C-o C-o : nxml-hide-other
####### C-c C-o C-r : nxml-refresh-outline
####### C-c C-o C-s : nxml-show
##### Variables
###### nxml-attribute-indent
- Indentation for the attributes of an element relative to the start-tag.
###### nxml-child-indent
- Indentation for the children of an element relative to the start-tag.
###### nxml-slash-auto-complete-flag
- Non-nil means typing a slash automatically completes the end-tag.
  This is used by `nxml-electric-slash'.
##### Link
- [[http://www.thaiopensource.com/nxml-mode/][nXML mode]]
- [[https://www.emacswiki.org/emacs/NxmlMode][Nxml Mode - Emacs Wiki]]
#### rng-valid
- real-time validation of XML using RELAX NG
##### Keybinds
###### tmp
####### C-c C-n : rng-next-error
####### C-c C-v : rng-validate-mode
####### C-c C-s C-a : rng-auto-set-schema-and-validate
####### C-c C-s C-f : rng-set-schema-file-and-validate
####### C-c C-s C-l : rng-save-schema-location
####### C-c C-s C-t : rng-set-document-type-and-validate
####### C-c C-s C-w : rng-what-schema
### org\
#### org
##### Functions
###### org-cycle (<TAB> @org-mode)
- (org-cycle &optional ARG)
###### org-sort (C-c ^ @org-mode)
###### org-preview-latex-fragment (C-c C-x C-l @org-mode)
- (org-preview-latex-fragment &optional SUBTREE)
- Preview the LaTex fragment at point, or all locally or globally.
##### Keybinds
###### C-c ^ : org-sort
###### <TAB> : org-cycle
### progmodes\
#### ada-mode
#### bat-mode
#### cc-cmds
##### Functions
###### c-electric-delete
- (c-electric-delete ARG)
  Delets preceding or following character or whitespace.
#### cc-mode
#### cpp
#### hideshow
##### Functions
###### hs-minor-mode
- (hs-minor-mode &optional ARG)
  Minor mode to selectively hide/show code and comment blocks.
###### hs-hide-all
###### hs-show-all
###### hs-hide-block
###### hs-show-block
###### hs-hide-level
###### hs-toggle-hiding
#### flymake
#### js
#### python
#### ruby-mode
#### scheme
#### sh-script
##### Alias
###### shell-script-mode
- alias for "sh-mode"
- (shell-script-mode)
##### Functions
###### sh-mode
##### Keybinds
###### C-c C-c : sh-case
- case statement
###### C-c C-d : sh-cd-here
###### C-c C-f : sh-for
- for loop
###### C-c C-i : sh-if
- if statement
###### C-c C-l : sh-indexed-loop
- indexed loop from 1 to n
###### C-c C-o : sh-while-getopts
- while getopts loop
###### C-c C-r : sh-repeat
- repeat loop
###### C-c C-s : sh-select
- select loop
###### C-c C-u : sh-until
- until loop
###### C-c C-w : sh-while
- while loop
###### C-c ( : sh-function
- function definition
###### C-c + : sh-add
###### C-c = : sh-set-indent
#### sql
### term\
### textmodes\
#### fill
##### Functions
###### fill-paragraph
- (fill-paragraph &optional JUSTIFY REGION)
  Fill paragraph at or after point.
### url\
#### url
##### Functions
###### url-retrieve-synchronously
- (url-retrieve-synchronously URL &optional SILENT INHIBIT-COOKIES)
  Retrieve URL synchronously.
### vc\
#### diff
#### ediff
### apropos
#### apropos
- (apropos PATTERN &optional DO-ALL)
  Show all meaningful Lisp symbols whose names match PATTERN.
  Symbols are shown if they are defined as functions, veriables, or faces, or if they have nonempty property lists.

#### apropos-documentation (F1 d)
- (apropos-documentation PATTERN &optional DO-ALL)
  Show symbols whose documentation cotains matches for PATTERN
- 関数名に加えて説明文章も検索対象に加わる。
### bindings
#### Functions
#### Variables
##### minor-mode-alist
- Alist saying how to show minor modes in the mode line.
### compile
#### Functions
##### compile
- (compile COMMAND &optional COMINT)
  Compile the program including the current buffer.
##### compilation-window-height
- Number of lines in a compilation window.
  
### custom
#### Functions
##### custom-set-variables
- (custom-set-variables &rest ARGS)
  Install user customizations of variable values specified in ARGS.
  These settings are registered as theme "user".
  The arguments should each be a list of the form :
    (SYMBOL EXP [NOW [REQUEST [COMMENT]]])
##### user-variable-p
- (user-variable-p VARIABLE)
  Return non-nil if VARIABLE is a customizable variable.
#### Macros
##### defcustom
- (defcustom SYMBOL STANDARD DOC &rest ARGS)
  Declare SYMBOL as a customizable variable.
  SYMBOL is the variable name.
  STANDARD is an expression specifying the variable's standard value.
  It is evaluated once by "defcustom", and the value is assigned to SYMBOL if the variable is unbound.
  
  This macro uses "devar" as a subroutine, which also marks the variable as "special",
  so that it is always dynamically bound even when "lexical-binding" is t.
  
  The remeining arguments should have the form [KEYWORD VALUE]...

- ARGS keywords
  - :type
    VALUE should be a widget type for editing the symbol's value
  - :options
  - :initialize
  - :set
  - :require
  - :set-after
  - :risky
  - :safe
  - :group
    VALUE should be a customization group.
    Add SYMBOL (or FACE with "defface") to that group.
  - :link
  - :version
  - :package-version
  - :tag
  - :load

- ユーザが編集可能な変数を宣言する。
##### defface
- (defface FACE SPEC DOC &rest ARGS)
  Declare FACE as a customizable face that defaultts to SPEC.
  FACE does not need to be quoted.
### cus-edit
#### Variables
##### custom-file
- File used for storing customization information.
### dabbrev
#### Functions
##### dabbrev-expand (M-/)
- (dabbrev-expand ARG)
  Expand previous word "dynamically".
  Expand to the most recent, preceding word for which this is a prefix.

### dired
#### Functions
##### dired
- (dired DIRENAME &optional SWITCHES)
  "Edit" directory DIRNAME --delete, rename, print, etc.
#### Keybinds
##### dired
###### R : dired-do-rename
###### f
### env
#### Functions
##### setenv
- (setenv VARIABLE &optional VALUE SUBSTITUTE-ENV-VARS)
  Set the value of the environment variable named VARIABLE to VALUE.
  
### files
#### Functions
##### abbreviate-file-name
- (abbreviate-file-name FILENAME)
  Return a version of FILENAME shortened using "directory-abbrev-alist".
  This also substitutes "~" for the user's home directory and removes automounter prefixes.
##### basic-save-buffer
- (basic-save-buffer)
  Save the current buffer in its visited file, if it has been modified.
##### file-name-extension
- (file-name-extension FILENAME &optional PERIOD)
  Return FILENAME's final "extension".
##### file-name-sans-extension
- (file-name-sans-extension FILENAME)
  Return FILENAME sans final "extension"
##### find-file (C-x C-f)
- (find-file FILENAME &optional WILDCARDS)
  Edit file FILENAME.
##### load-file
- (load-file FILE)
  Load the Lisp file named FILE.
#### Variables
##### auto-mode-alist
- 
  Alist of filename patterns vs corresponding major mode functions.
  Each element looks like (REGEXP . FUNCTION) or (REGEXP FUNCTION NON-NIL).

##### backup-directory-alist
- Alist of filename patterns and backup directory names.
##### directory-abbrev-alist
- Alist of abbreviations for file directories.
  A list of elements of the form (FROM . TO), each meaning to replace FROM with TO when it appears in a directory name.
##### make-backup-files
- Non-nil means make a backup of a file the first time it is saved.
  This can be done by renaming the file or by copying.
##### visible-bell
- Non-nil means try to flash the frame to represent a bell.
##### write-file-hooks
- List of functions to be called before writing out a buffer to a file.
  
- ファイルを書き込む直前に呼び出されるフックを指定する。
### frame
#### Functions
##### blink-cursor-mode
- (blink-cursor-mode &otoinal ARG)
  Toggle cursor blinking (Blink Cursor mode).
### help
#### Functions
##### help
- (help)
  an alias for `help-for-help-internal`
##### describe-bindings (C-h b)
- 
  show key-bindings list

##### describe-key (C-h k key)
- 
  show key bindings that you will press

##### describe-key-briefly (C-h c key)
- 
  Print the name of the function KEY invokes.
##### describe-minor-mode
- (describe-minor-mode MINOR-MODE)
  Display documentation of a minor mode given as MINOR-MODE.
##### describe-mode (C-h m)
- (describe-mode &optional BUFFER)
  Display documentation of current major mode and minor mode
- 
  現在のメジャーモードの説明

##### describe-function (C-h f)
- (describe-function FUNCTION)

##### describe-variable (C-h v)
- 
  Display the full documentation of VARIABLE (a symbol).
  Returns the documentation as a string, also.

##### help-with-tutorial (C-h t)
- 
  Emacsの対話型チュートリアルに入る

##### view-lossage (C-h l)
- 
  これまでに打鍵した最後の100文字を表示する
### hexl
#### Functions
##### hexl-mode
- (hexl-mode &optional ARG)
##### hexl-mode-exit
##### hexl-insert-decimal-char (C-M-d)
##### hexl-insert-octal-char (C-M-o)
##### hexl-insert-hex-char (C-M-x)
##### hexl-insert-hex-string
- (hex-insert-hex-string STR ARG)
  Insert hexadecimal string STR at point ARG times.
#### Keybinds
##### C-M-d : hexl-insert-decimal-char
##### C-M-o : hexl-insert-octal-char
##### C-M-x : hexl-insert-hex-char
### ielm
- Inferior Emacs Lisp Mode
  this acts like an intreactive Lisp interpreter.
  real little REPL.

#### Functions
##### ielm
- (ielm)
  Interactively evaluate Emacs Lisp expresions.
### image-file
#### Functions
##### auto-image-file-mode
- (auto-image-file-mode &optional ARG)
  Toggle visiting of image files as image (Auto Image File mode).
### indent
#### Functions
##### indent-for-tab-command (C-i)
- (indent-for-tab-command &optional ARG)
  Indent the current line or region, or insert a tab, as appropriate.
##### indent-region (C-M-\)
- (indent-region START END &optional COLUMN)
  Indent each nonblank line in the region.
#### Variables
##### tab-stop-list
- List of tab stop positions used by "tab-to-tab-stop"
### info
#### Functions
##### info
- (info &optional FILE_OR_NODE BUFFER)
  the documentation browser.
  FILE-OR-NODE specifies the file to examine;
  
##### info-emacs-manual
- (info-emacs-manual)
  Display the Emacs manual in Info mode.
### info-look
#### Functions
##### info-lookup-symbol (C-h S)
- (ifo-lookup-symbol SYMBOL &optional MODE)
  Display the definition of SYMBOL, as found in the relevant manual.
### isearch
#### Functions
##### isearch-delete-char
- (isearch-delete-char)
  Discard last input item and move point back.
##### isearch-backward (C-r)
- (isearch-backward &optional REGEXP-P NO-RECURSIVE-EDIT)
  Do incremental search backward.
##### isearch-forward
- (isearch-forward &optiona REGEXP-P NO-RECURSIVE-EDIT)
  Do incremental search forward.
###### Memo
- C-w : カーソル後続の文字列を取り込む。繰り返すと範囲が広がる。
- M-c : case sensitive <-> insensitive
- M-e : 検索文字列をミニバッファで修正
- M-r : 正規表現による検索、取りやめ
  
##### word-search-backward
- (word-search-backward STRING &optional BOUND NOERROR COUNT)
  Search backward from point for STRING, ignoring differences in punctuation.
##### word-search-forward
- (word-search-forward STRING &optional BOUND NOERROR COUNT)
  Search forward from point for STRING, ignoring differences in punctuation.
### jka-cmpr-hook
#### Functions
##### auto-compression-mode
- (auto-compression-mode &optional ARG)
  Toggle Auto Compression mode.
### linum
#### Functions
##### global-linum-mode
- (global-linum-mode &optional ARG)
  Toggle Linum mode in all buffers.
##### linum-mode
- (linum-mode &optional ARG)
  Toggle display of line numbers in the left margin.
### menu-bar
#### Functions
##### menu-bar-mode
- (menu-bar-mode &optional ARG)
  Toggle display of a menu bar on each frame (Menu Bar mode)
### minibuffer
#### Functions
##### completion-at-point
- (completion-at-point)
  Perform completion on the text around point.
##### read-file-name
- (read-file-name PROMPT &optoinal DIR DEFAULT-FILENAME MUSTMATCH INITIAIL PREDICATE)
  Read file name, prompting with PROMPT and completing in directory DIR.
  The return value is not expanded -- call "expand-file-name" yourself.
#### Keybind
##### M-p, up : previous-history-element
##### M-n, down : next-history-element
##### M-r : previous-matching-history-element
##### M-s : next-matching-history-element
##### C-M-i : completion-at-point
#### Variables
##### insert-default-directory
- Non-nil means when reading a filename start with default dir in minibuffer.
##### read-file-name-completion-ignore-case
- Non-nil means when reading a file name completion ignores case.
### newcomment
#### Functions
##### comment-region
- (comment-region BEG END &optional ARG)
##### comment-or-uncomment-region
- (comment-or-uncomment-region BEG END &optional ARG)
##### uncomment-region
- (uncomment-region BEG END &optional ARG)
### outline
#### Functions
##### outline-mode
- (outline-mode)
### paren
#### Variables
##### show-paren-style
- Style used when showing a matching paren.
- Value
  - parenthesis
  - expression
  - mixed
### profiler
#### Functions
##### profiler-start
- (profiler-start MODE)
  Start/restart profilers.
  MODE can be one of "cpu", "mem" or "cpu+mem".

##### profiler-stop
##### profiler-report
##### profiler-reset
### rect
#### Functions
##### rectangle-number-lines (C-x r N, C-u C-x r N)
- (rectangle-number-lines START END START-AT &optional FORMAT)
- Insert numbers in front of region-rectangle.
- 連番を矩形選択された箇所に挿入する。
  前置引数(C-u)を付けて起動すると、各種パラメータをinteractiveに聞いてくれる。
#### KeyBindings
##### C-x r N : rectangle-number-lines
### replace
#### Functions
##### replace-string (M-r)
- (replace-string FROM-STRING TO-STRING &optional DELIMITED STRAT END BACKWARD)
  Replace occurrences of FROM-STRING with TO-STRING.
##### replace-regexp
- (replace-regexp REGEXP TO-STRING &optional DELIMITED START END BACKWARD)
  Replace things after point matching REGEXP with TO-STRING.
### server
#### Functions
##### (server-running-p &optional NAME)
      Test whether server NAME is running.
### simple
#### Functions
##### beginning-of-buffer (M-<, C-home)
- (beginning-of-buffer &optional ARG)
  Move point to the beginning of the buffer.
  With numeric arg N, put point N/10 of the way from the beginning.
- マーク位置を変更してしまうため、プログラムでは利用しない。代わりに(goto-char (point-min))などを使う。
##### column-number-mode
- (column-number-mode &optional ARG)
  Toggle column number display in the mode line.
##### delete-backward-char
- (delete-backward-char N &optional KILLFLAG)
  Delete the previous N characters (following if N is negative).
##### end-of-buffer (M->, C-end)
- (end-of-buffer &optional ARG)
  Move point to the end of the buffer.
  With numeric arg N, put point N/10 of the way from the end.
##### eval-expression (M-:)
- (eval-expression EXP &optional INSERT-VALUE)
  Evaluate EXP and print value in the echo area.
##### fundamental-mode
- (fundamental-mode)
  Major mode not specialized for anything in particular.
##### keyboard-quit (C-g)
- (keyboard-quit)
  Signal a "quit" condition.

##### kill-line
- (kill-line &optional ARG)
  Kill the rest of the current line; if no nonblanks there, kill thru newline.
##### kill-region
- (kill-region BEG END &optional REGION)
  Kill ("cut") text between point and mark.
- Kill-ringを変更するため、Emacs-Lisp中からは利用しない。
##### move-end-of-line
- (move-end-of-line ARG)
  Move point to end of current line as displayed.
##### next-line (C-n)
- (next-line &optoinal ARG TRY-VSCROLL)
  Move cursor vertically down ARG lines.
- goal-columnの制御などが含まれているため、プログラムとして使用する場合はforward-lineを用いる。
##### previous-line (C-p)
- (previous-line &optional ARG TRY-VSCROLL)
  Move cursor vertically up ARG lines.
##### read-quoted-char
- (read-quoted-char &optoinal PROMPT)
  Like "read-char", but do not allow quitting.
  Also, if the first character read is an octal digit,
  we read any number of octal digits and return the specified character code.
- 読み込んだ最初の文字が0-7の場合はもう2桁読み、3桁の8進数にしてその値に対応するコードを返す。
##### repeat-complex-command (C-x M-:)
- (repeat-complex-command ARG)
  Edit and re-evaluate last complex command, or ARGth from last.
##### toggle-truncate-lines
- (toggle-truncate-lines &optional ARG)
  Toggle turncating of long lines for the current buffer.
  When truncating is off, long lines are folded.
#### Variables
##### column-number-mode
- Non-nil if Column-Number mode is enabled.
##### eval-expression-print-length
- Value for "print-length" while printing value in "eval-expression".
  
##### next-line-add-enwlines
- If non-nil, "next-line" inserts newline to avoid "end of buffer" error.
### sort
#### Functions
##### delete-duplicate-lines
- (delete-duplicate-lines BEG END &optional REVERSE ADJACENT KEEP-BLANKS INTERACTIVE)
  Delece all but one copy of any identical lines in the region
### startup
#### Functions
##### normal-top-levevl-add-subdirs-to-load-path
- (normal-top-levevl-add-subdirs-to-load-path)
  Add all subdirectories of "default-directory" to "load-path"
#### Variables
##### after-init-hook
- Normal hook run after initializing the Emacs session.
  It is run after Emacs loads the init file, "default" library,
  the abbrevs file, and additional Lisp packages (if any),
  and setting the value of "after-init-time".
### subr
#### Alias
##### int-to-string
- (int-to-string NUMBER)
  alias for "number-to-string"
##### not
- alias for "null"
  (not OBJECT)
##### store-match-data
- 
  alias for "set-match-data"
##### string=
- (string= S1 S2)
  alias for "string-equal"
  Return t if two strings have identical contents.

##### string<
- 
  alias for "string-lessp"
##### string-to-int
- (string-to-int STRING &optional BASE)
  alias for "string-to-number"
##### (obsolete)
###### eval-current-buffer
- alias for "eval-buffer"
  obsolete since 22.1. use "eval-buffer".
#### Functions
##### add-hook
- (add-hook HOOK FUNCTION &optional APPEND LOCAL)
  Add to the value of HOOK the function FUNCTION.
  FUNCTION is not added if already present.

##### add-to-list
- (add-to-list LIST-VAR ELEMENT &optional APPEND COMPARE-FN)
  This function has a compiler macro.
  Add ELEMENT to the value of LIST-VAR if it isn't there yet.
##### error
- (error STRING &rest ARGS)
  Signal a error, making error message by passing all args to "format".
  
##### eval-after-load
- (eval-after-load FILE FORM)
  Arrange that if FILE is loaded, FORM will be run immediately afterwards.
  If FILE is already loaded, evaluate FORM right now.
##### kbd
- (kdb KEYS)
  Convert KEYS to the internal Emacs key representation.
##### keyboard-translate
- (keyboard-translate FROM TO)
  Translate character FROM to TO on the current terminal.
##### last
- (last LIST &optional N)
  Return the last link of LIST. Its car is the last element.
##### local-set-key
- (local-set-key KEY COMMAND)
  Give KEY a local binding as COMMAND.
  
  呼び出した際に使われているキーマップに対してキーを設定する。
##### locate-library
- (locate-library LIBRARY &optional NOSUFFIX PATH INTERACTIVE-CALL)
  Show the precise file name of Emacs library LIBRARY.
##### global-set-key
- (global-set-key KEY COMMAND)
  Give KEY a global binding as COMMAND.
  
  same as (define-key global-map KEY COMMAND).
##### match-string
- (match-string NUM &optional STRING)
  Return string of text matched by last search.
##### match-string-no-properties
- (match-string-no-properties NUM &optional STRING)
  Return string of text matched by last search, without text properties.
##### save-match-data
- (save-match-data &rest BODY)
  Execute the BODY forms, restoring the global value of the match data.
  The value returned is the value of the last form in BODY.
- match-dataの内容を保存して"BODY"を評価した後内容を復帰する。
##### set-match-data
- (set-match-data LIST &optional RESEAT)
  Set internal data on last search match from elements of LIST.
##### sit-for
- (sit-for SECONDS &optional NODISP)
  Redisplay, then wait for SECONDS seconds. Stop when input is available.
##### string-equal
- (string-equal S1 S2)
  Return t if two strings have identical contents.
##### string-lessp
- (string-lessp S1 S2)
  Return t if first arg string is less than second in lexicographic order.
##### y-or-n-p
- (y-or-n-p PROMPT)
  Ask user a "y or n" question. Return t if answer is "y".
  PROMPT is the string to display to ask the question.
#### Macros
##### dolist
- (dolist (VAR LIST [RESULT]) BODY...)
  Evaluate BODY with VAR bound to each car from LIST, in turn.
  Then evaluate RESULT to get return value, default nil.
##### dotimes
- (dotimes (VAR COUNT [RESULT]) BODY...)
  Loop a certain number of times.
##### kbd
- (kbd KEYS)
  Convert KEYS to the internal Emacs key representation.
##### lambda
- (lambda ARGS [DOCSTRING] [INTERACTIVE] BODY)
  Return a lambda expression.

##### push
- (push NEWELT PLACE)
  Add NEWELT to the list stored in the generalized variable PLACE.
##### unless
- (unless COND BODY...)
  If COND yields nil, do BODY, else return nil.
##### when
- (when COND BODY...)
  If COND yields non-nil, do BODY, else return nil.
#### Variables
##### user-emacs-directory
- Directory beneath which additional per-user Emacs-specific files are placed.
### time
#### Functions
##### dispaly-time
- (display-time)
  Enable display of time, load level, and mail flag in mode lines.
### tutorial
#### Functions
##### help-with-tutorial
- (help-with-tutorial &optional ARG DONT-ASK-FOR-REVERT)
- Command : (C-h t)
  Select the Emacs learn-by-doing tutorial.
### version
#### Variables
##### emacs-major-version
##### emacs-minor-version
### window
#### Functions
##### display-buffer
- (display-buffer BUFFER-OR-NAME &optional ACTION FRAME)
  Display BUFFER-OR-NAME in some window, without selecting it.
##### pop-to-buffer
- (pop-to-buffer BUFFER &optional ACTION NORECORD)
  Select buffer BUFFER in some window, preferably a different one.
##### switch-to-buffer
- (switch-to-buffer BUFFER-OR-NAME &optional NORECORD FORCE-SAME-WINDOW)
  Display buffer BUFFER-OR-NAME in teh selected window.
##### switch-to-next-buffer
- (switch-to-next-buffer &optoinal WINDOW)
  In WINDOW switch to next buffer.
##### switch-to-prev-buffer
- (switch-to-prev-buffer &optional WINDOW BURY-OR-KILL)
  WINDOW switch to previous buffer.
### emacs 25
#### let-alist
- http://elpa.gnu.org/packages/let-alist.html
#### seq
## Other Packages
### auto-complete-config
#### Functions
##### auto-complete-config
- (ac-config-default)
### auto-save-buffers
- http://0xcc.net/misc/auto-save/

### bind-key
- [[http://emacs.rubikitch.com/bind-key/][bind-key.el : define-keyを直接書くのは時代遅れ！Emacsの重鎮が行っているスタイリッシュキー割り当て管理術！ - るびきち「新生日刊Emacs」]]
#### Functions
##### describe-personal-keybindings
- (describe-personal-keybindings)
  Display all the personal keybindings defined by 'bind-key'.
#### Macros
##### bind-key
- (bind-key KEY-NAME COMMAND &optional KEYMAP PREDICATE)
  Bind KEY-NAME to COMMAND in KEYMAP ("global-map" if not passed).
##### bind-key*
- (bind-key* KEY-NAME COMMAND &optional PREDICATE)
  Similar to "bind-key", but overrides any mode-specific bindings.
##### bind-keys
- (bind-keys &rest ARGS)
  Bind multiple keys at once.
##### bind-keys*
- (bind-keys* &rest ARGS)

### cl-lib
- GNU Emacs Common Lisp Emulation
#### About
- 
  The CL package adds a number of Common Lisp functions and control structures to Emacs Lisp.
  While not a 100% complete implementation of Common Lisp, it ads enough functionality to make Emacs Lisp programming significantly more convenient.
  
#### Link
- [[http://www.gnu.org/software/emacs/manual/html_mono/cl.html][GNU Emacs Common Lisp Emulation]]
### company
- 入力補完
#### Vairables
##### company-selection-wrap-around
- If enabled, selecting item before first or after last wraps around.
#### Link
- [[http://qiita.com/syohex/items/8d21d7422f14e9b53b17][auto-completeユーザのための company-modeの設定 - Qiita]]
### dash
### el-get
#### Functions
#### Link
- [[https://github.com/dimitri/el-get][dimitri/el-get - github]]a
- [[http://tarao.hatenablog.com/entry/20150221/1424518030][Caskはもう古い、これからはEl-Get - いまどきのEmacsパッケージ管理 - 貳佰伍拾陸夜日記]]
### el-get-build
#### Variables
##### el-get-install-info
- install-info path
### emmet-mode
#### KeyBindings
##### default
###### C-M-right : emmet-next-edit-point
###### C-M-left : emmet-prev-edit-point
###### C-c w : emmet-wrap-with-markup
##### edited
###### C-' : emmet-expand-line
##### original
###### C-j : emmet-expand-line
###### C-return : emmet-expand-line
#### Functions
##### emmet-expand-line
#### Settings
- emmet-mode/confに.json設定ファイルがあるので、修正可能。
  修正後、pythonでjsontohashを実行することがおそらく必要。
  もしくは、"Don't edit"とあるが、.elをいじるか、作成されるテーブルを後で書き換えてあげればよいかも。
#### Link
- [[https://github.com/smihica/emmet-mode][smihica/emmet-mode - github]]
### esup
### etags
- Etags
#### Functions
##### find-tags
- M-. / <menu-bar><edit><goto><find-tag>
### evil
### gtags
#### Functions
##### gtags-find-tag
- (gtags-find-tag TAGNAME &optional OTHER-WIN)
  Input tag name and move to the definition.
##### gtags-find-rtag
- (gtags-find-rtag TAGNAME)
  Input tag name and move to hte referenced point.
##### gtags-find-symbol
- (gtags-find-symbol TAGNAME)
  Input symbol and move to the locations.
##### gtags-pop-stack
- (gtags-pop-stack)
  Move to previous point on the stack.
#### Variables
##### gtags-path-style
- Controls the style of path in [GTAGS SELECT MODE].
- Values :
  - root (default)
  - relative
- Memo
  Windowsでは、root->relativeを設定することで動作するようになった。
### helm
#### Functions
##### helm-M-x
##### helm-mini
##### helm-find-files
##### helm-show-kill-ring
#### Link
- [[https://qiita.com/jabberwocky0139/items/86df1d3108e147c69e2c][初心者〜初級者のためのEmacs-Helm事始め : 前編 - Qiita]]
### init-loader
#### Link
- http://emacs.rubikitch.com/init-loader/
- http://blog.aqutras.com/entry/2016/07/14/210000
- https://qiita.com/tadsan/items/181a352edcda740582ec
### initchart
- https://github.com/yuttie/initchart
- provides macros and functions to measure and visualize a init process of Emacs.
#### Functions
##### initchart-record-execution-time-of
##### initchart-visualize-init-sequence
- (initchart-visualize-init-sequence &optional FP)
  指定したfilepathに計測結果をsvg形式でグラフ表示する。
### ivy/counsel
### js2-mode
#### Functions
#### KeyBindings
##### C-c C-a : js2-mode-show-all
##### C-c C-e : js2-mode-hide-element
##### C-c C-f : js2-mode-toggle-hide-functions
##### C-c C-j : js-set-js-comment
##### C-c C-o : js2-mode-toggle-element
##### C-c C-s : js2-mode-show-element
##### C-c C-t : js2-mode-toggle-hide-comments
##### C-c C-w : js2-mode-toggle-warnings-and-errors
##### C-c M-: : js-eval
##### C-M-q : prog-indent-sexq
##### C-M-x : js-eval-defun
##### M-. : js-find-symbol
#### Link
- [[https://github.com/mooz/js2-mode][mooz/js2-mode - github]]
### magit
#### Link
- [[https://github.com/magit/magit][magit/magit - github]]
- [[https://magit.vc/manual/][magit - User Manuals]]
### noflet
- https://github.com/nicferrier/emacs-noflet
- Local function decoration
  ローカル関数を定義するマクロ。
#### About
- 
  By default, valid names of configuration files stat with two digits.
- platform specific configration file has prefix corresponds to the platform.
  these are loaded after non-platform specific configuration files.
  |-----------+-------------------+---------------+-----------------------------|
  | Platform  | Subplatform       | Prefix        | Exapmle                     |
  |-----------+-------------------+---------------+-----------------------------|
  | Windows   |                   | windows-      | windows-fonts.el            |
  |           | Meadow            | meadow-       | meadow-commands.el          |
  | Mac OS X  | Carbon Emacs      | carbon-emacs- | carbon-emacs-applescript.el |
  |           | Cocoa Emacs       | cocoa-emacs-  | cocoa-emacs-plist.el        |
  | GNU/Linux |                   | linux-        | linux-commands.el           |
  | All       | Non-window system | nw-           | nw-key.el                   |
  |-----------+-------------------+---------------+-----------------------------|

#### Functions
##### init-loader-load
##### init-loader-show-log
- (init-loader-show-log)
  Show init-loader log buffer.
#### Link
- [[https://github.com/emacs-jp/init-loader][emacs-jp/init-loader - github]]
### picture-mode
- 
  picture-modeかedit-pictureを選択する。
- C-c C-c
  pictureモードから抜ける。

- C-c <, C-c >, C-c ^, C-c .
  

- C-right, C-left, C-up, C-down
  線を描く。

- M-right, M-left, M-up, M-down
  線を消す。

### px
- Preview inline latex in any mode
  [[https://github.com/emacsmirror/px][px - github]]
#### Functions
##### px-preview-region
- (px-preview-region BEG END)
  Preview LaTeX fragments
##### px-preview
- (px-preview)
  Preview LateX fragments in the current buffer.
##### px-remove
- (px-remove)
  Remove LaTeX preview image in current buffer.
##### px-toggle
- (px-toggle)
  Toggle display of LaTeX preview in the current buffeer.
### slime
#### Functions
##### slime
- (slime &optional COMMAND CODING-SYSTEM)
##### slime-compile-defun
- C-c C-c
- (slime-compile-defun &optional RAW-PREFIX-ARG)
  Compile the current toplevel form.
  
##### slime-compile-and-load-file
- C-c C-k
- (slime-compile-and-load-file &optional POLICY)
  Compile and load the buffer's file and highlight compiler notes.

##### slime-switch-to-output-buffer
- C-c C-z (slime-repl.el)
- (slime-switch-to-output-buffer)
  Select the output buffer, when possible in an existing window

#### Memo
##### Error on Windows 7
- 
  Path中にspaceがあると、argumentとして取られてしまう模様。エラーとなる。
  [[http://stackoverflow.com/questions/17860785/slime-on-windows-7][SLIME on Windows 7]]

#### Link
- [[https://common-lisp.net/project/slime/][SLIME: The Superior Lisp Interaction Mode for Emacs]]
  
### straight
#### Link
- http://www.mhatta.org/wp/2018/09/23/org-mode-101-6/
- https://nukosuke.hatenablog.jp/entry/straight-el

### use-package
#### Memo
##### Keywords
-
  |--------------+--------------------------------------+-------+---------------------------------------|
  | keyword      | comment                              | defer | format                                |
  |--------------+--------------------------------------+-------+---------------------------------------|
  | :config      | 設定コード                           |       | ロード後に評価                        |
  | :init        | 初期化コード                         |       | ロード前に評価する式（複数でもOK）    |
  | :if          | 場合分け                             |       | 条件文                                |
  | :commands    | autoload                             | ○     | command or そのリスト                 |
  | :bind        | autoload＋キー割り当て               | ○     | (key . command) or そのリスト         |
  | :mode        | autoload＋auto-mode-alist設定        | ○     | regex or (regex . mode) or そのリスト |
  | :interpreter | autoload＋interpreter-mode-alist設定 | ○     | regex or (regex . mode) or そのリスト |
  | :defer       | 遅延ロード                           | ○     | boolean                               |
  | :disabled    | 無効化                               |       | boolean                               |
  |--------------+--------------------------------------+-------+---------------------------------------|

#### Link
- [[http://emacs.rubikitch.com/use-package-2/][use-package.el : Emacsの世界的権威が行っている最先端ラクラクinit.el整理術 - るびきち「新生日刊Emacs」]]
- [[http://qiita.com/kai2nenobu/items/5dfae3767514584f5220][use-packageで可読性の高いinit.elを書く - Qiita]]

### web-mode
#### KeyBindings
##### C-; (C-c C-;) : web-mode-comment-uncomment
##### C-c C-a : web-mode-indent-buffer
##### C-c C-b : web-mode-beginning-of-element
##### C-c C-d : web-mode-delete-element
##### C-c C-e : web-mode-select-element-content
##### C-c C-f : web-mode-toggle-folding
##### C-c C-i : web-mode-insert
##### C-c C-j : web-mode-duplicate-element
##### C-c C-n : web-mode-match-tag
##### C-c C-p : web-mode-parent-element
##### C-c C-r : web-mode-rename-element
#### Functions
##### web-mode-beginning-of-element (C-c C-b)
##### web-mode-comment-uncomment (C-; / C-c C-;))
##### web-mode-delete-element (C-c C-d)
- (web-mode-delete-element)
  Delete the current HTML element
##### web-mode-duplicate-element (C-c C-j)
- (web-mode-duplicate-element)
  Duplicate the current HTML element.
##### web-mode-indent-buffer (C-c C-a)
##### web-mode-match-tag (C-c C-n)
- (web-mode-match-tag)
  Match tag
- タグの開始タグ・終了タグへジャンプする
##### web-mode-rename-element (C-c C-r)
- (web-mode-rename-element)
  Rename the current HTML element.
##### web-mode-toggle-folding (C-c C-f)
- (web-mode-toggle-folding)
  Toggle folding on a block.
- HTMLタグを折りたたむ。
### yasnipet
- Tag
  ex) html, then tab
#### KeyBindings
##### C-i : yas-expand-from-trigger-key
##### Tab : yas-expand
##### C-c & C-n : yas-new-snippet
##### C-c & C-s : yas-insert-snippet
##### C-c & C-v : yas-visit-snippet-file
#### Functions
##### yas-describe-tables
- 利用できるスニペット一覧を表示可能。
##### yas-expand
##### yas-insert-snippet
- Prompts you for possible snippet expansion
##### yas-load-snippet-bufer
##### yas-load-snippet-bufer-and-close
##### yas-new-snippet
- Lets you create a new snippet file in the correct subdirectory.

##### yas-tryout-snippet
##### snippet-mode
- (snippet-mode)
###### KeyBindings
####### C-c C-c : yas-load-snippet-buffer-and-close
####### C-c C-l : yas-load-snippet-buffer
####### C-c C-t : yas-tryout-snippet
####### C-M-i : ispell-complete-word
#### Variables
##### yas-snippet-dires
- The directory where user-created snippets are to be stored.
#### Memo(yasnippet)
##### 作成
- Command
  yas-new-snippet(C-c & C-n)

- form
  - name : テンプレートの名前
  - key : TABで展開するキー
  - # : コメントが残せる
  - # -- 以下 : 展開したいコードを記述。
    Tabで$1,$2と飛ぶ。$0には、展開後にカーソルがその位置に飛ぶ。
    ${1:default text}とも設定可能。
    なお、#から始まる文字列でも問題なく入力できた模様。

- 
  - 終了 : C-c C-c
  - テスト : C-c C-t

##### 入力
- 略語(key) + TAB
- TABを押すごとに$1, $2...、全て終わった後$0に飛ぶ。
#### Link
- [[https://github.com/joaotavora/yasnippet/blob/master/yasnippet.el][joaotavora/yasnippet - github]]
- [[http://emacs.rubikitch.com/sd1601-auto-yasnippet/][#21 定型文を瞬時に入力　yasnippet の実力 (Software Design 2016年1月号掲載記事) Emacs auto-yasnippet インストール 設定 使い方 - るびきち「新生日刊Emacs」]]
## Type
### Language
#### Python
- Python Programming In Emacs
  https://www.emacswiki.org/emacs/PythonProgrammingInEmacs
- PythonをEmacsで書く+α
  http://ksknw.hatenablog.com/entry/2016/05/07/171239
- jedi
  http://qiita.com/yuizho/items/4c121bdecc103109e4fd
- py-autopep8
  https://github.com/paetzke/py-autopep8.el
## Memo
### パッケージ管理
#### package.el
- デフォルト
#### Cask
#### El-Get
- [[http://tarao.hatenablog.com/entry/20150221/1424518030][Caskはもう古い、これからはEl-Get - いまどきのEmacsパッケージ管理 - 貳佰伍拾陸夜日記]]
### 今後取り入れ希望
#### quickrun
- http://emacs.rubikitch.com/quickrun/
#### magit
## Link
- [[https://github.com/emacs-tw/awesome-emacs][Awesome Emacs - emacs-tw/awesome-emacs - github]]
- [[http://krazedkrish.com/blog/2015/12/27/awesome-emacs-plugins/][Awesome Emacs plugins you might not know - krazedkrish]]
- [[http://qiita.com/hottestseason/items/1e8a46ad1ebcf7d0e11c][Emacsパッケージ特集 - Qiita]]

- [[https://qiita.com/blue0513/items/c0dc35a880170997c3f5][Emacsの補完&検索を超強化する - Qiita]]
- https://qiita.com/tadsan/items/33ebb8db2271897a462b
