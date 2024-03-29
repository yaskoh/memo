# Visual Studio Code
## Folder Structure
### ~/.vscode
## Keyboard shortcuts
- Reference Keyboard Shortcuts : Ctrl+K Ctrl+S / Cmd K Cmd S
- Edit: Command Palette -> Open Keyboard Shortcuts (JSON)、keybinding.jsonを変更
  ※Emacsなしは、移動ができないので無理でした。。<-キーバインドはデフォルトで使うことにした。。辛いかもしれない。(2021/7/15)
### Markdown
#### Ctrl + K, V : サイドバイサイドでプレビュー表示
#### Ctrl + Shift + V : 別タブとしてプレビュー表示
### tmp
- Custmize keyboard shortcuts : Ctl K Ctl S / ⌘K ⌘S
- Open : Cmd + O
- : Cmd + P
- Command palette : Cmd + Shift + P
- Change language mode : ⌘K M
- Change theme : ⌘K ⌘T
- User Settings : ⌘,
- Extensions : Shift + Cmd + X 
- Toggle Sidebar : Cmd + B
- Zen Mode : Cmd + K, Z
- Split window : Cmd + \
- Switch between editors : Cmd + 1, Cmd + 2, ...
- Close current folder
### General
### Basic editing
### Link
- https://code.visualstudio.com/shortcuts/keyboard-shortcuts-windows.pdf
- https://code.visualstudio.com/shortcuts/keyboard-shortcuts-macos.pdf
## Structure
### Editor
### Panel
### Side bar
### Activity bar
### Status bar
## Extensions
### Draw.io Integration
#### Memo
##### 拡張子 : drawio.svg
- 拡張子をdrawio.svgとすることで、Drawioのファイルと認識される。
##### テーマ変更
- Preferences -> Settings -> Extensions -> Draw.io Integration -> Themeで変更可能。
##### 画像の種類を追加
- 左下の"More Shapes..."から各種画像セットを追加可能。AzureとかAWSなども可。
      
#### Link
- [[https://syachiku.net/vscodedrawioaws/][VScodeでdraw.ioを使ってAWS図面を作ってみる - SyachikuLOG]]
     
### Obsolete
#### Emacs Keymap
#### Org Mode
## Docs
### Overview
### Setup
#### Overview
##### Cross platform
##### Update cadence
- releases a new version each month
  - most plaftorms support auto updateing
  - manually : Help > Check for Updates...
##### Additional components
##### Extensions
#### Linux
#### Mac
#### Windows
#### Network
#### Additional Components
### Get Started
#### Intro Videos
#### Tips and Tricks
##### Basic
###### Getting Started
###### Command Palette
- Win: Ctrl+Shift+P, F1
- Mac: ⇧⌘P
###### Default keyboard shortcuts
- See right on the Command Palette
###### Keyboard Reference Sheets
- https://code.visualstudio.com/shortcuts/keyboard-shortcuts-windows.pdf
- https://code.visualstudio.com/shortcuts/keyboard-shortcuts-macos.pdf
###### Quick Open
- Win: Ctrl+P
- Mac: ⌘P

- ? to view help suggestions
###### Navigate
###### Open multiple files
- Right arrow key will open in background and can continue selecting files.
##### Command line
- code .
- code -r .
- code -n
- code --locale=es
##### Status Bar
###### Errors and Warning
###### Change language mode
##### Customization
##### Extensions
##### Files and Folders
##### Editing Hacks
##### IntelliSense
##### Snippets
##### Get integration
##### Debugging
##### Task Runner
##### Insiders builds
#### User Interface
#### Themes
#### Settings
#### Key Bindings
#### Display Language
### User Guide
### Language
## Memo
### 言語設定を変更
- コマンドパレットで"Configure Language" -> locale.jsonが開く
  "locale:en-US"
- https://qiita.com/tinymouse/items/13d6e3564581a3199d32
### 設定の共有
#### Settings Sync (VSCode)
- Turn On Settings Sync...
  https://forest.watch.impress.co.jp/docs/news/1240071.html
#### old
##### 設定ファイルの場所
- Windows: %APPDATA%\Code\User\settings.json
- Mac: $HOME/Library/Application Support/Code/User/settings.json
- Linux: $HOME/.config/Code/User/settings.json
##### Settings Sync
- Synchronize Settings, Snippets, Themes, File Icons, Launch, Keybindings, Workspaces and Extensions
  Across Multiple Machines Using GitHub Gist.
  https://marketplace.visualstudio.com/items?itemName=Shan.code-settings-sync
## Link
- Visual Studio Code - Docs
  - [[https://code.visualstudio.com/docs][Getting Started - Visual Studio Code - Docs]]
  - [[https://code.visualstudio.com/docs/getstarted/introvideos][Introductory Videos - Visual Studio Code - Docs]]
  - [[https://code.visualstudio.com/docs/getstarted/tips-and-tricks][Visual Studio Code Tips and Tricks - Visual Studio Code - Docs]]


- [[https://www.atmarkit.co.jp/ait/articles/1507/10/news028.html][Visual Studio Codeの使い方、基本の「キ」 - @IT]]

- https://qiita.com/sensuikan1973/items/74cf5383c02dbcd82234?utm_content=buffer4ae03&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer

- https://code.visualstudio.com/docs/setup/mac
