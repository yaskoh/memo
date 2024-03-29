# Make
## GNU make
### Command
- make [OPTION]... [TARGET]...
- -b, -m
- -B, --always-make
- -C dir, --directory=dir
- -d
- --debug[=FLAGS]
- -e, --environment-overrides
- -f file, --file=file, --makefile=FILE
  Use file as a makefile
- -i, --ignore-errors
- -I dir, --include-dir=dir
  Specifies a directory dir to search for included makefiles.
- -j [jobs], --jobs[=jobs]
- -k, --keep-going
- -l [load], --load-average[=load]
- -L, --check-symlink-times
- -n, --just-print, --dry-run, --recon
  Print the commands that would be executed, but do not execute them
- -o file, --old-file=file, --assume-old=file
- -O[type], --output-sync[=type]
- -p, --print-data-base
  Print the data base (rules and variable values) that results from reading the makefiles; then execute as usual or as otherwise specified.
- -q, --question
- -r, --no-builtin-rules
- -R, --no-builtin-variables
- -s, --silent, --quiet
- -S, --no-keep-going, --stop
- -t, --touch
- --trace
- -v, --version
- -w, --print-directory
- --no-print-directory
- -W file, --what-if=file, --new-file=file, --assume-new=file
- --warn-undefined-variables
### Specification
#### Makefiles
##### Contain
- explicit rules
  when and how to remake one or more files, called teh rule's targets.
- implicit rules
  when and how to remake a class of files based on their names.
- variable definitions
  a line that specifies a text string value for a variable that can be substituted into the text later.
- directives
  an instruction for make to do something special while reading the makefile.
- comments
  '#' starts a comment, which and the rest of line are ignored.
##### Names
- make tries to looks for the makefiles as following names in order: GNUmakefile, makefile, Makefile
##### Including other makefiles
- inculde 'filenames'...
##### Override
##### Secondary Expansion
#### Rules
##### Syntax
- targets : prerequisites
      recipe
      ...
- targets : prerequisites ; recipe
      recipe
      ...
##### Wildcards
##### Directory Search
###### General Search
- VPATH
###### Selective Search
- vpath pattern directories
- vpath pattern
- vpath
##### Phony Targets
##### Force Targets
##### Empty Targets
##### Special Targets
###### .PHONY
- The prerequisiets of the special target .PHONY are considered to be phony targets.
###### .SUFFIXES
- The prerequisites of the special trget .SUFFIXES are the list of suffixes to be used in checking for suffix roles.
###### .DEFAULT
###### .PRECIOUS
###### .INTERMEDIATE
###### .SECONDARY
###### .SECONDEXPANSION
###### .DELETE_ON_ERROR
###### .IGNORE
###### .LOW_RESOLUTION_TIME
###### .SILENT
###### .EXPORT_ALL_VARIABLES
###### .NOTPARALLEL
###### .ONESHELL
###### .POSIX
#### Recipes
##### Syntax
##### Echoing
##### Execution
##### Parallel
##### Errors
##### Interrupts
##### Recursion
##### Canned Recipes
##### Empty Recipes
- target: ;
#### Using Variables
#### Conditionals
##### Syntax
- conditional-directive-one
  text-if-one-is-true
  else conditional-directive-two
  text-if-two-is-true
  else
  text-if-one-and-two-are-false
  endif
##### Conditional directives
###### ifeq
- ifeq (arg1, arg2)
- ifeq 'arg1' 'arg2'
- ifeq "arg1" "arg2"
- ifeq "arg1" 'arg2'
- ifeq 'arg1' "arg2"
###### ifneq
- ifneq (arg1, arg2)
- ifneq 'arg1' 'arg2'
- ifneq "arg1" "arg2"
- ifneq "arg1" 'arg2'
- ifneq 'arg1' "arg2"
###### ifdef
- ifdef variable-name
###### ifndef
- ifndef variable-name
#### Functions
##### Syntax
- $(function arguments)
- ${funciton arguments}
##### Text
###### $(subst from,to,text)
##### File Name
##### Conditional
##### Foreach
##### File
##### Call
##### Value
##### Eval
##### Origin
##### Flavor
##### Make Control
##### Shell
##### Guile
#### Invoking make
#### Implicit Rules
##### Implicit Variables
- AR : Archive-maintaining program; default 'ar'
- AS : Program for compiling assembly files; default 'as'
- CC : Program for compiling C programs; default 'cc'
- CXX : Program for compiling C++ programs; default 'g++'
- CPP : Program for running the C preprocessor, with results to standard output; default '$(CC) -E'
- FC
- M2C
- PC
- CO
- GET
- LEX
- YACC
- LINT
- MAKEINFO
- TEX
- TEXI2DVI
- WEAVE
- CWEAVE
- TANGLE
- CTANGLE
- RM

