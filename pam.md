- `可插入式認證模組`（`Pluggable Authentication Module`，`PAM`）廣泛應用在網路服務的認證系統上，角色就類似於使用者與應用程式的中介，使用者須經由`PAM`認證程序通過後，方可使用相關的應用程式。
- 一般在`Linux`系統上都是利用輸入使用者帳號以及密碼等相關資訊來進行身分認證，例如要登入`Linux`系統時，必須提供使用者名稱和密碼，而後登入程序才能根據使用者所給的名稱和密碼來確認是否為合法的帳號。
- 如果企業要導入`SSO`（`Single Sing On`，`單一簽入入口`），此種驗證方式一般都需要向遠方的`LDAP`認證主機來查詢相關的認證資訊，此種認證型式勢必要重新編譯相關的程序。也就是，在一般傳統的認證程序中均能針對個別的認證型式進行處理，若改用不同的認證方式，則必須重新編譯相關進行認證的程序。
- 那麼是否能有一個比較彈性的機制，只透過設定組態檔的方式就能夠指定應用程式採用那種驗證方式（甚至可指定多重驗證，即一個應用程式可指定多種的認證方式），而不必重新編譯相關的程序？`PAM`機制即是此類具有彈性的機制，它允許系統管理員利用設定組態檔的方式來動態指定應用程式可使用那些認證方式，而不必再重新編譯要進行認證的程序。使用`PAM`認證模組時，使用者只需要編輯一個配置文件，就可以決定認證模組要如何嵌入應用程式中。
- `PAM`模組設定資訊位於「`/etc/pam.d`」目錄下，該目錄下的各個檔案名稱即為服務名稱，例如`login`即為`login`服務設定的相關資訊。 
 
`PAM`設定了如下四種的認證模組類型： 

`auth`：對使用者所提供的認證資訊進行驗證，例如**檢查帳號密碼是否為有效的使用者**。 
`account`：檢查非認證方面的帳號管理，例如**檢查使用者帳號是否已過期、哪些帳號可從哪些來源端來存取服務或限定存取服務的時間等等**。 
`password`：與更新認證訊息有關，例如**使用者變更密碼時會檢查新密碼是否夠安全**。 
`session`：這個模組類型裡所使用的模組，是與使用者在存取服務前後需要執行的一些工作有關聯，例如**紀錄掛載目錄的資訊等等相關資訊**。 

當`PAM`執行模組驗證成功或失敗之後所須執行的動作，`PAM`指定下列控制符號來進行模組驗證成功或失敗之後的動作： 

`required`：**當認證模組驗證成功時即執行模組所定義的情況，而當模組驗證失敗的時候，如果使用者有設定其他的認證模組，即繼續執行其另外定義的認證模組**。 
`requisite`：**如果認證模組驗證失敗，即直接回覆失敗的訊息，而不再繼續執行其他的認證模組**。 
`sufficient`：**如果這個模組驗證成功，則不執行後面的認證模組，但如果之前已設定Required的認證模組，則此模組的結果將會被忽略**。 



