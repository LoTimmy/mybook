`IPv6`

> 每個與網際網路連接的伺服器和裝置都必須有數字網際網路協定 (`IP`) 地址。

> `IPv4`的位址格式是採用`32`位元長度，位址能提供2的32次方個，換算後約42億個。雖然`IPv4`有這麼多IP位址，但依舊在2011年的2月3日消耗殆盡。

> `IPv4`的IP位址是由`32`位元所組成，**原始的表示方式是8個位元為一個單位，分4個部分。每個部分以2進位表示，並以「.」做區隔**，譬如：「`10110110.11101001.01001100.11111111`」。不過這樣的表示法太長，不便記憶。所以通常都以10進位的方法表示，而每個部份的數字會呈現0至255的整數，譬如`210.59.230.150`。

> 而`IPv6`的位址格式則採用`128`位元長度，其位址能提供2的128次方個。它所能提供的`IP`位址，遠遠超過`IPv4`的數量，**預估能讓地球上每個人都分到100萬個IP位址，或是地球上每平方公尺面積皆提供1000多個IP位址**。簡而言之，轉換到`IPv6`後，`IP`位址的數量多到幾乎不可能用盡。

> 而`IPv6`的`IP`位址則是`128`位元組成，表示方式是使用`8`組數字，每組為`4`個字元的`16`進位方法表示。而區隔每個部分的方式亦與`IPv4`不同，是以「`:`」表示。譬如「`1079:0BD3:6ED4:1D71:414B:2E2A:7144:72BE`」，這樣就是一組標準的`IPv6`網路位址。

> 不過`IPv6`的位址表示法太長，所以位址有所謂的省略規則，以下為2個位址省略規則：
- 規則1：為每組數字的第一個0可以省略，若整組皆為0，則以0表示。譬如，「0DB8」可以省略為「DB8」，「0000」則為「0」。
- 規則2：為連續出現的0000可以省略成「::」。譬如：「:0000:0000:0000:0000:」可以省略成「:0000:0000:0000::」、「:0:0:0:0:」、「:0::0:」或「::」。
> 但需注意的是，由於「::」表示為連續且數量多的0，所以如果位址中出現2個「::」時，會讓人搞不清楚實際代表的位址。因為這樣，在位址省略規則中有明訂，對於一個IPv6位址，只能出現一次「::」來省略0。
> 由於`IPv6`的位址經過省略後，依舊不方便一般人記憶。所以在網頁存取位址，或撰寫應用程式呼叫網址時，建議不要直接使用`IPv6`位址，應該使用`DNS`網域名稱會較為方便。
> 除了表示方式不同外，兩者間的位址型態也有些許差異。像`IPv6`提供`Unicast`、`Anycast`及`Multicast`，三種位址型態。其中`Unicast`對應單點傳送、`Multicast`則取代廣播，只有這兩點與`IPv4`類似。而`Anycast`則是發送給群組，但只有最近的介面會接收到。

> `IPv6` 是新的網際網路協定版本，它使用的地址空間比之前的 `IPv4` 更大。`IPv4` 的每個 `IP` 地址長度為 `32` 位元，可允許 `43` 億個唯一地址。`IPv4` 地址的範例為 `192.0.2.1`。相較之下，`IPv6` 地址為 `128` 位元，可允許約三百四十兆個唯一 IP 地址。`IPv6` 地址的範例為：`2001:0db8:85a3:0:0:8a2e:0370:7334`

> `IPv6`的未來走向已經逐漸明朗，那就是取代`IPv4`成為下一代網路通訊協定。

> 基本上，一般企業都相信，翻新網路架構與伺服器來採用`IPv6`，可以加快網路的傳輸效率以及建立更安全、穩定的網路環境，因為`IPv6`可以帶來更多的`IP`數量，足以應付網路設備、行動電話等管理需求。

> `IPv6`的出現，預計會讓現有`IPv4`的網路世界逐漸改觀，不過在達到那一階段之前，還有許多階段必須跨越。目前有個技術名詞稱為「`dual stack`」，宣稱**可以同時實現`IPv4`與`IPv6`共存**的理想，不僅用戶終端、路由器與交換器可以同時執行兩種協定的運作，而且還能預設以`IPv6`為優先。

> `IPv6` 位址大小是 `128` 位元。 偏好的 `IPv6` 位址表示法為 `x:x:x:x:x:x:x:x`，其中每一個 `x` 都是十六進位值，共 `8` 個 16 位元位址片段。`IPv6` 位址範圍從 `0000:0000:0000:0000:0000:0000:0000:0000` 到 `ffff:ffff:ffff:ffff:ffff:ffff:ffff:ffff`。

