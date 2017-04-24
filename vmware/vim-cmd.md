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
```

```console
shell> vim-cmd vmsvc/tools.install <vmid>

shell> vim-cmd hostsvc/net/info
shell> vim-cmd hostsvc/hosthardware
```

`Retrieves and displays the listsummary status from the vm.`
```console
shell> vim-cmd vmsvc/get.summary vmid
``` 

`Register a VM`
```console
shell> vim-cmd solo/registervm path_to_vmx_file
``` 

`Unregister a VM`
```console
shell> vim-cmd vmsvc/unregister vmid #
```

`Delete a VM`
```console 
shell> vim-cmd vmsvc/destroy vmid # 
```

`Get a listing of VMs on a host`
```console
shell> vim-cmd vmsvc/getallvms 
```

`Power on a VM`
```console
shell> vim-cmd vmsvc/power.on vmid $(vim-cmd vmsvc/getallvms | grep '' | awk '{$1}')
```

`Shutdown a VM`
```console
shell> vim-cmd vmsvc/power.shutdown vmid
```

`Reboot a VM`
```console
shell> vim-cmd vmsvc/power.reboot vmid
```

`Power off a VM`
```console
shell> vim-cmd vmsvc/power.off vmid
```

`Get the current power state of a VM`
```console
shell> vim-cmd vmsvc/power.getstate vmid
```

`Get the uptime for a VM`
```console
shell> vim-cmd vmsvc/get.summary vmid | grep uptimeSeconds
```

`Reset a VM`
```console
shell> vim-cmd vmsvc/power.reset vmid
```

`Determine if a VM has a snapshot`
```console
shell> vim-cmd vmsvc/get.snapshot vmid
```

`Take a snapshot of a VM`
```console
shell> vim-cmd vmsvc/snapshot.create vmid snapshot_name
```

`Remove a snapshot of a VM`
```console
shell> vim-cmd vmsvc/snapshot.remove vmid
```

```console
shell> vim-cmd vmsvc/power.hibernate vmid
```

```console
shell> vim-cmd vmsvc/snapshot.revert vmid snapshot_name
```

`Upgrade VMware Tools in a VM`
```console
shell> vim-cmd vmsvc/tools.upgrade vmid
```

`Display the IP address of a VM`
```console
shell> vim-cmd vmsvc/get.guest vmid |grep -m 1 "ipAddress = \""
```

```console
shell> vim-cmd vmsvc/power.suspend vmid
```

`Sets the Console window's resolution.`
```console
shell> vim-cmd vmsvc/setscreenres vmid width height
```

`Convert the virtual machine to a template.`
```console
shell> vim-cmd vmsvc/convert.toTemplate vmid
```

`Convert the template to a virtual machine.`
```console
shell> vim-cmd vmsvc/convert.toVm vmid
```

`Retrieves and displays the configuration object for the vm.`
```console
shell> vim-cmd vmsvc/get.config vmid
```

```console
shell> vim-cmd vimsvc/license --show

shell> vim-cmd hostsvc/datastore/listsummary
shell> vim-cmd hostsvc/datastore/summary datastore1
shell> vim-cmd hostsvc/datastore/listvm datastore1
```

---

```console
shell> vim-cmd vmsvc/getallvms
shell> vim-cmd vmsvc/power.shutdown vmid
shell> cd /vmfs/volumes/datastore1
shell> mkdir newexamplevm
shell> vmkfstools -i examplevm/examplevm.vmdk -d thin newexamplevm/newexamplevm.vmdk
shell> vim-cmd vmsvc/power.on vmid
```

```console
shell> vim-cmd vmsvc/getallvms
shell> vim-cmd vmsvc/snapshot.get vmid
shell> vim-cmd vmsvc/snapshot.removeall vmid
shell> vim-cmd vmsvc/snapshot.create vmid snapshot1 snapshot 0 0
shell> cd /vmfs/volumes/datastore1
shell> mkdir newexamplevm
shell> vmkfstools -i examplevm/examplevm.vmdk -d thin newexamplevm/newexamplevm.vmdk
shell> vim-cmd vmsvc/snapshot.removeall vmid
```

#### :books: 參考網站：
- [Cloning and converting virtual machine disks with vmkfstools](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1028042)
- https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1002310

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