![](http://www.postfix.org/mysza.gif)

---

```console
shell> apt-get install postfix 
shell> apt-get install procmail
shell> apt-get install dovecot-common dovecot-pop3d dovecot-imapd dovecot-postfix

shell> postalias hash:/etc/aliases
```

```
disable_plaintext_auth = no
```

```console
shell> dpkg-reconfigure postfix

shell> postconf
shell> postconf -m
shell> postconf -n

shell> postconf mail_version
shell> postconf myhostname
shell> postconf mydestination
```

```console
shell> postconf default_destination_concurrency_limit
shell> postconf default_destination_recipient_limit
shell> postconf default_process_limit
shell> postconf hash_queue_depth
```

```
smtpd_sender_restrictions = reject_unknown_sender_domain
smtpd_sender_restrictions = reject_unknown_sender_domain,
    check_sender_access hash:/etc/postfix/access
```

**The Spamhaus Block List**

**`SBL`**

```
myorigin = $myhostname
myorigin = $mydomain

accept_domain = test.net 
mydestination = $accept_domain

mydestination = $myhostname localhost.$mydomain localhost
mydestination = $myhostname localhost.$mydomain localhost $mydomain
mydestination = $myhostname localhost.$mydomain localhost www.$mydomain ftp.$mydomain

mynetworks_style = subnet
mynetworks_style = host

mynetworks = 172.168.96.0/24
mynetworks = 127.0.0.0/8
mynetworks = 127.0.0.0/8 168.100.189.2/32
mynetworks = 168.100.189.0/28, 127.0.0.0/8

masquerade_domains = $mydomain

relay_domains = $mydestination
relay_domains =
relay_domains = $mydomain
relay_domains = example.com, .example.com

relayhost =
relayhost = $mydomain
relayhost = [mail.$mydomain]
relayhost = [mail.isp.tld]

proxy_interfaces = 1.2.3.4

virtual_alias_domains = example.com ...other hosted domains...
virtual_alias_maps = hash:/etc/postfix/virtual
```

```
notify_classes = resource, software
```

```
postmaster@example.com postmaster
info@example.com       joe
sales@example.com      jane
```

```console
shell> postmap /etc/postfix/virtual
shell> postfix reload
```

#### :books: 參考網站：
- [Postfix Virtual Domain Hosting Howto](http://www.postfix.org/VIRTUAL_README.html)

```console
shell> postfix reload

shell> postfix check
shell> egrep '(reject|warning|error|fatal|panic):' /some/log/file 
 
```

#### :books: 參考網站：
- [BASIC_CONFIGURATION_README](http://www.postfix.org/BASIC_CONFIGURATION_README.html)

```
permit_mynetworks
permit_sasl_authenticated
```

```
message_size_limit (default: 10240000)
mydestination (default: $myhostname, localhost.$mydomain, localhost)
```

```console
shell> postconf -e 'myhostname = mail.example.com'
shell> postconf -e 'mydomain = example.com'
shell> postconf -e 'myorigin = $mydomain'

shell> postconf -e 'smtpd_banner = $myhostname ESMTP $mail_name'
shell> postconf -e 'smtpd_use_tls = no'
shell> postconf -e 'home_mailbox = Maildir/'
shell> postconf -e 'inet_protocols = ipv4'
shell> postconf -e 'smtpd_client_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_rbl_client zen.spamhaus.org'

shell> postconf -e 'message_size_limit = 0'
shell> postconf -e 'smtpd_recipient_limit = 1000'

shell> postconf -e 'append_dot_mydomain = no'
shell> postconf -e 'append_at_myorigin = no'

shell> postconf -e 'maximal_queue_lifetime = 0'
shell> postconf -e 'bounce_queue_lifetime = 0'

shell> postconf -e 'disable_vrfy_command = yes'
shell> postconf -e 'smtpd_helo_required = yes'

shell> service dovecot restart
shell> service postfix restart

shell> postqueue -d
shell> postsuper -d queue_id
shell> postsuper -d ALL
shell> postcat -q queue_id
```

---

```console
shell> apt-get install fetchmail
shell> vim ~/.fetchmailrc
```

```console
shell> grep sasl_method=LOGIN /var/log/mail.log
```

```console
shell> qshape -s hold | head
shell> qshape -s active
shell> qshape active
```

```console
shell> vim /etc/rsyslog.d/50-default.conf
```
```
mail.*                          -/dev/null
```

```
"protocol imap {
  mail_plugins = autocreate
}
plugin {
  autocreate = Trash
  autocreate2 = Spam
  #autocreate3 = ..etc..
  autosubscribe = Trash
  autosubscribe2 = Spam
  #autosubscribe3 = ..etc..
}
"
```
---

<img src="http://i.imgur.com/GHjoJiD.jpg" alt="" width=58 height=58>

### 服务器使用 SpamAssassin 防治垃圾邮件

> SpamAssassin 是免費的垃圾郵件篩選器
> SpamAssassin 是一个邮件过滤器，它部署在邮件服务器端，可以使用一系列的机制来确认垃圾邮件，这些机制包括：文本分析、Bayesian （贝叶斯判决规则）过滤、DNS 数据块列表，以及合作性的过滤数据库。
> SpamAssassin 包括 spamd 守护进程和 spamc 客户端。

- Headeranalysis (标题分析)：检查疑似垃圾邮件的标题，有些垃圾邮件被人采用某种技巧处理后，可能会被误认为是合法的电子邮件。
- Text analysis (文本分析)：检查电子邮件正文中的垃圾邮件特征。
- Blacklists (黑名单)：检查名单，看看发件人是否在现有垃圾邮件发送者列表中。
- Database (数据库)：检查针对 Vipul's Razor (razor.sourceforge.net) 的邮件签名，它是一个垃圾邮件跟踪数据库。


`sample-nonspam.txt.gz`

```console
shell> echo "hi there" | spamc
```

``` 
 X-Spam-Checker-Version: SpamAssassin 3.3.2-r929478 (2010-03-31) on sobell.com 
 X-Spam-Flag: YES 
 X-Spam-Level: ****** 
 X-Spam-Status: Yes, score=6.9 required=5.0 tests=EMPTY_MESSAGE,MISSING_DATE, 
 MISSING_HEADERS,MISSING_MID,MISSING_SUBJECT,NO_HEADERS_MESSAGE,NO_RECEIVED, 
 NO_RELAYS autolearn=no version=3.3.2-r929478 
 X-Spam-Report: 
 * -0.0 NO_RELAYS Informational: message was not relayed via SMTP 
 * 1.2 MISSING_HEADERS Missing To: header 
 * 0.1 MISSING_MID Missing Message-Id: header 
 * 1.8 MISSING_SUBJECT Missing Subject: header 
 * 2.3 EMPTY_MESSAGE Message appears to have no textual parts and no 
 * Subject: text 
 * -0.0 NO_RECEIVED Informational: message has no Received headers 
 * 1.4 MISSING_DATE Missing Date: header 
 * 0.0 NO_HEADERS_MESSAGE Message appears to be missing most RFC-822 
 * headers 
 hi there 
 Subject: [SPAM] 
 X-Spam-Prev-Subject: (nonexistent)
```

```console
shell> spamassassin --help

shell> spamassassin --test-mode < /usr/share/doc/spamassassin/examples/sample-nonspam.txt
shell> spamassassin --test-mode < /usr/share/doc/spamassassin/examples/sample-spam.txt

shell> mail -s "mail-tester" web-PDYtN2@mail-tester.com < /usr/share/doc/spamassassin/examples/sample-nonspam.txt
shell> mail -s "mail-tester" web-PDYtN2@mail-tester.com < /usr/share/doc/spamassassin/examples/sample-spam.txt

shell> spamc -R < /usr/share/doc/spamassassin/examples/sample-spam.txt

shell> sendmail root < /usr/share/doc/spamassassin/examples/sample-nonspam.txt
shell> sendmail root < /usr/share/doc/spamassassin/examples/sample-spam.txt
```

```console
shell> sa-learn --clear
shell> sa-learn --showdots --spam /home/spam/Maildir/{cur,new}
shell> sa-learn --dump magic
```

$HOME/.procmailrc
```
MAILDIR=$HOME/Mail


:0 c
* ^X-Spam-Status: Yes
.\&V4NXPpD1TvY-/     # 垃圾郵件

.Junk/
```

#### :books: 參考網站：
- [sample-nonspam.txt](http://spamassassin.apache.org/full/3.0.x/dist/sample-nonspam.txt)
- [sample-spam.txt](http://spamassassin.apache.org/full/3.0.x/dist/sample-spam.txt)
- [procmailrc](http://spamassassin.apache.org/full/3.0.x/dist/procmailrc.example)
- [透過Procmail連結Postfix伺服器與MySQL](http://www.netadmin.com.tw/article_content.aspx?sn=1304010005)

---


![Imgur](http://i.imgur.com/EMVHPdi.png)

```
mydomain.com.   3600    IN  TXT "v=spf1 mx mx:mydomain.com -all"
mydomain.com.   3600    IN  TXT "v=spf1 ip4:192.168.1.100 -all"
```

```
"+"	Pass
"-"	Fail
"~"	SoftFail
"?"	Neutral
```

```
"v=spf1 -all"
"v=spf1 a -all"
"v=spf1 a mx -all"
"v=spf1 +a +mx -all"
```

---

**opendkim-genkey - DKIM filter key generation tool**

```console
shell> apt-get install opendkim-tools
shell> opendkim-genkey -r -D -d mydomain.com
```
---

#### :books: 參考網站：
- [mail-tester](http://www.mail-tester.com/)

---


```console
shell> sa-update && /etc/init.d/spamassassin reload
```
---

`轉發` (`Relay`)

`DNS 黑名單` (`DNSBL`)

- `DNSBL` 是儲存網際網路`SMTP 主機記錄的資料庫，這些主機是已知的垃圾電子郵件來源或容許的第三者、開放式轉遞。

即時黑名單殺傷力很強，經常因誤攔合法信件頻率過高，遭致批評。因為大部分郵件伺服器軟體都支援RBL，當企業擁有的郵件伺服器IP或網域名稱被列入DNS的黑名單，企業寄送的任何信件，甚至SMTP連線，都可能被視為垃圾信行為，導致收件人無法收到信件。收到垃圾信，處理起來固然令人困擾，但是收件人無法順利接到信件，使得整個郵件系統形同停擺。

在黑名單榜上有名，除了歸咎於企業刻意主動發出大量信件，造成網路使用者的困擾外，被列入黑名單有時也可能是因為IT人員未注意伺服器的不當設定，例如Open Relay、Open Proxy，或是遭遇電腦病毒感染、網路入侵，在不知情的情況下發出大量垃圾信所致。

`Open Relay`
不限制信件轉發的來源就是`Open Relay`。發送垃圾郵件的人能利用網際網路上這些伺服器的`Open Relay`來傳送大批的訊息，以便偽裝真實的郵件來源進而隱藏自己的身分，讓無辜的企業成為「免費」、「匿名」傳送大量郵件的資源，增加無謂的郵件處理工作。

`Open Proxy`
`代理伺服器` (`Proxy Server`) 可透過HTTP連接任意的TCP埠，如果不限制連線來源的TCP埠或服務對象範圍，可能會被濫用，例如連至郵件伺服器的25埠作為中繼站，建立SMTP或Telnet等服務傳送特定指令，即可發出大量垃圾信，甚至攻擊內部網路。

各種即時黑名單組織各自採取不同封鎖立場和做法，例如`Spamhaus`提供2種黑名單，`SBL`分別針對垃圾郵件來源和已知垃圾郵件運作記錄的發信人，`XBL`專攻非法用途，包括Proxy、蠕蟲和木馬等；而Composite Blocking List不收集Open Relay名單，站方立場不提供支援資料或證據檔案，你無法詢問被列入的原因。

解除封鎖最簡單的方法是從網頁上直接解除，但大部分都需要寫信通知`RBL`管理者。`Spamhaus`的移除程序中提到，他們希望用戶主動聯繫`SBL`的工作人員，解釋企業解決垃圾郵件濫發的方法，如果處理完成，他們才會從`SBL`裡移除。

---

#### :books: 參考網站：
- [zen](https://www.spamhaus.org/zen/)
- [setup.dns](http://www.iredmail.org/docs/setup.dns.html)
- [SPF_Record_Syntax](http://www.openspf.org/SPF_Record_Syntax)
- [關於 DKIM](https://support.google.com/a/answer/174124?hl=zh-Hant)
- [啟動 SMTP 連線的 DNS 黑名單過濾程式](http://www.ibm.com/support/knowledgecenter/zh-tw/SSKTMJ_8.5.3/com.ibm.help.domino.admin85.doc/H_ENABLING_HOST_CHECKING_FOR_SMTP_CONNECTIONS_OVER.html)
- [當企業上了垃圾郵件黑名單](http://www.ithome.com.tw/node/31174)
- [大量寄件者指南](https://support.google.com/mail/answer/81126?hl=zh-Hant)
- [設定 MX 紀錄](https://support.google.com/a/answer/140034?hl=zh-Hant&ref_topic=2705493)
- [使用 DKIM 驗證電子郵件](https://support.google.com/a/answer/174124?hl=zh-Hant&ref_topic=2752442&rd=1)
- [LOCAL_RECIPIENT_README](http://www.postfix.org/LOCAL_RECIPIENT_README.html)
- https://opensource.apple.com/source/amavisd/amavisd-124/amavisd/amavisd-new-2.6.6/amavisd.conf-default

---

```
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases

canonical_maps = hash:/etc/postfix/canonical
check_recipient_access hash:/etc/postfix/recipient_access
check_sender_access hash:/etc/postfix/access

mynetworks = hash:/etc/postfix/network_table
mynetworks = cidr:/etc/postfix/network_table.cidr

postscreen_dnsbl_reply_map = texthash:/etc/postfix/dnsbl_reply

recipient_bcc_maps = hash:/etc/postfix/recipient_bcc
recipient_canonical_maps = hash:/etc/postfix/recipient_canonical
relay_recipient_maps = hash:/etc/postfix/relay_recipients
relocated_maps = hash:/etc/postfix/relocated

sender_canonical_maps = hash:/etc/postfix/sender_canonical
smtp_generic_maps = hash:/etc/postfix/generic
smtp_tls_policy_maps = hash:/etc/postfix/tls_policy


transport_maps = hash:/etc/postfix/transport

virtual_alias_maps = hash:/etc/postfix/virtual
```

```
alias_maps = hash:/etc/postfix/aliases            (local aliasing)
header_checks = regexp:/etc/postfix/header_checks (content filtering)
transport_maps = hash:/etc/postfix/transport      (routing table)
virtual_alias_maps = hash:/etc/postfix/virtual    (address rewriting)
```


`/etc/postfix/network_table.cidr`
```
192.168.1.1             OK
192.168.0.0/16          OK
```

```console
shell> postmap -q info@example.com hash:/etc/postfix/virtual
```

#### :books: 參考網站：
- [ADDRESS_REWRITING_README](http://www.postfix.org/ADDRESS_REWRITING_README.html)
- [canonical](http://www.postfix.org/canonical.5.html)
- [cidr_table](http://www.postfix.org/cidr_table.5.html)

---

Default user:	admin
Default password: 	secret

```
myserver.net.in.	3599	IN	TXT	"v=spf1 mx mx:ds1515.dyndns.info -all"
```

#### :books: 參考網站：
- [企业开源电子邮件系统安全保障实战精要: 第 2 部分，Postfix 安全防护实战及垃圾邮件防范](http://www.ibm.com/developerworks/cn/linux/1304_liyang_mailsecure2/)
- http://www.postfix.org/RESTRICTION_CLASS_README.html
- http://www.postfix.org/STANDARD_CONFIGURATION_README.html
- http://www.postfix.org/postconf.5.html#mydestination

---

```
Mar 17 03:25:54 mail imapd: LOGIN, user=bob, ip=[::ffff:192.168.8.205], port=[64109], protocol=IMAP
```
---

```
mailbox_command = /usr/bin/maildrop -d ${USER}
```

`/etc/letsencrypt/live/mail.example.com`

```
.
├── cert.pem -> ../../archive/mail.example.com/cert1.pem
├── chain.pem -> ../../archive/mail.example.com/chain1.pem
├── fullchain.pem -> ../../archive/mail.example.com/fullchain1.pem
├── privkey.pem -> ../../archive/mail.example.com/privkey1.pem
└── README

0 directories, 5 files
```

```console
shell> postconf -e 'smtpd_use_tls = yes'
shell> postconf -e 'smtpd_tls_auth_only = yes'
shell> postconf -e 'smtpd_tls_cert_file = /etc/letsencrypt/live/mail.example.com/fullchain.pem'
shell> postconf -e 'smtpd_tls_key_file = /etc/letsencrypt/live/mail.example.com/privkey.pem'
shell> postconf -e 'tls_random_source = dev:/dev/urandom'
shell> postconf -e 'smtpd_tls_received_header = yes'
shell> postconf -e 'smtp_use_tls = yes'
shell> postconf -e 'smtp_tls_note_starttls_offer = yes'
```


```console
shell> openssl req -new -newkey rsa:2048 -nodes -out server.csr -keyout server.key -subj "/C=TW/ST=Taiwan/L=Taipei/O=Microsoft Corp./CN=*.example.com"

shell> cat www_yourdomain_com.crt COMODORSADomainValidationSecureServerCA.crt COMODORSAAddTrustCA.crt > ssl-bundle.crt
```

```
smtpd_use_tls = yes
smtpd_tls_security_level = may
smtpd_tls_auth_only = no
smtpd_tls_cert_file = /etc/postfix/ssl/cert.pem
smtpd_tls_key_file = /etc/postfix/ssl/key.pem
smtpd_tls_CAfile = /etc/postfix/ssl/ssl-bundle.crt
smtpd_tls_session_cache_database = btree:/var/run/smtpd_tls_session_cache
smtpd_tls_received_header = yes
smtpd_tls_mandatory_ciphers = medium
smtpd_tls_mandatory_protocols = !SSLv2, !SSLv3
smtpd_tls_protocols = !SSLv2, !SSLv3
smtpd_tls_exclude_ciphers = EXP, MEDIUM, LOW, DES, 3DES, SSLv2
smtpd_tls_ciphers = high
smtpd_tls_loglevel = 1
smtpd_tls_session_cache_timeout = 3600s
smtpd_tls_dh1024_param_file = /etc/postfix/ssl/postfix.dh.param

tls_random_source = dev:/dev/urandom
tls_high_cipherlist = kEECDH:+kEECDH+SHA:kEDH:+kEDH+SHA:+kEDH+CAMELLIA:kECDH:+kECDH+SHA:kRSA:+kRSA+SHA:+kRSA+CAMELLIA:!aNULL:!eNULL:!SSLv2:!RC4:!MD5:!DES:!EXP:!SEED:!IDEA:!3DES
tls_medium_cipherlist = kEECDH:+kEECDH+SHA:kEDH:+kEDH+SHA:+kEDH+CAMELLIA:kECDH:+kECDH+SHA:kRSA:+kRSA+SHA:+kRSA+CAMELLIA:!aNULL:!eNULL:!SSLv2:!MD5:!DES:!EXP:!SEED:!IDEA:!3DES

smtp_tls_session_cache_database = btree:/var/run/smtp_tls_session_cache

smtp_use_tls = yes
smtp_tls_mandatory_protocols = !SSLv2, !SSLv3
smtp_tls_protocols = !SSLv2, !SSLv3
smtp_tls_exclude_ciphers = EXP, MEDIUM, LOW, DES, 3DES, SSLv2
smtp_tls_ciphers = high
```


#### :books: 參考網站：
- https://www.checktls.com/perl/TestReceiver.pl
- [Postfix TLS Support](http://www.postfix.org/TLS_README.html)
- https://access.redhat.com/articles/1468593


```console
shell> cat /etc/letsencrypt/live/mail.example.com/cert.pem /etc/letsencrypt/live/mail.example.com/chain.pem /etc/letsencrypt/live/mail.example.com/privkey.pem > combined.pem
```

```console
shell> cat /etc/letsencrypt/live/mail.example.com/privkey.pem /etc/letsencrypt/live/mail.example.com/cert.pem > /etc/courier/imapd.pem
shell> openssl dhparam 2048 >> /etc/courier/imapd.pem 
```



`/etc/courier/imapd-ssl`
```
SSLADDRESS=0.0.0.0

TLS_CERTFILE=/etc/courier/imapd.pem
TLS_CERTFILE=/etc/courier/combined.pem
```

`courier-imap-ssl`
`993`

```console
shell> service courier-imap-ssl restart
```
---


`/var/lib/amavis`
`/var/lib/amavis/virusmails`

---

`pflogsumm - Postfix log entry summarizer`

```console
shell> apt-get install pflogsumm
shell> pflogsumm -d yesterday /var/log/maillog
shell> pflogsumm -d today /var/log/maillog
```
---

`postfix-cluebringer - anti-spam plugin for Postfix`

---

`50-user`

```
$final_spam_destiny       = D_PASS;
$sa_spam_subject_tag = undef;
```
```
$final_virus_destiny      = D_DISCARD; # (defaults to D_BOUNCE)
$final_banned_destiny     = D_DISCARD;  # (defaults to D_BOUNCE)
$final_spam_destiny       = D_DISCARD;  # (defaults to D_REJECT)
$final_bad_header_destiny = D_PASS;  # (defaults to D_PASS), D_BOUNCE suggested
```

---

```
$HOME/.mailfilter
/etc/courier/maildroprc
$HOME/.mailfilters
```

#### :books: 參考網站：
- http://www.courier-mta.org/localmailfilter.html
- http://www.courier-mta.org/maildrop/maildropfilter.html

`$HOME/.mailfilter`
```
logfile maildrop.txt

if ( /^From: root@matc.tw/ )
{
  to "./Maildir/.Junk/."
}

if ( /^Subject:\s*test.*/ )
{
  to "./Maildir/.Trash/."
}
```

```
if ( /^To:\s*(.*)/ && lookup( $MATCH1, "badto.dat" ))
```

```
X-Spam-Flag: NO
X-Spam-Score: 5.18
X-Spam-Level: *****
X-Spam-Status: No, score=5.18 tagged_above=2 required=6.31

X-Spam-Flag: YES
X-Spam-Score: 999
X-Spam-Level: ****************************************************************
X-Spam-Status: Yes, score=999 tag=2 tag2=6.31 kill=6.31
```

```
amavis
CLEAN
BAD-HEADER-7
SPAM
```
```
ALL_TRUSTED
GTUBE
DYN_RDNS_SHORT_HELO_HTML
FSL_HELO_NON_FQDN_1
HTML_MESSAGE
HTML_MIME_NO_HTML_TAG
MIME_HTML_ONLY
MISSING_DATE
MISSING_MID
RDNS_DYNAMIC
TO_EQ_FM_DOM_SPF_FAIL
TO_EQ_FM_DIRECT_MX
SPF_FAIL
TO_EQ_FM_SPF_FAIL
```

```
autolearn=no
```
