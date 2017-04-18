<img src="http://i.imgur.com/LyBWs0l.png" width="200">

---

```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>accordion demo</title>
  <link rel="stylesheet" href="//code.jquery.com/ui/1.12.1/themes/smoothness/jquery-ui.css">
  <script src="//code.jquery.com/jquery-1.12.4.js"></script>
  <script src="//code.jquery.com/ui/1.12.1/jquery-ui.js"></script>
</head>
<body>
 
<div id="accordion">
  <h3>Section 1</h3>
  <div>
    <p>Mauris mauris ante, blandit et, ultrices a, suscipit eget.
    Integer ut neque. Vivamus nisi metus, molestie vel, gravida in,
    condimentum sit amet, nunc. Nam a nibh. Donec suscipit eros.
    Nam mi. Proin viverra leo ut odio.</p>
  </div>
  <h3>Section 2</h3>
  <div>
    <p>Sed non urna. Phasellus eu ligula. Vestibulum sit amet purus.
    Vivamus hendrerit, dolor aliquet laoreet, mauris turpis velit,
    faucibus interdum tellus libero ac justo.</p>
  </div>
  <h3>Section 3</h3>
  <div>
    <p>Nam enim risus, molestie et, porta ac, aliquam ac, risus.
    Quisque lobortis.Phasellus pellentesque purus in massa.</p>
    <ul>
      <li>List item one</li>
      <li>List item two</li>
      <li>List item three</li>
    </ul>
  </div>
</div>
 
<script>
  $( "#accordion" ).accordion();
</script>
 
</body>
</html>
```

---

```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>jQuery UI Resizable - Default functionality</title>
  <link rel="stylesheet" href="//code.jquery.com/ui/1.12.1/themes/base/jquery-ui.css">
  <link rel="stylesheet" href="/resources/demos/style.css">
  <style>
  #resizable { width: 150px; height: 150px; padding: 0.5em; }
  #resizable h3 { text-align: center; margin: 0; }
  </style>
  <script src="https://code.jquery.com/jquery-1.12.4.js"></script>
  <script src="https://code.jquery.com/ui/1.12.1/jquery-ui.js"></script>
  <script>
  $( function() {
    $( "#resizable" ).resizable();
  } );
  </script>
</head>
<body>
 
<div id="resizable" class="ui-widget-content">
  <h3 class="ui-widget-header">Resizable</h3>
</div>
 
 
</body>
</html>
```

#### :books: 參考網站：
- [jqueryui](http://jqueryui.com/)


