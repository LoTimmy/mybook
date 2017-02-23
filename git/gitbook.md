<!--
<img src="https://avatars0.githubusercontent.com/u/7111340?v=3&s=200" height="30">
-->

<img src="https://www.gitbook.com/assets/images/logo/512-text.png" height="30">

<img src="http://i.imgur.com/VMxh8oX.png" width="200">

> `GitBook` 它基於`Git`建立，並且直接考量技術文件編寫上的各種需求，像是所視即所得的`Markdown`編輯器、也可以自動地將`Markdown`轉換為`PDF`、`ePub`、`mobi`等電子書格式，甚至包辦了出版及販售電子書的相關平臺功能，越來越多開發者選擇在`GitBook`撰寫技術文件，甚至其他領域的使用者也聞風而來，就連現任臺北市長之前在競選時，也運用`GitBook`來發表市政白皮書。

---

### 安裝 {#installing}

```console
shell> npm install -g gitbook-cli
shell> gitbook help

shell> mkdir mybook
shell> cd mybook
shell> gitbook init
shell> gitbook serve
```

### Configuration {#config}

`book.json`

`title`

`description`

`author`

`language`

`plugins`

#### :books: 參考網站：
- https://toolchain.gitbook.com/config.html
- https://toolchain.gitbook.com/plugins/

### GitBook Editor {#editor}

![](https://www.gitbook.com/assets/images/editor/preview_windows.png)

#### :books: 參考網站：
- https://www.gitbook.com/editor
- [windows](https://www.gitbook.com/editor/windows/download)
- [linux](https://www.gitbook.com/editor/linux/download)
- [osx](https://www.gitbook.com/editor/osx/download)

### Plugins {#plugins}

`book.json`

```json
{
  "plugins": ["myPlugin", "anotherPlugin"]
}
```

```json
{
  "plugins": ["advanced-emoji"]
}
```

```json
{
  "plugins": ["youtube", "jsfiddle"]
  "pluginsConfig": {
    "jsfiddle": {
      "type": "script",
      "tabs": ["result", "js", "css", "html", "resources"],
      "height": "500",
      "width": "500",
      "fontColor": "00FF00"
    }
  }
}
```

`youtube`

`{% youtube %}https://www.youtube.com/watch?v=9bZkp7q19f0{% endyoutube %}`

{% youtube %}https://www.youtube.com/watch?v=9bZkp7q19f0{% endyoutube %}

```console
shell> gitbook install
```

`jsfiddle`

```
[source code](https://jsfiddle.net/4o4z6fqn/9/)
```

`search-pro`

```json
{
  "plugins": [
    "-lunr", "-search", "search-pro"
  ]
}
```

`emphasize`

```json
{
  "plugins": ["emphasize"]
}
```

This text is {% em %}highlighted !{% endem %}

This text is {% em %}highlighted with **markdown**!{% endem %}

This text is {% em type="green" %}highlighted in green!{% endem %}

This text is {% em type="red" %}highlighted in red!{% endem %}

This text is {% em color="#ff0000" %}highlighted with a custom color!{% endem %}

```
This text is {% em %}highlighted !{% endem %}

This text is {% em %}highlighted with **markdown**!{% endem %}

This text is {% em type="green" %}highlighted in green!{% endem %}

This text is {% em type="red" %}highlighted in red!{% endem %}

This text is {% em color="#ff0000" %}highlighted with a custom color!{% endem %}
```

`splitter`

```json
{
  "plugins": ["splitter"]
}
```

`tbfed-pagefooter`
```json
{
  "plugins": ["tbfed-pagefooter"],
  "pluginsConfig": {
    "tbfed-pagefooter": {
      "type": "script",
      "copyright": "&copy Taobao FED Team",
      "modify_label": "該檔案修訂時間：",
      "modify_format": "YYYY-MM-DD HH:mm:ss"
    }
  }
}
```

`toggle-chapters`
```json
{
  "plugins": ["toggle-chapters"]
}
```

`plugin-fontsettings`
```json
{
  "plugins": ["-fontsettings"]
}
```

```json
{
  "pluginsConfig": {
    "fontsettings": {
      "theme": 'white', // 'sepia', 'night' or 'white',
      "family": 'sans', // 'serif' or 'sans',
      "size": 1 // 1 - 4
    }
  }
}
```

`cover.jpg`

`cover_small.jpg`

#### :books: 參考網站：
- http://www.ithome.com.tw/voice/95002
- [gitbook](https://www.gitbook.com/)
- [gitbook](https://github.com/GitbookIO/gitbook)
- [gitbook-cli](https://github.com/GitbookIO/gitbook-cli)
- [markdown](https://toolchain.gitbook.com/syntax/markdown.html)
- [toolchain](https://toolchain.gitbook.com/)
- [GitBook.gitignore](https://github.com/github/gitignore/blob/master/GitBook.gitignore)
- [plugins](https://plugins.gitbook.com/)
- [highlight.js](https://highlightjs.org/)
- [advanced-emoji](https://github.com/codeclou/gitbook-plugin-advanced-emoji)
- https://plugins.gitbook.com/plugin/jsfiddle
- https://plugins.gitbook.com/plugin/youtube
- https://plugins.gitbook.com/plugin/search-pro
- https://plugins.gitbook.com/plugin/emphasize
- https://plugins.gitbook.com/plugin/splitter
- https://plugins.gitbook.com/plugin/tbfed-pagefooter
- https://plugins.gitbook.com/plugin/toggle-chapters
- https://github.com/GitbookIO/plugin-fontsettings

