`supervisor - System for controlling process state`

`supervisorctl - supervisorctl Documentation`

`Installing Supervisor`

```console
shell> apt-get update && apt-get install -y supervisor
shell> mkdir -p /var/log/supervisor
```


`echo_supervisord_conf - Supervisor Configuration Documentation`


```console
shell> echo_supervisord_conf > /etc/supervisor/supervisord.conf
```

`/etc/supervisor/conf.d/supervisord.conf`

```
[supervisord]
nodaemon=true

[program:sshd]
command=/usr/sbin/sshd -D

[program:apache2]
command=/bin/bash -c "source /etc/apache2/envvars && exec /usr/sbin/apache2 -DFOREGROUND"
```


```
[program:gitbook]
command=/home/chrism/bin/httpd -c "ErrorLog /dev/stdout" -DFOREGROUND
user=chrism
environment=HOME="/home/chrism",USER="chrism"
```




```
[inet_http_server]         ; inet (TCP) server disabled by default
port=127.0.0.1:9001        ; (ip_address:port specifier, *:port for all iface)
username=user              ; (default is no username (open server))
password=123               ; (default is no password (open server))
```

```
;[program:theprogramname]
;autostart=true
;autorestart=true
;stdout_logfile=/a/path
;stderr_logfile=/a/path
;directory=/tmp
;command=/bin/cat
;user=chrism
```

```console
shell> /usr/bin/supervisord
```

```console
shell> supervisorctl

supervisor> help
```

```
default commands (type help <topic>):
=====================================
add    exit      open  reload  restart   start   tail   
avail  fg        pid   remove  shutdown  status  update 
clear  maintail  quit  reread  signal    stop    version
```

```console
shell> supervisorctl status
shell> supervisorctl reload

shell> supervisorctl stop
shell> supervisorctl start
shell> supervisorctl restart
```

#### :books: 參考網站：
- [supervisord](http://supervisord.org/)
- [using_supervisord](https://docs.docker.com/engine/admin/using_supervisord/)
- http://supervisord.org/installing.html