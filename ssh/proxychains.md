**proxychains - proxy chains - redirect connections through proxy servers**

```
shell> apt-get install proxychains
shell> proxychains
```
```
dynamic_chain
strict_chain
random_chain
```
```
socks5	192.168.67.78	1080	lamer	secret
http	192.168.89.3	8080	justu	hidden
socks4	192.168.1.49	1080
http	192.168.39.93	8080
```

```
./proxychains.conf
$(HOME)/.proxychains/proxychains.conf
/etc/proxychains.conf
```
---

```
shell> ssh -N -D 0.0.0.0:1080 matt@remotehost
shell> ssh -f -N -D 0.0.0.0:1080 matt@remotehost
```

```
socks4	192.168.1.49	1080
```

```
shell> proxychains telnet targethost.com
```

---

#### :books: 參考網站：
- [proxychains](http://proxychains.sourceforge.net/)
