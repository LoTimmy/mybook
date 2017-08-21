`p7zip - 7z file archiver with high compression ratio`

### 安裝 {#installing}

```
shell> brew install masscan
```


`scan some web ports on 192.168.88.x at 10kpps`
```
shell> masscan -p80,8000-8100 192.168.88.0/24 --rate=10000
```

`list those options that are compatiable with nmap`
```
shell> masscan --nmap
```

`save results of scan in binary format to <filename>`
```
shell> masscan -p80 192.168.88.0/24 --banners -oB <filename>
```

```
shell> masscan -p80 192.168.88.0/24 --banners --echo > masscan.conf
shell> masscan -c masscan.conf --rate=10000
```

`read binary scan results in <filename> and save them as xml in <savefile>`
```
shell> masscan --open --banners --readscan <filename> -oX <savefile>
```


```
shell> masscan 192.168.88.0/24 -p80
```
