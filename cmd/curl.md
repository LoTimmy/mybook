`curl - transfer a URL`


```console
shell> curl --version
curl 7.47.0 (x86_64-pc-linux-gnu) libcurl/7.47.0 GnuTLS/3.4.10 zlib/1.2.8 libidn/1.32 librtmp/2.3
Protocols: dict file ftp ftps gopher http https imap imaps ldap ldaps pop3 pop3s rtmp rtsp smb smbs smtp smtps telnet tftp 
Features: AsynchDNS IDN IPv6 Largefile GSS-API Kerberos SPNEGO NTLM NTLM_WB SSL libz TLS-SRP UnixSockets 
```

```console
shell> curl-config --protocols
DICT
FILE
FTP
FTPS
GOPHER
HTTP
HTTPS
IMAP
IMAPS
LDAP
LDAPS
POP3
POP3S
RTSP
SMB
SMBS
SMTP
SMTPS
TELNET
TFTP
```

```console
shell> curl -s --head http://127.0.0.1/

shell> if curl -s --head http://100.101.102.103/ | grep "200 OK" > /dev/null; then ; fi

shell> curl http://127.0.0.1/login?username=admin&password=secret

shell> curl -d "username=admin&password=secret" http://127.0.0.1/login
shell> curl -L -d "username=admin&password=secret" http://127.0.0.1/login

shell> curl -w "\n" -d '{"username":"admin", "password":"secret"}' -H "Content-Type: application/json" http://127.0.0.1/login 
```

```
-d, --data <data>
-H, --header <header>
-K, --config <config file>
-L, --location
-s, --silent
-S, --show-error
-f, --fail
```

```console
shell> curl -sSL https://get.docker.com/ | sh
shell> curl -fsSL https://experimental.docker.com/ | sh
shell> curl -L https://npmjs.com/install.sh | sh
```

```
# --- Example file ---
# this is a comment
url = "curl.haxx.se"
output = "curlhere.html"
user-agent = "superagent/1.0"

# and fetch another URL too
url = "curl.haxx.se/docs/manpage.html"
-O
referer = "http://nowhereatall.com/"
# --- End of example file ---
```

```
-H 'User-Agent: Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/55.0.2883.87 Safari/537.36' 
-H "Content-Type: application/json"
-H "Accept-Language: zh-TW"
```

```console
shell> curl -I https://httpd.apache.org/
```
```
HTTP/1.1 200 OK
Date: Thu, 16 Feb 2017 07:15:17 GMT
Server: Apache/2.4.7 (Ubuntu)
Last-Modified: Wed, 25 Jan 2017 14:38:55 GMT
ETag: "2551-546ec313cb061"
Accept-Ranges: bytes
Content-Length: 9553
Vary: Accept-Encoding
Content-Type: text/html
```

```console
shell> curl -I http://expressjs.com/
```
```
HTTP/1.1 200 OK
Date: Thu, 16 Feb 2017 07:16:38 GMT
Content-Type: text/html; charset=utf-8
Connection: keep-alive
Set-Cookie: __cfduid=da7a8ccccc54fc1e59546b6dab6f7211e1487229397; expires=Fri, 16-Feb-18 07:16:37 GMT; path=/; domain=.expressjs.com; HttpOnly
Last-Modified: Wed, 15 Feb 2017 17:39:30 GMT
Access-Control-Allow-Origin: *
Expires: Thu, 16 Feb 2017 07:26:38 GMT
Cache-Control: max-age=600
X-GitHub-Request-Id: 7774:7A03:113D903:16A02D5:58A551D6
Server: cloudflare-nginx
CF-RAY: 331f3719242653cc-LAX
```

```console
shell> curl -I -H "Accept-Encoding: deflate, gzip" https://httpd.apache.org/
```

```
HTTP/1.1 200 OK
Date: Wed, 08 Mar 2017 05:19:04 GMT
Server: Apache/2.4.7 (Ubuntu)
Last-Modified: Wed, 25 Jan 2017 14:38:55 GMT
ETag: "2551-546ec313cb061-gzip"
Accept-Ranges: bytes
Vary: Accept-Encoding
Content-Encoding: gzip
Content-Length: 2759
Content-Type: text/html
```

`.curlrc`

`_curlrc`

```
# --- Example file ---
# this is a comment
proxy = "http://127.0.0.1:8888"
url = "example.com"
output = "curlhere.html"
user-agent = "superagent/1.0"

# and fetch another URL too
url = "example.com/docs/manpage.html"
-O
referer = "http://nowhereatall.example.com/"
# --- End of example file ---
```


#### :books: 參考網站：
- [Accept-Encoding](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Accept-Encoding)
