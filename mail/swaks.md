`swaks - SMTP command-line test tool`

```console
shell> apt-get install swaks
```

```console
shell> swaks --to user@example.com --server test-server.example.net
shell> swaks --to user@example.com --from me@example.com --auth CRAM-MD5 --auth-user me@example.com --header-X-Test "test email"
shell> swaks --to user@example.com --from me@gmail.com --auth --auth-user=me --auth-password= -tls --server smtp.gmail.com:587 --header ""
```

```console
shell> swaks --attach-type text/html --attach report.html
shell> swaks --body report.html --add-header "MIME-Version: 1.0" --add-header "Content-Type: text/html"
```

```console
shell> swaks --body report.html --add-header "MIME-Version: 1.0" --add-header "Content-Type: text/html" --to user@example.com --server test-server.example.net
```

#### :books: 參考網站：
- [swaks](http://www.jetmore.org/john/code/swaks/)