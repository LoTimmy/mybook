
![](http://www.netadmin.com.tw/images/news/NP151111000415111111352102.png)

- `Wireshark`這是一個免費開源的網路封包分析軟體，原本名稱叫`Ethereal`，但在2006年，因為商標的問題，而從`Ethereal`更名為`Wireshark`。`Wireshark`支援目前市面上多種主流的作業系統，在`Windows`、`UNIX`、`Mac OS`等之下都有相對應的程式版本。此套軟體的最主要功能就是去擷取網路封包，並盡可能地分析顯示出最詳細的網路封包資料、標頭欄位等等，其用途大多在檢測網路問題、檢查網路安全、嗅探網路封包。`Wireshark`支援的`通訊協定`(`Protocol`)不但很多而且完整，更因為其軟體本身架構為開放原始碼的緣故，因此若想要更新最新的通訊協定相當簡易迅速。另外，在使用頁面上，`Wireshark`的圖形化介面也可以讓新手輕易上手，透過篩選不同網路線段分析、不同種類封包的挑選，來找出所欲擷取的封包格式，輕鬆地了解封包的一切資訊，是一套整合性相當完整的網路封包擷取軟體。 
- `Wireshark`是一款網路封包解析工具，提供圖形化的操作介面和功能完整的過濾器，協助鎖定分析目標，擷取出異常封包，並掌握詳細資訊與證據。 
- `Wireshark`是一款網路封包分析軟體，功能是擷取網路封包，並盡可能地顯示出最為詳細的網路封包資料。`Wireshark`支援了多種作業系統，在`Windows`、`UNIX`、`Mac OS`等都有相對應的版本。藉由此軟體，可以抓取資料封包，進一步分析封包內的摘要與詳細資訊，一般常用在網路故障排除、監聽異常封包、軟體封包問題檢測等地方。`Wireshark`的方便強大之處，在於其支援的`Protocol`較多且完整，更因為開放原始碼的關係，更新`Protocol`相當迅速，不同封包擷取軟體所產生的檔案亦可在此讀取檢視。此外，在介面使用上，`Wireshark`圖形化的介面相當容易上手，並提供豐富的過濾語言，可以輕鬆判別出封包的種類，是一套整合度完整的軟體，也是目前全世界最廣泛的網路封包分析軟體之一。 
- 網路上資料的傳輸是以封包的方式傳遞，網路封包是網路用來傳送資料的最小單位。封包裡面通常含有來源和目的地的IP位址、來源和目的地的`MAC`(`Media Access Controller`)位址，以及所要傳輸的資料。 
- 封包因不同的應用服務或通訊協定，而有各種不同的大小。**一個封包由`標頭`(`Header`)和`資料`(`Data`)所組成**，封包的屬性被詳細地定義在標頭內，包括所使用的通訊協定、來源的IP位址、來源的通訊埠、目的地的IP位址、目的地的通訊埠等欄位。不過，並非所有的通訊協定都有相同的欄位資料，由於採用不同的通訊協定，網路封包的結構都有些許的差異。兩台電腦資料要透過網路溝通，就必須藉由封包傳送來完成。透過傳輸封包，發訊端製作封包，並把封包送出，收訊端接收封包，並將恢復為原來發訊端的傳輸內容，兩台電腦互傳封包，就可以相互溝通。
- 在網路上傳送網路封包，**`路由器`(`Router`)主要是依據封包標頭所記載的目的地IP位址進行路由的交換，以確定依據目前的`路由表`(`Routing Table`)能夠將封包送到目的地**。因此，在網路架構中的適當位置擷取網路封包，就可以取得相關的資訊進行行為分析。目前常見的網路封包分析工具有`Tcpdump`、`Sniffer`、`NetXRay`、`Wireshark`(`Ethereal`)等，其中`Wireshark`雖然屬於`Open Source`軟體，但是所具備的功能卻足可媲美許多商業軟體。在`GNU` `GPL`通用授權的保障之下，使用者可以免費取得軟體及其程式碼，並擁有修改原始碼與客製化的權利。
- 一般而言，之所以想要解析網路封包，大致上有以下幾種原因：瞭解電腦網路目前進行的動作、監聽側錄另一台電腦網路連線、瞭解網路程式如何運行以及學習網路通訊協定。透過網路封包的工具，使用者可以掌握目前網路上的通訊和使用者行為模式。準備擷取網路封包時，必須配合`Hub`、`Y-TAP`或`Switch`進行網路介面的對應，這是因應`Switch`本身設備的特性而必須進行的設定。大多數中高階的交換器都會提供`Port Mirror`或`Port Mapping`功能，這樣才能夠確保安裝網路封包分析工具的設備能夠正確地擷取到網路封包。  
- 乙太網路`集線器`(`HUB`)有兩大特性：廣播以及半雙工。**廣播是指，當網路要透過`HUB`傳送資料給A電腦時，網路端送出來的資料其實連接在這台`HUB`上的電腦都會收到，但是只有A電腦會將資料收起來，其他電腦則是將封包丟掉**。**封包監控的原理，即是將所有經過`HUB`的封包全部擷取出來**。半雙工則是指，收資料或送資料不能同時，一次只能做其中一種。由於`HUB`的這種特性，所以**當`HUB`連接非常多的電腦時，網路就會變慢**。`HUB`範圍從非常小的4埠裝置到企業環境內安裝於機架上所設計的大型48埠不等。

![](http://www.netadmin.com.tw/images/news/NP160105000516010517580504.png)
- `Wireshark`這款網路封包解析軟體，具備完整且豐富的過濾器和統計分析的功能。其操作介面包含最上方的功能表、工具列、篩選工具列、網路封包清單、封包內容、封包位元組和狀態列。 

在網路封包清單中，可以針對不同的通訊協定或過濾規則指定顏色，這種設計方式可以協助使用者針對特定的目標分析網路封包，有助於通訊協定的行為研究與異常行為的偵測，快速辨識各種不同通訊協定，或者過濾規則符合目前網路流量的情況，能夠更方便進行後續處理工作。`Wireshark`相關的操作窗格，分別說明如下： 

`封包清單窗格`(`Packet List Pane`)：顯示封包清單，所列出的可能是目前擷取的封包，或是之前存檔的封包內容，預設會以第一個欄位（流水號）來排序，其中包含五個欄位：No（擷取封包數）、Time（封包擷取時間，預設從開始擷取為第0秒）、Source（封包傳送來源）、Destination（封包傳送目的地）、Protocol（傳輸協定）、Info（有關封包的其他訊息內容）。 

`封包內容窗格`(`Packet Details Pane`)：當點選封包列表內的其中一筆資料時，在封包詳細資訊窗格中會以樹枝化狀呈現該筆封包的詳細資訊，包含封包擷取的大小、時間、來源、目的、協定等資訊。 

`封包位元組窗格`(`Packet Bytes Pane`)：顯示內容和封包內容窗格相同，但以位元組的格式來呈現，當使用者選取封包內容窗格中的通訊協定欄位時，此處相對應的位元組會自動反白顯示。 

`過濾器`(`Filter`)：封包擷取時，不管是不是屬於該電腦的封包，都會將網卡上所收到的封包全部都擷取下來，此時會看到封包列表窗格內，有許多不同協定的封包正在傳送。如果只想看到某些協定或IP的封包傳送狀況時，就會變得很不方便，捲軸要向下拉很長一段距離才能看到需要的資訊，若透過`Filter`工具列，就能過濾需要的封包資訊。 

![](http://www.netadmin.com.tw/images/news/NP160105000516010517580505.png)

#### :books: 參考網站： 
- [側錄無線AP可疑連線 動手揪出存取異常手機](http://www.netadmin.com.tw/article_content.aspx?sn=1601050005)
- [驗證駭客破解PPTP手法 驚見VPN帳密全都露](http://www.netadmin.com.tw/article_content.aspx?sn=1601040003)
- [網路封包分析的好幫手—Wireshark 擷取分析、防範攻擊無所不包](http://www.netadmin.com.tw/article_content.aspx?sn=0808050013)

---

`tshark`
 
```console
shell> tshark -i 2 -f "port 25" -R "smtp.rsp.parameter contains "Sender""
shell> tshark -i 2 -f "port 110" -R "pop.request.parameter contains "user""
shell> tshark -f "port 110" -R "pop.request.command == "USER" || pop.request.command == "PASS""
shell> tshark -i 2 -f "port 25" -T fields -e smtp.auth.username
shell> tshark -i 2 -f "port 3306" -T fields -e mysql.query

shell> tshark -i 2 -f "port 3306" -T fields -R mysql.query -e frame.time -e ip.src -e ip.dst -e mysql.query
shell> tshark -i 2 -f "port 3306" -T fields -R 'mysql matches "SELECT|INSERT|DELETE|UPDATE"' -T fields -e "ip.src" -e "mysql.query"
shell> tshark -i 2 -f "port 3306" -R 'mysql.command == 3' -T fields -e "ip.src" -e "mysql.query"


shell> tshark  -f "port 53" -n -T fields -e dns.qry.name -e dns.resp.addr
shell> tshark  -f "port 53" -n -T fields -e frame.time -e ip.src -e ip.dst -e dns.qry.name -e dns.resp.addr

shell> tshark -R 'http.request.method == "POST"'
shell> tshark -R 'http.request.method == "GET"'

```

```
ip.addr ne 192.168.4.1
tcp.port == 80 and ip.src == 192.168.2.1
tcp.port == 80 || tcp.port == 443 || tcp.port == 8080
tcp.port in {80 443 8080}
tcp.port eq 80
```

#### :books: 參考網站： 
- [tshark](https://www.wireshark.org/docs/man-pages/tshark.html)
- [dns](https://www.wireshark.org/docs/dfref/d/dns.html)
- [frame](https://www.wireshark.org/docs/dfref/f/frame.html)
- [ip](https://www.wireshark.org/docs/dfref/i/ip.html)
- [pop](https://www.wireshark.org/docs/dfref/p/pop.html)
- [imap](https://www.wireshark.org/docs/dfref/i/imap.html)
- https://www.wireshark.org/docs/wsug_html_chunked/ChCapCaptureFilterSection.html
- https://www.wireshark.org/docs/wsug_html_chunked/ChWorkBuildDisplayFilterSection.html
- https://www.wireshark.org/docs/man-pages/wireshark-filter.html