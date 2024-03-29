# Ansible
## Documentation
- http://docs.ansible.com/ansible/latest/index.html
### Introduction
#### Installation
##### Basics/What Will Be Installed
##### What Version to Pick?
- Release cycles : Usually 4 months long.
- Installation
  - recommend to use OS package manager
  - pip, python package manager
  - source also sharing
##### Control Machine Requirements
- any machine with Python 2 or Pyton 3.
  Windows isn't supported for the control machine.
##### Managed Node Requirements
- you need a way to communicate, which is normally ssh.
  By default this uses sftp, and if that's not available, you can switch to scp in ansible.cfg.
##### Installing the Control Machine
###### Yum
###### Apt(Ubntu)
###### Apt(Debian)
###### Portage(Getnoo)
###### pkg(FreeBSD)
###### OSX
###### OpenCSW(Solaris)
###### Pacman(Arch Linux)
###### pip
###### Tarballs of Tagged release
###### Running From Source
##### Ansible on GitHub
#### Getting Started
##### Foreword
##### Remonte Connection Information
- 
  - Control Persist, Kerberos, .ssh/config Options (such as Jump Host setup).
  - Using above, fedore's openssh is too old.
    wishing to use features like Kerberized SSH and more, using Fedora, OS X, or Ubuntu as control machine.
- default: paramiko
  Native SSH had to be explicitly selected with the -c ssh option or set in the configuration file.
##### Your first commands
##### Host Key Checking
- Ansible 1.2.1 and later have host key checking enabled by default.
- host key cheking in paramiko mode is reasonably slow.
#### Inventory
- default inventory : /etc/ansible/hosts
- specify : -i <path>

- you can use multiple inventory files at the same time,
  pull inventory from dynamic or cloud sources or different formats. (Dynamic Inventory)
##### Hosts and Groups
- the format for "/etc/ansible/hosts" will be an INI_like
#### Dynamic Inventory
#### Patterns
#### Introduction To Ad-Hoc Commands
#### Configuration file
- configuration file reading order:
  - ANSIBLE_CONFIG (an env var)
  - ansible.cfg (in the current directory)
  - .ansible.cfg (in the home directory)
  - /etc/ansible/ansible.cfg
##### Getting the latest configuration
- installing from pip or source, you may want to create config file.
  get from here: https://raw.githubusercontent.com/ansible/ansible/devel/examples/ansible.cfg
##### Environmental configuration
- Environmental vars are defined in constants.py.
##### Explanation of values by section
###### General defaults
####### ask_pass
- controling whether an Ansible playbook should prompt for a password by default.
####### ask_sudo_pass
- Ansible playbook should prompt for a sudo password
- depriceted? use --ask-become-pass.
####### ask_vault_pass
###### Privilege Escalation Settings
####### become_ask_pass
- Ask for privilege escalation password, default is False.
###### Paramiko Specific Settings
###### OpenSSH Specific Settings
###### Accelerated Mode Settings
###### Selinux Specific Settings
###### Galaxy Settings
#### BSD Support
#### Windows Support
##### Windows: How Does It Work
- asnible start to support for managing win machine form v1.7, using native PowerShell.
- still be run from a Linux control machine, and uses the "winrm" Python module to talk to remote ohsts.
  Win Subsystem for Linux bash also can be a control machine, though not supported.
  
