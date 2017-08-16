### 安裝 {#installing}

```
shell> apt-get install clamav 
shell> apt-get install spamassassin
shell> apt-get install mailscanner

shell> vim /etc/MailScanner/MailScanner.conf
```

```
Run As User = postfix
Run As Group = postfix

Incoming Queue Dir = /var/spool/mqueue.in
Outgoing Queue Dir = /var/spool/mqueue
MTA = sendmail

Virus Scanning = yes
Virus Scanners = clamav

Use SpamAssassin = yes
SpamAssassin User State Dir = /var/spool/MailScanner/spamassassin

Sign Clean Messages = no
Dangerous Content Scanning = no
Maximum Archive Depth = 0
Use Stricter Phishing Net = no
Highlight Phishing Fraud = no

Spam Modify Subject = start
High Scoring Spam Modify Subject = start

Spam Subject Text = {Spam?}
High Scoring Spam Subject Text = {Spam?}

Spam Actions = deliver header "X-Spam-Status: Yes"
Spam Actions = store forward anonymous@ecs.soton.ac.uk
High Scoring Spam Actions = store
Non Spam Actions = deliver header "X-Spam-Status: No"

Spam List Definitions = %etc-dir%/spam.lists.conf
Spam List = # spamhaus-ZEN # You can un-comment this to enable them
Spam Lists To Be Spam = 1
Spam Domain List =

Required SpamAssassin Score = 6
High SpamAssassin Score = 10

Phishing Subject Text = {Fraud?}
Phishing Modify Subject = no

Disarmed Modify Subject = start
Disarmed Subject Text = {Disarmed}

Virus Modify Subject = start
Virus Subject Text = {Virus?}

Scanned Modify Subject = no
Scanned Subject Text = {Scanned}
```

`/etc/MailScanner/rules/spam.whitelist.rules`

`/etc/default/mailscanner`
```
run_mailscanner=1
```

`/etc/default/spamassassin`
```
ENABLED=1
```

`/etc/postfix/header_checks`
```
/^Received:/ HOLD
```

```
shell> postconf -e 'header_checks = regexp:/etc/postfix/header_checks'	
```

```
shell> vim /etc/init.d/mailscanner
```
```
start-stop-daemon --start --quiet --nicelevel $run_nice --exec $DAEMON --name $NAME -- $DAEMON_ARGS
start-stop-daemon --start --quiet --nicelevel $run_nice -c ${user} --exec $DAEMON --name $NAME -- $DAEMON_ARGS
```

```
shell> service spamassassin restart
shell> service mailscanner restart
```

#### :books: 參考網站：
- [mailscanner](https://www.mailscanner.info/)
- [mailscanner](https://www.mailscanner.info/MailScanner.conf.index.html)
- [mailscanner](https://www.mailscanner.info/postfix/)
