`arp-scan - arp scanning and fingerprinting tool`

### 安裝 {#installing}

```
shell> brew install arp-scan
shell> apt-get install arp-scan
```

```
shell> sudo arp-scan -l -I eth0
shell> sudo arp-scan -l -I en0
shell> sudo arp-scan -I en0 192.168.31.0/24
shell> sudo arp-scan -I en0 192.168.31.1-192.168.31.50
```

`/usr/share/arp-scan/ieee-oui.txt`
`/usr/share/arp-scan/ieee-iab.txt`
`/usr/local/Cellar/arp-scan/1.9/share/arp-scan`

```
shell> get-iab
shell> get-oui
```


```
shell> arp-fingerprint 192.168.0.1
shell> arp-fingerprint -o "-N -I eth1" 192.168.0.202
```