##### Installing on the Control Machine
##### Using a Windows control machine
##### Authentication Options
###### Certificate
###### Kerberos
###### CredSSP
###### Credential Delegation
##### Inventory
##### Windows System Prop
##### Getting to PowerShell 3.0 or higher
#### Networking Support
### Quickstart Video
### Playbooks
#### Intro to Playbooks
#### Creating Resuable Playbooks
##### old
###### Playbook Roles and Include Statements
#### Variables
#### Templating (Jinga2)
##### old
###### Jinja2 filters
###### Jinja2 tests
#### Conditionals
#### Loops
#### Blocks
#### Strategies
#### Best Practices
### Playbooks:Special Topics
#### Become
#### Accelerated Mode
- Later 1.5, you might nott need this.
#### Asynchronous Actions and Polling
#### Check Mode
#### Playbook Debugger
#### Delegation, Rolling Updates, and Local Actions
#### Setting the Environment
#### Error Handling In Playbooks
#### Advanced Syntax
#### USing Lookups
#### Prompts
#### Tag
#### Vault
#### Start and Stop
#### Directives Glossary
### About Modules
#### Introduction
#### Core Modules
#### Extra Modules
#### Common Return Values
#### Internal use
### Module Index
#### All Modules
#### System Modules
##### ping
- Try to connect to host, verify a usable python and return pong on success
#### Windows Modules
### Ansible Vault
### Command Line Tools
#### ansible
##### Synopsis
- ansible <host-pattern> [options]
##### Common Options
###### -a <MODULE_ARGS>, --args <MODULE_ARGS>
###### -b, --become
- run operations with become (does not imply password prompting)
###### -e, --extra-vars
- set additional variables as key=value or YAML/JSON, if filename prepend with @
###### -k, --ask-pass
- ask for connection password
###### -K, --ask-become-pass
- ask for privilege escalation password
###### -m <MODULE_NAME>, --module-name <MODULE_NAME>
###### -s, --sudo
###### -u <REMOTE_USER>, --user <REMOTE_USER>
###### -U <SUDO_USER>, --sudo-user <SUDO_USER>
###### -v, --verbose
###### --become-user <BECOME_USER>
###### deprecated
####### --ask-su-pass
- use "become"
####### --ask-sudo-pass
- use "become"
##### Environment
##### Files
#### ansible-playbook
##### Synopsis
- ansible-playbook [options] playbook.yml [playbook2 ...]
#### ansible-vault
#### ansible-galaxy
#### ansible-console
#### ansible-console
#### ansible-config
#### ansible-doc
##### Synopsis
- ansible-doc [-l|-s] [options] [-t <plugin type] [plugin]
##### Common Options
#### ansible-inventory
#### ansible-pull
### Detailed Guides
#### Amazon Web Services Guide
#### Azure
#### Rackspace
#### Google Cloud Platform
#### (ry
### Developer Information
#### Ansible Architecture
#### Developing Modules
#### Developing Plugins
#### Developing Dynamic Inventory Sources
#### Pyhton API
#### Developing the Ansible Core Engine
#### Helping Tseting PRs
#### Releases
### Ansible Tower
### Ansible Galaxy
### Testing Strategies
### Configuration
#### Common Options
##### HOST_KEY_CHECKING
- Description:
  Set this to "False" if you want to avoid host key checking by the underlying tools Ansible uses to connect to the host.
- Enviroment:
  ANSIBLE_HOST_KEY_CHECKING
#### Environment Variables
##### ANSIBLE_CONFIG
##### ANSIBLE_HOST_KEY_CHECKING
- Ste this to "False" if you want to avoid host key checking by the underlying tools Ansible uses to connect to the host
### Glossary
### YAML Syntax
## Commands
### ansible
- Syntax: ansible <host-pattern> [-m module_name] [-a args] [option]
  run a task on a target host(s)

#### Option
##### -m MODULE_NAME, --module-name=MODULE_NAME
- module name to execute (default=command)

##### -a MODULE_ARGS, --args=MODULE_ARGS
- module argument

##### -S, --su
- run operations with su

##### -s, --sudo
- run operations with sudo

##### -u REMOTE_USER, --user=REMOTE_USER
- connect as this user (default=current-user like vagrant)

### ansible-playbook
- run an ansible playbook
#### option
- -i PATH, --inventory=PATH
  The PATH to the inventory, which default to /etc/ansible/hosts.

- -C, --check
  don't make any changes; instead, try to predict some of the cahnges that may occur
  dry run

- --list-tasks
  list all tasks that would be executed
  taskコマンドの確認

- --list-hosts
  対処サーバの確認

- --syntax-check
  perform a syntaxcheck on the playbook, but do not execute it
  書式確認

#### playbook
- hosts
  対称のホストまたはグループを指定する。glob[*]も使用可能。
  カンマ区切りもYAMLのリスト指定もOK。

- sudo
  sudoを使って実行する。
  デフォルトではrootとしての実行だが、別途sudo_userを指定することで別のユーザとしても実行可能。

- tasks
  実行する処理を定義する。
  nameは必須でない。
  モジュール名に続きオプションをとる。

### ansible-doc
- 
  Ansible Moduleのドキュメントが読めるコマンド。
  ex) ansible-doc ping

