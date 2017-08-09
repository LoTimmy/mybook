### 安裝 {#installing}

```console
shell> brew install privoxy
shell> apt-get install privoxy
```

`/usr/local/etc/privoxy`

`/usr/local/etc/privoxy/config`

`config`
```
forward-socks5t   /               127.0.0.1:9050 .

forward .youtube.com 127.0.0.1:8888

actionsfile user.action      # User customizations
```

```
forward .youtube.com 127.0.0.1:8888
forward .facebook.com 127.0.0.1:8888
forward .gitbook.com 127.0.0.1:8888

forward         192.168.*.*/     .
forward            10.*.*.*/     .
forward           127.*.*.*/     .

forward-socks5t .torproject.org 127.0.0.1:9050 .
forward-socks5t .onion 127.0.0.1:9050 .
```

```
permit-access  localhost

permit-access  192.168.45.64/26
deny-access    192.168.45.73    www.dirty-stuff.example.com
```

---

`config`

```
enable-edit-actions 0
```

`user.action`
```
{+block}
{+block +handle-as-image +set-image-blocker{}}
{+block +handle-as-image +set-image-blocker{https://placeholdit.imgix.net/~text?txtsize=75&txt=}}
https://s.yimg.com/cv/ae/tw/audience/070727/120x60246wpt7c2.jpg
```

- http://config.privoxy.org/
- http://config.privoxy.org/show-status
- http://config.privoxy.org/show-version
- http://config.privoxy.org/show-request
- http://config.privoxy.org/show-url-info
- http://config.privoxy.org/toggle
- http://config.privoxy.org/toggle?set=disable
- http://config.privoxy.org/toggle?set=enable

---

{{alias}}

+forward-override{forward .}
+forward-override{forward-socks5 127.0.0.1:9050 .}
{+forward-override{forward-socks5 127.0.0.1:12345 .}}
+forward-override{forward 127.0.0.1:8123}

---


```
{{alias}}

+forward-override{forward 127.0.0.1:8123}
+forward-override{forward-socks5 127.0.0.1:9050 proxy.example.org:8000}
```

#### :books: 參考網站：
- https://www.privoxy.org
- http://www.privoxy.org/user-manual/actions-file.html
- http://www.privoxy.org/user-manual/actions-file.html#FORWARD-OVERRIDE

---

```
shell> ssh -N -D 0.0.0.0:1080 matt@remotehost
```

```
Host remotehost
    User matt
    DynamicForward 0.0.0.0:1080
```

```
forward-socks5    /               127.0.0.1:1080 .
```

---
