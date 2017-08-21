- http://rubyinstaller.org/downloads/

<img src="http://i.imgur.com/WQ9Fm38.png" width="200">

<img src="https://cdn.rubyinstaller.org/images/logo.png" width="200">

> `Compass` 是開放原始碼 `CSS` 撰寫架構，可讓您使用 `Sass` 來建立 `CSS3` 樣式表。

```
shell> gem update --system
shell> gem install compass

shell> compass create <myproject>
shell> compass create
```
```
directory css/
directory sass/
   create sass/screen.scss
   create sass/print.scss
   create sass/ie.scss
    write css/ie.css
    write css/print.css
    write css/screen.css

*********************************************************************
Congratulations! Your compass project has been created.

You may now add and edit sass stylesheets in the sass subdirectory of your project.

Sass files beginning with an underscore are called partials and won't be
compiled to CSS, but they can be imported into other sass stylesheets.

You can configure your project by editing the config.rb configuration file.

You must compile your sass stylesheets into CSS when they change.
This can be done in one of the following ways:
  1. To compile on demand:
     compass compile [path/to/project]
  2. To monitor your project for changes and automatically recompile:
     compass watch [path/to/project]

More Resources:
  * Website: http://compass-style.org/
  * Sass: http://sass-lang.com
  * Community: http://groups.google.com/group/compass-users/


To import your new stylesheets add the following lines of HTML (or equivalent) to your webpage:
<head>
  <link href="/css/screen.css" media="screen, projection" rel="stylesheet" type="text/css" />
  <link href="/css/print.css" media="print" rel="stylesheet" type="text/css" />
  <!--[if IE]>
      <link href="/css/ie.css" media="screen, projection" rel="stylesheet" type="text/css" />
  <![endif]-->
</head>
```

```
shell> compass version
```

```
Compass 1.0.3 (Polaris)
Copyright (c) 2008-2016 Chris Eppstein
Released under the MIT License.
Compass is charityware.
Please make a tax deductable donation for a worthy cause: http://umdf.org/compass
```

```
shell> cd /path/to/project
shell> compass watch

shell> compass compile [path/to/project]
shell> compass watch [path/to/project]

shell> compass compile --production
shell> compass compile --output-style compressed --force

shell> cp config.rb prod_config.rb
shell> compass compile -c prod_config.rb --force

shell> compass compile --force
```

---

`config.rb`

```
http_path = "/"
css_dir = "stylesheets"
sass_dir = "sass"
images_path = "images"
javascripts_dir = "javascripts"

environment = :development
environment = :production

output_style = :expanded
output_style = :compressed
output_style = :nested
output_style = :compact
output_style = (environment == :production) ? :compressed : :expanded

line_comments = false

css_dir = "css"
javascripts_dir = "js"
images_path = "images"
```
#### :books: 參考網站：
- http://compass-style.org/help/documentation/configuration-reference/
- http://compass-style.org/help/documentation/command-line/
- http://compass-style.org/help/tutorials/production-css/

---

```html
<head>
  <link href="/stylesheets/screen.css" media="screen, projection" rel="stylesheet" type="text/css" />
  <link href="/stylesheets/print.css" media="print" rel="stylesheet" type="text/css" />
  <!--[if IE]>
      <link href="/stylesheets/ie.css" media="screen, projection" rel="stylesheet" type="text/css" />
  <![endif]-->
</head>
```


---

```sass
@import "compass";

@import "compass/reset";

@import "compass/support"
@import "compass/layout"

@import "compass/utilities";
@import "compass/utilities/tables";


@import "compass/css3";
@import "compass/css3.scss";

@import "compass/css3/text-shadow";
```

```sass
@include text-shadow(white 1px 1px 4px);
@include text-shadow(rgba(blue, 0.2) 1px 1px 0, rgba(blue, 0.2) 2px 2px 0, rgba(blue, 0.2) 3px 3px 0);


@include border-radius(25px);
@include border-top-left-radius(25px);
@include border-top-right-radius(25px);
@include border-bottom-left-radius(25px);
@include border-bottom-right-radius(25px);
@include border-top-radius(25px);
@include border-bottom-radius(25px);
@include border-left-radius(25px);
@include border-right-radius(25px);
@include border-corner-radius(top, left, 40px);
@include border-corner-radius(top, right, 5px);
@include border-corner-radius(bottom, left, 15px);
@include border-corner-radius(bottom, right, 30px);

@include box-sizing(content-box);
@include box-sizing(border-box);

@include font-face("Blooming Grove", font-files("examples/bgrove.ttf", "examples/bgrove.otf"));

 
.simple   { @include border-radius(4px, 4px); }
.compound { @include border-radius(2px 5px, 3px 6px); }
.crazy    { @include border-radius(1px 3px 5px 7px, 2px 4px 6px 8px)}

#box-shadow-custom {
  @include box-shadow(red 2px 2px 10px);
}

```

#### :books: 參考網站：
- http://compass-style.org/examples/compass/css3/box_shadow/
- http://compass-style.org/reference/compass/css3/border_radius/

---

#### :books: 參考網站：
- http://compass-style.org/install/
