# Computer Science
## Glossary
### Type safe
- 型安全性
  http://postd.cc/what-is-type-safety/
### Memory safe
- メモリ安全性
### Liskov substitution principle リスコフの置換原理
- オブジェクト指向プログラミングにおける派生型の定義の一種。
### 数の表現方法
#### HEX
#### BIN
#### BCD - binary coded decimal notation
- 1桁に4ビットずつ割り振る。
- http://www.system-brain.com/bcd.htm
#### OCT
#### BIN - binary
### Amdahl's law アムダールの法則
- 計算機の並列度を上げた場合に、全体として期待できる性能向上の程度を数式として表現したもの。
## Memo
### Evaluation
#### normal-order evaluation
- 正規順序の評価
  完全に展開し、簡約する

#### applicative-order evaluation
- 作用的順序の評価
  引数を評価し、作用させる

### bound variable
- 
  
### Scope
#### Level
##### Expression

##### Block

##### Function

##### File

##### Module

##### Global

#### Kind
- [[https://en.wikipedia.org/wiki/Scope_(computer_science)][Scope (computer science)]]
##### Lexical/Static Scope 
- 字句を解析した時点でスコープが決定する。
  ソースの構造で外枠（外側の環境）が決定する。
##### Dynamic Scope
- 静的スコープに加え、実行時に親子関係の子側から親側のスコープを参照できるスコープ。
  このとき参照されるのは、親子関係を親側に辿り、より近いブロックにある変数。
### Order of growth

#### Big O

#### Theta
### Two Hard Things
- 
  There are only two hard things in Computer Science:
  cache invalidation and naming things.
  -- Phil Karlton
