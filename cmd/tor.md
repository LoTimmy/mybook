<img src="https://www.torproject.org/images/tor-logo.jpg" width="100">

<img src="https://www.torproject.org/images/onion.jpg" width="40">

> `Tor`為`The Onion Router`(`洋蔥路由器`)的縮寫，它是一個匿名網路，藉由網路上的隨機路由器傳遞，經過多個路由器之後才會到達使用者所要造訪的目的網站，就像層層的洋蔥，可隱匿使用者的來源


### 安裝 {#installing}

```
shell> brew install tor
shell> apt-get install tor    
```

```
deb http://deb.torproject.org/torproject.org jessie main
deb-src http://deb.torproject.org/torproject.org jessie main
```

```
shell> gpg --keyserver keys.gnupg.net --recv A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89
shell> gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add -

shell> apt-get update
shell> apt-get install tor deb.torproject.org-keyring
```

#### :books: 參考網站：
- https://www.torproject.org/docs/debian.html.en
- https://check.torproject.org/