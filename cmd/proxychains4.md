
```console
shell> brew install proxychains-ng
```

`/usr/local/etc/proxychains.conf`
```
strict_chain
proxy_dns
socks4  127.0.0.1 9050
```

```console
shell> proxychains4 -f /etc/proxychains-other.conf telnet targethost2.com
shell> proxychains4 curl -s https://api.ipify.org
```

```
[proxychains] config file found: /usr/local/etc/proxychains.conf
[proxychains] preloading /usr/local/Cellar/proxychains-ng/4.12_1/lib/libproxychains4.dylib
[proxychains] DLL init: proxychains-ng 4.12
[proxychains] Dynamic chain  ...  127.0.0.1:9050  ...  127.0.0.1:8888 <--socket error or timeout!
```

`.curlrc`
```
# proxy = "http://127.0.0.1:8888"
```

```console
shell> proxychains4 curl -s https://api.ipify.org
```
```
[proxychains] config file found: /usr/local/etc/proxychains.conf
[proxychains] preloading /usr/local/Cellar/proxychains-ng/4.12_1/lib/libproxychains4.dylib
[proxychains] DLL init: proxychains-ng 4.12
[proxychains] Dynamic chain  ...  127.0.0.1:9050  ...  api.ipify.org:443  ...  OK
51.15.48.253
```

```console
shell> proxychains4 ssh 36.231.79.221
```

---

```
Usage:	proxychains4 -q -f config_file program_name [arguments]
	-q makes proxychains quiet - this overrides the config setting
	-f allows one to manually specify a configfile to use
	for example : proxychains telnet somehost.com
More help in README file
```

- https://github.com/rofl0r/proxychains-ng
- https://support.apple.com/en-us/HT204899
- https://support.apple.com/zh-tw/HT204899
