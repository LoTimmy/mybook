```.console
shell> crontab
shell> /etc/crontab
```

``` 
SHELL=/bin/bash
PATH=/sbin:/bin:/usr/sbin:/usr/bin
MAILTO=root
HOME=/
# For details see man 4 crontabs
# Example of job definition:
# .---------------- minute (0 - 59)
# | .------------- hour (0 - 23)
# | | .---------- day of month (1 - 31)
# | | | .------- month (1 - 12) OR jan,feb,mar,apr ...
# | | | | .---- day of week (0 - 6) (Sunday=0 or 7) OR sun,mon,tue,wed,thu,fri,sat
# | | | | |
# * * * * * username  command to be executed

# m h  dom mon dow   command

# run five minutes after midnight, every day
5 0 * * *       $HOME/bin/daily.job >> $HOME/tmp/out 2>&1

# run at 2:15pm on the first of every month -- output mailed to paul
15 14 1 * *     $HOME/bin/monthly

# run at 10 pm on weekdays, annoy Joe
0 22 * * 1-5    mail -s "It's 10pm" joe%Joe,%%Where are your kids?%

23 0-23/2 * * * echo "run 23 minutes after midn, 2am, 4am ..., everyday"

5 4 * * sun     echo "run at 5 after 4 every sunday"

# Run on every second Saturday of the month
0 4 8-14 * *    test $(date +\%u) -eq 6 && echo "2nd Saturday"
```

```
string         meaning
------         -------
@reboot	   Run once, at	startup	of cron.
@yearly	   Run once a year, "0 0 1 1 *".
@annually	   (same as @yearly)
@monthly	   Run once a month, "0	0 1 * *".
@weekly	   Run once a week, "0 0 * * 0".
@daily	   Run once a day, "0 0	* * *".
@midnight	   (same as @daily)
@hourly	   Run once an hour, "0	* * * *".
@every_minute   Run once a minute, "*/1 * * * *".
@every_second   Run once a second.
```

#### :books: 參考網站：
- https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Deployment_Guide/ch-Automating_System_Tasks.html
- https://docs.fedoraproject.org/en-US/Fedora/14/html/Deployment_Guide/ch-Automated_Tasks.html