> `IPv6` 位址的另一種替代格式結合了冒號和帶點表示法，所以 `IPv4` 位址可以內含於 `IPv6` 位址。最左邊的 `96` 位元指定十六進位值，最右邊的 `32` 位元指定十進位值，表示內含的 `IPv4` 位址。

> 它可讓 `IPv6` 應用程式直接與 `IPv4` 應用程式通訊。 例如，`0:0:0:0:0:ffff:192.1.56.10` 和 `::ffff:192.1.56.10/96` (簡短格式)。

> 既然不可能短期之內從純`IPv4`轉成`IPv6`，如何讓使用者能夠在這兩者間的網路，同時保持連線，**而目前較主要的`IPv6`移轉技術有三個，`雙協定堆疊`（`Dual Stack`，以下簡稱雙協定）、`穿隧`（`Tunneling`）、`轉換`（`Translation`）**。

> **以雙協定技術而言，它是讓網路設備同時具備`IPv4`與`IPv6`的網路位址，如果要連線至純`IPv4`網站，就能用本身的`IPv4`位址去連接，而`IPv6`亦然**。**穿隧技術則是在`IPv4`網路上建立一個隧道，讓個別獨立的`IPv6`端點能互通**。**轉換技術則是三個技術中，唯一能讓純`IPv4`與純`IPv6`互連的一個方法，它能夠將`IPv4`位址轉換成`IPv6`位址，且`IPv6`亦然**。

> **而目前最建議使用的`IPv6`轉移技術為雙協定技術，由於它能夠同時擁有`IPv4`與`IPv6`的`IP`位址，使用者不論要連線到哪個網站都可行**。雖然這技術的缺點，是雙協定設備的普及度要夠高。使用者才能隨意連線到`IPv4`與`IPv6`的網站。

> 不過事實上，這技術其實已經默默的出現在我們週遭的設備上，只是我們使用上渾不自覺。**像目前市面上的作業系統，其實有95%都支援雙協定**，僅剩少數不能使用。而轉換技術雖然能讓IPv4與IPv6互相連接，但卻是最不建議使用的一種方法。這是因為它所能提供的服務人數少，且只支援單純的位址解析。如果有特殊的應用位址，則需要配合應用層閘道器使用，故該技術大多出現在實驗室居多。


> 一般而言，`dual stack`技術上是要完成網路核心到邊際之間的溝通，讓兩種`TCP/IP`協定可以在`WAN`的核心路由器、周邊路由器、防火牆、伺服器群集路由器，最後到用戶終端都能運行無阻。等到這些網路基礎建設都支援兩種通訊協定之後，接下來就換伺服器和終端電腦系統了。另一方面，還有一個相關的技術名詞叫做「`tunnel`」技術，它是指讓一項協定整合進入另一項協定之中。這種通道技術是將`IPv6`封包包覆在`IPv4`的封包裡，好讓這些封包可以傳送到部分尚未升級為`IPv6`的網路區段。

> 眾所周知在`IPv4`網路中，只要不在同一個子網路之下，終端設備就無法連接到網際網路中，因此我們在設定網路時都必須知道該網路的子網路遮罩與相關`IP`位址設定，這對管理者與使用者而言都是相當耗時費力的工作，所幸後來有`DHCP`協定，只要設定好`DHCP`伺服器，任何新設備都可以自動發出要求，並獲得一個可供利用的`IP`位址。但是這也正是`IPv4`網路最大的問題所在，因為`IP`位址不足的狀況日益嚴重，加上管理要求使然，幾乎`DHCP`伺服器都是存在在`NAT`網路架構之下另行配發虛擬`IP`位址，雖然可以解決`IP`位址不足的問題，卻也因此降低了機動性與便利性。

> 不過在`IPv6`網路中可以讓所有的行動裝置取得一個真實`IP`位址，不管網路環境多大，都足以應付。並且只要基礎設施建置完成，就不需要特別升級以因應Mobile IP的存在。雖然`IPv6`位址相當難以記憶，不過`IPv6`同樣提供了自動配置的方式，讓設備可以自動取得IP，並且還能夠自動搜尋芳鄰，提高網路的可用性。


