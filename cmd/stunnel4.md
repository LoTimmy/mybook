### 在 `Ubuntu` 14.04 LTS 上建置 `stunnel4`

```console
shell> lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04 LTS
Release:	14.04
Codename:	trusty
```
### 安裝 stunnel4 
```console
shell> aptitude install stunnel4
```

```console
shell> openssl req -x509 -new -nodes -out stunnel-cert.pem \
 -newkey rsa:2048 -keyout stunnel-key.pem -days 7305 \
 -subj "/C=TW/ST=Taiwan/L=TPE/O=Example Company/OU=MYCA/CN=stunnel"
```

```console
shell> vim /etc/stunnel/stunnel.conf
```

```ini
pid = /var/run/stunnel4.pid
cert = /etc/stunnel/stunnel-cert.pem
key = /etc/stunnel/stunnel-key.pem
options = NO_SSLv2

[socks_server]
  accept = 3000
  connect = 8080
```

```console
shell> vim /etc/default/stunnel4
```

```ini
ENABLED=1
```

---
### 安裝 stunnel4 
```console
shell> aptitude install stunnel4
```

```console
shell> vim /etc/stunnel/stunnel.conf
```
```ini
pid = /var/run/stunnel4.pid
options = NO_SSLv2

[socks_client]
    client = yes
    accept = 3000
    connect = 127.0.0.1:8080
    verify = 4
```





### :books: 參考網站：

- [https://www.stunnel.org/docs.html](https://www.stunnel.org/docs.html)
- [https://www.stunnel.org/static/stunnel.html](https://www.stunnel.org/static/stunnel.html)
