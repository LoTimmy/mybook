![](https://camo.githubusercontent.com/8594e925d6bba1f3a52de49f9b47d044e53ccb8b/68747470733a2f2f7261772e6769746875622e636f6d2f656d72652f73746f726d2f6d61737465722f7265736f75726365732f6c6f676f732f73746f726d2d6c6f676f2e706e67)

![](https://raw.github.com/emre/storm/master/resources/screenshot.png)

![](https://camo.githubusercontent.com/d7f0270766047695d9c163ea190224a6b8fec09a/687474703a2f2f692e696d6775722e636f6d2f7756746e5778782e706e67)

### 安裝 {#installing}

```
shell> pip install stormssh

shell> brew install stormssh
shell> brew install stormssh-completion
```

```
shell> storm add my_vps root@emreyilmaz.me:22
shell> storm edit my_vps emre@emreyilmaz.me:2400
shell> storm update my_vps-[1-5] --o user=emre
shell> storm delete my_vps
shell> storm search git
shell> storm delete_all
shell> storm add web-prod web@webprod.com --o "StrictHostKeyChecking=no" --o "UserKnownHostsFile=/dev/null"
```


#### :books: 參考網站：
- http://stormssh.readthedocs.io/en/master/index.html
- https://github.com/emre/storm/
