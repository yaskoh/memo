# UnitTest
## xUnit
### Java
#### JUnit
##### JUnit4
- 
  アノテーションに対応。

###### About
####### JUnitCore
- 以下の流れで実行する
  1. テストケースの収集
  2. テストの実行
  3. テスト結果の出力（レポート）

####### TestRunner
- 
  テスト実行に関するカスタマイズ要求を満たすもの。

######## JUnit4
- org.junit.runners.JUnit4クラス
  JUnitの標準的なテストを実行するテストランナー。
  明示的にテストランナーを指定しなかった場合、このテストランナーが使用される。

######## Suite
- org.junit.runners.Suiteクラス
  複数のテストクラスをまとめて実行する
  
  
######### Test Suites Class
- 
  複数のテストクラスを束ねるには、テストスイートクラスを作成する。
  慣例として「〜Tests」のように、クラス名を複数形とする。
  特に「AllTests」は、よく使われるテストスイートクラス名。
  
- ex
  @Runwith(Suite.class)
  @SuiteClasses({ FooTest.class, BarTest.class })
  public class AllTests {
  }
  
- 実行
  通常のクラスなので、通常のテストクラスを指定する場合と同様、コマンドラインから実行できる。
  $ java org.junit.runner.JUnitCore test.AllTests
  

######## Enclosed
- org.junit.experimental.runners.Enclosed
  構造化したテストクラスのテストを実行するテストランナー。
  ネストしたクラスを定義し、テストケースは各ネストしたクラスに定義数r。
  ネストしたテストクラスはいくつでも定義できる。

######## Theories
- org.junit.experimental.theories.Theories
  パラメータ化したテストをサポートする。
  テストケースとテストデータを分離し、同じテストメソッドを複数のパラメータで再利用して使うメソッド。
  org.junit.Testアノテーションの代わりにorg.junit.experimenttal.theories.Theoryアノテーションを使用する。
  パラメータは、org.junit.experimental.theories.DataPointsアノテーションの付与されたstaticフィールドなどで定義する。

######## Categories
- org.junit.experimental.categories.Categories
  特定カテゴリのテストクラスをまとめて実行する。
  テストクラスをカテゴリ化し、実行するテストケースをフィルタリングする。

###### License
- CPL(Common Public License)

###### Execution
####### CommandLine
- Compile
  (Mac)javac -cp .:junit-4.XX.jar Test.java
  (Win)javac -cp .;junit-4.XX.jar Test.java
- Execute
  (Mac)java -cp .:junit-4.XX.jar:hamcrest-core-1.3.jar org.junit.runner.JUnitCore Test
  (Win)java -cp .;junit-4.XX.jar;hamcrest-core-1.3.jar org.junit.runner.JUnitCore Test

####### TestClass
- 
  下記のようにエントリポイントを定義して、以下コマンドで実行する。
  $ java ch05.TestClassName

- Entry Point
  public static void main(String[] args) {
    org.junit.runner.JUnitCore.main(TestClassName.class.getName());
  }

###### Annotation
####### @Test
- org.junit.Test
  戻り値がvoidの引数を持たないpublicメソッドである必要がある。
  expectedとtimeoutの2つの属性を持つことができる

######## expected

######## timeout

####### @Ignore
- 
  テストの実行から除外する

####### @Before
- 
  テストの実行前に処理を行う
  慣習としてメソッド名をsetUp()とする。

####### @After
- 
  テストの実行後に処理を行う
  慣習としてメソッド名をtearDown()とする。

####### @BeforeClass
- 
  テストの実行前に一度だけ処理を行う

####### @AfterClass
- 
  テストの実行後に一度だけ処理を行う

####### @RunWith
- org.junit.runner.RunWith
  テストランナーとなるクラスを指定する。

####### @SuiteClasses
- org.junit.runners.Suite.SuiteClasses
  テストスイートに含めるテストクラスの指定

####### @Theory
- org.junit.experimental.theories.Theory
  パラメータ化テストを行う際に使用する。

####### @DataPoints
- org.junit.experimental.theories.DataPoints
  パラメータ化テストでテストメソッドに渡すパラメータなどに付与する。
  
####### @Category
- org.junit.experimental.categories.Category

####### @ExcludeCategory
- 
  実行から除外するカテゴリーを指定する

###### Assertion
####### About
- 
  staticインポートを利用し、自然言語に近い記述を実現する。
  
  Assert.assertThat(3 + 4, CoreMatchers.is(7));
  ↓
  assertThat(3 + 4, is(7));

####### Assert
######## assertThat
- 
  汎用的な値の比較検証

######## fail
- 
  無条件にテストを失敗させる。
  

