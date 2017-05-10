
<img src="http://i.imgur.com/Dd0Sffn.png" width="200">

<!-- <img src="http://i.imgur.com/t51VWq9.png" width="100"> -->

`app`

`osx`

`macos-sierra`

`macOS Sierra`

`Command ⌘`

`Option ⌥`

`Caps Lock ⇪`

`Control ⌃`

`Shift ⇧`

`Fn`

<img src="http://i.imgur.com/TyG4Hnl.png" width="600">


#### :books: 參考網站：
- [Keyboard_Shortcuts](http://www.sequelpro.com/docs/Keyboard_Shortcuts)

---

> <kbd>Command ⌘</kbd> + <kbd>Shift ⇧</kbd> + <kbd>+</kbd> 放大所選項目。

> <kbd>Command ⌘</kbd> + <kbd>Shift ⇧</kbd> + <kbd>-</kbd> 縮小所選項目。

> <kbd>Command ⌘</kbd> + <kbd>0</kbd>

**睡眠、登出和關機快速鍵**

> <kbd>Shift ⇧</kbd> + <kbd>Control ⌃</kbd> + <kbd>電源按鈕</kbd> 使顯示器進入睡眠。 

> <kbd>Command ⌘</kbd> + <kbd>Control ⌃</kbd> + <kbd>電源按鈕</kbd> 強制 Mac 重新啟動。 

> <kbd>Command ⌘</kbd> + <kbd>Shift ⇧</kbd> + <kbd>Option ⌥</kbd> + <kbd>Q</kbd> 立即登出 OS X 使用者帳號，系統不會要求確認。   

> <kbd>Command ⌘</kbd> + <kbd>Shift ⇧</kbd> + <kbd>Q</kbd> 登出 OS X 使用者帳號。系統會要求您確認。 

> <kbd>Command ⌘</kbd> + <kbd>Option ⌥</kbd> + <kbd>Control ⌃</kbd> + <kbd>電源按鈕</kbd> 結束所有 app，然後將 Mac 關機。如果任何開啟中文件尚有未儲存的變更，系統會詢問您是否要儲存。  

---

**Finder 快速鍵**

> <kbd>Command ⌘</kbd> + <kbd>E</kbd> 退出所選磁碟或卷宗。

> <kbd>Command ⌘</kbd> + <kbd>Shift ⇧</kbd> + <kbd>Delete</kbd> 清空垃圾桶。

> <kbd>Command ⌘</kbd> + <kbd>Shift ⇧</kbd> + <kbd>Option ⌥</kbd> + <kbd>Delete</kbd> 不顯示確認對話框便直接清空垃圾桶。

---

- **`Token`** `[ˋtokən]` `to・ken`
- **`Provider`** `[prəˋvaɪdɚ]` `提供者` `pro・vid・er`
- **`Field`** `[fild]` `欄位` `field`
- **`Communication`** `[kə͵mjunəˋkeʃən]` `通訊` `com・mu・ni・ca・tion`
- **`Macintosh`** [ˋmækɪn͵tɑʃ] `mac・in・tosh` 

---


- `Apple Pay`採用`Visa`的`Token`代碼化服務
- `Apple Pay`是基於`近場無線通訊` (`Near Field Communication`，`NFC`) 技術
- `Apple Pay`背後的關鍵技術之一是採用`Visa`的`Token`代碼化服務，讓消費者可以把真實卡換替換成一組代碼，來避免因手機遭竊、商店系統被駭而導致卡號被盜的風險。因此，在整個支付流程中，必須經過一個組織進行代碼轉換後，再與發卡銀行系統串接。而這個進行代碼轉換的組織可以是`Visa`、`MasterCard`、中國銀聯這類的國際組織，也可以是經過國際晶片卡發卡組織`EMVCo`驗證過的`TSP業者` (`Token Services Provider`)
- `OS X`是`蘋果公司`以`Unix`為基礎所開發的圖形化使用者介面作業系統，專屬於`Macintosh`電腦，是`Mac OS`的最終版本。
- `OS X`作業系統包含兩個主要的部分：核心名為「`Darwin`」，是以`FreeBSD`原始碼和`Mach`微核心為基礎，由`蘋果公司`和獨立開發者社群協力開發，以及一個名為「`Aqua`」之專有版權的圖形使用者介面，由蘋果電腦自行開發。 
- 以往的`OS X`版本是以大型貓科動物命名，例如Mac OS X v10.7被稱為「`Lion`」，隨著2013年6月OS X Mavericks的公布，命名方式開始轉為採用加州地標。 


`OS X`作業系統

- `山獅` (`Mountain Lion`, 10.8)
- `小牛` (`Mavericks`, 10.9)
- `優勝美地` (`Yosemite`, 10.10)

#### :books: 參考網站：
- [sierra](http://www.apple.com/tw/macos/sierra/)
- [macOS Sierra](https://itunes.apple.com/tw/app/macos-sierra/id1127487414?l=zh&mt=12)

---

```console
shell> dscl . -read /Users/$(whoami) UserShell
```

---

`sips -- scriptable image processing system.`

```console
shell> sips -s format jpeg --out rose.jpg rose.png
shell> sips -s format png  --out rose.png rose.jpg
shell> sips -Z 640 *.jpg
```

---

`purge -- force disk cache to be purged (flushed and emptied)`

```console
shell> sudo purge
```

---

`networksetup -- configuration tool for network settings in System Preferences.`

```console
shell> networksetup -listallnetworkservices
```
```
An asterisk (*) denotes that a network service is disabled.
Wi-Fi
Bluetooth PAN
Thunderbolt Bridge
```
```console
shell> networksetup -getinfo Wi-Fi
```
```
DHCP Configuration
IP address: 192.168.8.114
Subnet mask: 255.255.255.0
Router: 192.168.8.88
Client ID: 
IPv6: Automatic
IPv6 IP address: none
IPv6 Router: none
Wi-Fi ID: a0:99:9b:08:cb:87
```
```console
shell> networksetup -listallhardwareports
```
```
Hardware Port: Wi-Fi
Device: en0
Ethernet Address: a0:99:9b:08:cb:87

Hardware Port: Bluetooth PAN
Device: en3
Ethernet Address: a0:99:9b:08:cb:88

Hardware Port: Thunderbolt 1
Device: en1
Ethernet Address: 6a:00:00:93:8e:00

Hardware Port: Thunderbolt 2
Device: en2
Ethernet Address: 6a:00:00:93:8e:01

Hardware Port: Thunderbolt Bridge
Device: bridge0
Ethernet Address: 6a:00:00:93:8e:00

VLAN Configurations
===================
```console
shell> networksetup -getairportpower en0
```
```
Wi-Fi Power (en0): On
```
```console
shell> networksetup -setairportpower on
shell> networksetup -setairportpower off
```

#### :books: 參考網站：
- [networksetup](https://developer.apple.com/legacy/library/documentation/Darwin/Reference/ManPages/man8/networksetup.8.html)

---

`scutil -- Manage system configuration parameters`

```console
shell> sudo scutil --dns
shell> sudo scutil --proxy
shell> sudo scutil --get ComputerName
shell> sudo scutil --set ComputerName ""
shell> sudo scutil --get HostName
shell> sudo scutil --set HostName ""       
```

#### :books: 參考網站：
- [scutil](https://developer.apple.com/legacy/library/documentation/Darwin/Reference/ManPages/man8/scutil.8.html)

---

`在 OS X 重置 DNS 快取`

```console
shell> sudo killall -HUP mDNSResponder
shell> sudo discoveryutil mdnsflushcache
shell> sudo dscacheutil -flushcache
```

#### :books: 參考網站：
- [在 OS X 重置 DNS 快取](https://support.apple.com/zh-tw/HT202516)

---

```console
shell> echo Hello, World | pbcopy
shell> pbpaste
```

#### :books: 參考網站：
- [pbcopy](https://developer.apple.com/legacy/library/documentation/Darwin/Reference/ManPages/man1/pbcopy.1.html)

---

`dot_clean -- Merge ._* files with corresponding native files.`

```console
shell> dot_clean /Volumes/test
shell> dot_clean .
```

#### :books: 參考網站：
- [dot_clean](https://developer.apple.com/legacy/library/documentation/Darwin/Reference/ManPages/man1/dot_clean.1.html)

---

`say - Convert text to audible speech`


```console
shell> say Hello, World
shell> say -v Alex -o hi -f hello_world.txt
shell> say -v ting-ting Hello, World
shell> say -v mei-jia Hello, World
shell> say -v sin-ji Hello, World
shell> say Hello, World
```

#### :books: 參考網站：
- [say](https://developer.apple.com/legacy/library/documentation/Darwin/Reference/ManPages/man1/say.1.html)

---

`hdiutil -- manipulate disk images (attach, verify, create, etc)`

```console
shell> hdiutil imageinfo ubuntu-16.04-server-i386.iso
shell> hdiutil imageinfo 2016-09-23-raspbian-jessie-lite.img
shell> hdiutil burn ubuntu-16.04-server-i386.iso
shell> hdiutil makehybrid -iso -joliet -o myVolume.iso /Volumes/myVolume
```

#### :books: 參考網站：
- [hdiutil](https://developer.apple.com/legacy/library/documentation/Darwin/Reference/ManPages/man1/hdiutil.1.html)

---

`/private/etc/hosts`

---

```console
shell> route get default
shell> route get default | grep gateway
shell> netstat -rn | grep default | awk '{ print $2 }'
```

---

```console
shell> ditto src dst_directory 
```

#### :books: 參考網站：
- [ditto](https://developer.apple.com/library/mac/documentation/Darwin/Reference/ManPages/man1/ditto.1.html)

---

```console
shell> softwareupdate --list 
```

```
Software Update Tool
Copyright 2002-2015 Apple Inc.

Finding available software
Software Update found the following new or updated software:
   * OS X El Capitan Update-10.11.6
	OS X El Capitan 更新 (10.11.6), 471282K [recommended] [restart]
```

```console
shell> softwareupdate --install Safari8.0.6Yosemite-8.0.6
shell> softwareupdate --install --all 
```

#### :books: 參考網站：
- [softwareupdate](https://developer.apple.com/legacy/library/documentation/Darwin/Reference/ManPages/man8/softwareupdate.8.html)

---

```console
shell> system_profiler SPSoftwareDataType
```

```
Software:

    System Software Overview:

      System Version: OS X 10.11.5 (15F34)
      Kernel Version: Darwin 15.5.0
      Boot Volume: Untitled
      Boot Mode: Normal
      Computer Name: Apple’s MacBook Air
      User Name: Apple (apple)
      Secure Virtual Memory: Enabled
      System Integrity Protection: Enabled
      Time since boot: 6 days 5:24
```

```console
shell> sw_vers
shell> sw_vers -productName
shell> sw_vers -productVersion
shell> sw_vers -buildVersion
```

```
ProductName:	Mac OS X
ProductVersion:	10.11.5
BuildVersion:	15F34

ProductName:	Mac OS X
ProductVersion:	10.12.1
BuildVersion:	16B2555
```

#### :books: 參考網站：
- [system_profiler](https://developer.apple.com/legacy/library/documentation/Darwin/Reference/ManPages/man8/system_profiler.8.html)
- [sw_vers](https://developer.apple.com/legacy/library/documentation/Darwin/Reference/ManPages/man1/sw_vers.1.html)

---

```console
shell> defaults read com.apple.desktopservices 
shell> defaults write com.apple.desktopservices DSDontWriteNetworkStores true
```

```console
shell> defaults read com.apple.appstore
shell> defaults write com.apple.appstore ShowDebugMenus true
shell> defaults delete com.apple.appstore ShowDebugMenus 
```

```console
shell> defaults read com.apple.finder
shell> defaults write com.apple.finder ShowHardDrivesOnDesktop true
```

#### :books: 參考網站：
- [defaults](https://developer.apple.com/legacy/library/documentation/Darwin/Reference/ManPages/man1/defaults.1.html)

---

### 磁碟工具程式
```console
shell> diskutil list
shell> diskutil info /dev/disk2

shell> diskutil unmount /Volumes/Untitled

shell> diskutil unmountDisk /dev/disk2
shell> diskutil eject /dev/disk2
```

```
/dev/disk0 (internal, physical):
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *500.3 GB   disk0
   1:                        EFI EFI                     209.7 MB   disk0s1
   2:          Apple_CoreStorage Macintosh HD            499.4 GB   disk0s2
   3:                 Apple_Boot Recovery HD             650.0 MB   disk0s3

/dev/disk1 (internal, virtual):
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:                            Macintosh HD           +499.0 GB   disk1
                                 Logical Volume on disk0s2
                                 3CC9C26E-BF69-4488-8E6C-FA12C20CACBB
                                 Unencrypted

/dev/disk2 (internal, physical):
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:     FDisk_partition_scheme                        *31.1 GB    disk2
   1:             Windows_FAT_32 NO NAME                 31.1 GB    disk2s1

/dev/disk3 (external, physical):
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:     FDisk_partition_scheme                        *16.1 GB    disk3
   1:             Windows_FAT_32 NO NAME                 16.1 GB    disk3s1
```

```console
shell> disktype
```

#### :books: 參考網站：
- [diskutil](https://developer.apple.com/legacy/library/documentation/Darwin/Reference/ManPages/man8/diskutil.8.html)

---
```console
shell> df -hl
```
---

> 如果管理者帳號沒有密碼（空密碼），必須先提供密碼給該使用者，然後才使用 sudo 指令。
使用 sudo 指令完畢之後，可以再次變更帳號密碼，不過建議管理者帳號最好還是要設定非空白密碼。

```console
shell> sudo -i
shell> visudo
```
```
[...]
# User privilege specification
root    ALL=(ALL) ALL
%admin  ALL=(ALL) NOPASSWD: ALL
[...]
```

---

`Xcode`

```console
shell> xcodebuild

shell> xcode-select --version
shell> xcode-select --install
```

#### :books: 參考網站：
- [xcode](https://developer.apple.com/xcode/)
- [xcode-select](https://developer.apple.com/legacy/library/documentation/Darwin/Reference/ManPages/man1/xcode-select.1.html)
- [xcodebuild](https://developer.apple.com/legacy/library/documentation/Darwin/Reference/ManPages/man1/xcodebuild.1.html)

---

```console
shell> tell application "Finder" to quit
shell> tell application "Finder" to launch
```

```console
shell> osascript -e "tell application \"Safari\" to activate"
```

#### :books: 參考網站：
- https://developer.apple.com/library/content/documentation/AppleScript/Conceptual/AppleScriptLangGuide/reference/ASLR_cmds.html

---

`.bash_profile`

```
export CLICOLOR=1

if [ -f $(brew --prefix)/etc/bash_completion ]; then
  . $(brew --prefix)/etc/bash_completion
fi
```

<!--
Fusion 8 Pro
```
FA3RK-FHGD5-M88TZ-V4WEZ-MVAW0
FU75U-4KD5L-0845Z-JEXNZ-MLKD8
UV7XK-4PXEJ-080WY-4WXQT-NC0ZF
VC79R-6NF81-M84XZ-VNW5G-NKUW8
GC1HA-01Z14-H8D2P-04NNZ-Z6RY0
```
-->

---

#### :books: 參考網站：
[http://support.apple.com/kb/HT1629](http://support.apple.com/kb/HT1629)
[https://developer.apple.com/library/mac/documentation/Darwin/Reference/Manpages/man8/diskutil.8.html](https://developer.apple.com/library/mac/documentation/Darwin/Reference/Manpages/man8/diskutil.8.html)
[http://developer.apple.com/library/mac/#documentation/AppleScript/Conceptual/AppleScriptLangGuide/reference/ASLR_cmds.html](http://developer.apple.com/library/mac/#documentation/AppleScript/Conceptual/AppleScriptLangGuide/reference/ASLR_cmds.html)

---

![](https://support.apple.com/library/content/dam/edam/applecare/images/zh_TW/mac_apps/itunes/macos-itunes12-5-device-callout.jpg)
![](https://support.apple.com/library/content/dam/edam/applecare/images/en_US/mac_apps/itunes/osx-elcapitan-itunes12-4-device-iphone-icon.png)
![](https://support.apple.com/library/content/dam/edam/applecare/images/zh_TW/mac_apps/itunes/macos-itunes12-5-device-summary.jpg)
#### :books: 參考網站：
- https://support.apple.com/zh-tw/HT201253
- [使用 AirDrop 從 Mac 傳送內容](https://support.apple.com/zh-tw/HT203106)
- [透過 Apple ID 裝置列表來查看您所登入的裝置](https://support.apple.com/zh-tw/HT205064)
