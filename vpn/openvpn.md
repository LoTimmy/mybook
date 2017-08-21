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
``` 
shell> apt-get install openvpn easy-rsa
```

切換至`/etc/openvpn`目錄下。
```bash
shell> cd /etc/openvpn
```

`/usr/share/easy-rsa`

```
build-ca  build-dh  build-inter  build-key  build-key-pass  build-key-pkcs12  build-key-server  build-req  build-req-pass  clean-all  inherit-inter  list-crl  openssl-0.9.6.cnf  openssl-0.9.8.cnf  openssl-1.0.0.cnf  pkitool  revoke-full  sign-req  vars  whichopensslcnf
```


### Certificate Authority Setup
```
shell> cp -r /usr/share/doc/openvpn/examples/easy-rsa/2.0 ./easy-rsa
```

使用指令`vi vars`開始編輯`vars`檔。
```
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
```
shell> ln -s openssl-1.0.0.cnf openssl.cnf
```
`匯出` (`Export`) 剛剛所編輯的 `vars` 環境，使用「`source vars`」
```
shell> source vars
```
使用指令「`./clean-all`」清掉所有暫存的`CA`。
```
shell> ./clean-all
```
接著建置`Root CA`。使用指令「`./build-ca`」來執行此動作。
``` 
shell> ./build-ca
```
---
### Server Certificates

執行指令「`./build-key-server server`」建置`Server Key`和`Server Crt`
```
shell> ./build-key-server server
```

---

接著建置「密鑰交換」Diffie-Hellman，執行指令「./build-dh」。
```
shell> ./build-dh
```
```
shell> cd keys/
shell> cp server.crt server.key ca.crt dh1024.pem /etc/openvpn/
```

```
shell> openssl dhparam -out dhparam.pem 2048
```


---
### Client Certificates
shell> ./build-key client1

開始編輯設定檔。由於剛裝好的OpenVPN並沒有server.conf檔，使用者必須自行從範例檔複製
```
shell> cp /usr/share/doc/openvpn/examples/sample-config-files/server.conf.gz /etc/openvpn/
shell> gzip -d /etc/openvpn/server.conf.gz
shell> vi /etc/openvpn/server.conf
```

```
push "redirect-gateway def1"
plugin /usr/lib/openvpn/openvpn-auth-pam.so common-account
```

```
shell> iptables -t nat -A POSTROUTING -s 10.8.0.0/24 -o eth0 -j MASQUERADE
```
---
### 安裝 Google Authenticator (`兩步驟驗證`)
```
shell> wget https://google-authenticator.googlecode.com/files/libpam-google-authenticator-1.0-source.tar.bz2
shell> apt-get install  libpam0g-dev
```
```
shell> cd /etc/pam.d
shell> cp common-account openvpn
shell> vi openvpn
```
```
auth required /etc/openvpn/pam_google_authenticator.so
```
```
shell> vi /etc/openvpn/server.conf
```
```
plugin /usr/lib/openvpn/openvpn-auth-pam.so openvpn
```

---
```
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

---

``` 
shell> apt-get install openvpn easy-rsa 
shell> apt-get install libpam-pwdfile apache2-utils
```

```
shell> openssl req -nodes -new -x509 -keyout ca.key -out ca.crt -days 3650 -subj "/CN=172.16.5.115"
shell> openssl req -nodes -new -x509 -keyout ca.key -out ca.crt -days 7305 -subj "/C=TW/L=Taipei/CN=172.16.5.115"
shell> openssl x509 -in ca.crt -text -noout

shell> openssl req -nodes -new -keyout server.key -out server.csr
shell> openssl req -nodes -new -keyout server.key -out server.csr -subj "/C=TW/L=Taipei/CN=172.16.5.115"
shell> openssl ca -out server.crt -in server.csr
shell> openssl x509 -in server.crt -text -noout
```

```
shell> openssl dhparam -out dh3072.pem 3072
```

```
push "route 192.168.88.0 255.255.255.0"
push "route 10.8.0.0 255.255.255.0"
dev tun

management 127.0.0.1 1195

server 10.8.0.0 255.255.255.0

dh /etc/openvpn/keys/dh3072.pem
ca /etc/openvpn/keys/ca.crt
cert /etc/openvpn/keys/server.crt
key /etc/openvpn/keys/server.key

max-clients 20

comp-lzo

persist-tun
persist-key

verb 3

log-append /var/log/openvpn.log

keepalive 10 60
reneg-sec 0

plugin /usr/lib/openvpn/openvpn-plugin-auth-pam.so openvpn
client-cert-not-required
username-as-common-name
duplicate-cn

status /tmp/ovpn_status_2_result 30
status-version 2
proto udp6
port 1194
cipher BF-CBC
auth SHA1
```

```
auth       required     pam_pwdfile.so pwdfile=/etc/openvpn/passwdfile
account    required     pam_permit.so

session    optional   pam_lastlog.so
```

```
shell> htpasswd -cd /etc/openvpn/passwdfile zeus
shell> htpasswd -d /etc/openvpn/passwdfile janedoe
```

