`lnav - ncurses-based log file viewer`

![](https://static1.squarespace.com/static/51bd4e13e4b0052d7873ad34/t/551aa43fe4b065952ea849ad/1427809346467/?format=750w)

### 安裝 {#installing}

```
shell> apt-get install lnav
```

```
shell> lnav -s
shell> lnav /var/log
shell> lnav /var/log/apache2
shell> make 2>&1 | lnav -t
```

```sql
SELECT c_ip, count(*), sum(sc_bytes) AS total FROM access_log GROUP BY c_ip ORDER BY total DESC;
```
```
shell> lnav -n \
 -c ';SELECT c_ip, count(*) AS total FROM access_log GROUP BY c_ip ORDER BY total DESC LIMIT 10' \
 -c ':write-csv-to -' \
 access.log
```


#### :books: 參考網站：
- [lnav](http://lnav.org/)