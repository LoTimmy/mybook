`curlftpfs - filesystem to access FTP hosts based on FUSE and cURL`

### 安裝 {#installing}

```sh
shell> apt-get install curlftpfs
shell> apt install curlftpfs
```

```console
shell> curlftpfs -v -o allow_other -o user="user:pass" ftp.myserver.com:21 /mnt/ftp
shell> curlftpfs -o codepage=utf8,iocharset=big5,ipv4,user={username}:{password} ftp://{servicename} /root/file-sharing
```

`/etc/fstab`
```
curlftpfs#ftp.host.com /mnt/ftp fuse allow_other,rw,uid=500,user,auto 0 0
```

`/root/.netrc`

```
machine ftp.host.com  
login myuser  
password mypass 
```

```
shell> fusermount -u /mnt/ftp
```


#### :books: 參考網站：
- [curlftpfs](http://curlftpfs.sourceforge.net/)
