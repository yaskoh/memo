# Maven
## About
- 
  Apache Maven is a software projcet management and comprehension tool.

## Command
### mvn
- usage:
  mvn [options] [<goal(s)>] [<phase(s)>]
#### Options
- -h, --help
  Display help information
- -v, --version
  Display version information
#### Lifecycle
- [[https://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html#Lifecycle_Reference][Lifecycle Reference - Apache Maven Project]]
##### default
###### validate
###### initialize
###### generate-sources
###### process-sources
###### generate-resources
###### process-resources
###### compile
###### process-classes
###### generate-test-sources
###### process-test-soures
###### generate-test-resources
###### process-test-resoures
###### test-compile
###### process-test-classes
###### test
###### prepare-package
###### package
###### pre-integration-test
###### integration-test
###### post-integration-test
###### verify
###### install
###### deploy
##### clean
###### pre-clean
###### clean
###### post-clean
##### site
###### pre-site
###### site
###### post-site
###### site-deploy
##### Built-in Bindings
- [[https://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html#Built-in_Lifecycle_Bindings][Built-in Lifecycle Bindings - Apache Maven Project]]
## Plugins
### Core plugins
#### clean
- Clean up after the build.
#### compiler
#### install
#### site
### Packaging types/tools
### Reporting plugins
### Tools
#### archetype
##### Goals
###### archetype:generate
- creates a Maven project from an archetype: 
  asks the user to choose an archetype from the archetype catalog, and retrieves it from the remote repository.
####### Parameters
######## Required
######### interactiveMode
- Defalut : $(settings.intreractiveMode)
- User propety : interactiveMode
######## Optional
###### archetype:create-from-project
###### archetype:crawl
###### archetype:jar
###### archetype:integration-test
###### archetype:update-local-catalog
###### (deprecated)archetype:create
## POM
- POM stands for "Project Object Model".
  https://maven.apache.org/pom.html
### Fields
#### Basics
##### modelVersion
##### groupId
##### artifactId
##### version
##### packaging
##### name
##### classifier
### Dependencies
### sourceDirectory
### testSourceDirectory
### outputDirectoyr
### testOutputDirectory
### resources
### testResources
## Environmental Variables
### MAVEN_OPTS
## Structure
### src/main/java
- directory containing the project source code
### src/test/java
- directory containing the test source
### pom.xml
- Project Object Model, or POM
## Files
### conf/settings.xml
### maven.confiure
### extensions.xml
## Glossary
### POM
- Project Object Model
  
### Goal
- Mavenのプラグインが持つ機能のこと

### Phase
- プロジェクトのビルドサイクルに含まれる個々のステップのこと。
  実際には対応するプラグインで行われており、プラグインのゴールのエイリアスとも考えられるが、
  特定のフェイズに関連付けてプラグインを実行させることができるため、
  正確には"mvn compile"と"mvn compiler:compile"は同じ動作をするとは限らない。

## Memo
### 開始方法
- mvn archetype:generate
  プロジェクトを作成。各種求められる値を入力。"pom.xml"が作成される。
## Link
- [[https://maven.apache.org/index.html][Apache Maven Project]]

- [[https://maven.apache.org/users/index.html][Mave Users Centre - Apache Maven Project]]  
- [[http://maven.apache.org/guides/][Documentation - Apache Maven Project]]

- [[http://sambatriste.github.io/maven3-tutorial/][Maven3 チュートリアル]]
- [[https://kengotoda.gitbooks.io/what-is-maven/content/index.html][Maven3のはじめかた]]
