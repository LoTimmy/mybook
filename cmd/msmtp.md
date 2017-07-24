```
msmtp-mta - light SMTP client with support for server profiles - the regular MTA
msmtp - An SMTP client
```

`~/.msmtprc`

```
host 192.168.2.93
port 25

from joe_smith@freemail.example
```

msmtp --host=192.168.2.93 -t joe_smith@freemail.example
msmtp -C ~/.msmtprc -t joe_smith@freemail.example

echo "" | msmtp --host=192.168.2.93 -t joe_smith@freemail.example
cat | msmtp --host=192.168.2.93 -t


- http://msmtp.sourceforge.net/doc/msmtprc.txt
- http://msmtp.sourceforge.net/doc/msmtp.html
