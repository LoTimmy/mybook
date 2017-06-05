<img src="http://i.imgur.com/3hIAdKc.png" width="150">

<img src="http://i.imgur.com/PTsVNBp.png" width="64">

`OpenVPN`

> 開放源碼的`OpenVPN`為全球最廣為使用的虛擬私有網路之一，它支援跨平台
> `OpenVPN`是透過`OpenSSL`加密庫中的SSLv3/TLSv1協議函數庫，建構企業內部`虛擬私有網路`，`OpenVPN`允許參與建立`VPN`的單點使用公開金鑰、電子證書或是帳戶／密碼來進行身分認證。它並不是一個Web-based的`VPN`軟體，也不與`IPsce`及其他`VPN`軟體相容，目前`OpenVPN`能夠在`Linux`、`FreeBSD`、`OpenBSD`、`Solaris`、`Mac OS X`與微軟的Windows 2000/XP/Vista/2003上運行。 
> `OpenVPN`預設採用`1194`埠做通訊，並且**推薦使用`UDP`協議，不過同時也支援`TCP`，使用者可以自己修改**。`OpenVPN`提供了`Tun`和`Tap`驅動兩種虛擬網路介面，透過它們可以建立`Layer3`的IP通道或是虛擬`Layer2`乙太網路，後者可以傳送任何類型的`Layer2`乙太網路封包，並可以使用`LZO演算法`壓縮。使用`Layer3`或`Layer2`時，使用者可以依自己的網路架構做選擇。 
> 在選擇使用`TCP`或`UPD`協議時，需要注意**如果有高延遲或是遺失封包較多的情況，建議選擇`TCP`協議作為底層傳輸的協定，因`UDP`協定為不可靠傳輸，網路不穩定時可能會導致要求通道上層的協議進行重傳，效率非常低**。 
> `OpenVPN`是基於`SSL` (`Secure Socket Layer`)進行資料加密傳輸。


安裝作業系統及`OpenVPN`相關套件。
因本文主要介紹`OpenVPN`如何安裝及設定，作業系統方面就不再詳述。

### 安裝 {#installing}

安裝`OpenVPN`套件。
```bash 
shell> apt-get install openvpn
```

切換至`/etc/openvpn`目錄下。
```bash
shell> cd /etc/openvpn
```
### Certificate Authority Setup
```bash
shell> cp -r /usr/share/doc/openvpn/examples/easy-rsa/2.0 ./easy-rsa
```

使用指令`vi vars`開始編輯`vars`檔。
```bash
shell> cd /etc/openvpn/easy-rsa/
shell> vi vars
```
```ini
export KEY_SIZE=2048
export CA_EXPIRE=3650

export KEY_COUNTRY="TW"
export KEY_PROVINCE="Taiwan"
export KEY_CITY="TPE"
export KEY_ORG="Example Company"
export KEY_EMAIL="steve@example.com"
export KEY_CN=MyVPN
export KEY_NAME=MyVPN
export KEY_OU=MyVPN
```
```bash
shell> ln -s openssl-1.0.0.cnf openssl.cnf
```
匯出 (Export) 剛剛所編輯的 vars 環境，使用「source vars」
```bash
shell> source vars
```
使用指令「./clean-all」清掉所有暫存的CA。
```bash
shell> ./clean-all
```
接著建置Root CA。使用指令「./build-ca」來執行此動作。
```bash 
shell> ./build-ca
```
---
### Server Certificates

執行指令「./build-key-server server」建置Server Key和Server Crt
```bash
shell> ./build-key-server server
```

---

接著建置「密鑰交換」Diffie-Hellman，執行指令「./build-dh」。
```bash
shell> ./build-dh
```
```bash
shell> cd keys/
shell> cp server.crt server.key ca.crt dh1024.pem /etc/openvpn/
```
---
### Client Certificates
shell> ./build-key client1

