`swaks - SMTP command-line test tool`
`tokyocabinet-bin - Tokyo Cabinet Database Utilities`

```
shell> apt-get install swaks
shell> apt install tokyocabinet-bin
```

```
shell> swaks --to user@example.com --server test-server.example.net
shell> swaks --to user@example.com --from me@example.com --auth CRAM-MD5 --auth-user me@example.com --header-X-Test "test email"
shell> swaks --to user@example.com --from me@gmail.com --auth --auth-user=me --auth-password= -tls --server smtp.gmail.com:587 --header ""
shell> swaks --to foo@example.net,bar@example.com
shell> SWAKS_OPT_to='foo@example.net,bar@example.com' swaks

shell> echo "--to foo@example.net,bar@example.com" >> .swaksrc
shell> swaks --config .swaksrc

shell> swaks --add-header "X-Test-Header: foo"
shell> swaks --h-Subject "Hello World"
```

`$HOME/.swaksrc`

```
shell> swaks --attach-type text/html --attach report.html
shell> swaks --body report.html \
--add-header "MIME-Version: 1.0" \
--add-header "Content-Type: text/html"
```

`tcucodec - popular encoders and decoders`

`中文`

```
shell> tcucodec quote report.html > my-email.html
shell> swaks --body my-email.html \
--header "Subject: Hello World" -S \
--add-header "MIME-Version: 1.0" \
--add-header "Content-Type: text/html; charset=UTF-8" \
--add-header "Content-Transfer-Encoding: quoted-printable" \
--to user@example.com \
--server test-server.example.net
```


```
shell> curl www.example.com/mypage | swaks -f me@example.com -t user@example.com --attach-type text/html --attach -   
```

```
shell> file --mime-type example_image.png | sed 's/.*: //'

shell> swaks -s test-server.example.net -p 25 \ 
-t user@example.com -f me@example.com \
--header "Subject: Hello World" -S \
--protocol ESMTP -a -au me -ap passwd  \
--body "This is a test mailing" \
--body "Hello, this is an e-mail. I hope you like it ;-)" \
--attach-type text/html --attach report.html \
--attach-type text/html --attach report.html
```

`-S, --silent [level]`

`-d, --data [data-portion]`


```
shell> swaks --from me@example.com --h-From: '"Me" <me@example.com>'
```

`--protocol LMTP`
`--protocol ESMTP`
`--protocol SMTP`

#### :books: 參考網站：
- [swaks](http://www.jetmore.org/john/code/swaks/)
- http://www.jetmore.org/john/code/swaks/faq.html
- http://manpages.ubuntu.com/manpages/xenial/man1/swaks.1.html
