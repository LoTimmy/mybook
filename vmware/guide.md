> 虛擬化系統主要可分為全虛擬化與半虛擬化兩種，前者是安裝在原本作業系統之上，如`VMware Server`；而後者則直接安裝在伺服器上、不須架構在一般作業系統上，像`Citrix XenServer`、`VMware ESX`等。兩者相較，半虛擬化的效能比較佳，因此在實務上，也都是以此建置虛擬化系統。      
> `開放虛擬化格式` (`Open Virtualization Format`, `OVF`) 是 Distributed Management Task Force, Inc. 提供的封裝標準，其設計目的是要協助移植和部署虛擬裝置。

#### :books: 參考網站：
- [ovf](https://www.vmware.com/support/developer/ovf/)
- [Sample ovftool command syntax to export, deploy, and 1-step export and deploy packages in vCenter Server (1038709)](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1038709)
- [VMware products and their virtual hardware version](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1003746)
- [VMware 产品及其虚拟硬件版本](https://kb.vmware.com/selfservice/search.do?cmd=displayKC&docType=kc&docTypeID=DT_KB_1_1&externalId=2048332)

```
shell> vmware -vl
VMware ESXi 5.0.0 build-469512
VMware ESXi 5.0.0 GA

VMware ESXi 6.0.0 build-3620759
VMware ESXi 6.0.0 Update 2
```

---

`open-vm-tools`

```
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

```
shell> ovftool "%HOMEPATH%\Documents\Virtual Machines\xenial\xenial.vmx" "%HOMEPATH%\Documents/xenial.ova"
shell> ovftool "%HOMEPATH%\Documents\Virtual Machines\yakkety\yakkety.vmx" "%HOMEPATH%\Documents/yakkety.ova"

shell> ovftool "%HOMEPATH%\Documents/xenial.ova"
shell> ovftool "%HOMEPATH%\Documents/yakkety.ova"
```

```
shell> ovftool ubuntu-1604.vmwarevm/ubuntu-1604.vmx ~/Documents/ubuntu
shell> ovftool --acceptAllEulas ~/Documents/"Virtual Machines.localized/Windows 7 x64.vmwarevm/Windows 7 x64.vmx" ~/Documents/windows7.ova
```

```
shell> ovftool ~/Documents/ubuntu-1604.ova
```

`Rename the OVF Package`

```
shell> ovftool “Windows 7.ovf” win7.ovf
```

`Converting a VMX File to an ESXi host`

```
shell> ovftool /ovfs/my_vm.vmx vi://username:pass@my_esx_host
```

```
shell> ovftool package.ovf vi://my.esx-machine.example.com/
shell> ovftool package.ovf vi://username:pass@my.esx-machine.example.com/

shell> ovftool -ds=datastore1 --net:nat="VM Network" ubuntu-1604.ova vi://root@192.168.168.196
shell> ovftool -ds=datastore2 --net:nat="VM Network" ubuntu-1604.ova vi://root@192.168.168.196
```

```
shell> chmod +x VMware-ovftool-4.0.0-2301625-lin.x86_64.bundle
shell> ovftool --help
```

#### :books: 參考網站：
- [ovftool](https://www.vmware.com/support/developer/ovf/ovf410/ovftool-410_userguide.pdf)
- [ovftool](https://www.vmware.com/support/developer/ovf/ovf301/ovftool-301-userguide.pdf)
- [ovftool](https://www.vmware.com/support/developer/ovf/ovf20/ovftool_201_userguide.pdf)
- [ovftool](https://my.vmware.com/web/vmware/details?productId=491&downloadGroup=OVFTOOL410)

---

```
shell> chmod +x VMware-VIX-1.13.2-1744117.x86_64.bundle
shell> ./VMware-VIX-1.13.2-1744117.x86_64.bundle
```

```
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

```
shell> /usr/bin/host_reboot.sh
shell> /usr/bin/host_shutdown.sh
```
---

```
Switch VMware Fusion to Full Screen View
Use the ⌘+Control+F keyboard shortcut to switch to Full Screen view.
```

---

`VirtualMachineName`

```
shell> smbiosDump
shell> esxcfg-info | less -I
```
#### :books: 參考網站：
- https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1003587
- https://kb.vmware.com/selfservice/search.do?cmd=displayKC&docType=kc&docTypeID=DT_KB_1_1&externalId=2086454

```
shell> esxcfg-nics --list
shell> esxcfg-nics -l

shell> vsish

shell> vmware --version
VMware ESXi 5.0.0 build-469512
shell> vmware -v
shell> vmware --level
VMware ESXi 5.0.0 GA
```


```
shell> esxcfg-nics --list
shell> esxcfg-vswitch --list

shell> esxcfg-vmknic --list

shell> esxcfg-route --list
shell> esxcfg-route -l

shell> esxcfg-route -a default 192.168.1.151
```

```
shell> /sbin/powerOffVms
shell> /sbin/poweroff

shell> /bin/reboot
```

```
RemoteDisplay.vnc.enabled = "TRUE"
RemoteDisplay.vnc.port = "portnumber"
```

**`5901` to `6001`**

---

```
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

```
shell> /etc/init.d/SSH restart
```

---


```
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

```
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
shell> ifconfig | grep -A2 vmnet
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
shell> swapoff /dev/sdXY
shell> resize2fs /dev/sdXY

shell> mkswap /dev/sdXY
shell> swapon /dev/sdXY
```

`ext4`


#### :books: 參考網站：
- https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1007907
- https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=2075729
- https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1004071
- https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=2076593
- https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1006371
- https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=2075199

---

```
shell> esxcli system settings advanced set -o /Net/GuestIPHack -i 1
```

```
shell> cat <<EOF > /etc/vmware/firewall/vncServer.xml
<ConfigRoot>
  <service>
    <id>vncServer</id>
    <rule id='0000'>
      <direction>inbound</direction>
      <protocol>tcp</protocol>
      <porttype>dst</porttype>
      <port>
        <begin>5900</begin>
        <end>5999</end>
      </port>
    </rule>
    <enabled>true</enabled>
    <required>false</required>
  </service>
</ConfigRoot>
EOF
shell> esxcli network firewall refresh
shell> esxcli network firewall ruleset list
```

#### :books: 參考網站：
- https://www.netiq.com/documentation/cloudmanager22/ncm22_reference/data/bxzaz5n.html
- https://docs.vmware.com/en/VMware-Fusion/8.0/rn/fusion-858-release-notes.html

---

`-locale en_US`
```
"C:\Program Files (x86)\VMware\Infrastructure\Virtual Infrastructure Client\Launcher\VpxClient.exe" -locale en_US
```