開始編輯設定檔。由於剛裝好的OpenVPN並沒有server.conf檔，使用者必須自行從範例檔複製
```bash
shell> cp /usr/share/doc/openvpn/examples/sample-config-files/server.conf.gz /etc/openvpn/
shell> gzip -d /etc/openvpn/server.conf.gz
shell> vi /etc/openvpn/server.conf
```

```
push "redirect-gateway def1"
plugin /usr/lib/openvpn/openvpn-auth-pam.so common-account
```

```bash
shell> iptables -t nat -A POSTROUTING -s 10.8.0.0/24 -o eth0 -j MASQUERADE
```
---
### 安裝 Google Authenticator (`兩步驟驗證`)
```bash
shell> wget https://google-authenticator.googlecode.com/files/libpam-google-authenticator-1.0-source.tar.bz2
shell> apt-get install  libpam0g-dev
```
```bash
shell> cd /etc/pam.d
shell> cp common-account openvpn
shell> vi openvpn
```
```
auth required /etc/openvpn/pam_google_authenticator.so
```
```bash
shell> vi /etc/openvpn/server.conf
```
```
plugin /usr/lib/openvpn/openvpn-auth-pam.so openvpn
```

---
```bash
shell> vim client.ovpn
```
```
client
dev tun
proto tcp

remote my-server-2 443
resolv-retry infinite
nobind

persist-key
persist-tun

<ca>
-----BEGIN CERTIFICATE-----
[...]
-----END CERTIFICATE-----
</ca>
<cert>
-----BEGIN CERTIFICATE-----
[...]
-----END CERTIFICATE-----
</cert>
<key>
-----BEGIN PRIVATE KEY-----
[...]
-----END PRIVATE KEY-----
</key>

ns-cert-type server
comp-lzo

verb 0

auth-user-pass mypassword.txt
auth-nocache

auth-user-pass
```

---

`openvpn.zip`

`C:\Program Files\OpenVPN\config`
`YOUR_SERVER_IP`
`ca.crt`
`VPNConfig.ovpn` 

