
<img src="https://pbs.twimg.com/profile_images/788014136575668224/lxEKmMnB_400x400.jpg" width="100">

<img src="http://i.imgur.com/yqRg1pl.png" width="100">

---

<a name="getstarted"></a>
> **`jQuery` 是一个跨浏览器的免费开源 `JavaScript` 库**。
> 流行的 `jQuery` `JavaScript` 库有一个简洁便携的 `JavaScript` `API` 集合，用于快速的 `web` 开发，该库是经 `MIT` 和 `GPL` 许可的免费库。
> `jQuery` 库是轻量级的（缩小/Gzip 压缩后仅 25KB）、`CSS3` 兼容且跨浏览器的。它提供一个丰富的 `API` 集合，包括 `HTML` `文档对象模型`（`DOM`）遍历和操作，可使用事件，且允许通过使用 `Asynchronous JavaScript` 和 `XML` (`Ajax`) 请求 `API` 进行服务器通信。除此之外，它也提供了网页动画和图像效果，以及一个功能强大的插件架构。

> 其核心设计思想是“`写更少的代码，做更多的事情`”(`Write Less Do More`)。

> `jQuery` 提供了一套易于使用的 `API`。这些 `API` 极大地简化了客户端(浏览器)编程过程中的许多方面，包括：
- `HTML` `DOM` 的遍历与操作
- 浏览器事件处理
- `AJAX`（`Asynchronous JavaScript And XML`）编程
- 特效（如动画效果）

> 在直接使用 `JavaScropt`+`DHTML` 的传统客户端编程方式下，开发人员不得不编写冗长的代码。并且，为了使这些代码能够兼容不同的浏览器，我们还得编写额外的代码来处理这些跨浏览器问题。`jQuery` 的设计目标正是在于简化客户端编程。让我们能够编写简练的代码，节约开发时间，而这些代码却一样可以功能强大，并且兼容多种浏览器。

> **`jQuery` 网站上提供了两种方式的发布文件。一种是内容经过压缩的文件；另一种是原始文件。前者文件中不包含代码注释以及代码运行过程中不需要的空白字符，它适合于生产环境(正式使用的环境)中使用，可以减少文件加载所需时间。后者文件中包含详细的代码注释，适合于开发和测试环境中使用。**

> **`jQuery` 语法的设计思想是"选择元素，对其操作"。这和 `CSS` 规则的语法非常类似。**

`jQuery` 的语法其实正是模仿了 `CSS` 规则的语法。其语法如下：

```js
$(selector).action(actionParameter);
```

这是个链式语法。因此，上述的语法等效于：

```js
var objTargetElements;//要施加操作的目标元素
objTargetElements=$(selector);//指定目标元素
//调用 objTargetElements 的相关方法，对目标元素进行操作
objTargetElements.action(actionParameter);
```

> $ ：美元符是 `jQuery` 核心函数 `jQuery` 的一个别名。当然，在 `JavaScript` 中“$”是一个合法的函数名。 Selector 参数指定了一个 `jQuery` 选择器。`jQuery` 选择器类似于 `CSS` 中的选择器，它告诉 `jQuery` 我们准备对哪些元素进行操作(action)。并且，`CSS` 中的各种选择器 `jQuery` 中都有等同的选择器。

> action ：该方法指定了要对 selector 所指定的元素进行什么具体操作。actionParameter 参数是个可选参数，是根据具体所指定的方法来定的，它会随具体方法的变化而变化。


##### 从本地站点引用 `jQuery`
```html
<html>
  <head>
    <title>使用 jQuery</title>
    <script src="../js/lib/jQuery/1.9.1/jQuery.js"></script>
  </head>

  <body>
  </body>
</html>
```

##### 从 `CDN` 引用 `jQuery`
```html
<html>
  <head>
    <title>使用 jQuery</title>
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.1.1/jquery.min.js"></script>
  </head>

  <body>
  </body>
</html>
```

##### `Hello World`
```html
<html>
  <head>
    <meta http-equiv="content-type" content="text/html;charset=utf-8">
    <script src="../js/lib/jQuery/1.9.1/jQuery.js"></script>
    <script>
      function initPage() {
        //jQuery 代码：调用 jQuery 的核心函数－－－$函数
        $("#message").html("Hello World, it is now:" + new Date().toLocaleString());
      }
    </script>
  </head>

  <body onload="initPage()">
    <span id="message"></span>
  </body>
</html>
```

