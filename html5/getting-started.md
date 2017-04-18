<img src="http://i.imgur.com/diUQ0Gl.png" width="200">

### Hello world 範例 {#hello-world}

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
</head>
<body>
  Hello World!
</body>
</html>
```

---

> 如果要讓行動裝置呈現最佳的顯示效果，建議您在文件標題中加入中繼檢視區，並且為其指定 `width=device-width, initial-scale=1` 這項參數。

```html
<meta name=viewport content="width=device-width, initial-scale=1">
```

```html
<meta name="format-detection" content="telephone=no">
```

---

### doctype {#doctype}

```html
<!doctype html>
<!DOCTYPE html>
<!DOCTYPE html public "-//W3C//DTD HTML 4.0//en">
<!DOCTYPE html public "-//W3C//DTD HTML 4.0 Strict//en">
<!DOCTYPE html public "-//W3C//DTD HTML 4.0 Transitional//en">
<!DOCTYPE html public "-//W3C//DTD HTML 4.0 Transitional//en" "http://www.w3.org/TR/html4/loose.dtd">
```

#### :books: 參考網站：
- https://msdn.microsoft.com/zh-tw/library/ms535242(v=vs.85).aspx

### html {#html}

```html
<HTML lang="en">
<html lang="en"> </html>
<html lang="en-US"> </html>
<html lang="en-us"> </html>
<html lang="zh-TW"> </html>
<html lang="zh-tw">
<html lang="zh-HK"> </html>
<html lang="zh-CN"> </html>

<html prefix="og: http://ogp.me/ns#">

<head> </head>
<title>Untitled</title>
<title>The Title of the Page</title>
<title>My Web Page</title>
<title>Test Page</title>
```

#### :books: 參考網站：
- https://www.ietf.org/rfc/rfc4646.txt
- https://msdn.microsoft.com/zh-tw/windows/uwp/publish/supported-languages
- https://msdn.microsoft.com/en-us/microsoft-r/jj657969

### script {#script}

```html
<!-- HTML4 and (x)HTML -->
<script type="text/javascript" src="javascript.js"></script>

<!-- HTML5 -->
<script src="javascript.js"></script>
```

```html
<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.3/jquery.min.js"></script>
<script src="//maxcdn.bootstrapcdn.com/bootstrap/3.3.2/js/bootstrap.min.js"></script>
```

```html
<script type="text/javascript">	</script>
<script> </script>
<noscript> </noscript>
<noscript><p class="center">Dropbox 網站需啟用 JavaScript。</p></noscript>    
<script src="//www.google-analytics.com/analytics.js"></script>	
<script src="script.js"></script>	
<script src="/static/javascript/external/zxcvbn.js" type="text/javascript" async></script>	
<script src="/static/javascript/external/zxcvbn.js" type="text/javascript" defer></script>	

<a onclick="alert("Hello world!")" href="javascript:;"></a>
```

#### :books: 參考網站：
- [script](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/script)
- [alert](https://developer.mozilla.org/en-US/docs/Web/API/Window/alert)

### video {#video}

```html
<video width="480" controls poster="https://archive.org/download/WebmVp8Vorbis/webmvp8.gif">
  <source src="https://archive.org/download/WebmVp8Vorbis/webmvp8.webm" type="video/webm">
  <source src="https://archive.org/download/WebmVp8Vorbis/webmvp8_512kb.mp4" type="video/mp4">
  <source src="https://archive.org/download/WebmVp8Vorbis/webmvp8.ogv" type="video/ogg"> Your browser doesn't support HTML5 video tag.
</video>

<video controls>
  <source src="somevideo.webm" type="video/webm">
  <source src="somevideo.mp4" type="video/mp4">
  I'm sorry; your browser doesn't support HTML5 video in WebM with VP8/VP9 or MP4 with H.264.
  <!-- You can embed a Flash player here, to play your mp4 video in older browsers -->
</video>

<video src="assets/launch.m4v" controls webkit-playsinline ad-outlet="video"></video>
```

`WebM`
`video/webm`
`audio/webm`

`Ogg Theora Vorbis`
`audio/ogg`
`video/ogg`
`application/ogg`

```
preload
autoplay
controls
height
width
src
poster
loop
muted
playsinline
```

#### :books: 參考網站：
- [video](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/video)
- [video](https://developer.mozilla.org/en-US/docs/Web/HTML/Supported_media_formats)
- https://developer.apple.com/library/content/documentation/AudioVideo/Conceptual/Using_HTML5_Audio_Video/Introduction/Introduction.html#//apple_ref/doc/uid/TP40009523
- https://developer.apple.com/library/content/documentation/UserExperience/Conceptual/iAdJSProgGuide/PlayingVideosinAds/PlayingVideosinAds.html
- https://msdn.microsoft.com/zh-tw/library/hh924820(v=vs.85).aspx

---

<img src="http://i.imgur.com/tgEkCDP.png" width="200">

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


```css
/* <= 480px */
@media screen and (max-width: 480px) {
  .example {
    font-size: 16pt;
  }
}

