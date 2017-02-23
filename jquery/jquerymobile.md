
```html
<link rel="stylesheet" href="http://code.jquery.com/mobile/1.4.5/jquery.mobile-1.4.5.min.css" />
<script src="http://code.jquery.com/jquery-1.11.1.min.js"></script>
<script src="http://code.jquery.com/mobile/1.4.5/jquery.mobile-1.4.5.min.js"></script>
```
```
http://ajax.googleapis.com/ajax/libs/jquerymobile/1.4.5/jquery.mobile.js
http://ajax.googleapis.com/ajax/libs/jquerymobile/1.4.5/jquery.mobile.min.js
http://ajax.googleapis.com/ajax/libs/jquerymobile/1.4.5/jquery.mobile.css
http://ajax.googleapis.com/ajax/libs/jquerymobile/1.4.5/jquery.mobile.min.css
```
---

```html
<!doctype html>
<html>
<head>
  <title>Multipage example</title>
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <link rel="stylesheet" href="//code.jquery.com/mobile/1.4.5/jquery.mobile-1.4.5.min.css" />
  <script src="//code.jquery.com/jquery-1.10.2.min.js"></script>
  <script src="//code.jquery.com/mobile/1.4.5/jquery.mobile-1.4.5.min.js"></script>
</head>
<body>
  <div data-role="page" id="page1">
    <div data-role="header">
      <h1>Page 1</h1>
    </div>
    <div role="main" class="ui-content">
      <a href="#page2" data-transition="slide" class="ui-btn ui-corner-all ui-btn-inline">Go To Page 2</a>
    </div>
  </div>
  <div data-role="page" id="page2">
    <div data-role="header">
      <h1>Page 2</h1>
    </div>
    <div role="main" class="ui-content">
      <a href="#page1" data-rel="back" data-transition="slide" class="ui-btn ui-corner-all ui-btn-inline">Go Back To Page 1</a>
    </div>
  </div>
</body>
</html>
```
---

```html
<!doctype html>
<html>

  <head>
    <title></title>
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <link rel="stylesheet" href="//code.jquery.com/mobile/1.4.5/jquery.mobile-1.4.5.min.css" />
    <script src="//code.jquery.com/jquery-1.10.2.min.js"></script>
    <script src="//code.jquery.com/mobile/1.4.5/jquery.mobile-1.4.5.min.js"></script>
    <style>
      .kaguretrA48e {
        position: relative;
        padding-bottom: 56.25%;
        height: 0;
        overflow: hidden;
        width: 100%;
        height: auto;
      }

      .kaguretrA48e iframe {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
      }
    </style>
  </head>

  <body>
    <div class="kaguretrA48e">
      <iframe width="1280" height="720" src="https://www.youtube.com/embed/yk2CUjbyyQY?list=PLj7CmGWxRE8RIpxvAB7iBEWz3-VcwOirm&autoplay=1&controls=0&showinfo=0" frameborder="0" allowfullscreen></iframe>
    </div>

  </body>
</html>

```

#### :books: 參考網站：
- http://jquerymobile.com/download/
- https://api.jquerymobile.com/pagecontainer/