![](https://hub.docker.com/public/images/official/php.png)

```console
shell> docker run --name php \
 --restart=always \
 --link db:mysql \
 -v /etc/localtime:/etc/localtime:ro \
 -v /docker/nginx/content:/var/www/html:ro \
 -d php:7.1-apache
 
shell> docker exec -ti php docker-php-ext-install mysqli  

shell> docker exec -ti php /bin/bash

shell> docker run -it --name phpfpm -v /path/to/app:/app bitnami/php-fpm
```
```
bcmath bz2 calendar ctype curl dba dom enchant exif fileinfo filter ftp gd gettext gmp hash iconv imap interbase intl json ldap mbstring mcrypt mysqli oci8 odbc opcache pcntl pdo pdo_dblib pdo_firebird pdo_mysql pdo_oci pdo_odbc pdo_pgsql pdo_sqlite pgsql phar posix pspell readline recode reflection session shmop simplexml snmp soap sockets spl standard sysvmsg sysvsem sysvshm tidy tokenizer wddx xml xmlreader xmlrpc xmlwriter xsl zip
```

`phpinfo.php`
```php
<?php
phpinfo();
?>
```

`index.php`
```php
<?php
$link = mysqli_connect($_ENV['MYSQL_PORT_3306_TCP_ADDR'], "root", $_ENV['MYSQL_ENV_MYSQL_ROOT_PASSWORD']);

if (!$link) {
    echo "Error: Unable to connect to MySQL." . PHP_EOL;
    echo "Debugging errno: " . mysqli_connect_errno() . PHP_EOL;
    echo "Debugging error: " . mysqli_connect_error() . PHP_EOL;
    exit;
}

echo "Success: A proper connection to MySQL was made! The my_db database is great." . PHP_EOL;
echo "Host information: " . mysqli_get_host_info($link) . PHP_EOL;

mysqli_close($link);
?>
```

```
docker network create app-tier --driver bridge
docker run -it --name phpfpm \
  --network app-tier
  -v /path/to/app:/app \
  bitnami/php-fpm
```


#### :books: 參考網站：
- [php](https://hub.docker.com/_/php/)
- https://docs.docker.com/engine/reference/commandline/run/
- https://hub.docker.com/r/bitnami/php-fpm/
- http://php.net/manual/en/function.mysqli-connect.php
- http://php.net/manual/en/function.phpinfo.php
- http://php.net/manual/en/install.unix.nginx.php
