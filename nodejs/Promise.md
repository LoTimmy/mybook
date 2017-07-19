```
new Promise( /* executor */ function(resolve, reject) { ... } );
```

```js
var x = false;

var myFirstPromise = new Promise(function (resolve, reject) {
  if (x) {
    resolve('Success!');
  } else {
    reject(Error('oh, no!'));
  }
});

var myFunc = function() {
  myFirstPromise.then(function(value){
    console.log(value);
  }
  .catch(function(e) {
    console.log(e);
  }
};

myFunc();

```

