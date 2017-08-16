```
shell> nsupdate
> update delete oldhost.example.com A
> update add newhost.example.com 86400 A 172.16.1.1
> send

shell> nsupdate
> prereq nxdomain nickname.example.com
> update add nickname.example.com 86400 CNAME somehost.example.com
> send
```

```
server 192.168.111.151
update delete oldhost.example.com A
update add newhost.example.com 86400 A 172.16.1.1
show
send
quit
```

```
shell> nsupdate nsupdate.commands
```

---

#### :books: 參考網站：
- [dns-configuration](https://help.ubuntu.com/lts/serverguide/dns-configuration.html)
- [nsupdate](http://docs.oracle.com/cd/E23824_01/html/821-1462/nsupdate-1m.html)
- [nsupdate BIND v9 examples](https://www.ibm.com/support/knowledgecenter/SSLTBW_1.13.0/com.ibm.zos.r13.halu101/f1a1c2a123.htm)
