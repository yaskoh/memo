# Markdown
## About
- 
  Markdown is a lightweigt markup language.
  It's designed to be able to convert to HTML.

- Extention
  .md

- Developed by
  John Gruber, in 2004

## Notation
### Paragraphs
- 
  Paragraphs are separated by another by one or more blank lines.
  - ex
    Paragraph 1,
    and this is 1, too.
    
    And here Paragraph 2.

### Headings
- #
  Use # symbols to express headings.
  The nmuber of # determine the size of the heading.
  
  - ex
    # The largest heading (<h1> tag)
    ## The second largest headings (<h2> tag)
    
- Lagest Headings
  You can use ======= and ------- to show header 1 and 2.

  - ex
    Header 1
    =======
    Header 2
    -------

### Blockquotes
- >
  Indicate blockquotes with a >.
  
  - ex
    > This line is quotes.

### Styling text
- *(Italic)
  A * or an _ around the text indicate emphasize.
  - ex
    *This text will be italic*

- **(Bold)
  Two * or _ makes your text bold.
  - ex
    **This text will be bold**

- ***(Italic and Bold)

### Lists
#### Unordered lists
- * / -
  unordered list is created by a * or a -.
  
  - ex
    * Item1
    * Item2
    
    - Item1
    - Item2

#### Ordered lists
- Number(such as 1., 2., etc)
  - ex
    1. Item1
    2. Item2
    3. Item3

#### Nested lists
- 
  Lists can be nested by indenting by two spaces.

  - ex
    1. Item 1
       1. Item 1-1
       2. Item 1-2
    2. Item 2
       * A Unorderd Item of 2
         * Item 2-1-1
         * Item 2-1-2

### Code formating
- `(Inline formats)
  Use single backticks (`) to format text as a code foramt, a special monospace format.
  
- ```(Multiple lines)
  Triple backticks(```) create a code formatting block.
  
  - ex
    ```
    x = 0
    x = 2 + 2
    what is x
    ```

### Links
- [] and ()
  link text in brackets[], and then wrapping the link in parentheses().
  
  - ex
    [Github](https://www.github.com)
  
## Cheatsheet
### 2023/8/6追加
- 見出し： #の数で表す
- リスト： -, +, *。tabで階層化。
- 数字リスト： 1., 2.などで記載
- 区切り線： ***, ---, ___ など3つ以上並べて入力
- 強調： 左のように、** で囲む **
- リンク： [リンク名] (URL)
https://qiita.com/Hase-pro/items/16379a0c83f2725e3a11

### 昔のやつ
見出し1
============

見出し2
------------

# 見出し1

## 見出し2

### 見出し3

#斜字*
##太字**
### 斜体で太字***

~~取り消し線~~

<details><summary>サマリ</summary>

###
線を引く

---

 * 箇条書き
 * 箇条書き2
   * 箇条書き3
     * 箇条書き4
 - 箇条書き1
   - 箇条書き2

1. 数字1
1. 数字2
1. 数字3

</details>

- [ ] チェックボックス
- [ ] test

> 引用
>> 二重引用

[リンクのテキスト](http://google.com "タイトル")

![画像の代替テキスト](http://google.com "タイトル")

```python
# python code
import numpy
import pandas
```

```c++
#include <iostream>
using namespace std;
```

## Link
- [[https://help.github.com/articles/markdown-basics/][Markdown Basics - GitHub Help]]
