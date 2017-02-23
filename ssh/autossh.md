`autossh - Automatically restart SSH sessions and tunnels`

### 安裝 {#installing}
```console
shell> apt-get install autossh
```

```console
shell> autossh -M 20000 -t remotehost 'screen -raAd sessionname'
shell> ssh -t remotehost screen -xRR
```
