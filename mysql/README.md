> **`MySQL`是一開放源碼資料庫軟體**，除了有免費下載版可用之外，也提供商用版的訂閱服務。

> `MySQL`的姊妹資料庫`MariaDB`。

> **`瑪莉亞資料庫` (`MariaDB`)如同`MySQL`的影子版本，`瑪莉亞資料庫` (`MariaDB`)是`MySQL`的一個`分支版本` (`Branch`)，而不是`衍生版本` (`Fork`)，提供的功能可和`MySQL`完全相容**。

> `MySQL`作者兼聯合創辦人`Michael Widenius` (代號`Monty`) 和其他創始人在1994年開始開發`MySQL`，2008年將`MySQL`賣給了`昇陽電腦`(`Sun`)，傳為開源軟體商業化的經典案例。

> `Michael Widenius`(網路代號：`Monty`)同為`MySQL`與`MariaDB`的創辦人，2008年他以10億美元的代價將`MySQL`出售給昇陽，兩年後甲骨文併購昇陽，`MySQL`經二度轉手。在甲骨文的經營下，原本主張開源的`MySQL`轉趨封閉，由於`Michael Widenius`對此策略不認同，因而分支出與`MySQL` 5.5完全相容的`MariaDB` 5.5。

> 2010年，`MySQL`更推出大受歡迎的5.5版，但`甲骨文` (`Oracle`)卻收購了`昇陽電腦`(`Sun`)。`MySQL`二度易主，`MySQL`社群擔心`甲骨文` (`Oracle`)箝制而紛紛出走，Michael Widenius因而推出了與`MySQL`相容的`瑪莉亞資料庫` (`MariaDB`)，而`MySQL`原有高層則成立了`SkySQL`公司，廣納舊版`MySQL`的開發工程師，來與`甲骨文` (`Oracle`)主導的`MySQL`分庭抗禮。

> 主導`MySQL`的`甲骨文` (`Oracle`)著重於追加一些華麗的新功能，而忽視了`MySQL`的穩定性與整體效率。`甲骨文` (`Oracle`)主導下的`MySQL`，在正式釋出可用版，對外揭露的資訊不足，十分缺乏透明度，而且，`甲骨文` (`Oracle`)較少修正來自使用者回報的臭蟲、也不常聽取開發社群的討論、意見與對新功能的需求，雖然`MySQL`是開放源碼的資料庫，`甲骨文` (`Oracle`)的作為，讓`MySQL`的封閉性色彩逐漸濃厚。

> 而`瑪莉亞資料庫` (`MariaDB`) 雖然`MySQL`是同源所生的程式碼，但運作的理念卻有很大的不同。`MariaDB`是由Michael Widenius領導，並囊括了許多最初開發`MySQL`的開發人員，創立目的就是為了擺脫`甲骨文` (`Oracle`)的控制。

> `甲骨文` (`Oracle`)對`MySQL`的封閉態度，加上`瑪莉亞資料庫` (`MariaDB`)和`MySQL`到目前為止其資料格式可以互通，導致許多企業都有將資料庫系統轉換的打算，例如，`維基百科`早已將資料庫從`MySQL`換成`瑪莉亞資料庫` (`MariaDB`)、而`Linux`作業系統`Red Hat`、`SUSE`也採用了`瑪莉亞資料庫` (`MariaDB`)作為其網站資料庫。

> **`瑪莉亞資料庫` (`MariaDB`)在因應複雜的查詢上，效率高過`MySQL`，而在`複製設定` (`Replication Setup`) 上的速度，`瑪莉亞資料庫` (`MariaDB`)也比`MySQL`高出許多**。

> **`MySQL`適合用管理小於1.5TB的資料，或者作為大量資料的後端備份系統**。

> **`MySQL`的優點是，簡易查詢的效率較高，對於一個簡易查詢的要求，通常能以小於500微秒 (μs) 的時間回應，此外，`MySQL`也有一個相對穩定的資料儲存層`InnoDB`，最後，`MySQL`的安裝與操作都相對容易，同時也有許多網路上的學習資源可供利用**。

> `MySQL` 5.7主要強化效能、可擴充性，與管理能力。在`SysBench`標竿測試中，基於1204個連結的Read-only Point-Selects每秒傳遞160萬次的查詢(`QPS`)，為`MySQL` 5.6的3倍。另有優化的`InnoDB`、更強大的複製能力、新的優化器、支援`JSON`、新的效能綱要(`performance schema`)與SYS綱要，改善了安全性，強化`NoSQL`能力，並擴充行動應用對地理資訊系統(`GIS`)的支援 。全新的`MySQL Router`則可藉由智慧型的`MySQL`資料庫路徑查詢以增加效能與上線時間，進而簡化應用的開發，亦針對`MySQL Fabric`提供跨語言的支援，能更方便地管理`MySQL`資料庫群組，自動化的`資料切分`(`data sharding`)則帶來高可得性與擴充性。

> `MySQL` 埠號 `3306`

