# Java SE API
## Java SE 8
### java
#### java.lang
- Provides classes that are fundamental to the design of the Java programming language.
##### Interface
##### Class
###### Boolean
###### Byte
###### Character
###### Character.Subset
###### Character.UnicodeBlock
###### Class<T>
- public final class Class<T> extends Object implements Serializable, GenericDeclaration, Type, AnnotatedElement
  Instances of the class "Class" represent classes and interfaces in a running Java application.
  
####### Methods
######## forName(String className)
- 
  Returns the Class object associated with the class or interface with the given string name.
######## getClasses()
- 
  Returns an array containing Class objects representing all the public classes and interfaces that are members of the class represented by this Class object.
######## getField(String name)
######## getFields()
######## getInterfaces()
######## getMethod(String name, Class<?>... parameter Types)
######## getMethods()
######## getModifiers()
######## getName()
- 
  Returns the name of the entity represented by this Class object, as a String.
######## getPackage()
######## getSuperclass()
######## getTypeName()
######## isAnnotation()
######## newInstance()
- 
  Creates a new instance of the class represented by this Class object.
###### ClassLoader
###### ClassValue<T>
###### Compiler
- Compiler class is provided to support Java-tonative-code compilers and related services.
###### Double
###### Enum<E extends Enum<E>>
###### Float
###### InheritableThreadLocal<T>
###### Integer
###### Long
###### Math
###### Number
###### Object
###### Package
###### Process
###### ProcessBuilder
###### ProcessBuilder.Redirect
###### Runtime
###### RuntimePermission
###### SecurityManager
###### Short
###### StackTraceElement
####### Constructors
####### Methods
###### StrictMath
###### String
####### Methods
######## indexOf(int ch)
- public int indexOf(int ch)
- 
  Returns the index within this string of the first occurrence of the specified character.
######## indexOf(int ch, int fromIndex)
######## indexOf(String str)
######## indexOf(String str, int fromIndex)
###### StringBuffer
###### StringBuilder
###### System
- The System class contains several useful class fields and methods.
####### Field
######## err
- static PrintStream err
  The "standard" error output stream.
######## in
- static InputStream in
  The "standard" input stream.
######## out
- static PrintStream out
  The "standard" output stream.
####### Method
######## console
- static Console console()
######## getProperties()
- static Properties
######### Keys
- 
  |-------------------------------+------------------------------------|
  | Key                           | Description                        |
  |-------------------------------+------------------------------------|
  | java.version                  | Java Runtime Environmental version |
  | java.vendor                   |                                    |
  | java.vendor.url               |                                    |
  | java.home                     |                                    |
  | java.vm.specification.version |                                    |
  | java.vm.specification.vendor  |                                    |
  | java.vm.specification.name    |                                    |
  | java.vm.version               |                                    |
  | java.vm.vendor                |                                    |
  | java.vm.name                  |                                    |
  | java.specification.version    |                                    |
  | java.specification.vendor     |                                    |
  | java.specification.name       |                                    |
  | java.class.version            |                                    |
  | java.class.path               |                                    |
  | java.library.path             |                                    |
  | java.io.tmpdir                |                                    |
  | java.compiler                 |                                    |
  | java.ext.dirs                 |                                    |
  | os.name                       | Operating system name              |
  | os.arch                       |                                    |
  | os.version                    |                                    |
  | file.separator                |                                    |
  | path.separator                |                                    |
  | line.separator                |                                    |
  | user.name                     | User's account name                |
  | user.home                     | User's home directory              |
  | user.dir                      | User's current working directory   |
  |-------------------------------+------------------------------------|
  
######## getProperty(String key)
- static String
- Gets the system property indicated by the specified key.
######## getProperty(String key, String def)
- static String
- Gets the system property indicated by the specified key.
###### Therad
###### ThreadGroup
###### ThreadLocal<T>
###### Throwable
- public class Throwable extends Object implements Serializable
- The Throwable class is the superclass of all errors and exceptions in the Java language.
####### Constructors
####### Methods
######## getStackTrace()
- public StackTraceElement[] getStackTrace()
- 
  Provides programmatic access to the stack trace information printed by printStackTrace().
  Returns an array of stack trace elements, each representing one stack frame.
