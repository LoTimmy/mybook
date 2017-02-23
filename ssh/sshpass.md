`sshpass - Non-interactive ssh password authentication`


### 安裝 {#installing}

```console
shell> apt-get install sshpass
```

```console
shell> sshpass -p 12345 ssh -l username remotehost
shell> sshpass -p 12345 sftp username@remotehost
```

```console
shell> set +o history
shell> sshpass -p 12345 ssh -l username remotehost
shell> set -o history
```