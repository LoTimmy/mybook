`curl - transfer a URL`

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
HTTP/1.1 200 OK
Date: Thu, 16 Feb 2017 07:15:17 GMT
Server: Apache/2.4.7 (Ubuntu)
Last-Modified: Wed, 25 Jan 2017 14:38:55 GMT
ETag: "2551-546ec313cb061"
Accept-Ranges: bytes
Content-Length: 9553
Vary: Accept-Encoding
Content-Type: text/html

shell> curl -I http://expressjs.com/
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