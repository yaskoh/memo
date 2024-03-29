# Emacs Built-in Packages
## C source code
### Functions
#### abs
- (abs ARG)
  Return the absolute value of ARG.
#### append
- (append &rest SEQUENCES)
  Concatenate all the arguments and make the result a list.
#### assoc
- (assoc KEY LIST)
  Return non-nil if KEY is "equal" to the car of an element of LIST.
#### autoload
- (autoload FUNCTION FILE &optional DOCSTRING INTERACTIVE TYPE)
  Define FUNCTION to autoload from FILE.
  FUNCTION is a symmol; FILE is a file name string to pass to "load".
#### backward-char
- (backward-char &optional N)
#### backward-word
- (backward-word &optional ARG)
  Move backward until encountering the beginning of a word.
#### beginning-of-line (C-a)
- (beginning-of-line &optional N)
  Move point to beginning of current line (in the logical order).
#### bobp
- (bobp)
  Return t if point is at the beginning of the buffer.
#### bolp
- (bolp)
  Return t if point is at the beginning of line.
#### buffer-substring
- (buffer-substring START END)
  Return the contents of part of the current buffer as a string.
#### buffer-substring-no-properties
#### car
- (car LIST)
  Return the car of LIST. If arg is nil, return nil.
#### cdr
- (cdr LIST)
  Return the cdr of LIST. If arg is nil, return nil.
#### ceiling
#### char-after
- (char-after &optional POS)
  Return character in current buffer at position POS.
#### char-before
- (char-before &optional POS)
  Return character in current buffer preceding position POS.
#### char-to-string
- (char-to-string CHAR)
  Convert arg CHAR to a string containing that character.
- ex
  (char-to-string ?a) -> "a"
#### completing-read
- (completing-read PROMPT COLLECTION &optional PREDICATE REQUIRE-MATCH INITIAL-INPUT HIST DEF INHERIT-INPUT-METHOD)
  Read a string in the minibuffer, with completion.
- "PROMPT"をミニバッファに表示して"COLLECTION"で指定した候補単語を補完入力し、結果を文字列として返す。
#### concat
- (concat &rest SEQUENCES)
  Concatenate all the arguments and make the result a string.
#### cons
- (cons CAR CDR)
  Create a new cons, give it CAR and CDR as components, and return it.
#### count-lines
- (count-lines START END)
  Return number of lines between START and END.
#### current-buffer
- (current-buffer)
  Return the current buffer as a Lisp object.
#### current-column
- (current-column)
  Return the horizontal position of point.
#### current-time-string
- (current-time-string &optional SPECIFIED-TIME)
  Return the current local time, as a human-readable string.
#### defalias
- (defalias SYMBOL DEFINITION &optional DOCSTRING)
  Set SYMBOL's function defenition to DEFINITION.
- このスペシャルフォームは、シンボルnameを定義definition(任意の正しいLisp関数)とする 関数 として定義する。
#### define-key
- (define-key KEYMAP KEY DEF)
  In KEYMAP, define key sequence KEY as DEF.
#### delete
- (delete ELT SEQ)
  Delete members of SEQ which are "equal" to ELT, and erturn the result.
#### delete-char
- (delete-char N &optional KILLFLAG)
  Delete the following N characters (previous if N is negative)
#### delete-region
- (delete-region START END)
  Delete the text between START and END.
#### ding
- (ding &optional ARG)
  Beep, or flash the screen.
  Also, unles an argument is given, terminate any keyboard macro currently executing.
- 変数"visible-bell"の値に応じて端末のベルを鳴らしたり、画面をフラッシュする。
#### downcase
- (downcase OBJ)
  Convert argument to lower case and return that.
#### downcase-word
- (downcase-word ARG)
  Convert to lower case from point to end of word, moving over

#### end-of-line
- (end-of-line &optional N)
  Move point to end of current line (in the logical order).
#### eobp
- (eobp)
  Return t if point is at the end of the buffer.
#### eolp
- (eolp)
  Return t if point is at the end of a line.
#### eq
- (eq OBJ1 OBJ2)
  Return t if the two args are the same Lisp object.
