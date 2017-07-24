
```console
shell> tcpdump -i eth0 -w tcpdump.out -s 1520 port 80
shell> tcptrace tcpdump.out
shell> tcptrace -l -o1 tcpdump.out
shell> tcptrace -r -l -o1 tcpdump.out

shell> tcpdump -nn -i ethX host ip-addr
shell> tcpdump -nn port 25
shell> tcpdump -nn -X 'port 21'
shell> tcpdump -s 0 -A 'tcp dst port 80 and (tcp[((tcp[12:1] & 0xf0) >> 2):4] = 0x504f5354)'
shell> tcpdump -vvv -i ethX -s 0 -A host 104.20.24.138 or 104.20.25.138
```

#### :books: 參考網站：
- http://www.tcpdump.org/tcpdump_man.html


