`dig - DNS lookup utility`

`dnsutils - Clients provided with BIND`

### 安裝 {#installing}

```console
shell> apt-get install dnsutils
```

```console
shell> dig www.apple.com
shell> dig @8.8.8.8 www.apple.com
shell> dig +trace www.apple.com
shell> dig +trace A www.apple.com
shell> dig @8.8.8.8 +trace www.apple.com
shell> dig -x 8.8.8.8

shell> dig +short AAAA www.cloudflare.com
shell> dig +short myip.opendns.com @resolver1.opendns.com
shell> dig +short TXT yourdomain.com 

shell> dig apple.com any
shell> dig @8.8.8.8 apple.com 

shell> dig @8.8.8.8 -p 40 apple.com 

shell> dig ANY yourdomain.com
shell> dig AXFR yourdomain.com @xfrout1.dynect.net

shell> dig +nocmd +multiline +noall +answer ANY yourdomain.com
```

---

```
ns1.google.com
ns2.google.com
ns3.google.com
ns4.google.com
```
---

```
example.net.  TXT  "v=spf1 mx a:pluto.example.net include:aspmx.googlemail.com -all"
```

`https://dns.google.com/resolve?name=apple.com&type=ANY`

#### :books: 參考網站：
- https://diagnostic.opendns.com/myip
- https://dns.google.com/
- [use-dig-to-download-zone-data](https://help.dyn.com/use-dig-to-download-zone-data/)
- https://help.dyn.com/configure-provider-for-zone-transfer/
- [dig](https://toolbox.googleapps.com/apps/dig/)
- [SPF_Record_Syntax](http://www.openspf.org/SPF_Record_Syntax)
