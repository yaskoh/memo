# Scheme
## About
- 
  Scheme is a statically scoped and properly tail recursive dialect of the Lisp programming language.
  
## Release
### R7RS / 2013
## Syntax
- (If needed, this section moves to under Release Sections)
- Syntax
  E ::= K | I | (E_0 E^*) | (lambda (I^*) E2) | (define I E')
  - E : Expressions
  - I : Identifiers(variables)
  - K : Constants

## Lexical conevention
### Identifier
#### !
#### $
#### %
#### &
#### *
#### +
#### -
#### .
#### /
#### :
#### <
#### =
#### >
#### ?
#### @
#### ^
#### _
#### ~
### Whitespace, comments
#### ;  Line comment
#### #;
#### #| |#  Block comment
### Other notations
### Datum labels
## Basic concepts
### Variables, syntactic keywords, regions
## Expressions
### Primitive expression types
#### Variable references
#### Literal expressions
#### Procedure calls
#### Procedures
#### Conditions
#### Assignments
#### Inclusion
### Derived expression type
#### Conditionals
#### Binding constructs
#### Sequencing
#### Iteration
#### Delayed evaluation
#### Dynamic bindings
#### Exception handling
#### Quasiquotation
#### Case-lambda
### Macros
## Program structure
### Import declaratios
### Variable definitions
### Syntax definitions
### Record-type definitions
### Libraries
## Procedures
### Equivalence predicates
### Numbers
### Booleans
### Pairs and lists
### Symbols
### Characters
### Strings
### Vectors
### Bytevectors
### Control features
### Exceptions
### Environments and evaluation
### Input and output
### System interface
### Types
#### Atoms
##### nummbers
##### boolean constants
- #T
- #F
##### empty list
- ()
##### strings
#### Simple Types
#### Composite Types
### Functions
#### defun
- 
  
#### List
##### car
##### cdr
##### null?
##### list
##### length
##### reverse
##### append
#### Boolean
##### +
##### (< )
##### (<= )
##### (> )
##### (>= )
##### (= )
##### eq?
##### eqv?
##### equal?
##### and
##### or
##### not
#### Conditional Expressions
##### if
- 
  
##### cond
- 
  (cond (<p1> <e1>)
        (<p2> <e2>)
        ...
        (<pn> <en>)
        (else <eelse>))

#### Math

##### reminder
## Feature
- scope
  - lexical

#### I/O
##### (read)
##### (write obj)
##### (display obj)
##### (newline)
##### (transcript-on filename)
##### (transcript-off)
## Implementation
### Gauche
- Start at Emacs
  Ctrl+c,s

- define
  ex: (define size 2)
  合成手続き
  ex: (define (square x) (* x x))
  
- cond
  conditional(条件付き)
  (cond (<p1> <e1>)
        (<p2> <e2>)
      ...
      (<pn> <en>))
  ex: (define (abs x)
      (cond ((> x 0) x)
          ((= x 0) 0)
          ((< x 0) -x)))
  
- if
  (if <predicate> <consequent> <alternative>)
  condの場合分けが2つの場合。
  (ifとcondの違いは、condの<e>は式の並び（複数の式)でよいということ。
   順に評価され、最後の値が返る。
   対してifは単一の式である必要あり。)

- and
  (and <e1> ... <en>)
  ある<e>が偽なら残りの式は評価されない。

- or
  (or <e1> ... <en>)
  ある<e>が真なら残りの式は評価されない。

- not
  (not <e>)
  <e>が偽なら真、そうでなければ偽。

## Memo
### functions
#### random
#### remainder
#### string-append
- 
  append strings
#### number->string
#### string->number
#### begin
- 
  evaluate multi lines.
  execute like progn on lisp.

#### begin0
## Link
- [[file:///C:/Users/yasutakk/Downloads/r7rs%20(1).pdf][Revised7 Report on the Algolithmic Language Scheme (pdf)]]
- [[http://www.scheme-reports.org/][Scheme Reprots Process]]
- [[http://www.scheme.com/tspl4/][The Scheme Programming Language]]
- [[https://classes.soe.ucsc.edu/cmps112/Spring03/languages/scheme/SchemeTutorialA.html][Scheme Tutorial]]
- [[https://www.shido.info/lisp/idx_scm_e.html][Yet Another Scheme Tutorial]]
