**`emmet`**

<img src="http://emmet.io/-/4076541266/i/logo.svg" alt="emmet" width=58 height=58>

```
#page>div.logo+ul#navigation>li*5>a{Item $}
```

```html
<div id="page">
    <div class="logo"></div>
    <ul id="navigation">
        <li><a href="">Item 1</a></li>
        <li><a href="">Item 2</a></li>
        <li><a href="">Item 3</a></li>
        <li><a href="">Item 4</a></li>
        <li><a href="">Item 5</a></li>
    </ul>
</div>
```

```
div>ul>li
```
```html
<div>
    <ul>
        <li></li>
    </ul>
</div>
```
```
div+p+bq
```
```html
<div></div>
<p></p>
<blockquote></blockquote>
```

```
div+div>p>span+em 
```
```html
<div></div>
<div>
    <p><span></span><em></em></p>
</div>
```

```
ul>li*5
```
```html
<ul>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
</ul>
```
---

```
m0
```
```css
margin: 0;
```

```
p10p20p
```

```css
padding: 10% 20%;
```
---

```
!
```

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Document</title>
</head>
<body>
  
</body>
</html>
```

```
meta:vp
```

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

```
style
```

```
script:src
src:sc
```
```html
<script src=""></script>
```

```
div.panel.panel-default>div.panel-body{Basic panel example}
```

```
<div class="panel panel-default">
  <div class="panel-body">
    Basic panel example
  </div>
</div>
```

```
lorem100

p*4>lorem

ul.generic-list>lorem10.item*4
```

#### :books: 參考網站：

- [emmet](http://emmet.io/)
- http://docs.emmet.io/abbreviations/syntax/
- [emmet-atom](https://github.com/emmetio/emmet-atom)
- [Cheat Sheet](http://docs.emmet.io/cheat-sheet/)
- http://livestyle.io/
- https://chrome.google.com/webstore/detail/emmet-livestyle/diebikgmpmeppiilkaijjbdgciafajmg?hl=zh-TW
