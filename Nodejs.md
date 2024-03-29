# Node.js
## v10.5.0
### File System
#### Classes
##### Class:fs.FSWatcher
##### Class:fs.ReadStream
###### Event:close
###### Event:open
###### Event:ready
###### readStream.bytesRead
###### readStream.path
##### Class:fs.Stast
##### Class:fs.WriteStream
#### Methods
##### fs.access(path[,mode],callback)
##### fs.accessSync(path[,mode])
#### Constans
#### Flags
### Net
### OS
### Path
### Readline
#### Classes
##### Class:Interface
###### Event:close
- The event is emitted when one of the following occur:
  - rl.close() method is called
  - input receives 'end'
  - input receives <ctrl>-D
  - input receives <ctrl>-C to signal SIGINT
###### Event:line
- whenever the input stream receives an end-of-line input (\n, \r or \r\n).
###### Event:pause
###### Event:resume
- The event is emitted whenever the input stream is resumed.
###### Event:SIGCONT
###### Event:SIGINT
###### Event:SIGTSTP
###### rl.close()
###### rl.pause()
###### rl.resume()
#### Methods
##### readline.clearLine(stream,dir)
##### readline.createInterface(options)
###### Arguments
- options <Object>
  - input <stream.Readable>
  - output <stream.Writable>
  - completer <Function>
  - terminal <boolean>
  - historySize <number>
  - prompt <string>
  - ctlfDeley <number>
  - removeHistoryDupulicates <boolean>
  
###### Retrun
- The method creates a new "readline.Interface" instance.
### Stream
## old
### v4.5.0
#### Command
- node [options] [v8 options] [script.js | -e "script"] [arguments]
##### Options
###### -v, --version
- Print node's version
###### -h, --help
- Print node command line options.
###### -e, --eval "script"
- Evaluate the following argument as JavaScript.
###### -p, --print "script"
- Identical to -e but prints the result.
##### Environmental Variables
###### NODE_PATH=path[:...]
##### Link
- [[https://nodejs.org/dist/latest-v4.x/docs/api/cli.html][Command Line Options - Node.js]]
#### Global Objects
##### Class:Buffer
##### __dirname
##### __filename
##### clearImmediate(immediateObject)
##### clearInterval(intervalObject)
##### clearTimeout(timeoutObject)
##### console
- <Object>
  Used to print to stdout and stderr.
  
##### exports
- 
  A reference to the "module.exports".

##### global
- <Object> The global namespace object
  In browsers, the top-level scope is the global scope.
  In Node.js, the top-level scope is not the global scope, and variables inside an Node.js module will be local to that module.
##### module
- <Object>
  A reference to the current module.
  In particular "module.exports" is used for defining what module exports and makes available through "require()".
  "module" isn't actually a global but rather local to each module.

##### process
- <Object>
  The process object.
##### require()
- <Function>
  To reqire modules.
  "require" isn't actually a global but rather local to each module.
##### setImmediate(callback[,arg][, ...])
##### setInterval(callback, delay[, arg][, ...])
##### setTimeout(callback, delay[, arg][, ...])
##### Link
- [[https://nodejs.org/dist/latest-v4.x/docs/api/globals.html][Globals - Node.js]]
#### Core Modules
##### Assert
##### Console
###### Class:Console
####### new Console(stdout[, stderr])
####### consle.assert(value[, mesage][, ...])
####### console.dir(obj[, options])
####### console.error([data][, ...])
####### console.info([data][, ...])
####### console.log([data][, ...])
####### console.time(label)
####### console.timeEnd(label)
####### console.trace(mesage[, ...])
####### console.warn([data][, ...])
##### HTTP
###### Class:http.Agent
###### Class:http.ClientRequest
###### Class:http.Server
###### Class:http.ServerResponse
###### Class:http.IncomingMessage
###### http.METHODS
###### http.STATUS_CODES
###### http.createClient([port][,host])
###### http.createServer([requestListener])
- Returns a new instance of http.Server.
  The "requestListener" is a function which is automatically added to the 'request' event.
###### http.get(options[,callback])
###### http.globalAgent
###### http.request(options[, callback])
##### Net
###### Class:net.Server
- The class inherits from net.Srever and has some additional events
####### Event:'checkContinue'
####### Event:'clientError'
####### Event:'connect'
####### Event:'connection'
####### Event:'request'
####### Event:'upgrade'
####### server.close([callback])
####### server.listen(handle[,callback])
####### server.listen(path[,callback])
####### server.listen(port[,callback])
####### server.listen(handle[,callback])
####### server.listen(handle[,callback])
###### Class:net.Socket
## Link
- [[https://nodejs.org/en/][node.js]]

- [[https://yosuke-furukawa.hatenablog.com/entry/2018/06/07/080335][Node.js�ɂ�����݌v�~�X By Ryan Dahl - from scratch]]

- [[https://github.com/pana/node-books][Pana/node-books - GitHub]]
### v4.5.0
- [[https://nodejs.org/dist/latest-v4.x/docs/api/cli.html#cli_command_line_options][Command Line Options - Node.js v4.5.0 Documentation]]

### Tutorial
- http://www.nodebeginner.org/index-jp.html
- http://rfs.jp/sb/javascript/node
- http://libro.tuyano.com/index2?id=1115003
- http://sakuratan.biz/archives/3101

- [[https://qiita.com/kenju/items/fe149acfa8f7b0ec25c8][Node.js�ǋL���܂Ƃ�(�����X�V) - Qiita]]
- https://qiita.com/MASAYUKI-ABE/items/856172b2958701d42808 (Express)
