<img src="http://i.imgur.com/D8x5kJw.png" alt="" width=58 height=58>

- `JavaScript`是一種`函數語言`(`Functional Language`)，可用來控制動態物件，也提供開發者熟悉的語法，這反映出它的功能特殊性，從物件角度來看，其實`JavaScript`語言比`Java`、`C++`或`C#`語言更優秀。
- **網頁開發框架`React`**。`React`幫助開發者專注在產品功能，而不用為了開發框架煩惱。**`React`框架的概念是將一個應用程式，拆解為數個獨立的元件，這些元件不會互相影響，因此開發者不需要因為更改了單一元件的功能，而擔心整個系統受影響。**另外，`React`最強大的是抽象化`DOM`(`Document Object Model`，`文件物件模型`)與`API`以簡化開發模型。
- **`JSX`是`Javascript`的類`XML`語法擴充，使用`JSX`編譯器能把類`XML`語法轉換成`Javascript`。**
- `React`是`Facebook`在2013年中開源的一個前端Web開發框架，**主要在於幫助開發者提高Web應用效能**。以往在開發前端Web網頁、App程式時，經常會因為不正確的操作導致程式出錯，甚至造成執行效能降低。而`React`則是設計了虛擬的`DOM`架構，稱為`VDOM`，來解決這個不當操作產生的問題。這是記憶體內的一個小物件，網頁畫面有任何改變時，會先在記憶體內繪製完畫面後，才顯示給使用者，以降低不當操作影響效能的情形。目前`Facebook`的網頁元件多數都是以`React`開發。`React`另一個好處是學習容易，熟悉`JavaScrip`的開發者，只要花一天時間就能學會，而且框架的架構思維模式簡單，開發者不用像以往得經過複雜處理步驟，出錯機率又高，並且已有許多企業實例驗證可行。
- 以往開發者一遇到程式有問題直覺反應就是重新載入頁面，以獲得保證正確的可用頁面。而在`React`世界的理念上，則是每一次只要資料發生改變，就會將頁面立即重繪，來得到一個乾淨的頁面。
- `React`這套工具的出現，不只徹底改變了既有的網頁開發作法，甚至也轉變開發架構策略，從以前「`一次編寫，到處運行`（`Write Once, Run Anywhere`）」到現在「`一次學習，到處編寫`（`Learn Once, Write Anywhere`）」策略。

---
```html
<script src="https://fb.me/react-0.14.3.js"></script>
<script src="https://fb.me/react-dom-0.14.3.js"></script>

<script src="https://fb.me/react-0.14.3.min.js"></script>
<script src="https://fb.me/react-dom-0.14.3.min.js"></script>
```
---


```html
<!doctype html>
<html>
  <head>
    <meta charset="utf-8">	
    <title>Hello React!</title>
     <script src="https://cdnjs.cloudflare.com/ajax/libs/react/0.13.3/react.min.js"></script>
     <script src="https://cdnjs.cloudflare.com/ajax/libs/react/0.13.3/JSXTransformer.js"></script>
  </head>
  <body>
    <div id="example"></div>

    <script type="text/jsx">
      React.render(
        <h1>Hello, world!</h1>,
        document.getElementById('example')
      );
    </script>
  </body>
</html>
```

```html
<!-- index.html -->
<!doctype html>
<html>
  <head>
    <meta charset="utf-8">	
    <title>Hello React</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/react/0.13.3/react.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/react/0.13.3/JSXTransformer.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/2.1.1/jquery.min.js"></script>
  </head>
  <body>
    <div id="content"></div>
    <script type="text/jsx">
      // Your code here
    </script>
  </body>
</html>
```

```jsx
var MyTextfield = React.createClass({
  render: function() {
    return <input type='text'/>;
  }
});

var MyButton = React.createClass({
  render: function() {
    return <button>{this.props.textlabel}</button>;
  }
});

React.render(<div>
  <MyTextfield/>
  <MyButton textlabel='OK'/>
</div>, document.getElementById('container'));
```


---

```console
shell> bower install react --allow-root
```

