# Compiler
## Tools
### lex/flex
- 
  flex is a tool for generating scanners.
  A scanner is aprogram which recognizes lexical patterns in text.

- [[http://flex.sourceforge.net/manual/index.html][Lexical Analysis With Flex, for Flex 2.5.37]]
  or "info flex"
  
#### Format
- 
  definitions
  %%
  rules
  %%
  user code

##### Definitions Section
- Form
  name difiniton
  - ex)
    DIGIT [0-9]
    ID    [a-z][a-z0-9]*

  - text in %{ %}
    copied verbatim to the output.
  
##### Rules Section
- Form
  pattern action

###### Patterns
- x
  match the characer 'x'

- .
  any character (byte) except newline

- [xyz]
  a character class, in this case, the pattern matches either an 'x', a 'y', or a 'z'.

- [abj-oZ]
  a "character class" with a range in it; matches an 'a', a 'b', any letter from 'j' to 'o' or a 'Z'.

- [^A-Z]
  a "negated character class", i.e., any character but those in the class.

- [a-z]{-}[aeiou]
  the lowercase consonants

- r*
  zero or more r's, where r is any regular expression

- r+
  one or more r's

- r?
  zero or one r's

- r{2,5}
  anywhere from two to five r's

- r{2,}
  two or more r's

- r{4}
  exactly 4 r's

- {name}
  the expansion of the 'name' definition

- "[xyz]\"foo"
  the literal string: '[xyz]"foo'

- \X
  if X is 'a', 'b', 'f', 'n', 'r', 't', or 'v', then the ANSI-C interpretation of '\x'.
  Otherwise, a literal 'X'

- \0
  a NUL character

- \123
  the character with octal value 123

- \x2a
  the character with hexadecimal value 2a

- (r)
  match an 'r'; parentheses are used to override precedence

- (?r-s:pattern)
  apply option 'r' and omit option 's' while interpreting pattern.
  Options may be zero or more of characters 'i', 's', or 'x'

##### User Code Section
- 
  The user code section is simply copied to lex.yy.c varbatim.

##### Comments
- 
  Flex supports C-style comments, '/*' and '*/'.
  
#### Values
##### char *yytext
- 
  holds the text of the current token.
  It may be modified but not lengthened(you cannot append characters to the end)

##### int yyleng

##### FILE *yyin

##### void yyrestart( FILE *new_file )

##### FILE *yyout

##### YY_CURRENT_BUFFFER

##### YY_START
#### Command
- 
  flex file.l

#### Memo
##### yywrap()
- 
  must supply a yywrap() function of your own, or link to libfl.a, or use "%option noyywrap"
### yakk/bison
- 
  Bison is a general-purpose parser generator hat converts a grammar description for an LALR(1) context-free grammer into a C program to paree that grammer.

- [[http://dinosaur.compilertools.net/bison/index.html][Bison The YACC-compatible Parser Generator]]

#### Bison Grammer File
##### Outline
%{
C declarations
%}

Bison declarations

%%
Grammer rules
%%
Additional C code

##### C Declarations
- 
  containing macro difinitions and declarations of functions and variables that are used in the actoins in the grammar rules.

##### Bison Declarations
- 
  containing declarations that define terminal and nonterminal symbols, specify precedence, and so on.
  In some simple grammars you may not need any declaratios.

##### Grammar Rules
- 
  containing one or more Bison grammar rules, and nothing else.

##### Additoinal C Code
- 
  this section is copied by verbatim to the end of 

#### Symbols
- 
  symblos represent the gramatical classifications of the language.

##### Terminal symbol (token type)
###### Kind
####### named token type
- wirtten with an identifier, like an identifier in C.
  
####### character token type (literal character token)
####### literal string token
##### Nonterminal symbol
##### Declare
###### %union
- Declare the collection of data types that semantic values may have
  %union {
    double val;
    symrec *tptr;
  }
###### %token
- Declare a terminal symbol with no precedence or associativity specified
- basic way
  %token name
- by appending an integer value
  %token NUM 300

###### %right
- Declare a terminal symbol that is right-associative
###### %left
- Declare a terminal symbol that is left-associative
###### %nonassoc
- Declare a terminal symbol that is nonassociative
###### %type
- Declare the type of semantic value for a nonterminal symbol
###### %start
- Specify the grammar's start symbol
###### %expect
- Declare the expected number of shift-reduce conflicts
###### %pure_parser
#### Command
- 
  bison --yacc -dv file.y
#### Memo
##### yyclearin
- 先読みしたトークンを捨てる
##### yyerrok
- エラー状態から復帰したことをyaccに通知する

## Memo
### Parser
#### LL(k)
- 
  Top-down parsers.
  Leftmost Derivation.

#### LR(k)
- 
  Bottom-up parsers.
  The L means that the parser reads intput text in one direction, typically Left to Right.
  The R means that the parser produces a reversed Rightmost derivation
  
##### LALR(k)
- Lookahead LR
  

##### SLR
- Simple LR
### Intern
- 
  プログラムに登場する識別子を登録するデータ構造を作って、
  新たに登場した識別子が登録されていればそのポインタを返し、なければ登録してそのポインタを返す、という操作。

### プログラミング言語を作る