- equalと異なり、オブジェクトの形式でなく、オブジェクト自体が完全に一致した（同じメモリを指している）場合のみtを返す。
#### equal
- (equal O1 O2)
  Return t if two lisp objects have similar structure and contents.
#### erase-buffer
- (erase-buffer)
  Delete the entire contents of the current buffer.
#### expand-file-name
- (expand-file-name NAME &optoinal DEFAULT-DIRECTORY)
  Convert filename NAME to absolute, and canonicalize it.
#### expt
- (expt ARG1 ARG2)
  Return the exponential ARG1 ** ARG2.
#### eval
- (eval FORM &opitonal LEXICAL)
  Evaluate FORM and return its value.
#### eval-buffer
- (eval-buffer &optional BUFFER PRINTFLAG FILENAME UNIBYTE DO-ALLOW-PRINT)
  Execute the current buffer as Lisp code.
#### fboundp
- (fboundp SYMBOL)
  Return t if SYMBOL's function definition is not void.
#### fceiling
#### file-exists-p
- (file-exists-p FILENAME)
  Return t if file FILENAME exists.
  関数が定義済みかどうかのチェック
#### file-name-nondirectory
- (file-name-nondirectory FILENAME)
  Return file name FILENAME sans its directory.
  ディレクトリパスを除いたファイル名を取得
#### file-name-directory
- (file-name-directory FILENAME)
  Return the directory component in file name FILENAME.
  ファイル名を除いたディレクトリパスを取得。
#### ffloor
- (ffloor ARG)
  Retrun the largest integer no reater than ARG, as a float.
#### float
- (float ARG)
  Return the floating point number equal to ARG.
#### floatp
#### floor
- (floor ARG &optonal DIVISOR)
  Retrun the largest integer no reater than ARG.
#### following-char
- (following-char)
  Return the character folloing point, as a number.
  At the end of the buffer or accesible region, return 0.
#### format
- (format STRING &rest OBJECTS)
  Format a string out of a format-string and arguments.

- 書式指定子の%と文字の間に数を指定して、表示幅の変更や左寄せをすることができる。
  「桁.精度」として指定する。どちらも省略可能。通常右寄せ、負の数を指定すると左寄せとなる。
##### 書式指定子
- %s : 文字列、シンボル
- %d : 整数
- %o : 8進数
- %x : 16進数
- %c : 文字コードに対応する文字
- %f : 浮動小数点数
- %S : S式
- %% : %自身
#### format-time-string
- (format-time-string FORMAT-STRING &optional TIME UNIVERSAL)
  Use FORMAT-STRING to format the time TIME, or now if omitted.
#### forward-char
- (forward-char &optional N)
#### forward-line
- (forward-line &optional N)
  Move N lines forward (backward if N is negative).
- backward-lineは存在しないので、上に移動する場合は負の引数を渡す。
  必ず次の行の先頭位置に移動する。
#### forward-word
- (forward-word &optional ARG)
#### fround
- (fround ARG)
  Return the nearest integer to ARG, as a float.
#### ftruncate
#### fset
- (fset SYMBOL DEFINITION)
  Set SYMBOL's function definition to DEFINITION, and return DEFINITION.
#### get-buffer
- (get-buffer BUFFER-OR-NAME)
  Return the bufer named BUFFER-OR-NAME.
#### get-buffer-create
- (get-buffer-create BUFFER-OR-NAME)
  Return the bufer specified by BUFFER-OR-NAME, creating a new one if needed.
#### get-text-property
- (get-text-property POSITION PROP &optional OBJECT)
  Return the value of POSITION's property PROP, in OBJECT.
#### goto-char
- (goto-char POSITION)
  Set point to POSITION, a number or marker.
#### goto-line
- (goto-line LINE &optional BUFFER)
  Go to LINE, counting from line 1 at beginning of buffer.
#### insert-before-markers
- (insert-before-markers &rest ARGS)
  Insert strings or characters at point, relocating markers after the text.
- insert関数同様、指定した引数をバッファに挿入するが、挿入位置にマーカーがある場合はそのマーカーよりも前にinsertする。
#### integer-or-marker-p
- (integer-or-marker-p OBJECT)
  Return t if OBJECT is an integer or a marker (editor pointer).