/* <= 768px */
@media screen and (max-width: 768px) {
  .example {
    font-size: 20pt;
  }
}

/* 768px ~ 992px */
@media screen and (min-width: 768px) and (max-width: 992px) {
  .example {
    font-size: 40pt;
  }
}

/* >= 1200px */
@media screen and (min-width: 1200px) {
  .example {
    font-size: 40pt;
  }
}

```

`Portrait` `直向`
`Landscape` `橫向`

`iPad`
```css
@media only screen and (min-device-width: 768px) and (max-device-width: 1024px) { ... }
@media only screen and (min-device-width: 768px) and (max-device-width: 1024px) and (orientation: landscape) { ... }
@media only screen and (min-device-width: 768px) and (max-device-width: 1024px) and (orientation: portrait) { ... }
```

`iPad Pro`
```css
@media only screen and (min-device-width: 1024px) and (max-device-width: 1366px) { ... }
@media only screen and (min-device-width: 1024px) and (max-device-width: 1366px) and (orientation: landscape) { ... }
@media only screen and (min-device-width: 1024px) and (max-device-width: 1366px) and (orientation: portrait) { ... }
```

`Retina 顯示器`
```css
@media only screen and (min-device-width: 768px) and (max-device-width: 1024px) and (-webkit-min-device-pixel-ratio: 2) { ... }
@media only screen and (min-device-width: 768px) and (max-device-width: 1024px) and (orientation: landscape) and (-webkit-min-device-pixel-ratio: 2) { ... }
@media only screen and (min-device-width: 768px) and (max-device-width: 1024px) and (orientation: portrait) and (-webkit-min-device-pixel-ratio: 2) { ... }
```

```css
@media only screen and (min-device-width: 768px) and (max-device-width: 1024px) and (-webkit-min-device-pixel-ratio: 1) { ... }
@media only screen and (min-device-width: 768px) and (max-device-width: 1024px) and (orientation: landscape) and (-webkit-min-device-pixel-ratio: 1) { ... }
@media only screen and (min-device-width: 768px) and (max-device-width: 1024px) and (orientation: portrait) and (-webkit-min-device-pixel-ratio: 1) { ... }
```

`iPhone 6 Plus`
```css
@media only screen and (min-device-width: 414px) and (max-device-width: 736px) { ... }
@media only screen and (min-device-width: 414px) and (max-device-width: 736px) and (orientation: landscape) { ... }
@media only screen and (min-device-width: 414px) and (max-device-width: 736px) and (orientation: portrait) { ... }
```

`iPhone 6`
```css
@media only screen and (min-device-width: 375px) and (max-device-width: 667px) { ... }
@media only screen and (min-device-width: 375px) and (max-device-width: 667px) and (orientation: landscape) { ... }
@media only screen and (min-device-width: 375px) and (max-device-width: 667px) and (orientation: portrait) { ... }
```

`iPhone 5`
```css
@media only screen and (min-device-width: 320px) and (max-device-width: 568px) { ... }
@media only screen and (min-device-width: 320px) and (max-device-width: 568px) and (orientation: landscape) { ... }
@media only screen and (min-device-width: 320px) and (max-device-width: 568px) and (orientation: portrait) { ... }
```

`iPhone 4`
```css
@media only screen and (min-device-width: 320px) and (max-device-width: 480px) { ... }
@media only screen and (min-device-width: 320px) and (max-device-width: 480px) and (orientation: landscape) { ... }
@media only screen and (min-device-width: 320px) and (max-device-width: 480px) and (orientation: portrait) { ... }
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

#### :books: 參考網站：
- https://developers.google.com/speed/docs/insights/ConfigureViewport
- https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries
- https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Grids


```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>Document</title>

    <link href="//getbootstrap.com/dist/css/bootstrap.min.css" rel="stylesheet">

    <!--[if lt IE 9]>
      <script src="//oss.maxcdn.com/html5shiv/3.7.2/html5shiv.min.js"></script>
      <script src="//oss.maxcdn.com/respond/1.4.2/respond.min.js"></script>
    <![endif]-->
  </head>
  <body>
    <h1>Hello, world!</h1>

    <script src="//ajax.googleapis.com/ajax/libs/jquery/1.11.3/jquery.min.js"></script>
    <script src="//getbootstrap.com/dist/js/bootstrap.min.js"></script>
  </body>
</html>
```

---

```html
<div id="resizable">
  <div id="items">
    <div>1</div>
    <div>2</div>
    <div>3</div>
    <div>4</div>
    <div>5</div>
  </div>
</div>
```

```css
#resizable {
  border: 1px dashed green;
  min-width: 100px;
  height: 150px;
}

#items div {
  border: 1px solid black;
  background: yellow;
  margin: .3em;
  width: 80px;
  text-align: center;
  float: left;
}

img {
  /* width: 60px; */
  max-width: 100%;
  height: auto;
}
```

`Fluid` `流體` `[ˋfluɪd]` `flu・id`
