> `SDN` 全名為（`Software Defined Network`）即`軟件定義網絡`，是現互聯網中一種新型的網絡創新架構,其核心技術`OpenFlow` 通過網絡設備控制面與數據面分離開來,從而實現網絡流量的靈活控制,為網絡及應用提供了良好的平台。
> 而`Mininet` 是一個輕量級軟件定義網絡和測試平台；它採用輕量級的虛擬化技術使一個單一的系統看起來像一個完整的網絡運行想過的內核系統和用戶代碼，也可簡單理解為`SDN` 網絡系統中的一種基於進程虛擬化平台，它支持`OpenFlow`、`OpenvSwith` 等各種協議，`Mininet` 也可以模擬一個完整的網絡主機、鏈接和交換機在同一台計算機上且有助於互動開發、測試和演示，尤其是那些使用`OpenFlow` 和`SDN` 技術；同時也可將此進程虛擬化的平台下代碼遷移到真實的環境中。

`Mininet` 實現的特性
> 支持 OpenFlow、OpenvSwitch 等軟定義網路部件
> 支持系統級的還原測試，支持複雜拓撲，自定義拓撲等
> 提供 Python API, 方便多人協作開發
> 很好的硬件移植性與高擴展性
> 支持數千台主機的網絡結構

![](https://www.ibm.com/developerworks/cn/cloud/library/1404_luojun_sdnmininet/image003.jpg)

```
shell> sudo apt-get install mininet
shell> sudo mn --test pingall
shell> mn
*** No default OpenFlow controller found for default switch!
*** Falling back to OVS Bridge
*** Creating network
*** Adding controller
*** Adding hosts:
h1 h2
*** Adding switches:
s1
*** Adding links:
(h1, s1) (h2, s1)
*** Configuring hosts
h1 h2
*** Starting controller

*** Starting 1 switches
s1 ...
*** Starting CLI:
mininet>
```

```
s1-eth1   Link encap:Ethernet  HWaddr 72:e9:3d:e8:6a:99
          inet6 addr: fe80::70e9:3dff:fee8:6a99/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:578 (578.0 B)  TX bytes:1066 (1.0 KB)

s1-eth2   Link encap:Ethernet  HWaddr a6:53:8c:42:db:bc
          inet6 addr: fe80::a453:8cff:fe42:dbbc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:578 (578.0 B)  TX bytes:1066 (1.0 KB)
```

```
mininet> help
Documented commands (type help <topic>):
========================================
EOF    gterm  iperfudp  nodes        pingpair      py      switch
dpctl  help   link      noecho       pingpairfull  quit    time
dump   intfs  links     pingall      ports         sh      x
exit   iperf  net       pingallfull  px            source  xterm

You may also send a command to a node using:
  <node> command {args}
For example:
  mininet> h1 ifconfig

The interpreter automatically substitutes IP addresses
for node names when a node is the first arg, so commands
like
  mininet> h2 ping h3
should work.

Some character-oriented interactive commands require
noecho:
  mininet> noecho h2 vi foo.py
However, starting up an xterm/gterm is generally better:
  mininet> xterm h2
```

```
mininet> h1 ifconfig
h1-eth0   Link encap:Ethernet  HWaddr a6:fe:7e:9a:56:3b
          inet addr:10.0.0.1  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::a4fe:7eff:fe9a:563b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1206 (1.2 KB)  TX bytes:648 (648.0 B)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

```
mininet> h1 ping h2
PING 10.0.0.2 (10.0.0.2) 56(84) bytes of data.
64 bytes from 10.0.0.2: icmp_seq=1 ttl=64 time=0.335 ms
64 bytes from 10.0.0.2: icmp_seq=2 ttl=64 time=0.055 ms
64 bytes from 10.0.0.2: icmp_seq=3 ttl=64 time=0.051 ms
64 bytes from 10.0.0.2: icmp_seq=4 ttl=64 time=0.054 ms
```

```
mininet> nodes
available nodes are:
h1 h2 s1
```

```
mininet> net
h1 h1-eth0:s1-eth1
h2 h2-eth0:s1-eth2
s1 lo:  s1-eth1:h1-eth0 s1-eth2:h2-eth0
```

```
mininet> dump
<Host h1: h1-eth0:10.0.0.1 pid=2993>
<Host h2: h2-eth0:10.0.0.2 pid=2996>
<OVSBridge s1: lo:127.0.0.1,s1-eth1:None,s1-eth2:None pid=3002>
```

```
mininet> iperf
*** Iperf: testing TCP bandwidth between h1 and h2
*** Results: ['65.6 Gbits/sec', '65.6 Gbits/sec']
```

```
shell> sudo apt-get install python-pip
shell> pip install --upgrade pip
shell> pip install ryu
```

`l2.py`
```
from ryu.base import app_manager

class L2Switch(app_manager.RyuApp):
    def __init__(self, *args, **kwargs):
        super(L2Switch, self).__init__(*args, **kwargs)
```

```
shell> ryu-manager ~/l2.py
```

#### :books: 參考網站：
- http://mininet.org/
- http://mininet.org/download/
- https://osrg.github.io/ryu/
- https://www.ibm.com/developerworks/cn/cloud/library/1404_luojun_sdnmininet/index.html
