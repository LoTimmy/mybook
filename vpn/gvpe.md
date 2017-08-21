`gvpe - creates a virtual ethernet between multiple endpoints`

`GNU Virtual Private Ethernet (GVPE)`

> `GNU Virtual Private Ethernet` 的安全性通過 `OpenSSL` 庫，借助公共/私有密匙機制進行處理。虛擬網絡中的每個主機都被提供一個惟一的主機密匙，公共版本用於加密通信信道。

> 同時，由於虛擬專用網基於支持的、以太網級網絡環境的，為每個主機都提供一個惟一的 `MAC` 地址，和一個本地以太網上的情況一樣。這意味著您可以通過發送者（和接收者，如果必要的話）的 `MAC` 地址來驗證信息的來源，額外提供了一級安全性。

> `GVPE` 支持`aes-128`、`aes-192`、`aes-256` 和`bf` (`blowfish`) 密碼，支持`sha512`、`sha256`、`sha1`、`ripemd160`、 `md5` 和`md4` 摘要算法。


### 安裝 {#installing}

```
shell> sudo apt-get install gvpe
```

`gvpe.conf` 配置文件
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

`創建公共/私有密匙`
> 需要為每台主機創建公共/私有密匙，它們將用於加密和主機識別。
> `hostkeys` 目錄包含每台主機的主機密匙（私有）信息。 `pubkeys` 目錄包含每台主機的公共密匙。

```
shell> gvpectrl -c /etc/gvpe -g
```

```
/etc/gvpe/hostkey
```

```
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

`網絡初始化腳本`

> 在每台主機上創建虛擬網絡時，新創建的網絡設備需要被配置一個 IP 地址，還需要配置路由方式，以便將數據從一台機器路由到另一台機器。

> 當 `gvpe` 在每台機器上啟動時，它將運行 `if-up`（`interface up` 的縮寫）來設置虛擬接口。在此過程中，它將提供一些腳本中可能會使用的標準 `shell` 環境變量來設置信息（比如識別節點名、接口名和 `gvpe` 生成的 `MAC` 地址）。

> 第一行通過使用指定的 `MTU` 設置接口的 `MAC` 地址。這些變量由 `gvpe` 設置，因此這條命令實際上將被擴展為下面的類似代碼：`ip link vpn0 address fe:fd:80:00:00:01 mtu 1500 up`。

> 第二和第三行設置虛擬用戶的 IP 地址。內聯測試允許您選擇將哪個 IP 地址分配給哪個主機。這就是您設置虛擬網絡的 IP 地址的地方。您應該選擇一個還沒有使用的網絡範圍（典型的示例是 10.0.0.0 範圍或 192.168.0.0 範圍）。

> 在本例中，指定為 private1 的節點將被設置為 IP 地址 10.0.1.1，private2 被設置為 10.0.2.1。

> 最後一行設置默認路由方式，重定向 10.0.0.0 網絡的所有流量通過新創建的虛擬接口。

```
#!/bin/sh
ip link set $IFNAME address $MAC mtu $MTU up
[ $NODENAME = private1 ] && ip addr add 10.0.1.1 dev $IFNAME
[ $NODENAME = private2 ] && ip addr add 10.0.2.1 dev $IFNAME
ip route add 10.0.0.0/16 dev $IFNAME
```

`將配置複製到每台機器`

> 現在腳本、配置和密匙信息已就緒，需要將這些信息複製到每台機器。由於我們的網絡中只有一台額外的機器，我們只需複製配置一次，但您可以針對您的網絡中的每台機器重複這個過程。

> 記住，您只需從 `etc/gvpe` 目錄複製 `gvpe.conf` 文件、`if-up` 腳本和公共密匙目錄（`pubkey`）。

`啟動 gvpe`
> `gvpe` 流程是簡單、靜默的。啟動後，它通常作為一個守護進程在後台運行。因此，只需運行以下命令即可離開：$ `gvpe`。

> 但是，您可能想從輸出獲取一些日誌信息。可以使用 `-l` 參數指定不同的日誌級別。對於測試，您還可以使用 `-D` 參數來阻止 `gvpe` 進入守護進程模式。您還需要指定節點名

```
$ gvpe -D -l info private1
gvpe daemon 2.22 (Jun 13 2010 11:05:50) starting up.
```
```
$ gvpe -l info -D private2
gvpe daemon 2.22 (Jun 13 2010 08:30:01) starting up.
private1(udp/192.168.1.20:407): connection established (direct), protocol version 0.1.
```

`監控虛擬網絡的狀態`
```
$ gvpectrl -s

Configuration

# of nodes:         2
this node:          <unset>
MTU:                1500
rekeying interval:  0
keepalive interval: 0
interface:          vpn0
primary rsa key:    <default>
rsa key size:       1280

 ID#  MAC               Com Conmode   Node        Host:Port
   1  fe:fd:80:00:00:01  Y  always    private1    192.168.1.20:407
   2  fe:fd:80:00:00:02  Y  always    private2    www.example.com:407
```


```
enable-udp = yes
udp-port = 407

# Set the name of the virtual device created

ifname = vpn0

# Set the first node

node = private1
hostname = 192.168.1.20

# Set the second node

node = private2
hostname = remote.example.com

node = private3
hostname = ec2.amazon.com
enable-tcp = yes
tcp-port = 443

node = private4
hostname = 129.168.23.47
enable-rawip = yes

node = private5
hostname = 192.168.100.20
udp-port = 20000
```



#### :books: 參考網站：
- http://savannah.gnu.org/projects/gvpe/
- http://software.schmorp.de/pkg/gvpe.html
- http://pod.tst.eu/http://cvs.schmorp.de/gvpe/doc/gvpe.conf.5.pod
- [使用 GNU Virtual Private Ethernet](https://www.ibm.com/developerworks/cn/aix/library/au-gnuvpe/)

---

> 通過對 `configure` 腳本使用 `--enable-digest` 選項來設置要使用的摘要，使用 `--enable-cipher` 來設置要使用的密碼。
如果沒有進行這個指定，將使用 `ripemd160` 摘要和 `aes-128` 密碼。

> 公共密匙必須被複製到虛擬網絡中的每台主機，因為每台主機都需要它們來進行通信。主機密匙只在每台具體主機上需要，即，`private1` 主機密匙（將位於 `hostkeys/private1` 中）只需被複製到虛擬網絡中充當 `private1` 的主機。


```
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

```
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

