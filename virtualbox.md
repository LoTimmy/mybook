
- [VirtualBox](https://www.virtualbox.org/)
- [Chapter 6. Virtual networking](https://www.virtualbox.org/manual/ch06.html)
- [Chapter 8. VBoxManage](https://www.virtualbox.org/manual/ch08.html)
- [Chapter 9. Advanced topics](https://www.virtualbox.org/manual/ch09.html)


![](http://i.imgur.com/bZfplic.png)

```console
shell> cd C:\Program Files\Oracle\VirtualBox
shell> VBoxManage internalcommands createrawvmdk -filename D:\VirtualBox\USB.vmdk -rawdisk \\.\PhysicalDrive3  
```

![](http://i.imgur.com/9ou2yiK.png)

```console
shell> VBoxManage internalcommands createrawvmdk -filename /path/to/USB.vmdk -rawdisk /dev/sda
```

```console
shell> VBoxManage startvm "Windows XP"
shell> VBoxManage modifyvm "Windows XP" --memory 512
shell> VBoxManage showvminfo "Windows XP"

shell> VBoxManage list extpacks
shell> VBoxManage list ostypes
shell> VBoxManage list vms
shell> VBoxManage list hostinfo
shell> VBoxManage list runningvms
shell> VBoxManage list -l runningvms

shell> VBoxManage import WindowsXp.ovf --dry-run

shell> VBoxManage extpack cleanup

shell> VBoxManage createvm --name "SUSE 10.2" --register

shell> VBoxManage unregistervm Ubuntu --delete  
```

![](http://i.imgur.com/Da92KYY.png)
![](http://i.imgur.com/OalywYf.png)
![](http://i.imgur.com/Aw87wCo.png)
![](http://i.imgur.com/DAm1o5S.png)
![](http://i.imgur.com/cwyIRdC.png)
![](http://i.imgur.com/DYgpdtt.png)
![](http://i.imgur.com/HMCLUo3.png)
![](http://i.imgur.com/SB8mAJp.png)

```
Name:            Ubuntu
Guest OS:        Ubuntu (32-bit)
Memory size:     768MB
VRAM size:       12MB
Number of CPUs:  1
Storage Controller Name (1):            SATA
Storage Controller Type (1):            IntelAhci
NIC 1:           MAC: 080027201FF8, Attachment: Bridged Interface 'Realtek PCIe GBE Family Controller', Cable connected: on, Trace: off (file: none), Type: 82540EM, Reported speed: 0 Mbps, Boot priority: 0, Promisc Policy: deny, Bandwidth group: none
```

```console
shell> VBoxManage createvm --name "Ubuntu" --ostype Ubuntu --register 
shell> VBoxManage showvminfo Ubuntu
shell> VBoxManage modifyvm Ubuntu --cpus 1 --memory 768 --vram 8 
shell> VBoxManage modifyvm Ubuntu --nic1 bridged --bridgeadapter1 eth0  
shell> VBoxManage createhd --filename "%HOMEPATH%\VirtualBox VMs\Ubuntu\Ubuntu.vdi" --size 8192 --variant Standard

shell> VBoxManage storagectl Ubuntu --name SATA --add sata --bootable on
shell> VBoxManage storageattach Ubuntu --storagectl SATA --port 0 --device 0 --type hdd --medium "%HOMEPATH%\VirtualBox VMs\Ubuntu\Ubuntu.vdi"

shell> VBoxManage storagectl Ubuntu --name IDE --add ide
shell> VBoxManage storageattach Ubuntu --storagectl IDE --port 0 --device 0 --type dvddrive --medium ubuntu-16.04-server-i386.iso
shell> VBoxManage startvm Ubuntu    
```

```console
shell> VBoxManage natnetwork add --netname natnet1 --network "192.168.15.0/24" --enable
shell> VBoxManage natnetwork add --netname natnet1 --network "192.168.15.0/24" --enable --dhcp on

shell> VBoxManage natnetwork modify --netname natnet1 --dhcp on
shell> VBoxManage natnetwork modify --netname natnet1 --dhcp off

shell> VBoxManage natnetwork start --netname natnet1
shell> VBoxManage natnetwork stop --netname natnet1
shell> VBoxManage natnetwork remove --netname natnet1

shell> VBoxManage natnetwork modify --netname natnet1 --port-forward-4 "ssh:tcp:[]:1022:[192.168.15.5]:22"
shell> VBoxManage natnetwork modify --netname natnet1 --port-forward-4 delete ssh

shell> VBoxManage list natnetworks
```


```
shell> VBoxManage export Ubuntu  --output Ubuntu.ovf
shell> VBoxManage import Ubuntu.ovf 
shell> VBoxManage import Ubuntu.ovf --dry-run  
```

```
VirtualBox VMs

MacOS_64
MacOS
MacOS106
MacOS106_64
MacOS107_64
MacOS108_64
MacOS109_64
MacOS1010_64
MacOS1011_64

Linux_64
Linux

Ubuntu_64
Ubuntu
Debian
Debian_64

Fedora
Fedora_64
RedHat
RedHat_64

Other

Windows31
Windows95
Windows98
Windows2000
WindowsXP
WindowsXP_64
Windows2003
Windows2003_64
Windows2008
Windows2008_64
Windows7
Windows7_64
Windows8
Windows8_64
Windows81
Windows81_64
Windows2012_64
Windows10
Windows10_64
```

- [VBoxManage](http://manpages.ubuntu.com/manpages/precise/man1/VBoxManage.1.html)