#### integerp
#### intern
- (intern STRING &optional OBARRAY)
  Return the canonical symbol whose name is STRING.
#### insert
- (insert &rest ARGS)
  Insert the arguments, either strings or characters, at point.
#### insert-char
- (insert-char CHARCTER &optional COUNT INHERIT)
  Insert COUNT copies of CHARACTER.
#### kill-all-local-variables
- (kill-all-local-variables)
  Switch to Fundamental mode by killing current buffer's local variables.
#### length
- (length SEQUENCE)
  Return the length of vector, list or string SEQUENCE.
#### line-end-position
- (line-end-position &optional N)
  Return the character position of the last character on the current line.
#### list
- (list &rest OBJECT)
  Return a newly created list with specified arguments as elements.
#### load
- (load FILE &optional NOERROR NOMESSAGE NOSUFFIX MUST-SUFFIX)
  Execute a file of Lisp code named FILE.
  First try FILE with ".elc" appendend, then try with ".el", then try FILE unmodified.

  This function searches the directories in "load-path".
  
  リロードの抑制がない以外はrequireと同じ動き。
#### local-key-binding
- (local-key-binding KEYS &optional ACCEPT-DEFAULT)
  Return the biding for command KEYS in current local keymap only.
#### lookin-at
- (looking-at REGEXP)
  Return t if text after point matches regular expression REGEXP.
#### macroexpand
- (macroexpand FORM &optional ENVIRONMENT)
  Return result of expanding macros at top level of FORM.
  
  ex) (macroexpand '(push 'a test))
#### make-key-map
- (make-keymap &optional STRING)
  Construct and return a new keymap, of the form (keymap CHARTABLE .ALIST).
  CHARTABLE is a char-table that holds the bindings for all characters without modifiers.
#### make-local-variable
- (make-local-variable VARIABLE)
  Make VARIABLE have a separate value in the current buffer.
#### make-marker
- (make-marker)
  Return a newly allocated marker which does not point at any place.
- 新規に作られたマーカーオブジェクトを返すので適宜変数に代入する。
#### make-string
- (make-string LENGTH INIT)
  Return a newly created string of length LENGTH, with INIT in each element.
  LENGTH must be an integer.
  INIT must be an integer that represents a character.
- 文字コードから文字を作る。
#### make-sparse-keymap
- (make-sparse-keymap &optional STRING)
  Construct and return a new sparse keymap.
#### mark
- (mark &optional FORCE)
  Return this buffer's mark value as integer, or nil if never set.
#### marker-buffer
- (marker-buffer MARKER)
  Return hte buffer that MARKER points into, or nil if none.
  Returns nil if MARKER points into a dead buffer.
#### marker-position
- (marker-position MARKER)
  Return the position MARKER points at, as a character number.
  Returns nil if MARKER points nowhere.
#### match-beginning
- (match-beginning SUBEXP)
  Return position of start of text matched by last search.
#### match-end
- (match-end SUBEXP)
  Return position of end of text matched by last search.
#### max
- (max NUMBER-OR-MARKER &rest NUMBERS-OR-MARKERS)
  Return largest of all the arguments.
#### member
- (member ELT LIST)
  Return non-nil if ELT is an elemnt of LIST.
#### message
- (message FORMAT-STRING &rest ARGS)
  Display a message at the bottom of the screen.
#### min
- (min NUMBER-OR-MARKER &rest NUMBERS-OR-MARKERS)
  Return smallest of all the arguments.
#### mod
- (mod X Y)
  Return X modulo Y.
#### move-to-column (M-g TAB)
- (move-to-column COLUMN &optoinal FORCE)
  Move point to column COLUMN in the current line.
#### move-to-window-line
- (move-to-window-line ARG)
  Position point relative to window.
- ウィンドウの先頭行を基準に指定行に移動する。
#### narrow-to-region
- (narrow-to-region START END)
  Restrict editing in this buffer to the current region.

#### number-p
- (numberp OBJECT)
#### number-to-string
- (number-to-string)
  Return the decimal representation of NUMBER as a string.
