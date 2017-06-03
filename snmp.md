![](http://www.net-snmp.org/images/logos/logo1_65_tr_small.gif)

---

```console
shell> lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04 LTS
Release:	14.04
Codename:	trusty
```

- `snmp - SNMP (Simple Network Management Protocol) applications`
- `snmpd - SNMP (Simple Network Management Protocol) agents`
- `snmp-mibs-downloader - Install and manage Management Information Base (MIB) files`
 
```console
shell> sudo apt-get update && sudo apt-get install snmp
shell> sudo apt-get install snmp-mibs-downloader
```

---

```console
shell> download-mibs

shell> snmpwalk -m SNMPv2-MIB -Os -c public -v 1 localhost system
shell> snmpwalk -m SNMPv2-MIB -Os -c public -v 1 localhost sysUpTime
shell> snmpwalk -m SNMPv2-MIB -Os -c public -v 1 localhost sysDescr

shell> snmpwalk -m HOST-RESOURCES-MIB -Os -c public -v 2c localhost hrSystemDate
```

---

`snmpd - SNMP (Simple Network Management Protocol) agents`

```console
shell> sudo apt-get update && sudo apt-get install snmpd
shell> vim /etc/default/snmpd

export MIBS=/usr/share/mibs
```
```console
shell> sed -i "s|-Lsd|-LS6d|" /etc/default/snmpd
```

```
rocommunity public
disk /
```

### :books: 參考網站：
- [SNMPD.CONF](http://net-snmp.sourceforge.net/docs/man/snmpd.conf.html)


```console
shell> snmpnetstat -v 2c -c public -Ca testhost
shell> snmpnetstat -v 2c -c public -Ci testhost
shell> snmpnetstat -v 2c -c public -CP tcp testhost

shell> snmpnetstat -v 2c -c public -Cr testhost

shell> snmpnetstat -v 2c -c public -Canp tcp testhost
```

```sh
function f1() {
  IpAddress=$1

  hrSystemUptime=$(/usr/bin/snmpwalk -Oqv -c public -v 2c $1 -m HOST-RESOURCES-MIB hrSystemUptime )
  sysName=$(/usr/bin/snmpwalk -Oqv -c public -v 2c $1 -m SNMPv2-MIB sysName )
  mongo test --quiet --eval "db.testData.insert({date: Date(), IpAddress:\"$IpAddress\", sysName: \"$sysName\", hrSystemUptime: \"$hrSystemUptime\"})"

  printf "%s %s %s " $date $hrSystemUptime $sysName
  echo 
}

f1 192.168.41.1
f1 192.168.41.2


function f2() {
  IpAddress=$1
  sysDescr=$(/usr/bin/snmpwalk -Oqv -c public -v 2c $IpAddress -m SNMPv2-MIB sysDescr )
  mongo test --quiet --eval "db.testData.insert({date: Date(), IpAddress:\"$IpAddress\", sysDescr: \"$sysDescr\" })"
}

f2 192.168.41.1
f2 192.168.41.2
f2 192.168.41.4
f2 192.168.41.5
f2 192.168.41.6
```

### :books: 參考網站：
- [snmpnetstat](http://www.net-snmp.org/docs/man/snmpnetstat.html)