- -l
  moduleをリスト表示する。

### ansible-pull

### ansible-galaxy

### ansible-vault
- 
  暗号化されたYAMLファイルを作る。
## Installation
- Linux : Recommend to use OS package manager
- Others : Reccomend installing via "pip", which is the Python package manager
### Yum (CentOS,RHEL,)
- yum install -y epel-release
- sudo yum install ansible --enablerepo=epel
### Apt (Ubuntu,)
- sudo apt-get install software-properties-common
- sudo apt-addrepository ppa:ansible/ansible
- sudo apt-get update
- sudo apt-get install ansible
### Pip (Linux,MacOS,)
- sudo easy_install pip
- sudo pip install ansible
## Modules
- Ansibleで実行できる機能。
  ansible-doc -lで一覧を取得できる。
  たくさんあるので(ansible-doc -l | wc -lの結果は242)、無理して覚えない。

### Cloud Modules

### Commands Modules

#### command

#### raw

#### script

#### shell
### Database Modules
#### Misc
#### Mysql
#### Postgresql

### Files Modules
#### file
- Sets attributes of files, symlinks, and directories, or removes.
##### Options
###### attributes
###### group
###### mode
###### owner
###### path
###### state
- choices
  - file
  - link
  - directory
  - hard
  - touch
  - absent
### Inventory Modules

#### add_host

#### group_by

### Messaging Modules

### Network Modules

### Notification Modules

### Packaging Modules

#### Language

##### composer
##### cpanm
##### easy_install
##### gem
##### npm
##### pip

#### Os

##### apt
##### apt_key
##### apt_repository
##### apt_rpm
##### homebrew
##### homebrew_cask
##### homebrew_tap
##### layman
##### macports
##### opnbsd_pkg
##### opkg
##### pacman
##### pkgin
##### pkgng
##### pkgutil
##### portage
##### portinstall
##### redhat_subscription
##### nhn_channel
##### rhn_register
##### rpm_key
##### svr4pkg
##### swdepot
##### urpmi
##### yum
##### zypper
##### zypper_repository

### Source Control Modules

#### bzr

#### git

#### github_hooks

#### hg

#### subversion

### System Modules

#### alternatives
#### at
#### authorized_key
#### capabilities
#### cron
#### crypttab
#### debconf
#### facter
#### filesystem
#### firewalld
#### getent
#### glusterfs
#### group
#### hostname
#### kernel_blacklist
#### locale_gen
#### Ivg
#### Ivol
#### modprobe
#### mount
#### ohai
#### open_iscsi
#### ping
#### seboolean
#### selinux
#### service
#### setup
#### sysctl
#### ufw
#### user
#### zfs

### Utilities Modules

### Web Infrastructure Modules

#### apache2_module

#### django_manage

#### ejabberd_user

#### htpasswd

#### jboss

#### jira

#### supervisorctl
### Windows Modules
- http://docs.ansible.com/ansible/latest/list_of_windows_modules.html
#### win_chocolately
#### win_copy
#### win_dsc
#### win_feature
- Installs and uninstalls Windows Features on Windows Server
#### win_package
#### win_path
#### win_reboot
#### win_regedit
#### win_robocopy
#### win_unzip
## Files
### Inventory file
- ansibleはインベントリファイルに書かれたホストにしかアクセスしない。
  -i でインベントリファイルを指定して実行する。
  デフォルトでは"/etc/ansible/hosts"を読む。

  対称は複数でもよく、またクラウドからとってくることもできる。

  フォーマットはINIフォーマットで書かれる。

#### group
- 
  ブラケット[]内にグループ名を記述する。複数グループを指定可能。
  SSH標準以外のポートを指定するには、ホストネームの後コロン:を置いた後ろに
  ポート番号を指定できる。
  ex) [webservers]
      badwolf.example.com:5309

#### alias
- 
  静的IPを使ってエイリアスを付ける場合、以下のようにすることが可能。
  ex) jumper ansible_ssh_port=5555 ansible_ssh_host=192.168.1.50

#### 複数指定
- 
  複数をまとめて指定可能。
  ex) www[01:50].example.com
      db-[a:f].example.com