#### nth
- (nth N LIST)
  Return the Nth element of LIST.
  N counts from zero.
#### nthcdr
- (nthcdr N LIST)
  Take cdr N times on LIST, return the result.
#### nreverse
- (nreverse LIST)
  Reverse LIST by modifying cdr pointers.
#### print
- (print OBJCET &optional PRINTCHARFUN)
  Output the printed representation of OBJECT, with newlines around it.
#### point
- (point)
  Return value of point, as an integer.
#### point-min
- (point-min)
  Return the minimum permissible value of point in the current buffer.
#### point-marker
- (point-marker)
  Return value of point, as a market object.
- ポイント位置を指し示すマーカーを作成し、そのマーカーオブジェクトを返す。
  make-marker + set-marker (point)を行ってくれるイメージ。
#### point-max
- (point-max)
  Return the maximum permissible value of point in the current buffer.
#### preceding-char
- (preceding-char)
  Return the character preceding point, as a number.
  At the beginning of the buffer or accessible region, return 0.
#### put-text-property
- (put-text-property START END PROPERTY VALUE &optional OBJECT)
  Set one property of the text from START to END.
  The arguments PROPERTY and VALUE specify the propety to add.
#### random
- (random &optional LIMIT)
  Return a pseudo-random number.
#### read-buffer
- (read-buffer PROMPT &optional DEF REQUIRE-MATCH)
  Read the name of a buffer and return as a string.
#### read-char
- (read-char &optional PROMPT INHERIT-INPUT-METHOD SECONDS)
  Read a caracter from the command input (keyboard or macro).
  It is returned as a number.
#### read-command
- (read-command PROMPT &optional DEFAULT-VALUE)
  Read the name of a command and return as a symbol.
#### read-key-sequence
- (read-key-sequence PROMPT &optional CONTINUE-ECHO DONT-DONCASE-LAST CAN-RETURN-SWITCH-FRAME CMD-LOOP)
  Read a sequence of keystrokes and return as a string or vector.
#### read-string
- (read-string PROMPT &optional INITIAL-INPUT HISTORY DEFAULT-VALUE INHERIT-INPUT-METHOD)
  Read a string from the minibuffer, prompting with string PROMPT.
#### read-variable
- (read-variable PROMPT &optoinal DEFAULT-VALUE)
  Read the name of a user option and return it as a symbol.
  Prompt with PROMPT.
#### region-beginning
- (region-beginning)
  Return the integer value of point or mark, whichever is smaller.
#### region-end
- (region-end)
  Return the integer value of point or mark, whichever is larger.
#### replace-match
- (replace-match NEWTEXT &optional FIXEDCASE LITERAL STRING SUBEXP)
  Replace text matched by last search with NEWTEXT.
  Leave point at the end of the replacement text.
#### re-search-backward
- (re-search-backward REGEXP &optional BOUND NOERROR COUNT)
  Search backward from point for match for regular expression REGEXP.
#### re-search-forward
- (re-search-forward REGEXP &optional BOUND NOERROR COUNT)
  Search forward from point for regular expression REGEXP.
#### require
- (require FEATURE &optional FILENAME NOERROR)
  If feature FEATURE is not loaded, load it from FILENAME.
  If FEATURE is not a member of the list "features", then the feature is not loaded; so load the file FILENAME.
#### round
- (round ARG &optional DIVIOR)
  Return the nearest integer to ARG.
#### save-restriction
- (save-restriction &rest BODY)
  Execute BODY, saving and restoring current buffer's restrictions.
- 現在設定されている範囲制限を保存してBODYを評価する。
#### search-backward
- (search-backward STRING &optional BOUND NOERROR COUNT)
  Search backward from point for STRING.
#### search-forward
- (search-forward STRING &optional BOUND NOERROR COUNT)
  Search forward from point for STRING.
  Set point to the end of occurrence found, and return point.

- 引数
  - BOUND : どこまで検索するかポイント位置で指定する。バッファ末までの時はnilを指定する。
  - NOERROR : 見つからなかった場合の処理を指定。
    - t : nilを返す(no error)
    - nil,t以外 : 検索範囲まで
  - COUNT : 指定した回数だけ検索を繰り返す。
