![](https://hub.docker.com/public/images/official/mysql.png)

```console
shell> sudo docker pull mysql:latest
shell> mkdir -p /docker/mysql/datadir
shell> mkdir -p /docker/mysql/custom

shell> docker cp db:/etc/mysql/conf.d /docker/mysql/custom


shell> sudo docker run --name db --restart=always \
-v /etc/localtime:/etc/localtime:ro \
-v /docker/mysql/datadir:/var/lib/mysql \
-v /docker/mysql/custom:/etc/mysql/conf.d \
-p 3306:3306 \
-e MYSQL_ROOT_PASSWORD=mysecretpassword \
-d mysql

shell> sudo docker run -it --link db:mysql --rm mysql sh -c 'exec mysql -h"$MYSQL_PORT_3306_TCP_ADDR" -P"$MYSQL_PORT_3306_TCP_PORT" -uroot -p"$MYSQL_ENV_MYSQL_ROOT_PASSWORD"'

shell> docker exec -ti db /bin/bash
```





#### :books: 參考網站：
- [mysql](https://hub.docker.com/_/mysql/)
- https://docs.docker.com/engine/reference/commandline/run/