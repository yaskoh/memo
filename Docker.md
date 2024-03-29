# Docker
## Commands
### docker
- show the full list of accepted arguments.
#### Options
##### --config string
##### -D, --debug
##### -H, --host list
##### -l, --log-level strisg
##### --tls
##### --tlscacert string
##### --tlscert string
##### --tlskey string
##### --tlsverify
##### -v, --version
#### Management Commands
##### checkpoint
##### config
##### container
- Usage : docker conaiter COMMAND
- Manage containers
###### Options
####### attach
####### commit
####### cp
####### exec
####### ls
- List containers
######## Aliases
- ls, ps, list
######## Options
######### -a, --all
- Show all containers (default shows just running)
######### -n, --last int
######### -l, --latest
######### -q, --quiet
######### -s, --size
##### image
- Usage : docker image COMMAND
- Manage images
###### Commands
####### bulid
####### history
####### import
####### inspect
####### load
####### ls
- List images
####### prune
####### pull
####### push
####### rm
####### save
####### tag
##### network
##### node
##### plugin
##### secret
##### service
##### stack
##### swarm
##### system
##### trust
##### volume
#### Commands
##### attach
- 
  Attach to a running container

##### build
##### commit
- 
  create a new image from a container's changes

- Usage
  docker commit [OPTIONS] CONTAINER [REPOSITORY [TAG]]

##### cp
##### create
##### deploy
##### diff
##### events
##### exec
- Run a command in a running container
###### Synopsis
- docker exec [OPTONS] CONTAINER COMMAND [ARG...]
###### Options
####### -d, --detach[=false]
####### -h, --help[=false]
####### -i, --interactive[=false]
- Keep STDIN open even if not attached
####### -t, --tty[=falsse]
- Allocate a pseudo-TTY
##### export
- 
  Stream the contents of a container as a tar archive

##### history
##### images
- 
  list images

- Usage

##### import
- 
  Create a new filesystem image from the contents of a tarball

##### info
- Display system-wide information
###### Options
####### -f, --format string
##### inspect
- 
  return low-level information on a container

- Usage
  docker inspect CONTAINER|IMAGE [CONTAIR|IMAGE...]

##### kill
##### load
- 
  Load an image from a tar archive on STDIN

- Usage
  docker load

- -i, --input=""
  Read from a tar archive file, instead of STDIN

##### login
##### logout
##### logs
- 
  fetch the logs of a container
  looks inside the container and returns its standard output.

##### pause
##### port
- 
  Lookup the public-facing port which is NAT-ed to PRIVATE_PORT

##### ps
- show a list of all running containers
###### Options
####### -a, --all
- show all containers including stopped ones.
####### -l, --latest
- show the ID of the machine you using
####### --no-trunc
####### -q, --quiet
  
##### pull
- 
  pull an image or a repository from the docker repository server

##### push
- 
  push an image or a repository to the Docker registry server

##### rename
##### restart
- 
  Restart a running container

##### rm
- 
  Remove a conatiner

- 
  All conteners can be deleted by using command as "docker rm `docker ps -a -q`"

##### rmi
- 
  Remove an image

##### run
- run a command in a new container.
  I usually use this command as "docker run -it image/images /bin/bash"
###### Options
####### -a, --attach list
####### -d, --detach=false
- detached mode: run container in the background and print new container ID
  tells Docker to run the container and put it in the background, to deamonize it.

####### -i, --interactive=false
- keep STDiIN open even if not attached
  allows us to make an interactive connection by grabbing the standard in of the container.

####### -p
- publish a container's port to the host
  format:  ip:hostPort:containerPont | ip::containerPort | hostPort:cantainerPort

####### -t, --tty=false
- allocate a pseudo-tty
  assign a pseudo-tty or terminal inside container

####### -v
- mount file or directory in the host to the container.
  -v /home/user/hostdir:/target/container
####### --add-host list
####### --name[=NAME]

##### save
- 
  save an image to a tar archive
- Usage
  docker save IMAGE
##### search
- 
  search for an image in the Docker index

##### start
- 
  Start a stopped container

##### stop
- 
  stop a running container
  tells Docker to politely stop the running container.

