`Prolific USB-Serial Cable driver`

```
shell> brew cask info pl2303
shell> brew cask install pl2303
```

---

```
==> Downloading http://prolificusa.com/files/PL2303_MacOSX_1.6.1_20160309.zip
######################################################################## 100.0%
==> Verifying checksum for Cask pl2303
==> Installing Cask pl2303
==> Running installer for pl2303; your password may be necessary.
==> Package installers may write to any location; options such as --appdir are ignored.
Password:
==> installer: Package name is Prolific USB to Serial Cable driver v1.6.1
==> installer: Installing at base path /
==> installer: The install was successful.
==> installer: The install requires restarting now.
🍺  pl2303 was successfully installed!
```

```
shell> ls /dev/cu.*
/dev/cu.Bluetooth-Incoming-Port  /dev/cu.iPhone-WirelessiAP  /dev/cu.usbserial

shell> screen /dev/cu.usbserial 9600
shell> screen /dev/cu.usbserial 38400
```

`Ctrl+a` `Ctrl+\`


---

```
shell> kextstat | grep prolific
  155    0 0xffffff7f84140000 0x6000     0x6000     com.prolific.driver.PL2303 (1.6.0) F6A6805D-685D-3E6D-BF81-106EBBC0A386 <130 41 5 4 3>

shell> ioreg -c IOSerialBSDClient | grep usbserial
```


---

```
******************************************************************************
* Copyright (c) 2010-2016 Hewlett Packard Enterprise Development LP          *
* Without the owner's prior written consent,                                 *
* no decompiling or reverse-engineering shall be allowed.                    *
******************************************************************************

User interface aux0 is available.



Please press ENTER.

Login authentication


Username:admin
Password:

<HPE>?
User view commands:
  initialize  Delete the startup configuration file and reboot system
  ipsetup     Assign an IP address to VLAN-interface 1
  password    Specify password of local user
  ping        Ping function
  quit        Exit from current command view
  reboot      Reboot system/board/card
  summary     Display summary information of the device.
  telnet      Establish one TELNET connection
  upgrade     Upgrade the system boot file or the Boot ROM program

<HPE>
```

```
IPV4: <System>ipsetup ip-address 192.168.88.57 24 default-gateway 192.168.88.1
IPV4: <System>ipsetup ip-address 192.168.88.60 24 default-gateway 192.168.88.1
IPV6: <System>ipsetup ipv6 address 2001::2 64 default-gateway 2001::1
<System> summary
<System> ping 192.168.88.1
<System> password
<System> quit
<System> reboot
```

```
Vlan-interface:                 1

Select menu option:             Summary
IP Method:                      DHCP
IP address:                     169.254.74.52
Subnet mask:                    255.255.0.0
Default gateway:

IPv6 Method:
IPv6 link-local address:
IPv6 subnet mask length:
IPv6 global address:
IPv6 subnet mask length:
IPv6 default gateway:

Mac address: 40B9-3C33-4A34

Current boot app is: flash:/jg924a-cmw520-r1115.bin
Next main boot app is: flash:/jg924a-cmw520-r1115.bin
Next backup boot app is: flash:/jg924a-cmw520-r1115_bak.bin

HPE Comware Platform Software
Comware Software, Version 5.20.99, Release 1115
Copyright (c) 2010-2016 Hewlett Packard Enterprise Development LP
HPE 1920-24G Switch uptime is 0 week, 6 days, 2 hours, 24 minutes

HPE 1920-24G Switch
128M    bytes DRAM
32M     bytes Flash Memory
Config Register points to Flash

Hardware Version is REV.A
Bootrom Version is 117
[SubSlot 0] 24GE+4SFP Hardware Version is REV.A
```


#### :books: 參考網站：
- http://www.prolific.com.tw/TW/ShowProduct.aspx?pcid=79
- http://h20564.www2.hpe.com/hpsc/doc/public/display?docId=mmr_kc-0118664
- http://h22208.www2.hpe.com/eginfolib/networking/docs/switches/K-KA-KB/15-18/5998-8160_ssw_mcg/content/ch06s10.html
