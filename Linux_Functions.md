# Linux Functions
## System calls
### _llseek(2)
### _exit(2)
- 
  statusを終了ステータスとしてプロセスを終了する。
  絶対に失敗しないので、呼び出したら戻らない。
  exit(3)と異なりlibc関連の後始末を行わない。

- def
  #include <unistd.h>
  void _exit(int status);

### brk(2)
- 
  物理アドレスが割り当てられていないページに物理アドレスを対応させる。
  malloc(3)やrealloc(3)が使っているシステムコール。
  sbrk(2)というシステムコールもある。

### chdir(2)
- 
  自プロセスのカレントディレクトリをpathに変更する。
  成功したら0、失敗したら-1を返しerrnoをセットする。

- def
  #include <unistd.h>
  int chdir(const char *path);

### chmod(2)
- 
  pathのモードをmodeに変更する。
  成功したら0を返し、失敗したら-1を返してerrnoをセットする。

- def
  #include <sys/types.h>
  #include <sys/stat.h>
  
  int chmod(const char *path, mode_t mode)

### chown(2)
- 
  pathの所有ユーザをownerに、所有グループをgroupに変更する。
  ownerはユーザID, groupはグループID。
  どちらかだけを変更したい場合、変更しない値を-1とする。
  lchownは、pathがシンボリックリンクだった場合はシンボリックリンク自体の情報を変更する。
  成功したら0を返す。失敗したら-1を返し、errnoを設定する。
  所有ユーザを変更する場合はスーパーユーザ権限が必要。
  所有グループを変更する場合はファイルの所有ユーゼでかつ自分がgroupに含まれる必要がある。
  スーパーユーザならば任意のグループに変更可能。

- def
  #include <sys/types>
  #include <unistd.h>
  
  int chown(const char *path, uid_t owner, gid_t group);
  int lchown(const char *path, uid_t owner, gid_t group);

### close(2)
- def
  #include <unistd.h>
  int close(int fd);

- argument
  fd:ファイルディスクリプタ

- return
  問題なく閉じられた場合は0, エラーがあった場合は-1を返す。

- ex
  if (close(fd) < 0){
      /* エラー処理 */
  }

### dup(2), dup2(2)
- 
  oldfdを複製するシステムコール。
  dup()は使われていない最小のファイルディスクリプタへoldfdを複製してそれを返す。
  dup2()はoldfdをnewfdに複製してそれを返す。
  エラーが起きた場合は-1を返す。
  dupはduplicateから。

- def
  #include <unistd.h>
  int dup(int oldfd);
  int dup2(int oldfd, int newfd);

### exec(2)
- 
  現在実行してるプロセスが消滅し、自プロセスに新しいプログラムをロードする。
  execは成功すると呼び出しが戻らないので、戻った場合は常に失敗。-1を返してerrnoをセットする。
  - l
    語尾に"l"がつくものは、コマンドライン引数を引数リストとして渡す。
    引数リストの最後はNULLを置かなければならない。
  - v
    コマンドライン引き巣を文字列の配列で渡す。argv[]の最後の要素はNULLにしなければならない。
  - e
    最後の引数として環境変数envpが追加される。
    eがついていないAPIでは、現プロセスの環境変数がそのまま使われる。
  - p
    第1引数programを環境変数PATHから自動で探す。
    pがついていない場合、常にpathを絶対パスまたは相対パスで指定しなければならない。

- def
  #include <unistd.h>

  int execl(const char *path, const char *arg, ... /* NULL */);
  int execlp(const char *program, const char *arg, ... /* NULL */);
  int execle(const char *path, const char *arg, ... /* NULL, */
             char * const envp[]);
  int execv(const char *path, char * const argv[]);
  int execvp(const char *program, char * const argv[]);
  int execve(const char *path, char * const argv[],
             char * const envp[]);

### fcntl(2)
- 
  ファイルディスクリプタ関連の操作をioctlより分離したもの。

- def
  #include <unistd.h>
  #include <fcntl.h>
  int fcntl(int fd, int cmd, ...);

