# .NET Framework
## Implementation
### .NET Framework
#### Version
##### .NET Framework 4.7
##### .NET Framework 4.6 and 4.5
##### .NET Framework 3.5
##### .NET Framework 3.0
##### .NET Framework SDK 2.0
##### .NET Framework 1.1
##### .NET Framework 1.0

### .NET Core
- 複数のOS向けに利用できる.NET実装。
  .NET FrameworkとSilverlightから分岐したもの。
### Alterentive Implementation 別実装
#### Mono
- Ecma標準に準じた.NET Framework互換の環境を実現するためのオープンソースソフトウェア群、またそのプロジェクト名。
##### Monoコンポーネント
###### 中核コンポーネント
###### Mono/Linux/GNOME開発スタック
###### マイクロソフト互換スタック
#### .NET Micro Framework
#### Portable.NET (part of DotGNU)
## Class Library
- [[https://msdn.microsoft.com/ja-jp/library/mt472912(v=vs.110).aspx]]
### Namespaces
#### System.Diagnostics
##### System.Diagnostics (Namespace)
##### System.Diagnostics.Eventing.Reader (Namespace)
- イベントログの読み取りと管理を行う
###### Classes
####### EventlLogSession (Class)
######## Constructers
######## Properties
######## Methods
######### ExportLog(String, PathType, String, String)
- イベントを外部のログファイルにエクスポートする
###### Enum
#### System.Net
##### System.Net (Namespace)
##### System.Net.Sockets (Namespace)
- implemantation of the Windows Socket interface for developers who need to tightly control access to the network.
###### Classes
####### TcpClient
- Provides client connectoins for TCP network services.
######## Constructors
######## Properties
######### Connected
- Gets a value indicating whether the underlying Socket for a TcpClient is connected to a remote host.
######## Methods
######### Close()
- Disposes this TcpClient instance and requests that the underlying TCP connection be closed.
######### Connect(IPAddress, Int32)
- Connects the client to a remote TCP host using the specified IP address and port number.
######### 
## Related tools
### SDK
#### Xamarin
## Glossary
### .NET Standard
- 基本APIのセット。このAPIを基本クラスライブラリ(BCL)と呼ぶ。
  どの.NET実装やOSで実行されても共有できる。
  https://msdn.microsoft.com/ja-jp/magazine/mt842506.aspx
## Memo
### 互換性(tmp)
- [[https://blogs.msdn.microsoft.com/jpvsblog/2015/04/06/net-framework-3/][.NET Frameworkの各バージョン同士の関係 - Developer]]
- 1.0 -> 1.1
- https://msdn.microsoft.com/ja-jp/library/cc825629.aspx
- https://msdn.microsoft.com/ja-jp/library/cc825633.aspx
- https://msdn.microsoft.com/ja-jp/library/cc825671.aspx
### 4.5以上でのsort algorithmの変更
- over 4.5
  - This method uses the introspective sort (introsort) algorithm as follows:
    - If the partition size is fewer than 16 elements, it uses an insertion sort algorithm.
    - If the number of partitions exceeds 2 * LogN, where N is the range of the input array, it uses a Heapsort algorithm.
    - Otherwise, it uses a Quicksort algorithm.
    [[https://msdn.microsoft.com/en-us/library/afwbytk2(v=vs.110).aspx][Array.Sort Method - Developer Network]]

- under 4.0
  - This method uses Array.Sort, which uses the QuickSort algorithm.
    This implementation performs an unstable sort; that is, if two elements are equal, their order might not be preserved.
    In contrast, a stable sort preserves the order of elements that are equal.

### DNX
- Net Core, ASP.NET Core1.0 RC1でDNXツールが導入、RC2でDNXから.NET Core CLIに移行。
  以前はKRE(K Rnutime Environment)、XRE(Cross-platform Runtime Environment)などと呼ばれていた。
- DNXは以下から構成
  - DNVM / DotNet Version Manager
  - DNX / DotNet Execution Environment
  - DNU
- CLIの導入により、単一のツールセットに含められた。
- https://docs.microsoft.com/ja-jp/dotnet/core/migration/from-dnx
### インストールされている.NET Frameworkバージョンを確認する
- https://docs.microsoft.com/ja-jp/dotnet/framework/migration-guide/how-to-determine-which-versions-are-installed
## Link
- [[https://msdn.microsoft.com/ja-jp/library/aa139615.aspx][.NET開発 - Developer Network]]
- [[https://msdn.microsoft.com/ja-jp/library/cc948946.aspx][.NET開発(1.0含む) - Developer Network]]