######## printStackTrace()
- public void printStackTrace()
- 
  Prints this throwable and its backtrace to the standard error stream.
######## printStackTrace(PrintStream s)
######## printStackTrace(PrintWriter s)
###### Void
##### Enum
##### Exception
###### Exception
- The class Exception and its subclasses are a form of Throwable that indicates conditions that a reasonable application want to catch.
##### Error
###### Error
- An Error is a subclass of Throwable that indicates serious problems that a reasonable application should not try to catch.
##### Annotation
###### Deprecated
###### FunctionalInterface
###### Override
###### SafeVarargs
###### SuppressWarnings
- Indicates that the named compiler warnings should be suppressed in the annotated element.
#### java.io
##### Interface
###### Closable
###### DataInput
###### DataOutput
###### Serializable
####### About
- 
####### Def
- public interface Serializable
####### 
##### Class
###### BufferedInputStream
###### BufferedOutputStream
###### BufferedReader
###### BufferedWriter
###### ByteArrayInputStream
###### ByteArrayOutputStream
###### Console
###### File
####### Fields
####### Constructor
####### Methods
######## toURI()
- Constructs a file: URI that represents this abstract pathname.
######## toURL()
- Deprecated
  the method does not automatically escape characters that are illegal in URLs.
  it is recommended converting URI first(using toURI for example), then use URI.toURL.
  (toURI.toURL)
###### FileDescripter
###### FileInputStream
- public class FileInputStream extends InputStream
- FileInputStreamは、ファイルシステム内のァイルから入力バイトを取得する。
  どのファイルが有効であるかはホスト環境に依存する。
  イメージデータなどのrawバイトのストリームを読み込む時に使用する。
####### Constracotrs
######## FileInputStream(File file)
- ファイルシステム内のfileで指定される実際のファイルへの接続を開くことにより、FileInputStreamを作成する。
######## FileInputStream(FileDescriptor fdObj)
- 実際のファイルへの既存の接続を表すファイル記述子fdObjを使用してFileImputStreamを作成する
######## FileInputStream(String name)
- パス名nameで指定される実際のファイルへの接続を開くことにより、FileInputStreamを作成する。
####### Methods
######## available()
######## close()
######## finalize()
######## read()
- public int read() throws IOException
- Reads a byte of data from this input stream. This method blocks if no input is yet available.
- Returns
  the next byte of data, or -1 if end of the file is reached.
###### FileOutputStream
####### Constractors
######## FileOutputStream(File file)
######## FileOutputStream(File file, boolean append)
######## FileOutputStream(FileDescriptor fdObj)
######## FileOUtputStream(String name)
- Creats a file output stream to write to the file with the specified name.
######## FileOUtputStream(String name, boolean append)
####### Methods
###### FileReader
###### FileWriter
###### InputStream
- public abstract class InputStream extends Object implements Closeable
- This abstract class is the superclass of all classes representing an input stream of bytes.
####### Constructors
######## InputStream()
####### Methods
######## write(byte[] b)
- Writes b.length bytes from the specified byte array to this output stream.
######## write(byte[] b, int off, int len)
######## write(int b)
###### OutputStream
- public abstract class OutputStream extends Object implements Closeable, Flushable
####### Constructors
######## OutputStream()
####### Methdos
######## read()
- abstract int read()
######## read(byte[] b)
- reads some number of bytes from the input stream and stores them into the buffer array b.
######## read(byte[] b, int off, int len)
###### PrintStream
####### Def
- java.lang.Object > java.io.OutputStream > java.io.FilterOutputStream > java.io.PrintStream
- Implemented Interfaces:
  Closeable, Flushable, Appendable, AutoCloseable