######## その他
- 
  JUnit3との互換性のために残されているため、基本使わない。

####### Matcher API
######## About
- 
  Hamcrestという独立したAPIに含まれていたが、JUnit4.4で本家にマージされた。
  Hamcrest、はmatchersのアナグラム。

- 
  可読性の高い記述、柔軟な比較、詳細な情報の提供を可能とする。
  一貫した書式で柔軟な比較検証を行うインターフェースを提供する。

######## CoreMatchers
- org.hamcrest.CoreMatchers

######### is
- 
  もっとも自然な比較を行うmatcherを返す。
  型パラメータを持つメソッドのため、nul

- 
  assertThat(actual, is(expected));

######### nullValue
- 
  nullであることを検証するmatcherを返す。

######### not
- 
  他のMatcherの評価値を反転させるMatcherを返す。

- 
  assertThat(actual, is(not(0)));

######### notNullValue
- 
  nullでないことを比較検証するMatcherを返す。

######### sameInstance
- 
  実測値と期待値が同一のインスタンスであるかを比較するMatcherを返す。

######### instanceOf
- 
  実測値が期待するクラスのインスタンスと互換性のある型であるかを比較判定するMatcherを返す。

######## JUnitMatchers
- org.junit.matchers.JUnitMatchers

######### hasItem
- 
  リストや配列など反復可能なオブジェクト（実測値）に期待する値が含まれているかを判定するMatcherを返す。

######### hasItems
- 
  リストや配列など反復可能なオブジェクト（実測値）に期待する値が複数含まれているかを判定するMatcherを返す。
  可変数引数をとり、すべての値が実測値に含まれているかを検証する。

- 
  assertThat(actual, hasItems("Hello", "World"));

######## hamcrest-library
- 
  Junit4.10の時点では拡張ライブラリ。

######### empty
- org.hamcrest.collection.IsEmptyCollection

######### hasSize
- org.hamcrest.collection.IsCollectionWithSize
######### hasEmpty
- org.hamcrest.collection.IsMapContaining
######### hasKey
- org.hamcrest.collection.IsMapContaining
######### hasValue
- org.hamcrest.collection.IsMapContaining
######### comparseEqualTo
- org.hamcrest.number.OrderingComparison
######### greaterThan
- org.hamcrest.number.OrderingComparison
######### greaterThanOrEqualTo
- org.hamcrest.number.OrderingComparison
######### lessThan
- org.hamcrest.number.OrderingComparison
######### lessThanOrEqualTo
- org.hamcrest.number.OrderingComparison
######### closeTo
- org.hamcrest.number.IsCloseTo
######### isEmptyString
- org.hamcrest.text.IsEmptyString
######### isEmptyOrNullString
- org.hamcrest.text.IsEmptyString
######### equalToIgnoringCase
- org.hamcrest.text.IsEqualIgnoringCase
######### samePropertyValuesAs
- org.hamcrest.beans.SamePropertyValues

####### Custom
######## About
- 
  org.hamcrest.Matcherインターフェースを実装したクラスとして作成する。
  ただし直接インプリメントすることは推奨されておらず、org.hamcrest.BaseMatcherクラスのサブクラスとする。

######### making flow
- Classの作成
  BaseMatcherクラスのサブクラスとしてクラスを作成。
  matchesメソッドとdescribeToメソッドを実装する。
  matchesは値の比較検証を行う。describeToは比較が失敗した場合にフレームワークに通知する情報を作成する。

- ファクトリメソッドの作成
  staticなファクトリメソッドを作成する。

- コンストラクタを定義

- matchesメソッドを実装

- describeToメソッドを実装

- テスト失敗メッセージの確認

###### Pattern
####### Basic
######## 標準的な振る舞いを検証
######## 例外の送出を検証
######## コンストラクタを検証
###### API
####### org.hamcrest
####### org.hamcrest.core
####### org.junit
####### org.junit.experimental
####### org.junit.matchers
####### org.junit.rules
####### org.junit.runner
####### org.junit.runner.manipulation
####### org.junit.runner.notification
####### org.junit.runners
####### org.junit.runners.model
####### org.junit.runners.parameterized
####### org.junit.validator
###### Link
- http://junit.org/junit4/
- [[http://junit.org/junit4/javadoc/latest/index.html][JUnit 4.12 API]]
- [[https://github.com/junit-team/junit4/wiki][Wiki junit4 - github]]
## TestNG
## Memo
### 4 Phase Test
- 
  - set up 事前準備
  - exercise 実行
  - verify 検証
  - tear down 後処理
## Link
- [[http://xunitpatterns.com/][xUnit Test Patters]]
