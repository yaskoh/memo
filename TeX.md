# TeX
## Kind
### LaTeX
- [[https://web.archive.org/web/20080630005635/http://www.latex-project.org/index.html][LaTeX - A document preparation waybackmachine]]
### LaTeX 2e
### pLaTeX 2e
## Expression
- [[http://hooktail.sub.jp/nocategory/latexImpress/][LaTeX表現集]]
### メタ
#### 行内数式
- $で挟み込む。
- ex: $\frac{x}{2}$
#### 別行立て数式
##### 数式番号付き
- \begin{equation}
    数式
  \end{equation}
- ex: 
  \begin{equation}
    \int_{0}^{\infty} \sin x dx
  \end{equation}
##### 数式番号なし
- \[
    数式
  \]
- ex:
- \[
    \sum_{k = 0}^{\infty} \sin x dx
  \]

##### amsmathパッケージ
- \begin{equation*}
    数式
  \end{equation*}

- ex:
  \begin{equation*}
    数式
  \end{equation*}

#### \documentclass{}
#### \title{}
#### \date{}
### 特殊文字
#### 括弧( \left(, \right) )
#### 円周率(\pi)
#### 無限大(\infty)
### 記号
#### 分数(\frac{num}{den})
- ex: $\frac{1}{n}$
#### 三角関数(\sin, \cos, \tan)
#### 対数(\log)
#### 平方根・n乗根(\sqrt[n]{x})
#### 総和(\sum)
#### 総乗(\prod)
#### 積分記号(\int, \int_{min}^{max})
### 添え字
- 上付き : x^{2}
- 下付き : x_{i}
- ex: $x_{i} = n^{5}$
  
### フォント
#### ローマン体
- \mathrm{文字}
- ex: $55 \mathrm{m/s}$
### スペースの扱い
- カンマ区切り文字の場合以下のように書く
  299{,}792{,}458
  {}がないと、数列と解釈されてスペースが入るため。
### 例
\[
  \frac{\pi}{2} =
  \left( \int_{0}^{\infty} \frac{\sin x}{\sqrt{x}} dx \right)^2 =
  \sum_{k=0}^{\infty} \frac{(2k)!}{2^{2k}(k!)^2} \frac{1}{2k+1} =
  \prod_{k=1}^{\infty} \frac{4k^2}{4k^2 - 1}
\]
## Install
### Mac
- 基本的にはMacTeXのpkgをインストールすればOK。

- [[http://doratex.hatenablog.jp/entry/20160608/1465311609][MacTeX 2016 のインストール＆日本語環境構築法 (El Capitan 以前/以後両対応) - TeX Alchemist Online]]
- [[http://qiita.com/hideaki_polisci/items/3afd204449c6cdd995c9][El Capitan / SierraでTeX環境をゼロから構築する方法 - Qiita]]
- [[http://doratex.hatenablog.jp/entry/20151008/1444310306][TeX界の El Capitan 迎撃戦記 - TeX Alchemist Online]]
  
## Tool
### TeXShop
- TeXの総合環境。
## Memo
### TeX Liveのアップデート
- sudo tlmgr update --self --all
### AUCTeX
- https://texwiki.texjp.org/?AUCTeX
## Link
- [[https://texwiki.texjp.org/][TeX Wiki]]
- [[https://www.latex-project.org/][The LaTeX Project]]
- [[https://www.tug.org/index.html][TeX Users Group web site]]
### TeX Live
- [[http://tug.org/texlive/doc/texlive-en/texlive-en.html][The TeX Live Guide - 2016]]
### mactex
- [[http://www.tug.org/mactex/index.html][MacTeX]]
- [[http://doratex.hatenablog.jp/entry/20160608/1465311609][MacTeX 2016 のインストール＆日本語環境構築法 (El Capitan 以前/以後両対応) - TeX Alchemist Online]]
### ghostscript
### dvipng
- [[http://www.nongnu.org/dvipng/][dvipng]]
### libgd
- [[https://libgd.github.io/][gdLibrary]]
- [[https://libgd.github.io/manuals/2.2.3/files/preamble-txt.html][About LibGD 2.2.3]]
### kpathsea
- Kpathsea is a library to do path searching.
- [[http://tug.org/texinfohtml/kpathsea.html][Kpathsea: A library for path searching]]
- [[http://tug.org/kpathsea/][Kpathsea]]