> initPage 这个函数会在页面加载完毕后被调用。而该函数在执行后会在 ID 为 message 的 HTML 结点内添加表示客户端当前时间的字符串。

![](http://www.ibm.com/developerworks/cn/web/1311_huangwh_jqueryhandson/image007.jpg)

```html
<a href="https://www.ibm.com/developerworks/cn/" target="_blank">IBM developerWorks 中文站</a><br/>
<a href="https://www.ibm.com/developerworks" target="_blank">IBM developerWorks</a><br/>
<a href="/" target="_blank">首页</a><br/>
```

```js
//用基于元素名称的选择器去匹配页面中的所有链接元素
$("a").each(function(index, ele) { //匿名函数作为 each 方法的参数，供其调用
  console.log("链接" + index + ":" + ele.href); //往控制台中打印链接 URL
});
```

```js
$("#tip").css("font-weight","bold");
```

---

```css
a {
  font-size: 25px;
}
```


```js
$("a").each(function() { //选择器表达式是"a"
  $(this).css("fontSize", "25px");
});
```

```js
/*
选择所有类为 amount 的元素
each 方法会针对选择器所匹配的每个元素
调用该方法的参数中所指定的函数。并将该
元素作为函数调用的第二个实际参数。
*/
$(".amount").each(function(i, ele) {
  //设置元素的值为其当前值加上货币符号前缀
  $(ele).val('￥' + $(ele).val());
});
```

```css
input[type="text"] {
  background-color: yellow;
}
```

```js
$("input[type=text]").css('background-color', 'yellow');
```
---

```js
$(document).ready(initPage); //页面加载完毕后，jQuery 会回调 initPage
```

```js
$(function() { //该函数在页面加载完毕会被 jQuery 调用
  //事件处理代码
});
```
---

```js
//当 ID 为 btnDetails 的按钮被单击时，下面的匿名函数会被 jQuery 调用
$("#btnDetails").bind("click", function() {
  $("#divDetails").toggle(); //显示或者隐藏 ID 为 divDetails 的元素
});
```

> `bind` 方法的语法是：
`event`：要处理的事件的名称。该名称不需要加前缀 on。
`handler`：事件监听器，即对浏览器事件进行处理的函数。这通常是一个匿名函数。**在 `event` 参数所表示的事件被触发后，`jQuery` 会调用这个函数（即回调），并向该函数传入一个 `jQuery` 自定义的事件对象**。该事件对象是 `jQuery` 根据原始的浏览器事件对象创建的。`jQuery` 这么做是通过一个"中立"的事件对象来规避不同的浏览器所提供的同一个事件的事件对象的属性不同的问题。这使得我们可以用同样的代码处理事件，而不必关心不同浏览器所提供的原始事件对象的差异。
`data` ：表示需要在事件触发后传递给事件监听器的额外数据。它是作为 `jQuery` 事件对象的 `data` 属性传递给事件监听器的。

```js
$("#txtVerifyCode").bind("keypress", function(evt) {
  var keyCode = evt.which; //从事件对象中获取当前按键的编码值
  var char = String.fromCharCode(keyCode); //将按键的编码转换为相应的字符
  if (!/\d/.test(char)) { //当前输入的字符不是数字字符
    //调用事件对象的 preventDefault 方法，取消事件的默认行为，此处即取消输入。
    evt.preventDefault();
  }
});
```
---

```js
function showTip(msg) {
  $('#divTips').html(msg); //显示具体的提示内容
}
```

```js
function showTipHandler(evt) {
  var data = evt.data; //获取额外参数
  /*额外参数是一个我们根据需要的自定义对象。这里，我们假设这个对象有个 msg 属性。
    它表示希望要显示的提示信息。
  */
  var msg = data.msg;
  showTip(msg);
}

```

```js
$('#tip1').bind('click', {
  msg: '中文提示'
}, showTipHandler);
$('#tip2').bind('click', {
  msg: 'English tip'
}, showTipHandler);
```

#### :books: 參考網站：
- [jQuery 实验教程](http://www.ibm.com/developerworks/cn/web/1311_huangwh_jqueryhandson/)
- [使用 jQuery 进行基于 DOM 的数据存储和检索 ](http://www.ibm.com/developerworks/cn/web/wa-domjquery/)
- [.mouseout()](https://api.jquery.com/mouseout/)
- [.css()](https://api.jquery.com/css/)
- https://msdn.microsoft.com/en-us/library/bb299886.aspx

---

```js
$("p").addClass("myClass yourClass");
```

- [.addClass()](https://api.jquery.com/addclass/)

---

#### :books: 參考網站：
- [lazyload](#lazyload)

---

```js
jQuery(document).ready(function() {});

$(document).ready(function() {});

$(function() {});
```

#### :books: 參考網站：
- [ready](http://api.jquery.com/ready/)

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>jQuery demo</title>
  </head>

  <body>
    <!--[if lt IE 9]>
    <script src="jquery-1.9.0.js"></script>
  <![endif]-->
    <!--[if gte IE 9]>
    <script src="jquery-2.0.0.js"></script>
  <!--<![endif]-->

    <script src="https://code.jquery.com/jquery-1.10.2.js"></script>
    <script>
      $(document).ready(function() {
        $("p").text("The DOM is now loaded and can be manipulated.");
      });
    </script>
  </body>
</html>

```

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>load demo</title>
    <style>
      body {
        font-size: 12px;
        font-family: Arial;
      }
    </style>
    <script src="https://code.jquery.com/jquery-1.10.2.js"></script>
  </head>

  <body>
    <b>Successful Response (should be blank):</b>
    <div id="success"></div><b>Error Response:</b>
    <div id="error"></div>
    <script>
      $("#success").load("/not-here.php", function(response, status, xhr) {
        if (status == "error") {
          var msg = "Sorry but there was an error: ";
          $("#error").html(msg + xhr.status + " " + xhr.statusText);
        }
      });
    </script>
  </body>
</html>
```

#### :books: 參考網站：
- [load](http://api.jquery.com/load/)

---

`ajax/test.html`

```html
<ul class="level-1">
  <li class="item-i">I</li>
  <li class="item-ii">II
    <ul class="level-2">
      <li class="item-a">A</li>
      <li class="item-b">B
        <ul class="level-3">
          <li class="item-1">1</li>
          <li class="item-2">2</li>
          <li class="item-3">3</li>
        </ul>
      </li>
      <li class="item-c">C</li>
    </ul>
  </li>
  <li class="item-iii">III</li>
</ul>
```


```js
$.post("ajax/test.html", function(data) {
  $(".result").html(data);
});

$.post("ajax/test.html", function(data) {
  $($.parseHTML(data)).find("li").css("background-color", "red");
});
```

#### :books: 參考網站：
- [post](http://api.jquery.com/jQuery.post/)
- [get](https://api.jquery.com/jquery.get/)
- [parseHTML](http://api.jquery.com/jQuery.parseHTML/)
- [find](http://api.jquery.com/find/)

---

```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>attr demo</title>
    <style>
      p {
        margin: 20px 0 0;
      }
      
      b {
        color: blue;
      }
    </style>
    <script src="https://code.jquery.com/jquery-1.10.2.js"></script>
  </head>

  <body>
    <input id="check1" type="checkbox" checked="checked">
    <label for="check1">Check me</label>
    <p></p>

    <script>
      $("input")
        .change(function() {
          var $input = $(this);
          $("p").html(".attr( 'checked' ): <b>" + $input.attr("checked") + "</b><br>" +
            ".prop( 'checked' ): <b>" + $input.prop("checked") + "</b><br>" +
            ".is( ':checked' ): <b>" + $input.is(":checked") + "</b>");
        })
        .change();
    </script>
  </body>
</html>

```

#### :books: 參考網站：

- [attr](http://api.jquery.com/attr/)

---

<a name="lazyload"></a>

[source code](https://jsfiddle.net/cccgtso7/)


```html
<script src="jquery.js"></script>
<script src="jquery.lazyload.js"></script>

<img class="lazy" data-original="http://placehold.it/640x480" width="640" height="480">

<script>
  $(function() {
    //  $("img.lazy").lazyload();
    $("img.lazy").lazyload({
      effect: "fadeIn"
    });
  });

</script>
```

**Install with Bower**
```console
shell> bower install jquery.lazyload
```

- [jquery_lazyload](https://github.com/tuupola/jquery_lazyload)
- [lazyload](http://www.appelsiini.net/projects/lazyload)
- [lazyload](http://www.appelsiini.net/projects/lazyload/enabled_fadein.html)

---

```js
$("div.demo-container").text("<p>This is a test.</p>");
$("p").text("<b>Some</b> new text.");

$("div.demo-container").html();

$("li").add("p").css("background-color", "red");
$("p").add("span").css("background", "yellow");

$(".inner").append("<p>Test</p>");

$("#target").click(function() {
  alert("Handler for .click() called.");
});

$("p").click(function() {
  var htmlString = $(this).html();
  $(this).text(htmlString);
});

$("div.demo-container")
  .html("<p>All new content. <em>You bet!</em></p>");

$.ajax({
  url: "test.html",
  context: document.body
}).done(function() {
  $(this).addClass("done");
});

$.ajax({
  statusCode: {
    404: function() {
      alert("page not found");
    }
  }
});

$.ajax({
    method: "POST",
    url: "some.php",
    data: {
      name: "John",
      location: "Boston"
    }
  })
  .done(function(msg) {
    alert("Data Saved: " + msg);
  });

$.ajax({
    url: "test.html",
    cache: false
  })
  .done(function(html) {
    $("#results").append(html);
  });

$.getJSON("test.js", function(json) {
  console.log("JSON Data: " + json.users[3].name);
});
```

```js
$( "#result" ).load( "ajax/test.html" );
$( "#result" ).load( "ajax/test.html", function() {
  alert( "Load was performed." );
});

```

```js
$("#result").load("ajax/test.html");
$("#result").load("ajax/test.html", function() {
  alert("Load was performed.");
});
```

---

#### :books: 參考網站：
- [lazyload](http://www.appelsiini.net/projects/lazyload)
- [dummyimage](http://dummyimage.com/)
- [jquery-dateFormat](https://github.com/phstc/jquery-dateFormat)
- [jquery-number](https://github.com/customd/jquery-number)
- [jQuery.formError](https://github.com/GarethElms/jQuery.formError)

---

```html
<!doctype html>
<html lang="en">

  <head>
    <meta charset="utf-8">
    <title>scrollTop demo</title>
    <style>
      pre {
        height: 600px;
      }
    </style>
  </head>

  <body>
    <a href="#" id="header">Header</a>
    <pre></pre> Go to <a href="#header">Header</a>
    <pre></pre> Go to <a href="#header">Header</a>
    <pre></pre> Go to <a href="#header">Header</a>

    <script src="https://code.jquery.com/jquery-1.10.2.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery-easing/1.3/jquery.easing.min.js"></script>
    <script>
      $(function() {
        $('a').click(function() {
          $('html,body').animate({
            scrollTop: $('#header').offset().top
          }, 2000, 'easeOutBounce');

          return false;
        });
      });
    </script>
  </body>
</html>
```

#### :books: 參考網站：

- http://gsgd.co.uk/sandbox/jquery/easing/
- [animate](http://api.jquery.com/animate/)
- [offset](http://api.jquery.com/offset/)
- [fadeout](http://api.jquery.com/fadeout/)

---

```html
<script src="http://ajax.googleapis.com/ajax/libs/jquery/1/jquery.min.js"></script>
<script src="http://malsup.github.com/jquery.cycle2.js"></script>
```

#### :books: 參考網站：
- http://jquery.malsup.com/cycle2/
- http://jquery.malsup.com/cycle2/demo/background.php
- http://jquery.malsup.com/block/

---

[source code](https://jsfiddle.net/wo3oqodm/)

```html
<div id="box1"></div>
```
```css
#box1 {
  width: 60px;
  height: 60px;
  background-color: green;
}
```
```js
$("#box1").click(function() {
  $(this).fadeOut(1000, function() {
    $(this).css("background-color", "blue").fadeIn(1000);
  });
});

```

#### :books: 參考網站：
- [click](http://api.jquery.com/click/)
- [fadeOut](http://api.jquery.com/fadeOut/)
- [css](http://api.jquery.com/css/)
- [fadeIn](http://api.jquery.com/fadeIn/)


---

```html
<script type="application/javascript">
  $(function() {
    $.getJSON("https://api.ipify.org?format=jsonp&callback=?",
      function(json) {
        document.write("My public IP address is: ", json.ip);
      }
    );
  });
</script>
```
#### :books: 參考網站：
- [ipify](https://www.ipify.org/)

---

```js
var a = 1;

function myCallback() {
  if (a == 1) {
    $(this).css("background-image", "url('http://placehold.it/350x150')");
    a = 2;
  } else if (a == 2) {
    $(this).css("background-image", "url('http://placehold.it/350x150')");
    a = 3;
  } else if (a == 3) {
    $(this).css("background-image", "url('http://placehold.it/350x150')");
    a = 1;
  }
}

setInterval(myCallback, 2000);
```
```js
var a = 1;
setInterval(function() {
  switch (a++ % 3) {
    case 0:
      $(this).css("background-image", "url('http://placehold.it/350x150')");
      break;
    case 1:
      $(this).css("background-image", "url('http://placehold.it/350x150')");
      break;
    case 2:
      $(this).css("background-image", "url('http://placehold.it/350x150')");
      break;
  }
}, 2000);
```

#### :books: 參考網站：
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/switch
- https://jsfiddle.net/

---

`jQuery UI`

```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>jQuery UI Draggable - Default functionality</title>
    <link rel="stylesheet" href="//code.jquery.com/ui/1.12.1/themes/base/jquery-ui.css">
    <link rel="stylesheet" href="/resources/demos/style.css">
    <style>
      #draggable {
        width: 150px;
        height: 150px;
        padding: 0.5em;
      }
    </style>
    <script src="https://code.jquery.com/jquery-1.12.4.js"></script>
    <script src="https://code.jquery.com/ui/1.12.1/jquery-ui.js"></script>
    <script>
      $(function() {
        $("#draggable").draggable();
      });
    </script>
  </head>

  <body>
    <div id="draggable" class="ui-widget-content">
      <p>Drag me around</p>
    </div>
  </body>
</html>
```

### Accordion

```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>jQuery UI Accordion - Default functionality</title>
    <link rel="stylesheet" href="//code.jquery.com/ui/1.12.1/themes/base/jquery-ui.css">
    <link rel="stylesheet" href="/resources/demos/style.css">
    <script src="https://code.jquery.com/jquery-1.12.4.js"></script>
    <script src="https://code.jquery.com/ui/1.12.1/jquery-ui.js"></script>
    <script>
      $(function() {
        $("#accordion").accordion();
      });
    </script>
  </head>

  <body>
    <div id="accordion">
      <h3>Section 1</h3>
      <div>
        <p>
          Mauris mauris ante, blandit et, ultrices a, suscipit eget, quam. Integer ut neque. Vivamus nisi metus, molestie vel, gravida in, condimentum sit amet, nunc. Nam a nibh. Donec suscipit eros. Nam mi. Proin viverra leo ut odio. Curabitur malesuada. Vestibulum
          a velit eu ante scelerisque vulputate.
        </p>
      </div>
      <h3>Section 2</h3>
      <div>
        <p>
          Sed non urna. Donec et ante. Phasellus eu ligula. Vestibulum sit amet purus. Vivamus hendrerit, dolor at aliquet laoreet, mauris turpis porttitor velit, faucibus interdum tellus libero ac justo. Vivamus non quam. In suscipit faucibus urna.
        </p>
      </div>
      <h3>Section 3</h3>
      <div>
        <p>
          Nam enim risus, molestie et, porta ac, aliquam ac, risus. Quisque lobortis. Phasellus pellentesque purus in massa. Aenean in pede. Phasellus ac libero ac tellus pellentesque semper. Sed ac felis. Sed commodo, magna quis lacinia ornare, quam ante aliquam
          nisi, eu iaculis leo purus venenatis dui.
        </p>
        <ul>
          <li>List item one</li>
          <li>List item two</li>
          <li>List item three</li>
        </ul>
      </div>
      <h3>Section 4</h3>
      <div>
        <p>
          Cras dictum. Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Vestibulum ante ipsum primis in faucibus orci luctus et ultrices posuere cubilia Curae; Aenean lacinia mauris vel est.
        </p>
        <p>
          Suspendisse eu nisl. Nullam ut libero. Integer dignissim consequat lectus. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos.
        </p>
      </div>
    </div>
  </body>
</html>
```

### Autocomplete

```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>jQuery UI Autocomplete - Default functionality</title>
    <link rel="stylesheet" href="//code.jquery.com/ui/1.12.1/themes/base/jquery-ui.css">
    <link rel="stylesheet" href="/resources/demos/style.css">
    <script src="https://code.jquery.com/jquery-1.12.4.js"></script>
    <script src="https://code.jquery.com/ui/1.12.1/jquery-ui.js"></script>
    <script>
      $(function() {
        var availableTags = [
          "ActionScript",
          "AppleScript",
          "Asp",
          "BASIC",
          "C",
          "C++",
          "Clojure",
          "COBOL",
          "ColdFusion",
          "Erlang",
          "Fortran",
          "Groovy",
          "Haskell",
          "Java",
          "JavaScript",
          "Lisp",
          "Perl",
          "PHP",
          "Python",
          "Ruby",
          "Scala",
          "Scheme"
        ];
        $("#tags").autocomplete({
          source: availableTags
        });
      });
    </script>
  </head>

  <body>
    <div class="ui-widget">
      <label for="tags">Tags: </label>
      <input id="tags">
    </div>
  </body>
</html>

```
---

#### :books: 參考網站：
- [jQuery.Marquee](https://github.com/aamirafridi/jQuery.Marquee)

---

```html
<script>
  window.onload = fnInit;

  function fnInit() {}
</script>
```

---

```js
function Person(firstName) {
  this.age = 0;
  this.firstName = firstName;

  setInterval(function growUp() {
    this.age++;
  }, 1000);
};

Person.prototype = {
  sayHello: function() {
    console.log("Hello, I'm " + this.firstName);
  },
  walk: function() {
    console.log("I am walking!");
  },
  sayGoodBye: function() {
    console.log("Goodbye!");
  }
};

/*
var p = new Person();
var person1 = new Person();
var person2 = new Person();
*/

var person1 = new Person('Alice');
var person2 = new Person('Bob');

console.log('person1 is ' + person1.firstName); // logs "person1 is Alice"
console.log('person2 is ' + person2.firstName); // logs "person2 is Bob"

person1.sayHello();
person2.sayHello();

person1.walk();
person2.walk();
```
---

```html
<script>
  $("a").click(function(event) {
    event.preventDefault();
    $("<div>")
      .append("default " + event.type + " prevented")
      .appendTo("#log");
  });
</script>
```

```html
<script type="text/javascript">
  $.ajax({
    type: "GET",
    url: "/path/to/data.xml",
    dataType: "xml",
    success: function(xmlData) {
      var totalNodes = $('*', xmlData).length; // count XML nodes
      alert("This XML file has " + totalNodes);
    },
    error: function() {
      alert("Could not retrieve XML file.");
    }
  });
</script>
```

```js
$("#target").submit(function(event) {
  alert("Handler for .submit() called.");
  //prevent the default action	
  event.preventDefault();
});
```
---

```html
<script type="text/javascript">
  var allImages = $("img"); // all IMG elements 
  var allPhotos = $("img.photo"); // all IMG elements with class "photo"
  var curPhoto = $("img#currentPhoto"); // IMG element with id "currentPhoto"
</script>

<script type="text/javascript">
  $("img").css({
      "padding": "1px",
      "border": "1px solid #333"
    })
    .wrap("<div class='img-wrap'/>");
</script>
```

```js
// shows every <p> on the page
$("p").show();

// hides every <p> on the page
$("p").hide();

// hides every other <p> on the page
$("p:odd").hide();
```
```html
<input type="button" id="showPicture">
<img src="/pic.jpg" id="picture"><span>This is the picture's caption</span>

<script type="text/javascript">
  $("#picture").hide().next().hide();
  $("#showPicture").click(function() {
    $("#picture").show("fast", function() {
      $("#picture").next().show();
    });
  });
</script>
```

#### :books: 參考網站：
- https://www.ibm.com/developerworks/xml/tutorials/x-processxmljquerytut/

---

#### :books: 參考網站：
- [CodeIgniter and Ajax using jQuery](https://www.ibm.com/developerworks/library/wa-aj-codeigniter/)
- [Very simple login using Perl, jQuery, Ajax, JSON and MySQL](https://www.ibm.com/developerworks/library/ws-simplelogin/)

---

```js
if ($(window).width() < 960) {
  console.log('Less than 960');
} else {
  console.log('More than 960');
}
```

#### :books: 參考網站：
- [width](http://api.jquery.com/width/)

---

<img src="http://zeptojs.com/logo.png" width="300">

#### :books: 參考網站：
- [zeptojs](http://zeptojs.com/)
- [velocityjs](http://velocityjs.org/)

---