##### tag
##### top
##### unpause
##### update
##### version
- show the Docker version information
###### Options
####### -f, --format string
- Format the output using the given Go template
##### wait
### docker-compose
- docker-compose.ymlが必要。
#### Options
#### Commands
## network
### Link
- [[http://deeeet.com/writing/2014/05/11/docker-network/][Dockerのネットワークの基礎 - SOTA]]

## Documents
### Guides
#### Get Docker
##### Install Docker
- Docker Community Edition (CE)
  - Stable : reliable updates every quarter
  - Edge : new features every month
- Docker Enterprise Edition
  - for enterprise development and IT teams
  - Edeition
    Basic, Standard, Advanced
- Platforms
  - Dsektoop
    - for Mac
    - for Windows
  - Cloud
    - AWS
    - Azure
    - IBM Cloud
  - Server
    - EE
      - CentOS
      - Oracle Linux
      - RHEL
      - SUSE
      - Ubuntu
      - Windows Server 2016
    - CE
      - CentOS
      - Debian
      - Fedora
      - Ubuntu
##### Docker EE
##### Docker CE
###### Debian
####### Prerequisits
######## Docker EE customers
######## OS requirements
######## Uninstall old versions
####### Install Docker CE
######## Install using the repository
######### Set up the repository
1. apt update
   sudo apt-get update
2. set apt to use over https
   sudo apt-get install apt-transport-https ca-certificates curl gnupg2 software-properites-common
3. Add Docker's official GPG key
4. Set stable repository
######### Install Docker CE
1. Update 
   sudo apt-get update
2. Install
   sudo apt-get install docker-ce
  
######### Upgrade Docker CE
######## Install from a package
######### Upgrade Docker CE
######## Install using the convenience script
######### Upgrade Docker after using the convenience script
####### Install Docker Compose for Raspbian
####### Uninstall Docker CE
##### Ubuntu
##### Platforms supporting Docker EE and Docker CE
##### Optional Linux post-installation setps
#### Get started
##### Get started with Docker
###### Part 1: Orientation
####### Docker concepts
######## Images and containers
- docker ps
######## Containers and virtual machines
####### Prepare your Docker environment
######## Test Docker version
- docker --version
- docker version, docker info
######## Test Docker installation
- docker run hello-world
- docker image ls
- docker container ls --all
####### Recap and cheat sheet
####### Conclusion of part one
###### Part 2: Containers
####### Prerequisites
####### Introduction
- Container : bottom of the hierarchy of on app (Part 2)
- Service : Next level, difining how contaires behave in production (Part 3)
- Stack : Top level, difining the interactions of all the services (Part 5)
####### Your new development environment
- Dockerfile
####### Define a container with Dockerfile
- Dockerfile defines what goas on in the environment inside your container.
######## Dockerfile
####### The app itself
######## requirements.txt
######## app.py
####### Build the app
####### Run the app
####### Share your image
######## Log in with your Docker ID
######## Tag the image
######## Publish the image
######## Pull and run the image from the remote repository
####### Conclusion of part two
###### Part 3: Services
###### Part 4: Swarms
###### Part 5: Stacks
###### Part 6: Deploy your app
##### Docker overview
#### Develop with Docker
#### Configure networking
#### Manage application data
#### Run your app in production
### Product manuals
### Reference
#### File formats
##### Dockerfile
##### Compose file
##### Docker Cloud Stack file
#### Command-Line Interfaces (CLIs)
##### Docker CLI (docker)
###### docker (base command)
###### docker ps
##### Daemon CLI (dockerd)
##### Compose CLI (docker-machine)
##### Machine CLI (docker-compose)
##### Trusted Registry CLI
##### Universal Control Plane CLI
#### Application Programming Interfaces (APIs)
#### Drivers and specifications
#### Compliance control references
## Memo
### detach
- press Ctr-p Ctr-q when you detach and leave a container.

### Windows
#### Docker Toolbox
#### Docker for Windows
#### Windows Container on Windows Server
#### Link
- https://qiita.com/tksarah/items/cf3ca3724532491a6861
## link
- [[http://www.techscore.com/blog/2014/08/05/introduction-to-docker/][隔離の技術Dockerの考え方と使い方の基本 - TECHSCORE BLOG]]
- [[http://yuuki.hatenablog.com/entry/docker-performance][Dockerは早いのか？Dockerのパフォーマンスについて重要なことは何か？ - ゆううきブログ]]
  