- ARFLAGS
- ASFLAGS
- CFLAGS
  Extra flags to give to the C compiler.
- CXXFLAGS
- COFLAGS
- CPPFLAGS
- FFLAGS
- GFLAGS
- LDFLAGS
- LDLIBS
- LFLAGS
- YFLAGS
- PFLAGS
- RFLAGS
- LINTFLAGS
##### Pattern Rules
###### Automatic Variables
####### $@
- The file name of the target of the rule.
  If the target is an archive member, then '$@' is the name of the archive file.
####### $%
- The target member name, when the target is an archive member.
####### $<
- The name of the first prerequisite.
####### $?
- The names of all the prerequisites that are newer than the target, with spaces between them.
####### $^
- The names of all prerequisites, with spaces between them.
  A target has 
####### $+
- This is like '$^', but prerequisites listed more than once are duplicated in the order they were listend in the makefile.
####### $|
- The names of all the order-only prerequisites, with spaces between them.
####### $*
- The stem with which an implicit rule matches.
##### Suffix Rules(Old-Fashioned)
- Double-suffix rule
  It is defined by a pair of suffixes: the target suffix and the source suffix.
  It matches any file whose name ends with the target suffix.
  '.o.c' is equivalent to the pattern rule '%.o : %.c'
- Single-suffix rule
  It is defined by a single sufix, which is the source suffix. It matches any file name.
  '.c' is equivalent to the pattern rule '% : %.c'.
- Adding one own suffix
  The known suffixes are simply the names of the prerequisites of the special target .SUFFIXES.
  Writing rules for .SUFFIXES allows you to add more prerequisites.
  - ex)
    .SUFFIXES: .hack .win   # Add suffix list
    .SUFFIXES:              # Delete the default suffixes
    
#### Archives
##### Archive Members
##### Archive Update
##### Archive Pitfalls
##### Archive Suffix Rules
#### Extending GNU make
#### Integrating GNU make
#### Features
#### Missing Featuser
#### Conventions
#### Quick Reference
- define variable
- define variable =
- define variable :=
- define variable ::=
- define variable +=
- define variable ?=
- endef
- undefine variable
- ifdef variable
- ifndef variable
- ifeq (a,b)
- ifeq "a" "b"
- ifeq 'a' 'b'
- ifneq (a,b)
- ifneq "a" "b"
- ifneq 'a' 'b'
- else
- endif
- include file
- -influde file
- sinclue file
- override variable-assignment
- export
- export variable
- export variable-assinment
- unexport variable
- private variable-assignment
- vpath pattern path
- vpath pattern
- vpath
- $(subst from,to,text)
- $(patsubst pattern,replacement,text)
- $(strip string)
- $(findstring find,text)
- $(filter pattern...,text)
- $(filter-out pattern...,text)
- $(sort list)
- $(word n,text)
- $(words text)
- $(wordlist s,e,text)
- $(firstword names...)
- 

### Link
- [[https://www.gnu.org/software/make/manual/][GNU Make Manual]]
- [[http://quruli.ivory.ne.jp/document/make_3.79.1/make-jp_toc.html#SEC_Contents][目次 - GNU Make Manual 日本語訳]]
- [[http://www.ecoop.net/coop/translated/GNUMake3.77/make_toc.jp.html][GNU Make 再コンパイル作業を制御するプログラム Version 3.77 May 1998]]
## nmake
## Borland make
