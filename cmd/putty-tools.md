`putty-tools - command-line tools for SSH, SCP, and SFTP`


### 安裝 {#installing}

```
shell> apt-get install putty-tools
shell> brew install putty

shell> puttygen my-key-pair.ppk -O private-openssh -o id_rsa
shell> puttygen my-key-pair.ppk -O public-openssh -o id_rsa.pub

shell> puttygen id_rsa -o my-key-pair.ppk

shell> puttygen -l my-key-pair.ppk

shell> puttygen -t rsa -C "my home key" -o mykey.ppk
shell> puttygen -t rsa -b 4096 -C "my home key" -o mykey.ppk
shell> puttygen -C "new comment" mykey.ppk
shell> puttygen -L mykey.ppk >> $HOME/.ssh/authorized_keys
```
