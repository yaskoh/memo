# Mainframe
## Command
### Function
- 
  設定で変更できるらしい。

- F2
  選択位置で画面分割

- F3
  - 画面から抜ける。編集は保存される。

- F5
  次の検索結果を見る

- F7, F8, F10, F11
  上、下、左、右へ画面上移動。

- Alt-F2
  表示の日本語-英語変換？

### コマンド
#### Cmd
- =1
  先頭に戻る。

- HEX
  16進数表示する。

- COLS
  行番号表示をする。

- SAVE
  保存する

- CAN
  保存しない

- SUB
  実行。

- PRE
  表示したいもの（その時はジョブ）を見れる。

#### Select
- B
  Browse、ファイルの中身の確認

- S
  Select、ファイルの選択

- C
  Cancel、取り消す

- P
  ログも消して抜ける。Cancelは残す。

#### Console?
- LOGOFF or @
  ログオフする。

#### EditSelect
- C
  置換。C ### $$$ ALLで、###を$$$に変換する。

- F 文字列
  検索

- L 数字
  Location。飛ぶ。

- D
  Delete。行削除

- M
  Move。行移動。

- R
  行を直下にコピー。

- C
  行をコピー。

#### EditCmd
- COPY 名前
  コピーする。

- RLSE
  リリース。確保した領域で、使わないものを解放する。

- BROWSE
## Hercules
### 概要
- 
  メインフレーム・エミュレータ。
  IBMのアーキテクチャをLinux/Windows上で動かすためのエミュレーションソフト。

