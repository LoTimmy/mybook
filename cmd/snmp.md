![](http://www.net-snmp.org/images/logos/logo1_65_tr_small.gif)

`簡單網絡管理協議` (`Simple Network Management Protocol`) 是一種應用層協議，是`TCP/IP`協議族的一部分。它使網絡設備之間能夠方便地交換管理信息。能夠讓網絡管理員管理網絡的性能，發現和解決網絡問題及進行網絡的擴充。
目前`SNMP`已成為網絡管理領域中事實上的工業標準，並被廣泛支持和應用，大多數網絡管理系統和平台都是基於`SNMP`的。

簡而言之，`SNMP` 協議是用來管理設備的協議，何謂管理呢？我斗膽將其歸納為兩個基本點：監控(`get`)和配置(`set`)。也就是說：人們管理一個設備的基本手段可以歸納為 `get` 和 `set` 兩種操作。

`SNMP` 基本管理控制框架
![](https://www.ibm.com/developerworks/cn/linux/l-cn-snmp/image001.jpg)

如果`NMS`(`網管系統`) 需要查詢被管理設備的狀態，則需要通過`SNMP`的`get`操作獲得設備的狀態信息；同樣，如果`NMS`需要修改或者配置被管理設備的參數，則需要通過`SNMP`的`set`操作來完成。

`MIB` 是描述被管理設備上的參數的數據結構。如前所述，管理一個設備，就是利用 `SNMP` 協議，通過網絡對被管理設備上的參數進行 `get` 和 `set` 操作。

那麼如何組織被管理設備上的參數呢？多數情況下，可以 `get` 和 `set` 的參數實在多得驚人，假如僅僅簡單地線性羅列它們，操作會十分不便。想像一下把 1000 個參數列成一張表，需要使用的時候查詢這樣一張表會有多麼困難啊？比如您打算在地球上找一個城市，”Ithaca”，如果沒有歸類和分級，則需要查找一張巨大的表格。但如果告訴您城市” Ithaca”是：南美洲國家圭亞那的北部城市"Ithaca"，那麼就容易些了吧？

被管理的設備相當複雜，擁有很多可以被管理的參數，需要對它們進行歸類，分級。`管理信息庫` (`MIB`) 是一個具有分層特性的信息的集合，我們可以通過 `SNMP` 去存取它。 `MIB` 的成員是一些被管理的對象 (`Managed Object`)，以對象標示符 (`Object Identifiers`) 來區分它們。被管理的對象由一個或多個對象實例 (`Object Instances`) 組成，本質上，這些對象實例就是變量。

很多能夠被 `SNMP` 管理的對像都是由標準組織定義好的。比如係統磁盤的信息，用 `OID` ”`1.3.6.1.4.1.2021.9`” 表示。這串數字是國際標準化組織協商定義好的，大家都要去遵循它。當然，國際組織不可能預知未來，如果您要開發的設備有一些管理需求沒有任何 `RFC` 定義過，那麼您也可以編寫自己的 `MIB` 文件來定義私有的 `MIB` 對象。

`SNMP Trap` 就是被管理設備主動發送消息給 `NMS` 的一種機制。


---

```console
shell> yum install net-snmp net-snmp-devel net-snmp-utils
/etc/snmp/snmpd.conf
```

```
syslocation Unknown (edit /etc/snmp/snmpd.conf)
syscontact Root <root@localhost> (configure /etc/snmp/snmp.local.conf)
```


---

```console
shell> iptables -A INPUT -i eth0 -p udp -s 123.123.123.123 --dport 161 -j ACCEPT
```

---


`Process Monitoring`

```
# At least one web server process must be running at all times
proc    httpd
procfix httpd  /etc/rc.d/init.d/httpd restart

# There should never be more than 10 mail processes running
#    (more implies a probable mail storm, so shut down the mail system)
proc    sendmail   10
procfix sendmail  /etc/rc.d/init.d/sendmail stop

# There should be a single network management agent running
#   ("There can be only one")
proc    snmpd    1  1
```
```
proc vsftpd

proc apache2
procfix apache2  service apache2 restart
```

- `snmpget`
- `snmpset`

```
UCD-SNMP-MIB::prIndex.1 = INTEGER: 1
UCD-SNMP-MIB::prIndex.2 = INTEGER: 2
UCD-SNMP-MIB::prNames.1 = STRING: apache2
UCD-SNMP-MIB::prNames.2 = STRING: snmpd
UCD-SNMP-MIB::prMin.1 = INTEGER: 1
UCD-SNMP-MIB::prMin.2 = INTEGER: 1
UCD-SNMP-MIB::prMax.1 = INTEGER: 0
UCD-SNMP-MIB::prMax.2 = INTEGER: 1
UCD-SNMP-MIB::prCount.1 = INTEGER: 0
UCD-SNMP-MIB::prCount.2 = INTEGER: 1
UCD-SNMP-MIB::prErrorFlag.1 = INTEGER: error(1)
UCD-SNMP-MIB::prErrorFlag.2 = INTEGER: noError(0)
UCD-SNMP-MIB::prErrMessage.1 = STRING: No apache2 process running
UCD-SNMP-MIB::prErrMessage.2 = STRING: 
UCD-SNMP-MIB::prErrFix.1 = INTEGER: noError(0)
UCD-SNMP-MIB::prErrFix.2 = INTEGER: noError(0)
UCD-SNMP-MIB::prErrFixCmd.1 = STRING: service apache2 restart
UCD-SNMP-MIB::prErrFixCmd.2 = STRING: 
```

```console
shell> snmpget -v 2c -c public -OvQe localhost UCD-SNMP-MIB::prErrorFlag.1
shell> snmpset -v 2c -c public localhost UCD-SNMP-MIB::prErrFix.1 = 1
```

```
Error in packet.
Reason: noAccess
Failed object: UCD-SNMP-MIB::prErrFix.1
```

```console
shell> snmpget -v 1 -c public localhost system.sysUpTime.0
shell> snmpwalk -v 2c -c public localhost system
```

```console
shell> snmpwalk -v 1 localhost -c public system
shell> snmpwalk -v 2c -c public localhost .1.3.6.1.4.1.2021.9
shell> snmpwalk -v 2c -c public localhost .1.3.6.1.4.1.2021.2
```

```console
shell> snmpget -v 1 -c public localhost ucdDemoPublicString.0 
shell> snmpset -v 1 -c public localhost ucdDemoPublicString.0 s "Hello, world!"
```

```console
shell> snmpnetstat -v 2c -c public localhost
shell> snmpnetstat -v 2c -c public localhost -Cn
``` 



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

#### :books: 參考網站：
- http://www.net-snmp.org/docs/man/snmpd.examples.html
- http://manpages.ubuntu.com/manpages/zesty/man5/snmpd.conf.5.html
- http://manpages.ubuntu.com/manpages/xenial/man5/snmpd.conf.5.html

---

`Old Style`
```
exec [MIBOID] NAME PROG ARGS"
sh   [MIBOID] NAME PROG ARGS"
execfix NAME PROG ARGS"
```

`New Style`
```
extend [MIBOID] NAME PROG ARGS"
extendfix [MIBOID] NAME PROG ARGS"
```

```
exec echotest /bin/echo hello world
exec shelltest /bin/sh /tmp/shtest
```

`/tmp/shtest`
```
#!/bin/sh
echo hello world
echo hi there
exit 35
```

```console
shell> snmpwalk -v 2c -c public localhost .1.3.6.1.4.1.2021.8
```

```
exec .1.3.6.1.4.1.2021.50 shelltest /bin/sh /tmp/shtest
exec .1.3.6.1.4.1.2021.51 ps /bin/ps
```

```console
shell> snmpd -v
NET-SNMP version:  5.5
Web:               http://www.net-snmp.org/
Email:             net-snmp-coders@lists.sourceforge.net
```


```console
shell> snmpd -v
NET-SNMP version:  5.7.3
Web:               http://www.net-snmp.org/
Email:             net-snmp-coders@lists.sourceforge.net
```

```
extend .1.3.6.1.4.1.2021.50 shelltest /bin/sh /tmp/shtest
extend .1.3.6.1.4.1.2021.51 ps /bin/ps
```

```console
shell> snmpwalk -v 2c -c public localhost .1.3.6.1.4.1.2021.50
```

---

`snmpdf`

`Disk Usage Monitoring`
```
includeAllDisks 10%
disk /var 20%
disk /usr  3%
#  Keep 100 MB free for crash dumps
disk /mnt/crash  100000
```

```console
shell> snmpdf -v 1 -c public -Cu localhost
Description              Size (kB)            Used       Available Used%
/                        162943468        27167548       135775920   16%

shell> snmpdf -v 1 -c public -Cu 192.168.2.93
Description              Size (kB)            Used       Available Used%
/                         16026128         3124588        12901540   19%

```


---

`snmpstatus` 

```console
shell> snmpstatus -v 1 -c public localhost
```

---

`snmptranslate`

`snmptranslate` 命令將 `MIB` `OIDs` 的兩種表現形式 (數字及文字) 相互轉換。並顯示 `MIB` 的內容與結構，如下所示：


```console
shell> snmptranslate -On -IR ssCpuRawSystem
.1.3.6.1.4.1.2021.11.52

shell> snmptranslate -On -Td -IR ssCpuRawSystem

shell> snmptranslate -Td .1.3.6.1.4.1.2021.11.52
UCD-SNMP-MIB::ssCpuRawSystem
ssCpuRawSystem OBJECT-TYPE
  -- FROM	UCD-SNMP-MIB
  SYNTAX	Counter32
  MAX-ACCESS	read-only
  STATUS	current
  DESCRIPTION	"The number of 'ticks' (typically 1/100s) spent
         processing system-level code.

         On a multi-processor system, the 'ssCpuRaw*'
         counters are cumulative over all CPUs, so their
         sum will typically be N*100 (for N processors).

         This object may sometimes be implemented as the
         combination of the 'ssCpuRawWait(54)' and
         'ssCpuRawKernel(55)' counters, so care must be
         taken when summing the overall raw counters."
::= { iso(1) org(3) dod(6) internet(1) private(4) enterprises(1) ucdavis(2021) systemStats(11) 52 }

```
---

snmptrap -d -v 2c -c public localhost "" UCD-SNMP-MIB::ucdStart message s "/ disk utilization exceed 80%"


#### :books: 參考網站：
- https://www.ibm.com/developerworks/cn/linux/l-cn-snmp/

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

export MIBS=+SNMPv2-MIB
```
```console
shell> sed -i "s|-Lsd|-LS6d|" /etc/default/snmpd
```

```
rocommunity public
disk /
```

`/etc/snmp/snmp.conf`
```
# mibs :
```

#### :books: 參考網站：
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
