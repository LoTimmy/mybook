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
{{alias}}

+forward-override{forward 127.0.0.1:8123}
+forward-override{forward-socks5 127.0.0.1:9050 proxy.example.org:8000}
```

#### :books: 參考網站：
- https://www.privoxy.org
- http://www.privoxy.org/user-manual/actions-file.html
- http://www.privoxy.org/user-manual/actions-file.html#FORWARD-OVERRIDE
