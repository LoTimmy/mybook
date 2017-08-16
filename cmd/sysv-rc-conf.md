`sysv-rc-conf - SysV init runlevel configuration tool for the terminal`

`rcconf - Debian Runlevel configuration tool`

### 安裝 {#installing}

```
shell> apt-get install sysv-rc-conf
shell> apt-get install rcconf dialog
```

```
shell> sysv-rc-conf
shell> sysv-rc-conf --list
shell> sysv-rc-conf --list dnsmasq
dnsmasq      0:off	1:off	2:on	3:on	4:on	5:on	6:off

shell> sysv-rc-conf dnsmasq on
shell> sysv-rc-conf dnsmasq off
dnsmasq      0:off	1:off	2:off	3:off	4:off	5:off	6:off
```

#### :books: 參考網站：
- http://manpages.ubuntu.com/manpages/zesty/en/man8/update-rc.d.8.html
- http://manpages.ubuntu.com/manpages/xenial/en/man8/sysv-rc-conf.8.html
- http://manpages.ubuntu.com/manpages/xenial/en/man8/rcconf.8.html