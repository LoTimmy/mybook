`autossh - Automatically restart SSH sessions and tunnels`

### 安裝 {#installing}
```
shell> apt-get install autossh
```

```
shell> autossh -M 20000 -t remotehost 'screen -raAd sessionname'
shell> ssh -t remotehost screen -xRR
```
