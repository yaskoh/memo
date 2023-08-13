# Linux Network
## Command
### ip
### ss
- netstatの代わり
### tc
- show/manipulate traffic control settings
## Memo
### ip
- ip(特にip a)に関するメモ
#### L1
##### lo, eth, pan
###### lo
- local loopback
  特別な仮想インターフェイス。ホスト自身を指し、必ず127.0.0.1が割り当てられる。
###### eth
- Ethernet
  有線
###### pan
- Private Area Network 短距離無線通信デバイス
  Bluetoothなどに割り当てられる。
  
##### UP, etc...
###### LOOPBACK
###### BROADCAST
###### MULTICAST
###### UP
- it has been enabled.
  this can be controlled by a man or a script using the "ip link set <device> up" 
###### LOWER_UP
- the state of Ethernet link, as Driver signals L1 up.
  it basically means the cable is fitted and it can see another device on teh other end of the cable.
##### mtu nnnn
- MTU(Maximum Transfer Unit : Ethernetフレームの最大転送サイズ)
##### qdisc
- Queueing discipline
- [[http://labs.gree.jp/blog/2014/10/11266/][よくわかるLinux帯域制限 - GREE Engineer's Blog]]
###### noqueue
###### pfifo_fast
##### state
###### UP
###### DOWN
###### UNKNOWN
##### qlen
#### L2以降
##### link, inet
###### link/*(ether, etc...)
- Mac address
####### brd ff:ff:ff:ff:ff:ff
- broadcast address
###### inet/*
- ip address
####### brd nnn:nnn:nnn:nnn
- broadcast address
####### scope
- host
- global
  
###### inet6/*
- ip v6
