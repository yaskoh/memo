# Dired
## About
- Start
  M-x dired (C-x d)
  
## Dired Command
### Open Files
#### RET
- ファイルを開く
#### e
- ファイルを開く
#### f
- ファイルを開く
#### a
- ファイルを開いた後にDiredバッファを削除する
  最初はdisableになっている。
#### o
- バッファの隣のウィンドウでファイルを開く。
  ウィンドウが分割されていないときは分割する。
#### C-o
- diredの横にファイルを開くが、ウィンドウは選択しない。
#### v
- カレントバッファを切り替えるが、その後にview-modeにする。
### ファイル編集
#### C
- コピー
#### D
- 削除
#### R
- リネーム・移動
#### H
- ハードリンク作成
#### S
- シンボリックリンク作成
### マーク
#### m
- マークをつける
#### u
- マークを外す
#### t
#### U
#### M-{
#### M-}
#### % m
#### * %
#### % g
### 削除
#### d
- 削除フラグを付ける
#### x
- 削除フラグが付いたファイルを本当に削除する
#### #
#### ~
#### % &
#### % d
#### * c *
#### * c D *
#### DEL
- 前の行に移動し、その行の削除フラグを消す。
### シェルコマンド
#### ! (dired-do-shell-command)
### ディレクトリ操作
#### g (revert-buffer)
- ディレクトリの再読み込み
#### i (dired-maybe-insert-subdir)
- サブディレクトリの一覧を追加する
#### > (dired-next-dirline)
#### < (dired-prev-dirline)
#### C-M-n (dired-next-subdir)
#### C-M-p (dired-prev-subdir)
#### + (dired-create-directory)
- ディレクトリを作成する
### ヘルプ
#### h (describe-mode)
#### q (quit-window)
## wdired
- M-x wdired-change-to-wdired-mode
- C-c C-c (wdired-finish-edit)
  変更を反映
- C-c C-s
  変更を反映
- C-c C-k
  変更の取り消し
- C-c ESC (wdired-abort-changes)
  変更の取り消し
## dired-hide-details-mode
## dired-toggle
- M-x dired-toggle (F5にキー設定中)
  画面右側にディレクトリを表示する。

## Memo
### dired-details
- 
  ⇒24.4以降では"dired-hide-details-mode"が入ったため、そちらを利用することに。。
- Command
  - ) (dired-details-show)
  - ( (dired-details-hide)

## Link
- [[http://rubikitch.com/category/dired/][#7 多機能ファイラー「dired」 (Software Design 2014年11月号掲載記事) Emacs dired wdired インストール 設定 使い方 - るびきち「日刊emacs」]]
- [[http://blog.perforb.com/archives/134][Emacsのファイラとdired]]
- [[http://www.bookshelf.jp/texi/emacs-20.6-man-jp/emacs_29.html][26.ディレクトリエディタdired]]
- http://piro.hatenablog.com/entry/20101216/1292506110
- http://at-aka.blogspot.tw/2006/12/emacs-dired-wdired.html
