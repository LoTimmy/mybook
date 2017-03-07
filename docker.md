![](https://assets-cdn.github.com/images/modules/site/docker_logo.png?sn?sn)

<img src="http://i.imgur.com/KtX3yig.png" width="200">

- `Docker`是一項最近竄紅的`容器技術` (`Container`)，讓開發人員可以在本機撰寫並測試完應用後「打包」成大型可執行檔送到其他地方之後再執行。和傳統`Virtual Machine`技術相較，`Docker`更為輕巧、執行也更快速。
- `Docker`是一個`Client-Server`架構的應用程式，在一個`Docker`執行環境中，包括了`Docker`用戶端程式、和在`背景執行` (`Daemon`)的Docker伺服器 (也稱為Docker Engine)，另外還有將Container封裝後的Docker映象檔，用來儲存映象檔的Registry服務。官方提供的映象檔Registry服務就稱為`Docker Hub`，這是類似`Github`程式碼`Repository`儲存服務的映象檔Repository儲存服務。
- 安裝`Docker`之後，會提供了一個命令列的用戶端程式來和在背景執行的Docker伺服器溝通。開發者可以直接從`Docker Hub`下載`Docker映象檔`(docker pull 指令)，再執行(docker run 指令)就可以用這個映象檔來建立一個`Container`。
- `Docker`映象檔是一種分層堆疊的運作方式，採用了`aufs`的檔案架構。要建立一個可提供應用程式完整執行環境的`Container映象檔`，要先從一個`基礎映象檔`(`Base Image`)開始疊起，一層層將不同`Stack`的`Docker映象檔`疊加上去，最後組合成一個應用程式所需`Container`執行環境的映象檔，而每一個Stack也都是可以會匯出成 (docker commit 指令) 一個映象檔。舉例來說，假設一個網頁執行環境需要有`OS`、`Apache`網站伺服器、`MySQL`資料庫、`Ruby`執行環境等不同的`Stack`。
- 虛擬化風潮席捲全球，技術日益翻新，目前最受矚目的是`Docker`，**其虛擬獨立環境內無須另外運行的作業系統核心及相關系統程，所以需動用到的系統資源大幅減少**。
- 虛擬化風潮席捲全球，技術日益翻新，目前市面上最熱門的作業系統層級虛擬化技術非`Docker`莫屬，因為**它不需要`Hypervisor`**。`Docker`是由`Linux`作業系統核心所構築的虛擬獨立環境為基礎，而每個`Docker`的虛擬獨立環境中並不需要執行另外運行的作業系統核心、相關系統程式及驅動程式，只需要所運作應用系統的相關程式庫與相關應用程式即可。 
- 因此可以想見，跟平台虛擬化技術`Xen`、`KVM`、`Microsoft Hyper-V`甚至`VMware`來相比，`Docker`所需的系統資源可說是少之又少，因為無須模擬轉譯硬體，所以同樣的硬體資源`Docker`可以執行得更快，因為不必執行額外的作業系統核心以及相關程式，所以同樣的硬體資源可以運作更多份`Docker`虛擬獨立環境。 
- 不過，因為`Docker`是依附在`Linux`作業系統核心下的技術，所以`Docker`本身所建立的虛擬獨立環境就只能執行跟`Linux`相關的應用，這些應用可以是運作在不同的`Linux`發行版上的應用，只要在環境內這個應用本身相關的程式庫與程式具備即可。如果是以`CentOS`為運行`Docker`的基礎作業系統，在`Docker`建立的虛擬獨立環境內，就可以執行`Debian`、`Ubuntu`或是`Arch Linux`等其他`Linux`發行版的應用程式。 

- 虛擬化環境以`Hypervisor`作為底層硬體資源與上層虛擬主機、作業系統的中介，而包括主機、磁碟、網路等所有上層物件，都是由`Hypervisor`所創建、並在`Hypervisor`上運作的虛擬物件，所有資料存取運作也都離不開`Hypervisor`這一層的協調。
- `Linux Container` (`LXC`) 的概念有別於現今伺服器虛擬化的主流技術 - `虛擬機器` (`Virtual Machine`)，**`虛擬機器`是以整臺電腦為基礎的虛擬化，而`Linux Container`的作法則是著眼於應用程式的虛擬化**。
- `虛擬機器`的做法是藉由`Hypervisor`軟體層，將硬體運算資源抽象化，再提供給每一臺虛擬機器，雖然每臺虛擬機器所分配到的運算資源，實際上只占硬體資源的一部分，但透過`Hypervisor`的作用，虛擬機器會以為它擁有獨立的硬體資源。
- **`Linux Container`技術則是如同貨櫃的概念，把應用程式打包成一個貨櫃，包含執行該應用程式最基本的作業系統核心、程式碼、函式庫等，讓應用程式可隔離、可移動，並且直接使用由作業系統來分割的硬體資源，因此不需要透過`Hypervisor`軟體層來配置硬體資源**。
- 因為不需要多一個`Hypervisor`軟體層，`Linux Container`最大的訴求就是輕量級的架構，它的映像檔只需包含一個小型的作業系統核心，比起虛擬機器是一個完整的作業系統來得小。也因為容量小、輕量化，部署或移動`Container`的速度比虛擬機器快很多，產生一個`Container`是以秒計算，然而產生一個虛擬機器卻是以分計算。

![](http://i.imgur.com/22S5qmn.png)
![](http://i.imgur.com/iUBa3dw.png)
![](http://i.imgur.com/lcXEoCK.png)

![Imgur](http://i.imgur.com/08lDi3b.png)

#### :books: 參考網站：
- [效能更快、資源更省 Docker虛擬化技術簡介](http://www.netadmin.com.tw/article_content.aspx?sn=1503060001)
- [VM太肥   紅帽擁抱新型輕量級虛擬化](http://www.ithome.com.tw/news/86808)
- [10個Q&A快速認識Docker](http://www.ithome.com.tw/news/91847)
- [如何搭配 Azure 使用 docker-machine](https://azure.microsoft.com/zh-tw/documentation/articles/virtual-machines-docker-machine/)

---

### 在 `Ubuntu` 14.04 LTS 上建置 `Docker`

![](https://hub.docker.com/public/images/official/ubuntu.png) + ![](http://i.imgur.com/co4QPyz.png)

安裝作業系統及`Docker`相關套件。
因本文主要介紹`Docker`如何安裝及設定，作業系統方面就不再詳述。

```console
shell> lsb_release -a
```
![Imgur](http://i.imgur.com/ci0qpEH.png)

`/etc/apt/sources.list.d/docker.list`

```
Ubuntu Precise 12.04 (LTS)
Ubuntu Trusty 14.04 (LTS)
Ubuntu Wily 15.10
Ubuntu Xenial 16.04 (LTS)
```

#### :books: 參考網站：
- [ubuntulinux](https://docs.docker.com/engine/installation/linux/ubuntulinux/)
- [mac](https://docs.docker.com/engine/installation/mac/)
- [docker-for-mac](https://docs.docker.com/docker-for-mac/)

```console
shell> sudo apt-get update
```

```
deb https://apt.dockerproject.org/repo ubuntu-precise main
deb https://apt.dockerproject.org/repo ubuntu-trusty main
deb https://apt.dockerproject.org/repo ubuntu-wily main
deb https://apt.dockerproject.org/repo ubuntu-xenial main
```

```console
shell> sudo apt-get update
shell> sudo apt-get install apt-transport-https ca-certificates
shell> sudo apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D

shell> echo "<REPO>" | sudo tee /etc/apt/sources.list.d/docker.list

shell> sudo apt-get install linux-image-generic-lts-trusty
shell> sudo reboot

shell> sudo apt-get install linux-image-extra-$(uname -r) linux-image-extra-virtual


shell> sudo apt-get install docker-engine
shell> sudo service docker start
shell> sudo docker run hello-world
```

```
WARNING: Your kernel does not support cgroup swap limit. WARNING: Your
kernel does not support swap limit capabilities. Limitation discarded.
```

`/etc/default/grub`

```
GRUB_CMDLINE_LINUX="cgroup_enable=memory swapaccount=1"
```
```console
shell> sudo update-grub
```

```console
shell> curl -sSL https://get.docker.com/ | sh
shell> wget -qO- https://get.docker.com/ | sh
```
```
If you would like to use Docker as a non-root user, you should now consider
adding your user to the "docker" group with something like:
```

```console
shell> sudo usermod -aG docker your-user
```

#### :books: 參考網站：
- [ubuntulinux](https://docs.docker.com/v1.4/installation/ubuntulinux/)
- [ubuntulinux](https://docs.docker.com/engine/installation/linux/ubuntulinux/)
- [compose](https://docs.docker.com/compose/gettingstarted/)
- [step_one](https://docs.docker.com/v1.11/linux/step_one/)

```console
shell> docker info # Check that you have a working install
```
```
Containers: 0
 Running: 0
 Paused: 0
 Stopped: 0
Images: 0
Server Version: 1.10.2
Storage Driver: aufs
 Root Dir: /var/lib/docker/aufs
 Backing Filesystem: extfs
 Dirs: 0
 Dirperm1 Supported: true
Execution Driver: native-0.2
Logging Driver: json-file
Plugins: 
 Volume: local
 Network: null host bridge
Kernel Version: 3.19.0-51-generic
Operating System: Ubuntu 14.04.4 LTS
OSType: linux
Architecture: x86_64
CPUs: 1
Total Memory: 237.2 MiB
Name: ubuntu
ID: GXLJ:O2FJ:FNRI:WHZI:VHEH:OCSZ:ELTZ:FK7W:LGQY:HBX4:6IMH:LAK4
WARNING: No swap limit support

shell> sudo docker version

Client:
 Version:      1.10.2
 API version:  1.22
 Go version:   go1.5.3
 Git commit:   c3959b1
 Built:        Mon Feb 22 21:37:01 2016
 OS/Arch:      linux/amd64

Server:
 Version:      1.10.2
 API version:  1.22
 Go version:   go1.5.3
 Git commit:   c3959b1
 Built:        Mon Feb 22 21:37:01 2016
 OS/Arch:      linux/amd64
```

```console
shell> docker pull ubuntu # Download an ubuntu image
shell> docker pull debian # Download an debian image
shell> docker pull centos # Download an centos image
shell> docker pull mysql

shell> docker pull ubuntu:12.04
```

<kbd>Ctrl</kbd>-<kbd>p</kbd>+<kbd>Ctrl</kbd>-<kbd>q</kbd>

```console
shell> docker run --help

shell> docker run -it ubuntu /bin/bash
shell> docker attach <container_id>
```

```console
shell> docker run -i -t debian /bin/bash
shell> docker run -d -i -t ubuntu /bin/bash

shell> docker run --rm -i -t -p 80:80 nginx
shell> docker run --name test -d -p 80:80 nginx 

shell> docker run -d coreos/apache /usr/sbin/apache2ctl -D FOREGROUND
shell> docker run -d -p 80:80 coreos/apache /usr/sbin/apache2ctl -D FOREGROUND

shell> docker run --name test -i -t ubuntu /bin/bash
shell> docker export test > latest.tar

shell> cat latest.tar | docker import - test:latest

shell> cat exampleimage.tgz | sudo docker import - exampleimagelocal:new

shell> docker run ubuntu:14.04  echo 'HelloWorld'
shell> docker images

shell> docker search
```
---
```console
shell> docker ps # Lists only running containers
shell> docker ps -a # Lists all containers
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS                      PORTS               NAMES
4f7e507c2c05        ubuntu:latest       /bin/bash           25 hours ago        Exited (0) 25 hours ago                         cranky_morse           

shell> docker start <container_id>

shell> docker rm <container_id>

shell> docker run --rm ubuntu /bin/ping 8.8.8.8
```

#### :books: 參考網站：
- [basics](https://docs.docker.com/engine/userguide/basics/)


```console
shell> docker run -idt ubuntu:12.04
shell> docker ps
shell> docker ps exec -ti agitated_mccarthy /bin/bash
```

```console
shell> docker commit <container_id> <some_name> # Commit your container to a new named image
shell> docker images # List your containers
```

```console
shell> JOB=$(sudo docker run -d -p 4444 ubuntu:12.10 /bin/nc -l 4444) # Bind port 4444 of this container, and tell netcat to listen on it

shell> PORT=$(sudo docker port $JOB 4444 | awk -F: '{ print $2 }') # Which public port is NATed to my container?
shell> echo hello world | nc 127.0.0.1 $PORT # Connect to the public port
shell> echo "Daemon received: $(sudo docker logs $JOB)" # Verify that the network connection worked
```

---

![](https://raw.githubusercontent.com/docker-library/docs/master/nginx/logo.png)

```console
shell> mkdir -p /docker/nginx/content
shell> docker cp nginx:/etc/nginx/nginx.conf /docker/nginx/nginx.conf

shell> docker run --name web -p 80:80 -v /docker/nginx/content:/usr/share/nginx/html:ro -v /docker/nginx:/etc/nginx/nginx.conf:ro -d nginx

shell> docker run --name web -p 80:80 -v /docker/nginx/content:/usr/share/nginx/html:ro -v /docker/nginx/nginx.conf:/etc/nginx/nginx.conf:ro -d nginx


shell> docker run --name web -p 80:80 -v /docker/nginx/content:/usr/share/nginx/html:ro -d nginx
shell> docker run --name web -P -v /some/content:/usr/share/nginx/html:ro -d nginx
shell> docker logs <container_id>

shell> docker exec -ti web /bin/bash

shell> docker rm web
```

Dockerfile
```
FROM nginx
COPY nginx.conf /etc/nginx/nginx.conf

VOLUME ["/usr/share/nginx/html"]
```

/var/lib/docker/volumes

```console
shell> docker build -t docker-nginx .
shell> docker run --name web -P -d docker-nginx
```


### :books: 參考網站：
- [nginx](https://hub.docker.com/_/nginx/)
- [build](https://docs.docker.com/engine/reference/commandline/build/)
- [build](https://docs.docker.com/mac/step_four/)

---

```console
shell> mkdir -p /docker/mysql
shell> sudo docker run --name some-mysql -v /docker/mariadb:/var/lib/mysql -p 3306:3306 -e MYSQL_ROOT_PASSWORD=mysecretpassword -d mysql
shell> sudo docker run --name some-mysql -P -e MYSQL_ROOT_PASSWORD=mysecretpassword -d mysql
shell> sudo docker run -it --link some-mysql:mysql --rm mysql sh -c 'exec mysql -h"$MYSQL_PORT_3306_TCP_ADDR" -P"$MYSQL_PORT_3306_TCP_PORT" -uroot -p"$MYSQL_ENV_MYSQL_ROOT_PASSWORD"'



shell> sudo docker run  -e MYSQL_ROOT_PASSWORD=mysecretpassword -d mysql:latest

shell> sudo docker run --name mysql -p 3306:3306 \
       -v /my/custom:/etc/mysql/conf.d \
       -v /my/own/datadir:/var/lib/mysql \
       -e MYSQL_ROOT_PASSWORD=mysecretpassword \
       -d mysql:latest                

shell> docker exec -ti mysql /bin/bash



shell> mkdir -p /docker/mariadb
shell> sudo docker run --name some-mariadb -v /docker/mariadb:/var/lib/mysql -p 3306:3306 -e MYSQL_ROOT_PASSWORD=mysecretpassword -d mariadb
shell> sudo docker run --name some-mariadb -P -e MYSQL_ROOT_PASSWORD=mysecretpassword -d mariadb
shell> sudo docker run -it --link some-mariadb:mysql --rm mariadb sh -c 'exec mysql -h"$MYSQL_PORT_3306_TCP_ADDR" -P"$MYSQL_PORT_3306_TCP_PORT" -uroot -p"$MYSQL_ENV_MYSQL_ROOT_PASSWORD"'

shell> mkdir -p /docker/redis
shell> docker run --name some-redis -p 6379:6379 -d redis
shell> docker run --name some-redis -v /docker/redis:/data -p 6379:6379 -d redis
shell> docker run --name some-redis -v /docker/redis:/data -v /myredis/conf/redis.conf:/usr/local/etc/redis/redis.conf -p 6379:6379 -d redis /usr/local/etc/redis/redis.conf
shell> docker run -it --link some-redis:redis --rm redis sh -c 'exec redis-cli -h "$REDIS_PORT_6379_TCP_ADDR" -p "$REDIS_PORT_6379_TCP_PORT"'

shell> mkdir -p /docker/mongo/db
shell> docker run --name some-mongo -p 27017:27017 -d mongo
shell> docker run --name some-mongo -v /docker/mongo/db:/data/db -p 27017:27017 -d mongo
shell> docker run -it --link some-mongo:mongo --rm mongo sh -c 'exec mongo "$MONGO_PORT_27017_TCP_ADDR:$MONGO_PORT_27017_TCP_PORT/test"'

shell> docker inspect some-mongo
shell> docker logs some-mongo

shell> sudo docker run -v ~/csharp:/srv  -i -t mono /bin/bash
```


**Dockerfile**
```
# Comment
FROM ubuntu:14.04
MAINTAINER Timmy Lo <timmylo@kimo.com>
RUN apt-get -qq update
RUN apt-get -qqy dmidecode
RUN ["/bin/bash", "-c", "dmidecode"]
RUN ["/bin/bash", "-c", "echo hello"]
```

```console
shell> sudo docker build -t some-custom-nginx .
```

---

安裝 Compose
```console
shell> curl -L https://github.com/docker/compose/releases/download/1.6.2/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose

shell> chmod +x /usr/local/bin/docker-compose
shell> docker-compose --version
docker-compose version 1.6.2, build 4d72027
```

```console
shell> mkdir composetest
shell> cd composetest
```

docker-compose.yml
```
version: '2'
services:
  web:
    image: nginx
    network_mode: "bridge"
    dns: 8.8.8.8
    ports:
     - "80:80"
     - "443:443"
    volumes:
     - /docker/nginx/content:/usr/share/nginx/html
    depends_on:
     - redis
     - mongo
     - mysql
    links:
     - db
  redis:
    image: redis
    network_mode: "bridge"
    ports:
     - "6379:6379"
  mongo:
    image: mongo
    network_mode: "bridge"
    ports:
     - "27017:27017"
  db:
    image: mysql
    network_mode: "bridge"
    ports:
     - "3306:3306"
  volumes:
     - /opt/data:/var/lib/mysql
    environment:
     - MYSQL_ROOT_PASSWORD=my-secret-pw
```

```console
shell> docker-compose up
shell> docker-compose up -d

shell> docker-compose stop

shell> docker-compose rm -f web
```

```console
shell> docker-compose ps
```

```console
shell> docker-compose run web env
```

### :books: 參考網站： 
- [virtual-machines-docker-compose-quickstart](https://azure.microsoft.com/zh-tw/documentation/articles/virtual-machines-docker-compose-quickstart/)
- [compose-file](https://docs.docker.com/compose/compose-file/)


---

```console
shell> docker-machine ls
shell> docker-machine create --driver virtualbox default
shell> docker-machine env default

shell> eval "$(docker-machine env default)"
shell> FOR /f "tokens=*" %i IN ('docker-machine env default') DO %i
```

```console
shell> brew cask install virtualbox
shell> brew install docker
shell> brew install boot2docker

shell> boot2docker init # Create a new Boot2Docker VM.
shell> boot2docker start # Start the boot2docker VM.

shell> boot2docker up
shell> boot2docker status

shell> boot2docker ip # Get the address of the boot2docker VM.
shell> boot2docker stop # Stop the boot2docker application.
shell> docker run hello-world # Run the hello-world container to verify your setup.
shell> boot2docker shellinit # Display the environment variables for the Docker client.

shell> docker run -d -P --name web nginx
shell> docker ps # Display your running container with docker ps command
```

```console
shell> docker run -d -p 80:80 --name webserver nginx
```

### :books: 參考網站：
- [](https://docs.docker.com/machine/get-started/)

---

```
├── docker-compose.yml
└── web
    ├── apache2.conf
    └── Dockerfile
```

web/Dockerfile
```
# Comment
FROM ubuntu:trusty
MAINTAINER Timmy Lo

ENV APACHE_RUN_USER www-data 
ENV APACHE_RUN_GROUP www-data
ENV APACHE_PID_FILE /var/run/apache2/apache2.pid
ENV APACHE_LOG_DIR /var/log/apache2
ENV APACHE_LOCK_DIR /var/lock/apache2

ENV TERM xterm

RUN apt-get -qq update && \
    DEBIAN_FRONTEND=noninteractive apt-get -y upgrade && \
    DEBIAN_FRONTEND=noninteractive apt-get -y install supervisor pwgen  && \
    apt-get -y install git apache2 libapache2-mod-php5 php5-mysql php5-pgsql php5-gd php-pear php-apc curl && \
    apt-get -y install ssl-cert apache2-utils && \
    apt-get -y install mysql-client unzip && \
    curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin && \
    mv /usr/local/bin/composer.phar /usr/local/bin/composer

# 
RUN apt-get -y install libapache2-modsecurity modsecurity-crs
RUN a2enmod security2
RUN cp /etc/modsecurity/modsecurity.conf-recommended /etc/modsecurity/modsecurity.conf

ADD apache2.conf /etc/apache2/sites-enabled/000-default.conf

RUN a2enmod rewrite

RUN apt-get -y autoremove

RUN cd /var/www/html && composer require codeigniter/framework && composer create-project codeigniter/framework test
RUN chown -R $APACHE_RUN_USER /var/www/html
RUN chgrp -R $APACHE_RUN_GROUP /var/www/html

ADD .htaccess /var/www/html/test

EXPOSE 80

VOLUME ["/var/www", "/var/log/apache2", "/etc/apache2"]

CMD ["-X"]
ENTRYPOINT ["apache2"]
```

docker-compose.yml
```
version: '2'
services:
  web:
    build: ./web
    ports:
     - "80:80"
```

```console
shell> docker-compose build
shell> docker-compose up
shell> docker-compose up -d
```

```console
shell> docker inspect web
```

### :books: 參考網站：
- [dockervolumes](https://docs.docker.com/engine/userguide/containers/dockervolumes/)
- [phpinfo](http://php.net/manual/en/function.phpinfo.php)
- [The-TERM-variable](https://www.gnu.org/software/gettext/manual/html_node/The-TERM-variable.html)
- [Setting Environment Variables](https://docs.oracle.com/cd/E19683-01/806-7612/customize-8/index.html)

```console
shell> docker volume ls -qf dangling=true
shell> docker volume rm $(docker volume ls -qf dangling=true)
```

---

- `Dockerfile` – 文字檔案，包含建立新容器映像所需的指令。 這些指令包含將用作基底的現有映像識別碼、在映像建立程序中執行的命令，以及部署容器映像新執行個體時所執行的命令。
- docker build - Docker 引擎命令，其使用 Dockerfile 並觸發映像建立程序。
- `Dockerfile` 在最基本的形式中可以極度簡易。 

- FROM 指令會設定新映像建立程序期間所使用的容器映像。
- RUN 指令指定要執行並擷取至新容器映像的命令。 這些命令可以包含安裝軟體、建立檔案和目錄，以及建立環境設定等項目。
- COPY 指令會將檔案和目錄複製到容器的檔案系統。 檔案和目錄必須位在相對於 Dockerfile 的路徑。
- ADD 指令與 COPY 指令非常類似，但是前者包含其他功能。 除了將檔案從主機複製到容器映像，ADD 指令也可以從具有 URL 規格的遠端位置複製檔案。
- WORKDIR 的指示會為其他 Dockerfile 指令設定工作目錄，例如 RUN``CMD，也會設定執行容器映像執行個體的工作目錄。
- CMD 指令會設定部署容器映像執行個體時要執行的預設命令。 例如，如果容器會裝載 NGINX 網頁伺服器，則 CMD 可能包含啟動網頁伺服器的指令，如 nginx.exe。 如果 Dockerfile 中指定了多個 CMD 指令，則只會評估最後的指令。

```
wget - retrieves files from the web
vim - Vi IMproved - enhanced vi editor
unzip - De-archiver for .zip files
git - fast, scalable, distributed revision control system
```

**Dockerfile**

```
# Comment
# Sample Dockerfile

FROM ImageName

FROM <image>
FROM <image>:<tag>
FROM <image>@<digest>

MAINTAINER <name>
RUN <command>
COPY <source> <destination>
ADD <source> <destination>
WORKDIR <path to working directory>
CMD ["<executable", "<param>"]


RUN echo 'we are running some # of cool things'
COPY testfile.txt c:\

FROM busybox
ENV foo /bar
WORKDIR ${foo}   # WORKDIR /bar
ADD . $foo       # ADD . /bar
COPY \$foo /quux # COPY $foo /quux
```

```
FROM ubuntu:14.04
FROM debian
FROM debian:jessie

RUN groupadd -r mysql && useradd -r -g mysql mysql

MAINTAINER Timmy Lo <timmylo@kimo.com>

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get -qq update && \
    DEBIAN_FRONTEND=noninteractive apt-get -qqy install --no-install-recommends  wget vim unzip curl git && \
    rm -rf /var/lib/apt/lists/*


# 安裝 nginx
RUN curl -sSL http://nginx.org/keys/nginx_signing.key | sudo apt-key add - && \
    echo deb http://nginx.org/packages/ubuntu/ "$(lsb_release -sc)" nginx | sudo tee /etc/apt/sources.list.d/nginx.list && \
    echo deb-src http://nginx.org/packages/ubuntu/ "$(lsb_release -sc)" nginx | sudo tee -a /etc/apt/sources.list.d/nginx.list && \
    apt-get -qq update && \
    DEBIAN_FRONTEND=noninteractive apt-get install -qqy --no-install-recommends nginx && \
    rm -rf /var/lib/apt/lists/*

RUN ln -sf /dev/stdout /var/log/nginx/access.log \
	&& ln -sf /dev/stderr /var/log/nginx/error.log

EXPOSE 80 443

CMD ["nginx", "-g", "daemon off;"]
```

```console
shell> docker build -f /path/to/a/Dockerfile .
shell> docker build -t foo/myapp .
shell> docker build -t foo/myapp:1.0.2 -t foo/myapp:latest .
shell> docker run -i -t foo/myapp /bin/bash
```

```
NAME                      DESCRIPTION                                     STARS     OFFICIAL   AUTOMATED
nginx                     Official build of Nginx.                        3604      [OK]       
redis                     Redis is an open source key-value store th...   2452      [OK]       
mysql                     MySQL is a widely used, open-source relati...   2740      [OK]       
busybox                   Busybox base image.                             746       [OK]       
debian                    Debian is a Linux distribution that's comp...   1519      [OK]       
neurodebian               NeuroDebian provides neuroscience research...   25        [OK]
ubuntu                    Ubuntu is a Debian-based Linux operating s...   4337      [OK]       
ubuntu-debootstrap        debootstrap --variant=minbase --components...   25        [OK]       
ubuntu-upstart            Upstart is an event-based replacement for ...   65        [OK]       
```

### :books: 參考網站：
- [builder](https://docs.docker.com/engine/reference/builder/)
- [manage_images](https://msdn.microsoft.com/zh-tw/virtualization/windowscontainers/management/manage_images)
- [manage_windows_dockerfile](https://msdn.microsoft.com/zh-tw/virtualization/windowscontainers/docker/manage_windows_dockerfile)
- [faq](https://docs.docker.com/engine/faq/)

---

```
FROM ubuntu:16.04
MAINTAINER Sven Dowideit <SvenDowideit@docker.com>

RUN apt-get update && apt-get install -y openssh-server
RUN apt-get install -y net-tools
RUN mkdir /var/run/sshd
RUN echo 'root:toor' | chpasswd
RUN sed -i 's/PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config

# SSH login fix. Otherwise user is kicked off after login
RUN sed 's@session\s*required\s*pam_loginuid.so@session optional pam_loginuid.so@g' -i /etc/pam.d/sshd

ENV NOTVISIBLE "in users profile"
RUN echo "export VISIBLE=now" >> /etc/profile

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
```

```
shell> docker build -t openssh-server .
shell> docker run -d -P --name test_sshd openssh-server
shell> docker port test_sshd 22

0.0.0.0:49154


shell> docker inspect test_sshd
shell> ssh root@127.0.0.1 -p 49154
```

### :books: 參考網站：
- [running_ssh_service](https://docs.docker.com/engine/examples/running_ssh_service/)

---

/src/webapp
/src/docs
/opt/webapp

web 
db1 
db2 
/dbdata 
dbstore
 
---

### :books: 參考網站：
- [Docker新版網路功能升級終於支援IPv6，容器可設唯讀強化控管，新增統計API即時監控運作狀態](http://www.ithome.com.tw/news/94137)
- http://docs.docker.com/installation/ubuntulinux/
- [First steps with Docker](http://docs.docker.com/articles/basics/)
- http://docs.docker.com/reference/commandline/cli/

- https://coreos.com/docs/launching-containers/building/getting-started-with-docker/
- http://www.ithome.com.tw/news/91847
- http://www.ithome.com.tw/news/91848
- http://www.ithome.com.tw/news/91602
- http://www.ithome.com.tw/news/92150
- http://www.fig.sh/yml.html
- https://registry.hub.docker.com/_/nginx/
- https://registry.hub.docker.com/_/ubuntu/
- https://registry.hub.docker.com/_/mysql/
