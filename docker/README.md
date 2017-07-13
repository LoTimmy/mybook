![](http://i.imgur.com/KtX3yig.png)

> `Docker`是一項最近竄紅的`容器技術` (`Container`)，讓開發人員可以在本機撰寫並測試完應用後「打包」成大型可執行檔送到其他地方之後再執行。和傳統`Virtual Machine`技術相較，`Docker`更為輕巧、執行也更快速。

> `Docker`是一個`Client-Server`架構的應用程式，在一個`Docker`執行環境中，包括了`Docker`用戶端程式、和在`背景執行` (`Daemon`)的Docker伺服器 (也稱為Docker Engine)，另外還有將Container封裝後的Docker映象檔，用來儲存映象檔的Registry服務。官方提供的映象檔Registry服務就稱為`Docker Hub`，這是類似`Github`程式碼`Repository`儲存服務的映象檔Repository儲存服務。

> 安裝`Docker`之後，會提供了一個命令列的用戶端程式來和在背景執行的Docker伺服器溝通。開發者可以直接從`Docker Hub`下載`Docker映象檔`(docker pull 指令)，再執行(docker run 指令)就可以用這個映象檔來建立一個`Container`。

> `Docker`映象檔是一種分層堆疊的運作方式，採用了`aufs`的檔案架構。要建立一個可提供應用程式完整執行環境的`Container映象檔`，要先從一個`基礎映象檔`(`Base Image`)開始疊起，一層層將不同`Stack`的`Docker映象檔`疊加上去，最後組合成一個應用程式所需`Container`執行環境的映象檔，而每一個Stack也都是可以會匯出成 (docker commit 指令) 一個映象檔。舉例來說，假設一個網頁執行環境需要有`OS`、`Apache`網站伺服器、`MySQL`資料庫、`Ruby`執行環境等不同的`Stack`。

> 虛擬化風潮席捲全球，技術日益翻新，目前最受矚目的是`Docker`，**其虛擬獨立環境內無須另外運行的作業系統核心及相關系統程，所以需動用到的系統資源大幅減少**。

> 虛擬化風潮席捲全球，技術日益翻新，目前市面上最熱門的作業系統層級虛擬化技術非`Docker`莫屬，因為**它不需要`Hypervisor`**。`Docker`是由`Linux`作業系統核心所構築的虛擬獨立環境為基礎，而每個`Docker`的虛擬獨立環境中並不需要執行另外運行的作業系統核心、相關系統程式及驅動程式，只需要所運作應用系統的相關程式庫與相關應用程式即可。 
> 因此可以想見，跟平台虛擬化技術`Xen`、`KVM`、`Microsoft Hyper-V`甚至`VMware`來相比，`Docker`所需的系統資源可說是少之又少，因為無須模擬轉譯硬體，所以同樣的硬體資源`Docker`可以執行得更快，因為不必執行額外的作業系統核心以及相關程式，所以同樣的硬體資源可以運作更多份`Docker`虛擬獨立環境。
 
> 不過，因為`Docker`是依附在`Linux`作業系統核心下的技術，所以`Docker`本身所建立的虛擬獨立環境就只能執行跟`Linux`相關的應用，這些應用可以是運作在不同的`Linux`發行版上的應用，只要在環境內這個應用本身相關的程式庫與程式具備即可。如果是以`CentOS`為運行`Docker`的基礎作業系統，在`Docker`建立的虛擬獨立環境內，就可以執行`Debian`、`Ubuntu`或是`Arch Linux`等其他`Linux`發行版的應用程式。
 
> 虛擬化環境以`Hypervisor`作為底層硬體資源與上層虛擬主機、作業系統的中介，而包括主機、磁碟、網路等所有上層物件，都是由`Hypervisor`所創建、並在`Hypervisor`上運作的虛擬物件，所有資料存取運作也都離不開`Hypervisor`這一層的協調。

> `Linux Container` (`LXC`) 的概念有別於現今伺服器虛擬化的主流技術 - `虛擬機器` (`Virtual Machine`)，**`虛擬機器`是以整臺電腦為基礎的虛擬化，而`Linux Container`的作法則是著眼於應用程式的虛擬化**。

> `虛擬機器`的做法是藉由`Hypervisor`軟體層，將硬體運算資源抽象化，再提供給每一臺虛擬機器，雖然每臺虛擬機器所分配到的運算資源，實際上只占硬體資源的一部分，但透過`Hypervisor`的作用，虛擬機器會以為它擁有獨立的硬體資源。

> **`Linux Container`技術則是如同貨櫃的概念，把應用程式打包成一個貨櫃，包含執行該應用程式最基本的作業系統核心、程式碼、函式庫等，讓應用程式可隔離、可移動，並且直接使用由作業系統來分割的硬體資源，因此不需要透過`Hypervisor`軟體層來配置硬體資源**。

> 因為不需要多一個`Hypervisor`軟體層，`Linux Container`最大的訴求就是輕量級的架構，它的映像檔只需包含一個小型的作業系統核心，比起虛擬機器是一個完整的作業系統來得小。也因為容量小、輕量化，部署或移動`Container`的速度比虛擬機器快很多，產生一個`Container`是以秒計算，然而產生一個虛擬機器卻是以分計算。

> 在提到`Docker`的外部第三方協力專案時，如果沒有提到`Kubernetes`，就表示遺漏了重要項目。`Kubernetes`是一個由`Google`所發展出來的`Docker`管理工具開放原始碼專案，用來協助在不同叢集群和不同電腦中部署`Container`。除了透過在叢集群中保持`Container`的部署平衡來協助管理`Docker`節點的工作負載，`Kubernetes`同時提供了讓`Container`之間彼此溝通的功能，以減少開放網路埠的需求，也能增加其他修改創新的機會。`Kubernetes`的這些特色與功能，和`Docker`一樣是以`Go`語言寫成，未來將因此很有機會被併入到`Docker`之內。

> `Docker Enterprise Edition` (`Docker EE`)
> 免費版的`Docker Engine`更名為`Docker Community Edition` (`CE`)。

![](http://i.imgur.com/22S5qmn.png)
![](http://i.imgur.com/iUBa3dw.png)
![](http://i.imgur.com/lcXEoCK.png)

![Imgur](http://i.imgur.com/08lDi3b.png)

#### :books: 參考網站：
- [效能更快、資源更省 Docker虛擬化技術簡介](http://www.netadmin.com.tw/article_content.aspx?sn=1503060001)
- [VM太肥   紅帽擁抱新型輕量級虛擬化](http://www.ithome.com.tw/news/86808)
- [10個Q&A快速認識Docker](http://www.ithome.com.tw/news/91847)
- [如何搭配 Azure 使用 docker-machine](https://azure.microsoft.com/zh-tw/documentation/articles/virtual-machines-docker-machine/)
- [kubernetes](https://github.com/kubernetes/kubernetes)
- [kubernetes](https://kubernetes.io/)
