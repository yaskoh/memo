# sed
## Commands
### ;
  label

### #
  comment
  長らく最初の行のみコメントとして有効だったが、
  最近はわりと、どこでも#から始まるものはコメントとして処理されるらしい。

  一行目の"#n"は"-n"と同じ意味になるとのこと。普通は最初の行はシバン。
  "#!/bin/sed -nf"は使えるが、"#!/bin/sed -fn"だとファイル名が"n"と認識されてしまうらしい。

### {....}
  Block

### =
  print line number
### a \
  Append
### b label
  Branch
### c \
  change
### d and D
  Delete
  行を削除する
### g and G
  Get
### h and H
  Hold
### i \
  Insert
### L
  Look
### n and N
  Next
### p and P
  Print
  行を出力する
### q
- 
  Quit、終了

### r filename
  Read File

### s/..../..../
  Substitute

  正規表現で置換処理をする。
    ex) sed s/day/night/ <old >new
  なくても動くが、クオートをつけるほうが好ましい。
    ex) sed 's/day/night/' <old >new

  パターンマッチした文字列を & で取得できる。
    ex) echo 123 abc | sed 's/[0-9]*/& &/'
        ⇒123 123 abc
  正規表現に"+"は本来ないが、GNU sedに"-r"オプションをつけると使えるようになる。
  (extended regular expressions).

  parenthesis()をつけてマッチしたものは、\1, \2という形で再利用できる。
    ex) echo you do | sed -r 's/([a-z]+) ([a-z]+)/\2 \1/'
        ⇒do you
  検索側の条件にも使える。
    ex) echo abc abc xyz | sed 's/\([a-z]*\) \1/\1/'
        ⇒abc xyz
  （最初の3文字を逆順にする）
    ex) echo 123456 | sed 's/^\(.\)\(.\)\(.\)/\3\2\1/'
        ⇒321456

### t label
  Test

### w filename
  Write FileName

### x
  eXchange
### y/..../..../
- 
  Transform
  一文字ずつ置換

## Pattern Flags
### /num (/2, /3...)
  末尾に数字を入れると、処理を開始する最初のパターンを指定できる。
  2番目の文字を消す場合：
    ex) echo Aa Bb Cc Dd | sed 's/[a-zA-Z]* //2'
        ⇒Aa Cc Dd
  2番目以降の文字を消す場合：
    ex) echo Aa Bb Cc Dd | sed 's/[a-zA-Z]* /DELETED /2g'
        ⇒Aa DELETED DELETED Dd
        (最後のDdはスペースの問題か変換されなかった。)

### /g
  Global
    ex) sed 's/[^ ]*/(&)/' <old >new
        (oldファイルの中身のうち、行の最初の単語に括弧がつく。)
        sed 's/[^ ]*/(&)/g' <old >new
        (oldファイルの中身のうち、すべての単語に括弧がつく。)

### /I
  Ignore Case
  パターンマッチの大文字小文字を無視する。
  以下の例ではabc, aBc, ABC, AbC...等にマッチする。
    ex) sed '/abc/I' <old >new

### /p
  Print
  表示させる。デフォルトでオン。
  -nオプションをつけた場合に、編集行や該当行のみ出力するためのオプション。
    ex) sed -n 's/pattern/&/p' <file
  -nフラグがない場合は、マッチした場合2回表示する。

### /w filename
  Write Filename
  ファイルに書き込む。
  以下の例では、"even"ファイルに結果が書き込まれる。
    ex) sed -n 's/^[0-9]*[02468] /&/w even' <file

## Command Line Options
### -e script
- 
  指定したスクリプト（条件式）で変換処理を行う。
  その後の文字列が編集用であることを示す。
  編集用コマンドが1つだけの場合は省略できるので、複数のコマンドをつなぐ場合に使う。
    ex) sed -e 's/a/A/' -e 's/b/B/' <old >new
  ちなみに、パイプでつなぐとプロセスが二つあがるため、-eでつなぐのが良い。

### -f scriptfile
- 
  指定したファイルに記述されているコマンドやスクリプトに従って処理を行う。
  ex) sed -f sedscript <old >new

### -h (--help)
- 
  sed -h or sed --help

### -i
- 
  ファイルを結果で置き換える。

### -n (--quiet, --silent)
- 
  パターンスペースの自動出力を抑制する。
  デフォルトではすべて出力するが、出力を抑制することになる。
  /pとあわせて使う場合が多い。

### -V
- 
  Version
  sed -v or sed --version

## Meta Characters
## etc
- The slash as a delimiter
  習慣的に/(slash)をデリミタに使う場合が多いが、特にスラッシュである必要はない。
    ex) _の場合： sed 's_/usr/local/bin_/common/bin_' <old >new
        :の場合： sed 's:/usr/local/bin:/common/bin:' <old >new

- Is sed recursive?
  パターンがマッチした後、次のマッチは残りの文字列を探しに行くので、
  下の例のようなコマンドも停止する。
    ex) sed 's/loop/loop the loop/g' <old >new

- Note the space after the "*" character
  スペースがない場合、長いこと結果が返ってこないバグがある（あった）。
    ex) x? : sed 's/[a-zA-Z}*//2' <old >new
        o  : sed 's/[a-zA-Z}* //2' <old >new

- Combining substitution flags
  フラグは組み合わせて使ってよい。
  ただし"w"は最後に置く必要あり。
    ex) sed -n 's/a/A/2pw /tpm/file' <old >new

- Quoting multiple sed lines in the Bourne shell
  bshでは複数行にsedスクリプトを書きたい場合に以下のように書ける。
    ex) #!/bin/sh
        sed '
        s/a/A/g
        s/e/E/g
        s/i/I/g' <old >new
  ちなみにcshでは以下のように書かなくてはいけない。
    ex) #!/bin/sh
        sed -e 's/a/A/g' \
            -e 's/e/E/g' \
            -e 's/i/I/g' <old >new

- 最短一致
  基本最長一致で、また特に最短一致のためのオプションもないことから、工夫する必要がある。
  たとえばタブを取得したいなら、
      sed s/\<[^\>]*\>//g test.html
  として、>以外のものが続く間だけマッチングさせるなど。
  [[http://techtipshoge.blogspot.jp/2011/10/sed.html][Tech Tips - sedの最短一致]]

## Link
- [[http://www.grymoire.com/Unix/Sed.html][Sed - An Introduction and Tutorial by Bruce Barnett]]

