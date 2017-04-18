`ntpdate - client for setting system time from NTP servers`

`ntpdate-debian - set the date and time via NTP`


```console
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

```console
shell> ntpdate-debian
```