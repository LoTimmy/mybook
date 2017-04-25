`gvpe - creates a virtual ethernet between multiple endpoints`

`GNU Virtual Private Ethernet (GVPE)`

### 安裝 {#installing}

```console
shell> sudo apt-get install gvpe
```

`/etc/gvpe/gvpe.conf`
```
# Specify the use of UDP and the default port
enable-udp = yes
udp-port = 407

# Set the name of the virtual device created
ifname = vpn0

mtu = 1492

compress = yes
router-priority = 1

# Set the first node
node = branch1
hostname = 44.88.167.250

# Set the second node
node = branch2
hostname = 145.253.105.130
```

`创建公共/私有密匙`

```console
shell> gvpectrl -c /etc/gvpe -g
```

```
/etc/gvpe/hostkey
```

```console
shell> gvpectrl -s
```


```
gvpe: /usr/bin/gvpectrl
gvpe: /usr/share/doc/gvpe/examples/if-up.gz
gvpe: /usr/share/doc/gvpe/examples/node-up
gvpe: /etc/gvpe
```

```
connect = ondemand
```

```
/etc/gvpe/hostkey
/etc/gvpe/if-up
```


```
#!/bin/sh
ip link set $IFNAME address $MAC mtu $MTU up
[ $NODENAME = branch1 ] && ip addr add 10.0.0.1 dev $IFNAME
[ $NODENAME = branch2 ] && ip addr add 10.1.0.1 dev $IFNAME
ip route add 10.0.0.0/8 dev $IFNAME
```


- http://savannah.gnu.org/projects/gvpe/
- http://software.schmorp.de/pkg/gvpe.html
- http://pod.tst.eu/http://cvs.schmorp.de/gvpe/doc/gvpe.conf.5.pod
- [使用 GNU Virtual Private Ethernet](https://www.ibm.com/developerworks/cn/aix/library/au-gnuvpe/)