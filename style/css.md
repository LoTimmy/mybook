<img src="http://i.imgur.com/TjmgUA1.png" width="50">

`Pseudo` `[ˋsudo]` `虛擬` `pseu・do`

---

<img src="http://i.imgur.com/zWoVYav.png" width="300">
<img src="http://i.imgur.com/BLxN8Y5.png" width="300">

- **`Selector`** `選擇器` `se・lec・tor`
- **`Declaration`** `[͵dɛkləˋreʃən]` `宣告` `de・cla・ra・tion`
- **`Property`** `[ˋprɑpɚtɪ]` `屬性` `prop・er・ty`
- **`Separator`** `[ˋsɛpə͵retɚ]` `分隔符號` `sep・a・ra・tor`

<img src="http://api.jquery.com/resources/0042_04_04.png" width="250">

- **`Padding`** `[ˋpædɪŋ]` `邊框間距` `與邊框距離` `pad・ding`
- **`Margin`** `[ˋmɑrdʒɪn]` `邊界` `mar・gin`
- **`Border`** `[ˋbɔrdɚ]` `框線` `bor・der`

<img src="https://developer.mozilla.org/files/4109/padding-bottom.svg" width="350">

- **`Area`** `[ˋɛrɪə]` `區域` `ar・e・a`

---

**`External stylesheet`**

`Stylesheet` `樣式表`

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>My CSS experiment</title>
    <link rel="stylesheet" href="style.css">
  </head>
  <body>
    <h1>Hello World!</h1>
    <p>This is my first CSS example</p>
  </body>
</html>
```

`style.css`
```css
h1 {
  color: blue;
  background-color: yellow;
  border: 1px solid black;
}

p {
  color: red;
}
```

---

```html
<style>
  body {
    background-color: #CFCFCF;
  }
  @import url("otherStyleSheet.css");
</style>
```

**`Internal stylesheet`**
```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>My CSS experiment</title>
    <style>
      h1 {
        color: blue;
        background-color: yellow;
        border: 1px solid black;
      }

      p {
        color: red;
      }
    </style>
  </head>
  <body>
    <h1>Hello World!</h1>
    <p>This is my first CSS example</p>
  </body>
</html>