```ini
dev tun
tls-client

remote YOUR_SERVER_IP 1194

# The "float" tells OpenVPN to accept authenticated packets from any address,
# not only the address which was specified in the --remote option.
# This is useful when you are connecting to a peer which holds a dynamic address
# such as a dial-in user or DHCP client.
# (Please refer to the manual of OpenVPN for more information.)

#float

# If redirect-gateway is enabled, the client will redirect it's
# default network gateway through the VPN.
# It means the VPN connection will firstly connect to the VPN Server
# and then to the internet.
# (Please refer to the manual of OpenVPN for more information.)

redirect-gateway def1

# dhcp-option DNS: To set primary domain name server address.
# Repeat this option to set secondary DNS server addresses.

#dhcp-option DNS DNS_IP_ADDRESS

pull

# If you want to connect by Server's IPv6 address, you should use
# "proto udp6" in UDP mode or "proto tcp6-client" in TCP mode
proto udp

script-security 2

comp-lzo

reneg-sec 0

auth-user-pass mypassword.txt
auth-nocache

<ca>
-----BEGIN CERTIFICATE-----
MIIDdTCCAl2gAwIBAgIJAOBnOMIz3wR1MA0GCSqGSIb3DQEBCwUAMFExCzAJBgNV
BAYTAlRXMQ8wDQYDVQQHDAZUYWlwZWkxFjAUBgNVBAoMDVN5bm9sb2d5IEluYy4x
GTAXBgNVBAMMEFN5bm9sb2d5IEluYy4gQ0EwHhcNMTYwOTEzMDcyMTAwWhcNMzYw
NTMxMDcyMTAwWjBRMQswCQYDVQQGEwJUVzEPMA0GA1UEBwwGVGFpcGVpMRYwFAYD
VQQKDA1TeW5vbG9neSBJbmMuMRkwFwYDVQQDDBBTeW5vbG9neSBJbmMuIENBMIIB
IjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAnpNSQgXXqAJ4rAtZ+HXQH5NW
kSBkfNVDwe/Whq/m4OwZTdkf5zGVNhzPJrs79lXSRyM7K/n8D3SIYFNzz024TnQa
dAR1k5+c4gkUOLiV+njTz7T3LLRKIHrKPtvST6fQRCK0wHiREFHXHS+v0QbnYgQj
rSl8or60GvsnaeTgCdudwaIyuDFI20fgOrCGDY+pDGlWY8gXM6Puj8kyNAf/RLY2
CWcpIdgkL2jUnULRKIwHtDBy2Dvq34ZfBKa03+tZDet4gh/rPlYDuBRYu3vnRadq
rvqbpBwGyvU+/Vx+Ahc2RelrR/qlemtl5NR1d4FHxpjEj89zPA8UZS8OlGcwJQID
AQABo1AwTjAdBgNVHQ4EFgQUkWAnEs0LgCwcZctxM0i7E6mk3qAwHwYDVR0jBBgw
FoAUkWAnEs0LgCwcZctxM0i7E6mk3qAwDAYDVR0TBAUwAwEB/zANBgkqhkiG9w0B
AQsFAAOCAQEAY/DQy/yovdS+aZJPUgI5cY+M1oy0AUBb7tcI19RsWuLcLEz6/qR1
Mr5HXKyCr6FxAE3fv8NX6cuPuoOy0DW5Fyq1EGXFe2e9xsKJ9jAJyANrYNS+jSK1
OKAlrdzCFkp1Llxy0ROClrPf6fcD0EtXlrA5HB5fU/6AJgRUQsSK3m/y6+VB1aBb
5aFZ7VQZBGGJyadHQorTgPEKXOlyDTskoOEsqMrSbRO6Yom68fRupKna7RS+gYOb
DFqCHX/3I2SqPpgLdNez1TZ5i8boll17sAauT3Sub/G1Z7vpsUfwKFvUbm6Fnncm
7+fqsz22Ii2+v2TRqmp5kdrgw0nHK/awxQ==
-----END CERTIFICATE-----
</ca>
```

---