- 
####### Constructors
######## PrintStream(File file)
######## PrintStream(File file, String csn)
######## PrintStream(OutputStream out)
######## PrintStream(OutputStream out, boolean autoFlush)
######## PrintStream(OutputStream out, boolean autoFlush, String encoding)
######## PrintStream(String fileName)
- Creates a new print stream, without automatic line flushing, with the specified line name.
######## PrintStream(String fileName, String csn)
- Creates a new print stream, without automatic line flushing, with the specified line name and charset.
####### Methods
######## println(char x)
######## println(char[] x)
######## println(String x)
- Prints a String and then terminate the line.
##### Exception
###### IOException
##### Error
###### IOError
#### java.lang.annotation
##### Interface
##### Enum
##### Exception
##### Error
##### Annotation
#### java.lang.invoke
##### Interface
##### Class
##### Exception
#### java.lang.ref
##### Class
#### java.lang.reflect
- Provides classes and interfaces for obtaining reflective information about classes and objects.
  Reflection allows programmatic access to information about the fields, methods and constructors of loaded classes,
  and use of reflected fields, methods, and constructors to operate on their underlying counterparts, within security restrictions.
##### Interface
##### Classes
###### AccessibleObject
- pulic class AccessibleObject extends Object implements AnntatedElement
  This class is the base class for Field, Method and Constructor objcets.
  It provides the ability to flag a reflected object as suppressing defult Java language access control checks when it is used.
####### Constructors
######## AccessibleObject()
####### Methods
###### Array
###### Constructor<T>
###### Executable
###### Field
- public final class Field extends AccessibleObject implements Member
  providing information about, and dynamic access to, a single field of a class or an interface.
  The reflected field may be a class (static) field or an instance field.
####### Methods
######## set(Object obj, Object value)
- 
  Sets the field represented by this Field object on the specified object argument to the specified new value.

###### Method
###### Modifier
###### Parameter
###### Proxy
###### ReflectPermission
##### Exception
##### Error
#### java.math
#### java.net
##### About
- ネットワークアプリケーションを実装するためのクラスを提供する。
  大きく分けて低レベルAPIと高レベルAPIの2つの部分に分けられる。
- 低レベルAPI:次の抽象概念を扱う
  - アドレス:IPアドレスのような、ネットワーク上の識別子
  - ソケット:基本的な双方向データ通信メカニズム
  - インターフェース:ネットワーク・インターフェースを記述する
- 高レベルAPI:次の抽象概念を扱う
  - URI:Universal Resource Identifier
  - URL:Universal Resource Locator
  - 接続:URLによって参照されるリソースへの接続を表す
##### Interfaces
##### Class
###### ClientHandler
###### DatagramSocket
- データグラム・パケットを送受信するためのソケット
###### ServerSocket
- サーバー・ソケットを実装する。
  ネットワーク経由で要求が送られてくるのを待ち、要求に基づいていくつかの操作を実行する。
  実際の処理はSocketImplクラスのインスタンスによって実行される。
  アプリケーションは、ソケット実装を作成するソケット・ファクトリを変更することでローカル・ファイアウォールに適したソケットを作成するようにアプリケーション自体を構成することができる。
- 
  - extends Object
  - implements Closeable
  
####### Constractors
######## ServerSocket()
- アンバウンドのサーバーソケットを作成する
######## ServerSocket(int port)
- 指定されたポートにバインドされたサーバー・ソケットを作成する
######## ServerSocket(int port, int backlog)
- サーバー・ソケットを作成し、指定された
######## ServerSocket(int port, int backlog, InetAddress bindAddr)
####### Methods
######## accept()
- public Socket accept() throws IOException
  Listens for a connection to be made to this socket and accepts it.
- Returns:
  the new Socket
- Throws:
  - IOException
  - SecurityExceptoin
  - SocketTimeoutException
  - IllegalBlockingModeException

###### Socket
####### Def
- public class Socket extends Object implements Closeable
- java.langObject
- Implemented Interfaces:
  Closeable, AutoCloseable
- クライアント・ソケットを実装する。
####### Constructors
####### Methods
######## getInputStream()
- InputStream getInputStream()
  Returns an input stream for this socket.
