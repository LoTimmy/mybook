```
shell> mount -v
```

---

`tmpfs`

```
shell> mount -t tmpfs -o size=100m none /mytmpfs
```


`/etc/fstab`

```
none	/mytmpfs	tmpfs	size=10G,mode=1777	0 0
```

```
shell> umount /mytmpfs
```

```
shell> time dd if=/dev/zero of=bigfile bs=1k count=1024
shell> time dd of=bigfile bs=1 count=0 seek=90M
shell> time truncate -s 90m bigfile
shell> time fallocate -l 90m bigfile
```

#### :books: 參考網站：
- [tmpfs](https://www.kernel.org/doc/Documentation/filesystems/tmpfs.txt)
- [ramfs-rootfs-initramfs](https://www.kernel.org/doc/Documentation/filesystems/ramfs-rootfs-initramfs.txt)
- [mount](http://manpages.ubuntu.com/manpages/xenial/man8/mount.8.html)

---

```
shell> sudo apt install ecryptfs-utils
shell> sudo mount -t ecryptfs /srv /srv
```
#### :books: 參考網站：
- [ecryptfs](https://help.ubuntu.com/lts/serverguide/ecryptfs.html)


---

```
shell> sudo mount -t cifs -o username=john,password=johnpass,domain=example.com //winserver/share /mnt/winshare
```

`/etc/fstab`
```
//winserver/share /mnt/winshare cifs gid=users,file_mode=0664,dir_mode=0775,auto,rw,username=john,password=johnpass 0 0
//winserver/share /mnt/winshare cifs credentials=credfile,uid=1000,gid=1000,iocharset=utf8,file_mode=0664,dir_mode=0775 0 0
```

#### :books: 參考網站：
- [cifs-utils](cmd/cifs-utils.md)

---

```
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
- [curlftpfs](cmd/curlftpfs.md)
- [mount.fuse](http://manpages.ubuntu.com/manpages/precise/man8/mount.fuse.8.html)
- [fusermount](http://manpages.ubuntu.com/manpages/precise/man1/fusermount.1.html)