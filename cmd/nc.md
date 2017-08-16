<img src="http://i.imgur.com/7YCFUSq.jpg" width="200">

----------
### nc
```

shell> nc -zv 
shell> nc -z -w 3 www.apple.com 80; echo $?

shell> nc -w 1 -z -u -v time.asia.apple.com 123
Connection to time.asia.apple.com 123 port [udp/ntp] succeeded!
```
```
shell> nc -zv www.apple.com 1-1000
shell> nc -w 1 -z -v www.apple.com 1-1000
nc: connect to www.apple.com port 1 (tcp) timed out: Operation now in progress
nc: connect to www.apple.com port 2 (tcp) timed out: Operation now in progress
nc: connect to www.apple.com port 3 (tcp) timed out: Operation now in progress
[...]
Connection to www.apple.com 80 port [tcp/http] succeeded!
```

```
shell> for i in {1..10}; do nc -w 1 -z -v 192.168.42.$i 22; done
Connection to 192.168.42.1 22 port [tcp/ssh] succeeded!
nc: connect to 192.168.42.2 port 22 (tcp) timed out: Operation now in progress
[...]
nc: connect to 192.168.42.7 port 22 (tcp) failed: Connection refused
```

```
shell> nc -vt www.apple.com 80
Connection to www.apple.com 80 port [tcp/http] succeeded!
GET / HTTP/1.1
User-Agent: WHttpTst Test Harness
Host: www.apple.com:80

HTTP/1.1 200 OK
Content-Type: text/html; charset=UTF-8
Cache-Control: max-age=165
Expires: Mon, 09 Feb 2015 12:36:33 GMT
Date: Mon, 09 Feb 2015 12:33:48 GMT
Content-Length: 8576
Connection: keep-alive
Server: Apache
```

```
shell> nc -l 3000
shell> echo 測試訊息 | nc 127.0.0.1 3000

shell> while true; do nc -l 3000; done
shell> while true; do nc -l 3000 < index.html ; done
```

```
shell> python -c 'print "<policy-file-request/>%c" % 0' | nc 127.0.0.1 843 
shell> perl -e 'printf "<policy-file-request/>%c",0' | nc 127.0.0.1 843         
```

```sh
#!/bin/bash
while true; do echo '<?xml version="1.0"?> 
<cross-domain-policy>
    <allow-access-from domain="*" to-ports="6000" />  
</cross-domain-policy>' | nc -l 843; done 
```

```
shell> /path/to/file/domainPolicyServer.sh > /dev/null &
```

---

`hping3 - Active Network Smashing Tool`

----------
#### :books: 參考網站：

- [Netcat](http://en.wikipedia.org/wiki/Netcat)
- [Netcat](http://nc110.sourceforge.net/)
- [http://help.adobe.com/en_US/as3/dev/WS5b3ccc516d4fbf351e63e3d118a9b90204-7c60.html](http://help.adobe.com/en_US/as3/dev/WS5b3ccc516d4fbf351e63e3d118a9b90204-7c60.html)
