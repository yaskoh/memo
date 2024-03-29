# Linux Memo
## アクセス権の補助フラグ
### suid
- 
  set user id。
  コマンドを実行するユーザに関係なく特定のユーザで実行したいときに、
  ファイルパーミッションのset-uidビット(set-user-ID bit)を立てておくと、
  起動したユーザに関わらず、ファイルのオーナー権限で起動される。
  パーミッションのxがsと表示される。
  setuid()システムコールとは何の関係もない。
-
  起動ユーザIDを実ユーザID(real user ID)、
  オーナーIDを実行ユーザID(effective user ID)という。

### sgid
- 
  set group id。
  suidとほとんど同じなのでそちらを参照。

- 
  起動ユーザグループIDを実グループID(real group ID)、
  プログラム所有グループIDを実行グループID(effective group ID)という。

### sticky
- 
  実行が終了した後もメモリ内にプログラムを残しておくようにカーネルへ要求する。
  再実行する際に高速に処理をすることを目的とするが、メモリの大容量化に伴い、使われなくなっている。

## heredoc
- 
  ヒアドキュメント。
  << の後にデリミタとなる識別子を続け、最初に指定した識別子だけの行がくるまで入力が続く。
  
  - 行頭を<<-ではじめることで、行頭のタブが無視され、インデントを崩さずヒアドキュメントを書ける。
  - デフォルトでは、変数展開やバッククオートのコマンド展開が行われる。($PWD等)
  - デリミタを引用符で囲むことで(<< "EOF")、コマンド展開等を無効にできる。

- ex:)
    cat > ~/.bashrc << "EOF"
    set +h
    unmask 022
    EOF

## Ctrl-s
- 
  スクロール停止キー。画面がフリーズしたように見える。
  ログを見ていて、一時的にとめておくために使ったりする。
  解除はCtrl-q

## glob
- 
  シェルが*?{}[]~などを解釈し、ファイル名として展開することをグロブ（ファイルグロブ）という。
  正規表現とは別物。
  働かせたくない場合は""等で囲む。
  ちなみにWindowsではLinuxと異なりプログラム側で展開する。

## tty, pts
- tty
  端末を表すttyは、TeleTYpewriterの略。
  制御端末のこと。実端末。

- pts
  sshなどの仮想端末。

- ptmx

## standard input/output
- 
  |----------------+---------------+--------+----------------|
  | FileDiscriptor | Macro         | stdio  | Meaning        |
  |----------------+---------------+--------+----------------|
  |              0 | STDIN_FILENO  | stdin  | 標準入力       |
  |              1 | STDOUT_FILENO | stdout | 標準出力       |
  |              2 | STDERR_FILENO | stderr | 標準エラー出力 |
  |----------------+---------------+--------+----------------|

## sys/types.h システム定義型
OSやCPUの差異を隠蔽するために別名で基本型を再定義している。
- size_t
  符号なし整数型
- ssize_ti
  符号付き整数型

## '\0'の有無
- 
  read(2)は終端に'\0'を想定していない。
  対して、printf()は末尾に'\0'を前提としているので、
  そのまま渡したり、合わせて使うのは間違い。
## ミドルウェアのユーザ
- 
  Apacheなどのミドルウェアに対し、専用のユーザを作成することが多いが、
  セキュリティ対策としてログインシェルを無効化しておくことが多い。
  ログインシェルを無効化するには、そのユーザのログインシェルとして無効なファイルを指定する。
  そうすると、ログインを試みた場合に自動でログアウトされる。
  /bin/falseなどに設定しておく。

## signal
- 
  実行中のプロセスに対し、さまざまなイベントを通知するために送出されるもの。
  SIGTERMやSIGKILLの他にも数十種類存在する。
  "kill -l"で参照可能。
  killコマンドでシグナルの送信が可能。
  また、シグナルを受信して処理するにはtrapコマンドが使える。

- よく使われるシグナル
  |------------------+------+------------+--------------------------------------------------------------------------------------------|
  | デフォルトの名前 | 補足 | 挙動       | 生成原因と用途                                                                             |
  |------------------+------+------------+--------------------------------------------------------------------------------------------|
  | SIGINT           | ○   | 終了       | 割り込み。Ctr+Cで生成され、中止したいときに使う。                                          |
  | SIGHUP           | ○   | 終了       | ユーザがログアウトしたときなどに生成、デーモンでは設定ファイルの読み直しに使う場合が多い。 |
  | SIGPIPE          | ○   | 終了       | 切れたパイプに書き込むと生成される。                                                       |
  | SIGTERM          | ○   | 終了       | プロセスを終了させるときに使う。killのデフォルト値。                                       |
  | SIGKILL          | ×   | 終了       | 確実にプロセスを終了させるために使う                                                       |
  | SIGCHLD          | ○   | 無視       | 子プロセスが停止または終了したときに生成される                                             |
  | SIGSEGV          | ○   | コアダンプ | アクセスが禁止されているメモリ領域にアクセスした。                                         |
  | SIGBUS           | ○   | コアダンプ | アラインメント違反。ポインタ操作を間違えたときに生成される。                               |
  | SIGFPE           | ○   | コアダンプ | 算術演算エラー。ゼロ除算や不動小数点数オーバーフローなど。                                 |
  |------------------+------+------------+--------------------------------------------------------------------------------------------|