### fork(2)
- create a child process
- Synopsis
  #include <unistd.h>
  ptd_t fork(void);

- 
  プロセスを複製し、2つのプロセスに分裂させる。
  両方のプロセスでfork()の呼び出しが戻る。
  元から存在しているほうを親プロセス、複製した方を子プロセスという。
  子プロセスでの戻り値は0で、親プロセスの戻り値は子プロセスのプロセスIDとなる。
  失敗した場合は子プロセスは作成されず、親でのみ-1が戻る。

- def
  #include <sys/types.h>
  #include <unistd.h>
  pid_t fork(void);

### getgroups(2)
- 
  自プロセスの捕捉グループIDをbufに書き込む。
  捕捉グループIDがbufsize個より多い場合は、エラーを返す。
  成功した場合捕捉グループIDの数を、失敗した場合は-1を返してerrnoをセットする。

- def
  #include <unistd.h>
  #include <sys/types.h>
  
  int getgroups(int bufsie, gid_t *buf);

### getpid(2), getppid(2)
- 
  getpid()は自分のプロセスIDを返す。
  getppid()は親プロセスのppidを返す。

- def
  #include <sys/types.h>
  #include <unistd.h>
  pid_t getpid(void);
  pid_t getppid(void);

### getrusage(2)
- 
  プロセスのリソース使用量を第2引数usageに書き込む。
  第1引数whoがRUSAGE_SELFならば自プロセスのリソース使用量を書き込む。
  第1引数whoがRUSAGE_CHILDRENならば子プロセスのリソース使用量を書き込む。
  この場合の子プロセスは「自プロセスからfork()した子プロセス全てのうち、waitしたもの」を意味する。
  呼び出しが成功したら0を返す。失敗したら-1を返してerrnoをセットする。

- def
  #include <unistd.h>
  #include <sys/resource.h>
  #include <sys/time.h>
  
  int getrusage(int who, struct rusage *usage);

- struct rusage
  「man getrusage」には沢山のメンバがあるが、
  Linuxではそのうちの一部しか正しい値がセットされない。
  
  |----------------+-----------+--------------------------|
  | 型             | メンバ名  | 意味                     |
  |----------------+-----------+--------------------------|
  | struct timeval | ru_utime  | 使われたユーザ時間       |
  | struct timeal  | ru_stime  | 使われたシステム時間     |
  | long           | ru_majflt | メジャーフォールトの回数 |
  | long           | ru_minflt | マイナーフォールトの回数 |
  | long           | ru_nswap  | スワップサイズ           |
  |----------------+-----------+--------------------------|

### gettimeofday(2)
- 
  UNIXエポックから現在までの経過時間をtvに書き込む。
  tzは既に使われていないので常にNULLを指定する。
  実行が成功したら0を返し、失敗したら-1を返しerrnoをセットする。

- def
  #include <sys/time.h>
  
  int gettimeofday(struct timeval *tv, struct timezone *tz);
  
  struct timeval {
      long tv_sec;   /* 秒 */
      long tv_usec;  /* ミリ秒 */
  };

### getuid(2), getgid(2)
- 
  現在のクレデンシャルを得る。
  getuidは実ユーザIDを、geteuidは実行ユーザIDを、
  getgidは実グループIDを、getegidは実行グループIDを、
  それぞれ返す。
  これらのシステムコールは失敗しない。

- def
  #include <unistd.h>
  #include <sys/types.h>
  
  uid_t getuid(void);
  uid_t geteuid(void);
  gid_t getgid(void);
  gid_t getegid(void);

### initgroups(2)
- 
  /etc/groupなどのデータベースを見て、
  ユーザuserの補足グループを自プロセスに設定する。
  また、第2引数のgroupも追加する。
  groupは通常、ユーザのグループ(primary group)を補足グループにも追加するために使う。
  成功したら0を返す。失敗したら-1を返しerrnoを設定する。
  スーパーユーザでないと成功しない。

