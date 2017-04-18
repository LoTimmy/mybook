`cvs - Concurrent Versions System`

### 安裝 {#installing}
```console
shell> sudo apt-get install cvs
shell> sudo apt-get install xinetd
```

`/etc/services`
```
cvspserver	2401/tcp			# CVS client/server operations
cvspserver	2401/udp			# CVS client/server operations
```

```console
shell> mkdir /cvs
shell> chmod -R 777 /cvs
```

`/etc/xinetd.d/cvs`
```
service cvspserver
{
	disable	= no
	port			= 2401
	socket_type		= stream
	protocol		= tcp
	wait			= no
	user			= root
	passenv			= PATH
	server			= /usr/bin/cvs
	env			= HOME=/cvs
	server_args		= -f --allow-root=/cvs pserver
#	bind			= 127.0.0.1
}
```

```console
shell> cvs -d /cvs init
```
```console
shell> export CVSROOT=:pserver:cvsuser@192.168.1.1:/cvs
shell> cvs login
```

#### :books: 參考網站：
- [cvs](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Managing_Confined_Services/sect-Managing_Confined_Services-Concurrent_Versioning_System-Configuration_Examples.html)

---

`cvsd - chroot wrapper to run 'cvs pserver' more securely`

### 安裝 {#installing}
```console
shell> sudo apt-get install cvs
shell> sudo apt-get install cvsd
```

`/var/lib/cvsd/myrepos/CVSROOT/config`
```
SystemAuth=no
LockDir=/var/lock/cvs
```

```console
shell> mkdir /var/lib/cvsd/myrepos
shell> mkdir -p /var/lib/cvsd/var/lock/cvs

shell> cvs -d /var/lib/cvsd/myrepos init
shell> cvsd-passwd /var/lib/cvsd/myrepos anonymous
shell> cvsd-passwd /var/lib/cvsd/myrepos cvsuser

shell> cvsd-passwd /var/lib/cvsd/myrepos -foo
shell> chown -R cvsd:cvsd /var/lib/cvsd
shell> service cvsd restart
```

`/etc/cvsd/cvsd.conf`
```
RootJail /var/lib/cvsd
Repos /myrepos
Listen * 2401
```

```console
shell> cvs -d :pserver:cvsuser@127.0.0.1:/myrepos login
shell> cvs -d :pserver:cvsuser@127.0.0.1:/myrepos checkout 
```