## ファイルの種類を判定するマクロ
- 
  |----------+----------------------------------|
  | マクロ名 | 効果                             |
  |----------+----------------------------------|
  | S_ISREG  | 普通のファイルなら非ゼロ         |
  | S_ISDIR  | ディレクトリなら非ゼロ           |
  | S_ISLNK  | シンボリックリンクなら非ゼロ     |
  | S_ISCHR  | キャラクタデバイスなら非ゼロ     |
  | S_ISBLK  | ブロックデバイスなら非ゼロ       |
  | S_ISFIFO | 名前付きパイプ（FIFO）なら非ゼロ |
  | S_ISSOCK | UNIXソケットなら非ゼロ           |
  |----------+----------------------------------|

## パーミッションを表す定数
- 
  |-------------------+-------+--------------------------|
  | 定数              |    値 | 意味                     |
  |-------------------+-------+--------------------------|
  | S_IRUSR, S_IREAD  | 00400 | 所有ユーザから読込可能   |
  | S_IWUSR, S_IWRITE | 00200 | 所有ユーザから書込可能   |
  | S_IXUSR, S_IEXEC  | 00100 | 所有ユーザから実行可能   |
  | S_IRGRP           | 00040 | 所有グループから読込可能 |
  | S_IWGRP           | 00020 | 所有グループから書込可能 |
  | S_IXGRP           | 00010 | 所有グループから実行可能 |
  | S_IROTH           | 00010 | 所有グループから実行可能 |
  | S_IWOTH           | 00010 | 所有グループから実行可能 |
  | S_IXOTH           | 00010 | 所有グループから実行可能 |
  |-------------------+-------+--------------------------|

## リダイレクト
- 
  標準入力が0, 標準出力は1, 標準エラー出力は2。

  標準出力サンプル。以下2つは同じ意味。
    echo Hello 1> hoge.txt
    echo Hello  > hoge.txt

  標準入力サンプル。以下2つも同じ意味。
    read fuga 0< hoge.txt
    read fuga  < hoge.txt

  標準エラー出力を標準出力にマージ
    some_command > hoge.txt 2>&1

## コマンドの終了ステータス
- $?
  "$?"で直前の終了ステータスを取得できる。

- PIPESTATUS[]
  パイプライン内の任意の位置の終了ステータスを拾いたい場合、
  PIPESTATUSという環境変数を利用する。
  配列で、添え字は0始まり。
    ex) echo ${PIPESTATUS[0]}

## 終了ステータス
- 
  0は成功、1はエラーというのは、Linux(UNIX)の決まりごと。
  成功・失敗のどちらかを表現するだけでよければ、
  EXIT_SUCCESSとEXIT_FAILUREというマクロを使うとよい。
  細かくステータスを分けたい場合、直接数値を書くべき。

