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
START_DAEMON="1"
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

#### :books: 參考網站：
- [gvpe](http://ftp.gnu.org/gnu/gvpe/)

---

```console
shell> apt-get install n2n
```

