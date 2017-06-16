`Prolific USB-Serial Cable driver`

```console
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

```console
shell> ls /dev/cu.*
/dev/cu.Bluetooth-Incoming-Port  /dev/cu.iPhone-WirelessiAP  /dev/cu.usbserial

shell> screen /dev/cu.usbserial 9600
shell> screen /dev/cu.usbserial 38400
```

`Ctrl+a` `Ctrl+\`

---

```
IPV4: <System>ipsetup ip-address 192.168.1.2 24 default-gateway 192.168.1.1
IPV6: <System>ipsetup ipv6 address 2001::2 64 default-gateway 2001::1
<System> summary
```


#### :books: 參考網站：
- http://www.prolific.com.tw/TW/ShowProduct.aspx?pcid=79
- http://h20564.www2.hpe.com/hpsc/doc/public/display?docId=mmr_kc-0118664
