### 安裝 {#installing}

```console
shell> pip install --upgrade dnsyo
```

```
--simple, -s          Simple output mode (good for UNIX parsing)
--extended, -x        Extended output mode including server addresses
--threads THREADS, -t THREADS
                      Number of worker threads to use
```

```console
shell> dnsyo -t 100 -q ALL example.com
shell> dnsyo --simple example.com
shell> dnsyo --extended example.com
shell> dnsyo google.com MX
```

#### :books: 參考網站：
- https://github.com/YoSmudge/dnsyo