```
dev tun
tls-client

remote YOUR_SERVER_IP 1194

# The "float" tells OpenVPN to accept authenticated packets from any address,
# not only the address which was specified in the --remote option.
# This is useful when you are connecting to a peer which holds a dynamic address
# such as a dial-in user or DHCP client.
# (Please refer to the manual of OpenVPN for more information.)

#float

# If redirect-gateway is enabled, the client will redirect it's
# default network gateway through the VPN.
# It means the VPN connection will firstly connect to the VPN Server
# and then to the internet.
# (Please refer to the manual of OpenVPN for more information.)

#redirect-gateway def1

# dhcp-option DNS: To set primary domain name server address.
# Repeat this option to set secondary DNS server addresses.

#dhcp-option DNS DNS_IP_ADDRESS

pull

# If you want to connect by Server's IPv6 address, you should use
# "proto udp6" in UDP mode or "proto tcp6-client" in TCP mode
proto tcp-client

script-security 2


comp-lzo

reneg-sec 0

auth-user-pass
<ca>
-----BEGIN CERTIFICATE-----
MIIDdTCCAl2gAwIBAgIJAOBnOMIz3wR1MA0GCSqGSIb3DQEBCwUAMFExCzAJBgNV
BAYTAlRXMQ8wDQYDVQQHDAZUYWlwZWkxFjAUBgNVBAoMDVN5bm9sb2d5IEluYy4x
GTAXBgNVBAMMEFN5bm9sb2d5IEluYy4gQ0EwHhcNMTYwOTEzMDcyMTAwWhcNMzYw
NTMxMDcyMTAwWjBRMQswCQYDVQQGEwJUVzEPMA0GA1UEBwwGVGFpcGVpMRYwFAYD
VQQKDA1TeW5vbG9neSBJbmMuMRkwFwYDVQQDDBBTeW5vbG9neSBJbmMuIENBMIIB
IjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAnpNSQgXXqAJ4rAtZ+HXQH5NW
kSBkfNVDwe/Whq/m4OwZTdkf5zGVNhzPJrs79lXSRyM7K/n8D3SIYFNzz024TnQa
dAR1k5+c4gkUOLiV+njTz7T3LLRKIHrKPtvST6fQRCK0wHiREFHXHS+v0QbnYgQj
rSl8or60GvsnaeTgCdudwaIyuDFI20fgOrCGDY+pDGlWY8gXM6Puj8kyNAf/RLY2
CWcpIdgkL2jUnULRKIwHtDBy2Dvq34ZfBKa03+tZDet4gh/rPlYDuBRYu3vnRadq
rvqbpBwGyvU+/Vx+Ahc2RelrR/qlemtl5NR1d4FHxpjEj89zPA8UZS8OlGcwJQID
AQABo1AwTjAdBgNVHQ4EFgQUkWAnEs0LgCwcZctxM0i7E6mk3qAwHwYDVR0jBBgw
FoAUkWAnEs0LgCwcZctxM0i7E6mk3qAwDAYDVR0TBAUwAwEB/zANBgkqhkiG9w0B
AQsFAAOCAQEAY/DQy/yovdS+aZJPUgI5cY+M1oy0AUBb7tcI19RsWuLcLEz6/qR1
Mr5HXKyCr6FxAE3fv8NX6cuPuoOy0DW5Fyq1EGXFe2e9xsKJ9jAJyANrYNS+jSK1
OKAlrdzCFkp1Llxy0ROClrPf6fcD0EtXlrA5HB5fU/6AJgRUQsSK3m/y6+VB1aBb
5aFZ7VQZBGGJyadHQorTgPEKXOlyDTskoOEsqMrSbRO6Yom68fRupKna7RS+gYOb
DFqCHX/3I2SqPpgLdNez1TZ5i8boll17sAauT3Sub/G1Z7vpsUfwKFvUbm6Fnncm
7+fqsz22Ii2+v2TRqmp5kdrgw0nHK/awxQ==
-----END CERTIFICATE-----
</ca>
```

- [使用Linux建置企業虛擬私有網路SSL VPN（上）](http://www.netadmin.com.tw/article_content.aspx?sn=1112270002)
- [使用Linux建置企業虛擬私有網路SSL VPN（下）](http://www.netadmin.com.tw/article_content.aspx?sn=1201120003)

---

<img src="https://tunnelblick.net/common/tb-icon-64x64.v1.png" >

`Tunnelblick`

### 安裝 {#installing}

下載並安裝 `Tunnelblick`。 您可以至下方連結下載最新版本。
https://tunnelblick.net/downloads.html


`openvpn.tblk`

`/Library/Application Support/Tunnelblick/Shared`
`~/Library/Application Support/Tunnelblick/Configurations`


#### :books: 參考網站：
- [tunnelblick](https://code.google.com/p/tunnelblick/)
- [Tunnelblick VPN Configurations Details](https://tunnelblick.net/cPkgs.html)
- [如何將您的設備連接到OpenVPN伺服器? (For Mac)](https://www.asus.com/tw/support/faq/1004472/)

---

`viscosity`

![](https://www.sparklabs.com/static/legacy/images/v2/page_viscosity/header_icon.png)

![](https://www.sparklabs.com/static/legacy/images/v2/page_viscosity/win_screenmini1_zoom.png)
![](https://www.sparklabs.com/static/legacy/images/v2/page_viscosity/win_screenmini2_zoom.png)
![](https://www.sparklabs.com/static/legacy/images/v2/page_viscosity/win_screenmini3_zoom.png)
![](https://www.sparklabs.com/static/legacy/images/v2/page_viscosity/win_screenmini4_zoom.png)
![](https://www.sparklabs.com/static/legacy/images/v2/page_viscosity/win_screenmini5_zoom.png)


#### :books: 參考網站：
- [viscosity](https://www.sparklabs.com/viscosity/)