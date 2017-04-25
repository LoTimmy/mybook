`dnsmasq - Small caching DNS proxy and DHCP/TFTP server`
`dnsmasq-utils - Utilities for manipulating DHCP leases`

> 为`DHCP`和`DNS`使用`dnsmasq`是一个不错的主意，因为`dnsmasq`的配置过程很容易。

---

```console
shell> apt-get install dnsmasq 

shell> brew install dnsmasq
shell> cp /usr/local/opt/dnsmasq/dnsmasq.conf.example /usr/local/etc/dnsmasq.conf
shell> sudo brew services start dnsmasq
```

`/usr/local/etc/dnsmasq.conf`

`/etc/default/dnsmasq`

`/etc/dnsmasq.conf`


```
interface=
bind-interfaces

dhcp-range=192.168.0.50,192.168.0.150,12h
dhcp-range=192.168.0.50,192.168.0.150,255.255.255.0,12h

dhcp-host=11:22:33:44:55:66,192.168.0.60
dhcp-host=11:22:33:44:55:66,192.168.0.70,infinite
dhcp-host=11:22:33:44:55:66,ignore

dhcp-option=3,1.2.3.4

dhcp-lease-max=150
dhcp-leasefile=/var/lib/misc/dnsmasq.leases
```

```
no-resolv
no-poll
server=8.8.8.8
server=8.8.4.4

server=/example.com/example.org/192.168.1.88
```

```
listen-address=127.0.0.1
listen-address=127.0.0.1,192.168.0.1

cache-size=1000
log-queries
log-facility=/var/log/dnsmasq.log

server=/localnet/192.168.0.1
server=/localnet/127.0.0.1#10053
server=/in-addr.arpa/127.0.0.1#10053
server=/ip6.arpa/127.0.0.1#10053

address=/double-click.net/127.0.0.1
local-ttl=
```

```console
shell> dnsmasq --test
dnsmasq: syntax check OK.
```

---

`dnscrypt-proxy - Tool for securing communications between a client and a DNS resolver`

#### :books: 參考網站：
- http://www.thekelleys.org.uk/dnsmasq/docs/dnsmasq-man.html
- https://dnscrypt.org/
- https://simplednscrypt.org/
- https://www.opendns.com/about/innovations/dnscrypt/
- https://github.com/alterstep/dnscrypt-osxclient
- http://manpages.ubuntu.com/manpages/xenial/man8/dnsmasq.8.html


---

`dhcping - DHCP Daemon Ping Program`

```console
shell> apt-get install dhcping
shell> dhcping -s 255.255.255.255 -r -v  
```

#### :books: 參考網站：
- [dhcping](http://manpages.ubuntu.com/manpages/precise/man8/dhcping.8.html)

`DNS spoofing` (`DNS 詐騙`)
因採用另一系統的`網域名稱系統` (`DNS`) 而導致破壞信任關係的行為。其實施模式通常是破壞受侵害系統的名稱服務快取，或者破壞有效網域的網域名稱伺服器。



<!--
https://www.l68.net/2745.html
-->
