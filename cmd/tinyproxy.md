`tinyproxy - A lightweight, non-caching, optionally anonymizing HTTP proxy`

### 安裝 {#installing}

```
shell> brew install arp-scan
shell> apt-get install tinyproxy
```

````
tcp        0      0 0.0.0.0:8888            0.0.0.0:*               LISTEN      672/tinyproxy
```   



`tinyproxy.conf`
```
Port 8888

Allow 127.0.0.1
Allow 192.168.0.0/16
Allow 172.16.0.0/12
Allow 10.0.0.0/8

AddHeader "X-My-Header" "Powered by Tinyproxy"
```

```
shell> curl https://tw.yahoo.com/ --proxy 127.0.0.1:8888 -k
shell> curl http://www.appledaily.com.tw/ --proxy 127.0.0.1:8888
```

#### :books: 參考網站：
- https://tinyproxy.github.io/

---

`dansguardian - Web content filtering`


```
shell> apt-get install dansguardian
```

