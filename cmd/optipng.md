`optipng - advanced PNG (Portable Network Graphics) optimizer`

`OptiPNG - Optimize Portable Network Graphics files`


### 安裝 {#installing}

```console
shell> brew install optipng
shell> yum install optipng
shell> apt-get install optipng
```

`-preserve		preserve file attributes if possible`

- **`Preserve`** `[prɪˋzɝv]` `保留` `pre・serve`

```console
shell> optipng file.png
shell> optipng -o7 file.png
shell> optipng file1.png file2.gif file3.tif
shell> optipng -o5 file1.png file2.gif file3.tif
shell> optipng -i1 -o7 -v -full -sim experiment.png
shell> optipng -o7 -f4 -strip all -quiet -preserve file.png 
shell> find . -type f -name "*.png" -exec optipng {} \;
```

---

```console
shell> optipng -strip all file.png
** Error: Lossy operations are not currently supported
```

```console
shell> optipng -v
OptiPNG 0.6.4: Advanced PNG optimizer.
Copyright (C) 2001-2010 Cosmin Truta.

This program is open-source software. See LICENSE for more details.

Portions of this software are based in part on the work of:
  Jean-loup Gailly and Mark Adler (zlib)
  Glenn Randers-Pehrson and the PNG Development Group (libpng)
  Miyasaka Masaru (BMP support)
  David Koblas (GIF support)

Using libpng version 1.2.49 and zlib version 1.2.7
```

#### :books: 參考網站：
- [optipng](http://optipng.sourceforge.net/)
- http://optipng.sourceforge.net/history.txt