- 
  フリーのMVS3.8と3270エミュレータがセットとなった学習用システムが以下にあったので、
  それを利用して動かすことができる。
  [[http://www.arteceed.net/?p=131][Windowsでメインフレーム(MVS)を動かす - 「メインフレーム・コンピュータ」で遊ぼう]]

- 
  GUIインターフェースも利用できるとこのこと。
  [[http://www.arteceed.net/?p=1679][HerculesのGUIインターフェース - 「メインフレーム・コンピュータ」で遊ぼう]]

### 操作手順
#### Herculesの起動/TSO端末の接続
1. 「Herculesシステムコンソール.lnk」を実行する。
   システムコンソールに使用するコマンドプロンプトへのショートカット。
2. "STARTMVS"と入力し、Herculesを起動する。
   実態は同フォルダ内にあるバッチで、herculesを起動するコマンドが入っている。
3. 仮想H/Wの電源がONになった状態。
   PageUp/Downキーでスクロール可能。
   ESCキーで状況表示モードに切り替えられる。再度押すことで戻る。
4. MVSコンソールとVTAM端末接続のため、3270エミュレータを起動する。
   上記同梱のwc3270であれば、MVSコンソール用が「MVSR38マスターコンソール.lnk」、
   VTAM端末用が「MVSR38VTAMターミナル.lnk」。
5. wc3270のキー割り付け設定は以下。
   |-----------+-------------|
   | PC        | 3270        |
   |-----------+-------------|
   | Ctrl+R    | Reset       |
   | Ctrl+C    | Clear       |
   | Ctrl+A    | Attn        |
   | PageUp    | PA1         |
   | PageDown  | PA2         |
   | End       | EraseEOF    |
   | Tab       | タブ        |
   | Shift+Tab | 逆タブ      |
   | Enter     | 改行        |
   | 右Ctrl    | 実行(Enter) |
   |-----------+-------------|

#### MVSの開始(IPL)
1. MVSコンソールが接続済みの状態で、Herculesシステムコンソール上"IPL 140"と入力する。
   IPLの引数にIPL装置のアドレスを取っている。
   構成ではアドレス140に3350Disk装置(ボリューム名MVSRES)が設置されている。
2. IPL開始後、CPU待ち状態でNIPが開始される。
   MVSコンソールがパラメータ入力待ちとなる。
3. MVSコンソールで、実行キーのみを押せばよい。
   例外の代表例として以下がある。
   - R 00, SYSP=10
     初期設定するパラメータにIEASYS10も使用する。
   - R 00, CMD=01
     IEASYS00のCMDパラメータを変更する。
   - R 00, CLPA
     CLPAはCreate LPA(Link Pack Area)という意味。
     ロードされるモジュールを修正した場合は必ずCLPAを指定したIPAを行う必要がある。
4. 下記設定を行う。PF11に同様のコマンドを設定してある。
   1. コンソールのスクロールモードを変更する。
      K Sと入力すると、メッセージ・スクロールモードが表示される。
      以下のように修正。
      ・K S,DEL=Y,SEG=09,CON=Y,RNUM=19,RTME=046
      ⇒K S,DEL=RD,SEG=19,CON=Y,RNUM=19,RTME=001
   2. 実行結果表示域をクリアーする。
      K A,NONEと入力。
5. 起動オプションを答える。
   COLDスタートの場合、CKPTとスプールがクリアされる。以下。
   - R 00,COLD,NOREQ
   WARMスタートの場合、CKPTとスプールを前回終了時の続きから利用する。
   PF12にも同様のコマンドが設定されている。
   - R 00,WARM,NOREQ
6. 上記でJES2の初期設定が完了。
7. VTAMを開始する。
   "S NET"と入力し、VTAMの初期設定処理を完了する。
8. TSOを開始する。
   "S TSO"と入力する。TSOの初期設定処理が完了する。

#### TSOへのログイン・ログオフ、RPF
1. VTAMコンソールで、"LOGON TSOUSER"と入力する。
   TSOUSERがテスト用ユーザとして用意されている。"LOGON"を除いても可。
2. "RPF"と入力して、ISPFと似た機能を持つ対話ツールを起動する。
3. RPFを終了させるには、PF03キーを押下するか、XをOptionフィールドに入力する。
4. TSOからログオフするには、"LOGOFF"と入力。
#### MVSの停止、Herculesの終了
1. MVSコンソールでTSOを停止する。
   "P TSO"と入力する。
2. リプライメッセージが出力されたら、Uを応答する。"R nn,U"という形。
   リプライ番号が01であれば、"R 01,U"とするか、
   JES2起動中であればRを省略できるので"1,U"と入力しても可。
3. VTAMを停止する。
   "Z NET,QUICK"と入力する。VTAMが終了する。
4. JES2を終了する。
   "$PJES2"と入力する。JES2が終了する。
5. 実際の運用システムでは、JES2停止後に"Z EOD"コマンドで
   メモリー上の統計応報を最終的にSMFデータセットに書き込む。
   またハード障害情報をSYS1.LOGRECデータセットに書き出し、
   3990装置のキャッシュ・データをDASDにコピーする等の処理を行う。
6. Herculesを停止する。
   Herculesコンソールで、"STOP"コマンドを入力する。
7. "QUIT"コマンドで、仮想H/W装置の電源OFFを行う。

## Memo
### IBM
#### History
- シリーズ/マシン
  - System/360
  - System/370
  - System z

- アーキテクチャ
  - S/360
  - S/370
  - z/Architecture

- OS
  - MVS系
    - OS/360
    - OS/VS
    - MVS
    - OS/390
    - z/OS

## Glossary
### ISPF
- 
  Interactive System Productivity Facility
  IBMメインフレームOS環境のツールセットの一つ。
  スクリーンエディタを含むユーザインターフェース。

### LPA
- 
  Link Pack Area。
  OSの中核以外のシステム常駐モジュールが配置される仮想記憶内の領域の1つ。

### NIP
- 
  Nucleus Initalization Program。エルパ。
  OSの中核部分を初期設定するためのプログラム。

### PSW
- 
  Program Status Word
  CPUの各種状態を表すフラグビットや、次に実行すべき命令の仮想記憶アドレスを持つ、特殊なレジスタ。
  
### SNA
- 
  Systems Network Architecture
  IBMが1974年に作ったコンピュータネットワーク・アーキテクチャ。
  更にはそれに基づいたプロトコルスタック。

### TSO
- 
  Time Sharing Option。
  MVSやOS/390,z/OSのようなIBMメインフレームのOSで使われる、
  相互対話式のコマンドラインインタープリタ。
  単独で使われる場合は稀で、通常ISPFを通して用いられる。合わせてTSO/ISPFと称する。

### VTAM
- 
  Virtual Telecommunications Access Method。
  メインフレームで使用されるIBMの通信ソフトウェア。
  SNAの実装。

### VSAM
- Virtual Storage Access Method
- メインフレームなどのOSで用いられる、外部記憶装置のファイル編成法の一つ。
## Link
- [[http://www.arteceed.net/][「メインフレーム・コンピュータ」で遊ぼう]]
- [[http://www.arteceed.net/?cat=12]['S/370アセンブラー講座' Category - 「メインフレーム・コンピュータ」で遊ぼう]]
