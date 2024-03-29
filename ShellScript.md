# ShellScript
## Rule
### Basics
#### First Line
- 
  #! /bin/sh
  
  use bshell for use every environment.

#### Comment
- 
  use #(sharp).
  comment is from # to end of the line.

#### Line
- 
  line break is the sign of the end of a command in UNIX.
  \(backslash) make ignoring the end sign and connect lines.

#### Wildcard
- 
  * : any characters or none
  ?      : a character
  [...]  : one of the character inside of [...]
  [!...] : one of the character not inside of [...]

- Hidden Files
  handle hidden files using wildcard, you have to write .(dot) explicitely.

#### Quotation
- three ways to Quotate : 
  - \(backslash)
  - '(single quote)
  - "(double quote)
  
- bachslash(\)
  escape-character
  assume a normal character the next of backslash.
  
- single quote '
  in the single quote, all characters are assumed as normal characters.
    
- double quote "
  all characters but $, `(backquote), \(backslash) are assumed as normal characters.
  backslash is work as escape character when next character is $, `, \, " only.
    
- ex
  using variables, sometimes need to use quotation.
  1) 
  STRING=
  test $STRING = john
  (Ë test   = john, error)
    
  STRING=
  test "$STRING" = john
  (Ëtest "" = john, error won't occur)
    
#### Command substitution with backquotes
- 
  backquote substitute command within them to the result of command execution.
  
  - ex)
    $ echo "Today is `date`"
    Ë Today is Sun Nov 23 11:37:33 JST 2015
  
- nest
  being escaped backquote by backslash can perform.
  
  - ex)
  $ STRING=`echo "abc \`echo def\` ghi"`
  $ echo $STRING
  Ë abc def ghi

#### Exit status
- 
  True, Normal : 0
  False, Error : 1

  result is in "$?" variable.

#### Command Separater
- 
  - LineBreak
  - ; (Semicolon)
  - | (Pipe) - make output input of next command
  - & (Ampersand) - excute in background
  - || - OR
  - && - AND

##### Semicolon ;
- 
  executing left to right

##### Pipe |
- 
  vertical line.
  output of the left command on a pipe is processed as input of the right command.

##### Ampersand &
- 
  background execution
  background command gets /dev/null as input.

##### OR Operator ||
- 
  when left command get fail, then right command is executed.

##### AND Operator &&
- 
  when left command get success, then right command is executed.

#### Grouping
##### Parentheses ()
- 
  grouping commands.
  commands in () will execute in subshells.
  environment won't take ovre subshells to parent.

##### Braces {}
- 
  grouping commands.
  unlike parentheses, commands is executed in current shell.
  but when using redirect (like {echo abc} > test.txt), it may be executed in subshell.

#### Control Statement
##### if statement
- format
  if condition1
  then
    command
  elif condition2
    command
  else
    command
  fi

  - else
    else is not mandatory.
  
  - elif
    you can use elif statement if there is some condition.

- test
  often used as condition in if statement.
  test can used as [ ].

##### for statement
- format
  for variable in word-list
  do
    command
    ...
  done

- ex
  for i in a b c d e
  do
    echo $i
  done

###### memo
####### make defined-times loop
- using with "seq" command.
- ex
  - for i in `seq 1 N`
####### operate some vars at once
- enclosing some vars by double-quote(")
- ex
  for i in "a b c" "d e" "f g h i"; do echo $i; done;
  ⇒a b c(\n)d e(\n)f
##### while statement
- format
  while command-list
  do
    command
    ...
  done

  - command-list
    loop while last command is true(0).

##### case statement
- format
  case string in
    pattern1) command-list ;;
    pattern2) commnad-list ;;
    pattern3) commnad-list ;;
    ...
  esac

  - match
    the first match pattern will be done.
    you should pay attention to write down conditions.

##### test statement
- format 1
  if test -r file
  then ~

- format 2
  if [ -r file ]
  then ~

#### Line Break and Semicolomn
- 
  Semi-colon (;) can use a substitution of return code.
  you can use this when you want make the code one-liner.
  
- ex
  if command-list
  then
    command
    ...

  ↓
  
  if command-list; then
    command
    ...

## Shell Variable
### About
- Rule
  - Name
    you can use Alphabet, Number, Underscore(_).
    Uppercase and lowercase is distinguished.
    First letter can not be a number.
    Convention : Use Uppercases

- Using
  - $ABC
  - ${ABC}
  
  - Double quotes expand variables. Single quotes don't do.

- 
  |----------+-----------------------|
  | variable | comments              |
  |----------+-----------------------|
  | $0 ~ $9  | positional parameters |
  | $#       | arguments number      |
  | $*, $@   | all arguments         |
  | $?       | end status            |
  | $$       | process id            |
  | $!       | background process id |
  | $-       | flags                 |
  |----------+-----------------------|

- temporary setting
  $CFLAGS=-g make -> (CFLAGS=-g; export CLAGS; make)
  
### Variable setting
- Set
  without space.
  like : 
    variable=value
  not :
    variable = value

