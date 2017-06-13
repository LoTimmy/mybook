`ip - show / manipulate routing, devices, policy routing and tunnels`

### ip addr {#ip-address}
```
ip addr [ add | del ] address dev ifname
```

`Assigning a Static Address Using ip Commands` 

```console
shell> ifconfig eth0 10.0.0.3

shell> ip address add 10.0.0.3/24 dev eth0
shell> ip addr show dev eth0
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether f0:de:f1:7b:6e:5f brd ff:ff:ff:ff:ff:ff
    inet 10.0.0.3/24 brd 10.0.0.255 scope global global eth0
       valid_lft 58682sec preferred_lft 58682sec
    inet6 fe80::f2de:f1ff:fe7b:6e5f/64 scope link 
       valid_lft forever preferred_lft forever
```

```console
shell> ifconfig eth0 192.168.0.77 netmask 255.255.255.0 broadcast 192.168.0.255
shell> ip addr 192.168.0.77/24 broadcast 192.168.0.255 dev eth0
```
```console
shell> ip addr delete 192.168.0.77/24 dev eth0
```

`Configuring Multiple Addresses Using ip Commands`
```console
shell> ip address add 192.168.2.223/24 dev eth1
shell> ip address add 192.168.4.223/24 dev eth1
shell> ip addr
3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 52:54:00:fb:77:9e brd ff:ff:ff:ff:ff:ff
    inet 192.168.2.223/24 scope global eth1
    inet 192.168.4.223/24 scope global eth1
```

```console
shell> ifconfig eth0:1 192.168.2.223
shell> ifconfig eth0:2 192.168.4.223

shell> ip address add 192.168.2.223/24 dev eth1 label eth0:1
shell> ip address add 192.168.4.223/24 dev eth1 label eth0:2
```

---

### ip neigh {#ip-neighbour}


```console
shell> arp -i eth1 -s 192.168.2.223 00:0c:29:2e:72:81
shell> ip neigh add 192.168.2.223 lladdr 00:0c:29:2e:72:81 nud permanent dev eth1

shell> ip neigh show 
```

```console
shell> ip -6 neigh show 
```

---

```console
shell> ip link ls
shell> ip route show
shell> ip link ls up
```
---

### ip route {#ip-route}

```console
shell> route
shell> ip route show

shell> ip route get 8.8.8.8

shell> route add -net 192.168.3.0/24 dev eth3
shell> ip route add 192.168.3.0/24 dev eth3

shell> route del -net 192.168.3.0/24 dev eth3
shell> ip route del 192.168.3.0/24 dev eth3

shell> route add -net 192.168.4.0/24 gw 192.168.4.1 
shell> ip route add 192.168.3.0/24 via 192.168.4.1
```
---

#### :books: 參考網站：
- [ip](http://manpages.ubuntu.com/manpages/trusty/man8/ip.8.html)
- [ip route](http://manpages.ubuntu.com/manpages/trusty/man8/ip-route.8.html)
- [ip neigh](http://manpages.ubuntu.com/manpages/trusty/man8/ip-neighbour.8.html)
- [route](http://manpages.ubuntu.com/manpages/trusty/man8/route.8.html)
- [network_mtu](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/network_mtu.html)
- [2.3.2. Configuring a Network Interface Using ip Commands](https://docs.fedoraproject.org/en-US/Fedora/22/html/Networking_Guide/sec-Configuring_a_Network_Interface_Using_ip_commands.html)
