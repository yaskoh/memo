# Vagrant
## command line interface
### box
#### add [box-name] [box-url]
- Boxを追加する

#### list
- Boxが追加されたことを確認する

#### outdated
#### remove [box-name]
- いらなくなったBoxの削除を行う

#### package
#### update
### connect
### distroy
- 
  仮想マシンを廃棄する

### global-status
### halt
- 
  仮想マシンをシャットダウンする

### init
- 
  仮想マシンの定義ファイルを作成する
  vagrant init [box-name] [box-url]

### login
### package
- 
  作業中のマシンをBox化する

### plugin

- list
  インストール済みのプラグイン確認
- install [name]

#### sahara

- sandbox
  - on
  - off
  - rollback

### port
### powershell
### provision
- 
  プロビジョニングを行う。

### rdp
### reload
- vagrant reload [vm-name]
- restarts vagrant machine, loads new Vagrantfile configration
- 仮想マシンを再起動する

#### --[no-]provision
- Enable ordisable provisioning
#### --provision-with-x,y,z
- Enable only certain provisioners, by type or by name.
### resume
- 
  一時停止(suspend)からの復帰

### share
### snapshot
### ssh
- 仮想マシンにssh接続する

#### Options
##### -F configfile
##### -i identity-file
### ssh-config
- 仮想マシンのSSH情報を確認する

### status
- 
  仮想マシンの状態を確認する

### suspend
- 
  仮想マシンを一時中断する

### up
- 
  仮想マシンを起動する

### version
- 
  show the version of Vagrant installed on my computer.
## vagrantfile
## boxes
- ~/.vagrant.d/boxes
## provisioning  
## networking
### 種類
- プライベートネットワーク
  ホストOSとゲストOS間でのみ通信が行える。
  特に設定しなければ、「ホストオンリーアダプタ」での接続になる。
  virtualbox_intnetによってゲストOS間の通信が行えるようにする。

- ポートフォワーディング
  ホストOSへの特定のポートを使った接続をゲストOSに転送する。
  これにより実質的にゲストOSへ

- パブリックネットワーク
  同一ネットワーク内のどの端末からでもゲストOSとの通信が行える。
  ブリッジアダプタに相当するもの。
  ホストOSと同じネットワーク上にあたかも独立しているように存在し、外部機器と通信が行える。

#### Link
- [[http://labs.septeni.co.jp/?p=966][Vagrantのネットワーク周りのあれこれ - SepteniEngineerBlog]]
- [[https://docs.vagrantup.com/v2/networking/index.html][NETWORKING - VAGRANTDOCS]]  

### 種類(VirtualBox)

- 未割り当て
- NAT
- NATネットワーク
- ブリッジアダプタ
- 内部ネットワーク
- ホストオンリーアダプタ
- 汎用アダプタ
## setting
### environment variables
#### VAGRANT_HOME
- vagrantのホームディレクトリ。
  ~/.vagrant.d
### node
- 
  一台でなく、複数ノードを設定できる。
  config.vm.define :nodeN do |node|
    node.vm.box = "centos6"
    ...
  end
  
## Plug-ins
### vbguest
#### Options
##### --status
## Memo
### VagrantのBox追加
- 
  vagrant box add {title} {url}
  vagrant init {title} ( <- not necesarry?)
  vagrant up

- Vagrantbox.es
  [[http://www.vagrantbox.es/][Vagrantbox.es]]
  
### Vagrantの紐付
- 
  .vagrant以下の場所にあるUUIDで紐付けている。
  <<.vagrant/machines/default/virtualbox/id>>

  仮想マシンのUUIDを知るには、以下のコマンドをたたく。
  VBoxManage.exe list vms

### Vagrantが起動しない場合
- 
  vagrant upが失敗していた場合、何が原因か調べるためにもGUIで起動する。
  今回は以下をVagrantfileへ追加（コメントを外せばよい）。
  - config.vm.provider "virtualbox" do |vb|
      vb.gui = true
    end

### ファイルを共有
#### 共有フォルダ設定
- Vagrantfileの設定値を変更する
  config.vm.synced_folder 

##### old
- Vagrantfileが設置されているフォルダ、
  および/vagrantが共有フォルダとして使用できる。

#### scp等による転送
- 1. 設定ファイルの下記だし
  vagrant ssh.config > ssh.config
- 2. 設定ファイルを利用してファイルを転送
  scp -F ssh.config hello.txt vagrant@default:~/
- https://qiita.com/sxo/items/2a2ce57a84b90100a20d
### Vagrantとホストの時刻同期
- 1.UTCの対処
  - sudo rm /etc/localtime
  - sudo ln -s /usr/share/zoneinfo/Asia/Tokyo /etc/localtime
- 2.時刻同期
  - config.vm.provider :virtualbox do |vb|
      vb.customize ["setextradata", :id, "VBoxInternal/Devices/VMMDev/0/Config/GetHostTimeDisabled",0]
    end
- https://polidog.jp/2014/01/08/vagrant/
### Error
#### command-line line 0: garbage at end of line
- spaceがあるパスの場合にエラー。macにて発生。
  v1.98のバグとのことで、2.01に更新して解決。
#### Vagrant was unable to mount VirtualBox shared folders
- VirtualBoxとGuest Additionsでバージョン不一致がある場合などに失敗する模様。
  vagrant-vbguestというプラグインが便利。
  https://qiita.com/ozawan/items/9751dcfd9bd4c470cd82
## Link
- [[https://www.vagrantup.com/docs/][VAGRANT DOCUMENTATION]]
- [[https://atlas.hashicorp.com/boxes/search][Vagrant Boxes - Atlas]]