- Pattern
  - ${variable:=value}
  - ${variable:-value}
  - ${variable:?message}
  - ${variable:+value}

  - omit colon(:)
    when omitting colon(:) like ${variable=value},
    null is regarded as being set and not setting a new variable.

#### =
- ${variable:=value}
  variable is undefiend or set null, set value.
- ${variable=value}
  variable is undefined, set value.

#### -
- ${variable:-value}
  when variable is undefiend or set null, return value but not set it.
- ${variable-value}
  when variable is undefined, return value and not set.

- positional parameters
  you can use this option to positonal parameters like following:
  {1:-abc}

#### ?
- ${variable:?message}
  when variable is undefined or set null, return messsage.
  in shellscripts, it stopped here.
  if omit message, show default messages.
- ${variable?message}
  when variable is undefined, return messsage.
  and see above.
  
#### +
- ${variable:+value}
  when variable is "not" undefiend or set null (when it is defined), return value but not set it.
  
- ${variable+value}
  when variable is defiend (null is ok), return value but not set it.

### Positional Parameter
- 
  arguments set to $0 $1 $2 ... $n
  $9 is a last value and can't set bigger than 10.

- shift [num]
  set a 1+num argument to $1, and as follows.
  
  - ex)
    shift 3
    script 1 2 3 4 5 6 
    -> $1:4, $2:5, ...

- $#
  show number of arguments.

- $*
  return all variables.
  when enculosing by double quotes, all variables are enclosed by a variables.
  - ex
    "$*" -> "$1 $2 $3 ..."
  
  when positional parameter is null, "$*" is "" (null)
  
- $@
  return all variables.
  when enculosing by double quotes, all variables are saparated each variables, then enclosed.
  - "$@" -> "$1" "$2" "$3" ...
  
  when positional parameter is null, "$@" is null.

### Special variables
- $?
  end status.
  when end normal, set 0. when abnormal end, set others (not 0).

- $$
  process id.
  usually used to attach unique number.

- $!
  background process id.
  - ex
    command &
    ...
    wait $!
    (wait command finish)

- $-
  flags.
  when start "command -atv", return "atv" in command.

## Shell Functions
- format
  name()
  {
    command
    ...
  }

- format (one-liner)
  name() { command; ... ; }

- alias
  bsh don't have alias functions, and you can use shell functions as substitutions of it.

- return [n]
  Command "return" set return code of the function.
  Refer to the value checking by $?.
  If there is no return command, the function returns the return code of the last executed command.

- Environment
  Usually function executing on the current shell.
  When using stdin/out redirection in the function, creating sub shell and the function being executed on it.

  - ex (lsl is a created function)
    $ lsl : on current shell
    $ lsl > lsl.file : on sub shell

  - influence
    - Directory
      When executing on current shell, current directory may be changed.
      On sub shell, back to working directory when it finishes.

    - Variables
      Remains variables modification  executing on current shell.
      On sub shell, the value of variables will be back when the function ends.

    - exit command
      on current shell, exit command ends not only function but also the shell itself.
      On sub shell, exit finishes the functions only.

## Built-in Functions
## Syntax
   
### $()
- 
  

### ``
- 
  
## Memo
### Addition of ShellVariables
- 
  1. num=`expr $num + 1`

  if using bash (not including sh), you can use following:
  1. num=$[$num+1]
  2. num=$(($num+1))
  3. let result=num*mult

- 
  [[http://qiita.com/d_nishiyama85/items/a117d59a663cfcdea5e4][シェルで変数のインクリメントにexprを使うと100倍遅い件 - Qiita]]
  [[http://www.atmarkit.co.jp/ait/articles/0010/19/news003.html][シェルの変数に慣れる - @IT]]

### Extract dirpath, filename, extention etc. from path
- command
  - dirname
  - basename
  
- Pattern
  - ${var#pattern}
    forward, shortest match
  - ${var##pattern}
    forward, longest match
  - ${var%pattern}
    backward, shortest match
  - ${var%%pattern}
    backward, longest match

- 
  [[http://zawapro.com/?p=1619][【シェル】パス文字列からディレクトリ部、ファイル名を取得する - ザワプロ！]]
  [[http://d.hatena.ne.jp/zariganitosh/20100921/get_file_name_ext_dir][ファイルパスからファイル名や拡張子を自由に取り出す - ザリガニが見ていた...。]]
  [[http://www.kishiro.com/FreeBSD/get_filename_in_shellscript.html][シェルスクリプトでパス文字列からファイル名／ディレクトリ名／拡張子を抽出する]]
### Move current execution location
- 
  pushd `dirname $0`
  ...
  popd
### Show full path of execution location
- echo $(cd $(dirname ${0}) && pwd)
### Using child process vars in parent process
- 
  use "source" command when calling files, and the contents of the called files are executed like just it typed on parent environmet.
  ex) source test.sh
### Return code of function
- ファンクションのリターンコマンドは、数字のみしか返すことができない。
  関数の戻り値として値を返したい場合、標準出力を行い戻り値を変数に代入したり、グローバル変数を使ったりするとよい。
  [[http://shellscript.sunone.me/function.html][関数の使用方法 - シェルスクリプト リファレンス]]
