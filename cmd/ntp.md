sudo apt install ntp
sudo systemctl reload ntp.service
sudo ntpq -p


```
shell> sudo apt install ntp
shell> sudo systemctl start ntp.service
shell> sudo systemctl stop ntp.service
shell> sudo ntpq -p
```

```
server 0.rhel.pool.ntp.org iburst
server 1.rhel.pool.ntp.org iburst
server 2.rhel.pool.ntp.org iburst
server 3.rhel.pool.ntp.org iburst

restrict 127.0.0.1
restrict ::1

restrict 192.168.88.0 mask 255.255.255.0 nomodify notrap
```



```
ntpdate -d -s 192.168.88.1
```



https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/7/html/System_Administrators_Guide/s1-Understanding_the_ntpd_Configuration_File.html