#### connection
   コネクションタイプを以下のように指定可能。
   ex) localhost          ansible_connection=local
       other.example.com  ansible_connection=ssh    ansible_ssh_user=mpdehaan

#### Groups of Groups, Group Variables
- 
  グループのグループや、それぞれに対しグループに対して変数を設定可能。
  ex) [atlanta]
      host1
      host2
      
      [raleigh]
      host2
      host3
      
      [southeast:children]
      atlanta
      raleigh]
      
      [southeast:vars]
      soe_server=foo.southeast.example.com
      halon_system_timeout=30
      self_destruct_countdown=60
      escape_pods=2
      
      [usa:children]
      southeast
      northeast
      southwest
      northwest

#### Splitting Out
- 
  hostとgroupについては、別ファイルにして指定のフォルダに格納することで読み込むことができる。
  ex) /etc/ansible/group_vars/raleigh
      /etc/ansible/group_vars/webservers
      /etc/ansible/host_vars/foosball
  
  更に、各グループやホスト名のディレクトリを作成して、配下にファイルを配備しても読み込んでくれる。
  ex) /etc/ansible/group_vars/raleigh/db_settrings
      /etc/ansible/group_vars/raleigh/cluster_settings

#### Behavioral Inventory Parameters
- ansible_ssh_host
  The name of the host to connect to, if different from the alias you wish to give to it.

- ansible_ssh_port
  The ssh port number, if not 22

- ansible_ssh_user
  The default ssh user name to use.

- ansible_ssh_pass
  The ssh password to use (this is insecure, we strongly recommend using --ask-pass or SSH keys)

- ansible_sudo_pass
  The sudo password to use (this is insecure, we strongly recommend using --ask-sudo-pass)

- ansible_sudo_exe (new in version 1.8)
  The sudo command path.

- ansible_connection
  Connection type of the host.
  Candidates are local, ssh or paramiko.
  The default is paramiko before Ansible 1.2,
  and 'smart' afterwards which detects whether usage of 'ssh'
  would be feasible based on whether ControlPersist is supported.

- ansible_ssh_private_key_file
  Private key file used by ssh.
  Useful if using multiple keys and you don't want to use SSH agent.

- ansible_shell_type
  The shell type of the target system.
  By default commands are formatted using 'sh'-style syntax by default.
  Setting this to 'csh' or 'fish' will cause commands executed on target systems
  to follow those shell's syntax instead.

- ansible_python_interpreter
  The target host python path.
  This is useful for systems with more than one Python or not located at "/usr/bin/python" such as \*BSD, 
  or where /usr/bin/python is not a 2.X series Python.
  We do not use the "/usr/bin/env" mechanism as that requires the remote user's path to be set right
  and also assumes the "python" executable is named python,
  where the executable might be named something like "python26".

- ansible\_\*\_interpreter
  Works for anything such as ruby or perl and works just like ansible_python_interpreter.
  This replaces shebang of modules which will run on that host.

### Playbooks
- リモートホストの状態を定義するyamlファイル
### ansible.cfg
- Ansibleの設定ファイル。置く場所によって読み込まれる優先順位が異なる。
- 優先順位、オススメはホームディレクトリへの配置。
  1. 環境変数のファイルパス(ANSIBLE_CONFIG=/usr/local/ansible/conf/ansible.cfg)
  2. カレントディレクトリ (./ansible.cfg)
  3. ホームディレクトリ ($HOME/.ansible.cfg)
  4. /etc/ansible/ansible.cfg

#### Parameters
##### forks
- ターゲットノードの並列処理を行うプロセス数
##### log_path
- ansible実行コマンドログの配置場所を設定。
##### host_key_checking
- ターゲットノードにSSH接続する際の公開鍵のフィンガープリントチェック
##### gathering
- ターゲットノードの詳細情報取得に関する情報
  - implicit
  - explicit
  - smart
##### gather_subset
##### transport

