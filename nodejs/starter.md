<img src="http://i.imgur.com/yrb3Srt.png" width="100">

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

建立名為 `hello.js` 的檔案，並新增下列程式碼：

```js
console.log('Hello World!');
```

使用下列指令來執行應用程式：

```
shell> node hello.js
```

### `變數` (`Variable`) {#var}

> `JavaScript` 有兩個範圍：**全域**和**區域**。在函式定義之外宣告的變數就是**全域變數**，其值可在整個程式中存取和修改。
> 宣告變數。在函式定義內宣告的變數則是**區域變數**。
> 可以宣告變數而不使用 `var` 關鍵字，並為變數指派值。 這稱為「`隱含宣告`」，但不建議使用。 隱含宣告會提供全域範圍給變數。
> 如果未初始化 `var` 中的變數，系統會自動指派 `JavaScript` 值 `undefined` 給此變數。
> 下列程式碼是示範如何宣告整數變數、指派其值，然後再為其指派新值的簡單範例。

```js
var a;
var a = 1;
var a = 0, b = 0;
var bigNumber = 1e100;
var mynumber = 99;

var u = undefined;

var myString = new String('Hello');
var mytext = 'Hello World!';

var b = new Boolean(false);
var x = new Boolean(false);
var x = false;
var myFalse = new Boolean(false);
var myboolean = true, myFalse = false;
var btrue = new Boolean(true);
var bfalse = new Boolean(false);
var F = new Boolean();
var T = new Boolean(true);
var F = new Boolean(0);
var T = new Boolean(1);

function doSomething() {}
var f = function() {};
f();
var myFunc = function() {};


var text = null;

var o = {};
var myObj = {}, myobject = { nickname: 'Jack', "registration_date": new Date(1995, 11, 25), "privileged_user": true };
var object = {
  someMethod: function() {}
};

var myarray = [], someArray = [ 1, 2, 3 ];

var greeting = "Hello, World!";

var index;  
var name = "Thomas Jefferson";  
var answer = 42, counter, numpages = 10;  
var myarray = new Array();
```

```js
var mynumber = 99;
console.log(`my favorite number is: ${mynumber}`);
```

### `常數` (`Constant`) {#const}

> 常數會使用 `const` 宣告
> 在這個範例中，常數 `MY_FAV` 永遠會是 7

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

```js
const months = 12, weeks = 52, days = 365;
const daysPerWeek = days / weeks;
const daysPerMonth = days / months;

const speedLimit = 55;
const pi = 3.14159265358979323846264338327950;
const Pi = 3.14159;
const SpeedOfLight = 300000; // km per sec.
```

`範例`

```js
var radius = 5.3; // Radius 半徑
const pi = 3.14159265358979323846264338327950; // PI 圓周率
var area = pi * (radius * radius); // Area 面積
```

> 宣告區塊範圍變數。
> 「`區域變數`」(`Local Variable`)
> 使用 `let` 來宣告變數，其範圍限於宣告所在的區塊。

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
- [let 陳述式 (JavaScript)](https://msdn.microsoft.com/zh-tw/library/dn263046(v=vs.94).aspx)
- [const](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/const)
- https://docs.microsoft.com/en-us/scripting/javascript/advanced/variable-scope-javascript


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
