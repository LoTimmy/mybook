`gvpe - creates a virtual ethernet between multiple endpoints`

`GNU Virtual Private Ethernet (GVPE)`

`GNU Virtual Private Ethernet` 的安全性通过 `OpenSSL` 库，借助公共/私有密匙机制进行处理。虚拟网络中的每个主机都被提供一个惟一的主机密匙，公共版本用于加密通信信道。

同时，由于虚拟专用网基于支持的、以太网级网络环境的，为每个主机都提供一个惟一的 `MAC` 地址，和一个本地以太网上的情况一样。这意味着您可以通过发送者（和接收者，如果必要的话）的 `MAC` 地址来验证信息的来源，额外提供了一级安全性。

`GVPE` 支持 `aes-128`、`aes-192`、`aes-256` 和 `bf` (`blowfish`) 密码，支持 `sha512`、`sha256`、`sha1`、`ripemd160`、`md5` 和 `md4` 摘要算法。



### 安裝 {#installing}

```console
shell> sudo apt-get install gvpe
```

`/etc/gvpe/gvpe.conf`
```
# Specify the use of UDP and the default port
enable-udp = yes
udp-port = 407

# Set the name of the virtual device created
ifname = vpn0

mtu = 1492

compress = yes
router-priority = 1

# Set the first node
node = branch1
hostname = 44.88.167.250

# Set the second node
node = branch2
hostname = 145.253.105.130
```

`创建公共/私有密匙`

```console
shell> gvpectrl -c /etc/gvpe -g
```

```
/etc/gvpe/hostkey
```

```console
shell> gvpectrl -s
```

```
gvpe: /usr/bin/gvpectrl
gvpe: /usr/share/doc/gvpe/examples/if-up.gz
gvpe: /usr/share/doc/gvpe/examples/node-up
gvpe: /etc/gvpe
```

```
connect = ondemand
```

```
/etc/gvpe/hostkey
/etc/gvpe/if-up
```

```
#!/bin/sh
ip link set $IFNAME address $MAC mtu $MTU up
[ $NODENAME = branch1 ] && ip addr add 10.0.0.1 dev $IFNAME
[ $NODENAME = branch2 ] && ip addr add 10.1.0.1 dev $IFNAME
ip route add 10.0.0.0/8 dev $IFNAME
```

#### :books: 參考網站：
- http://savannah.gnu.org/projects/gvpe/
- http://software.schmorp.de/pkg/gvpe.html
- http://pod.tst.eu/http://cvs.schmorp.de/gvpe/doc/gvpe.conf.5.pod
- [使用 GNU Virtual Private Ethernet](https://www.ibm.com/developerworks/cn/aix/library/au-gnuvpe/)

---

```console
shell> http://ftp.gnu.org/gnu/gvpe/gvpe-2.25.tar.gz

shell> gvpectrl -s
shell> /usr/local/sbin/gvpe -linfo branch3
shell> gvpectrl --kill
shell> sysctl -w net.ipv4.conf.eth0.proxy_arp=1
shell> sysctl -w net.ipv4.conf.vpn0.proxy_arp=1

shell> /usr/local/sbin/gvpe -linfo branch2
shell> /usr/local/sbin/gvpe -linfo branch1

shell> ./configure --enable-cipher=bf --enable-digest=md4
shell> ./configure --enable-hmac-length=16 --enable-rand-length=8 --enable-digest=sha1

shell> apt-get install libssl-dev
```

```console
shell> apt-get install gvpe
shell> vim /etc/default/gvpe
```

```
START_DAEMON=1
DAEMON_ARGS=" branch1"
```

`/usr/share/doc/gvpe/examples`

`/etc/gvpe/gvpe.conf`
```
enable-udp = yes
udp-port = 407
ifname = vpn0

node = doom

node = frank
hostname = 44.88.167.250
connect = always

node = rain
hostname = 145.253.105.130
```

```
shell> gvpectrl -c /etc/gvpe/ -g
```

```
-c, --config=DIR
-g, --generate-keys
```

```
mtu = bytes
Recommended values are 1500 (ethernet), 1492 (pppoe), 1472 (pptp).
```

```
shell> ip -4 addr list dev vpn0
shell> ip -4 route list dev vpn0
```

---
`MAXIMIZE SECURITY`
```
   ./configure --enable-hmac-length=16 --enable-rand-length=12 --enable-digest=ripemd610
```

`MINIMIZE CPU TIME REQUIRED`
```
   ./configure --enable-cipher=bf --enable-digest=md4
```


#### :books: 參考網站：
- [gvpe](http://ftp.gnu.org/gnu/gvpe/)
- http://manpages.ubuntu.com/manpages/zesty/man5/gvpe.conf.5.html
- https://manpages.debian.org/unstable/gvpe/gvpectrl.8.en.html