#### self-insert-command
- (self-insert-command N)
  Insert the character you type.
- 一般の関数に割り当てられている関数。
  押したキーそのものを挿入したいときなどに利用する。
#### set
- (set SYMBOL NEWVAL)
  Set SYMBOL's value to NEWVAL, and return NEWVAL.
#### set-buffer
- (set-buffer BUFFER-OR-NAME)
  Make bufer BUFFER-OR-NAME current for editing operations.
#### set-default
- (set-default SYMBOL VALUE)
  Set SYMBOL's default value to VALUE. SYMBOL and VALUE are evaluated.
#### set-marker
- (set-marker MARKER POSITION &optional BUFFER)
  Position MARKER before character number POSITION in BUFFER.
  If BUFFER is omitted or nil, it defaults to the current buffer.
  If POSITION is nil, makes marker point nowhere so it no longer slows down editing in any buffer.
  Retruns MARKER.
- "マーカー"を"ポイント値"の位置に設定する。
  POINTにnilを与えるとクリアできる。使われないマーカーがたまると動作が遅くなるので、使い終わったらクリアするようにする。
#### skip-chars-backward
- (skip-chars-backward STRING &optional LIM)
  Move point backward, stopping before a char not in STRING, or at pos LIM.
#### skip-chars-forward
- (skip-chars-forward STRING &optional LIM)
  Move point forward, stopping before a char not in STRING, or at pos LIM.
#### sleep-for
- (sleep-for SECONDS &optional MILLISECONDS)
  Pause, without updating display, for SECONDS seconds.
#### sort
- (sort LIST PREDICATE)
  Sort LIST, stably, comparing elements using PREDICATE.
  Returns the sorted list. LIST is modified by side effects.
  PREDICATE is called with two elements of LIST, and should return non-nil if the first element sohuld sort before the second.
#### stringp
#### string-equal
#### string-match
- (string-match REGEXP STRING &optional STRAT)
  Return index of start of first match for REGEXP in STRING, or nil.
#### string-to-char
- (string-to-char STRING)
  Return the first character in STRING.
#### string-to-number
- (string-to-number STRING &optional BASE)
  Parse STRING as a decimal number and return the number.
#### substring
- (substring STRING FROM &optional TO)
  Return a new string whose contents are a substring of STRING.
#### symbol-function
- (sybmol-functon SYMBOL)
  Return SYMBOL's function definition, or nil if that is void.
#### symbol-value
- (symbol-value SYMBOL)
  Return SYMBOL's value.
#### system-name
- (system-name)
  Return the host name of the machine you are running on, as a string.
#### this-command-keys
- (this-command-keys)
  Return the key sequence that invoked this command.
#### throw
- (throw TAG VALUE)
  Throw to the catch for TAG and return VALUE from it.
#### truncate
- (truncate ARG &optional DIVISOR)
  Truncate a floating point number to an int.
- 小数点以下を切り捨てた数を返す。
#### upcase
- (upcase OBJ)
  Convert argument to upper case and return that.
#### use-global-map
- (use-global-map KEYMAP)
  Select KEYMAP as the global keymap.
#### use-local-map
- (use-local-map KEYMAP)
  Select KEYMAP as the local keymap.
#### user-login-name
- (user-login-name &optional UID)
  Return the name under which the user logged in, as a string.
#### user-uid
- (user-uid)
  Return the effective uid of Emacs.
  Value is an integer or a float, dependingon the value.
#### widen
- (widen)
  Remove restrictions (narrowing) from current buffer.
- ナローイングを解除し、バッファのすべての範囲にアクセスできるようにする。
  強制手段の意味合いのため、一時的にナローイングを解除するためにはsave-restrictionを使う。
#### yes-or-no-p
- (yes-or-no-p PROMPT)
  Ask user a yes-or-no question.
  Return t if answer is yes, and nil if the answer is no.
