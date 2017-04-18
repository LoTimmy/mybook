![](https://assets-cdn.github.com/images/modules/site/node_logo.png?sn?sn)

### 安裝 {#installing}

```console
shell> brew install node
shell> apt-get install nodejs
```

```console
shell> brew install nvm
```

```console
shell> curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.32.1/install.sh | bash
shell> wget -qO- https://raw.githubusercontent.com/creationix/nvm/v0.32.1/install.sh | bash
shell> echo "source ~/.nvm/nvm.sh" >> .bashrc
```

```console
shell> nvm ls-remote
shell> nvm ls-remote --lts

shell> nvm install --lts
shell> nvm install --lts=argon
shell> nvm install --lts=boron
shell> nvm install v0.12.0
shell> nvm install v4.2.2
shell> nvm install v6.1.0

shell> nvm uninstall v4.2.2
shell> nvm uninstall v6.1.0

shell> nvm use --lts
shell> nvm use --lts=argon
shell> nvm use --lts=boron

shell> nvm ls
shell> nvm alias default 0.12.0
shell> nvm alias default 4.2.2
shell> nvm alias default lts/argon
shell> nvm alias default lts/boron
```

```console
shell> nvm install v6.10.1 --reinstall-packages-from=v6.10.0
shell> nvm uninstall v6.10.0

shell> nvm install v7.7.4

shell> nvm install 6 --reinstall-packages-from=5
shell> nvm install v4.2 --reinstall-packages-from=iojs
```

#### :books: 參考網站：
- [nvm](https://github.com/creationix/nvm)


### Hello world 範例 {#hello-world}

建立名為 hello.js 的檔案，並新增下列程式碼：

```js
console.log('Hello World!');
```

使用下列指令來執行應用程式：

```
shell> node hello.js
```

### 變數 (Variable) {#var}

```js
var a;
var a = 1;
var a = 0, b = 0;

var u = undefined;
var mytext = 'Hello World!';
var mynumber = 99;
var myboolean = true, myFalse = false;
var myFunc = function() {};
var text = null;
var myObj = {}, myobject = { nickname: 'Jack', "registration_date": new Date(1995, 11, 25), "privileged_user": true };
var myarray = [], someArray = [ 1, 2, 3 ];
```

```js
var mynumber = 99;
console.log(`my favorite number is: ${mynumber}`);
```

```js
// define MY_FAV as a constant and give it the value 7
const MY_FAV = 7;

MY_FAV = 20;

// will print 7
console.log("my favorite number is: " + MY_FAV);

var MY_FAV = 20; 

// MY_FAV is still 7
console.log("my favorite number is " + MY_FAV);
```

``` .js
'use strict';

function varTest() {
  var x = 31;
  if (true) {
    var x = 71;  // same variable!
    console.log(x);  // 71
  }
  console.log(x);  // 71
}

function letTest() {
  let x = 31;
  if (true) {
    let x = 71;  // different variable
    console.log(x);  // 71
  }
  console.log(x);  // 31
}
```

#### :books: 參考網站：
- [let](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let)
- [const](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/const)



### Events {#events}

```js
var EventEmitter = require('events').EventEmitter;
var myEmitter = new EventEmitter(); 

myEmitter.on('event', function () {
  console.log('an event occurred!'); 
});

myEmitter.emit('event');
```

```js
const EventEmitter = require('events');
class MyEmitter extends EventEmitter {}
const myEmitter = new MyEmitter();

myEmitter.on('event', () => {
  console.log('an event occurred!');
});

setTimeout(function() {
  myEmitter.emit('event');
}, 1000);
```

```js
var EventEmitter = require('events').EventEmitter;
var myEmitter = new EventEmitter();

myEmitter.on('hello', function (arg1, arg2) {
    console.log(arg1 + ' ' + arg2);
});

myEmitter.emit('hello', 'Hello', 'World');
```

```js
var EventEmitter = require('events').EventEmitter;
var myEmitter = new EventEmitter();

myEmitter.on('sayHello', function(name) {
  console.log("Hello" + " " + name);
});

myEmitter.emit('sayHello', 'Eric');
```
---

### Arrow functions {#Arrow_functions}

```js
var a = [
  'Hydrogen',
  'Helium',
  'Lithium',
  'Beryllium'
];

var a2 = a.map(function(s) { return s.length; });
console.log(a2); // logs [8, 6, 7, 9]

var a3 = a.map(s => s.length);
console.log(a3); // logs [8, 6, 7, 9]
```

---

```js
var myObj = {
  nickname: "Jack",
  registration_date: new Date(1995, 11, 25)
}

var {
  nickname,
  registration_date
} = myObj;

console.log(nickname);
console.log(registration_date);
```
```js
var nickname = 'Jack';
var registration_date = new Date(1995, 11, 25);
var myObj = {nickname, registration_date};

console.log(myObj);
```

---

#### :books: 參考網站：
- [events](https://nodejs.org/api/events.html)