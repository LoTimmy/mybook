![OpenSSL](http://i.imgur.com/1Za6NhV.jpg)

<h3 id="newca"></h3>

### Create CA certificate {#newca}

```console
shell> mkdir ca
shell> cd ca
shell> vim openssl.cnf    
```

```
[ req ]
distinguished_name     = req_distinguished_name

[ req_distinguished_name ]
C                      = GB
ST                     = Test State or Province
L                      = Test Locality
O                      = Organization Name
OU                     = Organizational Unit Name
CN                     = Common Name
emailAddress           = test@email.address

[ ca ]
default_ca	= CA_default

[ CA_default ]
dir		= ./
new_certs_dir	  = $dir
unique_subject	= no
certificate     = $dir/ca-cert.pem
database        = $dir/index.txt
private_key     = $dir/ca-key.pem
serial          = $dir/serial
default_days    = 7300
default_md      = sha1
policy          = policy_anything
x509_extensions = usr_cert
crl		= $dir/crl.pem
crlnumber	= $dir/crlnumber
default_crl_days= 30

[ policy_anything ]
commonName              = supplied
stateOrProvinceName     = optional
countryName             = optional
emailAddress            = optional
organizationName        = optional
organizationalUnitName  = optional

[ usr_cert ]
basicConstraints=CA:true
subjectKeyIdentifier=hash
authorityKeyIdentifier=keyid:always
keyUsage = digitalSignature, keyEncipherment
extendedKeyUsage=clientAuth
```
```console
shell> touch index.txt
shell> echo 01 > serial
shell> echo 01 > crlnumber
```

- [creating-ssl-files-using-openssl](http://dev.mysql.com/doc/refman/5.7/en/creating-ssl-files-using-openssl.html)

### Generate a CRL {#gencrl} 

```console
shell> openssl ca -gencrl -out crl.pem -config openssl.cnf
```

- `憑證廢止清單` (`Certificate Revoke List`, `CRL`)
- `憑證`有多層防護機制，其中一個有效的方法就是啟動瀏覽器中的`憑證廢止清單`(`CRL`)功能。
`憑證`一旦遭到廢止，就會把廢止的標的資料加入`憑證廢止清單`(`CRL`)中，使用者使用瀏覽器瀏覽時，就會連上該伺服器驗證憑證是否持續有效，以及是否被登記在`憑證廢止清單`(`CRL`)中。
這種`憑證廢止清單`(`CRL`)的保護機制是相當即時的，但問題在於，有些瀏覽器為了加快瀏覽效率而會將此一功能關閉，造成瀏覽器以為該列入`廢止憑證清單`(`CRL`)的網站仍是有效，徒增系統被駭的風險。

---

### Creating a Private Key {#openssl_pkey_new}

`To generate a RSA key`

```console 
shell> openssl genrsa -out ca-key.pem 2048
```

###### To generate a password-protected RSA key

To generate a password-protected RSA key using [`triple DES`](http://zh.wikipedia.org/wiki/3DES) ★★
```console
shell> openssl genrsa -des3 -out ca-key.pem 2048
```
To generate a password-protected RSA key using [`AES` (`Advanced Encryption Standard`)](http://zh.wikipedia.org/wiki/高级加密标准) ★★★

```console
shell> openssl genrsa -aes256 -out ca-key.pem 2048
Generating RSA private key, 2048 bit long modulus
...+++
........................................+++
e is 65537 (0x10001)
Enter pass phrase for ca-key.pem:
Verifying - Enter pass phrase for ca-key.pem:

shell> openssl genrsa -aes256 -passout pass:mypass -out ca-key.pem 2048
Generating RSA private key, 2048 bit long modulus
..............+++
..........+++
e is 65537 (0x10001)
```
###### check_key
```console
shell> openssl rsa -in ca-key.pem -noout -check -passin pass:mypass
shell> openssl rsa -in ca-key.pem -noout -check
RSA key ok
```

###### Create some DSA parameters
```console
shell> openssl dsaparam -out dsaparam.pem 2048
```
###### To generate a DSA key using triple DES
```console
shell> openssl gendsa -des3 -out ca-key.pem dsaparam.pem
```

###### To remove the pass phrase on an RSA private key
```console
shell> openssl rsa -in ca-key.pem -out ca-key.pem
```

###### To encrypt a private key using triple DES
```console
shell> openssl rsa -in ca-key.pem -des3 -out ca-key.pem
```

###### To convert a private key from PEM to DER format
```console
shell> openssl rsa -in ca-key.pem -outform DER -out ca-key.der
```

---

###### 建立憑證要求 (Generates a CSR) 

```console
shell> openssl req -new -key ca-key.pem -out ca-req.pem -subj "/C=TW/ST=Taiwan/L=TPE/O=Example Company/OU=MYCA/CN=MYCA"
```
其中
- C = 國家
- ST = 州
- L = 地點
- O = 組織
- OU = 組織單位
- CN = 一般名稱

###### Convert a certificate to a CSR
```console
shell> openssl x509 -x509toreq -in ca-cert.pem -out ca-req.pem -signkey ca-key.pem
```

:bulb: 撇步
###### 產生一個2048-bit長度的「`私鑰`」 (`Private Key`)和「`憑證簽章要求`」 (`CSR`)
```console
shell> openssl req -new -newkey rsa:2048 -nodes -out ca-req.pem -keyout ca-key.pem -subj "/C=TW/ST=Taiwan/L=TPE/O=Example Company/OU=MYCA/CN=MYCA"
```

```console
shell> openssl req -new -newkey rsa:2048 -sha256 -nodes -out ca-req.pem -keyout ca-key.pem -subj "/C=TW/ST=Taiwan/L=TPE/O=Example Company/OU=MYCA/CN=MYCA"
```

---
###### Creating a Self-Signed Certificate

```console
shell> openssl genrsa -out server.key 2048
shell> openssl req -new -x509 -key server.key -out server.crt -days 7305 -subj "/CN=172.16.5.115"
shell> openssl pkcs12 -export -in server.crt -inkey server.key -out server.p12
```~~~~


```console
shell> openssl x509 -req -days 7305 -in ca-req.pem -signkey ca-key.pem -out ca-cert.pem
```~~~~
```console
shell> openssl x509 -req -days 7305 -sha1 -extfile openssl.cnf -extensions v3_ca -signkey ca-key.pem -in ca-req.pem -out ca-cert.pem
```
```console
shell> openssl req -new -x509 -days 7305 -key ca-key.pem -out ca-cert.pem -subj "/C=TW/ST=Taiwan/L=TPE/O=Example Company/OU=MYCA/CN=MYCA"
```
---

:bulb: 撇步
###### 產生一個2048-bit長度的`私鑰` (`Private Key`)和憑證
```console
shell> openssl req -x509 -new -nodes -out ca-cert.pem -newkey rsa:2048 -keyout ca-key.pem -days 7305 -subj "/C=TW/ST=Taiwan/L=TPE/O=Example Company/OU=MYCA/CN=MYCA"
```
```console
shell> openssl x509 -in ca-cert.pem -text -noout
shell> openssl x509 -in ca-cert.pem -subject -noout
shell> openssl x509 -in ca-cert.pem -issuer -noout
shell> openssl x509 -in ca-cert.pem -dates -noout
```

---

```console
shell> openssl x509 -noout -modulus -in ca-cert.pem | openssl md5
shell> openssl rsa -noout -modulus -in ca-key.pem | openssl md5
shell> openssl req -noout -modulus -in ca-req.pem | openssl md5
```

### Create server certificate
###### Generates a CSR

```console
shell> openssl req -new -newkey rsa:key_strength -nodes -out path_to_csr -keyout path_to_keyfile
```
其中
- key_strength 是以位元數測量的金鑰強度
- path_to_csr 是「`憑證簽章要求` (`CSR`)」的路徑

```console
shell> openssl req -newkey rsa:2048 -days 365 -nodes -keyout server-key.pem -out server-req.pem -subj "/C=TW/ST=Taiwan/L=TPE/O=Example Company/OU=MYCA/CN=server"
```

```console
shell> openssl rsa -in server-key.pem -text -noout
shell> openssl req -in server-req.pem -noout -text
shell> openssl req -in server-req.pem -noout -text -verify
```
---   
```console
shell> openssl x509 -req -in full_path_to_CSR -days number_of_days -CA path_to_ca_cert -CAkey path_to_ca_key -set_serial serial_no -out server-cert.pem
```

其中：
- number_of_days 是憑證的有效天數
- full_path_to_CSR 是「`憑證簽章要求` (`CSR`)」的完整路徑
- path_to_ca_cert 是 CA 憑證檔的路徑
- serial_no 是要使用的憑證序號

```console
shell> openssl x509 -req -in server-req.pem -days 3650 -CA ca-cert.pem -CAkey ca-key.pem -set_serial 01 -out server-cert.pem
```
```console
shell> openssl ca -batch -config openssl.cnf -notext -in server-req.pem -out server-cert.pem 
shell> openssl x509 -in server-cert.pem -text -noout
```
---
```console
shell> openssl ca -revoke 01.pem -config openssl.cnf 
shell> openssl crl -in crl.pem  -text -noout
```
--- 

##### 將 PEM 憑證轉換為 PKCS#12 格式
```console
shell> openssl pkcs12 -export -in server-cert.pem -inkey server-key.pem -out server.p12
shell> openssl pkcs12 -export -in server-cert.pem -inkey server-key.pem -out server.pfx -name name
```
```console
shell> openssl pkcs12 -in server.p12
```

##### 將 PKCS#12 憑證轉換為 PEM 格式
```console
shell> openssl pkcs12 -in server.pfx -nocerts -out server-key.pem -nodes  
shell> openssl pkcs12 -in server.pfx -nokeys -out server-cert.pem 

shell> openssl x509 -in server-cert.pem -out server.crt 
shell> openssl rsa -in server-key.pem -out server.key
```

### :books: 參考網站：

- [casecurity.ssllabs.com](https://casecurity.ssllabs.com/)
- [certs.godaddy.com](https://certs.godaddy.com/repository/)
- [installing-an-ssl-certificate-in-apache-centos-5238](https://uk.godaddy.com/help/installing-an-ssl-certificate-in-apache-centos-5238)
- [installing-an-ssl-certificate-in-microsoft-iis-7-4801](https://uk.godaddy.com/help/installing-an-ssl-certificate-in-microsoft-iis-7-4801)
- [pkcs7](https://www.openssl.org/docs/manmaster/apps/pkcs7.html)
- [pkcs12](https://www.openssl.org/docs/manmaster/apps/pkcs12.html)

----------
```console
shell> openssl req -newkey rsa:2048 -days 365 -nodes -keyout user.key -out user.csr -subj "/C=TW/ST=Taiwan/L=TPE/O=Example Company/OU=MYCA/CN=user"
```
```console
shell> openssl rsa -in user.key -text -noout
shell> openssl req -in user.csr -noout -text
```
```console
shell> openssl ca -batch -config openssl.cnf -notext -in user.csr -out user.crt
```
```console 
shell> openssl x509 -in user.crt -text -noout
```~~~~

##### 將 PEM 憑證轉換為 PKCS#12 格式
```console
shell> openssl pkcs12 -export -in user.crt -inkey user.key -out user.p12 -name user -chain -CAfile ca.crt
```
```console 
shell> openssl pkcs12 -in user.p12
```
----------

###### openssl_private_encrypt — Encrypts data with private key
```console
shell> echo HelloWorld | openssl rsautl -inkey private_key.pem -sign | openssl enc -base64 -out crypted
```
###### openssl_public_decrypt — Decrypts data with public key
```console
shell> openssl enc -base64 -d -in crypted | openssl rsautl -verify -inkey public_key.pem -pubin 
```

###### openssl_public_encrypt — Encrypts data with public key
```console
shell> echo HelloWorld | openssl rsautl -encrypt -inkey public_key.pem -pubin | openssl enc -base64 > crypted
``` 
###### openssl_private_decrypt — Decrypts data with private key
```console
shell> openssl enc -base64 -d -in crypted | openssl rsautl -inkey private_key.pem -decrypt
```
----------
```console
shell> openssl enc -des3 -e -a -in testfile.txt -out testfile.txt.enc
shell> openssl enc -des3 -d -a -in testfile.txt.enc -out testfile.txt

shell> openssl enc -aes-256-cbc -e -a -in testfile.txt -out testfile.txt.enc
shell> openssl enc -aes-256-cbc -d -a -in testfile.txt.enc -out testfile.txt
```
----------
##### 文件加密
使用2,048位元RSA和AES加密技術。
此種加密技術唯一解密方式即是取得RSA-2048私鑰，否則所有加密文件將會無法解開文件的加密。
「`加密`」(`Encryption`)、「`解密`」(`Decryption`)

###### 產生一組RSA-2048金鑰。
```console
shell> openssl genrsa -out private_key.pem 2048
shell> openssl rsa -in private_key.pem -pubout -out public_key.pem
```

###### 以一個隨機產生的256位元金鑰，針對檔案文件以AES-256 CBC對稱加密進行加密。
```console
shell> openssl rand -base64 32 > passwd.txt
shell> openssl enc -aes-256-cbc -salt -in testfile.txt -out testfile.txt.enc -pass file:passwd.txt
```
```console
shell> openssl rsautl -encrypt -inkey public_key.pem -pubin -in passwd.txt -out passwd.txt.enc
```
解密方式
```console
shell> openssl rsautl -decrypt -inkey private_key.pem -in passwd.txt.enc -out passwd.txt
shell> openssl enc -d -aes-256-cbc -in testfile.txt.enc -out testfile.txt -pass file:passwd.txt

shell> openssl dgst -sha1 -sign private_key.pem -out sign.txt testfile.txt    
shell> openssl dgst -sha1 -verify public_key.pem -signature sign.txt testfile.txt
Verified OK    
```
---
```console
shell> openssl list-message-digest-commands
shell> openssl list-cipher-commands
shell> openssl list-standard-commands
```

---

```console
shell> openssl rand -out testfile.txt -base64 $(( 1024**3 * 2 )) 
```
---

```console
shell> openssl s_client -connect servername:443
```

- [s_client](https://www.openssl.org/docs/manmaster/apps/s_client.html)

---

```console
shell> openssl rand -hex 10
```




- 安全漏洞`DROWN`是一個典型的`跨協定攻擊` (`cross protocol attack`)，這類的攻擊透過`SSLv2`協定漏洞去攻擊採用`TLS`協定的安全連結。駭客可藉機進行中間人攻擊，破解加密傳輸，讀取機密流量，涵蓋密碼、信用卡號碼或金融等資料。
- `DROWN的`全名為`Decrypting RSA with Obsolete and Weakened eNcryption`，指的是破解基於老舊及脆弱加密的`RSA`演算法，駭客利用特製的連結存取`SSLv2`伺服器就能截取並解密`TLS`流量。
- `DROWN`是一個典型的`跨協定攻擊` (`cross protocol attack`)，這類的攻擊透過`SSLv2`協定漏洞去攻擊採用`TLS`協定的安全連結，雖然`SSLv2`與`TLS`皆支援`RSA`加密，但`TLS`能夠防禦針對`RSA`加密的攻擊，`SSLv2`則否。
- `DROWN`的漏洞編號為`CVE-2016-0800`，而另兩個`OpenSSL`漏洞則會讓形勢更嚴重，這兩個`OpenSSL`編號分別是`CVE-2015-3197`與`CVE-2016-0703`。




[研究人員揭露重大的DROWN安全漏洞，全球1/3的HTTPS網站安全拉警報](http://www.ithome.com.tw/news/104246)

![Note](https://help.ubuntu.com/libs/admon/note.png)

- 「`心臟出血`」 (`Heartbleed`)是`OpenSSL`加密軟體的安全瑕疵，可能讓駭客神不知鬼不覺地竊取機密資料。
- 這個漏洞存在`OpenSSL`的TLS/DTLS 傳輸安全層的Heartbeat (心跳)擴充功能之中「**一個用來查詢OpenSSL運作是否正常的Heartbeat（心跳）機制上，就像是MIS用來查詢網站服務是否正常的Ping指令，Heartbeat也會回傳一段資料給查詢者。**」，該漏洞受到攻擊時會造成記憶體內容的外洩「**也許當時為了加快這個簡單指令的處理速度，而忘了限制回傳資料的長度，直接回傳64KB的內容給查詢者。但是，這個資料量遠超過了Heartbeat要提供的資料內容，導致系統會任意複製記憶體內其他資料，補足64KB內容回傳給查詢者，而外洩了不該提供的資料。因為在系統記憶體內的資料大多是沒有加密的真實資料，例如像是使用者帳號和密碼，甚至是交易資料、信用卡卡號等。**」，可能從伺服器端外洩到客戶端，或者由客戶端外洩到伺服器端，因此研究人員將它命名為Heartbleed Bug，`Heartbleed`也就是「心在淌血」的意思。
- 也就是說，當執行Heartbeat服務時，假設，如果原先只需回傳2KB的資料，但因為沒有事先確認原本所需資料的大小，當OpenSSL函式庫預設回傳64KB的資料，執行Heartbeat服務的伺服器就會把暫存在記憶體中其他62KB的資料，一併回傳。
- 「這是一個撰寫C語言時，不應該出現的基本程式設計錯誤。」這種確認欄位資料的檢查，其實是所有程式撰寫時的基本功夫，不論是有心或是無意導致這樣的漏洞，會導致Heartbeat預設回傳64KB資料時，造成網站機敏資料外洩。
- 更讓人擔心的是，因為外洩資料的過程都無從察覺也沒有記錄，對於多數使用有`Heartbleed`漏洞的`OpenSSL`來做網站或產品加密的企業和廠商，甚至無法評估過去有多少外洩資料被駭客攔截並再利用。

```console
shell> wget https://gist.githubusercontent.com/sh1n0b1/10100394/raw/4f24ff250124a03ad2d3d6010b6402c3a483d2f3/ssltest.py
shell> python ssltest.py login.yahoo.com
```
```console
shell> wget https://raw.githubusercontent.com/noxxi/p5-scripts/master/check-ssl-heartbleed.pl
shell> perl check-ssl-heartbleed.pl login.yahoo.com:443
```
---
![Note](https://help.ubuntu.com/libs/admon/note.png)

一般憑證有效期限為1至3年，視發行者而定，長度最低為40位元，假如要破解目前採用的1024位元RSA密鑰，在短時間內是完全不可能的，所以憑證的安全性是非常高的，但需留意私鑰的保管，這些檔案最好是不能連上網路的地方，例如儲存於磁片。

強制解除一般密碼時，若用高效能電腦花上一定時間就能解開，但特殊規格加密的資料就沒有這麼容易。以RSA-1024加密規格來說，目前一般家用電腦最少需要花費2000年才能解開，而動用日本超級電腦ES2的640個節點資源，找出RSA-1024密碼使用的解密金鑰，也要花上10年的時間。
因此，按照「`摩爾定律`」（`Moore's Law`）推算，RSA-1024的安全期限應該在2019年內，故此加密法應無安全疑慮。

---
- DES (Data Encryption Standard)
- 「憑證管理中心」 (Certificate Authority, CA)
- 「根憑證管理中心」 (Root CA)
- 「中繼憑證管理中心」 (Intermediate CA)
- 「X.509數位認證標準」 (X.509)

---
![](http://upload.wikimedia.org/wikipedia/commons/thumb/8/80/CBC_encryption.svg/601px-CBC_encryption.svg.png)
![](http://upload.wikimedia.org/wikipedia/commons/thumb/2/2a/CBC_decryption.svg/601px-CBC_decryption.svg.png)
---

- 在2010年時便傳出1024-bit的`SSL`金鑰遭到破解，「`美國國家標準技術研究所`」(`National Institute of Standards and Technology`, `NIST`)建議別再使用1024-bit的金鑰。
- 雖然金鑰長度愈長也愈安全，但難免會影響到服務的效能。
- 「`公開金鑰`」、「`私密金鑰`」 (`Public Key`、`Private Key`)
- 使用「`非對稱加密演算法`」，加密端及解密端會分別使用不同的金鑰。
- 這兩個金鑰一個稱之為「`公開金鑰`」 (`Public key`），簡稱「`公鑰`」；另一個稱為「`私密金鑰`」(`Private Key`) 簡稱「`私鑰`」。公鑰公諸大眾，私密金鑰則由擁有人自行保存。像`RSA`演算法就屬於非對稱加密演算法，**加密時用公開金鑰，解密時須搭配私密金鑰；以私密金鑰產生簽章，以公開金鑰驗證簽章**，而這兩金鑰就是一種非對稱金鑰。

---

**opensslui**

OPENSSL_UI_PATH 

C:\openssl

SSL Keys
![](http://opensslui.sourceforge.net/imgs/keys.png)

Certificate Signing Requests (CSR)
![](http://opensslui.sourceforge.net/imgs/csrreq.png)

Self Signed Certificates
![](http://opensslui.sourceforge.net/imgs/selfsigned.png)

Sign CSR
![](http://opensslui.sourceforge.net/imgs/csrsign.png)

PKCS 12 Utility
![](http://opensslui.sourceforge.net/imgs/pkcs12util.png)


### :books: 參考網站：
- [opensslui](http://opensslui.sourceforge.net/)

---


```console
shell> openssl req -x509 -nodes -newkey rsa:2048 -sha1 -keyout ca-key.pem -out ca-cert.pem -days 7305 -subj "/CN=172.16.7.103" -config openssl.cnf

shell> openssl req -newkey rsa:2048 -days 365 -nodes -keyout server-key.pem -out server-req.pem -subj "/CN=172.16.7.103"
shell> openssl x509 -req -in server-req.pem -days 7305 -CA ca-cert.pem -CAkey ca-key.pem -set_serial 101 -out server-cert.pem

```



### :books: 參考網站：
- [openssl](http://support.citrix.com/article/CTX135602)

---

### :books: 參考網站：

- [x509v3_config](https://www.openssl.org/docs/apps/x509v3_config.html)
- [配置單向 SSL 的伺服器憑證](https://publib.boulder.ibm.com/tividd/td/ITIM/SC32-1150-02/zh_TW/HTML/svrcfg45mst88.htm)
- [http://pic.dhe.ibm.com/infocenter/tivihelp/v53r1/index.jsp?topic=%2Fcom.ibm.lmt75.doc%2Fcom.ibm.license.mgmt.security.doc%2Ft_creating_certificate_ca_max.html&lang%3Dzh_TW](http://pic.dhe.ibm.com/infocenter/tivihelp/v53r1/index.jsp?topic=%2Fcom.ibm.lmt75.doc%2Fcom.ibm.license.mgmt.security.doc%2Ft_creating_certificate_ca_max.html&lang%3Dzh_TW)
- [善用加密技術，讓網路更為安全](http://www.ithome.com.tw/node/49651)
- [OpenSSL加密出包　全球網路安全淌血](http://www.ithome.com.tw/news/86879)
- [IT產品Heartbleed災情大清查](http://www.ithome.com.tw/news/86881)
- [連鎖都失效了，不換新怎會安全](http://www.ithome.com.tw/voice/86876)
- [全面解讀電子簽章法（三）](http://www.ithome.com.tw/node/14824)
- [http://zh.wikipedia.org/wiki/块密码的工作模式](http://zh.wikipedia.org/wiki/块密码的工作模式)
- [http://www.ithome.com.tw/news/89871](http://www.ithome.com.tw/news/89871)