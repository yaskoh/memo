# Go - Standard Library
## Standard library
### archive
#### archive/tar
#### archive/zip
### bufio
### builtin
### bytes
### compress
#### compress/bzip2
#### compress/flate
#### compress/gzip
#### compress/lzw
#### compress/zlib
### container
#### container/heap
#### container/list
#### container/ring
### context
### crypto
#### aes
#### cipher
#### des
#### dsa
#### ecdsa
#### ellptic
#### hmac
#### md5
#### rand
#### rc4
#### rsa
#### sha1
#### sha256
#### sha512
#### subtle
#### tls
#### x509
##### pkix
### database
#### database/sql
##### database/sql/driver
### debug
#### debug/dwarf
#### debug/elf
#### debug/gosym
#### debug/macho
#### debug/pe
#### debug/plan9obj
### encoding
#### encoding/ascii85
#### encoding/ans1
#### encoding/base32
#### encoding/base64
#### encoding/binary
#### encoding/csv
#### encoding/gob
#### encoding/hex
#### encoding/json
#### encoding/pem
#### encoding/xml
### errors
### expvar
- interface to public variables, such as operation counters in servers.
### flag
### fmt
- formatted I/O with functions analogous to C's printf and scanf
#### Func
##### func Print
##### func Printf
##### func Println
##### func Scan
##### func Scanf
##### func Scanln
#### Type
### go
#### go/ast
#### go/build
#### go/constant
#### go/doc
#### go/format
#### go/importer
#### go/parser
#### go/printer
#### go/scanner
#### go/token
#### go/types
### hash
#### hash/adler32
#### hash/crc32
#### hash/crc64
#### hash/fnv
### html
#### html/template
### image
#### image/color
##### image/color/palette
#### image/draw
#### image/gif
#### image/jpeg
#### image/png
### index
#### index/suffixarray
- substring search in logarithmic time using an in-memory suffix array
### io
#### Overview
#### Constans
#### Variables
#### Functions
##### func Copy(dst Writer, src Reader) (written int64, err error)
- Copy copies from src to dst until either EOF is reached on src or an error occuers
#### Types
##### type Writer
###### func MultiWriter(writers ...Writer) Writer
### io/ioutil
### log
#### Constans
#### Functions
##### func Fatal(v ...interface{})
- Fatal is equivalent to Print() followed by a call to os.Exit(1)
##### func Fatalf(v ...interface{})
- Fatalf is equivalent to Printf() followed by a call to os.Exit(1)
#### Types
### log/syslog
### math
#### math/big
#### math/bits
#### math/cmplx
#### math/rand
- pseudo-random number generators
### mime
### mime/multipart
### mime/quotedprintable
### net
#### Overview
- portable interface for network I/O, including TCP/IP, UDP, domain name resolution, and Unix domain sockets.
#### Constants
#### Variables
#### Functions
#### Types
##### Conn
- a generic stream-oriented network connection
###### Def
###### Functions
####### func Dial(network, address string) (Conn, error)
- Dial connects to the address on the named network.
### net/http
#### Overview
#### Constants
#### Variables
#### Functions
##### func HandleFunc
- func HandleFunc(pattern string, handler func(ResponseWriter, * Requset))
- HandleFunc registers the handler function for given pattern in the DefaultServeMux.
##### func ListenAndServe
- func ListenAndServe(addr string, handler Handler) error
- ListenAndServe listens on the TCP network address addr and then calls Serve with handler to handle requests on incomming connections.
#### Types
##### type Client
##### type Cookie
##### type Dir
##### type File
##### type FileSystem
##### type Handler
- A Handler responts to an HTTP request.
  ServeHTTP should wirte reply headers and data to the ResponseWriter and then return.
- type Handler interface {
    ServeHTTP(ResponseWriter, *Request)
  }
##### type Header
##### type Pusher
##### type Request
##### type Response
##### type ResponseWriter
- A ResponseWriter interface is used by an HTTP handler to construct an HTTP response.
##### type ServeMux
- an HTTP requset multiplexer.
###### Functions
####### func NewServeMux() *ServeMux
####### func (mux *ServeMux) Handle(pattern string, handler Handler)
####### func (mux *ServeMux) HandleFunc(pattern string, handler func(ResponseWriter, *Request))
####### func (mux *ServeMux) Handleer(r *Request) (h Handler, pattern string)
####### func (mux *ServeMux) ServerHTTP(w Response Writer, r *Request)
##### type Server
##### type Transport
### net/http/cgi
### net/http/cookiejar
### net/http/fcgi
### net/http/httptest
### net/http/httptrace
### net/http/httputil
### net/http/pprof
### net/mail
### net/rpc
### net/rpc/jsonrpc
### net/smtp
### net/textprote
### net/url
### os
#### Constants
#### Variables
#### Functions
##### func Exit(code int)
- Exit causes the current program to exit with the given status code.
#### Types
### os/exec
### os/signal
### os/user
### path
#### path/filepath
### plugin
### regexp
#### regexp/syntax
### runtime
#### Constants
##### GOARCH
- sys.GOARCH
  architecture target: 386, amd64, arm...
##### GOOS
- sys.GOOS
  operating system target: darwin, freebsd, linux...
#### Variables
#### Func
#### Type
### runtime/cgo
### runtime/debug
### runtime/msan
### runtime/pprof
### runtime/race
### runtime/trace
### sort
### strconv
### strings
### sync
#### Overview
- basic synchronization primitives such as mutual execution lock.
#### Types
##### type Cond
##### type Locker
##### type Map
##### type Mutex
##### type Once
- Once is an object that will perform exactly one action.
###### Functions
####### func (o *Once) Do(f func())
##### type Pool
##### type RWMutex
##### type WaitGroup
### sync/atomic
### syscall
### testing
### testing/iotest
### testing/quick
### text
### text/
### text/
### text/template
### text/template/parse
### time
#### Constants
#### Func
##### func Now() Time
- returns the curent local time.
##### func (t Time) Weekday() Weekday
- returns teh day of the week specified by t.
#### Type
### unicode
### unicode/utf16
### unicode/utf8
### unsafe
