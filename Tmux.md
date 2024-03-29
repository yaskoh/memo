# tmux
## Commands
- tmux [-2Cluv] [-c shell-command] [-f file] [-L socket-name] [-S socket-path] [command [flags]]
### Tmp
#### ls
#### attach
### Option
#### show-options 
#### show-window-options
#### set-option / set
#### set-window-option / setw
#### list-keys
#### bind-key / bind
#### unbind-key / unbind
### Server
#### kill-server
### Session
#### kill-session
### Window
#### new-window
#### move-window / movew
#### swap-window / swapw
#### choose-window
### Client
#### detach-client
#### choose-tree
### Buffer
#### delete-buffer / deleteb
## Key Bindings
### Client
#### d : detach-client

### Session
#### ( : switch-client -p
#### ) : switch-client -n
#### s : choose-tree
#### $ : command-prompt -I #S "rename-session '%%'"

### Window
#### c : new-window

#### w : choose-window

#### l : last-window
#### n : next-window
#### p : previous-window

#### 0 : select-window -t :0
#### 1 : select-window -t :1
#### 2 : select-window -t :2
#### 3 : select-window -t :3
#### 4 : select-window -t :4
#### 5 : select-window -t :5
#### 6 : select-window -t :6
#### 7 : select-window -t :7
#### 8 : select-window -t :8
#### 9 : select-window -t :9
### Pane
#### Move pane
##### q : display-panes
##### o : select-pane -t :.+

##### ; : last-pane

##### -r Up : select-pane -U
##### -r Down : select-pane -D
##### -r Left : select-pane -L
##### -r Right : select-pane -R

#### Arrange pane
##### z :resize-pane -Z
- paneをフルサイズに。再度行うと元の分割状態に戻る。
##### " : split-window
##### % : split-window -h
##### ! : break-pane
- 別のWindowに分離させる
##### { : swap-pane -U
##### } : swap-pane -D
#### Layout pane
##### space : next-layout
##### M-1 : select-layout even-horizontal
##### M-2 : select-layout even-vertical
##### M-3 : select-layout main-horizontal
##### M-4 : select-layout main-vertical
##### M-5 : select-layout tiled
#### Resize pane
- C-矢印キーでPaneサイズを調整。M-矢印キーだとまとめて移動。
##### -r C-Up : resize-pane -U
##### -r C-Down : resize-pane -D
##### -r C-Left : resize-pane -L
##### -r C-Right : resize-pane -R
##### -r M-Up : resize-pane -U 5
##### -r M-Down : resize-pane -D 5
##### -r M-Left : resize-pane -L 5
##### -r M-Right : resize-pane -R 5

### Copy buffer
#### [ : copy-mode
#### - : delete-buffer
#### # : list-buffers

### Meta
#### t : clock-mode
#### ? : list-keys
#### ":" : command-prompt

### List
(Bind-key ?)
- C-z        suspend-client
- &          confirm-before -p "kill-window #W? (y/n)" kill-window
- '          command-prompt -p index "select-window -t ':%%'"
- ,          command-prompt -I #W "rename-window '%%'"
- .          command-prompt "move-window -t '%%'"
- =          choose-buffer -Z
- D          choose-client -Z
- L          switch-client -l
- ]          paste-buffer
- f          command-prompt "find-window '%%'"
- i          display-message
- r          refresh-client
- x          confirm-before -p "kill-pane #P? (y/n)" kill-pane
- ~          show-messages
- PPage      copy-mode -u
- M-n        next-window -a
- M-o        rotate-window -D
- M-p        previous-window -a
## Settings
### Optionの種類
- "set-option"は"set"というエイリアスがある。
  例: set-option -g -> set -g
#### Server Option サーバーオプション
- set-option -s
- tmuxのサーバプロセス全体で共有される
#### Session Global Option セッショングローバルオプション
- set-option -g
- セッション全体で適用される
#### Session Option セッションオプション
- tmux set-option
- 個別のセッションでオプションを上書きする
#### Window Global Option ウィンドウグローバルオプション
- set-optoin -w -g
- ウィンドウ全体で適用される
#### Window Option ウィンドウオプション
- set-option -w, (set-window-option, setw)
- 個別のウィンドウでオプションを上書き
### Optionの表示
- tmux show-options [-s|-g|-w|-wg]
- tmux show-options -wg = tmux show-window-option -g
## Structure
- https://qiita.com/sainuio/items/b7e04182e1dd8cb3bbd6
### Session
### Window
### Pane
## Reverse Lookup
### Paneを他のWindowに移す
- :join-pane -t :WindowNum
  Windowタブ番号は":2"のようにコロンの後に番号を置く。
### Windowの番号を動かす/Swapする
- 移動
  :move-window -t TabNum
- スワップ
  :swap-window -t TabNum
### tmuxの設定をOSによって切り替える
- if-shellを.tmux.confで使う。
- https://kiririmode.hatenablog.jp/entry/20150207/1423296151
### プレフィックスなしのキーバインドを使う
- bind-key -n KEY COMMAND
- https://blog.monochromegane.com/blog/2013/12/12/tmux-no-prefix/

- bind-key -T root KEY COMMAND
- https://mynavi-agent.jp/it/geekroid/2017/03/-11tmux.html
## Memo
### Copy/Paste
#### Windows
- Shiftを押しながらマウスを動かす・右クリックすると、
  コピーやペースト等の操作ができる。

#### Mac
- もともとコピペがうまく動かない。以下を導入
  - brew install reattach-to-user-namespace
  - .tmux.confで
    - set-option -g default-command "reattach-to-user-namespace -l zsh"
### Mouse
- tmux 2.1からmouse設定が変更になった模様。
  [[http://qiita.com/jyotti/items/70a3a8035d767f99f93d][tmux v2.1からmouse関連の設定が変わった - Qiita]]
  [[https://github.com/NHDaly/tmux-better-mouse-mode][tmux-better-mouse-mode]]

- Macでスクロールしたい場合は、まずPrefix + [を押して、copy modeに入るとよい。
  https://superuser.com/questions/1084487/scrolling-on-mac-with-tmux-and-iterm
  
## Link
- [[https://tmux.github.io/][tmux]]
- https://wiki.archlinux.jp/index.php/Tmux

- tmp
  - https://qiita.com/succi0303/items/cb396704493476373edf
  - https://qiita.com/b4b4r07/items/01359e8a3066d1c37edc
  - https://qiita.com/vintersnow/items/3d7e25d520bc7deefc77
  - https://qiita.com/Frog_woman/items/f6797f2a70c44e42863d
  - http://engineerspirit.com/2016/12/25/post-407/
  - https://mynavi-agent.jp/it/geekroid/2017/03/-11tmux.
