<img src="https://hapijs.com/public/img/logo.svg" width="200">


### 安裝 {#installing}

```console
shell> npm install hapi
shell> npm install hapi --save
```

---

### Creating a server

建立名為 `server.js` 的檔案，並新增下列程式碼：

```js
'use strict';

const Hapi = require('hapi');

const server = new Hapi.Server();
server.connection({
  port: 3000,
  host: 'localhost'
});

server.start((err) => {
  if (err) {
    throw err;
  }
  console.log(`Server running at: ${server.info.uri}`);
});
```

使用下列指令來執行應用程式：

```console
shell> node server.js
```

應用程式會啟動伺服器，並在埠 3000 接聽連線。
然後在瀏覽器中載入 `http://localhost:3000/`，以查看輸出。

---

### 基本路由 {#basic-routing}

> 路由是指判斷應用程式如何回應用戶端對特定端點的要求，而這個特定端點是一個 URI（或路徑）與一個特定的 HTTP 要求方法（GET、POST 等）。
> 每一個路由可以有一或多個處理程式函數，當路由相符時，就會執行這些函數。

path 是伺服器上的路徑。
method 是 HTTP 要求方法。
handler 是當路由相符時要執行的函數。

下列範例說明如何定義簡單的路由。

首頁中以 Hello World! 回應。

建立名為 `server.js` 的檔案，並新增下列程式碼：

```js
'use strict';

const Hapi = require('hapi');

const server = new Hapi.Server();
server.connection({
  port: 3000,
  host: 'localhost'
});

server.route({
  method: 'GET',
  path: '/',
  handler: function(request, reply) {
    reply('Hello World!');
  }
});

server.start((err) => {
  if (err) {
    throw err;
  }
  console.log(`Server running at: ${server.info.uri}`);
});
```

```js
server.route({
  method: 'GET',
  path: '/{name}',
  handler: function(request, reply) {
    reply('Hello, ' + encodeURIComponent(request.params.name) + '!');
  }
});
```

---

### Creating static pages and content

```js
server.register(require('inert'), (err) => {
  if (err) {
    throw err;
  }

  server.route({
    method: 'GET',
    path: '/hello',
    handler: function(request, reply) {
      reply.file('./public/hello.html');
    }
  });
});
```

---

### Using plugins

```console
shell> npm install --save good
shell> npm install --save good-console
shell> npm install --save good-squeeze
```

`server.js`

```js
'use strict';

const Hapi = require('hapi');
const Good = require('good');

const server = new Hapi.Server();
server.connection({ port: 3000, host: 'localhost' });

server.route({
  method: 'GET',
  path: '/',
  handler: function(request, reply) {
    reply('Hello, world!');
  }
});

server.route({
  method: 'GET',
  path: '/{name}',
  handler: function(request, reply) {
    reply('Hello, ' + encodeURIComponent(request.params.name) + '!');
  }
});

server.register({
  register: Good,
  options: {
    reporters: {
      console: [{
        module: 'good-squeeze',
        name: 'Squeeze',
        args: [{
          response: '*',
          log: '*'
        }]
      }, {
        module: 'good-console'
      }, 'stdout']
    }
  }
}, (err) => {

  if (err) {
    throw err; // something bad happened loading the plugin
  }

  server.start((err) => {

    if (err) {
      throw err;
    }
    server.log('info', 'Server running at: ' + server.info.uri);
  });
});

```

```
140625/143008.751, [log,info], data: Server running at: http://localhost:3000

140625/143205.774, [response], http://localhost:3000: get / {} 200 (10ms)
```


---

```console
shell> npm install hapi-swagger --save
shell> npm install inert --save
shell> npm install vision --save 
```

```js
const Hapi = require('hapi');
const Inert = require('inert');
const Vision = require('vision');
const HapiSwagger = require('hapi-swagger');
const Joi = require('joi');

const server = new Hapi.Server();
server.connection({
  host: 'localhost',
  port: 3000
});

const options = {
  info: {
    'title': 'Test API Documentation',
    'version': '0.0.2',
  }
};

server.route({
  method: 'GET',
  path: '/{name}',
  config: {
    tags: ['api'],
    validate: {
      params: {
        name: Joi.string().required()
      },
    },
    handler: function(request, reply) {
      reply('Hello, ' + encodeURIComponent(request.params.name) + '!');
    }
  }
});

server.route({
  method: 'POST',
  path: '/items',
  config: {
    tags: ['api'],
    handler: (request, reply) => {
      reply('OK');
    },
    validate: {
      payload: Joi.object({
        a: Joi.number(),
        b: Joi.number()
      })
    }
  }
});

server.route({
  method: 'GET',
  path: '/items/{pageNo}',
  config: {
    handler: (request, reply) => {
      reply('OK');
    },
    tags: ['api'],
    validate: {
      params: {
        pageNo: Joi.number()
      },
      query: {
        search: Joi.string()
      },
      headers: Joi.object({
        'authorization': Joi.string().required()
      }).unknown()
    }
  }
});

server.register([
  Inert,
  Vision, {
    'register': HapiSwagger,
    'options': options
  }
], (err) => {
  server.start((err) => {
    if (err) {
      console.log(err);
    } else {
      console.log('Server running at:', server.info.uri);
    }
  });
});
```

`http://localhost:3000/documentation`

<img src="https://raw.github.com/hapijs/joi/master/images/joi.png" width="200">


#### :books: 參考網站：
- [hapi-swagger](https://github.com/glennjones/hapi-swagger)
- [usageguide](https://github.com/glennjones/hapi-swagger/blob/master/usageguide.md)

---

- `Tutorials` `[tjuˋtorɪəl]` `教學課程` `tu・to・ri・als`

#### :books: 參考網站：
- [hapijs](https://hapijs.com/)
- [tutorials](https://hapijs.com/tutorials)
- [api](https://hapijs.com/api)

