- `PPTP`通訊協定因為簡單好用，所以很多企業至今仍在使用，其實只須配合適當的工具，要破解`PPTP`的帳號密碼，真的是輕而易舉。
- **`ARP Spoofing`是中間人攻擊的一種，它的原理很簡單，假設有A、B、C三個使用者，使用者C想要知道A與B談話的內容。因此使用者C告訴A使用者我是B，告訴B使用者我是A，然後告訴A來自B的訊息（當然是以B的身分告知），同樣地也告訴B來自A的訊息（當然是以A的身分告知）。因此，A跟B之間所有的訊息，C都會知道。**以網路觀念來說，它利用區域網路會進行廣播，把自己的`MAC Address`讓所有人知道的機制，搶先宣告自身的`ARP`資訊（`IP`與`MAC Address`的對映），例如C告訴A說B的`MAC Address`是AA.BB.CC.DD.EE.FF，但事實上AA.BB.CC.DD.EE.FF是C的`MAC Address`。C藉此去冒充B的身分，進行擷取封包甚至修改封包後再回傳給A。 

#### :books: 參考網站：
- [驗證駭客破解PPTP手法 驚見VPN帳密全都露](http://www.netadmin.com.tw/article_content.aspx?sn=1601040003)

---

### 在 `Ubuntu` 14.04 LTS 上建置 `pptpd`

安裝作業系統及`pptpd`相關套件。
因本文主要介紹`pptpd`如何安裝及設定，作業系統方面就不再詳述。

```
shell> lsb_release -a
```
```
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.3 LTS
Release:	14.04
Codename:	trusty
```

### 安裝 pptpd 
```
shell> sudo apt-get install pptpd
```

`/etc/pptpd.conf`

```
localip 192.168.0.1
remoteip 192.168.0.234-238,192.168.0.245
```

`/etc/ppp/pptpd-options`

```
nodefaultroute
ms-dns 10.0.0.1
```

`/etc/ppp/chap-secrets`

```
# client        server  secret                  IP addresses
VPNUser          pptpd   srj3J4boTP             *
```


net.ipv4.ip_forward=1


`/etc/modules`

```
nf_conntrack_pptp
nf_nat_pptp
```

