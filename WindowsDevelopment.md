# Windows API
## Versions
### Win16
- for 16-bit versions of Microsoft Windows.
### Win32
- the 32-bit application programming interface.
### Win32s
- a extension for the Windows 3.1x family that implemented a subset of the Win32 API for these systems.
### Win64
### WinCE
### WINE
- Wine Is Not an Emulator
  a Win32 API compatibility layer for Unix-like platforms.
## Functions
### Base Services
- 
  provides access to the basic resources. 
  file systems, devices, processe, threads, error handling, etc.

- kernel32.dll
  (16bit : kernel.exe, krnl286.exe, krnl386.exe)
### Advanced Services
- provides access to functions beyond the kernel, like the Windows registry, shutdown/restart, start/sto/creat a Windows service, manage user accouns.
- file
  - advapi32.dll
### Grahics Device Interface
- gdi32.dll (16bit : gdi.exe)
### User Interface
- user32.dll, comctl32.dll (16bit : user.exe)
### Common Dialog Box Library
- comdlg32.dll (16bit : commdlg.dll)
### Common Control Library
- comctl32.dll
### Windows Shell
- shell32.dll
### Network Services
- netapi32.dll
### etc
#### Web
#### Multimedia
#### Program interaction
#### Wrapper libraries

## Link
- [[http://language-and-engineering.hatenablog.jp/entry/20081108/1226172930][ウィンドウをきっかけに Windows の内部の仕組みを探る （前半）フレームワークからDLLまでのスケール - 主に言語とシステム開発に関して]]
# SDKs
## Microsoft Windows SDK
### About
- VistaからMicrosoft Platform SDKと.NET Framework SDKを統合し、Windows SDKとなった。
### Versions
#### v10
##### Windows Standalone SDK for Windows 10, Version 1607
##### Windows Standalone SDK for Windows 10, Version 1511
##### Windows Standalone SDK for Windows 10
#### v8
##### v8.1A
##### v8.1:Windows Software Development Kit (SDK) for Windows 8.1
##### v8.0A
##### v8.0:Microsoft Windows SDK for Windows 8 and .NET Framework 4.5
#### v7
##### v7.1A
##### v7.1
##### v7.0a
##### v7.0
#### v6
##### v6.1
##### v6.0:Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components
#### older
##### .Net Framework SDK
##### Platform SDK
##### Win32 SDK
##### Windows SDK
## Direct X SDK
- Windows SDK v8.0以降は、Direct X SDKはWindows SDKに統合された。
## Link
- [[https://msdn.microsoft.com/library/windows/desktop/hh920508.aspx][API Index - Windows Developer Center]]
- [[https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk][Windows 10 SDK - Windows Dev Center]]
## Memo
### Headerの場所
- 以下にIncludeが存在
  Program Files\Microsoft SDKs\Windows\vX.XN\Include
- Bin, Libも同階層に存在。
### Windows.h
- Win-specific header file,
  which contains declarations for all of the functions in the Windows API, all the common macros used by Windows programmers,
  and all the data types used by the various functions and subsystems.
  https://en.wikipedia.org/wiki/Windows.h
  
# Dev Center
## Windows apps
## Games
## Desktop
### Get started
### Design
### Develop
#### Desktop technologies
##### Desktop app UI
###### Accessibility
###### User Interaction
###### Windows and Messages
####### Windows
######## Reference
######### Window Functions
########## WinMain
- the conventional name for the user-provided entry point for a Windows-based application.
######### Window Macros
######### Window Messages
######### Window Notifications
######### Window Structures
######### Window Constants
####### Window Classes
####### Window Procedures
####### Messages and Message Queues
####### Timers
####### Window Properties
####### Configuration
####### Hooks
####### Multiple Document Interface
###### Desktop Window Manager
###### Dialog Boxes
##### Desktop enrironment
##### Application installation and servicing
##### Audio and video
##### Data access and storage
##### Devices
##### Diagnostics
##### Documents and printing
##### Graphics and gaming
##### Networking and Internet
##### Security and identity
##### System services
###### COM
####### Component Object Model (COM)
######## COM Fundamentals
######## OLE and Data Transfer
######## Controls and Property Pages
######## COM Language Translation
######## COM Glossary
- https://msdn.microsoft.com/en-us/library/windows/desktop/ms690233(v=vs.85).aspx
####### Automation
####### Microsoft Interface Definition Language (MIDL)
####### Structured Storage
###### COM+
###### Compression API
###### Distributed Transaction Coordinator(DTC)
###### Dynamic Link Libraries(DLLs)
####### Reference
######## DLL Functions
######### AddDllDirectory
######### DllMain
- An optional entry point into a dynamic-link library.
######### FreeLibrary
###### Help API
###### Kernel Transaction Manager(KTM)
###### MultiPoint Services
###### Operation Recorder
###### Power Management
###### Processes and Threads
###### Remote Desktop Services
###### Services
###### Synchronization
###### Windows Desktop Sharing
#### Server and system technologies
#### Graphics and game technologies
### Test and Deploy
### Compatibility
### API Reference
- [[https://msdn.microsoft.com/library/windows/desktop/hh920508.aspx][API Index]]
#### User Interface
##### Accessibility
##### Desktop Window Manager(DWM)
##### Globalization Services
##### High DPI
##### Multilingual User INterface(MUI)
##### ational Language Support(NLS)
##### User Interface elements
###### Buttons
##### Windows Animation Manager
##### Windows Ribbon Framework
#### Windows Environment(Shell)
##### Windows Property System
##### Windows Shell
##### Windows Search
##### Consoles
#### User Input and Messaging
##### User Interaction
##### Legacy User Interaction
##### Windows and Mesages
###### Messages and Message Queues
###### Windows
####### Window Functions
######## WinMain
- the conventional name for the user-provided entry point for a Windows-based application.
####### Window Macros
####### Window Messages
####### Window Notifications
####### Window Structures
####### Window Constants
###### Window Classes
###### Window Procedures
###### Timers
###### Window Properties
###### Hooks
#### Data acccess and storage
#### Diagnostics
#### Graphics and Multimedia
#### Devices
#### System Services
##### COM
##### COM+
##### Compression API
##### Distributed Transaction Coordinator(DTC)
##### Dynamic Link Libraries(DLLs)
###### Reference
####### DLL Functions
######## AddDllDirectory
######## DllMain
- An optional entry point into a dynamic-link library.
######## FreeLibrary
##### Help API
##### Kernel Transaction Manager(KTM)
##### MultiPoint Services
##### Operation Recorder
##### Power Management
##### Processes and Threads
##### Remote Desktop Services
##### Services
##### Synchronization
##### Windows Desktop Sharing
#### Security and Identity
#### Application Installation and Servicing
#### System Admin and Management
#### Networking and Internet
#### Deprecated or legacy APIs
## Windows IoT
## Microsoft Edge
## Holographic
# Visual C++
## C++ Language Reference
### Microsoft固有の修飾子
#### __based
#### __cdecl
#### __declspec
#### __fastcall
#### __restrict
#### __stdcall
- 概要
- Grammer
  - decl-specifier:
    __declspec ( extended-decl-modifier-seq )
  - extended-decl-modifier-seq:
    extended-decl-modifier(opt)
    extended-decl-modifier extended-decl-modifier-seq
  - extended-decl-modifier:
    align( #)
    allocate("segname")
    appdomain
    code_seg("segname")
    deprecated
    dllimport
    dllexport
    jitintrinsic
    naked
    noalias
    noinline
    noreturn
    nothrow
    vatable
    process
    property({get=get_func_name|,put=put_func_name})
    restrict
    safebuffers
    selectany
    thread
    uuid("ComObjectGUID")
#### __w64
#### __unaligned
#### __vectorcall
## C Language Reference
## C/C++ Preprocessor Reference
## C Runtime Library
- [[https://msdn.microsoft.com/ja-jp/library/59ey50w6.aspx][C ランタイム ライブラリ リファレンス - Microsoft Developer Network]]]
### Global variables, Basic types
### Global Constraints
#### _TRUNCATE
- #include <stdlib.h>
  文字列の切り捨て動作を指定する。
### Function References
#### strncpy_s
- 構文
  errno_t strncpy_s(
     char *strDest,
     size_t numberOfElements,
     const char *strSource,
     size_t count
  );
- 
  文字列の文字を他の文字列にコピーする。

## C++ Standard Library
## Memo
### Visual C++で純粋なC言語をコンパイル
- 
  1. 拡張子を.cにする。
  2. プロジェクトのプロパティで、コンパイル言語の選択→"Cコードとしてコンパイル(/TC)"を選択する。
     
- http://tinqwill.blog59.fc2.com/blog-entry-68.html
### Win32基本型
- [[http://www.wisdomsoft.jp/421.html][基本データ型と文字列 - WisdomSoft]]

### "mspdb110.dll is missing"
- vcvars32.batを実行した後に実行する。
  ("C:\Program Files (x86)\Microsoft Visual Studio 11.0\VC\bin"など)
## Link
- [[https://msdn.microsoft.com/ja-jp/library/hh875057.aspx][C++言語及び標準ライブラリ - Visual Studio 2015  Developer Network]]
# Memo
## Object Linking and Embedding, OLE
- COMの前身。マイクロソフトが開発した、オブジェクトをやり取りするための仕組み・規約。
### OLE 1.0
- 1990年、動的データ交換(Dynamic Data Exchange, DDE)の後継として公開された。
  1991年、OLE1がWindows 3.1と共に公開。
  仮想関数テーブル(vtable, VTBL)を用いてクライアント間の通信を行う。
### OLE 2.0
- 1992年、OLE2が公開される。
  生のVTBLでなくCOMを使って実装しなおされた。
## ActiveX
- マイクロソフトが開発するインターネットに関するソフトウェアコンポーネントやその技術を示す用語。
  元々はOLEのうちインターネットと関連のあるいくつかの技術を分離し、ActiveXとして名称変更。
## Component Object Model, COM
- マイクロソフトが提唱するソフトウェアの再利用を目的とした技術。
  アプリケーションソフトウェア間での通信や、OSとアプリケーションソフトウェアとのAPIに用いられる。
  1997年、コンポ―ネントを使用する技術名として名づける。
- OLE、OLEオートメーション、ActiveX、COM+、DCOMをカバーする包括的な用語としてよく使われる。
### COMコンポーネント
- COMを使用して開発されたソフトウェア部品。
  特定の開発言語に依存せず、様々な言語により開発可能。
### Link
- http://garicchi.com/?p=19259
## COM+
## Distributed Component Object Model, DCOM
- ネットワーク上に分散されたコンピュータ上のソフトウェアコンポーネント間通信（分散オブジェクト技術）のためのマイクロソフト独自の技術。
  当初Network OLEと呼ばれ、COMを拡張したもので、COM+サーバ基盤上での通信基盤となっていた。
  .NET Frameworkのトウジョウとともにすたれていった。
## .NET
- [[file:dotNetFramework.org][dotNetFramework.org]]
## Windows Runtime, WinRT
- Windows 8およびWindows RTにて、新たなアプリケーションの開発・実行基盤としてWinRTが導入された。
  COMを拡張したネイティブ技術だが、Windowsメタデータ(WinMD)および言語プロジェクション(language projection)と呼ばれる技術で、
  .NET言語やJavaScriptなどからも透過的に利用可能。
