`rename - renames multiple files`

```console
shell> brew install rename
shell> rename 's/\.bak$//' *.bak
shell> rename 'y/A-Z/a-z/' *

shell> rename IMG img *.jpg
shell> rename .html .htm *.html

shell> rename 's/$/.sh/' filename
shell> rename 's/$/.bak/' filename

shell> rename --keep-extension --expr '$_ = "NewName"' OldName.txt
```

#### :books: 參考網站：
- [rename](http://manpages.ubuntu.com/manpages/xenial/man1/rename.ul.1.html)


