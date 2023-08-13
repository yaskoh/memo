# CS

## memo

- Delegate
    日本語訳で「委譲」。
    メソッドのインターフェイスだけ決めておき、
    実行するメソッドを追加したり削除したりしてまとめることができる。
    
- Event

- Threading
    スレッド処理
    System.Threading.Thread（古い）
    System.Threading.Task, Parallel, etc(新しい)
    [[http://msdn.microsoft.com/ja-jp/library/system.threading.tasks(v=vs.110).aspx][Tasks名前空間]]


- リフレクション
    型情報など、メタデータを扱えるようにすること。
    Typeクラスなどを使って実装する。


## Sandcastle

- バッチによる作成
    バッチでまとめてヘルプファイルを作成したい場合、以下が可能。
    ただし、shfbprojはGUIで作るので、まとめてXMLを作成した。
    C:\Windows\Microsoft.NET\Framework\v4.0.30319\MSBuild.exe /p:Configuration=Release myProject.shfbproj
    [[http://stackoverflow.com/questions/7882746/build-sandcastle-documentation-when-building-visual-studio-project][Build Sandcastle Documentation When Building Visual Studio Project]]