> `甲骨文` (`Oracle`)在2010年底發布了`MySQL`的改版，5.5版中有不少重大的更新，例如：將原本預設的資料表儲存引擎由`MyISAM`更改成`InnoDB`、提供更多的分區選項、對多處理器核心系統效能的改進、支援`半同步複製功能` (`Semi-Synchronous Replication`)、加強資料毀壞修復的能力等。

> `MySQL`高可用性架構搭配使用`InnoDB`儲存引擎，更能達到一致性要求。因為`InnoDB`有Crash Safe功能，當主機發生故障時，可保證還在處理的資料能完全寫入，而且具有一致性。

> 5.1版之前，`MyISAM`一直是預設的儲存引擎，雖然它有著快速、簡單的特性，卻不支援`Transaction`（交易）的特性（不可分割、一致、隔離、耐久，簡稱為`ACID`）、`Foreign Key`（`外鍵`）等功能，但`InnoDB`都有，在5.5版中`MySQL`正式將`InnoDB`更改為預設的儲存引擎。

> `InnoDB`支援了`Transaction`的上述4種特性，它的特色是將數個`SQL`指令視為一個整體執行，只要其中一個指令錯誤，就會取消掉所有步驟，舉個例子，假設你正在提款機前操作某項交易，如果在過程中某個步驟發生錯誤，例如停電，則系統會取消掉整筆交易，而不是取消該步驟，這對於交易來說是一個很重要的安全機制；它同時支援`Foreign Key`，可以將數個資料表連結，而這最主要的功能就是確保資料的一致性；`InnoDB`也支援`資料列鎖定`（`Row-level locking`），如果有使用者正在操作一張資料表，那麼`InnoDB`會鎖定對方目前在存取的資料列，而非鎖定整個資料表，如此若別人存取同資料表的其他資料列就不會受影響。

> `MySQL`在5.5版中更進一步加強了`InnoDB`儲存引擎的功能，例如改善資料毀壞修復，過去如果資料庫發生了資料損壞，可能要數小時的修復時間，現在只要幾分鐘就能完成。另外針對資料庫暫存區的改進，現在`MySQL`可以新增多個暫存區（Multiple Buffer Pool Instances）──Buffer Pool是記憶體中的暫存區塊，將資料放在這個暫存區可以增加存取的速度，不過如果同時有多個執行?對暫存區進行存取，就會造成傳輸的瓶頸，而MySQL 5.5版允許使用者可以開啟最多64個暫存區，以改善這個問題，進而增加存取性能，同時管理者也可以自由設定暫存區的大小。

> 一般資料庫若沒有分區功能，又想將資料分散儲存，它可能必須將資料庫或資料表移動分散到不同的磁碟，然後利用連結指向這些位置，以提升系統的速度。而`分區`（`Partition`）則是更進階的作法，它是將資料表中同個屬性的欄或列進行分割，在不同的地方儲存成單獨的資料表，例如：我們可以將某資料表中不常使用到的欄位分配到同一個分區，這樣可以減少搜尋資料表的時間；另外，在搜尋資料時，資料庫系統如果知道要搜尋的資料在那個分區，就可以直接到該分區找，這樣會比搜尋整個資料表快。

> `MySQL`先前就有分區功能，在5.5版又有一些強化，例如：在5.1版中不支援對非整數類型例如Date（日期）分區，必須使用函數進行轉換，在5.5版中則可以對日期直接進行分區，而不需再透過函數，同時也加入了`TRUNCATE PARTITION`指令。

> 以往要刪除分區裡的資料只能用`DROP PARTITION`指令，該指令可以刪除分區的資料但同時也會將分區刪除，如果資料庫系統管理員想刪除分區的某部份資料，但又想保留分區本身就會非常麻煩，現在有了`TRUNCATE PARTITION`指令可以刪除分區資料，同時又保留分區本身，這對於管理員來說相當有幫助。

> 支援半同步複製也是新版才有的機制。在5.5版之前，`MySQL`只支援非同步複製，也就是說`Master`（`主要資料庫`）在使用者送來一個操作請求時，先將該操作處理完畢回覆給使用者，再將該記錄傳送給`Slave`（`備份資料庫`），**缺點是兩套資料庫之間的內容會有時間差，如果主要資料庫發生資料毀損，而備份資料庫的資料還沒更新到與主資料庫資料一致的情形下，那麼就無法靠備用資料庫維持資料一致性**。

> 而在5.5版中，`MySQL`提供了`半同步複製機制`(`Semi-Synchronous Replication`)，這個功能可以保證資料在主從伺服器同時傳入資料的情況下，將結果回傳給使用者，而**所謂的半同步，是指它只保證資料已經傳到備份資料庫上，卻不保證資料在備份資料庫上執行完成，所以還是有可能會發生資料不同步的狀況發生**。

> `MySQL` 5.5版本已經推出且穩定運行了一段時間，而5.6版也即將推出，預計會加入全文檢索及支援`NoSQL `，會是一個重大更新。

> `甲骨文` (`Oracle`) 釋出開放源碼的最新關聯性資料庫版本`MySQL` 5.7.4 `開發者里程碑版` (`Development Milestone Release, DMR`)，強調為了符合現代雲端與嵌入應用的需求，大幅改善了`MySQL`的效能、擴展性與可靠性，在標竿測試中其查詢速度是`MySQL` 5.6的兩倍、`MySQL` 5.5的3倍。

