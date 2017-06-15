
### 在 `Ubuntu` 16.04.2 LTS 上建置 `freeradius`

```console 
shell> lsb_release -a
```
```
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.2 LTS
Release:	16.04
Codename:	xenial
```

```
freeradius - high-performance and highly configurable RADIUS server
freeradius-mysql - MySQL module for FreeRADIUS server
```

### 安裝 `freeradius` 
```console
shell> apt-get install mysql-server-5.7
shell> sudo apt-get install -y freeradius freeradius-mysql 
shell> freeradius
shell> sudo service freeradius stop
```

`/etc/freeradius`

```console
shell> sudo cp /etc/freeradius/users /etc/freeradius/users.original
shell> sudo chmod a-w /etc/freeradius/users.original
```



`users`
```
steve	Cleartext-Password := "testing"
	Service-Type = Framed-User,
	Framed-Protocol = PPP,
	Framed-IP-Address = 172.16.3.33,
	Framed-IP-Netmask = 255.255.255.0,
	Framed-Routing = Broadcast-Listen,
	Framed-Filter-Id = "std.ppp",
	Framed-MTU = 1500,
	Framed-Compression = Van-Jacobson-TCP-IP
```



```console
shell> freeradius -X
```
```console
shell> radtest steve testing localhost 1812 testing123
```

```
Sending Access-Request of id 38 to 127.0.0.1 port 1812
	User-Name = "steve"
	User-Password = "testing"
	NAS-IP-Address = 127.0.1.1
	NAS-Port = 1812
	Message-Authenticator = 0x00000000000000000000000000000000
rad_recv: Access-Accept packet from host 127.0.0.1 port 1812, id=38, length=71
	Service-Type = Framed-User
	Framed-Protocol = PPP
	Framed-IP-Address = 172.16.3.33
	Framed-IP-Netmask = 255.255.255.0
	Framed-Routing = Broadcast-Listen
	Filter-Id = "std.ppp"
	Framed-MTU = 1500
	Framed-Compression = Van-Jacobson-TCP-IP
```

`clients.conf`
```
client localhost {
	secret		= testing123
}
```

```
COMMAND     PID    USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
freeradiu 12276 freerad    5u  IPv4 195719      0t0  UDP *:1812 
freeradiu 12276 freerad    6u  IPv4 195720      0t0  UDP *:1813 
freeradiu 12276 freerad    7u  IPv4 195721      0t0  UDP 127.0.0.1:18120 
freeradiu 12276 freerad    8u  IPv4 195722      0t0  UDP *:1814 
freeradiu 12276 freerad    9u  IPv4 195723      0t0  UDP *:54563 
```

```
client 192.168.88.120 {
	ipaddr = 192.168.88.120
	secret		= testing123
	require_message_authenticator = no
	nastype     = other
}
```

---

`/etc/freeradius/sql/mysql`

```
shell> mysql -u root -p -e "CREATE DATABASE radius;"
shell> mysql -u root -p radius < admin.sql
shell> mysql -u root -p radius < schema.sql
shell> mysql -u radius -p radius
```

`radpass`

```console
shell> sudo cp /etc/freeradius/radiusd.conf /etc/freeradius/radiusd.conf.original
shell> sudo chmod a-w /etc/freeradius/radiusd.conf.original

shell> sudo cp /etc/freeradius/sql.conf /etc/freeradius/sql.conf.original
shell> sudo chmod a-w /etc/freeradius/sql.conf.original
```

`radiusd.conf`
```
	$INCLUDE sql.conf
```

`sql.conf`
```
sql {
        database = "mysql"
        driver = "rlm_sql_${database}"
        server = "localhost"
        #port = 3306
        login = "radius"
        password = "radpass"
        radius_db = "radius"
        [...]
}

```

`/etc/freeradius/sites-available/default`
```
authorize {
        [...]
#       files
        sql
        [...]
}

[...]

accounting {
        [...]
        sql
        [...]
}

session {
        radutmp
        sql
}

post-auth {
        [...]
        sql
        [...]
}
```
`/etc/freeradius/sql/mysql/dialup.conf`

```
        # Uncomment simul_count_query to enable simultaneous use checking
        simul_count_query = "SELECT COUNT(*) \
                             FROM ${acct_table1} \
                             WHERE username = '%{SQL-User-Name}' \
                             AND acctstoptime IS NULL"
```

```
+------------------+
| Tables_in_radius |
+------------------+
| radacct          |
| radcheck         |
| radgroupcheck    |
| radgroupreply    |
| radpostauth      |
| radreply         |
| radusergroup     |
+------------------+
```



`radcheck`
```
+-----------+------------------+------+-----+---------+----------------+
| Field     | Type             | Null | Key | Default | Extra          |
+-----------+------------------+------+-----+---------+----------------+
| id        | int(11) unsigned | NO   | PRI | NULL    | auto_increment |
| username  | varchar(64)      | NO   | MUL |         |                |
| attribute | varchar(64)      | NO   |     |         |                |
| op        | char(2)          | NO   |     | ==      |                |
| value     | varchar(253)     | NO   |     |         |                |
+-----------+------------------+------+-----+---------+----------------+
```

`radusergroup`

```
+-----------+-------------+------+-----+---------+-------+
| Field     | Type        | Null | Key | Default | Extra |
+-----------+-------------+------+-----+---------+-------+
| username  | varchar(64) | NO   | MUL |         |       |
| groupname | varchar(64) | NO   |     |         |       |
| priority  | int(11)     | NO   |     | 1       |       |
+-----------+-------------+------+-----+---------+-------+
```

`radgroupreply`
```
+-----------+------------------+------+-----+---------+----------------+
| Field     | Type             | Null | Key | Default | Extra          |
+-----------+------------------+------+-----+---------+----------------+
| id        | int(11) unsigned | NO   | PRI | NULL    | auto_increment |
| groupname | varchar(64)      | NO   | MUL |         |                |
| attribute | varchar(64)      | NO   |     |         |                |
| op        | char(2)          | NO   |     | =       |                |
| value     | varchar(253)     | NO   |     |         |                |
+-----------+------------------+------+-----+---------+----------------+
```



```
INSERT INTO radgroupreply (groupname, attribute, op, value) VALUES ('user', 'Auth-Type', ':=','LOCAL');
INSERT INTO radgroupreply (groupname, attribute, op, value) VALUES ('user', 'Service-Type', ':=', 'Framed-User');
INSERT INTO radgroupreply (groupname, attribute, op, value) VALUES ('user', 'Framed-IP-Address', ':=', '172.16.3.33');

INSERT INTO radcheck (username, attribute, value) VALUES ('test', 'User-Password', 'test');
INSERT INTO radusergroup (username, groupname) VALUES ('test', 'user');
```

```console
shell> radtest test test localhost 0 testing123
```

```
rad_recv: Access-Reject packet from host 127.0.0.1 port 1812, id=164, length=20
```

```
Sending Access-Request of id 37 to 127.0.0.1 port 1812
	User-Name = "test"
	User-Password = "test"
	NAS-IP-Address = 127.0.1.1
	NAS-Port = 0
	Message-Authenticator = 0x00000000000000000000000000000000
rad_recv: Access-Accept packet from host 127.0.0.1 port 1812, id=37, length=32
	Service-Type = Framed-User
	Framed-IP-Address = 172.16.3.33
```
