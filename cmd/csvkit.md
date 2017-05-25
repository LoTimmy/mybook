### 安裝 {#installing}

```console
shell> pip install csvkit
```
```console
shell> sudo apt-get install python-dev python-pip python-setuptools build-essential
```

```console
shell> pip install --upgrade setuptools
shell> pip install --upgrade csvkit
```

```console
shell> wget https://github.com/wireservice/csvkit/raw/master/examples/dummy.xls
shell> in2csv dummy.xls > data.csv
shell> csvlook data.csv
shell> csvcut -n data.csv
shell> csvcut -c 1,3 data.csv
shell> csvcut -c 1,3 data.csv | csvlook
```

#### :books: 參考網站：
- https://github.com/wireservice/csvkit
- http://csvkit.readthedocs.io/en/latest/