```
-c     Create the passwdfile. If passwdfile already exists, it is rewritten and truncated. This option cannot be combined with the -n option.
-d     Use crypt() encryption for passwords.
```

``` 
shell> apt-get install sasl2-bin
shell> saslauthd -v
shell> saslauthd -a pam
saslauthd 2.1.26
authentication mechanisms: sasldb getpwent kerberos5 pam rimap shadow ldap

shell> testsaslauthd -u zeus -p blah -s openvpn
```

```
0: NO "authentication failed"
0: OK "Success."
```

#### :books: 參考網站：
- https://packages.ubuntu.com/en/trusty/amd64/libpam-pwdfile/filelist
- https://httpd.apache.org/docs/current/programs/htpasswd.html
- http://manpages.ubuntu.com/manpages/xenial/man1/htpasswd.1.html
- http://manpages.ubuntu.com/manpages/zesty/man8/pam_userdb.8.html
- http://docs.ansible.com/ansible/htpasswd_module.html
- `/usr/share/doc/libpam-pwdfile`
- http://www.netadmin.com.tw/article_content.aspx?sn=1110060001
- https://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html
- https://openvpn.net/index.php/open-source/documentation/miscellaneous/88-1xhowto.html



```
Certificate:
    Data:
        Version: 3 (0x2)
        Serial Number: 16169955393842119797 (0xe06738c233df0475)
    Signature Algorithm: sha256WithRSAEncryption
        Issuer: C=TW, L=Taipei, O=Synology Inc., CN=Synology Inc. CA
        Validity
            Not Before: Sep 13 07:21:00 2016 GMT
            Not After : May 31 07:21:00 2036 GMT
        Subject: C=TW, L=Taipei, O=Synology Inc., CN=Synology Inc. CA
        Subject Public Key Info:
            Public Key Algorithm: rsaEncryption
                Public-Key: (2048 bit)
                Modulus:
                    00:9e:93:52:42:05:d7:a8:02:78:ac:0b:59:f8:75:
                    d0:1f:93:56:91:20:64:7c:d5:43:c1:ef:d6:86:af:
                    e6:e0:ec:19:4d:d9:1f:e7:31:95:36:1c:cf:26:bb:
                    3b:f6:55:d2:47:23:3b:2b:f9:fc:0f:74:88:60:53:
                    73:cf:4d:b8:4e:74:1a:74:04:75:93:9f:9c:e2:09:
                    14:38:b8:95:fa:78:d3:cf:b4:f7:2c:b4:4a:20:7a:
                    ca:3e:db:d2:4f:a7:d0:44:22:b4:c0:78:91:10:51:
                    d7:1d:2f:af:d1:06:e7:62:04:23:ad:29:7c:a2:be:
                    b4:1a:fb:27:69:e4:e0:09:db:9d:c1:a2:32:b8:31:
                    48:db:47:e0:3a:b0:86:0d:8f:a9:0c:69:56:63:c8:
                    17:33:a3:ee:8f:c9:32:34:07:ff:44:b6:36:09:67:
                    29:21:d8:24:2f:68:d4:9d:42:d1:28:8c:07:b4:30:
                    72:d8:3b:ea:df:86:5f:04:a6:b4:df:eb:59:0d:eb:
                    78:82:1f:eb:3e:56:03:b8:14:58:bb:7b:e7:45:a7:
                    6a:ae:fa:9b:a4:1c:06:ca:f5:3e:fd:5c:7e:02:17:
                    36:45:e9:6b:47:fa:a5:7a:6b:65:e4:d4:75:77:81:
                    47:c6:98:c4:8f:cf:73:3c:0f:14:65:2f:0e:94:67:
                    30:25
                Exponent: 65537 (0x10001)
        X509v3 extensions:
            X509v3 Subject Key Identifier:
                91:60:27:12:CD:0B:80:2C:1C:65:CB:71:33:48:BB:13:A9:A4:DE:A0
            X509v3 Authority Key Identifier:
                keyid:91:60:27:12:CD:0B:80:2C:1C:65:CB:71:33:48:BB:13:A9:A4:DE:A0

            X509v3 Basic Constraints:
                CA:TRUE
    Signature Algorithm: sha256WithRSAEncryption
         63:f0:d0:cb:fc:a8:bd:d4:be:69:92:4f:52:02:39:71:8f:8c:
         d6:8c:b4:01:40:5b:ee:d7:08:d7:d4:6c:5a:e2:dc:2c:4c:fa:
         fe:a4:75:32:be:47:5c:ac:82:af:a1:71:00:4d:df:bf:c3:57:
         e9:cb:8f:ba:83:b2:d0:35:b9:17:2a:b5:10:65:c5:7b:67:bd:
         c6:c2:89:f6:30:09:c8:03:6b:60:d4:be:8d:22:b5:38:a0:25:
         ad:dc:c2:16:4a:75:2e:5c:72:d1:13:82:96:b3:df:e9:f7:03:
         d0:4b:57:96:b0:39:1c:1e:5f:53:fe:80:26:04:54:42:c4:8a:
         de:6f:f2:eb:e5:41:d5:a0:5b:e5:a1:59:ed:54:19:04:61:89:
         c9:a7:47:42:8a:d3:80:f1:0a:5c:e9:72:0d:3b:24:a0:e1:2c:
         a8:ca:d2:6d:13:ba:62:89:ba:f1:f4:6e:a4:a9:da:ed:14:be:
         81:83:9b:0c:5a:82:1d:7f:f7:23:64:aa:3e:98:0b:74:d7:b3:
         d5:36:79:8b:c6:e8:96:5d:7b:b0:06:ae:4f:74:ae:6f:f1:b5:
         67:bb:e9:b1:47:f0:28:5b:d4:6e:6e:85:9e:77:26:ef:e7:ea:
         b3:3d:b6:22:2d:be:bf:64:d1:aa:6a:79:91:da:e0:c3:49:c7:
         2b:f6:b0:c5
```