######## getOutputStream()
- OutputStream getOutputStream()
  Returns an output stream for this socket.
###### SocketAddress
- プロトコルに関連付けられていないソケット・アドレスを表す
###### SocketImpl
- 実際にソケットを実装するすべてのクラスに共通のスーパークラス。
####### Fields
####### Constrator
######## SocektImpl()
####### Methods
###### URI
###### URL
###### URLDecoder
####### Methods
######## decode(String s)
- Deprecated.
  The resulting string may vary depending on the platform's default encoding.
  use decode(String, String) method to specify the encoding.
######## decode (String s, String enc)
##### Enum
##### Exception
#### java.nio
#### java.nio.charset
#### java.nio.charset.spi
#### java.nio.file
#### java.nio.file.spi
#### java.nio.channels
#### java.nio.channels.spi
#### java.security
- Provides the classes and interfaces for the security framework.
##### Interfaces
###### PrivilegedAction<T>
- A computation to be performed with privileges enabled.
##### Classes
##### Enums
##### Exceptions
#### java.security.acl
#### java.security.cert
#### java.security.interfaces
#### java.security.spec
#### java.security.zip
#### java.text
##### Interfaces
##### Classes
###### SimpleDataFormat
- public class SimpleDateFormat
  extends DataFormat
- 日付のフォーマットと解析を、ロケールを考慮して行うための具象クラス。
####### Constructors
####### Methods
######## format(Date date, StringBuffer toAppendTo, FieldPosition pos)
- StringBuffer format(Date date, StringBuffer toAppendTo, FieldPosition pos)
  指定されたDateを日付/時間文字列にフォーマットし、指定されたStringBufferに結果を付与する。
#### java.text.spi
#### java.time
#### java.time.format
#### java.time.chrono
#### java.time.temporal
#### java.time.zone
#### java.util
##### Interfaces
###### Collection<E>
###### Enumeration<E>
- public interface Enumeration<E>
  An object that implements the Enumeration interface generates a series of elements, one at a time.
####### Methods
######## hasMoreElements()
- boolean hasMoreElements()
  Tests if this enumeration contains more elements.
######## nextElement()
- E nextElement()
  Returns the next element of this enumeration if this enumeration object has at least one more element to provide.
###### List<E>
###### Map<K,V>
- キーを値にマッピングするオブジェクト
####### Methods
######## computeIfAbsent(K key, Function<? super K,? super V,? extends V> remappingFunction)
- 指定されたキーがまだ値に関連付けられていない場合、指定されたマッピング関数を使用してその値の計算を試行し、null出ない場合はそれをこのマップに入力する。
######### Def
- default V computeIfAbsent(K key, Function<? super K,? super V,? extends V> remappingFunction)
######## get(Object key)
- 指定されたキーがマップされている値を返す。そのキーにマッピングが含まれていない場合はnullを返す。
######## put(K key, V value)
- 指定された値と指定されたキーをこのマップで関連付ける。
##### Class
###### AbstractCollection<E>
- Collectionインターフェースのスケルトン実装を提供する。
###### AbstractMap<K,V>
- Mapインターフェースのスケルトン実装を提供する。
###### HashMap<K,V>
- Mapインターフェースのハッシュ表に基づく実装
####### Def
- public class HashMap<K,V>
  extends AbstractMap<K,V>
  implements Map<K,V>, Cloneable, Serializable
####### Constractor
####### Methods
###### Locale
- public final class Locale extends Object implements Cloneable, Serializable
  This object represetns a specific geographical, political, or cultural region.
