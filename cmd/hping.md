
```
-F  --fin        set FIN flag
-S  --syn        set SYN flag
-R  --rst        set RST flag
-P  --push       set PUSH flag
-A  --ack        set ACK flag
-U  --urg        set URG flag
-1  --icmp       ICMP mode
-2  --udp        UDP mode
-i  --interval  wait (uX for X microseconds, for example -i u1000)
```

```
shell> brew install hping
shell> sudo hping host -i u10000 -1 -a 123.123.123.123
shell> sudo hping host -i u10000 -2 -a 123.123.123.123
shell> sudo hping host -i u10000 -S -a 123.123.123.123
shell> sudo hping host -i u10000 -S -F -a 123.123.123.123
shell> sudo hping host -i u10000 -S -F -R -P -A -U -a 123.123.123.123
shell> sudo hping host -i u1000

```

#### :books: 參考網站：
- [hping](http://www.hping.org/)
