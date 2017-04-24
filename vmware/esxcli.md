
```console
shell> esxcli network nic list
```

---

```console
shell> esxcli network ip interface ipv4 get
Name  IPv4 Address    IPv4 Netmask   IPv4 Broadcast  Address Type  DHCP DNS
----  --------------  -------------  --------------  ------------  --------
vmk0  192.168.31.200  255.255.255.0  192.168.31.255  STATIC           false

shell> esxcli network ip interface ipv4 set -i vmk0 I 10.27.51.143 -N 255.255.255.0 -t static    
```

`List active TCP/IP connections.`
```console
shell> esxcli network ip connection list
shell> esxcli network ip connection list | grep LISTEN | grep 0.0.0.0:59
```

`List ARP table entries.`
```console
shell> esxcli network ip neighbor list
```

```console
shell> esxcli network ip interface list
shell> esxcli network ip interface ipv4 get -i vmk<X>
shell> esxcli network ip interface ipv6 get -n vmk<X>
shell> esxcli network ip interface ipv4 set -i vmk<X> -I 192.168.1.200 -N 255.255.255.0 -t static
shell> esxcli network ip interface ipv6 address list
shell> esxcli network ip dns server list
shell> esxcli network vswitch standard list
```

#### :books: 參考網站：
- [Changing the ESXi server management IP address](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=2084629)

---

```console
shell> esxcli network firewall get
shell> esxcli network firewall set --enabled true
shell> esxcli network firewall set --enabled false

shell> esxcli network firewall ruleset list
shell> esxcli network firewall ruleset set --enabled true --ruleset-id=sshClient

shell> esxcli network firewall unload
```

#### :books: 參考網站：
- [About the ESXi 5.x and 6.x firewall](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=2005284)

---

```console

shell> esxcli system settings advanced list
shell> esxcli system settings advanced set -o /Net/GuestIPHack -i 1
```

```console
shell> esxcli system hostname get
shell> esxcli system hostname set --host=hostname
shell> esxcli system hostname set --fqdn=fqdn
```

#### :books: 參考網站：
- [Changing the name of an ESX or ESXi host](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1010821)

---

```
shell> esxcli esxcfg-route -l
shell> esxcli esxcfg-vmknic -l

shell> esxcli system welcomemsg get
shell> esxcli system version get
shell> esxcli system time get

shell> esxcli system syslog mark --message="this is a message!"
shell> esxcli system syslog config get

shell> esxcli vm process list
shell> esxcli vm process kill --type=[soft,hard,force] --world-id=WorldNumber
shell> esxcli vm process kill --type soft --world-id 1268395

shell> esxcli vm process list # Get a listing of VMs on a host
shell> esxcli vm process kill --type= [soft,hard,force] --world-id=WorldNumber
shell> esxcli vm process kill --type=force --world-id=33466

List all of the CPUs on this host.        
shell> esxcli hardware cpu list

List all of the PCI devices on this host.	
shell> esxcli hardware pci list

Get information about memory.        
shell> esxcli hardware memory get

Get information about the platform
shell> esxcli hardware platform get


shell> esxcli storage vmfs extent list
shell> esxcli storage filesystem list
shell> esxcli storage core path list
shell> esxcli storage core device list
t10.ATA_____WDC_WD5002ABYS2D18B1B0________________________WD2DWCASY4897543
   Display Name: Local ATA Disk (t10.ATA_____WDC_WD5002ABYS2D18B1B0________________________WD2DWCASY4897543)
   Has Settable Display Name: true
   Size: 476940
   Device Type: Direct-Access 
   Multipath Plugin: NMP
   Devfs Path: /vmfs/devices/disks/t10.ATA_____WDC_WD5002ABYS2D18B1B0________________________WD2DWCASY4897543
   Vendor: ATA     
   Model: WDC WD5002ABYS-1
   Revision: 02.0
   SCSI Level: 5
   Is Pseudo: false
   Status: on
   Is RDM Capable: false
   Is Local: true
   Is Removable: false
   Is SSD: false
   Is Offline: false
   Is Perennially Reserved: false
   Thin Provisioning Status: unknown
   Attached Filters: 
   VAAI Status: unsupported
   Other UIDs: vml.0100000000202020202057442d574341535934383937353433574443205744

shell> esxcli storage core device list -d vml.0100000000202020202057442d574341535934383937353433574443205744

shell> fdisk /vmfs/devices/disks/vml.0100000000202020202057442d574341535934383937353433574443205744
shell> fdisk /vmfs/devices/disks/naa.60024e805564a00016a1a2fa0c3a836c

shell> partedUtil get "/vmfs/devices/disks/vml.0100000000202020202057442d574341535934383937353433574443205744"
shell> partedUtil getptbl /vmfs/devices/disks/naa.60024e805564a00016a1a2fa0c3a836c

shell> esxcli software vib list
shell> esxcli software profile get

shell> esxcfg-scsidevs -a

shell> esxcli software acceptance
shell> esxcli software acceptance get
PartnerSupported
shell> esxcli software acceptance set --level=CommunitySupported


```

#### :books: 參考網站：
- https://pubs.vmware.com/vsphere-50/index.jsp?topic=%2Fcom.vmware.vcli.ref.doc_50%2Fesxcli_hardware.html