- def
  #define _BSD_SOURCE
  #include <grp.h>
  #include <sys/types.h>
  
  int initgroups(const char *user, gid_t group);

### ioctl(2)
- 
  ストリームがつながる先にあるデバイスに特化した操作を全て含めたシステムコール。

- def
  #include <sys.ioctl.h>
  int ioctl(int fd, int request, ...);

- argument
  request:どのような操作をするか定数で指定し、そのrequest特有の引数を第3引数以降に渡す。

### kill(2)
- 
  シグナルを送信するシステムコール。
  プロセスIDがpidのプロセスにシグナルsigを送信する。
  成功したら0を返す。失敗したら-1を返し、errnoをセットする。
  pidが負数のときは、IDが-pidのプロセスグループ全体にシグナルを送る。
  プロセスグループにシグナルを送るには、killpg()という専用のシステムコールもある。

- def
  #include <sys/types.h>
  #include <signal.h>
  
  int kill(pid_t pid, int sig);

### link(2)
- 
  ファイルsrcの実態に新しい名前distをつける。(ハードリンク）
  成功したときは0を返し、失敗したときは-1を返してerrnoをセットする。
  srcとdistは同じファイルシステム上に存在する必要がある。
  また、ディレクトリには使用できない。

- def
  #include <unistd.h>
  int link(const char *src, const char  *dest);

### lseek(2)
- 
  ファイルディスクリプタfd内部のファイルオフセットを指定した位置offsetへ移動する。
  移動方法はwhenceに指定する。

- def
  #include <sys/types.h>
  #include <unistd.h>
  off_t lseek(int fd, off_t offset, int whence);

- argument
  whence:位置の指定方法。
         SEEK_SET:offsetに移動（起点はファイル先頭）
         SEEK_CUR:現在のファイルオフセット+offsetに移動
         SEEK_END:ファイル末尾+offsetに移動

### mkdir(2)
- 
  ディレクトリpathを作成する。
  成功したら0を返し、失敗したら-1を返してerrnoをセットする。
  第2引数には作成時のパーミッションを指定する。

- def
  #include <sys/stat.h>
  #include <sys/types.h>

  int mkdir(const char *path, mode_t mode);

- error
  - ENOENT
    親ディレクトリがない
  - ENOTDIR
    pathで親ディレクトリに当たる部分がディレクトリでない
  - EEXIST
    pathにすでにファイルやディレクトリが存在する
  - EPERM
    親ディレクトリを変更する権限がない

### mmap(2)
- 
  ファイルやデバイスをメモリにマップ/アンマップする
  ファイル記述子fdで指定されたファイルの、オフセットoffsetからlengthバイトの範囲を
  メモリにマップする。
  このとき、なるべくメモリ上のaddrアドレスからはじめるようにマップする。
  実際には関数に対してのヒントでしかなく、通常は0を選択する。
  protは、メモリ保護をどのように行うか指定する。
  flagsは、マップされたオブジェクトのタイプ、マップ時のオプション、
  マップされたページコピーへの変更をそのプロセスだけが行えるのか指定する。

- def
  #include <sys/mman.h>
  void *mmap(void *addr, size_t length, int prot, int flags,
             int fd, off_t offset);
  int munmap(void *addr, size_t length);

#### Args
##### addr
- NULL: カーネルがマッピングを作成するアドレスを選択する。移植性のある新しいマッピング方法。
- NULLでない場合: どこに配置するかのヒントとしてaddrの値を利用。

##### prot
- 
  |------------+--------------|
  | フラグ名   | 内容         |
  |------------+--------------|
  | PROT_EXEC  | 実行可能     |
  | PROT_READ  | 読み込み可能 |
  | PROT_WRITE | 書き込み可能 |
  | PROT_NONE  | アクセス不能 |
  |------------+--------------|

##### flags
- マッピングに対する更新が同じ領域を更新している他のプロセスに見えるか否かを設定する。
- MAP_SHARED
- MAP_PRIVATE
#### Return
- 
  - mmap
    成功するとマップされた領域へのポインタを返す。
    失敗すると値MAP_FAILED((void *)-1)を返し、errnoがセットされっる。
  - munmap
    成功すると0を返し、失敗すると-1を返しerrnoがセットされる（多くの場合EINVAL）。

#### Error
### open(2)
- def
  #include <sys/types.h>
  #include <sys/stat.h>
  #include <fcntl.h>
  int open(const char *path, int flags);
  int open(const char *path, int flags, mode_t mode);

- argument
  path:openするファイルのパス
  flags:ストリームの性質を表すフラグ
  mode:O_CREATを指定した場合に、新規ファイルのパーミッションを指定する

  - flags 1
    常にどれか一つを指定する
    |----------+--------------|
    | O_RDONLY | 読み取り専用 |
    | O_WRONLY | 書込み専用   |
    | O_RDWR   | 読み書き両用 |
    |----------+--------------|

  - flag 2
    指定しなくても良いし、複数指定しても良い。
    下のもの以外にも色々ある。
    |----------+-----------------------------------------------------------------------------------|
    | O_CREAT  | ファイルが存在しなければ新しいファイルを作る                                      |
    | O_EXCL   | O_CREATとともに指定すると、すでにファイルが存在するときはエラーとなる             |
    | O_TRUNC  | O_CREATとともに指定すると、ファイルが存在するときはまずファイルの長さをゼロにする |
    | O_APPEND | write()が常にファイル末尾に書込まれるよう指定する                                 |
    |----------+-----------------------------------------------------------------------------------|

- return
  ファイルディスクリプタの値を返す。
  値はプロセスがオープンしていないファイルディスクリプターのうち最小の数字となる。

  - ex
    open(file, O_RDWR|O_CREAT|O_TRUNC, 0666)

### pipe(2)
- 
  両端とも自プロセスにつながったストリームを作成し、その両端のディスクリプタを返す。
  

- def
  #include <unistd.h>
  int pipe(int fds[2]);

### read(2)
- def
  #include <unistd.h>
  ssize_t read(int fd, void *buf, size_t bufsize);

- argument
  fd:ファイルディスクリプタの番号
  buf:格納先
  bufsize:最大読込バイト数

- return
  正常終了した場合は読込んだバイト数を返す。
  ファイル終端に達したときは0を、エラーが起きたときは-1を返す。

### readlink(2)
- 
  readlinkは、pathの表している名前をbufに格納する。
  ただし、いかなる場合もbufsizeバイトまでしか書込まない。
  また、文字列最後の'\0'は書込まれない。
  成功したらbufに格納したバイト数を返す。失敗したら-1を返してerrnoをセットする。
- def
  #include <unistd.h>
  int readlink(const char *path, char *buf, size_t bufsize);

### rename(2)
- 
  srcをdestに変更する。
  成功したら0を、失敗したら-1を返してerrnoをセットする。
  ファイルシステムをまたいで移動することはできない。その場合EXDEVがerrnoにセットされる。
- def
  #include <stdio.h>
  int rename(const char *src, const char *dest);

### rmdir(2)
- 
  ディレクトリpathを削除する。

- def
  #include <unistd.h>
  int rmdir(const char *path);

### setsid(2)
- 
  新しいセッションを作成し、自分がセッションリーダーになる。
  同時にそのセッションで最初のプロセスグループを作成し、そのグループリーダーとなる。
  戻り値は作成したセッションID。失敗した場合は-1を返しerrnoをセットする。
  失敗する多くの場合は、自分がプロセスグループリーダーの場合なので、
  あらかじめ1回多くforkしておいてグループリーダーではなくなっている必要がある。
  制御端末を持たないため、デーモンとなる。

- def
  #include <unistd.h>
  pid_t setsid(void);

### setuid(2), setgid(2)
- 
  setuid()は、実ユーザIDと実行ユーザIDをidに変更する。
  setgid()は、実グループIDと実行グループIDをidに変更する。
- def
  #include <unistd.h>
  #include <sys/types.h>
  
  int setuid(uid_t id);
  int setgid(gid_t id);

### sigaction(2)
- 
  sigaction()は第1引数のシグナルsigのハンドラを登録する。
  第2引数actにシグナルハンドラを指定する。具体的には関数ポインタかSIG_IGN, SIG_DFL。
  第3引数のoldactには、sigaction()呼び出し時のハンドラが返る。不要ならNULLを指定する。
  struct sigcationのsa_sigcationもシグナルハンドラを指定するメンバで、
  受信したときにシグナル番号以外の情報を得ることが出来る。
  
- def
  #include <signal.h>
  
  int sigaction(int sig, const struct sigaction *act,
                struct sigaction *oldact);
  
  struct sigaction {
      /* sa_handler, sa_sigactionは片方のみ使う */
      void (*sa_handler)(int);
      void (*sa_sigaction)(int, siginfo_t*, void*);
      sigset_t sa_mask;
      int sa_flags;
  };

- signalの問題点に対する対処
  - ハンドラの再設定
    sigaction()はOSに関わらずシグナルハンドラの設定を保持し続けることを保証する。
  - システムコールの再起動
    sigaction()はデフォルトでシステムコールを再起動しない。
    sa_flagsメンバにフラグSA_RESTARTを追加すると再起動する設定になる。
    一般には再起動されるほうが便利なので、SA_RESTARTを常に追加しておくのが無難。
  - シグナルのブロック
    sa_maskでブロックするシグナルを指定できる。
    シグナルハンドラの起動中は処理中のシグナルを自動的にブロックしてくれるので、
    ほとんどの場合はsa_maskは空にしておけば十分。空にするにはsigemptyset()を使う。

- sigset_t操作API
  - int sigemptyset(sigset_t *set);
    setを空に初期化する
  - int sigfillset(sigset_t *set);
    setをすべてのシグナルを含む状態にする
  - int sigaddset(sigset_t *set, int sig);
    シグナルsigをsetに追加する
  - int sigdelset(sigset_t *set, int sig);
    シグナルsigをsetから削除する
  - int sigismember(const sigset_t *set, int sig);
    シグナルsigがsetに含まれるとき真をかえす

- シグナルのブロック
  ブロックしていたシグナルを配送してもらうためのAPI。
  sigprocmaskは自プロセスのシグナルマスクをセットする。
  セット方法はフラグhowで決まる。
  sigpendingは保留されているシグナルをsetに書き込む。
  成功したら0、失敗したら-1を返しerrnoをセットする。
  sigsuspendはシグナルマスクmaskをセットすると同時にプロセスをシグナル待ちにする。
  ブロックしていたシグナルを解除して、保留されていたシグナルを処理するときに使う。
  sigsuspendは常に-1をかえす。

  - def
    #include <signal.h>
    
    int sigprocmask(int how, sigset_t *set, sigset_t *oldset);
    int sigpending(sigset_t *set);
    int sigsuspend(const sigset_t *mask);

  - sigprocmaskのhow値
    |-------------+---------------------------------------------------|
    | 値          | 効果                                              |
    |-------------+---------------------------------------------------|
    | SIG_BLOCK   | setに含まれるシグナルをシングルマスクに追加する   |
    | SIG_UNBLOCK | setに含まれるシグナルをシグナルマスクから削除する |
    | SIG_SETMASK | シグナルマスクをsetに置き換える                   |
    |-------------+---------------------------------------------------|

### signal(2)
- 
  signalを捕捉するAPI。
  シグナルを送るAPIでなくtrapするAPIなので注意。
  
  シグナル番号sigのシグナルを受けたときの挙動を、
  第2引数funcの関数を呼ぶように変更する。
  このfuncに渡す関数を、シグナルを処理する関数という意味でシグナルハンドラ(signal handler)と呼ぶ。

  問題が色々とあるため、sigaction()を用いるのがよい。

- def
  #include <signal.h>
  void (*signal (int sig, void (*func)(int)))(int)

  (わかりにくいので少し書き直すと↓
   typedef void (*sighandler_t)(int);
   sighandler_t signal(int sig, sighandler_t func);
  )

- 第2引数funcで用いられる特別な値
  |---------+--------------------------------------------------|
  | 定数    | 意味                                             |
  |---------+--------------------------------------------------|
  | SIG_DFL | OSのデフォルトの動作に戻す                       |
  | SIG_IGN | カーネルレベルでシグナルを無視するように指示する |
  |---------+--------------------------------------------------|

### stat(2), fstat, lstat, fstatat
- 
  statはpathで表されるエントリの情報を取得し、bufに書き込む。
  lstatもほとんど同じだが、シンボリックリンクの場合にリンクをたどらず自身の情報を返す。
  似たものに、ファイルディスクリプタから同じ情報を得られるfstatもある。
  成功したら0を返し、失敗したら-1を返してerrnoをセットする。
  
  原義はstatusらしい。

- def
  #include <sys/types.h>
  #include <sys/stat.h>
  #include <unistd.h>

  int stat(const char *path, struct stat *buf);
  int lstat(const char *path, struct stat *buf);

- struct statメンバ
  |-----------+------------+--------------------------------------------|
  | 型        | メンバ名   | 説明                                       |
  |-----------+------------+--------------------------------------------|
  | dev_t     | st_dev     | デバイス番号                               |
  | ino_t     | st_ino     | iノード番号                                |
  | mode_t    | st_mode    | ファイルタイプとパーミッションを含むフラグ |
  | nlink_t   | st_nlink   | リンクカウント                             |
  | uid_t     | st_uid     | 所有ユーザID                               |
  | gid_t     | st_gid     | 所有グループID                             |
  | dev_t     | st_rdev    | デバイスファイルの種別を表す番号           |
  | off_t     | st_size    | ファイルサイズ（バイト単位）               |
  | blksize_t | st_blksize | ファイルのブロックサイズ                   |
  | blkcnt_t  | st_blocks  | フロック数                                 |
  | time_t    | st_atime   | 最終アクセス時刻                           |
  | time_t    | st_mtime   | 最終変更時刻                               |
  | time_t    | st_ctime   | 付帯情報が最後に変更された時期             |
  |-----------+------------+--------------------------------------------|

### symlink(2)
- 
  シンボリックリンクを作成するシステムコール。
  srcを指す新しいシンボリックリンクをdestに作成する。
  成功したら0を、失敗したら-1を返す。
- def
  #include <unistd.h>
  int symlink(const char *src, const char *dest);

### time(2)
- 
  UNIXエポックから現在までの経過秒数を返す。
  tptrがNULLでない場合は*tptrにも同じ値を書き込む。
  秒までの単位しか扱えない。

- def
  #include <time.h>
  time_t time(time_t *tptr);

### umask(2)
- 
  直前までのumaskの値をmaskに変更し、直前万でのumaskを返す。
- def
  #include <sys/types.h>
  #include <sys/stat.h>
  
  mode_t umask(mode_t mask);

### unlink(2)
- 
  名前pathを消す。成功したら0を、失敗したら-1を返す。
  ディレクトリの削除はできない。
- def
  #include <unistd.h>
  int unlink(const char *path);

### utime(2)
- 
  pathの最終アクセス時刻(st_atime)と最終更新時刻(st_mtime)を変更する。
  bufがNULLでなければ最終アクセス時効をbuf->actime, 最終更新時刻をbuf->modtimeに変更する。
  bufがNULLなら両方を現在時刻に変更する。
  成功したら0を返し、失敗したら-1を返しerrnoを設定する。

- def
  #include <sys/types.h>
  #include <utime.h>
  
  int utime(const char *path, strut utimbuf *buf);
  
  struct utimbuf {
      time_t actime; /* 最終アクセス時刻 */
      time_t modtime; /* 最終更新時刻 */
  }

### wait(2)
- 
  waitは子プロセスのうちどれかひとつが終了するのを待つ。
  waitpidはpidで指定したプロセスが終了するのを待つ。
  statusにNULL以外を指定した場合、そのアドレスに子プロセスの終了ステータスが格納される。

- def
  #include <sys/types.h>
  #include <sys/wait.h>
  
  pid_t wait(int *status);
  pid_t waitpid(pid_t pid, int *status, int options);

- 終了の仕方を調べるマクロ

  |---------------------+----------------------------------------------------|
  | マクロ              | 意味                                               |
  |---------------------+----------------------------------------------------|
  | WIFEXITED(status)   | exitで終了していたら非0、それ以外なら0             |
  | WEXITSTATUS(status) | exitで終了し手いたときに、その終了コードを返す。   |
  | WIFSIGNALED(status) | シグナルで終了したら非0、それ以外なら0             |
  | WTERMSIG(status)    | シグナルで終了したときに、そのシグナル番号を返す。 |
  |---------------------+----------------------------------------------------|

### write(2)
- def
  #include <unistd.h>
  ssize_t write(int fd, const void *buf, size_t bufsize)

- argument
  fd:ファイルディスクリプタの番号
  buf:書込元
  bufsize:最大書込サイズ数

- return
  正常終了時は書き込んだバイト数を返す。
  エラー時は-1を返す。

## System calls (assembly)
- http://blog.rchapman.org/posts/Linux_System_Call_Table_for_x86_64/
- https://syscalls.kernelgrok.com/
### sys_read(rax:0)
- rax: 0
- rdi: unsigned int fd
- rsi: char *buf
- rdx: size_t count
### sys_write(rax:1)
- rax: 1
- rdi: unsigned int fd / ディスクリプタ(1=stdout)
- rsi: const char *buf / output file address
- rdx: size_t count / output byte counts
### sys_exit (rax:60)
- rax: 60
- rdi: int error_code
## Subroutine
## Headers
### aio.h
### arpa/inet.h
### assert.h
### complex.h
### cpio.h
### ctype.h
### dirent.h
### dlfcn.h
### errno.h
### fcntl.h
- ファイル操作用のPOSIX関数
  - create(), fcntl(), open()
### fenv.h
### float.h
### fmtmsg.h
### fnmatch.h
### ftw.h
### glob.h
### grp.h
### iconv.h
### inttypes.h
### iso646.h
### langinfo.h
### libgen.h
### limits.h
### locale.h
### math.h
### monetary.h
### mqueue.h
### ndbm.h
### net/if.h
### netdb.h
### netinet/in.h
### netinet/tcp.h
### nl_types.h
### poll.h
### pthread.h
### pwd.h
### regex.h
### sched.h
### search.h
### semaphore.h
### setjmp.h
### signal.h
### spawn.h
### stdarg.h
### stdbool.h
### stddef.h
### stdint.h
### stdio.h
### stdlib.h
### string.h
### strings.h
### stropts.h
### sys/ipc.h
### sys/mman.h
### sys/msg.h
### sys/resource.h
### sys/select.h
### sys/sem.h
### sys/shm.h
### sys/socket.h
### sys/stat.h
### sys/statvfs.h
### sys/time.h
### sys/times.h
### sys/types.h
- data types
#### blkcnt_t
#### blksize_t
#### pid_t
- Used for process IDs and process group IDs.
#### size_t
- Used for sizes of objects.
### sys/uio.h
### sys/un.h
### sys/utsname.h
### sys/wait.h
### syslog.h
### tar.h
### termios.h
### tgmath.h
### time.h
### trace.h
### ulimit.h
### unistd.h
- standard symbolic constants and types
### utime.h
### utmpx.h
### wchar.h
### wctype.h
### wordexp.h
## Link
- [[http://man7.org/linux/man-pages/man2/syscalls.2.html][SYSCALLS(2) - Linux Programmer's Manual]]
- [[https://linuxjm.osdn.jp/html/LDP_man-pages/man2/syscalls.2.html][SYSCALLS - Linux Programmer's Manual (2)]]
- [[http://pubs.opengroup.org/onlinepubs/9699919799/nframe.html][The Open Group base Specifications Issue 7]]
