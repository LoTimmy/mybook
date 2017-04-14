`dnsmasq - Small caching DNS proxy and DHCP/TFTP server`

`dnsmasq - A lightweight DHCP and caching DNS server.`

`dnsmasq-utils - Utilities for manipulating DHCP leases`

> 为`DHCP`和`DNS`使用`dnsmasq`是一个不错的主意，因为`dnsmasq`的配置过程很容易。

---

```console
shell> apt-get install dnsmasq 

shell> brew install dnsmasq

shell> cp $(brew list dnsmasq | grep dnsmasq.conf.example) $(brew --prefix)/etc/dnsmasq.conf
shell> cp $(brew --prefix dnsmasq)/dnsmasq.conf.example $(brew --prefix)/etc/dnsmasq.conf

shell> sudo brew services start dnsmasq
shell> sudo brew services stop dnsmasq
shell> sudo brew services restart dnsmasq
shell> sudo brew services list
```

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
server=8.8.8.8
```

```
listen-address=127.0.0.1
listen-address=127.0.0.1,192.168.0.1

cache-size=150
log-queries

server=/localnet/192.168.0.1

address=/double-click.net/127.0.0.1
address=/.facebook.com/127.0.0.1
```

#### :books: 參考網站：
- https://github.com/Homebrew/homebrew-services
- http://www.thekelleys.org.uk/dnsmasq/docs/dnsmasq-man.html

---

`dhcping - DHCP Daemon Ping Program`

```console
shell> apt-get install dhcping
shell> dhcping -s 255.255.255.255 -r -v  
```

#### :books: 參考網站：
- [dhcping](http://manpages.ubuntu.com/manpages/precise/man8/dhcping.8.html)

---

`dnscrypt-proxy - Tool for securing communications between a client and a DNS resolver`

```console
shell> brew install dnscrypt-proxy

shell> /usr/local/opt/dnscrypt-proxy/bin/dnscrypt-update-resolvers
shell> sudo brew services start dnscrypt-proxy
shell> sudo brew services stop dnscrypt-proxy
shell> sudo brew services restart dnscrypt-proxy
shell> sudo brew services list

shell> scutil --dns
```

`/usr/local/etc/dnscrypt-proxy.conf`
```
ResolverName random
ResolverName cisco
LocalAddress 127.0.0.1:40
```

`dnsmasq.conf`
```
server=127.0.0.1#40
```

#### :books: 參考網站：
- [dnscrypt](https://dnscrypt.org/)
- [simplednscrypt](https://simplednscrypt.org/)
- https://www.opendns.com/about/innovations/dnscrypt/
- https://github.com/alterstep/dnscrypt-osxclient
