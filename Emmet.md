# Emmet
## About
### Element types
#### Snippets
#### Abbreviations
#### Aliases
### "Lorem Ipsum" generator
- lorem(num)
## Syntax
### Elements
- Any names to generate HTML tags.
### Nesting operators
#### Child: >
- nest elements inside each other
#### Sibling: +
- place elements near each other, on the same level.
#### Climb-up: ^
- climb one level up by each one operator, and can use as many as you want.
#### Multiplication: *
- define elements many times
#### Grouping: ()
### Attribute operators
#### ID: #id
#### CLASS: .class
#### Custom attributes: [attr]
- adding custom attributes
#### Item numbering: $
- with multiplicaton * operator, being able to repeat elements,
  also with $, you can number them.
##### Numberning base: $@n
- ex: li.item$@3*5
##### Reverse Direction: $@-
- ex: li.item$@-*5
##### Reverse with base: $@-n
#### Text: {}
- ex
  - a{Click me} -> <a href="">Click me</a>
#### Implicit Tag Name
##### li
- under ul, ol
##### tr
- under table, tbody, thread, tfoot
##### td
- under tr
##### option
- under select, optgroup
##### memo
- on emacs, it works only as <div>
## Abbreviations
### HTML Abbreviation
#### !
#### a
#### a:link
#### a:mail
### CSS Abbreviations
#### alias
##### Value aliases
- p -> %
- e -> em
- x -> ex

- ex
  - w100p -> width: 100%
  - m10p30e5x -> margin: 10% 30em 5px

###### Memo
- 
  連続した数字を入れる場合、"-"で区切ることで上手く入力できた。
  ただし実験結果であり、仕様かは不明。

- ex
  bdrs8-8-8-8 -> border-radius: 8px 8px 8px 8px;

##### Coler values
- ex
  - #1 -> #111111
  - #e0 -> #e0e0e0
  - #fc0 -> #ffcc00
##### - Vender prefix
##### !important modifier
- you can add ! suffix at the end of any CSS abbreviation to get !important value.
#### Visual Formatting
##### pos
- position:relative;
###### pos:s
###### pos:a
###### pos:r
###### pos:f
##### t
- top:|;
###### t:a
##### r
- right:|;
###### r:a
##### b
- bottom:|;
###### b:a
##### l
- left:|;
###### l:a
##### ov
- overflow:hidden;
###### ov:v
- overflow:visible;
###### ov:h
- overflow:hidden;
###### ov:s
- overflow:scroll;
###### ov:a
- overflow:auto;
##### ovx
- overflow-x:hidden;
##### cur
- cursor:${pointer};
###### cur:a
###### cur:d
###### cur:c
###### cur:ha
###### cur:he
###### cur:m
###### cur:p
- cursor:pointer;
###### cur:t
#### Margin & Padding
#### Box Sizing
##### w
- width:|;
##### w:a
- width:auto;
##### h
- height:|;
##### h:a
##### maw
- max-width:|;
#### Font
##### fz
- font-size:|;
#### Text
#### Background
##### bgc
- background-color:#fff;
##### bgc:t
- background-color:transparent;
#### Color
#### Generated content
#### Outline
#### Tables
#### Border
##### bd
- border:|;
##### bdrs
- border-radius:|;
#### List
##### lis
- list-style:|;
##### list
- list-style-type:|;
#### Print
#### Others
### XSL
## Actions
## Filters
## Customization
## Link
- [[http://emmet.io/][Emmet]]
- [[http://docs.emmet.io/cheat-sheet/][Emmet CheatSheet]]

- [[https://blogs.adobe.com/creativestation/serialization/web-learning-emmet][HTML/CSSを爆速コーディング Emmet入門 - Adobe Creative Station]]
