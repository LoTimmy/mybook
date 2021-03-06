```js
new Promise(function(resolve, reject) {});
```


- `pending`: initial state, neither `fulfilled` nor `rejected`.
- `fulfilled`: meaning that the operation completed successfully.
- `rejected`: meaning that the operation failed.

```js
const myFirstPromise = new Promise((resolve, reject) => {
  // do something asynchronous which eventually calls either:
  //
  //   resolve(someValue); // fulfilled
  // or
  //   reject("failure reason"); // rejected
});
```

```js
let myFirstPromise = new Promise((resolve, reject) => {
  setTimeout(function(){
    resolve("Success!");
  }, 250);
});

myFirstPromise.then((successMessage) => {
  console.log("Yay! " + successMessage);
});
```

---

```js
// var b = true;
var b = false;

var p1 = new Promise(function (resolve, reject) {
  if (b) {
    resolve('Success!');
  } else {
    reject(Error('oh, no!'));
  }
});

var myFunc = function() {
  p1.then(function(value){
    console.log(value);
  })
  .catch(function(e) {
    console.log(e);
  })
};

myFunc();
```

```
var doSomething = function(value) {
  return new Promise(function (resolve, reject) {
    resolve('Success!');
  });
};
```

```
var doSomething = function(value) {
  return Promise.resolve('Success!');
};
```



- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/all
