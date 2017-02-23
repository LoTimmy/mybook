`cifs-utils - Common Internet File System utilities`

`samba - SMB/CIFS file, print, and login server for Unix`

`smbclient - command-line SMB/CIFS clients for Unix`


### 安裝 {#installing}
```console
shell> sudo apt-get install cifs-utils
```

```console
shell> sudo mkdir /mnt/winshare

shell> sudo mount -t cifs -o username=john,password=johnpass,domain=example.com //winserver/share /mnt/winshare
shell> sudo mount -t cifs //winserver/share /mnt/winshare -o user=john,password=johnpass,dir_mode=0664,file_mode=0775

shell> sudo mount -t cifs //winserver/share /mnt/winshare -o credentials=credfile
shell> sudo mount.cifs //winserver/share /mnt/winshare -o file_mode=0777,dir_mode=0777,user=john,password=johnpass,iocharset=utf8
```

`/etc/fstab`
```
//winserver/share /mnt/winshare cifs gid=users,file_mode=0664,dir_mode=0775,auto,rw,username=john,password=johnpass 0 0
//winserver/share /mnt/winshare cifs credentials=credfile,uid=1000,gid=1000,iocharset=utf8,file_mode=0664,dir_mode=0775 0 0
```

```
username=john
password=johnpass
domain=MYDOMWKG
```
```console
shell> chmod 400 credfile
```
```console
shell> mount -a

shell> umount -lf /mnt/winshare
```


#### :books: 參考網站：
- [如何搭配使用 Azure 檔案儲存體與 Linux](https://azure.microsoft.com/zh-tw/documentation/articles/storage-how-to-use-files-linux/)
- [mount.cifs](https://www.samba.org/samba/docs/man/manpages-3/mount.cifs.8.html)
- https://access.redhat.com/solutions/448263
- [mount.cifs](https://opensource.apple.com/source/samba/samba-92.15/samba/docs/htmldocs/mount.cifs.8.html)
- https://docs.oracle.com/cd/E37670_01/E41138/html/ch21s03s04.html
- https://www.novell.com/support/kb/doc.php?id=7000932