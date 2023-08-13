# Java SE Commands
- [[http://docs.oracle.com/javase/8/docs/technotes/tools/unix/intro.html#sthref18][Java Platform, Standard Edition Tools Reference]]
## Create and Build Applications
### appletviewer
### extcheck
### jar
- 
  Combines multiple files into a sinple JAR file.
### java
- Starts a java application.
  クラスファイルからクラスを読み込んで実行する。

#### Options
##### -client
##### -server
##### -agentlib:libname[=options]
##### -agentlib:libname[=options]
##### -classpath classpath, -cp classpath
- -classpath classpath
- -cp classpath
##### -jar
##### -version
##### -verbose
##### -verbose:class
##### -verbose:gc
##### -verbose:jni
##### -?
#### 非標準オプション
##### -X
- 非標準オプションの確認
##### -Xint
##### -Xdebug
##### -Xms'n'
##### -Xmx'n'
#### -XX Options
- [[file:JavaVM.org][JavaVM.org]]
#### Link
- https://docs.oracle.com/javase/jp/6/technotes/tools/windows/java.html

### javac
- javac [options] [sourcefiles] [classes] [@argfiles]
  Reads Java class and interface definitions and compiles them into bytecode and class files.
  .javaファイルから.classファイルを作成する。

- -cp path / -classpath path
  ユーザーのクラスファイルおよび注釈プロセッサやソースファイルの検索場所を指定する。
  クラスパスは、Java実行環境がクラスおよび他のソースファイルを検索するパス。

- 
  https://docs.oracle.com/javase/jp/6/technotes/tools/windows/javac.html

### javadoc
- 
  Generates HTML pages of API documentation from Java source file.

### javah
### javap

## Security
### keytool
### jarsigner
### policytool
## Internationalization
### native2ascii
## Remote Method Invocation (RMI)
### rmic
### rmiregistry
### rmid
### serialver
## Java IDL and RMI-IIOP
### tnameserv
### idlj
### orbd
### servertool
## Deploy Applications and Applets
### pack200
### unpack200
## Java Web Start
### javaws
## Monitor Java Applications
### jconsole
- Starts a graphical console that lets you monitor and manage Java applications.
- https://docs.oracle.com/javase/8/docs/technotes/tools/unix/jconsole.html
#### Synopsis
- jconsole [options] [connection ...]
#### Options
##### -interval=n
##### -notile
##### -pluginpath plugins
##### -version
##### -help
##### -Jflag
### jvisualvm
- Visually monitors, troubleshoots, and profiles Java applications.
- https://docs.oracle.com/javase/8/docs/technotes/guides/visualvm/index.html
#### Synopsis
- jvisualvm [options]
#### Options
##### -Jjvm_option
## Monitor the Java Virtual Machine
### jps
- (Experimental) Lists the instrumented Java Virtual Machines (JVMs) on the target system.

### jstat
- (Experimental) 
### jstatd
- (Experimental) 
### jms
## Web Services
### schemagen
### wsgen
- Reads a web service endpoint implementation (SEI) class and generates all of the required artifacts for web service deployment, end invocation.
- The wsgen command generates JAX-WS portable artifacts used in JAX-WS web services.
#### Synopsis
- wsgen [ options ] SEI
#### Options
- -classpath path, -cp path
  The location of the input class files.
### wsimport
- Generates JAX-WS portable artifacts that can be packaged in a web application archive(WAR) file and provides an Ant task.
#### Synopsis
- wsimport [options] <WSDL_URI>
#### Options
### xjc
## Troubleshooting
### jcmd
### jinfo
### jhat
### jmap
### jsadebugd
### jstack
## Scripting
### jrunscript