#### 1+
#### 1-
#### +
- (+ &rest NUMEBRS-OR-MARKERS)
#### -
#### %
#### *
#### /
#### <
#### <=
#### =
#### /=
#### >
#### >=
### Special forms
#### and
- (and CONDITIONS...)
  Eval args until one of htem yields nil, then return nil.
#### catch
- (catch TAG BODY...)
  Eval BODY allowing nonlocal exists using "throw".
  TAG is evalled to get the tag to use; it must not be nil.
- 
  throwされた場合にcatch式の評価がその値でただちに行われ、catch式を抜ける。

#### cond
- (cond CLAUSES...)
  Try each clause until one succeeds.
  Each clause looks like (CONDITION BODY...).
- 
  条件分岐をする際に用いる。

#### condition-case
#### defconst
- (defconst SYMBOL INITVALUE [DOCSTRING])
  Define SYMBOL as a constant variable.
  This declares that neither programs nor users should ever change the value.
  This constancy is not actually enforced by Emacs Lisp, but SYMBOL is marked as a special variable so that it is never lexically bound.

- defvarと異なり、既に値が入っていても変更する。
#### defvar
- (defvar SYMBOL &optional INITVALUE DOCSTRING)
  Define SYMBOL as a variable, and return SYMBOL.
  You are not required to define a variable in order to use it,
  but defining it lets you supply an initial value and documentation,
  which can be referred to by the Emacs help facilities and other programming tools.
  
  The optional argument INITVALUE is evaluated, and used to set SYMBOL,
  only if SYMBOL's value is void.

- 
  変数は宣言をしなくてもsetqなどで代入・利用できるが、
  defvarで変数宣言することでバイトコンパイラが文句を言わない。
  defconstと異なり、既に値が入っている場合は設定しない。

#### function
#### if
- (if COND THEN ELSE...)
  If COND yields non-nil, do THEN, else do ELSE...
  Returns the value of THEN or the value of the last of the ELSE's.

- (if 式 From1 Form2 ... Fromn)
  式がnil以外だった場合、From1を、nilだった場合はFrom2 ... Fromn までを実行する。

#### interactive
- (interactive &optional ARGS)
  Specify a way of parsing arguments for interactive use of a function.

