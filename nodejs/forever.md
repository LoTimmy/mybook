### 安裝 {#installing}

```console
shell> npm install forever -g
```

```console
shell> forever start app.js
```

```
.
├── forever
│   └── development.json
└── index.js
```

```json

// forever/development.json
{
    "uid": "app",
    "append": true,
    "watch": true,
    "script": "index.js",
    "sourceDir": "/home/myuser/app"
}
```


```console
shell> forever start ./forever/development.json
```

### :books: 參考網站：
- [forever](https://www.npmjs.com/package/forever)