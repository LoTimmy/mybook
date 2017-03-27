`timedatectl - Control the system time and date`

```console
shell> timedatectl
shell> timedatectl list-timezones
shell> timedatectl set-timezone Asia/Taipei
shell> timedatectl set-ntp true
```

`Changing the Time Zone`

```console
shell> ls /usr/share/zoneinfo
shell> sudo ln -sf /usr/share/zoneinfo/America/Los_Angeles /etc/localtime
```

#### :books: 參考網站：
- http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/set-time.html