```

**`Inline styles`**

`Inline` `內嵌` `內置`

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>My CSS experiment</title>
  </head>
  <body>
    <h1 style="color: blue;background-color: yellow;border: 1px solid black;">Hello World!</h1>
    <p style="color:red;">This is my first CSS example</p>
  </body>
</html>
```
#### :books: 參考網站：
- [How_CSS_works](https://developer.mozilla.org/en-US/docs/Learn/CSS/Introduction_to_CSS/How_CSS_works)

---

##### CSS 规则示意图
![](http://www.ibm.com/developerworks/cn/web/1311_huangwh_jqueryhandson/image003.jpg)

要将页面中一个 ID 为 message 的元素的字体颜色设置为蓝色、字体大小设置为 17px
```css
#message {
  color:blue;
  font-size:17px;
}
```
从上述 CSS 规则中可见，我们期望的对元素外观的操作（字体颜色设置为蓝色、字体大小设置为 17px）是通过  "color:blue" 和 "font-size:17px" 这 2 个属性声明指定的。而这些操作要作用于哪些元素，则是通过 CSS 的选择器 "#message" 指定为 ID 等于 "message" 的元素。

```css
div {
  width: 60px;
  height: 60px;
  margin: 5px;
  float: left;
}

pre, p {
  font-size: 2.5em;
  color: #FE7F88;
  background-color: transparent;
}
```

```html
<style type="text/css">
  div {
    padding: 10px;
  }
</style>
```

---

<a href="https://jsfiddle.net/agmkxp55/"><img src="http://i.imgur.com/A9cwqLx.png" width="50"></a>

```css
.fontSize-18 {
  font-size: 18px;
}

.colorRed {
  color: red;
}
```

```html
<div class="fontSize-18 colorRed">Test Message</div>
```

---

```html
<div style="background-color:blue;"></div>
<div style="background-color:rgb(15,99,30);"></div>
<div style="background-color:#123456;"></div>
<div style="background-color:#f11;"></div>
```

```css
background: green;
background: yellow;

background: url("../img/bg-pattern.png"), #7b4397;
background: url("../img/bg-pattern.png"), -webkit-linear-gradient(to left, #7b4397, #dc2430);
background: url("../img/bg-pattern.png"), linear-gradient(to left, #7b4397, #dc2430);

background-image: none;
background-image: url("http://www.example.com/bck.png");
background-image: inherit;

background-attachment: fixed;

background-repeat: repeat;
background-repeat: no-repeat;

background-position: top;
background-position: bottom;
background-position: left;
background-position: right;
background-position: center;
background-position: 25% 75%;

background-size: cover;
background-size: contain;
background-size: auto;
background-size: 50%;
background-size: 50% auto;

background-color: #123456;
background-color: #f11;
background-color: red;
background-color: blue;
background-color: lightblue;
background-color: rgb(15, 99, 30);
background-color: transparent;
background-color: #000000;
background-color: #ffffff;
```

---

```css
border: 2px solid green;
border: solid 2px blue;
border: 2px dotted;
border: medium dashed green;


border-bottom-left-radius: 15px 30px;
border-bottom-left-radius: 2em;
border-bottom-right-radius: 15px 30px;
border-bottom-right-radius: 5em;

border-color: #7f7f7f;

border-radius: 5px;

border-style: dashed;
border-style: solid;

border-top-left-radius: 10em;
border-top-left-radius: 50px 25px;
border-top-left-radius: 50px 30px;

border-top-right-radius: 50px 25px;
border-top-right-radius: 50px 30px;

border-width: 1px;
```

---

```css
font: 11px Verdana, Arial, Helvetica; /* 設定物件的個別字型屬性組合。亦或是從使用者喜好設定中的六個字型當中，設定一或多個字型。 */

font-family: Arial; /* 設定用於物件中文字的字型名稱。 */
font-family: sans-serif;
font-family: 'Microsoft JhengHei UI', 'Microsoft JhengHei', PMingLiU, MingLiU, 'Segoe UI', 'Lucida Grande', Verdana, Arial, Helvetica, sans-serif;

font-size: 20px;
font-style: italic;

font-weight: bold;
```
> `font-family` 屬性可用的任何字型家族值範圍。此屬性可設為多個以逗號分隔的值。其預設值會隨著使用者設定的不同而改變。

#### :books: 參考網站：
- [font](https://msdn.microsoft.com/zh-tw/library/ee371240(v=expression.40).aspx)
- [font-family](https://msdn.microsoft.com/zh-tw/library/ee371191(v=expression.40).aspx)

---

`margin`<a name="margin"></a>

```css
margin: 20px 0px 10px 75%;
margin: 8px;
margin: 0 0 0 .5em;
margin: 0px auto; /* 設定物件上、下、左、右邊界的寬度。 */
margin-top: 10px; /* 設定物件的上邊界高度。 */
margin-right: 10px; /* 設定物件的右邊界高度。 */
margin-bottom: 4cm; /* 設定物件的下邊界高度。 */
margin-left: 3%; /* 設定物件左邊界的高度。 */
```

> `margin` 此屬性為最多可指定四個寬度值的省略屬性；四個值的順序為：上、右、下、左。
> 如果指定一個寬度值，所有四個邊都會使用這個值。
> 如果指定兩個寬度值，那麼上和下框線會使用第一個寬度，而左和右框線則會使用第二個寬度。
> 如果指定三個值，這三個值將分別用於上、右/左及下框線。


#### :books: 參考網站：
- [margin-top](https://msdn.microsoft.com/zh-tw/library/ee371241(v=expression.40).aspx)
- [margin-right](https://msdn.microsoft.com/zh-tw/library/ee371256(v=expression.40).aspx)

**[⬆ Back to Top](#table-of-contents)**

---

```css
display: none; /* 設定是否呈現物件。 */

display: none; /* 不呈現物件。 */
display: inline; /* 預設值。物件會呈現為內嵌元素，並根據內容尺寸調整大小。 */
display: block; /* 物件會呈現為區塊元素。 */
display: inline-block; /* 物件會呈現為內嵌，但物件內容會呈現為區塊元素。相鄰的內嵌元素在空間允許的情況下會在同一行呈現。 */

display: contents;
display: list-item;
display: inline-list-item;
display: table; /* 物件會呈現為表格。 */
display: inline-table; /* 物件會呈現為區塊元素，並且會新增清單項目標記。 */
display: table-cell;
display: table-column;
display: table-column-group;
display: table-footer-group;
display: table-header-group;
display: table-row;
display: table-row-group;
display: table-caption;
display: flex;
display: inline-flex;
display: grid;
display: inline-grid;
display: subgrid;
display: ruby;
display: ruby-base;
display: ruby-text;
display: ruby-base-container;
display: ruby-text-container;
display: run-in;
```

#### :books: 參考網站：
- [display](https://developer.mozilla.org/en-US/docs/Web/CSS/display)
- [display](https://msdn.microsoft.com/zh-tw/library/ee371238(v=expression.40).aspx)

---

```css
box-shadow: 0 0 5px 5px sienna;
box-shadow: 5px 5px 5px lightgray;

clear: both;
clear: left;

color: blue;
color: grey;
color: red;
color: rgb(255, 255, 255);
color: yellow;
color: white;

cursor: pointer;

vertical-align: baseline;
vertical-align: sub;
vertical-align: super;
vertical-align: text-top;
vertical-align: text-bottom;
vertical-align: middle;
vertical-align: top;
vertical-align: bottom;
vertical-align: 10em;
vertical-align: 4px;
vertical-align: 20%;

direction: ltr;
direction: rtl;

float: left;

height: 60px;
height: 100%;
left: 50px;

list-style: none;

letter-spacing: 0.3em;
letter-spacing: 3px;
letter-spacing: .3px;

line-height: 25px;
line-height: normal;
line-height: 3.5;
line-height: 3em;
line-height: 34%;

float: right;

max-width: 100%;
max-height: 100%;
max-height: none;

-moz-border-radius: 10em 0 5em 2em;
-moz-border-radius: 10px;
-moz-box-shadow: 10px 10px 10px #FFFFCC inset;
overflow: hidden;
padding: 10px;
padding: 5px;
padding-top: 10px;
padding-bottom: 10px;
padding-left: 10px;

position: absolute;
position: relative;
position: fixed;

text-align: left;
text-align: right;
text-align: center;

text-decoration: line-through;
text-decoration: overline;
text-decoration: underline;

text-transform: capitalize;
text-transform: uppercase;
text-transform: lowercase;
text-transform: none;
text-transform: full-width;

text-decoration: none;                 /* No text decoration */
text-decoration: underline red;        /* Red underlining */
text-decoration: underline wavy red;   /* Red wavy underlining */
text-decoration: underline;
text-decoration: overline;
text-decoration: line-through;
text-decoration: blink;
text-decoration: none;
text-decoration: underline overline;

text-indent: 3mm; /* 設定物件中第一行文字的縮排。 */
text-indent: 40px;
text-indent: 5em;

vertical-align: sAlign; /* 設定物件的垂直對齊。 */

vertical-align: baseline; /* 預設值。將物件的內容對齊至基準線。 */
vertical-align: sub; /* 將文字垂直對齊至下標。不適用於表格儲存格。 */
vertical-align: super; /* 將文字垂直對齊至上標。不適用於表格儲存格。 */

vertical-align: text-top;
vertical-align: text-bottom;
vertical-align: middle;
vertical-align: top; /* 將物件內容垂直對齊至物件頂端。 */
vertical-align: bottom;

visibility: sVisibility; /* 設定是否顯示物件內容。 */
visibility: hidden; /* 隱藏物件。 */
visibility: visible; /* 物件為可見。 */

.vis1 {
  visibility: visible
}
.vis2 {
  visibility: hidden
}

overflow-y: hidden; /* Content is clipped, with no scrollbars */
overflow-y: visible; /* Content is not clipped */
overflow-y: scroll; /* Content is clipped, with scrollbars */
overflow-y: auto; /* Let the browser decide */

/* Global values */
overflow-y: inherit;
overflow-y: initial;
overflow-y: unset;

-webkit-border-radius: 10em 0 5em 2em;
-webkit-border-radius: 10px;
-webkit-box-shadow: 10px 10px 10px #FFFFCC inset;
white-space: normal;
white-space: nowrap;
width: 45%;
width: 60px;

z-index: -1; /* 設定定位物件的堆疊順序。 */

a:link { color: #ff0000; text-decoration: none; }
a:visited { color: #990000; text-decoration: none; }
a:active, a:hover { text-decoration: underline; }

.redtext {
  color: #ff0000;
}

bottom: 3px;
right: 3px;
```

<a href="https://jsfiddle.net/q7dxrj3t/"><img src="http://i.imgur.com/A9cwqLx.png" width="50"></a>

**`line-height`** <a href="https://jsfiddle.net/yfddkmwp/"><img src="http://i.imgur.com/A9cwqLx.png" width="50"></a>

**`position`** <a href="https://jsfiddle.net/2o8qm4ft/"><img src="http://i.imgur.com/A9cwqLx.png" width="50"></a>

#### :books: 參考網站：
- [max-height](https://developer.mozilla.org/en-US/docs/Web/CSS/max-height)
- [max-width](https://developer.mozilla.org/en-US/docs/Web/CSS/max-width)
- [bottom](https://developer.mozilla.org/en-US/docs/Web/CSS/bottom)
- [top](https://developer.mozilla.org/en-US/docs/Web/CSS/top)
- [left](https://developer.mozilla.org/en-US/docs/Web/CSS/left)
- [right](https://developer.mozilla.org/en-US/docs/Web/CSS/right)
- [direction](https://developer.mozilla.org/en-US/docs/Web/CSS/direction)
- [letter-spacing](https://developer.mozilla.org/en-US/docs/Web/CSS/letter-spacing)
- [text-align](https://developer.mozilla.org/en-US/docs/Web/CSS/text-align)
- [text-indent](https://developer.mozilla.org/en-US/docs/Web/CSS/text-indent)
- [text-indent](https://msdn.microsoft.com/zh-tw/library/ee371258(v=expression.40).aspx)
- [position](https://developer.mozilla.org/en-US/docs/Web/CSS/position)
- [text-transform](https://developer.mozilla.org/en-US/docs/Web/CSS/text-transform)
- [text-decoration](https://developer.mozilla.org/en-US/docs/Web/CSS/text-decoration)
- [background-attachment](https://developer.mozilla.org/en-US/docs/Web/CSS/background-attachment)


---

```html
<style>
  @media (max-width: 600px) {
    .facet_sidebar {
      display: none;
    }
  }
  
  .show {
    display: block !important;
  }
  
  .hidden {
    display: none !important;
  }
  
  .invisible {
    visibility: hidden;
  }
</style>
```

```html
<head> 
<style>
  @media only screen and (min-device-width: 320px) and (max-device-width: 480px) {
    .hidden { display: none; }
  }
  
  @media only screen and (min-device-width: 768px) and (max-device-width: 1024px) {
    .hidden { display: none; }
  }
  
  @media screen and (max-width: 900px) {
    .show { display: block !important; }
  }
</style>
</head>

<div class="show">...</div>
<div class="hidden">...</div>
```

```html
<link rel="stylesheet" media="screen and (max-device-width: 799px)" href="http://foo.bar.com/stylesheet.css" />
```

```css
// For computer screens, the font size is 12pt.
@media screen {
  body {font-size:12pt;}
}
// When printed, the font size is 8pt.
@media print {
  body {font-size:8pt;}
}

@media screen and (max-width:400px) {
  div {border:none;}
}

@media screen and (max-width:400px) and (max-height:600px) {
  ...
}

@media screen and (device-width: 800px) {
  ... 
}

@media screen and (device-aspect-ratio: 16/9) { 
  ... 
}

@media screen and (device-aspect-ratio: 32/18) { 
  ... 
}

@media screen and (device-aspect-ratio: 1280/720) { 
  ... 
}

@media screen and (device-aspect-ratio: 2560/1440) { 
  ... 
}
```

#### :books: 參考網站：
- https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries
- https://developer.mozilla.org/en-US/docs/Web/CSS/@media
- https://developer.mozilla.org/en-US/docs/Web/CSS/background-repeat
- https://developer.mozilla.org/en-US/docs/Web/CSS/overflow-y
- https://msdn.microsoft.com/zh-tw/library/ms530813.aspx
- https://msdn.microsoft.com/zh-tw/library/hh772064.aspx
- https://msdn.microsoft.com/zh-tw/library/windows/desktop/hh772062.aspx

---

```html
<head>
<style>
.vis1 {
   visibility: visible;
}
.vis2 {
   visibility: hidden;
}
</style>
</head>
<body>
   <img id="oSphere" src="sphere.jpg" alt="sphere">
   <p onmouseover="oSphere.className='vis2'" onmouseout="oSphere.className='vis1'">
   Mouseover this text to set visibility to hidden on the image of the sphere.</p>
</body>
```

#### :books: 參考網站：
- https://msdn.microsoft.com/zh-tw/library/ms531180(v=vs.85).aspx

---

```css
p { background: #ccccff; border: solid 1px #666699; }
h1 { background: #ccff99; }
```
![](https://i-msdn.sec.s-msft.com/en-us/expression/dd326790.PixieMill04_01(en-us,MSDN.10).gif)

---

![](https://i-msdn.sec.s-msft.com/en-us/expression/dd326790.PixieMill04_02(en-us,MSDN.10).gif)
---

#### :books: 參考網站：
- [Learning CSS](https://msdn.microsoft.com/en-us/expression/dd326792.aspx)
- [margin](https://msdn.microsoft.com/en-us/library/ms530799(v=vs.85).aspx)
- [margin-top](https://msdn.microsoft.com/zh-tw/library/ms530808(v=vs.85).aspx)
- [font-family](https://msdn.microsoft.com/zh-tw/library/ms530758(v=vs.85).aspx)
- [background-image](https://developer.mozilla.org/en-US/docs/Web/CSS/background-image)
- [position](https://developer.mozilla.org/en-US/docs/Web/CSS/position)
- [bottom](https://developer.mozilla.org/en-US/docs/Web/CSS/bottom)

---

![Imgur](http://i.imgur.com/WJl0p5y.png)

<a href="https://jsfiddle.net/b4u961fe/"><img src="http://i.imgur.com/A9cwqLx.png" width="50"></a>

```css
#d5ESWAchesut {
  position: absolute;
  background-color: #800080;
  width: 150px;
  height: 150px;
  top: 10px;
  left: 10px;
  z-index: 3;
}

#S2aKEGaMeswu {
  position: absolute;
  background-color: #008000;
  width: 150px;
  height: 150px;
  top: 20px;
  left: 20px;
  z-index: 2;
}

#xeSW8nagutr6 {
  position: absolute;
  background-color: #FF8040;
  width: 150px;
  height: 150px;
  top: 30px;
  left: 30px;
  z-index: 1;
}
```
```html
<div id="d5ESWAchesut"></div>
<div id="S2aKEGaMeswu"></div>
<div id="xeSW8nagutr6"></div>
```
---

![Imgur](http://i.imgur.com/S5v6IzG.png)

<a href="https://jsfiddle.net/vf8euwaa/"><img src="http://i.imgur.com/A9cwqLx.png" width="50"></a>

```css
div {
  background-color: #FF00FF;
  width: 60px;
  height: 60px;
}

p {
  position: relative;
  top: 10px;
  left: 50px;
}
```
```html
<div><p>HelloWorld</p></div>
```

---

<a href="https://jsfiddle.net/r1bhgry3/"><img src="http://i.imgur.com/A9cwqLx.png" width="50"></a>

```css
.w8EpEstevaWr {
  position: fixed;
  bottom: 20px;
  right: 20px;
  width: 100px;
  background-color: red;
}

pre {
  height: 600px;
}
```

```html
<div class="w8EpEstevaWr">HelloWorld</div>

<pre><p> HelloWorld</p><img id="sawezuswePh7" src="http://placehold.it/200x60" alt=""></pre>
<pre><p> HelloWorld</p><img id="sawezuswePh7" src="http://placehold.it/200x60" alt=""></pre>
<pre><p> HelloWorld</p><img id="sawezuswePh7" src="http://placehold.it/200x60" alt=""></pre>
```

**[⬆ Back to Top](#table-of-contents)**

---

<a href="https://jsfiddle.net/dcwnbthk/"><img src="http://i.imgur.com/A9cwqLx.png" width="50"></a>

```css
img {
  position: absolute;
  top: 0px;
  left: 0px;
  z-index: 1;
}
```
```html
<p> HelloWorld</p><img id="sawezuswePh7" src="http://placehold.it/200x60" alt="">
```

<a href="https://jsfiddle.net/b92xasu9/"><img src="http://i.imgur.com/A9cwqLx.png" width="50"></a>

```css
img {
  position: absolute;
  top: 0px;
  left: 0px;
  z-index: -1;
}
```

**[⬆ Back to Top](#table-of-contents)**

---

<a href="https://jsfiddle.net/yaj5n67j/"><img src="http://i.imgur.com/A9cwqLx.png" width="50"></a>

```css
div {
  position: absolute;
  text-align: center;
  width: 120px;
  height: 100px;
  font-family: sans-serif;
}

.redbox1 {
  background-color: red;
  top: 20px;
  left: 20px;
  z-index: -1;
}

.bluebox1 {
  background-color: lightblue;
  top: 50px;
  left: 40px;
  z-index: 1;
}

.redbox2 {
  background-color: red;
  top: 20px;
  left: 180px;
  z-index: 1;
}

.bluebox2 {
  background-color: lightblue;
  top: 50px;
  left: 200px;
  z-index: -1;
}
```

#### :books: 參考網站：
- https://msdn.microsoft.com/zh-tw/library/ms531188.aspx
- [z-index](https://msdn.microsoft.com/zh-tw/library/ee371254(v=expression.40).aspx)

**[⬆ Back to Top](#table-of-contents)**

---

```
<div class="text1">入陣曲</div>
```
```
.text1 {
  color: red;
  text-shadow: 4em 0 0 gray;
}
```

---

<a href="https://jsfiddle.net/5sn6d0hg/"><img src="http://i.imgur.com/A9cwqLx.png" width="50"></a>

```html
<div id="d5ESWAchesut"></div>
<div id="S2aKEGaMeswu"></div>
```
```css
#d5ESWAchesut {
  background-image: url("http://placehold.it/200x60/e3d454/ffffff");
  width: 400px;
  height: 60px;
  border: solid 1px #666699;
}

#S2aKEGaMeswu {
  background-image: url("http://placehold.it/200x60/e3d454/ffffff");
  background-repeat: no-repeat;
  width: 400px;
  height: 60px;
  border: solid 1px #666699;
  margin-top: 10px;
}
```

---

`Normalize.css`<a name="normalize.css"></a>

![](http://necolas.github.io/normalize.css/logo.svg)

```html
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/normalize/5.0.0/normalize.css">
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/normalize/5.0.0/normalize.min.css">
```

#### :books: 參考網站：
- [Normalize.css](http://necolas.github.io/normalize.css/)
- https://cdnjs.com/libraries/normalize
- https://necolas.github.io/normalize.css/latest/normalize.css

```
shell> npm install --save normalize.css
shell> bower install --save normalize-css
```

---

`CSS Reset`<a name="cssreset"></a>

```html
<link rel="stylesheet" href="http://yui.yahooapis.com/3.18.1/build/cssreset/cssreset-min.css">
<link rel="stylesheet" type="text/css" href="http://yui.yahooapis.com/3.18.1/build/cssreset/cssreset-min.css">
```
#### :books: 參考網站：
- [cssreset](http://yuilibrary.com/yui/docs/cssreset/)

---

#### :books: 參考網站：
- [gridbuilder](http://yui.github.io/gridbuilder/)

---

`SVG for Everybody`

#### :books: 參考網站：
- [svg4everybody](https://github.com/jonathantneal/svg4everybody)
- [svg4everybody](https://jonathantneal.github.io/svg4everybody/)

---

#### :books: 參考網站：
- [Materialize](http://materializecss.com/)
- http://getbootstrap.com/
- [Semantic UI](http://semantic-ui.com/)
- http://susy.oddbird.net/

---

<a href="https://jsfiddle.net/u6bsgrt9/"><img src="http://i.imgur.com/A9cwqLx.png" width="50"></a>

```css
@import url(https://fonts.googleapis.com/earlyaccess/notosanstc.css);
@import url(http://fonts.googleapis.com/earlyaccess/notosanstc.css);
* {
  font-family: 'Noto Sans TC', sans-serif;
}
```

---

```css
@charset "UTF-8";
@charset "iso-8859-15";
```

#### :books: 參考網站：
- [@charset](https://developer.mozilla.org/en-US/docs/Web/CSS/@charset)

---

```css
font-family: 'Noto Sans TC', 'Microsoft JhengHei', sans-serif !important;
font-size: 14px;
font-weight: 900;
text-shadow: black 0.01em 0.01em 0.05em !important; 
```

#### :books: 參考網站：
- [text-shadow](https://developer.mozilla.org/en-US/docs/Web/CSS/text-shadow)
- [Microsoft JhengHei](https://www.microsoft.com/typography/fonts/family.aspx?FID=368)
- [Microsoft YaHei](https://www.microsoft.com/typography/fonts/family.aspx?FID=350)

---

#### :books: 參考網站：
- [linear-gradient](https://developer.mozilla.org/en-US/docs/Web/CSS/linear-gradient)

---

<img src="http://i.imgur.com/fiyZJux.png" width="50" alt="Example">

<a href="https://jsfiddle.net/cavbrsed/"><img src="http://i.imgur.com/A9cwqLx.png" width="50"></a>


```html
<ul class="one"> List 1
  <li>List Item 1-1</li>
  <li>List Item 1-2</li>
  <li>List Item 1-3</li>
  <li>List Item 1-4</li>
</ul>
<ul class="two"> List 2
  <li>List Item 2-1</li>
  <li>List Item 2-2</li>
  <li>List Item 2-3</li>
  <li>List Item 2-4</li>
</ul>
<ul class="three"> List 3
  <li>List Item 3-1</li>
  <li>List Item 3-2</li>
  <li>List Item 3-3</li>
  <li>List Item 3-4</li>
</ul>
```

```css
.one {
  list-style:square inside;
}

.two {
  list-style-position: outside;
  list-style-type: circle;
}

.three {
  list-style-image: url("https://mdn.mozillademos.org/files/11979/starsolid.gif");
  list-style-position: inherit;
}
```

#### :books: 參考網站：
- [list-style-position](https://developer.mozilla.org/en-US/docs/Web/CSS/list-style-position)

---

`Pseudo-elements`<a name="pseudo-element"></a>

```css
/* CSS3 syntax */
::after { style properties }

/* CSS2 syntax */
:after { style properties }

p::first-line {font-variant: small-caps;}
p::first-letter {font-weight: bold; font-size: 32pt;}
label::after {content: ": "}  
```

<a href="https://jsfiddle.net/v3wyehnn/"><img src="http://i.imgur.com/A9cwqLx.png" width="50"></a>

**`HTML content`**
```html
<p class="boring-text">Here is some good old boring text.</p>
<p>Here is some moderate text that is neither boring nor exciting.</p>
<p class="exciting-text">Contributing to MDN is easy and fun. Just hit the edit button to add new live samples, or improve existing samples.</p>
```

**`CSS content`**
```css
.exciting-text::after {
  content: "<- now this *is* exciting!";
  color: green;
}

.boring-text::after {
  content: "<- BORING!";
  color: red;
}
```

Example
<a href="https://jsfiddle.net/95fwzqt2/"><img src="http://i.imgur.com/A9cwqLx.png" width="50"></a>

**`CSS content`**
```css
q::before { 
  content: "«";
  color: blue;
}
q::after { 
  content: "»";
  color: red;
}
```

<a href="https://jsfiddle.net/o48bxf8r/"><img src="http://i.imgur.com/A9cwqLx.png" width="50"></a>

**`HTML content`**
```html
<p>Here is the live example of the above code.<br />
  We have some <span data-descr="collection of words and punctuation">text</span> here with a few
  <span data-descr="small popups which also hide again">tooltips</span>.<br />
  Don't be shy, hover over to take a <span data-descr="not to be taken literally">look</span>.
</p>
```

**`CSS content`**
```css
span[data-descr] {
  position: relative;
  text-decoration: underline;
  color: #00F;
  cursor: help;
}

span[data-descr]:hover::after {
  content: attr(data-descr);
  position: absolute;
  left: 0;
  top: 24px;
  min-width: 200px;
  border: 1px #aaaaaa solid;
  border-radius: 10px;
  background-color: #ffffcc;
  padding: 12px;
  color: #000000;
  font-size: 14px;
  z-index: 1;
}
```

#### :books: 參考網站：
- [clear](https://developer.mozilla.org/en-US/docs/Web/CSS/clear)
- [Pseudo-elements](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-elements)
- [::after](https://developer.mozilla.org/en-US/docs/Web/CSS/::after)
- [::before](https://developer.mozilla.org/en-US/docs/Web/CSS/::before)
- [::first-letter](https://developer.mozilla.org/en-US/docs/Web/CSS/::first-letter)
- [::first-line](https://developer.mozilla.org/en-US/docs/Web/CSS/::first-line)

---


### Implementing image sprites in CSS {#Implementing_image_sprites_in_CSS}

```css
.toolbtn {
  background: url(myfile.png);
  display: inline-block;
  height: 20px;
  width: 20px;
}

#btn1 {
  background-position: -20px 0px;
}

#btn2 {
  background-position: -40px 0px;
}

```

```
platform-iphone
<img style="background: url(https://kapeli.com/sprites/platforms/sprite.png); background-position: -3690px 0px; width: 16px; height: 16px; border:none;">

platform-Mac
<img style="background: url(https://kapeli.com/sprites/platforms/sprite.png); background-position: -82px 0px; width: 16px; height: 16px; border:none;">

<img style="background: url(https://kapeli.com/sprites/platforms/sprite.png); background-position: -533px 0px; width: 16px; height: 16px; border:none;">
```


```
https://www-jp.mysql.com/common/themes/sakila/logo-sprite.png
https://kapeli.com/sprites/platforms/sprite.png
```



#### :books: 參考網站：
- [](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Images/Implementing_image_sprites_in_CSS)

---

```css
.button-success,
.button-error,
.button-warning,
.button-secondary {
  color: white;
  border-radius: 4px;
  text-shadow: 0 1px 1px rgba(0, 0, 0, 0.2);
}

.button-success {
  background: rgb(28, 184, 65);   /* this is a green */
}

.button-error {
  background: rgb(202, 60, 60);  /* this is a maroon */
}

.button-warning {
  background: rgb(223, 117, 20);  /* this is an orange */
}

.button-secondary {
  background: rgb(66, 184, 221);  /* this is a light blue */
}
```

```
sm: 'screen and (min-width: 35.5em)', // 568px
md: 'screen and (min-width: 48em)',   // 768px
lg: 'screen and (min-width: 64em)',   // 1024px
xl: 'screen and (min-width: 80em)'    // 1280px
```

`SMARTPHONES`
```css
@media (max-width:480px) { ... }
```

`TABLETS`
```css 
@media (min-width:768px) and (max-width:979px) { ... }
```


`SMARTPHONES TO TABLETS`
```css
@media (max-width:767px) { ... }
```

`DEFAULT`
```css
@media (min-width:980px) { ... }
```

```
@import url(style600min.css) screen and (min-width: 600px);
<link rel="stylesheet" type="text/css" media="screen and (max-device-width: 800px)" href="style800.css" />
```

```css 
.myclass {
  ...
}

.DivClass1 {
  ...
}
```


`Example`


