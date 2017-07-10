<img src="http://i.imgur.com/E1L4Ejv.png" width="300">

- `Bitcoin`
- `比特幣`

`比特幣` <img src="http://i.imgur.com/Yt7azjn.png" width="18"> 是雙向虛擬貨幣的一種，最初是在2008年由一位化名「中本聰」的匿名人士所發表的想法：一種去中心化、純粹的`P2P`電子貨幣。`比特幣`沒有發行單位，是透過被稱為「`挖礦`」的電腦運算解謎，才能「挖出」新的`比特幣`。但一般人只要持有`比特幣`電子錢包，就可以透過`比特幣` 交易所購買`比特幣`。`比特幣`去中心化的特點讓它的每一筆交易更動都必須要通過所有的「節點」同意，因此透明公開，難以竄改交易資料。
`比特幣` <img src="http://i.imgur.com/Yt7azjn.png" width="18"> 目前在國際間被當作支付貨幣，也被視為投資商品，由於身兼「`貨幣`」和「`商品`」兩種特質，在不同的國家有不同的監管方式。
`全家便利商店`合作`比特幣`小額購買服務的`BitoEx`「`幣託`」，以及在台灣和美國提供`比特幣`服務的`Maicoin`。

由於`比特幣`的匿名性，過去常常與犯罪行為連結，例如在「`暗網`」（`dark net`）中的各種非法交易，往往是以`比特幣`來支付。然而`比特幣`帶給世界最大的價值或許不是貨幣或商品本身，而是底層的「`區塊鍊`」技術（`blockchain`）。
`Maicoin`是台灣第一個比特幣買賣的交易平台，也提供比特幣電子錢包的服務。

> `Intel`® `進階加密標準新增指令` (`Intel`® `AES NI`) 是一組新的加密指令集，改善了`進階加密標準` (`AES`) 演算法，可加速 `Intel`® `Xeon`® 處理器產品與 `Intel`® Core™ 處理器產品中的資料加密。


#### :books: 參考網站：
- http://www.ithome.com.tw/news/107993
- https://www.intel.com.tw/content/www/tw/zh/architecture-and-technology/advanced-encryption-standard--aes-/data-protection-aes-general-technology.html


---

- `Bitcoin` <img src="http://i.imgur.com/Yt7azjn.png" width="18"> `比特幣` `BTC` `SHA-256`
- `Ethereum` <img src="http://i.imgur.com/fjj36UT.png" width="20"> `以太坊` `ETH` `Ethash`
 
- `Dashcoin` <img src="http://i.imgur.com/1Caweri.png" width="16"> `達世幣` `DASH` `X11` 
- `Account Balance` `帳戶餘額`
- `Chart` `圖表`

---

#### :books: 參考網站：
- https://poloniex.com

---

- `Monero` <img src="http://i.imgur.com/gFdgubO.png" width="16"> `墨內羅幣` `門羅幣` `XMR` `Cryptonight`

相較於比特幣可追踨金額及流向，`Monero` <img src="http://i.imgur.com/gFdgubO.png" width="16"> 基於`CryptoNote`協定，具有更高的交易隱匿性，外界只能得知交易金額，無法追踨交易流向。
2014年4月才現身的`Monero` (`XMR`) <img src="http://i.imgur.com/gFdgubO.png" width="16"> 奠基於`CryptoNote`協定，採用`CryptoNote`協定的貨幣雖然也利用分散式的公共分類帳來記錄所有的交易，但它的交易紀錄無法用來追蹤送款人或收款人，因此外界只能窺得交易金額，卻無法得知流向。相較於只有匿名特質、但可同時追蹤交易金額及流向的比特幣，`Monero`顯然是個更隱密的交易工具。

<a href="https://youtu.be/TZi9xx6aiuY" target="_blank">
  <img src="http://img.youtube.com/vi/TZi9xx6aiuY/0.jpg" alt="" width="240" height="180" >
</a>

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
```

```console
shell> sudo docker build -t minergate-cli .

shell> docker run --rm minergate-cli -help
shell> docker run --rm minergate-cli -version
shell> docker run -d --name test minergate-cli -user YOUR-EMAIL -xmr
shell> docker run --rm --name test -d minergate-cli -user YOUR-EMAIL -xmr
shell> docker run --rm --name test -d minergate-cli -user YOUR-EMAIL -bcn 2 -fcn+dsh 2

shell> docker logs test
shell> docker stop test
```

`-bcn`
`-xmr`

```
FROM ubuntu:16.04
ARG DEBIAN_FRONTEND=noninteractive

