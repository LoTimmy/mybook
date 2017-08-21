![](https://letsencrypt.org/images/letsencrypt-logo-horizontal.svg)

![Imgur](http://i.imgur.com/pEBGT1B.png)

`letsencrypt`

---

> `電子前線基金會` (`EFF`)、`Mozilla`、`Cisco`、`Akamai`、`IdenTrust`與密西根大學研究人員於2014年共同成立非營利組織「`網際網路安全研究小組`」 (`Internet Security Research Group, ISRG`)，隨後推出`Let's Encrypt`免費憑證服務，希望藉由簡化憑證的申請與部署，推動全球網站採用`HTTPS`加密傳輸。
> `Let's Encrypt`的用意在於推動網路的加密傳輸
> `Let's Encrypt`於2016年1月正式啟動
> `電子前線基金會` (`EFF`)、`Mozilla`、`Cisco`、`Akamai`、`IdenTrust`與密西根大學研究人員在2014年創立了非營利的`網際網路安全研究組織``Internet Security Research Group`(`ISRG`)，為了推動加密通訊而設立`Let's Encrypt`憑證組織，提供免費且自動化的憑證服務，並把原本需要耗時數小時的憑證申請流程縮短到30秒。



---

![](https://certbot.eff.org/images/certbot-logo-1A.svg)

```
shell> mkdir /opt/letsencrypt
shell> wget https://dl.eff.org/certbot-auto
shell> chmod a+x ./certbot-auto
shell> ./certbot-auto --help
shell> ./certbot-auto
shell> ./certbot-auto certonly --preferred-challenges --standalone-supported-challenges tls-sni-01 --register-unsafely-without-email --agree-tos -d example.com -d www.example.com -d other.example.net

shell> ./certbot-auto certonly --standalone-supported-challenges tls-sni-01 --register-unsafely-without-email --agree-tos -d example.com -d www.example.com -d other.example.net
shell> ./certbot-auto renew
```

```
shell> ./certbot-auto renew --standalone --pre-hook "service nginx stop" --post-hook "service nginx start"
```

```
shell> ./certbot-auto --apache -d example.com -d www.example.com -d other.example.net
shell> ./certbot-auto certonly --standalone --agree-tos --email admin@example.com -d example.com -d www.example.com -d other.example.net
```

```
shell> git clone https://github.com/certbot/certbot
shell> cd certbot
shell> ./certbot-auto --help
```


```
shell> openssl dhparam -out dhparam.pem 2048
```

```
shell> ./certbot-auto renew --dry-run
```

![Imgur](http://i.imgur.com/7hNAFJa.png)
![Imgur](http://i.imgur.com/3w8fptF.png)
![Imgur](http://i.imgur.com/szPIxbh.png)

#### :books: 參考網站：
- [renewing-certificates](https://certbot.eff.org/docs/using.html#renewing-certificates)

---

```
server {
	listen 443 ssl default_server spdy;
    listen 443 ssl http2;

	server_tokens off;


	ssl on;
	ssl_certificate /etc/letsencrypt/live/www.example.com/fullchain.pem;
	ssl_certificate_key /etc/letsencrypt/live/www.example.com/privkey.pem;
         
	ssl_dhparam /etc/ssl/private/dhparam.pem;

	#enables all versions of TLS, but not SSLv2 or 3 which are weak and now deprecated.
	ssl_protocols TLSv1 TLSv1.1 TLSv1.2;

	#Disables all weak ciphers
	ssl_ciphers "ECDHE-RSA-AES256-GCM-SHA384:ECDHE-RSA-AES128-GCM-SHA256:DHE-RSA-AES256-GCM-SHA384:DHE-RSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-SHA384:ECDHE-RSA-AES128-SHA256:ECDHE-RSA-AES256-SHA:ECDHE-RSA-AES128-SHA:DHE-RSA-AES256-SHA256:DHE-RSA-AES128-SHA256:DHE-RSA-AES256-SHA:DHE-RSA-AES128-SHA:ECDHE-RSA-DES-CBC3-SHA:EDH-RSA-DES-CBC3-SHA:AES256-GCM-SHA384:AES128-GCM-SHA256:AES256-SHA256:AES128-SHA256:AES256-SHA:AES128-SHA:DES-CBC3-SHA:HIGH:!aNULL:!eNULL:!EXPORT:!DES:!MD5:!PSK:!RC4";

	ssl_prefer_server_ciphers on;

	ssl_session_cache   shared:SSL:10m;
	ssl_session_timeout 10m;

	resolver 8.8.8.8;
	ssl_stapling on;
	ssl_stapling_verify on;
        
	#Enabling Strict Transport Security
	add_header Strict-Transport-Security "max-age=31536000; includeSubDomains; preload";
	add_header X-Frame-Options SAMEORIGIN;
	add_header Alternate-Protocol: 443:npn-spdy/3;
}
```

---

```
shell> sudo apt-get install letsencrypt 
shell> letsencrypt certonly --webroot -w /var/www/example -d example.com -d www.example.com -w /var/www/thing -d thing.is -d m.thing.is
shell> letsencrypt certonly --standalone -d example.com -d www.example.com
shell> letsencrypt renew --dry-run --agree-tos 
shell> letsencrypt renew --pre-hook "service nginx stop" --post-hook "service nginx start"
shell> letsencrypt renew 
```

---
#### :books: 參考網站：

- [letsencrypt](https://letsencrypt.org/)
- [certbot](https://github.com/certbot/certbot)
- [certbot](https://certbot.eff.org/docs/contributing.html)
- [](https://certbot.eff.org/#ubuntuxenial-haproxy)
