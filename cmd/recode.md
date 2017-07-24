`recode - converts files between character sets`

```console
shell> apt-get install recode
shell> brew install recode
```

```console
shell> recode --list | less
shell> recode UTF-16LE..UTF-8
shell> recode UTF-8..UTF-16LE
shell> recode gb2312..utf8
shell> recode big5..utf8
shell> echo '&deg;' | recode HTML..utf8
```
```console
shell> echo -n 0x02 | recode latin9/x1..dump-with-names
```
