# GNU linker
## About
- GNU linker ld (GNU Binutils)
## Manual
- https://sourceware.org/binutils/docs/ld/index.html
### 1 Overview
### 2 Invocation
#### 2.1 Command Line Options
#### 2.2 Environment Variables
### 3 Linker Scripts
#### 3.1 Basic Linker Scriptn Concepts
#### 3.2 Linker Script Format
#### 3.3 Simple Linker Script Example
#### 3.4 Simple Linker Script Commands
##### 3.4.1 Setting the Entry Point
##### 3.4.2 Commands Dealing with Files
###### INCLUDE filename
###### INPUT(file, file,...) / INPUT(file file ...)
###### GROUP(file, file,...) / GROUP(file file ...)
###### AS_NEEDED(file, file,...) / AS_NEEDED(file file ...)
###### OUTPUT(filename)
###### SEARCH_DIR(path)
###### STARTUP(filename)
##### 3.4.3 Commands Dealing with Object File Formats
###### OUTPUT_FORMAT(bfdname) / OUTPUT_FORMAT(default, big, little)
###### TARGET(bfdname)
##### 3.4.4 Assign alias names to memory regions
##### 3.4.5 Other Linker Scripts Commands
#### 3.5 Assigning Value to Symbols
#### 3.6 SECTIONS Command
#### 3.7 MEMORY Command
#### 3.8 PHDRS Command
#### 3.9 VERSION Command
#### 3.10 Expressions in Linker Scriptns
#### 3.11 Implicit Linker Scripts
### 4 Machine Dependent Features
### 5 BFD
#### 5.1 How It Works: An Outline of BFD
##### 5.1.1 Information Loss
##### 5.1.2 The BFD canonical object-file format
### 6 Reporting Bugs
## Memo
### 
- http://www.ertl.jp/~takayuki/readings/c/no09.html
- https://www.computex.co.jp/article/use_gcc_1.htm
- 全体
  - MEMORY
  - SECTIONS

- MEMMORYコマンド
  - システム全体の物理的なメモリ構成を決める。
    名前は任意につけることができ、SECTIONSコマンドでオブジェクトの出力先を指定するために使用する。

  - ORIGIN (O): 物理メモリのアドレスを指定
  - LENGTH (L): サイズ指定。M,Kなどの表現が可能。

## link
- https://sourceware.org/binutils/docs/ld/index.html#Top
