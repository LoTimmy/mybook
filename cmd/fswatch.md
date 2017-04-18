
```console
shell> brew install fswatch
```

#### :books: 參考網站：
- https://github.com/emcrisostomo/fswatch

---


`inotify-tools`


`inotifywait - wait for changes to files using inotify`


```console
shell> brew install fswatch
```

```
inotifywait
```

最简单的调用是`inotifywait -r -m`，它循环监控参数(`-r`)，并使该实用程序在每个事件(`-m`)之后保持运行：
```console
shell> inotifywait -r -m $HOME
Setting up watches.  Beware: since -r was given, this may take a while!
Watches established.
```

cd $HOME
touch a b c



shell> inotifywait -m -e CLOSE_WRITE $HOME --format "%w%f"  

CLOSE_WRITE

$ inotifywait -m -e close_write /var/alarms --format "%w%f"




#### :books: 參考網站：
- https://www.ibm.com/developerworks/cn/linux/l-ubuntu-inotify/