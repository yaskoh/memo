# C++
## Standard
### Language
#### General principles
#### Lexical conventions
#### Basic concepts
#### Standard conversions
#### Expressions
#### Statements
#### Declarations
#### Declarators
#### Classes
#### Derived classes
#### Member access control
#### Special member functions
#### Overloading
#### Templates
#### Exception handling
#### Preprocessing directives
### Library
#### Introduction
#### Lunguage support library
#### Diagnostics libarry
#### General utilities library
#### Strings library
#### Localization library
#### Containers library
#### Iterators library
#### Algorithms library
#### Numerics library
#### Input/output library
##### General
##### Requirements
##### Forward declarations <iosfwd>
##### Standard iostream objects <iostream>
###### Narrow strem objects
####### istream cin
####### ostream cout
####### ostream cerr
####### ostream clog
###### Wide stream objects
####### wistream wcin
####### wostream wcout
####### wosteram wcerr
####### wostearm wclog
##### Iostreams base classes <ios>
##### Stream buffers <streambuf>
##### Formatting and manipulators <istream>/<ostream>/<iomanip>
###### istream
##### String streams <sstream>
##### File streams <fstream>
##### File systems <filesystem>
##### C library files <cstdio>/<cinttypes>
#### Regular expressions library
#### Atomic operations library
#### Thread support library
## Reference
### Input/Output
#### <iostream>
##### Objects
###### Narrow characters
####### cin
####### cout
####### cerr
####### clog
###### Wide characters
####### wcin
####### wcout
####### wcerr
####### wclog
## Library
- http://www.cplusplus.com/reference/
- https://ja.wikipedia.org/wiki/%E6%A8%99%E6%BA%96C%2B%2B%E3%83%A9%E3%82%A4%E3%83%96%E3%83%A9%E3%83%AA
- http://cs.stmarys.ca/~porter/csc/ref/cpp_standlib.html
### C Library
- C++の標準Cライブラリのヘッダは、Cと異なり、先頭にcを加え、末尾の.hを取り除く。
  time.h -> ctime、など。
#### <cassert>
#### <cctype>
#### <cmath>
##### Functions
###### Other functions
####### abs
- Compute absolute value
##### Macnos/Functions
##### Macro constants
### Containers
#### <array>
#### <bitset>
#### <deque>
#### <forward_list>
#### <list>
#### <map>
#### <queue>
#### <set>
#### <stack>
#### <unordered_map>
#### <unordered_set>
#### <vector>
### Input/Output
#### <fstream>
#### <iomanip>
#### <ios>
##### Types
###### Class templates
###### Classes
####### ios
####### ios_base
- Base class for streams
####### wios
###### Other types
##### Format flag manipulators
##### Other functions
#### <iosfwd>
#### <ostream>
#### <istream>
#### <ostream>
#### <sstream>
#### <streambuf>
### Atomics and threading
### Miscellaneous
#### <algorithm>
##### Functions
###### Non-modifying sequence operations
###### Modifying sequence operations
###### Partitions
###### Sorting
####### sort
- Sorts the elements in the range [filst,last) into ascending order.
###### Binary search
## Compiler
### g++
- GNUのコンパイラ。
### Cling
- CERNで開発されているC++ Interpreter
- https://root.cern.ch/cling
## Tools
### Unit Testing Framework
#### googletest / Google C++ Testing Framework
- https://github.com/google/googletest
##### Documents
###### 入門ガイド
- http://opencv.jp/googletestdocs/primer.html
####### はじめに
####### 新しいテストプロジェクトを開始する
####### 基本コンセプト
- アサーションを書く
  - 結果は、成功、致命的でない失敗、致命的な失敗、の3種類。
- 1つのテストケースには、1つまたは複数のテストが含まれる。
  対象コードの構造を反映するように、テストをテストケースとしてグループ化すべし。
  共通のオブジェクトやサブルーチンを共有する必要がある場合、テストフィクスチャクラスに書くことが可能。
####### アサーション
- ASSERT_* : 致命的な失敗、実行中の関数を中断する
- EXPECT_* : 致命的でない失敗、中断しない。

- EXPECTが好まれるが、失敗したら後続をやっても仕方ない場合にはASSERTを使う。
####### 基本的なアサーション
- 
  |-------------------------+-------------------------+------------------|
  | ASSERT_TRUE(condition)  | EXPECT_TRUE(condition)  | conditionがtrue  |
  | ASSERT_FALSE(condition) | EXPECT_FALSE(condition) | conditionがfalse |
  |-------------------------+-------------------------+------------------|
  
####### 2つの値の比較
- 
  |-----------------------------+-----------------------------+--------------------|
  | ASSERT_EX(expected, actual) | EXPECT_EX(expected, actual) | expected == actual |
  | ASSERT_NE(val1, val2)       | NEPECT_NE(val1, val2)       | val1 != val2       |
  | ASSERT_LT(val1, val2)       | LTPECT_LT(val1, val2)       | val1 < val2        |
  | ASSERT_LE(val1, val2)       | LEPECT_LE(val1, val2)       | val1 <= val2       |
  | ASSERT_GT(val1, val2)       | GTPECT_GT(val1, val2)       | val1 > val2        |
  | ASSERT_GE(val1, val2)       | GEPECT_GE(val1, val2)       | val1 >= val2       |
  |-----------------------------+-----------------------------+--------------------|

