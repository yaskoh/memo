# LLVM
## Compiler
## Tools
### LLDB
- http://lldb.llvm.org/index.html
- http://lldb.llvm.org/tutorial.html

- Command Structure
  <noun> <verb> [-options [option-value]] [argument [argument...]]

#### Debugger commands
##### apropos
##### backtrace, bt
##### breakpoint, br
###### breakpoint set, br s
- 省略形: b hoge.c:8 (br -f hoge.c -l 8)
####### --name, -n
####### --file, -f
####### --line, -l
####### --method, -M
####### --selector, -S
####### --shlib, -s
###### breakpoint list
###### breakpoint command
####### add
##### bugreport
##### command
###### command alias
- ex: command alias b breakpoint
###### command unalias
- ex: command unalias b
##### disassemble
##### expression, expr
###### expression
##### frame
###### frame variable
###### frame select
##### gdb-remote
##### gui
##### help
##### kdb-remote
##### langugae
##### log
##### memory
##### platform
##### plugin
##### process
###### process attach
###### process launch
####### --stop-at-entry
####### --prograv_arg <value>
###### run, r
- same as "process launch" (alias)
##### quit
##### register
##### script
##### settings
###### settings set
##### target
###### target create
##### thread
###### thread continue
###### thread step-in
###### thread step-over
###### thread step-out
###### thread step-inst
###### thread step-over-inst
###### thread until
###### thread list
###### thread backtrace
####### all
###### thread select
##### type
##### version
##### watchpoint
##### watch
###### watch set
###### watch modify
###### watch list
####### -v
#### Abbreviations
##### b
##### bt
##### c
##### call
##### continue
##### detach
##### di
##### dis
##### display
##### env
##### exit
##### file
- ex: file /test/program.app

##### finish
##### image
##### j
##### jump
##### kill
##### l
##### list
##### n
##### next
##### p
- 構造体を出力できる
##### po
- Print Objectの略
##### print
##### q
##### r
##### rbreak
##### repl
#### Reverse lookup
##### Compile時オプション
- デバッグするためには、"-g"オプションをつけデバッグ可能な状態でコンパイルする。
  gcc -o hoge -g hoge.cなど。
##### ファイル名を指定して起動
- lldb filename
##### 実行
- (lldb) r  or  (lldb) run
