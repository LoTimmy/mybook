- `SysBench`是開源碼社群中頗富盛名的壓力測試軟體，可用來**測試主機上的檔案系統及記憶體的讀寫效能、CPU的運作效能**。 
除了上述傳統的效能測試項目外，`SysBench`更提供了**資料庫的運作效能測試，目前支援測試`MySQL`、`Oracle`、`PostgreSQL`等相關著名的資料庫軟體**。 
- `SysBench`測試資料庫的主要重點在於`OLTP`(`On-Line Transaction Processing system`，`連線交易處理系統`) 的效能測試。 
所謂`OLTP`，指的是一般傳統`關聯式資料庫`(`Relational Database`)的主要應用功能，其特色是當交易在進行時可針對交易資料進行即時處理，而非傳統的批次處理，例如`MySQL`就是一種著名的關聯式資料庫軟體。 
- 所以測試`OLTP`效能的重點是，當使用者在提出一個交易要求，而後資料庫系統接收到該筆交易要求並完成運算，再回覆給使用者的整段時間。而`SysBench`即是藉著測量此段時間的長短來評估資料庫的效能好壞。 



### 在 `Ubuntu` 14.04 LTS 上建置 `sysbench`

```
shell> lsb_release -a
```
```
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04 LTS
Release:	14.04
Codename:	trusty
```
### 安裝 sysbench 
```
shell> sudo apt-get install sysbench
```


--test：設定測試的對象。`SysBench`支援CPU、記憶體、檔案系統(fileio)、資料庫(`OLTP`)的效能。
![](http://www.netadmin.com.tw/images/news/NP150702000215070214031103.png)
![](http://www.netadmin.com.tw/images/news/NP150702000215070214033201.png)
![](http://www.netadmin.com.tw/images/news/NP150702000215070214033302.png)
```
shell> sysbench --test=cpu --cpu-max-prime=20000 run
```
```
shell> sysbench --test=memory --memory-block-size=8K --memory-total-size=1G --memory-oper=read run  
```
```
shell> sysbench --num-threads=16 --test=fileio --file-total-size=3G --file-test-mode=rndrw prepare
shell> sysbench --num-threads=16 --test=fileio --file-total-size=3G --file-test-mode=rndrw run
shell> sysbench --num-threads=16 --test=fileio --file-total-size=3G --file-test-mode=rndrw cleanup
```

```
shell> sysbench --test=oltp --mysql-table-type=myisam --oltp-table-size=1000000 --mysql-socket=/tmp/mysql.sock prepare
shell> sysbench --num-threads=16 --max-requests=100000 --test=oltp --oltp-table-size=1000000 --mysql-socket=/tmp/mysql.sock --oltp-read-only run
```


#### :books: 參考網站：
- [http://www.netadmin.com.tw/article_content.aspx?sn=1507020002&jump=3](http://www.netadmin.com.tw/article_content.aspx?sn=1507020002&jump=3)
