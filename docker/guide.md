<img src="http://i.imgur.com/KtX3yig.png" width="200">

### 安裝 {#installing}

安裝作業系統及`Docker`相關套件。
因本文主要介紹`Docker`如何安裝及設定，作業系統方面就不再詳述。

```console
shell> lsb_release -a
```
```
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.2 LTS
Release:	16.04
Codename:	xenial
```

#### :books: 參考網站：
- [ubuntu](https://docs.docker.com/engine/installation/linux/ubuntu/)
- [mac](https://docs.docker.com/engine/installation/mac/)
- [docker-for-mac](https://docs.docker.com/docker-for-mac/)

```console
shell> sudo apt-get update
shell> sudo apt-get install apt-transport-https ca-certificates curl software-properties-common
shell> curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
shell> echo deb https://apt.dockerproject.org/repo ubuntu-"$(lsb_release -sc)" main | sudo tee /etc/apt/sources.list.d/docker.list 

shell> sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"

shell> sudo apt-get install docker-ce
shell> sudo service docker start
shell> sudo docker run hello-world
```

`Recommended extra packages for Trusty 14.04`

```
shell> sudo apt-get update
shell> sudo apt-get install \
         linux-image-extra-$(uname -r) \
         linux-image-extra-virtual
```

```console
shell> curl -sSL https://get.docker.com/ | sh
shell> wget -qO- https://get.docker.com/ | sh
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
Images: 1
Server Version: 17.03.0-ce
Storage Driver: aufs
 Root Dir: /var/lib/docker/aufs
 Backing Filesystem: extfs
 Dirs: 1
 Dirperm1 Supported: true
Logging Driver: json-file
Cgroup Driver: cgroupfs
Plugins: 
 Volume: local
 Network: bridge host macvlan null overlay
Swarm: inactive
Runtimes: runc
Default Runtime: runc
Init Binary: docker-init
containerd version: 977c511eda0925a723debdc94d09459af49d082a
runc version: a01dafd48bc1c7cc12bdb01206f9fea7dd6feb70
init version: 949e6fa
Security Options:
 apparmor
 seccomp
  Profile: default
Kernel Version: 4.4.0-62-generic
Operating System: Ubuntu 16.04.2 LTS
OSType: linux
Architecture: x86_64
CPUs: 1
Total Memory: 988.3 MiB
Name: ubuntu
ID: PVMT:WHDH:NQFB:BMIL:P4VA:KHNT:5ERC:CUG5:U3ZS:GCKO:AQOB:LVZI
Docker Root Dir: /var/lib/docker
Debug Mode (client): false
Debug Mode (server): false
Registry: https://index.docker.io/v1/
WARNING: No swap limit support
Experimental: false
Insecure Registries:
 127.0.0.0/8
Live Restore Enabled: false

shell> sudo docker version

Client:
 Version:      17.03.0-ce
 API version:  1.26
 Go version:   go1.7.5
 Git commit:   3a232c8
 Built:        Tue Feb 28 08:01:32 2017
 OS/Arch:      linux/amd64

Server:
 Version:      17.03.0-ce
 API version:  1.26 (minimum version 1.12)
 Go version:   go1.7.5
 Git commit:   3a232c8
 Built:        Tue Feb 28 08:01:32 2017
 OS/Arch:      linux/amd64
 Experimental: false
```

```console
shell> docker pull ubuntu # Download an ubuntu image
shell> docker pull debian # Download an debian image
shell> docker pull centos # Download an centos image
shell> docker pull mysql

shell> docker pull ubuntu:12.04
```

`Ctrl`-`p`+`Ctrl`-`q`

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

#### :books: 參考網站：
- [Explore Official Repositories](https://hub.docker.com/explore/)

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

#### :books: 參考網站： 
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

#### :books: 參考網站：
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

#### :books: 參考網站：
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

#### :books: 參考網站：
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

#### :books: 參考網站：
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

```
FROM ubuntu:16.04

RUN apt-get update && apt-get install -y openssh-server apache2 supervisor
RUN mkdir -p /var/lock/apache2 /var/run/apache2 /var/run/sshd /var/log/supervisor

COPY supervisord.conf /etc/supervisor/conf.d/supervisord.conf

EXPOSE 22 80
CMD ["/usr/bin/supervisord"]
```

`supervisord.conf`
```
[supervisord]
nodaemon=true

[program:sshd]
command=/usr/sbin/sshd -D

[program:apache2]
command=/bin/bash -c "source /etc/apache2/envvars && exec /usr/sbin/apache2 -DFOREGROUND"
```

```console
shell> docker build -t mysupervisord .
shell> docker run -p 22 -p 80 -t -i mysupervisord
```

#### :books: 參考網站：
- https://docs.docker.com/engine/admin/using_supervisord/#exposing-ports-and-running-supervisor

---

### docker build {#build}

`Build with PATH`
```console
shell> docker build .
```

`Build with URL`
```console
shell> docker build github.com/creack/docker-firefox
```

`Build with -`
```console
shell> docker build - < Dockerfile
shell> docker build - < context.tar.gz
```

`Tag an image (-t)`

```console
shell> docker build -t vieux/apache:2.0 .
```

`Specify a Dockerfile (-f)`

```console
shell> docker build -f Dockerfile.debug .
shell> docker build -f dockerfiles/Dockerfile.debug -t myapp_debug .
shell> docker build -f dockerfiles/Dockerfile.prod  -t myapp_prod .
```

`.dockerignore`

#### :books: 參考網站：
- https://docs.docker.com/engine/reference/commandline/build/
- https://docs.docker.com/engine/reference/builder/#dockerignore-file

---

### docker cp {#cp}


#### :books: 參考網站：
- https://docs.docker.com/engine/reference/commandline/cp/

---

#### :books: 參考網站：
- [Docker新版網路功能升級終於支援IPv6，容器可設唯讀強化控管，新增統計API即時監控運作狀態](http://www.ithome.com.tw/news/94137)
- http://docs.docker.com/installation/ubuntulinux/
- [First steps with Docker](http://docs.docker.com/articles/basics/)
- http://docs.docker.com/reference/commandline/cli/
- https://docs.docker.com/engine/reference/commandline/run/
- https://coreos.com/docs/launching-containers/building/getting-started-with-docker/
- http://www.ithome.com.tw/news/91847
- http://www.ithome.com.tw/news/91848
- http://www.ithome.com.tw/news/91602
- http://www.ithome.com.tw/news/92150
- http://www.fig.sh/yml.html
- https://registry.hub.docker.com/_/nginx/
- https://registry.hub.docker.com/_/ubuntu/
- https://registry.hub.docker.com/_/mysql/
- https://docs.docker.com/engine/admin/ansible/#usage
