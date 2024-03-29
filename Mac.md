# Mac
## Framework
- Cocoa Framework
  Foundation
  AppKit(GUI)
  CoreData(Database)
- Cocoa Touch Framework
  Foundation
  UIKit(GUI)
- Carbon
  (XCode 4以降はサポートされず)

## Tools
### brew
#### Synopsis
- brew --version
- brew command [--verbose|-v} [options] [formula] ...
#### Commands
##### install formula
##### remove formula
##### update
##### list
##### link
- リンクを更新する
###### --force
###### --overwrite
##### search text|/text/
##### services
###### start
- サービスを実行。brew services start mongodb-community、など。
###### stop
- サービスを停止。brew services stop mongodb-community、など。
###### lists
- サービスのリストを表示。brew services list
##### audit
##### tap <user/repo>
  taps a formula repository from GitHub using HTTPS.
#### Memo
##### Install
- 公式ページ記載のスクリプトを実行
  https://brew.sh/index_ja.html
- updateがうまくいかなかった場合にも、
  公式ページからのスクリプトを実行するとうまく動いた。
##### brewをupdate
- cd $(brew --prefix)
  git fetch origin
  sudo git reset --hard origin/master
##### FormulaのInstall先
- /usr/local/Celler
##### brewのlinkを更新
- https://qiita.com/halo57/items/e7511f3befbcb9fedd6a
## Commands
### BSD
#### dd
#### diskutil(8)
- diskutil [quiet] verb [options]
##### VERBS
###### erase Disk format name device
###### list
###### unmount | unmount [force] device
###### mount
#### hdiutil(1)
- hdiutil verb [options]
- manipulate disk image
##### Options
##### Verbs
###### help
###### attach
###### convert image -format format -o outfile
- convert image to type format and write the result of outfile.
####### Format
- UDRW - UDIF read/write image
#### sync(8)
- force completion of pending disk writes (flush cache)
### softwareupdate
#### Link
- [[https://qiita.com/qoAop/items/7baae4c35d3af0060414][macOSのソフトウェアアップデートはコマンドラインで - Qiita]]

## Reverse lookup
### lsblkやblkidのようにディスクを調べる方法
- "diskutil list"を利用する
### mount用diskを作る
- diskutil list
  デバイス名を調べる。/dev/disk2など。
- diskutil eraseDisk MS-DOS USBTitle
  フォーマット
- diskutil unmount diskx
  ディスクをアンマウント
- dd if=imagefile of=/dev/disk2 bs=4k
  書き込む
- diskutil eject /dev/disk2
  取り出す
## Applications
### magnet
- 画面の
### windscribe
- VPN. mac & chrome ext.
  https://windscribe.com/
### Paragon
## Memo
### キーバインド
- 変更点
  - Control <-> Caps lock
  - Emacs
    - Command -> meta
    - SpotlightがCtrl+Spaceで当たっていたが、Command+Spaceに変更できた（現在はデフォルト？）
### マウスのスクロール
- マウスを使う場合、ウィンドウズとスクロールが逆。変更できる。
  システム環境設定→マウス→スクロールの方向：ナチュラル、のチェックを外す。
- https://itips.krsw.biz/reverse-direction-of-scroll-in-mac-os/
### 特殊キー
- ⌘ : Command コマンド
- ⌥ : Option, Alt オプション、オルト
- ⌃ : Control コントロール
- ⇧ : Shift シフト
### 写真の取り込み
- 2017/10/18は、イメージキャプチャで取り込んだ。
  写真だと日付や番号が見えないため、これが早いかも。
### NSSObject
- 
  すべてのオブジェクトのもと

### ARC(Automatic Reference Counting)
- 
  メモリ管理。コンパイラがコードを解析し、自動でメモリを解放。

### clang
- 
  Apple LLVM Compilerのコマンド。

### 画面の整理
#### magnet (app)
- Ctrl+Alt+αで制御。便利。
#### split window
- 最大化ボタンを長押し、半分のどちらかに寄せる。
  もう一つの画面をもう一つの半分の画面で選択する。
#### 画面最大化
- Ctrl + Opt + yで画面最大化

#### Mission Control
- Ctrl + ↑ : MissionControl （3本指上スワイプと同様）
- Ctrl + ↓ : アプリケーションウィンドウ （アプリの一覧）
- Ctrl + ← / → : 別デスクトップへの移動
### スライドショー
- 
  Space押すと出てくる画面を使うと話が早い。プレビューではできないようなので。。

### ウムラウトやアクセント記号の入力方法
#### キーボードショートカットで入力する方法
- 
  |----------+------------+------------|
  | Shortcut | Name       | Example    |
  |----------+------------+------------|
  | Opt + E  | acute      | café       |
  | Opt + U  | umlaut     | Übermensch |
  | Opt + i  | circumflex | être       |
  | Opt + N  | tilde      | España     |
  | Opt + C  |            | façade     |
  | Opt + _  | grave      | Voilà!     |
  | Opt + ?  |            |            |
  | Opt + 1  |            |            |

- 
  [[http://inforati.jp/apple/mac-tips-techniques/system-hints/how-to-enter-umlaut-diacritic-cedilla-with-macos.html][Macでウムラウトやアクセント記号などを入力する方法 - Inforati]]
  [[http://inforati.jp/apple/mac-tips-techniques/system-hints/how-to-use-special-characters-and-symbols-keyboard-shortcut-with-macos.html][Mac 記号や特殊文字のキーボードショートカットまとめ（133種類） - Inforati]]

### backslash / yen
- 
  デフォルトでyen signが出力される状態となっている。
  IMEを操作することで、デフォルトを\に変更可能。

- 
  http://www.glamenv-septzen.net/view/1119
### wheel
- 
  特権を持つユーザグループ
  http://superuser.com/questions/191955/what-is-the-wheel-user-in-os-x
### 「開発元が未確認のため開けません」の対処
- Ctrl+クリック、で開く
- 「セキュリティとプライバシー」から許可設定をする
### アプリのアンインストール
- App Storeダウンロード: Launch Padから削除する
- その他: アプリケーションを選択し削除
  https://support.apple.com/kb/PH25083?viewlocale=ja_JP&locale=ja_JP
### Hibernation / Sleep ハイバネーション、スリープ
- スリープ、セーフスリープ、ディープスリープの三種類が存在。

- http://inforati.jp/apple/mac-tips-techniques/system-hints/how-to-change-the-sleep-mode-of-mac.html
- http://www.hachim.jp/study-by-incident/mac-sleepimage.html
- http://weble.org/2012/04/09/mac-deep-sleep
### デスクトップの移動
- タッチパッドを使わずにキーボードで移動したい場合、Ctrl+矢印キー。
## Link
- [[http://www.jmuk.org/diary/index.php/2009/02/06/0/][伝統的なUNIXユーザがMac OSXを使うときにはまるポイント - val it: a -> a = fun]]