```
Certificate:
    Data:
        Version: 1 (0x0)
        Serial Number: 12750406713119902201 (0xb0f28b59dd4489f9)
    Signature Algorithm: sha256WithRSAEncryption
        Issuer: C=TW, L=Taipei, O=Synology Inc., CN=Synology Inc. CA
        Validity
            Not Before: Sep 13 07:21:01 2016 GMT
            Not After : May 31 07:21:01 2036 GMT
        Subject: C=TW, L=Taipei, O=Synology Inc., CN=synology.com
        Subject Public Key Info:
            Public Key Algorithm: rsaEncryption
                Public-Key: (2048 bit)
                Modulus:
                    00:cc:34:5b:50:ac:ee:db:cb:89:09:43:74:a2:ab:
                    4b:e8:ce:08:be:98:96:5c:98:fb:fb:15:dd:e4:82:
                    08:74:bc:7b:f6:11:f7:ab:8a:b3:2d:45:7d:11:b7:
                    63:09:68:a3:6a:d7:89:2f:6b:c2:23:85:78:56:25:
                    3f:e1:b5:9e:7c:26:50:78:6b:b6:3d:76:e7:47:3a:
                    57:03:3a:b8:fb:cf:1f:d7:e8:c5:ba:4a:50:b2:2a:
                    10:e2:63:63:16:8d:79:2d:4b:d1:55:83:88:c8:fb:
                    16:78:79:2d:65:cc:91:63:53:0f:a0:e0:91:88:20:
                    b1:d7:e6:e6:64:6a:ac:e1:45:fa:29:44:ff:60:7b:
                    9e:ef:d4:10:0b:d0:bb:d6:d6:42:7b:50:f4:bd:7b:
                    cd:87:13:f9:e3:96:90:c2:25:d9:18:ec:cf:7e:9d:
                    0d:c9:f0:53:f7:2e:c1:d3:6e:6a:99:9d:c5:d4:4f:
                    2e:a2:c7:4b:6b:98:39:8c:42:c5:c3:55:77:c9:31:
                    fb:fa:a8:9b:65:86:a8:53:9a:7e:52:ca:ed:9f:bb:
                    45:e7:6f:24:05:a0:1f:b4:85:65:74:c1:bf:8d:7f:
                    c3:51:97:fa:60:33:d8:8e:b0:b7:97:11:f2:d1:ef:
                    1a:53:b6:67:eb:f9:00:27:6e:0d:0d:ba:df:3d:95:
                    50:67
                Exponent: 65537 (0x10001)
    Signature Algorithm: sha256WithRSAEncryption
         97:fb:68:22:fe:00:9a:ed:b3:ee:63:ec:3c:d0:74:60:8e:a0:
         b0:58:44:70:48:49:88:4c:0d:f5:34:e2:be:ce:c6:6f:a9:1e:
         f3:08:9e:f6:2c:5c:7d:5e:a6:45:32:dc:87:79:3d:ca:a9:35:
         39:0b:1a:e4:27:65:63:cc:7d:d7:8d:5a:34:68:53:24:54:71:
         d0:24:11:ed:0f:5b:ef:ba:e3:12:a2:bb:7b:12:26:0c:11:bd:
         e3:19:4f:10:e7:4a:60:29:e4:6d:ec:ea:16:c5:d2:33:49:c4:
         7f:a2:0d:dd:15:34:db:b8:9b:61:f0:15:83:1c:8e:52:37:b8:
         d7:1a:72:d4:04:93:68:90:3b:a1:33:83:ed:11:49:83:b4:1b:
         f4:83:37:58:a7:47:5e:a2:60:8b:fe:66:d6:dd:fe:f9:8b:70:
         e7:a0:2b:5c:df:8d:17:b0:c1:21:de:0c:15:3c:22:a3:58:58:
         d0:0d:69:e6:1e:0a:1c:35:12:fb:d0:46:8c:d8:cd:f3:a7:b1:
         72:76:b9:55:f0:bf:df:91:7f:19:fe:b7:7c:f9:a2:7d:3a:88:
         c7:28:be:fa:5f:3b:46:29:06:69:b6:6b:95:c0:97:00:8d:45:
         bb:8c:8d:0b:4a:17:6a:a3:dc:db:51:68:05:07:7e:f7:83:34:
         0b:55:6c:18
```
