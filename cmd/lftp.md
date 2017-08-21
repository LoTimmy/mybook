`lftp - Sophisticated command-line FTP/HTTP/BitTorrent client programs`

### 安裝 {#installing}

```
shell> brew install lftp
shell> apt-get install lftp
shell> apt install lftp
```

```
shell> lftp -u admin,"secret" 192.168.168.188
shell> lftp -u admin,"secret" 192.168.168.188 -e "cd ; put ; bye"
```

`/etc/lftp.conf`
`~/.lftprc`
`~/.lftp/rc`