```html
<!doctype html>
<html>
  <head>
    <meta charset="utf-8">	
    <title>Hello React!</title>
    <script src="build/react.js"></script>
    <script src="build/react-dom.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/babel-core/5.8.23/browser.min.js"></script>

  </head>
  <body>
    <div id="example"></div>
    <script type="text/babel">
      ReactDOM.render(
        <h1>Hello, world!</h1>,
        document.getElementById('example')
      );
    </script>
  </body>
</html>
```


```html
<!doctype html>
<html>
  <head>
    <meta charset="utf-8">	
    <title>Hello React!</title>
    <script src="build/react.js"></script>
    <script src="build/react-dom.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/babel-core/5.8.23/browser.min.js"></script>
  </head>
  <body>
    <div id="content"></div>
    <script type="text/babel">
    var CommentBox = React.createClass({
      render: function() {
        return (
          <div className="commentBox">
            Hello, world! I am a CommentBox.
          </div>
        );
      }
    });
    ReactDOM.render(
      <CommentBox />,
      document.getElementById('content')
    );
    </script>

  </body>
</html>
```

```console
shell> npm install --global babel
shell> babel script.js --out-file script-compiled.js
shell> babel script.js --watch --out-file script-compiled.js
shell> babel src --watch --out-dir build
 ```

```html
<!doctype html>
<html>
  <head>
    <meta charset="utf-8">	
    <title>Hello React!</title>
    <script src="build/react.js"></script>
    <script src="build/react-dom.js"></script>
    <!-- No need for Babel! -->
  </head>
  <body>
    <div id="example"></div>
    <script src="build/helloworld.js"></script>
  </body>
</html>
```


#### :books: 參考網站：
- [babel](https://babeljs.io/docs/usage/cli/)

---

```jsx
var HelloWorld = React.createClass({
  render: function() {
    return <h1>Hello, world!</h1> ;
  }  
});

ReactDOM.render( <HelloWorld />, document.getElementById('example'));
```

```jsx
var Hello = React.createClass({
  render: function() {
    return <h1>Hello, {this.props.name}!</h1> ;
  }  
});

ReactDOM.render(<Hello name="羅得勝" />, document.getElementById('example'));
```

---

**main.js**

```js
var React = require('react');
var ReactDOM = require('react-dom');

ReactDOM.render(
  <h1>Hello, world!</h1>,
  document.getElementById('example')
);
```

```console
shell> npm install --save react react-dom
shell> npm install -g browserify
shell> npm install babelify
shell> npm install reactify
shell> browserify -t reactify main.js -o build/helloworld.js
```

#### :books: 參考網站：
- [reactify](https://www.npmjs.com/package/reactify)
- [babelify](https://www.npmjs.com/package/babelify)

---

helloworld.js
```js
var React = require('react');

module.exports = React.createClass({
  render: function() {
    return <h1>Hello, world!</h1> ;
  }  
});
```

main.js
```js
var React = require('react');
var ReactDOM = require('react-dom');
var HelloWorld = require('./helloworld.js');

ReactDOM.render( <HelloWorld />, document.getElementById('example'));
```

```console
shell> browserify -t reactify main.js -o build/helloworld.js
```

---

```jsx
var MyComponent = React.createClass({
  handleClick: function() {
   // window.alert("Hello world!");
   var input = this.refs.myInput;
   var inputValue = input.value;
   window.alert(inputValue);
  },

  render: function() {
    return (
      <div>
        <input ref="myInput" />
        <button type="submit" onClick={this.handleClick}>Submit</button>
      </div>
    );
  }
});
```

---

**test.jsx**
```jsx
var HelloMessage = React.createClass({
  render: function() {
    return <div>Hello {this.props.name}</div>;
  }
});

ReactDOM.render(<HelloMessage name="John" />, mountNode);
```

```console
shell> babel test.jsx
```

---

#### :books: 參考網站：

- [企業應用Web 2.0必備的網頁技術](http://www.ithome.com.tw/node/44234)
- [react](http://facebook.github.io/react/)
- [getting-started](http://facebook.github.io/react/docs/getting-started.html)
- [tutorial](https://facebook.github.io/react/docs/tutorial.html)
- [react](https://facebook.github.io/react/downloads.html)