####### Nested Classes
####### Fields
######## CANADA
######## CANADA_FRENCH
######## CHINA
######## CHINESE
######## ENGLISH
######## FRANCE
######## FRENCH
######## GERMAN
######## GERMANY
######## ITALIAN
######## ITALY
######## JAPAN
######## JAPANESE
######## KOREA
######## KOREAN
######## PRC
######## PRIVATE_USE_EXTENSION
######## ROOT
######## SIMPLIFIED_CHINESE
######## TAIWAN
######## TRADITIONAL_CHINESE
######## UK
######## UNICODE_LOCALE_EXTENSION
######## US
####### Constructors
####### Methods
###### Objects
- オブジェクトで操作するためのstaticユーティリティ・メソッドで構成されている
####### Methods
######## requireNonNull(T obj)
- 指定されたオブジェクト参照がnullでないことを確認する。
######## requireNonNull(T obj, String message)
- 指定されたオブジェクト参照がnullでないことを確認し、nullの場合はカスタマイズされたNullPointerExceptionをスローする。
######## requireNonNull(T obj, Supplier<String> messageSupplier)
- 指定されたオブジェクト参照がnullでないことを確認し、nullの場合はカスタマイズされたNullPointerExceptionをスローする。
###### ResourceBundle
- public abstract class ResourceBundle extends Object
  Resource bundles contain locale-specific objects.
####### Nested Classes
####### Fields
####### Constructors
######## ResourceBundle()
- 
  Sole constructor.
####### Methods
######## getBundle(String baseName)
- static ResourceBundle getBundle(String baseName)
  Gets a resource bundle using the specified base name, the default locale, and the caller's class loader.
######## getBundle(String baseName, Locale locale)
- static ResourceBundle getBundle(String baseName, Locale locale)
  Gets resource bundle using the specified base name and locale, and the caller's class loader.
######## getKeys()
- abstract Enumeration<String> getKeys
  Returns an enumeration of the keys
#### java.util.function
#### java.util.regex
#### java.util.stream
#### java.util.concurrent
#### java.util.concurrent.atomic
#### java.util.concurrent.locks
#### java.util.logging
##### Interfaces
###### Filter
###### LoggingMXBean
##### Classes
###### ConsoleHandler
###### ErorrManager
###### FileHandler
###### Formatter
###### Handler
###### Level
- 
###### Logger
#### java.util.spi
### javax
#### javax.annotation
#### javax.crypto
#### javax.imageio
#### javax.imageio.event
#### javax.imageio.metadata
#### javax.imageio.pulgins.bmp
#### javax.imageio.pulgins.jpeg
#### javax.imageio.imagio.spi
#### javax.imageio.imagio.stream
#### javax.jws
##### Enums
###### WebParam.Mode
##### Annotations
###### HandlerChain
###### Oneway
###### WebMethod
###### WebParam
###### WebResult
###### WebService
#### javax.jws.soap
##### Enums
###### SOAPBinding.ParameterStyle
###### SOAPBinding.Style
###### SOAPBinding.Use
##### Annotations
###### SOAPBinding
#### javax.naming
##### Interfaces
###### Context
- public interface Context
- 
  This interface represents a naming context, which consists of a set of name-to-object bindings.
####### Fields
####### Methods
##### Classes
###### InitialContext
- public class InitialContext extends Objcet implements Context
- 
  This class is the starting context for preforming naming operations.
  
####### Fields
####### Constructors
####### Methods
######## lookup(Name name)
- Retrieves the named object.
######## lookup(String name)
- Retrieves the named object.
##### Exception
#### javax.xml.ws
- This package contains the core JAX-WS APIs.
##### Interfaces
##### Classes
###### Endpoint
- public abstract class Endpoint
  extends Object
- A Web service endpoint.
####### Fields
####### Constructors
####### Methods
######## publish(String address, Object implementor)
- static Endpoint publish(String address, Object implementor)
  Creates and publishes an endpoint for the specified implementor object at the given address.
- 第1引数がWebサービスを公開するアドレス、第2引数がWebサービスで公開するオブジェクト。
##### Enums
##### Exceptions
##### Annotations
### org
#### org.w3c.dom
#### org.w3c.dom.bootstrap
#### org.w3c.dom.events
#### org.w3c.dom.ls
#### org.w3c.dom.views
#### org.xml.sax
#### org.xml.sax.ext
#### org.xml.sax.helpers

