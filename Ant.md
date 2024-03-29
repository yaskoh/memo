# Ant
## Command
- ant [options] [target [target2 [target3] ...]]

### Options
- -help, -h
- -projecthelp, -p
- -version
- -diagnostics
- -quiet, -q
- -silent, -S
- -verbose, -v
- -debug, -d
- -emacs, -e
- -lib <path>
- -logfile <file>
  -l      <file>
- -logger <classname>
- -listener <classname>
- -noinput
- -buildfile <file>
  -file      <file>
  -f         <file>
- -D<property>=<value>
  プロパティファイルの指定よりも優先される。
- -keep-going, -k
- -propertyfile <name>
- -inputhandler <class>
- -find <file>
  -s    <file>
- -nice number
- -nouserlib
- -noclasspath
- -autoproxy
- -main <class>
## Environment Variables
### ANT_HOME
### JAVACMD
### ANT_OPTS
### ANT_ARGS
## Buildfile
### About
- Each buildfile contain one project and at leasst one (default) target.
  Target contain task elements.
  Each task element can have an id attribute and can latare be referred to by the value supplied to this.
### Project
#### attributes
- name : the name of the project
- default : the default target to use when no target is supplied.
- basedir : the base directory from which all path calculations are done.
- description : option.
### Target
- A target can depend on other targets.
#### Attributes
- name
  the name of the target. Required.
- depends
  a comma-separated listo f names of targets on which this target depends.
- if
  the name of the property that msut be set in order for this target to execute, or something evaluating to true.
  当該ターゲットのみに影響を与えるため、依存関係にあるプロジェクトは結果に関係なく実行される。
- unless
  the name of the property that msut not be set in order for this target to execute, or something evaluating to false.
  当該ターゲットのみに影響を与えるため、依存関係にあるプロジェクトは結果に関係なく実行される。
- description
  a short description of this target's function
- extensionOf
  adds the current target to the depends list of the named extension-point. since Ant 1.8.0.
- onMissingExtensionPoint
  What to do if target tries to extend a missing extension-point ("fail", "warn", "ignore"). since Ant 1.8.2.
### Tasks
- A task is a piece of code that can be executed.
  
- structune
  <name attribute1="value1" attribute2="value2".../>

#### Common attributes
- id
- taskname
- description
#### List
- [[http://ant.apache.org/manual/index.html][Overview of Apache Ant Tasks]]
##### Archive
##### Audit/Coverage
##### Compile
###### Javac
- Compiles the specified source file(s) within the running (Apt) VM, or in another VM if the fork attribute is specified.
##### Development
##### Documentation
##### EJB
##### Execution
###### Ant
###### Apply/ExecOn
###### Exec
- Executes a system command.
####### Attributes
- command :
  the command to execute with all command line argumetns
- executable
- dir
- os
- osfamily
###### Java
- Executes a Java class within the running (Ant) VM, or in another VM if the fork attribute is specified.
###### Sleep
###### Waitfor
##### File
###### Attrib
###### Chmod
###### Chown
###### Concat
###### Copy
- Copies a files or Fileset to a new file or directory.
####### Attributes
- file
- preservelastmodified
- tofile
- todir
- overwrite
- force
- filtering
###### Delete
###### Mkdir
###### Move
###### Touch
##### Java2 Extensions
##### Logging
##### Mail
##### Miscellaneous
###### Echo
- Echoes text to System.out or to a file.
####### Attributes
- message :
  the message to echo.
- file :
  the file to write the message to.
- output :
  the Resource to write the message to. Since Ant 1.8.
- append
- level
- encoding
- force
##### Pre-process
##### Property
##### Remote
##### SCM
##### Testing
### Properties
- an important way to customize a build process or to just provide shortcuts for strings that are used repeatedly inside a bulid file.
#### Built-in Properties
- basedir
- ant.file
- ant.version :
  the version of Ant
- ant.project.name
- ant.project.default-target
- ant.project.invoked-targets
- ant.java.version
- ant.home
  this is set by the launcher script and maybe not set inside IDEs.
- ant.library.dir
  this is only set if Ant is started via the Launcher class
- java.lang.System.getProperty()で取得できるpropertyは全て利用可能。
#### Propety Helpers
### Type
#### List
##### Class Fileset
##### Description Type
##### Directory-based Tasks
##### DirSet
##### Extension Package
##### Set of Extension Packages
##### FileList
##### FileSet
##### File Mappers
##### FilterChains and FilterReaders
##### FilterSet
##### MultiRootFileSet
##### PatternSet
##### Path-like Structures
##### Permissions
##### PropertySet
##### I/O Redirectors
##### Regexp
##### Resources
##### Resource Collections
##### Selectors
##### TarFileSet
##### XMLCatalog
##### ZipFileSet
## Ant API
## Memo
### Optionalの導入
- Linuxでantを実行した際、Native2Asciiがない、と怒られたが、以下をインストールすることで解決した。
  Message : Cause: the class org.apache.tools.ant.taskdefs.optional.Native2Ascii was not found.
  Install : sudo yum install ant-nodeps
## Link
- [[http://ant.apache.org/][THE APACHE ANT PROJECT]]
- [[http://ant.apache.org/manual/index.html][Apache Ant 1.9.7 Manual]]

- [[http://www.techscore.com/tech/Java/ApacheJakarta/Ant/index/][Ant - TECHSCORE]]
