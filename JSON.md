# JSON
- JavaScript Object Notation
## Fundamental
- Objectが第一、Array、Pairが準上位構造、のイメージ。
  ただし上下関係は特にない。Array, Pairの下層にもObjectは使える。
## Structure
### JSON Values
- value
  - object
  - array
  - number
  - string
  - true
  - false
  - null

### Objects
- object
  - {}
  - { members }

- members
  - pair
  - pair, members

- pair
  - string : value

### Arrays
- array
  - []
  - [ elements ]

- elements
  - value
  - value, elements

### Numbers
- number
  - int
  - int frac
  - int exp
  - int frac exp

- int
  - digit
  - digit1-9 digits
  - - digit
  - - digit1-9 digits

- frac
  - . digits

- exp
  - e digits

- digits
  - digit
  - digit digits

- e
  - e
  - e+
  - e-
  - E
  - E+
  - E-

### String
- string
  - ""
  - " chars "

- chars
  - char
  - char chars

- char
  - any-Unicode-character-except-"-or-\-or-control-character
  - \"
  - \\
  - \/
  - \b
  - \f
  - \n
  - \r
  - \t
  - \u four-hex-digits
## Link
- [[https://www.ietf.org/rfc/rfc7159.txt][RFC7159]]
- [[http://json.org/json-ja.html][JSONの紹介]]
- [[http://www.ecma-international.org/publications/files/ECMA-ST/ECMA-404.pdf][ECMA-404 The JSON Data Interchange Standard.]]

