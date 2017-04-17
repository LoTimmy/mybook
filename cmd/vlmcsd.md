`kms-server`

`vlmcsd - a fully Microsoft compatible KMS server`

`vlmcs - a client for testing and/or charging KMS servers`


```console
shell> apt-get install p7zip-full

shell> wget http://rghost.net/download/62BgHwKq9/3aca2cf0274480ba9a34928220b549511fb4c515/3aca2cf0274480ba9a34928220b549511fb4c515/vlmcsd-svn818-2016-03-07-Hotbird64.7z

shell> 7za x vlmcsd-svn818-2016-03-07-Hotbird64.7z -o./kms-server -p2016 
```

```console
shell> man man/vlmcsd.8
shell> man man/vlmcs.1
shell> man man/vlmcsd.7
shell> man man/vlmcsd.ini.5
```

```
binaries/Linux/intel/static/
├── vlmcsdmulti-x64-musl-static
├── vlmcsdmulti-x86-musl-static
├── vlmcsd-x64-musl-static
├── vlmcsd-x86-musl-static
├── vlmcsd-x86-musl-static-threads
├── vlmcs-x64-musl-static
└── vlmcs-x86-musl-static

0 directories, 7 files
```

```console
shell> vlmcsd -De
shell> vlmcsd -l /var/log/vlmcsd.log
shell> vlmcsd -L 192.168.1.17
```

```console
shell> net start vlmcsd
shell> vlmcsd -s -U /n -l C:\logs\vlmcsd.log
```

```console
shell> ./vlmcsdmulti-x64-musl-static
vlmcsdmulti svn818, built 2016-03-07 23:06:06 UTC

Usage:
	./vlmcsdmulti-x64-musl-static vlmcsd [<vlmcsd command line>]
	./vlmcsdmulti-x64-musl-static vlmcs [<vlmcs command line>]

shell> ./vlmcsdmulti-x64-musl-static vlmcsd
shell> ./vlmcsdmulti-x64-musl-static vlmcs
```

```
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:1688            0.0.0.0:*               LISTEN      14712/vlmcsdmulti-x
tcp6       0      0 :::1688                 :::*                    LISTEN      14712/vlmcsdmulti-x
```

---

```console
shell> curl -sSL https://github.com/Wind4/vlmcsd/releases/download/svn1108/binaries.tar.gz -o binaries.tar.gz \
 && tar zxf binaries.tar.gz \
 && cp binaries/Linux/intel/static/vlmcsd-x86-musl-static /usr/bin/vlmcsd \
 && chmod 0755 /usr/bin/vlmcsd \
 && rm -rf binaries/ binaries.tar.gz

shell> vlmcsd -L 192.168.1.17 -l /var/log/vlmcsd.log
shell> vlmcsd -De
```

---

```console
shell> slmgr /ipk GCRJD-8NW9H-F2CDX-CCM8D-9D6T9
shell> slmgr /skms 192.168.1.17:1688
shell> slmgr /ato
```

```console
shell> cscript ospp.vbs /inpkey:YC7DK-G2NP3-2QQC3-J6H88-GVGXT
shell> cscript ospp.vbs /sethst:192.168.1.17
shell> cscript ospp.vbs /setprt:1688 
shell> cscript ospp.vbs /act
```

```console
shell> vlmcs kms.example.com
shell> vlmcs 192.168.1.17
```

**Windows Server 2012 R2 Server Standard**
```console
shell> slmgr.vbs /upk
shell> slmgr.vbs /ipk D2N9P-3P6X9-2R39C-7RTCD-MDVJX
shell> slmgr /skms 192.168.1.17:1688
shell> slmgr.vbs /ato
shell> slmgr.vbs /dlv
```

---

```
_vlmcs._tcp.my-home-net.local. 10800 IN SRV 100 100 kms1.my-home-net.local.
kms1.my-home-net.local. 10800 IN A 192.168.1.17
```

`/etc/dnsmasq.conf`

```
srv-host=_vlmcs._tcp,192.168.1.55,1688,0,100
```

```console
shell> dig -t SRV -q _vlmcs._tcp
shell> nslookup -type=SRV _vlmcs._tcp 
```

`GVLK`
`KMS Client Setup Key`

```
W269N-WFGWX-YVC9B-4J6C9-T83GX - Windows 10 Professional
FJ82H-XT6CR-J8D7P-XQJJ2-GPDD4 - Windows 7 專業版

TX9XD-98N7V-6WMQ6-BX7FG-H8Q99 - Windows 10 Home
3KHY7-WNT83-DGQKR-F7HPR-844BM - Windows 10 Home N
7HNRX-D7KGG-3K4RQ-4WPJ4-YTDFH - Windows 10 Home Single Language
PVMJN-6DFY6-9CCP6-7BKTT-D3WVR - Windows 10 Home Country Specific
789NJ-TQK6T-6XTH8-J39CJ-J8D3P - Windows 8.1 Professional with Media Center
M9Q9P-WNJJT-6PXPY-DWX8H-6XWKK - Windows 8.1 Core
7B9N3-D94CG-YTVHR-QBPX3-RJP64 - Windows 8.1 Core N
BB6NG-PQ82V-VRDPW-8XVD2-V8P66 - Windows 8.1 Core Single Language
NCTT7-2RGK8-WMHRF-RY7YQ-JTXG3 - Windows 8.1 Core Country Specific
GNBB8-YVD74-QJHX6-27H4K-8QHDG - Windows 8 Professional with Media Center
BN3D2-R7TKB-3YPBD-8DRP2-27GG4 - Windows 8 Core
8N2M2-HWPGY-7PGT9-HGDD8-GVGGY - Windows 8 Core N
2WN2H-YGCQR-KFX6K-CD6TF-84YXQ - Windows 8 Core Single Language
4K36P-JN4VD-GDC6V-KDT89-DYFKP - Windows 8 Core Country Specific
```

### :books: 參考網站：
- https://technet.microsoft.com/zh-tw/library/ff793405.aspx

---

```console
shell> echo -n I | od -o | awk 'FNR==1{ print substr($2,6,1)}'
```

`This returns 1 for little-endian systems and 0 for big-endian systems.`

```
little endian
位元組由小到大

big endian
Big Endian
位元組由大到小
```

---

### :books: 參考網站：
- [大量啟用的 Slmgr.vbs 選項](https://technet.microsoft.com/zh-tw/library/dn502540.aspx)
- [附錄 A：KMS 用戶端安裝識別碼](https://technet.microsoft.com/zh-tw/library/jj612867.aspx)
- [Office 2010](https://technet.microsoft.com/en-us/library/ee624355(v=office.14).aspx#section2_3)
- [Office 2013](https://technet.microsoft.com/en-us/library/dn385360.aspx)
- https://github.com/Wind4/vlmcsd
- https://github.com/Wind4/docker-library/blob/master/vlmcsd/Dockerfile
- https://github.com/Wind4/vlmcsd/releases/