## 色属性のエスケープシーケンス
- ESC[色属性m
  上記のように書くことで、色属性が変更される。
  ESCはエスケープ文字だが、「\e」か「\033」もしくはESC制御文字(16進で"1b")を入力する。
  属性をリセットしデフォルトにするには、「ESC[0m」もしくは「ESC[m」とする。

- カラーコード
  カラーコード"31"の1文字目"3"は文字色指定を表す。
  また、"4"は背景色指定を表す。
  2文字目がカラーコードとなる。
  
  |------+---------|
  | 数字 | 色      |
  |------+---------|
  |    0 | Black   |
  |    1 | Red     |
  |    2 | Green   |
  |    3 | Yellow  |
  |    4 | Blue    |
  |    5 | Magenta |
  |    6 | Cyan    |
  |    7 | White   |
  |------+---------|

- 付加属性
  
  |----------+----------------+--------|
  | 属性番号 | attributes     | 属性   |
  |----------+----------------+--------|
  |        1 | bold           | 太字   |
  |        2 | low intensity  | 弱強調 |
  |        4 | underline      | 下線   |
  |        5 | blink          | 点滅   |
  |        7 | reverse video  | 反転   |
  |        8 | invisible text | 非表示 |
  |----------+----------------+--------|

- 例
  echo -e "\e[33;41;1mhoge\e[m"

- リンク
  [[http://www.m-bsys.com/linux/echo-color-1][シェル - echo で文字に色をつける その1]]
 
## プロセス置換
- 
  コマンドの出力結果をファイルとして扱う機能。
  <(command)という形で使う。
    ex) diff text.txt <(sed -e 's/hoge/HOGE HOGE/' text.txt)

## アドレス空間の確認
- 
  プロセスIDがｎのメモリ配置を見たければ、
  /proc/n/mapsを確認すればよい。
  
  pはprivateな領域、sはshared（共有）領域を表す。

## zombie
- 
  fork()した後wait()しない場合に残っている状態。
  子が死んでも、親がwaitするときに備えてプロセス管理テーブル内の子エントリを開放せずに残しておくため、
  waitをしないといつまでも子エントリが残り続ける。
  ゾンビはリソースを開放しない上にシグナルは無視される。
  親プロセスがwaitせずに終了してしまった場合、initプロセスが自分の養子として引き受ける。
  psコマンドには"zombie"とか"defunct"と表示される。
  対策としては、1:forkしたらwait, 2:ダブルfork, 3:sigcation()を使う, などがある。

## session
- 
  ユーザのログインからログアウトまでの流れを管理するための概念。
  ログインシェルを基点に、ユーザが同じ端末から起動したプロセスを1つにまとめる働きがある。
  結果プロセスグループをまとめるような形になる。
  最初にセッションを作ったプロセスがセッションリーダーで、
  psコマンド等で確認するとPID(プロセスID)とSID(セッションID)が等しい。
  リーダーは新しいセッションやプロセスを作れない。
  セッションと関連付けられた端末を、プロセスの制御端末(controlling terminal)という。
## ログインセッション
- 
  特定の端末上でセッションを開始したプロセスの子孫のプロセスが全て含まれる。

## process group
- 
  パイプでつなげたプロセス群全てに処理の中断を行ってもらいたい、など、
  ある程度まとまった単位にシグナルを送れるように遅れるようにしたもの。
  最初にプロセスグループを作ったプロセスがプロセスグループリーダーで、
  psコマンド等で確認するとPID(プロセスID)とPGID(プロセスグループID)が等しい。

## daemon
- 
  制御端末を持たないプロセスをdeamon processという。
  "ps ax"などで確認すると、ttyが"?"となっている。
  
## 他のプロセスのカレントディレクトリ
- 
  自プロセス以外のカレントディレクトリは変更できない。
  知るだけなら/proc/プロセスID/cwdで確認可能。

## environment variable
- 重要な環境変数
  |---------+-----------------------------------------------------|
  | 名前    | 意味                                                |
  |---------+-----------------------------------------------------|
  | PATH    | コマンドの存在するディレクトリ                      |
  | TERM    | 使っている端末の種類                                |
  | LANG    | ユーザのデフォルトロケール。                        |
  | LOGNAME | ユーザのログイン名                                  |
  | TEMP    | 一時ファイルを置くディレクトリ。/tmpなど。          |
  | PAGER   | manなどで起動するテキスト閲覧プログラム。lessなど。 |
  | EDITOR  | デフォルトエディタ。viやemacsなど                   |
  | MANPATH | manのソースをおいてあるディレクトリ                 |
  | DISPLAY | X Window Systemのデフォルトディスプレイ             |
  |---------+-----------------------------------------------------|

- environ
  グローバル関数environを介して環境変数にアクセスできる。
  型はchar**で、どのヘッダファイルでも宣言されていないので、
  自分で直接extern宣言をする必要がある。
  environの指す先は移動することがあるので、変数に保存しあとで使う等してはいけない。
  ex) extern char **environ;
## ユーザ時間、システム時間
- システム時間
  そのプロセスのためにカーネルが働いた時間のこと。
- ユーザ時間
  システム時間以外の、プロセスが完全に自分で消費した時間のこと。

## メジャーフォールト、マイナーフォールト
- メジャーフォールト major fal
  
- マイナーフォールト
## UNIX epoch
- 
  Linuxカーネルは時刻を1970年1月1日からの経過秒数で保持している。
  この日時を俗に"UNIXエポック"と呼んでいる。
  1970年なのはUNIXの最初のバージョンがその頃に出来たため。
  Linuxカーネルでは常に協定世界時(UTC : Coordinated Universal Time)で計算している。

## ログイン
- 
  ログインの流れ
  1. initが端末の数だけgettyコマンドを起動(/ect/linittabに設定値)
  2. 端末からのユーザ名入力を待ち、loginコマンドを起動
     gettyは端末をopen()し、read()して、ユーザ名がタイプされるのを待つ。
     端末の細かい設定などが必要なので、gettyという独立プログラムが必要。
     ユーザ名が入力されたら、dup()を使って0, 1, 2番につなぎ、loginをexecする。
  3. loginコマンドがユーザ認証
     ユーザデータベースのある場所等の差異は、/etc/nsswitch.confの設定にある。
     パスワードはPAMがあればそこで吸収、導入されていなければloginコマンドで意識する必要あり。
     伝統的には/etc/login.defsで設定していた。
  4. シェルを起動
     execするときにコマンドの頭に「-」をつけて起動数rと、ログインシェルとなり、動作が少し変わる。
     例）execl("/bin/sh", "-sh", ....);

## PAM
- 
  Pluggable Authentication Module。
  実態は共有ライブラリだが、柔軟に対応できるようダイナミックロードを使ってライブラリを分割している。
  ライブラリは/lib/security。

## sshの秘密鍵接続
- 
  ssh-keygenで、秘密鍵と公開鍵を作成する。
  "~/.ssh/authorized_key"に公開鍵を登録してあげることで、パスワードを入れなくてもssh接続できるようになる。
  パーミッションは600にしておくこと。

## sudo管理者権限
- 
  sudoコマンドは、設定をしていない場合は一般ユーザは使用できない。
  設定ファイルは/etc/sudoersだが、そのままviで編集してはいけない。
  設定ミスが問題になりうるので、ファイルのロックや構文の確認をしてくれるvisudoコマンドを使う。
  [[http://linux.kororo.jp/cont/intro/sudo.php][sudoによる管理者権限の付与]]

## serviceと/etc/init.d/xxxの違い
- /etc/init.d/xxx start
  コマンドを実行したときの環境変数がそのまま引き継がれる。
- service xxx start
  環境変数はPATHとTERMのみ引き継がれる。
## プロセスディスクリプタ
- 
  プロセスの実行を停止する際、カーネルはその時点でのプロセスの内容をディスクリプタの中に退避する。
  レジスタはPCやSP、汎用レジスタ、浮動小数点レジスタ、プロセッサ制御レジスタ、メモリ管理レジスタなど。
  実行再開時に、退避していたプロセスディスクリプタのメンバを使用し、CPUレジスタを復旧する。

## スピンロック
- 
  ロックの一種で、スレッドがロックを獲得できるまで単純にループ（スピン）して定期的にロックをチェックしながら待つ方式。
  セマフォを使用する場合複数の処理が必要となるため、短期間のブロックではスピンロックの使用が効果的である。
  そのため、カーネル内でよく使われる。

## IPC
- 
  IPCはInterprocess Communication。
  System V IPCとして、セマフォ(semaphore)、メッセージキュー(message que)、共有メモリ(shared memory)がある。
  shmget(), semget(), msgget()といったシステムコールを呼び出すことで、カーネルはIPC資源を獲得する。

## プロセスグループ
- 
  ex) ls | sort | more
  上記のようなコマンドラインを実行する場合、bashのようなプロセスグループを扱えるシェルでは、
  3つのプロセス用の新しいグループを生成する。
  シェルは、その3つのプロセスをあたかも1つであるかのように取り扱う。各プロセスディスクリプタにはプロセスグループIDメンバがある。

## ディストリビューションの確認
- 
  /etc配下にディストリビューションやバージョンが書いてあるファイルがあるので、
  それを確認する。
  ex)
  - cat /etc/redhat-release (Redhat)
  - cat /etc/debian_version (Debian)
  - cat /etc/SuSe-release (SuSE)
  - cat /etc/vine-release (Vine)
  
  もしくは、issueに入っているとのこと。
  - cat /etc/issue

  [[http://d.hatena.ne.jp/PRiMENON/20080119/1200750903][インストールしたLinuxディストリビューション名とバージョンを確認するには]]

## スーパーブロック
- 
  論理パーティションを管理するためのメタデータ。
  細かい点は不明。リンク参照。
  
- Link
  [[https://ja.wikipedia.org/wiki/%E3%82%B9%E3%83%BC%E3%83%91%E3%83%BC%E3%83%96%E3%83%AD%E3%83%83%E3%82%AF_(%E3%83%95%E3%82%A1%E3%82%A4%E3%83%AB%E3%82%B7%E3%82%B9%E3%83%86%E3%83%A0)][スーパーブロック（ファイルシステム） - Wikipedia]]
  [[http://open-groove.net/linux/linux-filesystem-superblock/][Linuxファイルシステムにおけるスーパーブロックとは - OpenGroove]]

## IFSの変更
- 
  シェルの区切り文字を指定する、"IFS(Internal Field Separator)"という変数がある。
  スペースと改行がデフォルトで区切り文字となっているが、スペース区切りの行を一つのまとまりとして認識したい場合、
  IFS=$"\n" とすることで改行のみを区切り文字として変更可能。
  （もとのIFSはバックアップを取っておいて、変更後もとに戻すとよい）

- 
  [[http://linux.just4fun.biz/%E9%80%86%E5%BC%95%E3%81%8D%E3%82%B7%E3%82%A7%E3%83%AB%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%97%E3%83%88/%E3%82%B9%E3%83%9A%E3%83%BC%E3%82%B9%E3%81%8C%E5%90%AB%E3%81%BE%E3%82%8C%E3%82%8B%E6%96%87%E5%AD%97%E5%88%97%E3%82%921%E8%A1%8C%E3%81%A8%E3%81%97%E3%81%A6%E6%89%B1%E3%81%86%E6%96%B9%E6%B3%95.html][スペースが含まれる文字列を1行として扱う方法 - 逆引きシェルスクリプト]]

## how to change forgotten root password
### centos
- 
  1. Boot CenTOS and press esc key when seeing the message "Press any key to enter the menu"
  2. Select your operating system and press 'a' to modify kernel argument.
  3. Pet number "1" or character "S" in kernel configuration.
  4. Starting with single mode, command 'pwd' and change password.

- Link
  [[http://lintut.com/reset-forgotten-root-password-in-centos/][Easy way to reset forgotten root password in CentOS 6.5 - LinTut]]

## change kbdmap
- setxkbmap dvorak
  change xkeyboardmap to dvorak.

- loadkeys
  loadkeys dvorak.map
  loadkeys /usr/share/keymaps/i386/dvorak/dvorak.map.gz

- Link
  [[http://www.kaufmann.no/roland/dvorak/linux.html][Installing the Programmer Dvorak Keyboard Layout on Linux]]

## check OS x86 or x86_x64
- 
  type "uname -a"
## extend lvm volumes
- create partition
  fdisk /dev/sda
  (type some commands like p(print), n(add)->p, m(help), t(change system id), w(write table to disk and exit) etc)
  
- reboot
  reboot
  
- create lvm physical volume
  pvcreate /dev/sda3

- check volumegroup
  vgs

- set phsycal volume to volume group
  vgextend VolGroup00 /dev/sda3

- extend logical volume
  lvextend -l +100%Free /dev/VolGroup00/LogVol00

- resize file system
  resize2fs /dev/VolGroup00/LogVol00

- check the size
  df -h

- [[https://users.miraclelinux.com/technet/document/linux/training/2_2_3.html][Linux技術トレーニング 基本管理コースⅡ - MIRACLE]]
- [[http://se-suganuma.blogspot.jp/2009/04/centoslvmvmwarehdd.html][【CentOS】LVMでディスク容量を拡張（VMwareのHDD容量を増やす） - SE奮闘記]]
  
## iptables
- 
  the command to configure the tables,chains and rules provided by Netfilter,
  which is Linux kernel firewall for packet processing.
  Packet Filtering, Network Address Translation modules for IPv4.

  ip6tables for IPv6, arptables to ARP, ebtables to Ethernet frames.
  
- Tables
  choose tagret to filter
  - filter
    control packet accessing, droping.
    - chain : INPUT, OUTPUT, FORWARD
  - nat
    overwrite packet source or destination etc.
    - chain : POSTROUTING, PREROUTING, OUTPUT
  - mangle
    overwiret TOS (Type Of Services) field.
    - chain : POSTROUTING, PREROUTING, INPUT, OUTPUT, FORWARD
  - raw
    Mark special packet not to tracking.
    - chain : PREROUTING, OUTPUT

  - settings
    *filter(nat, mangle, raw)
      #write down settings
    COMMIT

- Chains
  - INPUT
    Packets is going to be locally delivered.
    It does not have anything to do with processes having an opend socket;
  - OUTPUT
    output packet
  - FORWARD
    forwarding packet
  - PREROUTING
    Packets will enter this chain before a routing decision is made
  - POSTROUTING
    Rounting decision has been made. Packets enter this chain just before handing them off to the hardware.

- Targets
  - ACCEPT
    allow packet passing.
  - DROP
    drop packets.
  - RETURN

  - MASQUERADE
    
  - REJECT
    reject packets and not reply.
  - REDIRECT, PREROUTING
    redirect other ports.
  - LOG
    write log.
    
- Rules
  - -p [!] <protocol>
    protocol.
    able to choose one of following : tcp, udp, icmp, all

  - -s [!} <address> [/<netmask>]
    source IP

  - -d [!] <address> [/<netmask>]
    destination IP

  - --sport <port>
    source port
  - --dport <port>
    destination port
  
  - -j <target>
    
  - -i <interface>
    input interface. eth0, eth1, etc.

  - -o <interface>
    output interface.
  
  - -t <table>
    target table

  - -m <module>
    set module.
  
## SELinux
- 
  Security-Enhanced Linux.

- status
  - diabled
  - permissive
    write audit log only
  - enforcing

- command for checking status
  - getenforce
    return Disabled, Permissive or Enforcing
  - setlinuxenabled
    when disabled, return 1. others, return 0.
    check with "echo $?"
  - sestatus
    most detailed.

- command for change status
  - setenforce 0
    set permissive.
  - setenforce 1
    set enforcing

- setting file
  - /etc/selinux/config

  - /etc/sysconfig/selinx
    symbolic link of /etc/selinux/config.
    change above one.

- auditlog
  - /var/log/audit/audit.log
  - ausearch -m avc

### TE - Type Enforcement

### RBAC

### MAC

### Domain

## Unset autolock 
- CentOS
  System->Preferences->Screensaver
  uncheck : Lock screen when screensaver is active

## RHEPL/CentOS Development Tools
- 
  install some Development Tools.
  yum groupinstall 'Development Tools'
  [[http://www.cyberciti.biz/faq/centos-linux-install-gcc-c-c-compiler/#more-1210][RHEL/CentOS Linux Install Core Development Tools Automake, Gcc(C/C++), Perl, Python & debuggers - nixCraft]]

## Check i-node inoformation
- 
  i-nodeがどれだけ使われているかは、"df -i"で調べられる。
  また、特定のファイルやディレクトリのiノード情報は、"stat"コマンドで確認できる。

## Copy directory structure without files
- 
  find . type >dirs.txt
  xargs mkdir -p <dirs.txt
  [[http://stackoverflow.com/questions/4073969/copy-folder-structure-sans-files-from-one-location-to-another][Copy folder structuer (sans files) from one location to another - stackoverflow]]

- 
  find workarea_root -type d -exec echo doing/{} \; | xargs mkdir -p

## Get ShellScript's Location Path
- 
  cd, and then pwd.
  only executing pwd, it shows a current position where command is executed.

  - ex
    echo $(cd $(dirname $0) && pwd)

- Link
  [[http://www.task-notes.com/entry/20150214/1423882800][シェルスクリプトで相対パスと絶対パスを取得する - TASK NOTES]]
## About LVM
### Disk
### Physical Volume
### Volume Group
### Logical Volume
### Mount Point
## lost+found
- 
  running fsck, and it might find data fragments that are 
  [[http://unix.stackexchange.com/questions/18154/what-is-the-purpose-of-the-lostfound-folder-in-linux-and-unix][What is the purpose of the lost+found folder in Linux and Unix? - UNIX & LINUX]]

## /etc/mtab, /proc/mounts
- /etc/mtab
  通常のファイルで、ファイルシステムがマウント・アンマウントされると常にmountプログラムによって更新される。
- /proc/mounts
  proc仮想ファイルシステムの一部。/proc/配下にある他のファイルと同様、mounts"ファイル"はどとディスクドライブにも存在しない。
  実際にはファイルでもなく、ファイル形式で見ることができるシステム状態。
- 
  [[http://web.mit.edu/rhel-doc/4/RH-DOCS/rhel-isa-ja-4/s1-storage-rhlspec.html][5.9. Red Hat Enterprise Linux 固有の情報 - Red Hat Enterprise Linux 4: システム管理入門ガイド 5章. ストレージを管理する]]

## 監視はtail -fでなくless +Fでよい
- 
  less +Fを使うことにより、監視モードと通常モードをlessを起動したまま行き来できるので、
  tailよりも便利、とのこと。
  [[http://www.softantenna.com/wp/unix/stop-using-tail-f/][「tail -f」を使うのは情弱、情強は「less +F」を使う - ソフトアンテナブログ]]

## CPU数、コア数、ハイパースレッディングの調査
- 
  cat /proc/cpuinfo | grep (processor | "physical id" | "cpu cores" | etc.. )
  [[http://tooljp.com/linux/faq/5B503D6E4FD173C549257A570051833A.html][【質問】CPU数、コア数、ハイパースレッディング (Hyper-Threading) を調査する方法 - Redhat Enterprise linux (EL) FAQ]]

## メモリの確認
- 
  cat /proc/meminfo

## spool
- Simultaneous Peripheral Operation On-Line
  もともとはIBM用語。
  転じて、FIFO(キュー)と呼ばれるバッファとして使われている。

## MTA
- Mail Transfer Agent

### sendmail
- 
  MTAの中でもUNIXで古くから使われてきたソフト。
  ほとんどのUNIX系OSにデフォルトでインストールされており、通常/etc/mailに設定ファイルが集められている。
- 
  http://rfs.jp/server/sendmail/sendmail.html
## Linuxサーバ確認オペレーション
- Link
  - [[http://yuuki.hatenablog.com/entry/linux-server-operations][Linuxサーバにログインしたらいつもやっているオペレーション - ゆううきブログ]]
  - [[http://think-t.hatenablog.com/entry/20090218][サーバを調査するときにやること(Linux編) - think-t の晴耕雨読]]
  - [[http://techblog.netflix.com/2015/11/linux-performance-analysis-in-60s.html][Linux Performance Analysis in 60,000 Milliseconds - The Netflix Tech Blog]]

### まず確認すること
#### w
- 他のユーザを確認
#### uptime
- サーバの前回起動してから現在までの稼働している時間の確認。
  ただしwでも同様の情報が出る。
#### ps
- ps auxf
- pstreeでも似たようなことが可能
#### ip
- ip a
#### df
- df Th
### 負荷状況確認
#### top
- top -c, 更に1を押す
- mpstat -P ALLでも見れる
#### iostat
- iostat -dx 5
#### netstat / ss
- netstat -tnl

### ログ調査
#### /var/log/messages or /var/log/syslog
- カーネルやOSの標準的なプロセスログ
#### /var/log/secure
- ssh接続の情報
#### /var/log/cron
- cronが実行されたか否か確認
#### /var/log/nginx, /var/log/httpd, /var/log/mysql
- middlewareログは、/var/log/{middleware}にある場合が多い。
#### /etc
- /etc/{middleware}辺りにログなどの設定ファイルが書いていないか確認する。
#### lsof
- lsof -p <pid>
  <pid>が開いたファイルディスクリプタ情報が見えるので、そこからログファイルなどを探す。
## 他のユーザにメッセージを送る
- write:
  to a perticular user
  - usage 
    write [username]
    messages...
  
- wall:
  to all users logging in
  send a message to everybody's terminal.
  - usage
    wall 

- pts
  echo "message here" > /dev/pts/num
## net-tools, iproute2
### net-tools
#### arp
#### hostname
#### ifconfig
#### ipmaddr
#### iptunnel
#### mil-tool
#### meif
#### netstat
#### plipconfig
#### rarp
#### route
#### slattach
### iproute2
#### ip
#### ss
### Link
- [[http://www.linuxfoundation.org/collaborate/workgroups/networking/net-tools][net-tools THE LINUX FOUNDATION]]
## extundelete (rmしてしまった場合の復元)
- 
  1. 書き込まれないように、readonlyなどにしてマウントし直す。
  2. 時間をとっておく。
  3. extundeleteをインストール、ビルド。ext3, ext4に対応しているらしい。
  4. パーティションと時間（エポック秒）を指定してextundeleteを実行、復元。
  5. 名前が戻せないものは、ディレクトリ直下にfiles.{inode番号}みたいな形で並ぶ。
  
- 
  [[http://d.hatena.ne.jp/y-kawaz/20110123/1295779916][Linuxでうっかりrm -rfしちゃったけど復活出来たよー＼(＾o＾)／  - y-kawazの日記]]
  [[https://tech.aucfan.com/rm-rf-retrieval/][rm -rfでやらかした時すかさず実行する復元コマンド(Linux編) - aucfan Engineer's blog]]
## ANSI escape code
- 
  ターミナル上で文字を強調したりできる。
  CSI(Control Sequence Introducer)と呼ばれるEsc / [を先頭につけた形とし、
  その後に数字を続ける。
  [[http://shiroyasha.io/escape-sequences-a-quick-guide.html][Escape Sequences - A Quick Guide]]
  https://en.wikipedia.org/wiki/ANSI_escape_code
## パイプの入力をシェルコマンドとして実行
- 
  sh、でパイプで受け取った文字列をシェルコマンドとして実行できる。
  ex) echo 'hoge foo var' | sed 's/^/mkdir /' | sh -x
  http://d.hatena.ne.jp/srkzhr/20081216/1229449984
## Manual Sections
### Research Unix, BSD, OS X, Linux)
- 
  |---------+------------------------------------------------------------------|
  | Section | Description                                                      |
  |---------+------------------------------------------------------------------|
  |       1 | General commands                                                 |
  |       2 | System calls                                                     |
  |       3 | Library functions, covering in particular the C standard library |
  |       4 | Special files (usually devices, those found in/dev) and others   |
  |       5 | File formats and conventions                                     |
  |       6 | Games and screensavers                                           |
  |       7 | Miscellanea                                                      |
  |       8 | System administration commands and daemons                       |
  |---------+------------------------------------------------------------------|

## VSS, RSS, PSS, USS
### VSS(VSZ)
- virtual set size
  プロセスがアクセスできるアドレスの総和で、
  mallocして書き込まれていないメモリなど、まだ使用していない領域も含む。
### RSS
- resident set size
  実際に使用しているRAMの層メモリ量。
  プロセスが使用しているものと、共有ライブラリが使用しているものを合計し算出している。
  共有ライブラリはプロセス数と関係なく一度しか読み込まれないため、誤解を招くことがある。

### PSS
- proportional set size
  共有ライブラリを適切なサイズに分割し算出する点でRSSと異なる。
  3つのプロセスが30ページの共有ライブラリを用いている場合、各プロセスのPSSに10ページ分計上される。
  キルした場合に正しい指標でなくなる。

### USS
- unique set size
  プロセスに完全に一意であるようなプライベートなメモリ使用量。

### Link
- [[http://gntm-mdk.hatenadiary.com/entry/2015/01/21/231258][VSS RSS PSS USS の説明 - Meblog]]
## Gentoo Installation Temporary
### Block devices
- /dev/sd*
  SCSI and Serial ATA drives are both labeled /dev/sd*;
  even IDE drives are labeled /dev/sd* with the newer libata framowork in the kernel.
  with old device framework, then the first IDE drive is /dev/hda.

### Partiton tables
- 
  full disk block devices are split up in smaller, more manageable block devices.
  On x86, these are called partitions.
  There are two standard paritioning technologies in use: MBR and GPT

#### MBR
- Master Boot Record
  using 32-bit identifiers for the start sector and length of hte partitons.
  
- Type
  - primary
    it stored information in the master boot record itself.
    master boot record is a very small, usually 512 bytes, location at the very beginning of the disk.
    Due to small spaces, only four primary partitons are supported.
  - extended
    it can contain logical partitons.
  - logical
    it can be contained in a extended partition.
  - all
    each partitons is limited to 2 TB in size.
    MBR setup does not provide any backup-MBR.

#### GPT
- GUID Partition Table
  using 64-bit identifiers for the partitions.
  the size of a partition is bounded by almost 8ZB.
  
  When a system's software interface between os and farmware is UEFI (Instead of BIOS), GPT is almost mandatory.
  having a backup GPT at the end of the disk. carring CRC32 checksums to detect errors.
   
## network接続ができない場合
- (RHEL, CENTOS)
  vmwareなどにosを入れてyum update、など打った際に、ネットワークにつながっておらずDNSエラーが起こる場合がある。
  /etc/sysconfig/network-scripts/ifcfg-...などのONBOOT項目が"no"になっている場合、起動されていないので、
  "yes"とし再起動をかける。
  [[http://oki2a24.com/2015/05/27/resolve-dns-error-of-centos-6-in-virtualbox/][【CentOS 6】yum が DNS 名前解決できないエラーで使えない問題を解決【OSインストール後】 - oki2a24]]
## フルパスでls -R
- 
  再帰的でなければ、なければls -dでOK。
  -dと-Rが併用できないため、サブディレクトリを含めたい場合はfindと組み合わせる。
  例) ls -l $(find . -type f)
  [[http://orebibou.com/2014/10/ls%E3%82%B3%E3%83%9E%E3%83%B3%E3%83%89%E3%81%A7%E3%83%95%E3%83%AB%E3%83%91%E3%82%B9%E8%A1%A8%E7%A4%BA%E3%82%92%E3%81%99%E3%82%8B%E6%96%B9%E6%B3%95/][lsコマンドでフルパス表示をする方法 - 俺的備忘録 〜なんかいろいろ〜]]
## ターミナルの文字コード変更
- 
  [端末]->[文字コードの設定]->[日本語(UTF-8)]など。
## watchdog
- 
  ウォッチドッグ、ウォッチドッグタイマーとは、システムが正常に動作しているかどうかを監視するためのデバイスの総称。
  システム上で動作しているそれぞれのアプリケーションに定期的に信号を遅らせていて、
  一定周期を経過してウォッチドッグに信号を送らなかったアプリケーションがあればハングアップなど異常事態にあると判断しCPUに割り込みをかける。

- Linux daemon
  [[http://linux.die.net/man/8/watchdog][watchdog(8) - Linux man page]]
  
## cron設定
### crondの確認、起動
- 確認
  /etc/init.d/crond status
- 起動
  /etc/init.d/crond start
### cronの設定ファイル
- 設定ファイル
  - /var/spool/cron/user : ユーザの自動タスク設定ファイル
  - /etc/crontab : 自動タスクのメイン設定ファイル。以下のフォルダ配下を実行するための設定も入っている。
  - /etc/cron.hourly : 毎時実行される自動タスクを配置するディレクトリ
  - /etc/cron.daily : 毎日実行される自動タスクを配置するディレクトリ
  - /etc/cron.monthly : 毎月実行される自動タスクを配置するディレクトリ
  - /etc/cron.weekly : 毎週実行される自動タスクを配置するディレクトリ
  - /etc/cron.cron.d : 上記以外の自動タスクを配置するディレクトリ
  - /etc/cron.deny : 利用を拒否するユーザ名を設定
  - /etc/cron.allow : 利用を許可するユーザ名を設定
### crontabコマンド
- オプション
  - -e : ファイルを対話的に編集する
  - -l : ファイルの内容を表示する
  - -r : ファイルを削除する
  - -u user : userで指定したユーザのcrontabファイルを走査の対象とする。rootのみが利用可能。
### crontabファイルの設定
- フォーマット
  - /var/spool/cron/user
    分 時 日 月 曜日 コマンド
  - /etc/crontab他
    分 時 日 月 曜日 ユーザ コマンド
- 設定範囲
  |----------+-------------------------------|
  | 分       | 0~59                          |
  | 時       | 0~23                          |
  | 日       | 1~31                          |
  | 月       | 1~12 or jan~dec               |
  | 曜日     | 0~7(0,7は共に日曜) or sun~sat |
  | コマンド | コマンドを記述                |
  |----------+-------------------------------|
- 設定方法
  |--------+------------+--------------------------------------------------------------|
  | リスト | 0,15,30,45 | 分の場合、15分ごとに処理を実行する                           |
  | 範囲   | 1-5        | 曜日の場合、月-金に処理を行う                                |
  | 共存   | 1,3,7-9    | 時間の場合、1,3,7,8,9時に処理を行う                          |
  | 間隔値 | 1-5/2      | 時間の場合、1,3,5に処理を行う。/の後の時間間隔で処理をする。 |
  |--------+------------+--------------------------------------------------------------|
### Link
- [[https://www.express.nec.co.jp/linux/distributions/knowledge/system/crond.html][cronの設定ガイド]]
## 配列
- http://shellscript.sunone.me/array.html
- set
  - array=("v1" "v2" "v3")
  - array[1]=3
- add
  - array+=(1)
  - array+=("a" "b" "c")
- refer
  - ${array[ind_num]} # select ind_num value
  - ${array[@]} # select all values
- length
  - ${#array[*]}
  - ${#array[@]}

## 指定行を取得する
- cat text.txt | head -終了行 | tail -`expr 終了行 - 開始行 + 1`
- sed -n '開始行,終了行p' ファイル名
- [[http://linux.just4fun.biz/%E9%80%86%E5%BC%95%E3%81%8DUNIX%E3%82%B3%E3%83%9E%E3%83%B3%E3%83%89/%E6%8C%87%E5%AE%9A%E3%81%97%E3%81%9F%E7%AF%84%E5%9B%B2%E3%81%AE%E8%A1%8C%E3%82%92%E5%8F%96%E5%BE%97%E3%81%99%E3%82%8B%E6%96%B9%E6%B3%95.html][指定した範囲の行を取得する方法 - 逆引きUNIXコマンド]]
## バイナリの閲覧・編集
- 閲覧
  - hexdump -C file
  - od file
- 編集
  - vi -b file
    - :%!xxd 
    - :%!xxd -r
  - dd
## [と[[
- "["はtestコマンド
- "[["はシェルのキーワード
- http://detail.chiebukuro.yahoo.co.jp/qa/question_detail/q1389236638
## -develとついたパッケージ
- 開発用のパッケージ。
## シェルで2進数、8進数、10進数、16進数変換
- bcコマンドを使う。
  obaseとibaseを設定することで計算可能。
  http://www.mazn.net/blog/2013/02/24/854.html
## mkdirしつつcd
- $_
  mkdir -p xxx/yyy; cd $_
  - $_は最後に実行したコマンドの最後の引数となるので、それを利用。

- cd !!$
  !!は一つ前に実行したコマンドラインをサイド引用して実行。直後に$をつけることで最後の引数のみを取り出す。

- cd !$
  $の前にイベント指示詞が省略された場合は、直前に実行されたコマンドラインを参照することになる。
  本来!と$の間にはイベント指示子が必要だが、上記により省略した形でも実行可能。

- https://dev.classmethod.jp/etc/make-and-cd-patterns/
