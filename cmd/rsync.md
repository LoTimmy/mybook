`rsync - fast, versatile, remote (and local) file-copying tool`

```console
shell> rsync -avz foo:src/bar /data/tmp
shell> rsync -avz --delete src/ dst_directory/

shell> rsync -av --partial --append --progress mylinux.iso 10.1.2.3:~/
shell> rsync -avP --append mylinux.iso 10.1.2.3:~/

shell> rsync -avz --delete --append --progress -e ssh 10.1.2.3:~/src dst_directory/  
```
