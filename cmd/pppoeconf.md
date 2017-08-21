### 安裝 {#installing}

```
shell> apt-get install pppoeconf
```

`/etc/ppp/peers/dsl-provider is pppd options file for your dsl provider.`

`/etc/ppp/pap-secrets and /etc/ppp/chap-secrets are described in pppd documentation.  pppoeconf may add lines to theses files.`

`chap-secrets`
```
"username" * ""
"75172901@hinet.net" * "uzrswxsl"
```

`pap-secrets`
```
"75172901@hinet.net" * "uzrswxsl"
```

`dsl-provider`
```
noipdefault
defaultroute
replacedefaultroute
hide-password
#lcp-echo-interval 30
#lcp-echo-failure 4
noauth
persist
#mtu 1492
#persist
#maxfail 0
#holdoff 20
plugin rp-pppoe.so eth1
user "username"
usepeerdns
```

```
username@ip.hinet.net
username@hinet.net

75172901@ip.hinet.net
75172901@hinet.net
```

```
auto eth1
iface eth1 inet ppp
pre-up /bin/ip link set eth1 up # line maintained by pppoeconf
provider dsl-provider
```

`myisp`

```
shell> pppoeconf
shell> poff -a
shell> pon dsl-provider
shell> plog
```
