`ntpdate - client for setting system time from NTP servers`

`ntpdate-debian - set the date and time via NTP`


```
shell> apt-get install ntpdate
shell> ntpdate -u time.apple.com
shell> ntpdate -u time.asia.apple.com
shell> ntpdate -u time.euro.apple.com
shell> ntpdate -u ntp.ubuntu.com
```

`/etc/default/ntpdate`
```
# The settings in this file are used by the program ntpdate-debian, but not
# by the upstream program ntpdate.

# Set to "yes" to take the server list from /etc/ntp.conf, from package ntp,
# so you only have to keep it in one place.
NTPDATE_USE_NTP_CONF=yes

# List of NTP servers to use  (Separate multiple servers with spaces.)
# Not used if NTPDATE_USE_NTP_CONF is yes.
NTPSERVERS="time.asia.apple.com ntp.ubuntu.com"

# Additional options to pass to ntpdate
NTPOPTIONS=""
```

```
shell> ntpdate-debian
```

---

```
shell> sudo apt install ntp
shell> sudo systemctl reload ntp.service
```

`/etc/ntp.conf`
```
server time1.google.com iburst
server time2.google.com iburst
server time3.google.com iburst
server time4.google.com iburst
```

如何找到你想要連結的`NTP`伺服器?(此以台灣的`NTP`伺服器為例)

1. 請至以下網址 http://support.ntp.org/bin/view/Servers/WebHome
`Finding A Time Server` → `Browsing the Lists` →
選擇並點擊其一伺服器連結(此以點擊「`Public NTP Pool Time Servers`」為例)

2. 找到對應表中的亞洲，點擊連結「`asia.pool.ntp.org`」。

3. 找到台灣的`NTP`伺服器為「`tw.pool.ntp.org`」

```
driftfile /var/lib/ntp/ntp.drift

server 0.tw.pool.ntp.org
server 1.tw.pool.ntp.org
server 2.tw.pool.ntp.org
server 3.tw.pool.ntp.org

server 0.pool.ntp.org
server 1.pool.ntp.org
server 2.pool.ntp.org
server 3.pool.ntp.org

server 0.asia.pool.ntp.org
server 1.asia.pool.ntp.org
server 2.asia.pool.ntp.org
server 3.asia.pool.ntp.org

server 0.europe.pool.ntp.org
server 1.europe.pool.ntp.org
server 2.europe.pool.ntp.org
server 3.europe.pool.ntp.org

server 0.ubuntu.pool.ntp.org
server 1.ubuntu.pool.ntp.org
server 2.ubuntu.pool.ntp.org
server 3.ubuntu.pool.ntp.org

server 0.amazon.pool.ntp.org iburst
server 1.amazon.pool.ntp.org iburst
server 2.amazon.pool.ntp.org iburst
server 3.amazon.pool.ntp.org iburst
```

```
shell> sudo service ntp reload
shell> ntpq -pn
shell> ntpstat
```

#### :books: 參考網站：
- https://developers.google.com/time/
- http://www.pool.ntp.org/zone/europe
- http://www.pool.ntp.org/zone/tw
- http://www.pool.ntp.org/zh/use.html
- http://support.ntp.org/bin/view/Servers/NTPPoolServers
- https://help.ubuntu.com/lts/serverguide/NTP.html
- http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/set-time.html
- https://www.asus.com/tw/support/faq/111041

