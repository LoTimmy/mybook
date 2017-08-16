![](https://hub.docker.com/public/images/official/nginx.png)

```
shell> mkdir -p /docker/nginx/content
shell> mkdir -p /docker/nginx/custom
shell> docker pull nginx

shell> docker run --name web -d nginx
shell> docker cp web:/etc/nginx/nginx.conf /docker/nginx/custom/nginx.conf
shell> docker rm -f web

shell> docker run --name web -p 80:80 --restart=always \
-v /etc/localtime:/etc/localtime:ro \
-v /docker/nginx/content:/usr/share/nginx/html:ro \
-v /docker/nginx/custom/nginx.conf:/etc/nginx/nginx.conf:ro \
-d nginx

shell> docker run --name web -p 80:80 --restart=always \
 --link phpfpm:phpfpm \
-v /etc/localtime:/etc/localtime:ro \
-v /docker/nginx/content:/usr/share/nginx/html:ro \
-v /docker/nginx/custom/nginx.conf:/etc/nginx/nginx.conf:ro \
-d nginx

shell> curl -I http://127.0.0.1/

shell> docker logs <container_id>

shell> docker exec -ti web /bin/bash

shell> docker rm web
```

`Dockerfile`
```
FROM nginx
COPY nginx.conf /etc/nginx/nginx.conf

VOLUME ["/usr/share/nginx/html"]
```

`/var/lib/docker/volumes`

```
shell> docker build -t docker-nginx .
shell> docker run --name web -P -d docker-nginx
```


`index.html`
```html
<!DOCTYPE html>
<html>
  <head>
    <title>Hello World!</title>
  </head>
  <body>
    <h1>Hello World!</h1>
  </body>
</html>
```

#### :books: 參考網站：
- [nginx](https://hub.docker.com/_/nginx/)
- [build](https://docs.docker.com/engine/reference/commandline/build/)
- [build](https://docs.docker.com/mac/step_four/)
- https://docs.docker.com/engine/reference/commandline/run/
