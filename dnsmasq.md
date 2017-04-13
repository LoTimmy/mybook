`dnsmasq - Small caching DNS proxy and DHCP/TFTP server`
`dnsmasq-utils - Utilities for manipulating DHCP leases`

> 为`DHCP`和`DNS`使用`dnsmasq`是一个不错的主意，因为`dnsmasq`的配置过程很容易。
---

```console
shell> apt-get install dnsmasq 
```

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
listen-address=127.0.0.1
listen-address=127.0.0.1,192.168.0.1

cache-size=150
log-queries

server=/localnet/192.168.0.1

address=/double-click.net/127.0.0.1
```


---

`dnscrypt-proxy - Tool for securing communications between a client and a DNS resolver`

#### :books: 參考網站：
- http://www.thekelleys.org.uk/dnsmasq/docs/dnsmasq-man.html
- https://dnscrypt.org/
- https://simplednscrypt.org/
- https://www.opendns.com/about/innovations/dnscrypt/
- https://github.com/alterstep/dnscrypt-osxclient


---

`dhcping - DHCP Daemon Ping Program`

```console
shell> apt-get install dhcping
shell> dhcping -s 255.255.255.255 -r -v  
```

#### :books: 參考網站：
- [dhcping](http://manpages.ubuntu.com/manpages/precise/man8/dhcping.8.html)