
`User Name` `admin`

`HP 1920G Switch` → `Network` → `Service`
✓ `Enable Telnet service`
✓ `Enable HTTP service`

`HP 1920G Switch` → `Authentication` → `Users`


```console
Connecting to 192.168.8.214:23...
Connection established.
To escape to local shell, press 'Ctrl+Alt+]'.

******************************************************************************
* Copyright (c) 2010-2015 Hewlett-Packard Development Company, L.P.          *
* Without the owner's prior written consent,                                 *
* no decompiling or reverse-engineering shall be allowed.                    *
******************************************************************************


Login authentication


Username:admin
Password:
<HP 1920G Switch>
```

`Jinhua1920unauthorized`

```console
<HP 1920G Switch>_cmdline-mode on
All commands can be displayed and executed. Continue? [Y/N]y
Please input password:**********************
Warning: Now you enter an all-command mode for developer's testing, some commands may affect operation by wrong use, please carefully use it with our engineer's direction.
<HP 1920G Switch>?
User view commands:
  archive        Specify archive settings
  backup         Backup next startup-configuration file to TFTP server
  boot-loader    Set boot loader
  bootrom        Update/read/backup/restore bootrom
  cd             Change current directory 
  clock          Specify the system clock
  cluster        Run cluster command
  copy           Copy from one file to another 
  crypto-digest  Compute the hash digest for a specified file
  debugging      Enable system debugging functions
  delete         Delete a file 
  dir            List files on a file system 
  display        Display current system information
  fixdisk        Recover lost chains in storage device
  format         Format the device
  free           Clear user terminal interface
  ftp            Open FTP connection 
  initialize     Delete the startup configuration file and reboot system
  ipc            Interprocess communication
  ipsetup        Assign an IP address to VLAN-interface 1 
  lock           Lock current user terminal interface
  logfile        Specify log file configuration
  mkdir          Create a new directory 
  more           Display the contents of a file 
  move           Move the file 
  ntdp           Run NTDP commands
  password       Specify password of local user
  ping           Ping function 
  pwd            Display current working directory 
  quit           Exit from current command view
  reboot         Reboot system/board/card
  rename         Rename a file or directory 
  reset          Reset operation
  restore        Restore next startup-configuration file from TFTP server 
  rmdir          Remove an existing directory 
  save           Save current configuration
  schedule       Schedule system task
  scp            Secure copy
  screen-length  Specify the lines displayed on one screen
  send           Send information to other user terminal interface
  sftp           Establish one SFTP connection 
  ssh2           Establish a secure shell client connection 
  stack          Switch stack system
  startup        Specify system startup parameters 
  summary        Display summary information of the device.
  super          Set the current user priority level 
  system-view    Enter the System View
  telnet         Establish one TELNET connection 
  terminal       Set the terminal line characteristics 
  tftp           Open TFTP connection 
  tracert        Trace route function 
  undelete       Recover a deleted file 
  undo           Cancel current setting
  upgrade        Upgrade the system boot file or the Boot ROM program 
  xmodem         Establish an xmodem connection
```

```console
<HP 1920G Switch> display current-configuration
```

```
sysname HP 1920G Switch
sysname HP   

clock timezone Taipei add 08:00:00
telnet server enable
ssh server enable

local-user admin    
password cipher $c$3$lOtYo1ghyhmBzuZr3qSQS6s5yP/MfJ/eRSkW    
authorization-attribute level 3    
service-type ssh telnet terminal   





ntp-service unicast-server 192.168.88.1

interface Vlan-interface1
 ip address dhcp-alloc

interface GigabitEthernet1/0/1
 port auto-power-down
 stp edged-port enable

interface GigabitEthernet1/0/1    
poe enable    
stp edged-port enable   



snmp-agent
snmp-agent local-engineid 383030303633413236353133354338413338304443353641
snmp-agent community read public
snmp-agent sys-info version v2c v3


```

```
<HP 1920G Switch>sys   
System View: return to User View with Ctrl+Z.
[HP 1920G Switch]

```




#### :books: 參考網站：
- http://h20564.www2.hpe.com/hpsc/doc/public/display?docId=emr_na-c03690685
- http://h22208.www2.hpe.com/eginfolib/networking/docs/switches/common/15-18/5998-8158_bog/content/ch03s03.html