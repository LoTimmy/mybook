`curlftpfs - filesystem to access FTP hosts based on FUSE and cURL`

```console
shell> curlftpfs -v -o allow_other -o user="user:pass" ftp.myserver.com:21 /mnt/ftp
shell> curlftpfs -o codepage=utf8,iocharset=big5,ipv4,user={username}:{password} ftp://{servicename} /root/file-sharing
```

`.netrc`

```
machine ftp.host.com  
login myuser  
password mypass 
```

#### :books: 參考網站：
- [curlftpfs](http://curlftpfs.sourceforge.net/)