## Directory layout
### 最小構成
- hosts #Inventory
- site.yml #Playbook
### [[http://docs.ansible.com/playbooks_best_practices.html#directory-layout][directory-layout best practice]]
- 
  - production         # inventory file for production servers
  - stageing           # inventory file for stage environment
   
  - group_vars/
    - group1           # here we assign variables to particular groups
    - group2           # ""
  - host_vars/
    - hostname1        # if systems need specific variables, put them here
    - hostname2        # ""
   
  - library/           # if any custom modules, put them here (optional)
  - filter_plugins/    # if any custom filter plugins, put them here (optional)
   
  - site.yml           # master playbook
  - webservers.yml     # playbook for webserver tier
  - dbservers.yml      # playbook for dbserver tier
   
  - roles/
    - common/          # this hierarchy represents a "role"
      - tasks/         #
        - main.yml     #  <-- tasks file can include smaller files if warranted
      - handlers/      #
        - main.yml     #  <-- handlers file
      - templates/     #  <-- files for use with the template resource
        - ntp.conf.j2  #  <------- templates end in .j2
      - files/         #
        - bar.txt      #  <-- files for use with the copy resource
        - foo.sh       #  <-- script files for use with the script resource
      - vars/          #
        - main.yml     #  <-- variables associated with this role
      - defaults/      #
        - main.yml     #  <-- default lower priority variables for this role
      - meta/          #
        - main.yml     #  <-- role dependencies

    - webtier/         # same kind of structure as "common" was above, done for the webtier role
    - monitoring/      # ""
    - fooapp/          # ""
### Memo
#### *.yml
- 
  ymlファイルにAnsibleで何をするかの定義がある。
  site.ymlが大本のファイルだが、include情報が主で、
  実際の定義はroles以下のmain.ymlに書かれる。

#### hosts
- 
  inventoryファイル。
  上のbest practiceではproductionとstageか。
  サーバをグループ分けしたりする。

#### vars
- 
  変数を外だしする。
  上でいうとgorup_varsとhost_varsか。

#### roles
- 
  サーバの役割による分岐点。
  上のbest practiceではcommon, webtier, monitoring, fooappなどに分かれている。
  更に各ディレクトリもいくつかのディレクトリに分ける。

##### tasks
- 
  各roleごとに何を実施するかが具体的に書かれる。
  サーバの設定やサービスのインストールはtasksディレクトリ以下のmainymlに書く。

##### handlers
- 
  サービス再起動のmain.ymlをおく。
  taskディレクトリ以下のmain.ymlでサーバの設定を行い、
  設定反映のためhandlersで再起動するイメージ。

##### templates
- 
  サービスの設定ファイルテンプレートをj2形式でおく。
  すべてPlaybookで書くよりも、テンプレートファイルを使用したほうが簡単のため。

## Memo
### host key
- 
  1.2.1以降のバージョンでは、ホストキーのチェックがデフォルトで実行される。
  もし不要であれば、"/etc/ansible/ansible.cfg"か"~/.ansile.cfg"を以下のように編集する。
    [defaults]
    host_key_checking = False

  以下でもよい。
    $ export ANSIBLE_HOST_KEY_CHECKING=False

### 基本構成
- inventry
- playbook
### Windowsでの利用
- 概要
  - Windows Remote Management(WinRM)を使用して操作を行う。
- Winの準備
  - WinRMの起動と構成を行う。
    - 構成スクリプトのダウンロード
      Invoke-WebRequest -Uri https://raw.githubusercontent.com/ansible/ansible/devel/examples/scripts/ConfigureRemotingForAnsible.ps1 -OutFile ConfigureRemotingForAnsible.psl
      (https://github.com/ansible/ansible/blob/devel/examples/scripts/ConfigureRemotingForAnsible.ps1)
    - ネットワークプロファイルの確認
      Get-NetConnectionProfile -IPv4Connectivity Internet
    - 実行 (プロファイルがPublicの場合、コマンド末尾の"-SkipNetworkProfileCheck"が必要、その他の場合は不要。)
      powershell -ExecutionPolicy RemoteSigned .\ConfigureRemotingForAnsible.ps1 [-SkipNetworkProfileCheck]
- Ansible側
  - pipのインストール
  - pywinrmのダウンロード
    pip install pywinrm
- [[http://qiita.com/yunano/items/f9d5652a296931a09a70][AnsibleでWindowsを操作する準備をする - Qiita]]
## Link
- [[https://www.ansible.com/][ANSIBLE]]
- [[http://docs.ansible.com/][Documentation]]
- [[http://techblog.clara.jp/2014/06/ansible_no1-how_to_install/][Ansible(1)概要とインストール方法について - CLARA ONLINE TECHBLOG]]