#### :books: 參考網站：
- [透過pam_mysql模組連接資料庫  為PAM認證系統建立帳號管理機制](http://www.netadmin.com.tw/article_content.aspx?sn=1110060001)

```console 
shell> apt-get install libpam-pwdfile apache2-utils
```

```
auth       required     pam_pwdfile.so pwdfile=/etc/openvpn/passwdfile
account    required     pam_permit.so
```

```console
shell> htpasswd -cd /etc/openvpn/passwdfile zeus
```

```
-c     Create the passwdfile. If passwdfile already exists, it is rewritten and truncated. This option cannot be combined with the -n option.
-d     Use crypt() encryption for passwords.
```
---

```console 
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

---

`pam_tally2.so`
`pam_tally2`

`/lib/x86_64-linux-gnu/security/pam_tally2.so`

`/sbin/pam_tally2`

```
auth       required     pam_tally2.so deny=3 unlock_time=5 even_deny_root root_unlock_time=10
auth     required       pam_tally2.so deny=4 even_deny_root unlock_time=1200
```

```console 
shell> pam_tally2 --user janedoe
shell> pam_tally2 --user janedoe --reset
shell> faillog -r
```

---


```
libpam-pwdfile - PAM module allowing authentication via an /etc/passwd-like file
libpam-google-authenticator - Two-step verification
libpam-geoip - PAM module checking access of source IPs with a GeoIP database
libpam-pwquality - PAM module to check password strength
libpam-radius-auth - The PAM RADIUS authentication module
libpam-mysql - PAM module allowing authentication from a MySQL server
```

`/lib/x86_64-linux-gnu/security`
```
pam_access.so  pam_echo.so  pam_extrausers.so  pam_ftp.so    pam_keyinit.so  pam_listfile.so   pam_mail.so       pam_namespace.so  pam_pwdfile.so    pam_rootok.so     pam_sepermit.so  pam_succeed_if.so  pam_tally.so      pam_tty_audit.so  pam_userdb.so  pam_xauth.so
pam_debug.so   pam_env.so   pam_faildelay.so   pam_group.so  pam_lastlog.so  pam_localuser.so  pam_mkhomedir.so  pam_nologin.so    pam_pwhistory.so  pam_securetty.so  pam_shells.so    pam_systemd.so     pam_time.so       pam_umask.so      pam_warn.so
pam_deny.so    pam_exec.so  pam_filter.so      pam_issue.so  pam_limits.so   pam_loginuid.so   pam_motd.so       pam_permit.so     pam_rhosts.so     pam_selinux.so    pam_stress.so    pam_tally2.so      pam_timestamp.so  pam_unix.so       pam_wheel.so

```


```
plugin lib/radiusplugin.so /etc/openvpn/radiusplugin.cnf
```

`radiusplugin.cnf`
```
NAS-Identifier=OpenVpn
Service-Type=5
Framed-Protocol=1
NAS-Port-Type=5
NAS-IP-Address=127.0.0.1
OpenVPNConfig=/usr/syno/etc/packages/VPNCenter/openvpn/openvpn.conf
subnet=255.255.255.0
overwriteccfiles=true
server
{
	acctport=31068
	authport=31067
	name=127.0.0.1
	retry=1
	wait=5
	sharedsecret=4synovpn
}
```


```
/lib/x86_64-linux-gnu/security/pam_tally2.so
```

```
auth       optional     pam_mysql.so user=root passwd=password
account    required     pam_mysql.so user=root passwd=password
```

```
SELECT ENCRYPT('mypass'), PASSWORD('mypass'), MD5('mypass');
```



```
account
auth
sufficient
requisite
required
optional
```
```
pam_rootok.so
pam_shells.so
pam_mysql.so
pam_unix.so
pam_deny.so
pam_permit.so
pam_umask.so
pam_systemd.so
```
shell> apt-get install libpam-mysql libmysql++-dev libpam0g-dev

#### :books: 參考網站：
- http://manpages.ubuntu.com/manpages/wily/man8/pam_tally2.8.html
- http://manpages.ubuntu.com/manpages/zesty/man8/pam_userdb.8.html
- https://dev.mysql.com/doc/refman/5.7/en/pam-pluggable-authentication.html
- https://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/pam.html

<!--


https://support.asperasoft.com/hc/en-us/articles/216127348-Getting-PAM-to-authenticate-against-MySQL

auth optional pam_mysql.so user=登入mysql的帳號 passwd=登入mysql的密碼 host=localhost db=你的db table=你的table usercolumn=table中的使用者欄位名稱 passwdcolumn=table中的密碼欄位名稱 crypt=1 sqllog=0 
account required pam_mysql.so user=登入mysql的帳號 passwd=登入mysql的密碼 host=localhost db=你的db table=你的table usercolumn=table中的使用者欄位名稱 passwdcolumn=table中的密碼欄位名稱 crypt=1 sqllog=0 


```
#%PAM-1.0
session    optional     pam_keyinit.so    force revoke
#数据库认证
auth       sufficient   /lib/security/pam_mysql.so user=vsftpd passwd=abc123 host=localhost db=vsftpd table=users usercolumn=name passwdcolumn=passwd crypt=2
#vsftp默认的其余认证
auth       required     pam_listfile.so item=user sense=deny file=/etc/vsftpd/ftpusers onerr=succeed
auth       required     pam_shells.so
auth       include      password-auth
#授权和认证也是一样的
account    sufficient   /lib/security/pam_mysql.so user=vsftpd passwd=abc123 host=localhost db=vsftpd table=users usercolumn=name passwdcolumn=passwd crypt=2
account    include      password-auth
session    required     pam_loginuid.so
session    include      password-auth
```

---

http://lemonup.logdown.com/posts/175031-ubuntu-vsftpd-install-notes
http://technote.aven-network.com/796/rhel7-centos7-vsftpd-virtual-users-libpam-pwfile


```
auth    required pam_pwdfile.so pwdfile /etc/vsftpd.passwd
account required pam_permit.so
```

htpasswd -cd /etc/vsftpd.passwd user1 #建立第一個user時使用

---

`使用 pam_tally2.so 達成登入安全機制`

http://technote.aven-network.com/866/using-pam_tally2-so
https://www.tecmint.com/use-pam_tally2-to-lock-and-unlock-ssh-failed-login-attempts/
https://ssorc.tw/1216





```
libpam-mysql - PAM module allowing authentication from a MySQL server
```

`/lib/security/pam_mysql.so`

```console
shell> cd /etc/pam.d
shell> vi openvpn
```

```
CREATE DATABASE openvpn;
USE openvpn;
CREATE TABLE user_auth (
  username VARCHAR(50) NOT NULL,
  `password` VARCHAR(50) NOT NULL,
  full_name VARCHAR(100),
  enabled CHAR(2) NOT NULL DEFAULT 'on',
  PRIMARY KEY (username),
  KEY enabled (enabled)
) ENGINE=INNODB DEFAULT CHARSET=utf8;

INSERT INTO `openvpn`.`user_auth` (`username`, `password`) VALUES ('zeus', 'blah'); 
```

`/usr/share/doc/libpam-mysql/README.gz`

```
user
passwd
host
db
table
usercolumn
passwdcolumn
crypt
```

```
auth       optional     pam_mysql.so user=root passwd=password host=192.168.88.19 db=openvpn table=user_auth usercolumn=username passwdcolumn=password where=enabled='on' crypt=0
account    required     pam_mysql.so user=root passwd=password host=192.168.88.19 db=openvpn table=user_auth usercolumn=username passwdcolumn=password where=enabled='on' crypt=0  

auth       optional     pam_mysql.so config_file=/etc/libpam-mysql.conf
account    required     pam_mysql.so config_file=/etc/libpam-mysql.conf


auth       optional     pam_mysql.so config_file=/etc/pam-mysql.conf
account    required     pam_mysql.so config_file=/etc/pam-mysql.conf


auth       optional     pam_mysql.so config_file=/etc/pam_mysql.conf
account    required     pam_mysql.so config_file=/etc/pam_mysql.conf



auth       optional     /lib/security/pam_mysql.so user=root passwd=password host=192.168.88.19 db=openvpn table=user_auth usercolumn=username passwdcolumn=password where=enabled='on' crypt=0
account    required     /lib/security/pam_mysql.so user=root passwd=password host=192.168.88.19 db=openvpn table=user_auth usercolumn=username passwdcolumn=password where=enabled='on' crypt=0  
```



```
crypt (plain)
    The method to encrypt the user's password:
       0 (or "plain") = No encryption.  Passwords stored in plaintext.
                        HIGHLY DISCOURAGED.
       1 (or "Y")     = Use crypt(3) function.
       2 (or "mysql") = Use MySQL PASSWORD() function. It is possible
                        that the encryption function used by PAM-MySQL
                        is different from that of the MySQL server, as
                        PAM-MySQL uses the function defined in MySQL's
                        C-client API instead of using PASSWORD() SQL function
                        in the query.                        
       3 (or "md5")   = Use plain hex MD5.
       4 (or "sha1")  = Use plain hex SHA1.

where
    Additional criteria for the query. For example:
            [where=Host.name="web" AND User.active=1]

config_file
    Path to a NSS-MySQL style configuration file which enumerates the options
    per line. Acceptable option names and the counterparts in the PAM-MySQL
    are listed below:

    - users.host (host)
    - users.database (db)
    - users.db_user (user)
    - users.db_passwd (passwd)
    - users.where_clause (host)
    - users.table (table)
    - users.update_table (update_table)
    - users.user_column (usercolumn)
    - users.password_column (passwdcolumn)
    - users.status_column (statcolumn)
    - users.password_crypt (crypt)
    - users.use_323_password (use_323_passwd)
    - users.use_md5 (md5)
    - users.where_clause (where)
    - users.disconnect_every_operation (disconnect_every_op) *1
    - verbose (verbose)
    - log.enabled (sqllog)
    - log.table (logtable)
    - log.message_column (logmsgcolumn)
    - log.pid_column (logpidcolumn)
    - log.user_column (logusercolumn)
    - log.host_column (loghostcolumn)
    - log.rhost_column (logrhostcolumn) *2
    - log.time_column (logtimecolumn)

    A "#" in front of the line makes it a comment as in NSS-MySQL.

    This is available since 0.7pre1.

    (*1: added in 0.7RC1)
    (*2: added in 0.7pre3)
```



```
saslauthd[3823]: PAM unable to dlopen(pam_mysql.so): /lib/security/pam_mysql.so: undefined symbol: make_scrambled_password
saslauthd[3823]: PAM adding faulty module: pam_mysql.so
saslauthd[3823]: DEBUG: auth_pam: pam_authenticate failed: Permission denied
saslauthd[3823]: do_auth         : auth failure: [user=zeus] [service=openvpn] [realm=] [mech=pam] [reason=PAM auth error]
```




```
users.host 		= localhost
users.database 		= mysql
users.db_user 		= root
users.db_passwd		= YOUDIDN'TSETONEDIDYOU?
#users.where_clause 	= (host)
users.table 		= user
#users.update_table 	= (update_table)
users.user_column 	= User
users.password_column 	= Password
#users.status_column 	= (statcolumn)
users.password_crypt 	= 2
#users.use_323_password	= (use_323_passwd)
#users.use_md5 		= yes
#users.where_clause 	= (where)
#users.disconnect_every_operation	= (disconnect_every_op) *1
#verbose 		= (verbose)
#log.enabled 		= (sqllog)
#log.table 		= (logtable)
#log.message_column 	= (logmsgcolumn)
#log.pid_column 	= (logpidcolumn)
#log.user_column 	= (logusercolumn)
#log.host_column 	= (loghostcolumn)
#log.rhost_column 	= (logrhostcolumn) *2
#log.time_column 	= (logtimecolumn)
```



<!--
http://b.gkp.cc/2010/08/08/setup-openvpn-with-mysql-auth/
-->

-->
