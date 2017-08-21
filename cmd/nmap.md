<img src="http://i.imgur.com/feKPiX8.png" alt="nmap" width=58 height=58>

---

![](http://i.imgur.com/brQgda0.png)

```
shell> nmap -A -T4 scanme.nmap.org

#TCP SYN scan
shell> nmap -sS -vv -P0 scanme.nmap.org
#TCP connect scan
shell> nmap -sT -vv -P0 scanme.nmap.org
#Xmas scan 
shell> nmap -sX -vv -P0 scanme.nmap.org
#Null scan 
shell> nmap -sN -vv -P0 scanme.nmap.org

shell> nmap --scanflags URGACKPSHRSTSYNFIN -vv -P0 scanme.nmap.org
shell> nmap --scanflags SYNRST -vv -P0 scanme.nmap.org

shell> nmap -sT -O localhost

shell> nmap -sS -vv -P0 -O scanme.nmap.org

shell> nmap -sT -P0 -F -O scanme.nmap.org
```

```
shell> nmap -sV --reason -PN -n --top-ports 100 scanme.nmap.org

shell> nmap --script=ssl-cert,ssl-enum-ciphers -p 443 scanme.nmap.org 
```

```
shell> nmap -sP 192.168.1.0/24
```
```
shell> nmap -sU --script nbstat.nse -p137 192.168.1.*
```

```
shell> nmap -sP -PR --packet-trace 192.168.31.0/24
shell> nmap -sP -PS --packet-trace --send-ip 192.168.31.0/24
```

```
shell> nmap --script broadcast-ping
```

```
shell> nmap -sV --script=http-php-version scanme.nmap.org
```
```
shell> nmap --script http-slowloris --max-parallelism 400 scanme.nmap.org
shell> nmap --script http-slowloris --max-parallelism 400 --script-args http.useragent="-" scanme.nmap.org  
```

```
shell> openssl s_client -connect scanme.nmap.org:443 
```

```
shell> nmap --script=ip-geolocation-maxmind scanme.nmap.org 
```

```
shell> nmap --script=vuln scanme.nmap.org 
```

```
shell> nmap -p 80 --script=http-backup-finder scanme.nmap.org
shell> nmap -p 80 --script=http-email-harvest scanme.nmap.org
shell> nmap -p 80 --script=http-brute scanme.nmap.org

shell> nmap --script http-headers -p80,8080 scanme.nmap.org
shell> nmap -sV --script=http-headers scanme.nmap.org 

shell> nmap --script=smb-brute -p445 scanme.nmap.org
shell> nmap -sU -sS --script=smb-brute -p U:137,T:139 scanme.nmap.org

shell> nmap --script ssh2-enum-algos scanme.nmap.org
shell> nmap --script ssh-hostkey scanme.nmap.org
```


```
shell> nmap -sP 192.168.42.0/24
```

```
/usr/share/nmap/scripts
```

`Nmap常用通訊埠掃描參數`
![](http://i.imgur.com/Kqagq4g.png)

#### :books: 參考網站：
- [掃port利器開外掛 輕鬆擴充nmap掃描能力](http://www.netadmin.com.tw/article_content.aspx?sn=1312030002&jump=2)
- [smb-brute](http://nmap.org/nsedoc/scripts/smb-brute.html)
- [http-headers](http://nmap.org/nsedoc/scripts/http-headers.html)
- [nbstat](https://nmap.org/nsedoc/scripts/nbstat.html)