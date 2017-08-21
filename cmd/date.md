


```
shell> date --help

shell> date -d "1977-10-12"
Wed Oct 12 00:00:00 CST 1977

shell> date +"%c"
Sat 03 Jun 2017 12:23:57 PM CST

shell> date
Sat Jun  3 12:00:25 CST 2017

shell> TZ=GMT date
Sat Jun  3 04:00:25 GMT 2017

shell> date -d now
shell> date -d today
shell> date -d yesterday
shell> date -d tomorrow
shell> date -d sunday
shell> date -d last-sunday
```

```
shell> date -d "1977-10-12" +"%s"
245433600

shell> date -d @245433600
Wed Oct 12 00:00:00 CST 1977

shell> date -d "1977-10-12" +"%A"
Wednesday

shell> date +"%F"
2017-06-03
```

```
last
next
last-week
next-week
last-month
next-month
last-year
next-year
```

```
       %a     locale's abbreviated weekday name (e.g., Sun)
       %A     locale's full weekday name (e.g., Sunday)
       %b     locale's abbreviated month name (e.g., Jan)
       %B     locale's full month name (e.g., January)
       %c     locale's date and time (e.g., Thu Mar  3 23:05:25 2005)
       %F     full date; same as %Y-%m-%d
       %s     seconds since 1970-01-01 00:00:00 UTC
```

`/etc/localtime`


`/usr/share/zoneinfo`


#### :books: 參考網站：
- http://php.net/manual/en/datetime.formats.relative.php

