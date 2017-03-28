> 虛擬化系統主要可分為全虛擬化與半虛擬化兩種，前者是安裝在原本作業系統之上，如`VMware Server`；而後者則直接安裝在伺服器上、不須架構在一般作業系統上，像`Citrix XenServer`、`VMware ESX`等。兩者相較，半虛擬化的效能比較佳，因此在實務上，也都是以此建置虛擬化系統。      
> `開放虛擬化格式` (`Open Virtualization Format`, `OVF`) 是 Distributed Management Task Force, Inc. 提供的封裝標準，其設計目的是要協助移植和部署虛擬裝置。

#### :books: 參考網站：
- [ovf](https://www.vmware.com/support/developer/ovf/)
- [Sample ovftool command syntax to export, deploy, and 1-step export and deploy packages in vCenter Server (1038709)](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1038709)
- [VMware products and their virtual hardware version](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1003746)
- [VMware 产品及其虚拟硬件版本](https://kb.vmware.com/selfservice/search.do?cmd=displayKC&docType=kc&docTypeID=DT_KB_1_1&externalId=2048332)

```console
shell> vmware -vl
VMware ESXi 5.0.0 build-469512
VMware ESXi 5.0.0 GA

VMware ESXi 6.0.0 build-3620759
VMware ESXi 6.0.0 Update 2
```

`Power on a VM`
```console
shell> vim-cmd vmsvc/power.on vmid $(vim-cmd vmsvc/getallvms | grep '' | awk '{$1}')
```
---

`open-vm-tools`

```console
shell> vmware-toolbox-cmd help
shell> vmware-toolbox-cmd -v

shell> vmware-toolbox-cmd timesync status
shell> vmware-toolbox-cmd timesync enable
shell> vmware-toolbox-cmd timesync disable

shell> vmware-checkvm
```

#### :books: 參考網站：
- [open-vm-tools](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=2073803)
- [vmware-tools-cli](http://www.vmware.com/pdf/vmware-tools-cli.pdf)

---

`vmware-manager - utility to manage VMware virtual machines`

---


### VMware OVF Tool {#ovftool} 

`OVFTool`

![](http://i.imgur.com/DfZH2Pt.png)


`C:\Program Files (x86)\VMware\VMware Workstation\OVFTool`

`C:\Program Files\VMware\VMware OVF Tool`

`c:\ovfs\my_vapp.ovf`

`c:\vms\my_vm.vmx`

`c:\VirtualMachines\MyVM.vmx`


`--noSSLVerify`

```console
shell> ovftool "%HOMEPATH%\Documents\Virtual Machines\xenial\xenial.vmx" "%HOMEPATH%\Documents/xenial.ova"
shell> ovftool "%HOMEPATH%\Documents\Virtual Machines\yakkety\yakkety.vmx" "%HOMEPATH%\Documents/yakkety.ova"

shell> ovftool "%HOMEPATH%\Documents/xenial.ova"
shell> ovftool "%HOMEPATH%\Documents/yakkety.ova"
```

```console
shell> ovftool ubuntu-1604.vmwarevm/ubuntu-1604.vmx ~/Documents/ubuntu
shell> ovftool --acceptAllEulas ~/Documents/"Virtual Machines.localized/Windows 7 x64.vmwarevm/Windows 7 x64.vmx" ~/Documents/windows7.ova
```

```console
shell> ovftool ~/Documents/ubuntu-1604.ova
```

`Rename the OVF Package`

```console
shell> ovftool “Windows 7.ovf” win7.ovf
```

`Converting a VMX File to an ESXi host`

```console
shell> ovftool /ovfs/my_vm.vmx vi://username:pass@my_esx_host
```

```console
shell> ovftool package.ovf vi://my.esx-machine.example.com/
shell> ovftool package.ovf vi://username:pass@my.esx-machine.example.com/

shell> ovftool -ds=datastore1 --net:nat="VM Network" ubuntu-1604.ova vi://root@192.168.168.196
shell> ovftool -ds=datastore2 --net:nat="VM Network" ubuntu-1604.ova vi://root@192.168.168.196
```

```console
shell> chmod +x VMware-ovftool-4.0.0-2301625-lin.x86_64.bundle
shell> ovftool --help
```

#### :books: 參考網站：
- [ovftool](https://www.vmware.com/support/developer/ovf/ovf410/ovftool-410_userguide.pdf)
- [ovftool](https://www.vmware.com/support/developer/ovf/ovf301/ovftool-301-userguide.pdf)
- [ovftool](https://www.vmware.com/support/developer/ovf/ovf20/ovftool_201_userguide.pdf)
- [ovftool](https://my.vmware.com/web/vmware/details?productId=491&downloadGroup=OVFTOOL410)

---

```console
shell> chmod +x VMware-VIX-1.13.2-1744117.x86_64.bundle
shell> ./VMware-VIX-1.13.2-1744117.x86_64.bundle
```

```console
shell> /usr/local/bin/vmrun
shell> vmrun -T ws start "c:\my VMs\myVM.vmx"
shell> vmrun start "C:\Documents and Settings\<user>\My Documents\My Virtual Machines\WinXP\WinXP.vmx"
shell> vmrun -T ws -gu guestUser -gp guestPassword runProgramInGuest "c:\my VMs\myVM.vmx" "c:\Program Files\myProgram.exe"
shell> vmrun -T ws snapshot "c:\my VMs\myVM.vmx" mySnapshot
shell> vmrun -T ws revertToSnapshot "c:\my VMs\myVM.vmx" mySnapshot
shell> vmrun -T ws deleteSnapshot "c:\my VMs\myVM.vmx" mySnapshot
shell> vmrun -T ws enableSharedFolders "c:\my VMs\myVM.vmx"
shell> vmrun list

shell> vmrun -T esx -h https://esx.example.com:8333/sdk -u root -p secretpw list

shell> vmrun -T ws reset /path/to/vm/RHEL4/RHEL4.vmx soft
shell> vmrun stop "C:\Documents and Settings\<user>\My Documents\My Virtual Machines\WinXP\WinXP.vmx"

shell> vmrun -T esx -h https://10.0.1.8/sdk -u root -p <pass> start "[storage1] WinXP/WinXP.vmx"

shell> vmrun -T fusion installTools RedHatEnt5/RedHatEnt5.vmx
shell> vmrun deleteVM "c:\my VMs\myVM.vmx"

shell> vmrun -T ws -gu guestUser -gp guestPassword runProgramInGuest "c:\my VMs\myVM.vmx" "c:\Program Files\myProgram.exe"
shell> vmrun -T ws -gu <user> runProgramInGuest WinXP\WinXP.vmx cmd.exe
shell> vmrun -T ws -gu <user> runProgramInGuest WinXP\WinXP.vmx -activeWindow cmd.exe
shell> vmrun -T ws -gu <user> runScriptInGuest Win2k\Win2k.vmx C:\perl\perl.exe C:\script.pl

shell> vmrun -T ws -gu <user> -gp <pass> runScriptInGuest Ubuntu/Ubuntu.vmx /bin/bash /home/<user>/runit
shell> vmrun -gu <user> -gp <pass> runProgramInGuest SUSE/SUSE.vmx /usr/bin/xclock -display :0
shell> vmrun -T ws -gu <user> -gp <pass> runProgramInGuest Ubuntu/Ubuntu.vmx /usr/bin/perl -e 'print "Hello World\n"'


shell> vmrun -gu <user> -gp <pass> CopyFileFromHostToGuest Ubuntu/Ubuntu.vmx 

```

#### :books: 參考網站：
- [vmrun](https://my.vmware.com/web/vmware/free#desktop_end_user_computing/vmware_player/6_0|PLAYER-600-A|drivers_tools)
- [vmrun](http://www.vmware.com/pdf/vix160_vmrun_command.pdf)
- [vmrun](http://www.vmware.com/pdf/vix180_vmrun_command.pdf)

---

```console
shell> /usr/bin/host_reboot.sh
shell> /usr/bin/host_shutdown.sh
```
---

```
Switch VMware Fusion to Full Screen View
Use the ⌘+Control+F keyboard shortcut to switch to Full Screen view.
```

---

```console
shell> esxcli network ip interface ipv4 get
Name  IPv4 Address    IPv4 Netmask   IPv4 Broadcast  Address Type  DHCP DNS
----  --------------  -------------  --------------  ------------  --------
vmk0  192.168.31.200  255.255.255.0  192.168.31.255  STATIC           false

shell> esxcli network ip interface ipv4 set -i vmk0 I 10.27.51.143 -N 255.255.255.0 -t static    
```


```console
List active TCP/IP connections.
shell> esxcli network ip connection list
shell> esxcli network ip connection list | grep LISTEN | grep 0.0.0.0:59
shell> esxcli network ip neighbor list
shell> esxcli network nic list

shell> esxcli network ip interface list
shell> esxcli network ip interface ipv4 get -i vmk<X>
shell> esxcli network ip interface ipv6 get -n vmk<X>
shell> esxcli network ip interface ipv6 address list
shell> esxcli network ip dns server list
shell> esxcli network vswitch standard list

shell> esxcli network firewall get
shell> esxcli network firewall set --enabled true
shell> esxcli network firewall set --enabled false

shell> esxcli network firewall unload

shell> esxcli esxcfg-route -l
shell> esxcli esxcfg-vmknic -l

List ARP table entries.
shell> esxcli network ip neighbor list

shell> esxcli system welcomemsg get

shell> esxcli system syslog mark --message="this is a message!"
shell> esxcli hardware memory get
shell> esxcli hardware cpu list
shell> esxcli hardware pci list
shell> esxcli system syslog config get

VirtualMachineName
shell> esxcli vm process list
shell> esxcli vm process kill --type=[soft,hard,force] --world-id=WorldNumber
shell> esxcli vm process kill --type soft --world-id 1268395

shell> esxcfg-nics --list
shell> esxcfg-nics -l

List all of the CPUs on this host.        
shell> esxcli hardware cpu list

Get information about memory.        
shell> esxcli hardware memory get

shell> esxcli system hostname get

shell> esxcli storage vmfs extent list
shell> esxcli storage filesystem list
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

shell> vsish

shell> vmware --version
VMware ESXi 5.0.0 build-469512
shell> vmware -v
shell> vmware --level
VMware ESXi 5.0.0 GA

shell> esxcli software vib list
shell> esxcli software profile get

shell> esxcfg-scsidevs -a

shell> esxcli software acceptance
shell> esxcli software acceptance get
PartnerSupported
shell> esxcli software acceptance set --level=CommunitySupported
```

```console
shell> esxcfg-nics --list
shell> esxcfg-vswitch --list

shell> esxcfg-vmknic --list

shell> esxcfg-route --list
shell> esxcfg-route -l

shell> esxcfg-route -a default 192.168.1.151
```

```console
shell> /sbin/powerOffVms
shell> /sbin/poweroff

shell> /bin/reboot
```

```console
shell> vim-cmd
Commands available under /:
hbrsvc/       internalsvc/  solo/         vmsvc/        
hostsvc/      proxysvc/     vimsvc/       help

shell> vim-cmd vmsvc/
Commands available under vmsvc/:
acquiremksticket                 get.spaceNeededForConsolidation  
acquireticket                    get.summary                      
connect                          get.tasklist                     
convert.toTemplate               getallvms                        
convert.toVm                     gethostconstraints               
createdummyvm                    login                            
destroy                          logout                           
device.connection                message                          
device.connusbdev                power.getstate                   
device.disconnusbdev             power.hibernate                  
device.diskadd                   power.off                        
device.diskaddexisting           power.on                         
device.diskremove                power.reboot                     
device.getdevices                power.reset                      
device.toolsSyncSet              power.shutdown                   
device.vmiadd                    power.suspend                    
device.vmiremove                 power.suspendResume              
devices.createnic                queryftcompat                    
get.capability                   reload                           
get.config                       setscreenres                     
get.config.cpuidmask             snapshot.create                  
get.configoption                 snapshot.dumpoption              
get.datastores                   snapshot.get                     
get.disabledmethods              snapshot.remove                  
get.environment                  snapshot.removeall               
get.filelayout                   snapshot.revert                  
get.filelayoutex                 snapshot.setoption               
get.guest                        tools.cancelinstall              
get.guestheartbeatStatus         tools.install                    
get.managedentitystatus          tools.upgrade                    
get.networks                     unregister                       
get.runtime                      upgrade                          
get.snapshotinfo


shell> vim-cmd vmsvc/getallvms # Get a listing of VMs on a host
shell> esxcli vm process list # Get a listing of VMs on a host


shell> esxcli vm process kill --type= [soft,hard,force] --world-id= WorldNumber


shell> esxcli vm process kill --type=force --world-id=33466

shell> vim-cmd vmsvc/get.summary vmid       # Retrieves and displays the listsummary status from the vm.

shell> vim-cmd solo/registervm path_to_vmx_file # Register a VM
shell> vim-cmd vmsvc/unregister vmid # Unregister a VM
shell> vim-cmd vmsvc/destroy vmid # Delete a VM

Determine if a VM has a snapshot
shell> vim-cmd vmsvc/get.snapshot vmid

Take a snapshot of a VM
shell> vim-cmd vmsvc/snapshot.create vmid snapshot_name

Remove a snapshot of a VM
shell> vim-cmd vmsvc/snapshot.remove vmid

shell> vim-cmd vmsvc/power.hibernate vmid

shell> vim-cmd vmsvc/snapshot.revert vmid snapshot_name


Power on a VM
shell> vim-cmd vmsvc/power.on vmid # Power on the specified virtual machine.

Reboot a VM
shell> vim-cmd vmsvc/power.reboot vmid

Shutdown a VM
shell> vim-cmd vmsvc/power.shutdown vmid

Power off a VM
shell> vim-cmd vmsvc/power.off vmid # Power off the specified virtual machine.

Get the current power state of a VM
shell> vim-cmd vmsvc/power.getstate vmid

Get the uptime for a VM
shell> vim-cmd vmsvc/get.summary vmid | grep uptimeSeconds

Reset a VM
shell> vim-cmd vmsvc/power.reset vmid


Upgrade VMware Tools in a VM
shell> vim-cmd vmsvc/tools.upgrade vmid

Display the IP address of a VM
shell> vim-cmd vmsvc/get.guest vmid |grep -m 1 "ipAddress = \""

shell> vim-cmd vmsvc/power.suspend vmid

Sets the Console window's resolution.
shell> vim-cmd vmsvc/setscreenres vmid width height

Convert the virtual machine to a template.
shell> vim-cmd vmsvc/convert.toTemplate vmid

Convert the template to a virtual machine.
shell> vim-cmd vmsvc/convert.toVm vmid

Retrieves and displays the configuration object for the vm.
shell> vim-cmd vmsvc/get.config vmid

shell> vim-cmd vimsvc/license --show

shell> vim-cmd hostsvc/datastore/listsummary
shell> vim-cmd hostsvc/datastore/summary datastore1
shell> vim-cmd hostsvc/datastore/listvm datastore1
```

```
RemoteDisplay.vnc.enabled = "TRUE"
RemoteDisplay.vnc.port = "portnumber"
```

**5901 to 6001**

---

```console
shell> vim-cmd vmsvc/tools.install vmid
```

```console
shell> sudo mount /dev/cdrom /media/cdrom
shell> ls /mnt/cdrom
shell> tar xzvf /media/cdrom/VMwareTools-x.x.x-xxxx.tar.gz -C /tmp/
shell> cd /tmp/vmware-tools-distrib/
shell> sudo ./vmware-install.pl -d
shell> sudo reboot
```

####  參考網站：
- [在 Ubuntu 虚拟机中安装 VMware Tools](http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=2041399)
- [Performing common virtual machine-related tasks with command-line utilities](http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=2012964)

---

```console
shell> sshpass -p 12345 ssh -l username remotehost "vim-cmd vmsvc/getallvms"
shell> sshpass -p 12345 ssh -l username remotehost "esxcli vm process list"
```

---

`Power-on Boot Delay`
`Power On to BIOS`

`.vmx`

```
bios.forceSetupOnce = "TRUE"
bios.bootDelay = "xxxx"
```

`Workstation 7.x and later` 
`VM` > `Power` > `Power On to BIOS`

####  參考網站：
- [Accessing the BIOS when the POST screen clears too quickly](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1004129)

---

```
ide1:0.present = "TRUE"
ide1:0.fileName = "/vmfs/volumes/datastore1/packages/5.0.0/vmtools/linux.iso"
ide1:0.deviceType = "cdrom-image"
ide1:0.startConnected = "TRUE"
```

```
ide1:0.fileName = "/vmfs/volumes/datastore1/isoimages/ubuntu/ubuntu-12.04.1-server-amd64.iso"
```

---

`/etc/ssh/sshd_config`

```
UseDNS no
Compression yes
```

```console
shell> /etc/init.d/SSH restart
```

---

```console
shell> vim-cmd vmsvc/tools.install <vmid>

shell> vim-cmd hostsvc/net/info
shell> vim-cmd hostsvc/hosthardware

shell> vmkfstools -X 20GB srcDisk
shell> vmkfstools -extendvirtualdisk srcDisk

shell> vmkfstools -i srcDisk -d thin dstDisk

shell> esxcfg-nics -l
shell> esxcfg-vswitch -l

shell> vm-support -x

shell> ps | grep vmx

shell> esxtop
```

---

fusion-windows-create-virtual-machine
captureScreen
deleteVM

---


#### :books: 參考網站：
- [VMware-viclient-all-5.0.0-455964.exe](http://vsphereclient.vmware.com/vsphereclient/4/5/5/9/6/4/VMware-viclient-all-5.0.0-455964.exe)
- [VMware-viclient-all-4.1.0-258902.exe](http://vsphereclient.vmware.com/vsphereclient/2/5/8/9/0/2/VMware-viclient-all-4.1.0-258902.exe)
- [SSLIgnore](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=2002617)


```
-------------- Example 1 --------------

-------------- Example 2 --------------

-------------- Example 3 --------------

datastore1
datastore2
examplevm
```


```
vmware-cmd -s unregister /vmfs/volumes/VMname/vm.vmx
vmware-cmd -s register /vmfs/volumes/VMname/vm.vmx

```

`Fusion`
`ESXi/ESX`
`Player`
`Ubuntu 64-bit`
`Other`

`trusty` `14.04 LTS`
`precise` `12.04 LTS`

---

`xenial` `16.04 LTS`
`yakkety` `16.10`

```console
shell> ovftool "%HOMEPATH%\Documents\Virtual Machines\xenial\xenial.vmx" "%HOMEPATH%\Documents/xenial.ova"
shell> ovftool "%HOMEPATH%\Documents\Virtual Machines\yakkety\yakkety.vmx" "%HOMEPATH%\Documents/yakkety.ova"

shell> ovftool "%HOMEPATH%\Documents/xenial.ova"
shell> ovftool "%HOMEPATH%\Documents/yakkety.ova"
```

`ubuntu`
`insecure`



```
C:\Documents and Settings\username\My Documents\My Virtual Machines
C:\Users\username\Documents\Virtual Machines

C:\Documents and Settings\All Users\Documents\Shared Virtual Machines
C:\Users\Public\Documents\Shared Virtual Machines
/var/lib/vmware/Shared VMs
```



`VMware OVF Tool for Windows 32-bit`
`VMware OVF Tool for Windows 64-bit`
`VMware OVF Tool for Linux 32-bit`
`VMware OVF Tool for Linux 64-bit`
`VMware OVF Tool for Mac OSX`

#### :books: 參考網站：
- https://www.debian.org/releases/wheezy/example-preseed.txt

`Windows`

`Mac OS X`

`Linux`

`Android`

```
ifconfig | grep -A2 vmnet
```
```
vmnet1: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500
	ether 00:50:56:c0:00:01 
	inet 192.168.47.1 netmask 0xffffff00 broadcast 192.168.47.255
--
vmnet8: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500
	ether 00:50:56:c0:00:08 
	inet 192.168.118.1 netmask 0xffffff00 broadcast 192.168.118.255
```

vmnet1（仅主机）
vmnet8 (NAT)
#### :books: 參考網站：
- https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1026510

---


```
swapoff /dev/sdXY
resize2fs /dev/sdXY

mkswap /dev/sdXY
swapon /dev/sdXY
```

`ext4`


#### :books: 參考網站：
- https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1007907
- https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=2075729
- https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1004071
- https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=2076593
- https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1006371