> 在效能與擴展性上，`MySQL` 5.7.4針對`固態硬碟`強化了效能與吞吐量，改善`InnoDB`緩衝區與元資料鎖定，強化其`半同步的複製`效能，其每秒查詢速度是5.6版的2倍，5.5版的3倍。在管理功能上，帶來更精確的成本計算，改善效能架構，並有符合`AES`標準的256bit加密及新的密碼管理選項。

> `甲骨文` (`Oracle`) 發表`MySQL Fabric`，這是一個可用來管理眾多`MySQL`伺服器的開放源碼延伸框架，強調高可得性與擴充能力，為甲骨文`MySQL Utilities` 1.4.3的元件之一。

> `MySQL Fabric`具備自動化的故障偵測、資料切割 (`Sharding`) 能力，也支援`PHP`、`Python`及`Java`連結器(`Connector`)。**它能夠監控主要的資料庫，在發現該資料庫伺服器故障時，可立即遴選其他資料庫當作主資料庫；還能自動把交易傳送到主資料庫，並保持從屬資料庫的查詢負載平衡，可自應用程式清楚檢視資料庫伺服器的拓撲結構及狀態**。

> 把資料庫切割成分片（`shards`）並放置到不同伺服器的用意在於疏解單一伺服器的負載，並改善效能。其自動化的資料切割與重新切割能力允許表格的讀寫可橫向擴展；可選擇所要切割的表格及指定切割欄位；或是把既有已切割的分片移到新的伺服器或再拆分這些分片。

> `MySQL` 5.5是在2010年12月發表，`MySQL` 5.6則於2013年2月釋出。

> Web2.0概念的成熟發展促成了`NoSQL`資料庫的興起。過去幾年使用者網路行為的改變，挑戰了`關聯式資料庫`的效能和彈性，因應爆量讀寫頻繁的需求，`NoSQL`的概念重新被提出，`NoSQL`資料庫的特色是不使用`SQL`當作查詢語言、動態列儲存及分散式架構等。

> `關聯式資料庫`的操作具有`ACID`的特性，第一、`不可分割性` (`Atomicity`)，在一次的`交易` (`Transaction`)，操作必須全部成功，一旦發生錯誤，所有資料更動將回復到交易之前，不容許有中間狀態，第二、`一致性` (`Consistency`)，所有的`交易`，都必須遵守資料庫設定規則，第三、`獨立性`  (`Isolation`) 資料交易進行中，不受其他交易影響，第四、`持久性` (`Durability`)，交易成功後，所做的任何變更都會被永久保存。這些特性在金融交易很重要，可以確保其過程安全及結果的可靠性，而過去的靜態網頁的資料庫操作，讀取比例遠高於寫入，在關聯式資料庫也是沒有問題的。

> 但近年盛行的網路服務，如社群網站、社群遊戲甚至是網路遊戲，龐大的使用者規模以及頻繁互動的操作模式，`關聯式資料庫`的可靠性無用武之地，反而成為效能瓶頸。

> `NoSQL`資料庫因其`分散式架構`，容量容易擴充，但資料更新可能會有不同步的狀況，對此`NoSQL`資料庫採用`資料遲早會一致` (`Eventually Consistency`) 的做法，不同資料庫伺服器，或許資料會因時間差而不同，但終究會同步。

> `關聯式資料庫`必須遵守`ACID`的特性，`NoSQL`資料庫應用上更具彈性，**兩類型資料庫系統沒有優劣之分，只有需求考量不同**。

> 資料庫的設計是採取主從 (`Master/Slave`) 架構，並沒有考量到高可用性。這種架構的好處是，讀取與寫入分別由不同主機負責，因此，當使用者端的資料寫入`Master`主機後，會進一步複寫到`Slave`主機，等到使用者端需要讀取資料時，就可直接由`Slave`主機回應，藉此達到降低`Master`主機負載的目標。

> 然而，這種架構的設計，因為只有一臺`Master`主機，沒有考量到高可用性，只要`Master`主機發生故障，就會影響到網站服務。

> `MySQL`使用`memcached`分散式快取系統相容的`API`作為`NoSQL`，透過該程式介面可以直接驅動`InnoDB`儲存引擎，大幅提昇讀取速度。另外，`memcached`的資料都是儲存在記憶體之中，因此執行效率遠高於一般放置於硬碟的`SQL`資料庫。

> 負責維護`MySQL`開源版本的資料庫服務商`Percona`，該公司旗下`QA`工程師`David Bennett`透露，在`Percona Live 2016`會議上，`MySQL`社群決定以後不會推出`MySQL 5.8`，而是直接改版為`MySQL 8.0`。`David Bennett`表示，8.0版將會針對記憶體、`SSD`和硬碟的特性，來優化查詢。另外也不再需要依賴`MyISAM`，不用使用`FRM`檔案。8.0的新虛擬索引機制可以支援`JSON`的文件陣列。