- ARGS
  ex) (interactive "sInputString :a\nsInputString :b\n"
  最初の文字が引数の型で、\nまでがプロンプトとして利用される。

##### Code letters
- a
- b
- B
- c : character
- C
- d
- D : Directory name
- e
- f : Exsisting file name
- F
- G
- i
- k
- K
- m
- M
- n : Number read using minibuffer.
- N
- p : Prefix arg converted to numebr. Does not do I/O.
  C-u prefixで与えた値。デフォルト1
- P : Prefix arg in raw form. Does not do I/O.
  C-u prefixで与えた値。デフォルト nil
- r : Region point and mark as 2 numeric args, smallest first. Des not do I/O.
  2つの引数に、関数呼び出し時に設定されているマークとポインタそれぞれの値が入る。
- s : Any string.
- S : Any symbol.
- U
- v
- x
- X
- z
- Z

#### lambda
- (lambda ARGS [DOCSTRING] [INTERACTIVE] BODY)
  Return a lambda expression.
  
#### let
- (let VARLIST BODY...)
  Bind variables according to VARLIST then eval BODY.

- 局所的に利用する変数を作成する。
  (let (変数リスト)
    本体)
#### let*
- (let* VARLIST BODY...)
- letとの違いは、直前の宣言部での値を代入可能。

#### or
- (or CONDITIONS...)
  Eval args until one of them yields non-nil, then return that value.
#### point-min
- (point-min)
  Return the minimum permissible value of point in the current buffer.
#### progn
- (progn BODY...)
  Eval BODY forms sequentially and return value of last one.
- 複数の処理をまとめる。
  式を順に評価していく。複数のS式を一つにまとめるためのもの。
  prognは最後の式を式を評価して返すが、prog1は一つ目の式、prog2は二つ目の式を返す。
#### prog1
- (prog1 FIRST BODY...)
  Eval FIRST and BODY sequentially; return value from FIRST.
#### prog2
- (prog2 FORM1 FORM2 BODY...)
  Eval FORM1, FORM2 and BODY sequentially; return value FORM2.
#### quote
- (quote ARG)
  Return the argument, without evaluating it.
#### save-current-buffer
#### save-excursion
- (save-excursion &rest BODY)
  Save point, mark, and current buffer; execute BODY; resutore those things.
#### save-restriction
#### setq
- (setq [SYM VAL]...)
  Set each SYM to the value of its VAL.
#### setq-default
- (setq-default [VAR VALUE]...)
  Set the default value of variable VAR to VALUE.
#### track-mouse
- (track-mouse BODY...)
  Evaluate BODY with mouse movement enabled.
#### unwind-protect
- (unwind-protect BODYFORM UNWINDFORMS...)
  Do BODYFORM, protecting with UNWINDFORMS.
  If BODYFORM completes normally, its value is returned after executing the UNWINDFORMS.
  If BODYFORM exits nonlocally, the UNWINDFORMS are executed anyway.
- 
  途中で何らかの理由で終了した場合でも、最後まで処理をおこなってくれる関数。
  prog1の最後までやりきる版みたいなもの。評価値は最初の式。
#### while
- (while TEST BODY...)
  If TEST yields non-nil, eval BODY... and repeat.
  The order of execution is thus TEST, BODY, TEST, BODY and so on until TEST returns nil.
- 
  while 式 本体
  ループ
### Variables
#### buffer-file-coding-system
- Coding system to be used for encoding the buffer contents on saving.
#### buffer-file-name
- Name of file visited in current buffer, or nil if not visiting a file.
#### case-fold-search
- Non-nil if searches and matches should ignore case.
#### case-replace
- Non-nil means "query-replace" should preserve case in replacements.
#### completion-ignore-case
- non-nil means don't consider case significant in completion.
  For file-name completion, "read-file-name-completion-ignore-case" controls behavior.
  For buffer name completion, "read-buffer-completion-ignore-case" controls the behavior.
#### debug-on-error
- Non-nil means enter ebugger if an error is signaled.
  Does not apply to errors handleb dy "condition-case" ore those matched by "debug-ignored-errors".
#### default-directory
- Name of default directory of current buffer.
#### default-major-mode
- Value of "major-mode" for new buffers.
#### exec-directory
- Directory for executables for Eamcs to invoke.
#### features
- A list of symbols which are the features of the executing Emacs.
#### indent-tabs-mode
- Indentation can insert tabs if this is non-nil.
  Original value : t
#### last-command-event
- Last input event that was part of a command.
#### load-path
- List of directories to search for files to load.
#### major-mode
- Symbol for current buffer's major mode.
  
#### minor-mode-map-alist
- Alist of keymaps to use for minor modes.
  Each element looks like (VARIABLE . KEYMAP); KEYMAP is used to read key sequences 
  and look up bindings if VARIABLE's value is non-nil.
#### minor-mode-overriding-map-alist
- Alist of keymaps to use for minor modes, in current major mode.
#### overriding-localmap
-  Keymap htat replaces (overrides) local keymaps.
   Id htis variable is non-nil, Emacs looks up bindings in this keymap INSTEAD OF the keymap char property, and the buffer's local map.
#### read-buffer-completion-ignore-case
- Non-nil means completion ignores when reading a bufer name.
#### scroll-margin
- Number of lines of margin at the top and bottom of a window.
#### scroll-step
- The number of lines to try scrolling a window by when point moves out.
#### system-type
- The value is a sybmol indicating the type of operating system you are using.
- Values
  - gnu
  - gnu/linux
  - darwin
  - ms-dos
  - windows-nt
  - cygwin
#### this-command
- The command now being executed.
#### toggle-truncate-lines
- Non-nil means do not display continuation lines.
  Instead, give each line of text just one screen line.
#### windows-system
- Name of window system through which the selected frame is displayed.
- Values:
  - nil : a termcap frame
  - x   : an Emacs frame that is really an X window
  - w32 : an Emacs frame that is a window on MS-Windows display.
  - ns  : an Emacs frame on a GNUstep on Macintosh Cocoa display.
  - pc  : a direct-write MS-DOS frame.
