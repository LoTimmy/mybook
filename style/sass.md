<img src="https://pbs.twimg.com/profile_images/583681608269471744/jCR2zNJV_400x400.png" width="200">

```
shell> brew install rbenv ruby-build
```
```
export RBENV_ROOT=/usr/local/var/rbenv
eval "$(rbenv init -)"
```

```
shell> rbenv install 2.3.3
shell> rbenv global 2.3.3
shell> ruby -v

shell> gem update --system
shell> gem install sass

shell> sass input.scss output.css

shell> sass --style nested input.scss output.css
shell> sass --style compact input.scss output.css
shell> sass --style compressed input.scss output.css
shell> sass --style expanded input.scss output.css

shell> sass --watch input.scss:output.css
shell> sass --watch app/sass:public/stylesheets

# Convert Sass to SCSS
shell> sass-convert style.sass style.scss

# Convert SCSS to Sass
shell> sass-convert style.scss style.sass

shell> sass-convert style.css style.scss
```
---

#### Variables

```sass
$font-stack:    Helvetica, sans-serif;
$primary-color: #333;

body {
  font: 100% $font-stack;
  color: $primary-color;
}
```

```css
body {
  font: 100% Helvetica, sans-serif;
  color: #333;
}
```
---

#### Nesting

```sass
nav {
  ul {
    margin: 0;
    padding: 0;
    list-style: none;
  }

  li { display: inline-block; }

  a {
    display: block;
    padding: 6px 12px;
    text-decoration: none;
  }
}
```

```css
nav ul {
  margin: 0;
  padding: 0;
  list-style: none;
}

nav li {
  display: inline-block;
}

nav a {
  display: block;
  padding: 6px 12px;
  text-decoration: none;
}
```
---

`_reset.scss`
```sass
// _reset.scss

html,
body,
ul,
ol {
   margin: 0;
  padding: 0;
}
```
`base.scss`
```sass
// base.scss

@import 'reset';

body {
  font: 100% Helvetica, sans-serif;
  background-color: #efefef;
}
```

```css
html, body, ul, ol {
  margin: 0;
  padding: 0;
}

body {
  font: 100% Helvetica, sans-serif;
  background-color: #efefef;
}
```
---
```sass
@mixin border-radius($radius) {
  -webkit-border-radius: $radius;
     -moz-border-radius: $radius;
      -ms-border-radius: $radius;
          border-radius: $radius;
}

.box { @include border-radius(10px); }
```
```css
.box {
  -webkit-border-radius: 10px;
  -moz-border-radius: 10px;
  -ms-border-radius: 10px;
  border-radius: 10px;
}
```
---
```sass
.message {
  border: 1px solid #ccc;
  padding: 10px;
  color: #333;
}

.success {
  @extend .message;
  border-color: green;
}

.error {
  @extend .message;
  border-color: red;
}

.warning {
  @extend .message;
  border-color: yellow;
}
```

```css
.message, .success, .error, .warning {
  border: 1px solid #cccccc;
  padding: 10px;
  color: #333;
}

.success {
  border-color: green;
}

.error {
  border-color: red;
}

.warning {
  border-color: yellow;
}
```
---

```sass
.container { width: 100%; }

article[role="main"] {
  float: left;
  width: 600px / 960px * 100%;
}

aside[role="complementary"] {
  float: right;
  width: 300px / 960px * 100%;
}

```
```css
.container {
  width: 100%;
}

article[role="main"] {
  float: left;
  width: 62.5%;
}

aside[role="complementary"] {
  float: right;
  width: 31.25%;
}
```

---

#### :books: 參考網站：
- http://sass-lang.com/
- http://sass-lang.com/guide
- http://sass-lang.com/documentation/file.SASS_REFERENCE.html
- https://github.com/gruntjs/grunt-contrib-sass
- http://bourbon.io/
---


```sass
header {
  position: relative;
  width: 100%;
  min-height: auto;
  overflow-y: hidden;
  background: url("../img/bg-pattern.png"), #7b4397;
  /* fallback for old browsers */
  background: url("../img/bg-pattern.png"), -webkit-linear-gradient(to left, #7b4397, #dc2430);
  /* Chrome 10-25, Safari 5.1-6 */
  background: url("../img/bg-pattern.png"), linear-gradient(to left, #7b4397, #dc2430);
  /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */
  color: white;

  .header-content {
    text-align: center;
    padding: 150px 0 50px;
    position: relative;
  }

  .header-content .header-content-inner {
    position: relative;
    max-width: 500px;
    margin: 0 auto;
  }
}
```

---

```sass
$font-size: 20px;

@mixin background() {
  background: yellow;
  font-size: 20px;
}

.header {
  @include background;
}

.footer {
  @include background;
}

```

```
.header {
  background: yellow;
  font-size: 20px; }

.footer {
  background: yellow;
  font-size: 20px; }
```
---

```sass
invert($color)
mix($color1, $color2)
lighten($color, $amount)
darken($color, $amount)



mix(#f00, #00f) => #7f007f
mix(#f00, #00f, 25%) => #3f00bf

lighten(#800, 20%) => #e00
darken(#800, 20%) => #200

```

#### :books: 參考網站：
- http://sass-lang.com/documentation/Sass/Script/Functions.html