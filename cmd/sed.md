`sed - stream editor for filtering and transforming text`

> `sed` 是十分强大和小巧的文本流编辑器。
> `sed` 是很有用（但常被遗忘）的 `UNIX` 流编辑器。在以批处理方式编辑文件或以有效方式创建 `shell` 脚本来修改现有文件方面，它是十分理想的工具。

`/pattern/`

```

shell> sed -e 'd' /etc/services
shell> sed -e '1d' /etc/services | more
shell> sed -e '1,10d' /etc/services | more
shell> sed -e '/^#/d' /etc/services | more
shell> sed -e '/regexp/d' /path/to/my/test/file | more
shell> sed -n -e '/regexp/p' /path/to/my/test/file | more
shell> sed -n -e '/BEGIN/,/END/p' /my/test/file | more

shell> sed -e 's/$/\r/' myunix.txt > mydos.txt

shell> sed -e 's/foo/bar/' myfile.txt
shell> sed -e 's/foo/bar/g' myfile.txt
shell> sed -e '1,10s/enchantment/entrapment/g' myfile2.txt
shell> sed -e 's:/usr/local:/usr:g' mylist.txt
shell> sed -e 's/<[^>]*>//g' myfile.html

shell> sed -i 's/regexp/replacement/g' myfile.txt
shell> sed -n '5,10p' myfile.txt

shell> sed -i -e 's/regexp/replacement/g' -e 's/str/newstr/' -e '/re/d' myfile.txt

shell> sed -n -f mycommands.sed myfile.txt


shell> cat oldfile | sed -e "s/testpattern/$REPL/g" > newfile
```

`mycommands.sed`
```
1,20{
    s/[Ll]inux/GNU\/Linux/g
    s/samba/Samba/g
    s/posix/POSIX/g
}
```



#### :books: 參考網站：
- [sed](https://www.ibm.com/support/knowledgecenter/ssw_aix_71/com.ibm.aix.cmds5/sed.htm)
- [sed](https://www.ibm.com/support/knowledgecenter/en//ssw_i5_54/rzahz/sed.htm)
- [Sed by example, Part 1](https://www.ibm.com/developerworks/library/l-sed1/)
- [Sed by example, Part 2](https://www.ibm.com/developerworks/library/l-sed2/)
- [Sed by example, Part 3](https://www.ibm.com/developerworks/library/l-sed3/)
- [通用线程 -- sed 实例，第 1 部分](https://www.ibm.com/developerworks/cn/linux/shell/sed/sed-1/)
- [通用线程 -- sed 实例，第 2 部分](https://www.ibm.com/developerworks/cn/linux/shell/sed/sed-2/)
- [通用线程 -- sed 实例，第 3 部分](https://www.ibm.com/developerworks/cn/linux/shell/sed/sed-3/)
- [sed 命令](https://www.ibm.com/support/knowledgecenter/zh/ssw_aix_61/com.ibm.aix.cmds5/sed.htm)