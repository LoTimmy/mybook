<img src="http://i.imgur.com/E1L4Ejv.png" width="300">

- `Bitcoin`
- `比特幣`

`比特幣`是雙向虛擬貨幣的一種，最初是在2008年由一位化名「中本聰」的匿名人士所發表的想法：一種去中心化、純粹的P2P電子貨幣。比特幣沒有發行單位，是透過被稱為「`挖礦`」的電腦運算解謎，才能「挖出」新的`比特幣`。但一般人只要持有`比特幣`電子錢包，就可以透過`比特幣`交易所購買`比特幣`。`比特幣`去中心化的特點讓它的每一筆交易更動都必須要通過所有的「節點」同意，因此透明公開，難以竄改交易資料。
`比特幣`目前在國際間被當作支付貨幣，也被視為投資商品，由於身兼「貨幣」和「商品」兩種特質，在不同的國家有不同的監管方式。
全家便利商店合作比特幣小額購買服務的`BitoEx`「`幣託`」，以及在台灣和美國提供`比特幣`服務的`Maicoin`。

由於`比特幣`的匿名性，過去常常與犯罪行為連結，例如在「`暗網`」（`dark net`）中的各種非法交易，往往是以`比特幣`來支付。然而`比特幣`帶給世界最大的價值或許不是貨幣或商品本身，而是底層的「`區塊鍊`」技術（`blockchain`）。
`Maicoin`是台灣第一個比特幣買賣的交易平台，也提供比特幣電子錢包的服務。

相較於比特幣可追踨金額及流向，`Monero`基於`CryptoNote`協定，具有更高的交易隱匿性，外界只能得知交易金額，無法追踨交易流向。
2014年4月才現身的`Monero` (`XMR`) 奠基於`CryptoNote`協定，採用`CryptoNote`協定的貨幣雖然也利用分散式的公共分類帳來記錄所有的交易，但它的交易紀錄無法用來追蹤送款人或收款人，因此外界只能窺得交易金額，卻無法得知流向。相較於只有匿名特質、但可同時追蹤交易金額及流向的比特幣，`Monero`顯然是個更隱密的交易工具。


- http://www.ithome.com.tw/news/107993


---

- `Bitcoin`
- `Ethereum`
- `Monero`
- `墨內羅幣`
- `Dashcoin`
- `Account Balance`
- `帳戶餘額`

---

#### :books: 參考網站：
- https://poloniex.com

---

`Dockerfile`
```
FROM ubuntu:16.04

RUN apt-get update \
    && apt-get -qq -y --no-install-recommends install ca-certificates wget \
  	&& rm -rf /var/lib/apt/lists/*

RUN wget -q --content-disposition https://minergate.com/download/deb-cli \
    && dpkg -i *.deb \
    && rm *.deb

ENTRYPOINT ["minergate-cli"]
CMD ["-user", "YOUR-EMAIL", "-xmr"]
```

```
shell> sudo docker build -t xmr .
```

`-bcn`
`-xmr`

#### :books: 參考網站：
- https://minergate.com/faq/how-minergate-console
- https://minergate.com/faq/what-pool-address