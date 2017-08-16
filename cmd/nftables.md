`nftables - Program to control packet filtering rules by Netfilter project`

```
shell> sudo apt-get install nftables
```

```
shell> nft list table ip filter
```

`/etc/nftables`
`/usr/share/doc/nftables/examples`

`nftables.conf`

```
#!/usr/sbin/nft -f

flush ruleset

table inet filter {
	chain input {
		type filter hook input priority 0;

		# accept any localhost traffic
		iif lo accept

		# accept traffic originated from us
		ct state established,related accept

		# activate the following line to accept common local services
		#tcp dport { 22, 80, 443 } ct state new accept

		# accept neighbour discovery otherwise IPv6 connectivity breaks.
		ip6 nexthdr icmpv6 icmpv6 type { nd-neighbor-solicit,  nd-router-advert, nd-neighbor-advert } accept

		# count and drop any other traffic
		counter drop
	}
}
```

#### :books: 參考網站：
- http://www.netfilter.org/
- http://netfilter.org/projects/nftables/index.html
- http://www.netfilter.org/projects/nftables/manpage.html
