
```js
var crypto = require('crypto')
var buf = crypto.randomBytes(32);
// var randomstring = buf.toString('hex').substr(0, 8); // → 3f549018
var randomstring = buf.toString('base64').substr(0, 8); // → idWxZoFX
console.log(randomstring);
```

### :books: 參考網站：

- [crypto](https://nodejs.org/api/crypto.html)
- [substr](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/substr)