dhcpcd — a DHCP client

`/etc/dhcpcd.conf`

```
interface eth0
static ip_address=
destination routers

interface wlan0
static ip_address=192.168.31.226/24
static routers=192.168.31.1
static domain_name_servers=127.0.0.1
```

- http://manpages.ubuntu.com/manpages/trusty/man5/dhclient.conf.5.html
- http://manpages.ubuntu.com/manpages/trusty/man8/dhclient.8.html