![](https://docs.oracle.com/cd/E19683-01/817-0573/images/dual.epsi.gif)

---

![](http://docs.oracle.com/cd/E23823_01/html/816-4554/figures/basic-IPv6-address.png)

![](http://docs.oracle.com/cd/E23823_01/html/816-4554/figures/link-local-unicast.png)


`單點傳播位址`

`鏈結本端位址`
 
`Link-Local`
`fe80::`
`fe80::/10`
`fe80::interface-ID/10`
`fe80::23a1:b152`

`fc00::/7`

`fe80::20c:29ff:fe12:f198`
HWaddr `00:0c:29:12:f1:98`
`fe80::29c6:4c36:4eca:9bbe`

`::ffff:x.x.x.x/96`
`2001::/32`
`2002::/16`

> `鏈結本端位址`是為了使用於單一本端鏈結 (`區域網路`) 而設計。
> 用於`鏈結本端位址`的字首為 `fe80::/10`。
> **`路由器`不轉遞目的地或來源位址含有`鏈結本端位址`的封包**。

`廣域位址`
> `廣域位址`是為了使用於任何網路而設計的。
> 用於`廣域位址`的字首開頭是二進位 `001`。

`未指定的位址`
> `未指定的位址`為 `0:0:0:0:0:0:0:0`。
> 可以將該位址縮寫成兩個冒號 (`::`)。

`迴圈位址`
> `迴圈位址`為 `0:0:0:0:0:0:0:1`。
> 可以將該位址縮寫成 `::1`。

`IPv4`
``` 
127.0.0.1	localhost
```

`IPv6`
```
::1     localhost ip6-localhost ip6-loopback
```

`任意點傳送位址`
`多點傳播位址`


![](http://i.imgur.com/K1mqW5H.png)

```
192.168.15.1 → ::ffff:192.168.15.1
               ::ffff:c0a8:0e01

114.35.124.22 → 0:0:0:0:0:ffff:7223:7c16
                ::ffff:114.35.124.22
```

```
nameserver 8.8.8.8
nameserver 8.8.4.4

nameserver 2001:4860:4860::8888
nameserver 2001:4860:4860::8844

nameserver 168.95.1.1
nameserver 168.95.192.1

nameserver 2001:b000:168::1
nameserver 2001:b000:168::2
```

`ping6`
`ping`

`6to4`
`2002:WWXX:YYZZ::/48`


 


#### :books: 參考網站：
- https://www.ibm.com/support/knowledgecenter/zh-tw/ssw_ibm_i_61/rzai2/rzai2ipv6addrformat.htm
- https://www.ibm.com/support/knowledgecenter/zh-tw/ssw_ibm_i_61/rzai2/rzai2ipv6addrtypes.htm
- [當DHCP遇見IPv6 快速入門DHCPv6協定](http://www.netadmin.com.tw/article_content.aspx?sn=1506290006)
- [認識IPv4與IPv6的差異](http://www.ithome.com.tw/tech/92046)
- http://www.ithome.com.tw/news/102444
- http://www.ithome.com.tw/node/29037
- https://zh.wikipedia.org/wiki/IPv6
- [ipv4toipv6](https://www.ultratools.com/tools/ipv4toipv6)
- [ipv6Info](https://www.ultratools.com/tools/ipv6Info)
- https://msdn.microsoft.com/zh-tw/library/aa450092.aspx

---

`透過 DHCP 自動取得 IPv6 位址`
`透過路由器通告自動取得 IPv6 位址`
`靜態 IPv6 位址`

---

```
eth0      Link encap:Ethernet  HWaddr 00:0c:29:12:f1:98  
          inet addr:192.168.88.1  Bcast:192.168.88.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe12:f198/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:231273945 errors:0 dropped:11558 overruns:0 frame:0
          TX packets:233224490 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:162498189508 (162.4 GB)  TX bytes:257383907367 (257.3 GB)

eth1      Link encap:Ethernet  HWaddr 00:0c:29:12:f1:8e  
          inet addr:211.23.141.208  Bcast:211.23.141.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe12:f18e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:267044977 errors:0 dropped:0 overruns:0 frame:0
          TX packets:235917901 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:259991317276 (259.9 GB)  TX bytes:165104279876 (165.1 GB)
```

```
ens32     Link encap:Ethernet  HWaddr 00:0c:29:62:13:07  
          inet addr:192.168.88.10  Bcast:192.168.88.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe62:1307/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4334605 errors:0 dropped:0 overruns:0 frame:0
          TX packets:668408 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:519042843 (519.0 MB)  TX bytes:483552343 (483.5 MB)
```

```
Windows IP 設定


乙太網路卡 區域連線:

   連線特定 DNS 尾碼 . . . . . . . . :
   連結-本機 IPv6 位址 . . . . . . . : fe80::29c6:4c36:4eca:9bbe%11
   IPv4 位址 . . . . . . . . . . . . : 192.168.88.254
   子網路遮罩 . . . . . . . . . . . .: 255.255.255.0
   預設閘道 . . . . . . . . . . . . .: 192.168.88.1
```

```console
shell> ping6 -I eth0 fe80::20c:29ff:fe62:1307
shell> ping6 -I eth0 -c 5 fe80::20c:29ff:fe62:1307
PING fe80::20c:29ff:fe62:1307(fe80::20c:29ff:fe62:1307) from fe80::20c:29ff:fe12:f198 eth0: 56 data bytes
64 bytes from fe80::20c:29ff:fe62:1307: icmp_seq=1 ttl=64 time=0.124 ms
64 bytes from fe80::20c:29ff:fe62:1307: icmp_seq=2 ttl=64 time=0.121 ms
64 bytes from fe80::20c:29ff:fe62:1307: icmp_seq=3 ttl=64 time=0.088 ms
64 bytes from fe80::20c:29ff:fe62:1307: icmp_seq=4 ttl=64 time=0.094 ms
64 bytes from fe80::20c:29ff:fe62:1307: icmp_seq=5 ttl=64 time=0.108 ms

--- fe80::20c:29ff:fe62:1307 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 3997ms
rtt min/avg/max/mdev = 0.088/0.107/0.124/0.014 ms

shell> ping6 -I eth0 fe80::29c6:4c36:4eca:9bbe
```

```console
shell> ping fe80::20c:29ff:fe62:1307%11

Ping fe80::20c:29ff:fe62:1307%11 (使用 32 位元組的資料):
回覆自 fe80::20c:29ff:fe62:1307%11: time<1ms
回覆自 fe80::20c:29ff:fe62:1307%11: time<1ms
回覆自 fe80::20c:29ff:fe62:1307%11: time<1ms
回覆自 fe80::20c:29ff:fe62:1307%11: time<1ms

fe80::20c:29ff:fe62:1307%11 的 Ping 統計資料:
    封包: 已傳送 = 4，已收到 = 4, 已遺失 = 0 (0% 遺失)，
大約的來回時間 (毫秒):
    最小值 = 0ms，最大值 = 0ms，平均 = 0ms
```

```console
shell> netsh interface ipv6 show neighbors
```

```
介面 11: 區域連線


網際網路位址                                  實體位址           類型
--------------------------------------------  -----------------  -----------
ff02::1                                       33-33-00-00-00-01  永久
ff02::2                                       33-33-00-00-00-02  永久
ff02::16                                      33-33-00-00-00-16  永久
ff02::fb                                      33-33-00-00-00-fb  永久
ff02::1:2                                     33-33-00-01-00-02  永久
ff02::1:3                                     33-33-00-01-00-03  永久
ff02::1:ff0b:ccde                             33-33-ff-0b-cc-de  永久
ff02::1:ff12:f198                             33-33-ff-12-f1-98  永久
ff02::1:ff75:9db4                             33-33-ff-75-9d-b4  永久
```

```console
shell> ping6 fe80::1408:9434:b01d:c7f9%en0
```

- https://technet.microsoft.com/en-us/library/cc753156(v=ws.10).aspx

---

```console
shell> ssh -6 ::1
shell> ssh -6 fe80::6231:97ff:fe75:9db4%eth0
```


---

`http://[fe80::6231:97ff:fe75:9db4]/`


---

![](http://i.imgur.com/hJ6QvFs.png)

---
<!--



```

4. 設區網ip
一般用 3ffe 開頭的即可，mask用64就可以
電腦1 # ip -6 addr add 3ffe:ffff::1/64 dev eth0
電腦2 # ip -6 addr add 3ffe:ffff::2/64 dev eth0
我習慣把區網內 192.168.1.xx 最後的 xx 對應 ipv6 的
3ffe:ffff::xx/64

5. ping6
# ping6 3ffe:ffff::1
# ping6 3ffe:ffff::2

6. 再測 ssh
# ssh 3ffe:ffff::1
# ssh 3ffe:ffff::2


# ssh -6 fe80::21b:21ff:fe22:e865%eth1
# ssh -6 ::1

```


因為stateless autoconfigure方式取得IPv6的IP是Global prefix+eui64所的128byte數字，
像我這台主機取得的IP為2001:288:829f:5:211:25ff:fe8d:7e8c，
其中的前半段(64byte)為Global prefix(2001:288:829f:5)，
而後半段(64byte，211:25ff:fe8d:7e8c)是由網卡MAC號碼(48byte)轉換成EUI64格式的MAC(64byte)。


首先我們必須先取得相關的環境設定值：
1.default gateway: 2001:288:829f:5:209:fff:fe85:ebb7
我們在autoconfigure時，就取得了fe80::209:fff:fe85:ebb7，去掉Link Local prefix(fe80::)，加上Global prefix(2001:288:829f:5::)，就成為 2001:288:829f:5:209:fff:fe85:ebb7。



- http://blog.hmes.kh.edu.tw/wordpress/jang/2010/04/22/centos5-ipv6-%E7%B6%B2%E8%B7%AF%E7%92%B0%E5%A2%83%E8%A8%AD%E5%AE%9A2/

-->

