telnet://192.168.42.253

```
User Access Verification
Password: 
Switch> enable

Switch# configure terminal
Switch# config t

Switch# show boot
BOOT path-list:       
Config file:          flash:/config.text
Private Config file:  flash:/private-config.text
Enable Break:         no
Manual Boot:          no
HELPER path-list:     
NVRAM/Config file
      buffer size:    32768


Switch# show version
Cisco Internetwork Operating System Software 
IOS (tm) C2950 Software (C2950-I6Q4L2-M), Version 12.1(13)EA1, RELEASE SOFTWARE (fc1)
Copyright (c) 1986-2003 by cisco Systems, Inc.
Compiled Tue 04-Mar-03 02:14 by yenanh
Image text-base: 0x80010000, data-base: 0x805A8000

ROM: Bootstrap program is CALHOUN boot loader

C2950 uptime is 1 week, 2 days, 5 hours, 52 minutes
System returned to ROM by power-on
System image file is "flash:/c2950-i6q4l2-mz.121-13.EA1.bin"

cisco WS-C2950SX-24 (RC32300) processor (revision F0) with 20839K bytes of memory.
Processor board ID FHK0743Z1BJ
Last reset from system-reset
Running Standard Image
24 FastEthernet/IEEE 802.3 interface(s)
2 Gigabit Ethernet/IEEE 802.3 interface(s)

32K bytes of flash-simulated non-volatile configuration memory.
Base ethernet MAC Address: 00:0E:38:5E:F3:C0
Motherboard assembly number: 73-8135-06
Power supply part number: 34-0965-01
Motherboard serial number: FOC07430MRG
Power supply serial number: DAB0740DLFY
Model revision number: F0
Motherboard revision number: A0
Model number: WS-C2950SX-24
System serial number: FHK0743Z1BJ
Configuration register is 0xF
```

```
Switch> enable
Switch# config t
Enter configuration commands, one per line.  End with CNTL/Z.
Switch(config)# ntp server time1.google.com
Switch(config)# ntp server time2.google.com
Switch(config)# ntp server time3.google.com
Switch(config)# ntp server time4.google.com
Switch(config)# end
```

```
Switch# show interfaces gigabitethernet0/2
```

```
Switch(config-if)# authentication order mab webauth
```

```
Switch# ?
Exec commands:
  <1-99>           Session number to resume
  access-enable    Create a temporary Access-List entry
  access-template  Create a temporary Access-List entry
  archive          manage archive files
  cd               Change current directory
  clear            Reset functions
  clock            Manage the system clock
  cns              CNS subsystem
  configure        Enter configuration mode
  connect          Open a terminal connection
  copy             Copy from one file to another
  debug            Debugging functions (see also 'undebug')
  delete           Delete a file
  dir              List files on a filesystem
  disable          Turn off privileged commands
  disconnect       Disconnect an existing network connection
  dot1x            IEEE 802.1X commands
  enable           Turn on privileged commands
  erase            Erase a filesystem
  exit             Exit from the EXEC
  format           Format a filesystem
  fsck             Fsck a filesystem
  help             Description of the interactive help system
  lock             Lock the terminal
  login            Log in as a particular user
  logout           Exit from the EXEC
  mkdir            Create new directory
  more             Display the contents of a file
  name-connection  Name an existing network connection
  no               Disable debugging functions
  ping             Send echo messages
  pwd              Display current working directory
  rcommand         Run command on remote switch
  reload           Halt and perform a cold restart
  rename           Rename a file
  resume           Resume an active network connection
  rmdir            Remove existing directory
  rsh              Execute a remote command
  send             Send a message to other tty lines
  setup            Run the SETUP command facility
  show             Show running system information
  systat           Display information about terminal lines
  telnet           Open a telnet connection
  terminal         Set terminal line parameters
  test             Test subsystems, memory, and interfaces
  traceroute       Trace route to destination
  tunnel           Open a tunnel connection
  udld             UDLD protocol commands
  undebug          Disable debugging functions (see also 'debug')
  verify           Verify a file
  vlan             Configure VLAN parameters
  vmps             VMPS actions
  vtp              Configure global VTP state
  where            List active connections
  write            Write running configuration to memory, network, or terminal

```

- http://www.cisco.com/c/en/us/td/docs/switches/lan/catalyst2960/software/release/12-2_55_se/command/reference/2960_cr/cli1.html
- http://www.cisco.com/c/en/us/td/docs/switches/lan/catalyst2960/software/release/12-2_55_se/command/reference/2960_cr/cli2.html
- http://www.cisco.com/c/en/us/td/docs/switches/lan/catalyst2960/software/release/12-2_55_se/command/reference/2960_cr/cli3.html
- http://www.cisco.com/c/en/us/td/docs/ios-xml/ios/sec_usr_ssh/configuration/15-s/sec-usr-ssh-15-s-book/sec-secure-shell-algorithm-ccc.html
