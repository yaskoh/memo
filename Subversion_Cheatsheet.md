# Subversion Cheatsheet
## svn
- svn import -m "message" soourcePath repositoryURL
- svn [checkout|co] file:///repoUrl [localName]
  - svn co -r N svnPath [localName]
- svn status fileName
  - svn status -v
  - svn status {--show-updates | -u}
- svn diff fileName
  - svn diff -rHEAD filename
- svn commit -m "message"

- svn update
  - 効用
    - リポジトリ内のバージョンを最新に
    - リポジトリから最新資材を取得
    - リポジトリで競合があった場合もマージ可能であれば行う
  - 確認: svn status -v (現在の各obj verを確認)
  - 配下を更新するため、subdirで実行すると一部が更新される。
    - ファイル名等を指定して一部を更新することも可能。(svn update bulid.xml src/ など)
- svn resolved fileName
- svn revert fileName
  - ローカルの変更を破棄する

- svn log fileName
  - svn log --verbose fileName
- svn info Repo
- svn add Target
- svn [copy|cp] sourceFile destFile
- svn [move|mv|rename|ren] oldName newName
  - svn move -m "message" svn://from/name svn://to/name
    - リポジトリで直接move
- svn propset propetyName propertyValue target
- svn propedit propertyName target
- svn proplist target
  - getting prop list
- svn propget propName target
  - getting prop value
## svnadmin
- svnadmin create {folder}
## 変更情報
- A: Add
- U: Update
- D: Delete
- G: Merge
- C: Conflict

- 1列目はファイル、2列目はファイル属性情報。
## 属性
- svn:ignore
  - 無視するファイルを設定、*.class、など。
- svn:eol-style
  - native, CRLF, LF, CR
- svn:mime-type
- svn-executable
## リビジョン識別子
- 番号
  - リポジトリ内のリビジョン番号
- 日時
  - 指定した日時以前でもっとも近いリビジョンが取得される。
- HEAD
  - リポジトリに格納されている最新のリビジョン
- BASE
  - 作業コピーのベースになっているリビジョン
- COMITTED
  - BASEと同じかそれ以前のリビジョンで、ファイル・ディレクトリが最後に変更されたリビジョン
- PREV
  - COMITTEDの直前のリビジョン