RUN set -ex; \
    \
    apt-get update; \
    apt-get install -y --no-install-recommends libmicrohttpd10 libssl1.0.0; \
    rm -rf /var/lib/apt/lists/*;

RUN set -ex; \
    \
    fetchDeps='ca-certificates wget curl g++ libmicrohttpd-dev libssl-dev make git'; \
    apt-get update; \
    apt-get install -y --no-install-recommends $fetchDeps; \
    rm -rf /var/lib/apt/lists/*; \
    curl -SL https://cmake.org/files/v3.8/cmake-3.8.2-Linux-x86_64.tar.gz \
    | tar --strip=1 -xzC /usr/local; \
    git clone https://github.com/fireice-uk/xmr-stak-cpu.git; \
    cd xmr-stak-cpu; \
    cmake .; \
    make -j$(nproc); \
    apt-get purge -y --auto-remove $fetchDeps

WORKDIR /xmr-stak-cpu

EXPOSE 62787
ENTRYPOINT ["bin/xmr-stak-cpu"]
CMD ["/conf/config.txt"]
```

`dockerfiles/Dockerfile.alpine`
```
FROM alpine:3.5

RUN apk add --no-cache libcurl \
    libstdc++ \
    libgcc \
    openssl

RUN apk add --no-cache --virtual .build-deps  \
    autoconf \
    automake \
    build-base \
    curl \
    curl-dev \
    git

RUN git clone https://github.com/wolf9466/cpuminer-multi
RUN cd cpuminer-multi && ./autogen.sh
RUN cd cpuminer-multi && ./configure CFLAGS="-O3"
RUN cd cpuminer-multi && make
RUN apk del .build-deps

WORKDIR /cpuminer-multi

ENTRYPOINT ["./minerd"]
CMD ["-c", "/conf/minerd.json"]
```

`conf/minerd.json`
```json
{
  "url": "stratum+tcp://198.251.81.82:3333",
  "user": "47HtbDvpVQwDsiegiDZqYxcQEDZtj3DGxHcdeaqem4jqQxkBQtpxgopUZ5oVg2HaWfTjGye2MBZZJTPvDpeL1Koq5ZtaFH1",
  "pass": "x",
  "algo": "cryptonight"
}
```

docker build -f dockerfiles/Dockerfile.alpine -t minerd .
docker run --rm -v "$(pwd)/conf:/conf:ro" -d minerd -c /conf/minerd.json

`conf/config.txt`
```
"cpu_threads_conf" :
[
   { "low_power_mode" : true, "no_prefetch" : true, "affine_to_cpu" : 0 },
   { "low_power_mode" : false, "no_prefetch" : true, "affine_to_cpu" : 1 },
   { "low_power_mode" : false, "no_prefetch" : true, "affine_to_cpu" : 2 },
   { "low_power_mode" : false, "no_prefetch" : true, "affine_to_cpu" : 3 },
   { "low_power_mode" : false, "no_prefetch" : true, "affine_to_cpu" : 4 },
],
"use_slow_memory" : "warn",
"nicehash_nonce" : false,
"pool_address" : "198.251.81.82:3333",
"wallet_address" : "47HtbDvpVQwDsiegiDZqYxcQEDZtj3DGxHcdeaqem4jqQxkBQtpxgopUZ5oVg2HaWfTjGye2MBZZJTPvDpeL1Koq5ZtaFH1",
"pool_password" : "x",
"httpd_port" : 62787,
"prefer_ipv4" : true,
```

```console
shell> docker build -f dockerfiles/Dockerfile -t xmr-stak-cpu .
shell> docker run --rm -v "$(pwd)/conf:/conf:ro" -p 62787:62787 -d xmr-stak-cpu
```


#### :books: 參考網站：
- https://minergate.com/faq/how-minergate-console
- https://minergate.com/faq/what-pool-address

---

```
shell> grep aes /proc/cpuinfo
shell> openssl speed aes-128-cbc
shell> openssl speed -evp aes-128-cbc
shell> dd if=/dev/zero count=100 bs=1M | ssh -c aes128-cbc localhost "cat >/dev/null"
```

#### :books: 參考網站：
- https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Security_Guide/sect-Security_Guide-Encryption-OpenSSL_Intel_AES-NI_Engine.html
- https://software.intel.com/zh-cn/articles/improving-openssl-performance
- https://technet.microsoft.com/zh-tw/library/cc811537(v=ws.11).aspx

---

- `演算法`
- `加密演算法`
- `AES-GCM 256`
- `AES-GCM 192`
- `AES-GCM 128`
- `AES-CBC 256`
- `AES-CBC 192`
- `AES-CBC 128`
- `3DES`
- `DES`
 
---

- 名為「`影子經紀人`」 （`The Shadow Brokers`, `TSB`）的駭客組織
- 駭客組織「`影子掮客`」 (`The Shadow Brokers`, `TSB`)
- 駭客組織「`方程式團體`」 (`Equation Group`)
- 「`零時差漏洞`」（**指還沒有修補程式的安全漏洞**，`Zero Day Exploit`）

