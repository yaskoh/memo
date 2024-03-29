# Racket
## About
- 
  Racket is a full-spectrum programming language.
  It goas beyond Lisp and Scheme with dialects that support objects, types, laziness, and more.

## Feature
- Racket is a lexically scoped language.

## Module
- all of the code putting in the definitions window is inside a module.

### Various way of module distributing

- module name "pict/flash" means the module implemented in the "flash.rkt" that is located in the "pict" collection.
  module name including no slash refers to a "main.rkt" file.

- Some modules are distributed through tha PLaneT server, and they can be downloaded automatically on demand.

### slideshow

### racket/class
- 
  class module

### racket/gui/base
- 
  
## Class
- 
  class names are end with %.
  using them, import racket/class.

### new
- 
  creates an instance of a class.

### send
- (send instance method boolean)
  calls a method of the instance object.

## Function
### define
- 
  define an identifier.

### let
- (let ([bind1 data1] [bind2 data2] ...))
  binds many identifiers at once.

### let*
- (let* ([bind1 data1] [bind2 data2(<-bind1 is availale here)] ...))
  it can use some bindings which is difined former in itself in later bindings.

### lambda
- (lambda (arg) (funcion))
  creates anonymous function.

### list
- (list v1 v2 ...)
  make list.

### map
- (map function list)
  apply the function to each element of the list, and returns the result-combined list.

### apply
- (apply function list)
  apply the function to all the elements of the list at once.
  function needs to take any number of arguments.

### require
- (require module)
  import additional funcions from module.

### provide
- (provide function ...)
  provide functions on another module when it's required.

### circle
- (circle size)
  draw a circle

### rectangle
- (rectangle width height)
  draw a retangle.

### Pict Combines

#### append
- v & h
  v is "virtically", and h is "horizontally".

- v align
    - l left
    - c center
    - r right


##### vl-append
##### vc-append
##### vr-append
##### ht-append
##### htl-append
##### hc-append
- (hc-append [d] picture1 picture2)
  combines pictures.
  The part of name "h" means "horizontally", and "c" is "centered vertically"

##### hbl-append
##### hb-append


#### superimpose

### colorize
- (colorize figure color)
  colorize a figure.

### code
- 
  syntax.

### define-syntax
- 
  
### sytax-rules
- 
  
## DrRacket
### Help
- F1

### Display
#### Definitions Window
- upper : definition area
  for defining programs
#### Interactions Window
- lower : interaciton area
  for evaluating Racket expressions interactively.
#### Status Line
## Link
- [[http://docs.racket-lang.org/][Racket Documentation]]