####### 文字列の比較
- 
  |--------------------------------------------+--------------------------------------------+--------------------------------|
  | ASSERT_STREQ(expected_str, actual_str)     | EXPECT_STREQ(expected_str, actual_str)     | 内容が等しい                   |
  | ASSERT_STRNE(str1, str2)                   | EXPECT_STRNE(str1, str2)                   | 内容が等しくない               |
  | ASSERT_STRCASEEQ(expected_str, actual_str) | EXPECT_STRCASEEQ(expected_str, actual_str) | CASEを無視して内容が等しい     |
  | ASSERT_STRCASENE(str1, str2)               | EXPECT_STRCASENE(str1, str2)               | CASEを無視した内容が等しくない |
  |--------------------------------------------+--------------------------------------------+--------------------------------|

####### 簡単なテスト
- 作成方法
  - TEST()マクロを利用してテスト関数を定義
  - 

###### 上級ガイド
- http://opencv.jp/googletestdocs/advancedguide.html#advancedguide
##### Library
###### libtest.a
###### libtest_main.a
##### Memo
###### 設定例
- https://qiita.com/medaka5/items/171e10d5fa2d5e04f860

- gtest_mainを使う場合
  - g++ test1.cpp -I$GTEST_INCLUDEDIR -L$GTEST_LIBDIR -lgtest -lgtest_main
- mainを自分で書く場合
- g++ test1.cpp -I$GTEST_INCLUDEDIR -L$GTEST_LIBDIR -lgtest

#### Boost.Test
- https://www.boost.org/doc/libs/1_67_0/libs/test/doc/html/index.html
#### CppUnit
#### CppUnitLite
### Build
#### CMake
##### Documentation
###### CMake 3.11
- https://cmake.org/cmake/help/v3.11/
####### Command-Line Tools
######## cmake
######### Synopsis
- cmake [(-D <var>=<value>)...] -P <cmake-script-file>
######### Options
########## -C <initial-cache>
########## -D <var>:<type>=<value>,-D <var>=<value>
######## ctest
######## cpack
####### Interactive Dialogs
######## cmake-gui
######## ccmake
####### Reference Manuals
######## cmake-buildsystem
######### Introduction
######### Binary Tragets
########## Binary Executables
########## Binary Library Types
######### Build Specification and Usage Requirement
######### Pseudo Targets
######## cmake-commands
######### Scripting Commands
########## break
########## cmake_minimum_required
- Set the minimum required version of cmake for a project and update Policy Settings to match the version given
########## continue
########## elseif
########## else
########## endif
########## file
########## message
- Display a messega to the user.
########## if
########## set
- Set a normal, cache, or environment variable to given value.
######### Project Commands
########## add_definitions
- マクロの指定
########## add_executable
- Add an executable to the project using the specified source files.
########## add_library
- ライブラリを作成する
########## add_test
- Add a test to the project to be run by ctest.
- テストを追加する
########## enable_testing
- ctestを有効化する
########## include_directories
- インクルードパスの指定
########## link_directories
########## project
- Set a name, version, and enable languages for the entire project.
########## target_link_libraries
- リンクするライブラリの追加
######### CTest Commands
######### Deprecated Commands
######## cmake-compile-features
######## cmake-develoker
######## cmake-language
######### Organization
######### Syntax
######### Control Structures
######### Variables
######### Lists
######## cmake-server
######## cmake-modules
######## cmake-packages
######## cmake-variables
######### Variables that Provide Information
######### Variables that Change Behavior
########## CMAKE_BUILD_TYPE
- Specifies the build type on single--configuration generators.
######### Variables that Describe the System
######### Variables that Control the Build
######### Variables for Languages
######### Variables for CTest
######### Variables for CPack
##### Download
- https://cmake.org/download/
##### Link
- https://cmake.org/

- [[http://www.wagavulin.jp/entry/2011/11/27/222636][CMakeを使ってみた（1）経緯と簡単なアプリケーション - wagavulin's blog]]
- [[http://www.wakayama-u.ac.jp/~chen/cmake/cmake.html][CMakeの勧め]]

- [[https://qiita.com/mrk_21/items/25ee7f00cebb9934b472][CMake:CTest - Qiita]]
## Memo
### Standard C++
- C++17 : 2017年予定
- C++14 : ISO/IEC 14882:2014 (2014/12/15)
- C++11 : ISO/IEC 14882:2011 (2011/9/1)
- C++TR1 : ISO/IEC 14882:2007 (2007/11/15)
- C++03 : ISO/IEC 14882:2003 (2003/10/16)
- C++98 : ISO/IEC 14882:1998 (1998/9/1)

### :: / Scope resolution スコープ解決演算子
- ::は名前空間の区切りを表す。
  ex) std::cout
  どの名前空間にも属さない変数はグローバル名前空間(globla namespace)という特別な名前空間に属しており、
  ::fooという書き方となる。
## Link
- [[https://isocpp.org/std/the-standard][The Standard - THE C++ PROGRAMMING LANGUAGE]]

- [[http://ezoeryou.github.io/cpp-book/C++11-Syntax-and-Feature.xhtml#][C++11の文法と機能(C++11:Syntax and Feature)]]

- [[https://github.com/cplusplus/draft][C++ 20 : C++ Stardard Draft Sources]]
- [[http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/n4659.pdf][2017: March 2017 working draft, C4659.pdf]]
- [[http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4296.pdf][(Afetr 2014)N4296 Working Draft, Standard for Programming Language C++ / 2014-11/19]]
- [[http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3337.pdf][(After 2011)N3337 Working Draft, Standard for Programming Laguage C++ / 2012-01-16]]

- [[http://www.cplusplus.com/][cplusplus.com]]

- [[http://isoparametric.hatenablog.com/entry/20080926/1222386910][Effective なんとかを読めば良いというものではない - 神様なんて信じない僕らのために]]
