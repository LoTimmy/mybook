<img src="https://www.strongswan.org/images/strongswan.png" width="100">

`strongswan - IPsec VPN solution metapackage`
`xl2tpd - layer 2 tunneling protocol implementation`


```console
shell> lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.2 LTS
Release:	16.04
Codename:	xenial
```

```console
shell> sudo apt-get install strongswan xl2tpd
```

```console
shell> ipsec version
Linux strongSwan U5.3.5/K4.4.0-64-generic
Institute for Internet Technologies and Applications
University of Applied Sciences Rapperswil, Switzerland
See 'ipsec --copyright' for copyright information.
```


`/etc/sysctl.conf`

```
net.ipv4.ip_forward=1
```

```console
shell> sysctl -w net.ipv4.ip_forward=1
```

`/etc/ipsec.secrets`

```
: PSK "12345678"
```

`ipsec.conf`

```
config setup

conn L2TP-PSK-NAT
	rightsubnet=vhost:%priv
	also=L2TP-PSK-noNAT

conn L2TP-PSK-noNAT
	type=transport
	authby=secret
	keyingtries=3
	rekey=no
	dpddelay=30
	dpdtimeout=120
	dpdaction=clear
	leftprotoport=17/1701
 	left=%defaultroute
	right=%any
	rightprotoport=17/%any
	auto=add
```

`/etc/xl2tpd/xl2tpd.conf`

```
[global]
port = 1701
listen-addr = 192.168.192.130
ipsec saref = yes

[lns default]
ip range=10.2.0.2-80
local ip=10.2.0.1
require chap = yes
refuse pap = yes
require authentication = yes
ppp debug = yes
ppp debug=no
length bit = yes
pppoptfile = /etc/ppp/options.xl2tpd
name = l2tpd
```

`/etc/ppp/options.xl2tpd`

```
name l2tpd
require-mschap-v2
refuse-mschap
refuse-chap
refuse-pap

ms-dns 8.8.8.8

mtu 1400
mru 1400
connect-delay 5000
noccp
auth
crtscts
lock
debug
proxyarp
defaultroute
```

`/etc/ppp/chap-secrets`
```
zeus		*	blah *
```

```console
shell> service strongswan start
shell> service xl2tpd start
shell> update-rc.d strongswan enable
shell> ipsec start
shell> ipsec restart
shell> ipsec stop
shell> ipsec status
shell> ipsec statusall

shell> systemctl status xl2tpd.service
```

```console
shell> iptables -t nat -A POSTROUTING -s 10.2.0.0/24 -o ens32 -j MASQUERADE
```

```console
shell> iptables -A INPUT -p udp -m policy --dir in --pol ipsec -m udp --dport 1701 -j ACCEPT
```


#### :books: 參考網站：
- http://www.cisco.com/c/en/us/support/docs/ip/internet-key-exchange-ike/117258-config-l2l.html
- http://www.cisco.com/c/en/us/support/docs/network-management/remote-access/117257-config-ios-vpn-strongswan-00.html
- [ipsec.secrets](http://manpages.ubuntu.com/manpages/zesty/man5/ipsec.secrets.5.html)
- https://libreswan.org/man/ipsec.conf.5.html
- https://download.libreswan.org/old-freeswan/freeswan-2.06/doc/manpage.d/ipsec.conf.5.html
- https://download.libreswan.org/old-openswan/openswan-2.6.16/testing/pluto/mast-l2tp-02/east.l2tpd.conf
- https://download.libreswan.org/old-openswan/openswan-2.6.16/testing/pluto/l2tp-01/north.l2tpd.conf
- https://download.libreswan.org/old-freeswan/freeswan-2.06/doc/manpage.d/ipsec_auto.8.html
- http://docs.oracle.com/cd/E19253-01/816-4555/pppsvrconfig.reference-46/index.html
- https://ppp.samba.org/pppd.html
- [在Cisco IOS和strongSwan配置示例之间的IKEv1/IKEv2](http://www.cisco.com/c/zh_cn/support/docs/ip/internet-key-exchange-ike/117258-config-l2l.html)

---

`Dead Peer Detection`

```
dpddelay=30
dpdtimeout=120
dpdaction=clear
```

---

`PAP`：`VPN` 客戶端的密碼在認證過程中將不加密。
`MS-CHAP v2`：`VPN` 客戶端的密碼在認證過程中將使用 `Microsoft CHAP version 2 加密`。
`MTU` (`Maximum Transmission Unit`，`傳輸單元最大值`)：設定 `VPN` 傳輸允許的最大資料封包大小。

#### :books: 參考網站：
- https://www.synology.com/zh-tw/knowledgebase/DSM/help/VPNCenter/vpn_setup
- https://www.synology.com/zh-tw/releaseNote/VPNCenter
- https://www.synology.com/zh-tw/knowledgebase/DSM/tutorial/General/What_network_ports_are_used_by_Synology_services
- https://www.synology.com/zh-tw/knowledgebase/SRM/help/VPNPlusServer/vpnplus_server_standardvpn
- https://www.synology.com/zh-tw/knowledgebase/SRM/tutorial/Network/How_to_connect_to_VPN_Plus_Server_using_a_Windows_PC_or_Mac

---

#### :books: 參考網站：
- [strongswan](https://www.strongswan.org/)
- [ipsec.conf](http://manpages.ubuntu.com/manpages/wily/man5/ipsec.conf.5.html)
- [ipsec.secrets](http://manpages.ubuntu.com/manpages/xenial/man5/ipsec.secrets.5.html)
- http://www.cisco.com/cisco/web/support/CN/113/1133/1133929_117258-config-l2l.html
- https://libreswan.org/
- https://download.libreswan.org/old-openswan/openswan-2.6.16/programs/examples/l2tp-psk.conf.in

