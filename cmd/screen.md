`screen - terminal multiplexer with VT100/ANSI terminal emulation`

卸離 (Detach)

<kbd>Ctrl</kbd>+<kbd>a</kbd> <kbd>d</kbd>

Create

<kbd>Ctrl</kbd>+<kbd>a</kbd> <kbd>c</kbd>

Next

<kbd>Ctrl</kbd>+<kbd>a</kbd> <kbd>n</kbd>

前一 (Previous)

<kbd>Ctrl</kbd>+<kbd>a</kbd> <kbd>p</kbd>


```console
shell> apt-get install screen
shell> screen
shell> screen -d -m aria2c http://example.org/mylinux.torrent
shell> screen -r
shell> screen -ls
shell> screen -d -S foo -m bash -c ""
```

---

`.screenrc`

```
hardstatus on
hardstatus alwayslastline
hardstatus string "%{.bW}%-w%{.rW}%n %t%{-}%+w %=%{..G} %H %{..Y} %m/%d %C%a "
```
---

#### :books: 參考網站：
- [screen](https://www.gnu.org/software/screen/)
- [screen](https://www.gnu.org/software/screen/manual/screen.html)
- [对话 UNIX: 使用 Screen 创建并管理多个 shell](https://www.ibm.com/developerworks/cn/aix/library/au-gnu_screen/)
