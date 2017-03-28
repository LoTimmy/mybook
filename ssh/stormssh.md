
### 安裝 {#installing}

```console
shell> pip install stormssh

shell> brew install stormssh
shell> brew install stormssh-completion
```

```console
shell> storm add my_vps root@emreyilmaz.me:22
shell> storm edit my_vps emre@emreyilmaz.me:2400
shell> storm update my_vps-[1-5] --o user=emre
shell> storm delete my_vps
shell> storm search git
shell> storm delete_all
shell> storm add web-prod web@webprod.com --o "StrictHostKeyChecking=no" --o "UserKnownHostsFile=/dev/null"
```

![](https://raw.github.com/emre/storm/master/resources/screenshot.png)
- http://stormssh.readthedocs.io/en/master/index.html
