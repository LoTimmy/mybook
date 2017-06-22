`VPN Server`
`VPNServer`

`/var/packages/VPNCenter/etc`

### `synovpn.conf`

```
pptp_auth_conn=3
l2tp_auth_conn=3
ovpn_auth_conn=3
vpninterface=eth0
l2tp_custom_dns=yes
runl2tpd=yes
ppp_custom_dns=yes
runpptpd=yes
```

### `synovpn_port`

```
[vpn_server_pptp]
title="VPN Server (PPTP)"
desc="VPN Server"
port_forward="yes"
dst.ports="1723/tcp"

[vpn_server_openvpn]
title="VPN Server (OpenVPN)"
desc="VPN Server"
port_forward="yes"
dst.ports="1194/udp"

[vpn_server_l2tp]
title="VPN Server (L2TP/IPsec)"
desc="VPN Server"
port_forward="yes"
dst.ports="1701/udp"

[vpn_server_ipsec]
title="VPN Server (L2TP/IPsec)"
desc="VPN Server"
port_forward="yes"
dst.ports="500,4500/udp"
```


```console
shell> /usr/syno/bin/synovpnc
```

```
Usage:
	vpnc_tool COMMAND [ARGS]

	available COMMAND:
		get				(get config info)
		get_conn		(get current connection info)
		kill_client		(kill client)
		clear			(clear temp files of connection)
		connect			(connect)
		reconnect		(redial)
		update_conf		(sync new keys to old config files)
	available ARGS:
		--name
		--id
		--protocol
		--retry			(retry n times if connection failed)
		--interval		(time interval between each retry)
		--keepfile              (keep reconnection file)
	example:
		get --name=<test>
		get_conn
		kill_client
		connect --id=<id>
		reconnect --protocol=<pptp|l2tp|openvpn> --name=<test> [--retry=5] [--interval=30] [--keepfile]
		update_conf
		clear
```

```console
shell> /usr/syno/bin/synovpnc get_conn 
```

```
/usr/syno/etc/synovpnclient

/var/packages/VPNCenter/target/scripts

shell> /var/packages/VPNCenter/target/scripts/openvpn.sh start
shell> /var/packages/VPNCenter/target/scripts/openvpn.sh stop
shell> /var/packages/VPNCenter/target/scripts/openvpn.sh restart

shell> /var/packages/VPNCenter/target/scripts/l2tpd.sh start
shell> /var/packages/VPNCenter/target/scripts/l2tpd.sh stop
shell> /var/packages/VPNCenter/target/scripts/l2tpd.sh restart
```
---

`synoservice`
```
Copyright (c) 2003-2016 Synology Inc. All rights reserved.

SynoService Tool Help (Version 8451)
Usage: synoservice
	--help							Show this help
	--help-dev						More specialty functions for deveplopment
	--is-enabled		[ServiceName]			Check if the service is enabled
	--status		[ServiceName]			Get the status of specified services
	--enable		[ServiceName]			Set runkey to yes and start the service (alias to --start)
	--disable		[ServiceName]			Set runkey to no and stop the service (alias to --stop)
	--hard-enable		[ServiceName]			Set runkey to yes and start the service and its dependency (alias to --hard-start)
	--hard-disable		[ServiceName]			Set runkey to no and stop the service and its dependency (alias to --hard-stop)
	--restart		[ServiceName]			Restart the given service
	--reload		[ServiceName]			Reload the given service
	--pause			[ServiceName]			Pause the given service
	--resume		[ServiceName]			Resume the given service
	--pause-by-reason	[ServiceName]	[Reason]	Pause the service by given reason
	--resume-by-reason	[ServiceName]	[Reason]	Resume the service by given reason
	--pause-all		[Reason]	(Event)		Pause all service by given reason with optional event
	--pause-all-no-action	[Reason]	(Event)		Set all service runkey to no but leave the current service status
	--resume-all		[Reason]			Resume all service by given reason
	--reload-by-type	[type]		(buffer)	Reload services with specified type
	--restart-by-type	[type]		(buffer)	Restart services with specified type
								Type may be {ip|mtu|hostname|file_protocol|application|link}
								Sleep $buffer seconds before exec the command (default is 0)

```
```console
shell> synoservice --list
shell> synoservice --restart crond
shell> synoservice --restart pkgctl-VPNCenter
```

---

```console
shell> sudo -i
shell> vim /etc/crontab
shell> synoservice --restart crond
```

```
# For details see man 4 crontabs
# Example of job definition:
# .---------------- minute (0 - 59)
# | .------------- hour (0 - 23)
# | | .---------- day of month (1 - 31)
# | | | .------- month (1 - 12) OR jan,feb,mar,apr ...
# | | | | .---- day of week (0 - 6) (Sunday=0 or 7) OR sun,mon,tue,wed,thu,fri,sat
# | | | | |
# * * * * * username  command to be executed

MAILTO=""
PATH=/sbin:/bin:/usr/sbin:/usr/bin:/usr/syno/sbin:/usr/syno/bin:/usr/local/sbin:/usr/local/bin
#minute	hour	mday	month	wday	who	command
0	0	1	*	*	root	/usr/syno/bin/syno_disk_health_record
0	4	*	*	1	root	/usr/syno/bin/synodatascrubbingnotify /usr/syno/etc/datascrubbing.conf raid5datascrubbingscheduledtime
0	0	13	*	*	root	/tmp/synoschedtask --run id=1
0	0	28	*/6	*	root	/tmp/synoschedtask --run id=2
40	3	*	*	0	root	/tmp/synoschedtask --run id=3
0	0	*	*	*	root	/tmp/synoschedtask --run id=4
```

```console
shell> synoschedtask --get id=4
```

```
               ID: [4]
             Name: [Task 4]
            State: [enabled]
            Owner: [root]
             Type: [daily]
       Start date: [0/0/0]
         Run time: [0]:[0]
          Command: [synoservice --restart pkgctl-VPNCenter]
           Status: [No last run record]
```

---

`/var/log`
`/var/log/synopkg.log`
`/var/log/synoservice.log`



### :books: 參考網站：

---

`停止嗶聲`

「`硬體 & 電源`」→「`一般`」→ 「`停止嗶聲`」

---
