<img src="https://avatars3.githubusercontent.com/u/3006190?v=3&s=200" width="50">

<img src="http://i.imgur.com/UsYeOvB.png" width="150">

```
client <---> ss-local <--[encrypted]--> ss-remote <---> target
```

### 安裝 {#installing}

`python-pip - alternative Python package installer`

`shadowsocks - Fast tunnel proxy that helps you bypass firewalls`

```console
shell> lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.2 LTS
Release:	16.04
Codename:	xenial
```

```console
shell> sudo apt-get install python-pip
shell> pip install --upgrade pip
shell> pip install shadowsocks
```

`/usr/local/bin/ssserver`

```console
shell> ssserver -c /etc/shadowsocks.conf
shell> ssserver -k barfoo! -m aes-256-cfb
shell> ssserver -c /etc/shadowsocks.conf -d start
shell> ssserver -d stop
shell> ssserver -c /etc/shadowsocks.conf -d restart   
```

```
Proxy options:
  -c CONFIG              path to config file
  -s SERVER_ADDR         server address, default: 0.0.0.0
  -p SERVER_PORT         server port, default: 8388
  -k PASSWORD            password
  -m METHOD              encryption method, default: aes-256-cfb
  -t TIMEOUT             timeout in seconds, default: 300
  --fast-open            use TCP_FASTOPEN, requires Linux 3.7+
  --workers WORKERS      number of workers, available on Unix/Linux
  --forbidden-ip IPLIST  comma seperated IP list forbidden to connect
  --manager-address ADDR optional server manager UDP address, see wiki
```

`/etc/shadowsocks.conf`

```
{
    "server":"0.0.0.0",
    "server_port":8388,
    "local_port":1080,
    "password":"barfoo!",
    "timeout":600,
    "fast_open": true,
    "workers": 1,
    "method":"aes-256-cfb"
}
```

`/etc/security/limits.conf`
```
* soft nofile 51200
* hard nofile 51200
```

```console
shell> ulimit -n 51200
```

`/etc/sysctl.conf`

```
fs.file-max = 51200

net.core.rmem_max = 67108864
net.core.wmem_max = 67108864
net.core.netdev_max_backlog = 250000
net.core.somaxconn = 4096

net.ipv4.tcp_syncookies = 1
net.ipv4.tcp_tw_reuse = 1
net.ipv4.tcp_tw_recycle = 0
net.ipv4.tcp_fin_timeout = 30
net.ipv4.tcp_keepalive_time = 1200
net.ipv4.ip_local_port_range = 10000 65000
net.ipv4.tcp_max_syn_backlog = 8192
net.ipv4.tcp_max_tw_buckets = 5000
net.ipv4.tcp_fastopen = 3
net.ipv4.tcp_mem = 25600 51200 102400
net.ipv4.tcp_rmem = 4096 87380 67108864
net.ipv4.tcp_wmem = 4096 65536 67108864
net.ipv4.tcp_mtu_probing = 1
net.ipv4.tcp_congestion_control = hybla
```

```
shell> sysctl -p
```

- [config](https://shadowsocks.org/en/config/quick-guide.html)
- [config](https://shadowsocks.org/en/config/advanced.html)

---

- [shadowsocks-qt5](https://github.com/shadowsocks/shadowsocks-qt5/releases)
- [shadowsocks](https://itunes.apple.com/tw/app/shadowsocks/id665729974?l=zh&mt=8)

---

#### :books: 參考網站：
- [shadowsocks](https://github.com/shadowsocks)
- [shadowsocks](https://shadowsocks.org/en/index.html)
- [clients](https://shadowsocks.org/en/download/clients.html)
- https://github.com/Wind4/docker-library/blob/master/shadowsocks-libev/debian/Dockerfile
- https://github.com/Wind4/docker-library/blob/master/shadowsocks-libev/Dockerfile

