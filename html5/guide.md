<img src="http://i.imgur.com/Ovy92WP.png" width="80">
<img src="http://i.imgur.com/Vk22Gg1.png" width="100">


`DOM` (`Document Object Model`，`文件物件模型`)

<img src="http://i.imgur.com/ZAwncGq.png" width="400">

---

#### :books: 參考網站：
- [Markup Validation Service](https://validator.w3.org/)

---

```html
<!--[if IEMobile]>
<![endif]-->

<!--[if mso]>
<![endif]-->

<!--[if gte mso 9]>
<![endif]-->

<!--[if gte mso 11]>
<![endif]-->

<!--[if lte IE 7]>
<![endif]-->

<!--[if gte IE 7]>
<![endif]-->

<!--[if IE 8]>
<![endif]-->

<!--[if lt IE 8]>
<![endif]-->

<!--[if lt IE 9]>
<![endif]-->

<!--[if IE]><p>You are using Internet Explorer.</p><![endif]-->
<!--[if !IE]><p>You are not using Internet Explorer.</p><![endif]-->

<!--[if IE 7]><p>Welcome to Internet Explorer 7!</p><![endif]-->
<!--[if !(IE 7)]><p>You are not using version 7.</p><![endif]-->

<!--[if gte IE 7]><p>You are using IE 7 or greater.</p><![endif]-->
<!--[if (IE 5)]><p>You are using IE 5 (any version).</p><![endif]-->
<!--[if (gte IE 5.5)&(lt IE 7)]><p>You are using IE 5.5 or IE 6.</p><![endif]-->
<!--[if lt IE 5.5]><p>Please upgrade your version of Internet Explorer.</p><![endif]-->


<!--[if IE 8]>
<p>Welcome to Internet Explorer 8.</p>
<![endif]-->

<!--[if lt IE 8]>
<p>Please upgrade to Internet Explorer version 8.</p>
<![endif]-->

<!--[if gte IE 7]>
<script>
  alert("Congratulations! You are running Internet Explorer 7 or a later version of Internet Explorer.");
</script>
<p>Thank you for closing the message box.</p>
<![endif]-->

```

#### :books: 參考網站：
- https://msdn.microsoft.com/en-us/library/ms537512(v=vs.85).aspx
- https://msdn.microsoft.com/zh-cn/library/cc817577.aspx

---

```html
<noscript>
   <strong>Warning !</strong>
   Because your browser does not support HTML5, some elements are simulated using JScript.
   Unfortunately your browser has disabled scripting. Please enable it in order to display this page.
</noscript>
```

---

```
MyWebsite/
  |--css/
  |  |--style.css <-- compiled from scss/style.scss
  |
  |--images/
  |
  |--js/
  |  |--materialize.js
  |
  |--scss/
  |  |--style.scss
  |  |--components/
  |
  |--index.html
```

---

`link`<a name="link"></a>

```html
<link rel="stylesheet" href="//maxcdn.bootstrapcdn.com/bootstrap/3.3.2/css/bootstrap.min.css">
<link rel="stylesheet" href="//maxcdn.bootstrapcdn.com/bootstrap/3.3.2/css/bootstrap-theme.min.css">

<link href="//netdna.bootstrapcdn.com/font-awesome/3.1.1/css/font-awesome.css" rel="stylesheet">
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/font-awesome/4.4.0/css/font-awesome.min.css">
```

---


`css`<a name="css"></a>


> 「網站圖示」(也稱為「捷徑圖示」或 `Favicon`) 是與特定網站或網頁相關聯的小型影像。
> `16x16`、`24x24`、`32x32`、`64x64`

`favicon.ico`

```html
<head>
  <link rel="SHORTCUT ICON" href="http://www.mydomain.com/myicon.ico"/>
  <title>My Title</title>
</head>
```

> 使用 `rel="canonical"` 連結元素指出偏好網址


```html
<link rel="shortcut icon" href="/favicon.ico" />
<link rel="shortcut icon" href="https://www.example.com/favicon.ico">	
<link rel="Shortcut Icon" href="/favicon.ico" type="image/x-icon">	
<link rel="icon" type="image/png" href="assets/i/favicon.png">
<link rel="icon" type="text/x-icon" href="tmp/favicon.ico">
<link href="https://www.example.com/CqvycaYb5lt.png" rel="apple-touch-icon">	
<link type="text/css" rel="stylesheet" href="https://www.example.com/style.css">	

<link href='https://fonts.googleapis.com/css?family=Love+Ya+Like+A+Sister' rel='stylesheet' type='text/css'>

<link rel="canonical" href="https://blog.example.com/dresses/green-dresses-are-awesome" />
<link rel="canonical" href="http://www.apple.com/" />

<!-- Include the CSS -->
<link rel="stylesheet" href="style.css">	
<link rel="stylesheet" type="text/css" href="//www.example.com/style.css" media="all">	

<!-- Add to homescreen for Chrome on Android -->
<meta name="mobile-web-app-capable" content="yes">
<link rel="icon" sizes="192x192" href="assets/i/app-icon72x72@2x.png">

<!-- Add to homescreen for Safari on iOS -->
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="black">
<meta name="apple-mobile-web-app-title" content="Amaze UI"/>
<link rel="apple-touch-icon-precomposed" href="assets/i/app-icon72x72@2x.png">

<!-- Tile icon for Win8 (144x144 + tile color) -->
<meta name="msapplication-TileImage" content="assets/i/app-icon72x72@2x.png">
<meta name="msapplication-TileColor" content="#0e90d2">

<style>	</style>
```
#### :books: 參考網站：
- [使用標準網址](https://support.google.com/webmasters/answer/139066?hl=zh-Hant)

---
`meta`<a name="meta"></a>

```html
<meta charset="utf-8">
<meta name="en:locale" content="zh_TW">

<meta name="robots" content="noindex,nofollow">
<meta name="robots" content="noodp, noydir">
<meta name="robots" content="noodp">
<meta name="robots" content="noindex">

<meta name="googlebot" content="noindex,nofollow">
<meta name="googlebot" content="noindex">

<meta name="description" content="">
<meta name="Description" content="" />
<meta name="description" content="A description of the page" />

<meta name="author" content="">

<meta name="viewport" content="width=device-width">
<meta name="viewport" content="initial-scale=1">
<meta name="viewport" content="width=500, initial-scale=1">
<meta name="viewport" content="initial-scale=1, maximum-scale=1">
<meta name="viewport" content="width=device-width, initial-scale=1">
<meta name="viewport" content="width=320; initial-scale=1.0; user-scalable=no;">

<meta name="HandheldFriendly" content="true">
<meta name="MobileOptimized" content="{device-width-in-pixels}" />

<meta name="title" content="">

<meta content="text/html; charset=UTF-8" http-equiv="content-type">
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">

<meta content="" name="description">

<meta http-equiv="X-UA-Compatible" content="IE=EmulateIE7" />
<meta http-equiv="X-UA-Compatible" content="IE=8" />
<meta http-equiv="X-UA-Compatible" content="IE=8; IE=9" />
<meta http-equiv="X-UA-Compatible" content="IE=Edge">
<meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">

<meta http-equiv="refresh" content="0;url=pages/index.html">

<meta name="google" content="notranslate" />

<!-- Set render engine for 360 browser -->
<meta name="renderer" content="webkit">

<!-- No Baidu Siteapp-->
<meta http-equiv="Cache-Control" content="no-siteapp" />
```

`robots.txt`
```
User-agent: *
Allow: /*?$
```

```
User-agent: *
User-agent: Googlebot
User-agent: Googlebot-News
User-agent: Googlebot-Image
User-agent: Googlebot-Video
User-agent: Googlebot-Mobile
User-agent: Mediapartners-Google
User-agent: Adsbot-Google
```

#### :books: 參考網站：
- [可讓 Google 識別的中繼標記](https://support.google.com/webmasters/answer/79812?hl=zh-Hant)
- [Viewport_meta_tag](https://developer.mozilla.org/en-US/docs/Mozilla/Mobile/Viewport_meta_tag)
- [HandheldFriendly](https://developer.blackberry.com/playbook/html5/documentation/handheldfriendly.html)
- [viewport](https://developer.blackberry.com/playbook/html5/documentation/viewport.html)
- http://www.ibm.com/support/knowledgecenter/SS4SHV_7.0.0/com.volantis.mcs.eclipse.doc/wag/wag_meta_viewport.html
- https://support.google.com/webmasters/answer/93710?hl=zh-Hant
- [Search Console](https://www.google.com/webmasters/tools/home?hl=zh-TW&pli=1)
- [robots_txt](https://developers.google.com/webmasters/control-crawl-index/docs/robots_txt)
- [建立 robots.txt 檔案](https://support.google.com/webmasters/answer/6062596?hl=zh-Hant)

---

`img`<a name="img"></a>

```html
<img src="mygraphic.bmp">	
<img src="large.png" width="20">
<img src="mdn-logo-sm.png" alt="MDN">
<img src="/uploads/100-marie-lloyd.jpg" alt="" width="100" height="150">
```

#### :books: 參考網站：
- [img](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/img)

---

<img src="http://ogp.me/logo.png" width="200">

`opengraph`<a name="opengraph"></a>


```html
<html prefix="og: http://ogp.me/ns#">
<head>
<title>The Rock (1996)</title>
<meta property="og:title" content="The Rock" />
<meta property="og:type" content="video.movie" />
<meta property="og:url" content="http://www.imdb.com/title/tt0117500/" />
<meta property="og:image" content="http://ia.media-imdb.com/images/rock.jpg" />
...
</head>
...
</html>
```

```html
<meta property="og:title" content="" />
<meta property="og:description" content="" />
<meta property="og:url" content="http://" />
<meta property="og:locale" content="zh_TW" />
<meta property="og:locale" content="zh_CN" />
<meta property="og:locale" content="zh_HK" />
<meta property="og:locale" content="en_US" />
<meta property="og:image" content="" />
<meta property="og:type" content="website" />
<meta property="og:site_name" content="" />
```

```html
<meta property="fb:app_id"          content="1234567890" /> 
<meta property="og:type"            content="article" /> 
<meta property="og:url"             content="http://newsblog.org/news/136756249803614" /> 
<meta property="og:title"           content="Introducing our New Site" /> 
<meta property="og:image"           content="https://scontent-sea1-1.xx.fbcdn.net/hphotos-xap1/t39.2178-6/851565_496755187057665_544240989_n.jpg" /> 
<meta property="og:description"    content="http://samples.ogp.me/390580850990722" />
```

```html
<meta property="og:type" content="article" />
<meta property="og:type" content="video.movie" />
<meta property="og:type" content="book" />

<meta property="og:title" content="Introducing our New Site" />
<meta property="og:description" content="http://samples.ogp.me/390580850990722" />
<meta property="og:type" content="article" />
<meta property="og:image" content="https://scontent-sea1-1.xx.fbcdn.net/hphotos-xap1/t39.2178-6/851565_496755187057665_544240989_n.jpg" />
<meta property="og:url" content="http://newsblog.org/news/136756249803614" />
```

```html
<meta property="og:url" content="http://www.imdb.com/title/tt2562232/" />
<meta property='og:image' content="https://images-na.ssl-images-amazon.com/images/M/MV5BODAzNDMxMzAxOV5BMl5BanBnXkFtZTgwMDMxMjA4MjE@._V1_UY1200_CR90,0,630,1200_AL_.jpg" />
<meta property='og:type' content="video.movie" />
<meta property='og:title' content="Birdman or (The Unexpected Virtue of Ignorance) (2014)" />
<meta property='og:site_name' content='IMDb' />
<meta property="og:description" content="Directed by Alejandro G. Inarritu.  With Michael Keaton, Zach Galifianakis, Edward Norton, Andrea Riseborough. Illustrated upon the progress of his latest Broadway play, a former popular actor's struggle to cope with his current life as a wasted actor is shown."
/>
```

```html
<meta property="fb:app_id" content="1234567890" /> 
```


![Imgur](http://i.imgur.com/DXvQWTV.png)

#### :books: 參考網站：
- [Open Graph protocol](http://ogp.me/)
- [opengraph](https://developers.facebook.com/docs/sharing/opengraph)
- https://developers.facebook.com/docs/reference/opengraph/object-type/article/
- https://developers.facebook.com/docs/sharing/opengraph/using-objects
- https://developers.facebook.com/docs/opengraph/getting-started
- [分享偵錯工具](https://developers.facebook.com/tools/debug/)


---

```css
list-style-type: disc;
list-style-type: circle;
list-style-type: square;
list-style-type: decimal;
list-style-type: georgian;
list-style-type: cjk-ideographic;
list-style-type: kannada;
```

<a href="https://jsfiddle.net/grpkdp33/"><img src="http://i.imgur.com/A9cwqLx.png" width="50"></a>

```html
<ul>
  <li></li>
</ul>

<ul style="list-style-type: square;">
  <li>Item 1</li>
  <li>Item 2</li>
</ul>

<ul style="list-style-type: decimal;">
  <li>Item 1</li>
  <li>Item 2</li>
</ul>

<ul style="list-style-type: decimal-leading-zero;">
  <li>Item 1</li>
  <li>Item 2</li>
</ul>

<ul style="list-style-type: lower-alpha;">
  <li>Item 1</li>
  <li>Item 2</li>
</ul>

<ul style="list-style-type: upper-alpha;">
  <li>Item 1</li>
  <li>Item 2</li>
</ul>

<ul style="list-style-type: lower-roman;">
  <li>Item 1</li>
  <li>Item 2</li>
</ul>

<ul style="list-style-type: trad-chinese-formal;">
  <li>Item 1</li>
  <li>Item 2</li>
</ul>

<ul style="list-style-type: trad-chinese-informal;">
  <li>Item 1</li>
  <li>Item 2</li>
</ul>
```

#### :books: 參考網站：
- [list-style-type](https://developer.mozilla.org/en-US/docs/Web/CSS/list-style-type)
- [list-style](https://developer.mozilla.org/en-US/docs/Web/CSS/list-style)
- [list-style-image](https://developer.mozilla.org/en-US/docs/Web/CSS/list-style-image)
- https://msdn.microsoft.com/zh-tw/library/1f6ss9cc(v=vs.100).aspx

---

```html
<option selected="" value="">請擇一</option>
<option selected="" value="">Select one</option>

<body> </body>
<div> </div>
<div id="clickme"> </div>

<h1>Hello, world!</h1>
<h2> </h2>

<span> </span>
<label>	</label>
<textarea> </textarea>
<button> </button>
<br>
<br />
<p>	</p>
<b>	</b>
<i>	</i>


	
<tbody>	</tbody>
<thead>	</thead>
<tr> </tr>
<th> </th>
	
<a href="" target="_blank">	</a>
<a href="">	</a>

class=""
id="myDiv"
```

```
80x80 (avatar)
150x112 (thumbnail)
320x240 (thumbnail)
640x480 (message boards)
800x600 (15-inch monitor)
1024x768 (17-inch monitor)
1280x1024 (19-inch monitor)
1600x1200 (21-inch monitor)
```

---
`form`<a name="form"></a>

```html
<form> </form>

<form name="aspnetForm" method="post" action="Search.aspx" id="aspnetForm">
</form>

<FORM METHOD="Get" ACTION="Profile.asp"> 
  <INPUT TYPE="Text" NAME="FirstName">  
  <INPUT TYPE="Text" NAME="LastName"> 
  <INPUT TYPE="Text" NAME="Age"> 
  <INPUT TYPE="Hidden" NAME="UserStatus" VALUE="New"> 
  <INPUT TYPE="Submit" VALUE="Enter"> 
</FORM> 

<FORM NAME="Button Example" METHOD="POST" ACTION="button.asp">
  <H3>Computer Programming Experience:</H3>
  <p>
    <INPUT TYPE="RADIO" NAME="choice" VALUE="Less than 1"> Less than 1 year.
    <BR>
    <INPUT TYPE="RADIO" NAME="choice" VALUE="1 to 5"> 1-5 years.
    <BR>
    <INPUT TYPE="RADIO" NAME="choice" VALUE="More than 5"> More than 5 years.
    <BR>
  </p>
  <p>
    <INPUT TYPE="SUBMIT" VALUE="Submit">
    <INPUT TYPE="RESET" VALUE="Clear Form">
  </p>
</form>

<input id="username" maxlength="64" name="username" type="text">
<input id="password" maxlength="64" name="password" type="password">

<input placeholder="Email address" type="email">
<input placeholder="Username" type="text">
<input placeholder="Password" type="password">

<input type="text" id="customerName" name="customerName" maxlength="50" size="30" tabindex="1" value="" autocomplete="off">	
<input type="email" id="email" name="email" maxlength="64" size="30" tabindex="3" value="" autocorrect="off" autocapitalize="off">	

<input type="email" id="inputEmail" class="form-control" placeholder="Email address" required autofocus>
<input type="password" id="inputPassword" class="form-control" placeholder="Password" required>
```
---

<a href="https://jsfiddle.net/5Lgdnbt3/"><img src="http://i.imgur.com/A9cwqLx.png" width="50"></a>

`空格` `Space`

```html
&nbsp;
&#160;
```
```
<p style="text-indent: 5em;">Hello World!</p>
```

---

<a href="https://jsfiddle.net/y9po4nxv/"><img src="http://i.imgur.com/A9cwqLx.png" width="50"></a>

```html
<!DOCTYPE HTML>
<html lang="en">
  <head>
    <title>Untitled</title>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
    <meta http-equiv="Cache-Control" content="no-cache">
    <meta http-equiv="Pragma" content="no-cache">
    <meta http-equiv="Expires" content="-1" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">
  </head>

  <body>
    <div class="container">

      <form class="form-inline">
        <div class="form-group">
          <span>Email:</span>
          <input tabindex="1" maxlength="100" class="form-control" name="email" id="email" origvalue="myname@example.com" value="myname@example.com">
        </div>
        <br />
        <br />
        <div class="form-group">
          <span>Login:</span>
          <input class="form-control" tabindex="3" maxlength="50" name="loginName" id="loginName" origvalue="loginName" value="loginName">
        </div>
        <br />
        <br />
        <div class="form-group">
          <select class="form-control" id="myselect">
            <option value="1">01 - January</option>
            <option value="2">02 - February</option>
            <option value="3">03 - March</option>
            <option value="4">04 - April</option>
            <option value="5">05 - May</option>
            <option value="6">06 - June</option>
            <option value="7">07 - July</option>
            <option value="8">08 - August</option>
            <option value="9">09 - September</option>
            <option value="10">10 - October</option>
            <option value="11">11 - November</option>
            <option value="12">12 - December</option>
          </select>
        </div>
      </form>
      <br />
      <br />
      <button type="submit" class="btn btn-default" id="btn">btn</button>
    </div>
    <!--Load the AJAX API-->
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.3/jquery.min.js"></script>
    <!-- Latest compiled and minified JavaScript -->
    <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.5/js/bootstrap.min.js" integrity="sha512-K1qjQ+NcF2TYO/eI3M6v8EiNYZfA95pQumfvcVrTHtwQVDG+aHRqLi/ETn2uB+1JqwYqVG3LIvdm9lj6imS/pQ==" crossorigin="anonymous"></script>

    <script type="text/javascript">
      // execute when the HTML file's (document object model: DOM) has loaded
      $(document).ready(function() {});

      $("#btn").click(function() {
        // alert( $( "#myselect option:selected" ).text() );
        alert($("#myselect").val());
      });
    </script>
  </body>
</html>

<!-- Bootstrap core CSS -->
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.5/css/bootstrap.min.css" integrity="sha512-dTfge/zgoMYpP7QbHy4gWMEGsbsdZeCXz7irItjcC3sPUFtf0kuFbDz/ixG7ArTxmDjLXDmezHubeNikyKGVyQ==" crossorigin="anonymous">

<!-- Optional theme -->
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.5/css/bootstrap-theme.min.css" integrity="sha384-aUGj/X2zp5rLCbBxumKTCw2Z50WgIr1vs/PFN4praOTvYXWlVyh2UtNUU0KAUhAX" crossorigin="anonymous">

<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/font-awesome/4.4.0/css/font-awesome.min.css">
<link rel="stylesheet" type="text/css" href="https://fonts.googleapis.com/css?family=Varela+Round">
```

`data_URIs`

```html
<!DOCTYPE HTML>
<html lang="en">
  <head>
    <style>
    </style>
    <link type="text/css" rel="stylesheet" href="data:text/css;base64,">
  </head>

  <body>
    <img src="mygraphic.png">

    <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAEAAAABACAI
AAAFSDNYfAAAAaklEQVR42u3XQQrAIAwAQeP%2F%2F6wf8CJBJTK9lnQ7FpHGaOurt1
I34nfH9pMMZAZ8BwMGEvvh%2BBsJCAgICLwIOA8EBAQEBAQEBAQEBK79H5RfIQAAAAA
AAAAAAAAAAAAAAAAAAAAAAID%2FABMSqAfj%2FsLmvAAAAABJRU5ErkJggg%3D%3D">

    <a download="mygraphic.png" href="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAEAAAABACAI
AAAFSDNYfAAAAaklEQVR42u3XQQrAIAwAQeP%2F%2F6wf8CJBJTK9lnQ7FpHGaOurt1
I34nfH9pMMZAZ8BwMGEvvh%2BBsJCAgICLwIOA8EBAQEBAQEBAQEBK79H5RfIQAAAAA
AAAAAAAAAAAAAAAAAAAAAAID%2FABMSqAfj%2FsLmvAAAAABJRU5ErkJggg%3D%3D">mygraphic.png</a>
  </body>
</html>
```

#### :books: 參考網站：
- [data_URIs](https://developer.mozilla.org/en-US/docs/Web/HTTP/data_URIs)
- [data Protocol](https://msdn.microsoft.com/zh-tw/library/cc848897(v=vs.85).aspx)

---

```html
<pre>
body {
  color: red;
}

a {
  color: green;
}
</pre>
```

#### :books: 參考網站：
- [pre](https://developer.mozilla.org/es/docs/Web/HTML/Elemento/pre)

---

```html
<!DOCTYPE html>
<html>
  <head>
    <meta http-equiv="refresh" content="0;url=pages/index.html">
    <title>Untitled</title>
    <script language="javascript">
      window.location.href = "pages/index.html"
    </script>
  </head>

  <body>
    Go to <a href="pages/index.html">/pages/index.html</a>
  </body>
</html>
```

#### :books: 參考網站：

- [行動裝置相容性測試](https://www.google.com/webmasters/tools/mobile-friendly/)
- [http-compression-test](http://www.whatsmyip.org/http-compression-test/)
- [fonts](https://developers.google.com/fonts/docs/getting_started)
- [a](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/a)

---

```html
<table id="producttable">
  <thead>
    <tr>
      <td>UPC_Code</td>
      <td>Product_Name</td>
    </tr>
  </thead>
  <tbody>
    <!-- existing data could optionally be included here -->
  </tbody>
</table>

<template id="productrow">
  <tr>
    <td class="record"></td>
    <td></td>
  </tr>
</template>

<script type="text/javascript">
  if ('content' in document.createElement('template')) {
    // Instantiate the table with the existing HTML tbody and the row with the template
    var t = document.querySelector('#productrow'),
      td = t.content.querySelectorAll("td");
    td[0].textContent = "1235646565";
    td[1].textContent = "Stuff";

    // Clone the new row and insert it into the tabledocument.querySelector
    var tb = document.getElementsByTagName("tbody");
    var clone = document.importNode(t.content, true);
    tb[0].appendChild(clone);

    // Create a new row
    td[0].textContent = "0384928528";
    td[1].textContent = "Acme Kidney Beans";

    // Clone the new row and insert it into the table
    var clone2 = document.importNode(t.content, true);
    tb[0].appendChild(clone2);
  } else {
    // Find another way to add the rows to the table because 
    // the HTML template element is not supported.
  }
</script>
```


```html
<link rel="import" href="myfile1.html">
<link rel="import" href="myfile2.html">
```

myfile1.html
```html
<link rel="import" href="jquery.html">
```

myfile2.html
```html
<link rel="import" href="jquery.html">
```

```html
<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.3/jquery.min.js"></script>
```

#### :books: 參考網站：
- [HTML_Imports](https://developer.mozilla.org/en-US/docs/Web/Web_Components/HTML_Imports)
- [vulcanize](https://github.com/Polymer/vulcanize)

---

#### :books: 參考網站：
- [How To  Determine Browser Version from a Script](https://support.microsoft.com/en-us/kb/167820)
- [performance](https://developers.google.com/web/fundamentals/performance/?hl=zh-tw)
- [How do I get the text value of a selected option?](http://learn.jquery.com/using-jquery-core/faq/how-do-i-get-the-text-value-of-a-selected-option/)
- [click](http://api.jquery.com/click/)
- [移除禁止轉譯 JavaScript](https://developers.google.com/speed/docs/insights/BlockingJS?hl=zh-tw)
- [為 CSS 傳送進行最佳化處理](https://developers.google.com/speed/docs/insights/OptimizeCSSDelivery)
- [CSS Sprite Generator](http://spritegen.website-performance.org/)
- [HEAD](https://github.com/joshbuchea/HEAD)


---


- http://placehold.it/60/ffffff/000000
- http://placehold.it/460x250/e67e22/ffffff&text=HTML5
- https://placeholdit.imgix.net/~text?txtsize=75&txt=&w=800&h=300
- https://placeholdit.imgix.net/~text?txtsize=75&txt=800×300&w=800&h=300
- https://placeholdit.imgix.net/~text?txtsize=8&bg=008000&txtclr=000000&txt=&w=60&h=60
