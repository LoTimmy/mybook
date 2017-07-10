- `Bash Shell`為`UNIX`的殼層程式，不但是`GNU`作業系統的殼層程式，也是`Linux`及`Mac OS X`的預設殼層程式，算是各種`Linux`版本上最常見的公用程式。它採用命令列介面，允許使用者輸入文字命令，也可讓使用者遠端下達指令（如透過`ssh`或` telnet`）。
- `Bash`是一個指令列`shell` （殼層）程式，廣泛存在於 `Linux`、`BSD` 和 `Mac OS X` 等`UNIX-based`的作業系統，使用者只要將指令輸入到一個簡單的文字式視窗，作業系統便會依指令運作。

---
```console
shell> foo='() { echo not patched; }' bash -c foo
```

```console
shell> env x='() { :;}; echo vulnerable' bash -c "echo this is a test"
```

```sh
# for name [ [ in [ word ... ] ] ; ] do list ; done

for seq in 1 2 3 4 5 6 7 8 9 10; do
  echo $seq
done

for seq in 1 2 3 4 5 6 7 8 9 10; do
  printf "%03d\n" $seq
done

for seq in $(seq 1 2 20); do
  echo $seq
done

# for (( expr1 ; expr2 ; expr3 )) ; do list ; done
for (( i=1; i<=5; i++ )); do
  echo $seq
done

# 無限迴圈
for (( ; ; )); do
  echo "Hello World!"
done
 
```
---

```
((expression))
expression1 && expression2
[[ expression ]]

-eq
-ne
-lt
-le
-gt
-ge
  
```

```sh
#!/bin/bash
while true
do
  echo "$(date +"%Y-%m-%d %T") $(netstat -ntap | grep 46998 | grep ESTABLISHED | wc -l)" | tee -a LogFile
  sleep 2
done
```

```sh
#!/bin/bash

i=1
while [ $i -le 5 ]
do
  echo $i
  (( i++ ))
done
```


```sh
while read line ; do
  # echo $line
  printf "%2d\n" $line
  printf "%.2f\n" $line  
done < <(cat /samples/comics.lst)
```

```sh
IFS=':'
while read name junk junk1 junk2 junk3
do
  echo $name
done </samples/comics.lst
```

#### :books: 參考網站：
- https://www.ibm.com/support/knowledgecenter/SSLTBW_1.13.0/com.ibm.zos.r13.bpxa500/read.htm
- https://www.ibm.com/support/knowledgecenter/zh/ssw_aix_71/com.ibm.aix.cmds4/read.htm


```sh
RAM_SIZE=$(free -b | grep Mem | awk '{print $2}')
HOSTNAME=`/bin/hostname -f`

uname -m | grep 64
IS_64BIT=$?
#BIT_WIDTH=64
BIT_WIDTH=32
CONNTRACK_MAX=$(($RAM_SIZE / 16384 * 32 / $BIT_WIDTH))

echo $IS_64BIT
echo $CONNTRACK_MAX
echo $RAM_SIZE
echo $RANDOM

echo My home directory is $HOME
echo "My current directory is $PWD"
```

---
```sh
#!/bin/bash

ip=$(curl -s https://api.ipify.org)
echo "My public IP address is: $ip"
```

#### :books: 參考網站：
- [ipify](https://www.ipify.org/)

---

```sh
#!/bin/bash
if COMMANDS; then COMMANDS;
else COMMANDS;
fi
```

---

```
# You may uncomment the following lines if you want `ls' to be colorized:
export LS_OPTIONS='--color=auto'
eval "`dircolors`"
alias ls='ls $LS_OPTIONS'
alias ll='ls $LS_OPTIONS -l'
alias l='ls $LS_OPTIONS -lA'

# Some more alias to avoid making mistakes:
# alias rm='rm -i'
# alias cp='cp -i'
# alias mv='mv -i'
```

```
# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi
```

---
`daemon - turns other processes into daemons`

### 安裝 {#installing}
```console
shell> sudo apt-get install daemon
shell> daemon -r ./test.sh
```

`test.sh`

```sh
#!/bin/bash

# 無限迴圈
while true; do
  echo "$(date +"%Y-%m-%d %T") > /dev/shm/date.txt 
  sleep 2
done
```

```console
shell> start-stop-daemon --start --background --exec /root/test.sh
shell> start-stop-daemon --stop --name test.sh
```

#### :books: 參考網站：
- https://www.ibm.com/developerworks/cn/linux/l-cn-nohup/
- http://manpages.ubuntu.com/manpages/zesty/en/man8/start-stop-daemon.8.html

---

`-n     do not output the trailing newline`

`-e     enable interpretation of backslash escapes`

`\r     carriage return`

`Carriage Return`
`歸位字元`
`↵`

```sh
#!/bin/bash

echo -ne '#####                     (33%)\r'
sleep 1
echo -ne '#############             (66%)\r'
sleep 1
echo -ne '#######################   (100%)\r'
echo -ne '\n'
```
---

```
export HISTCONTROL='ignoredups'
```

```console
shell> dpkg --print-architecture
```

---

#### :books: 參考網站：
- [Unix /Linux 的Bash Shell 出現重大漏洞，危險等級可能超越 Heartbleed](http://www.ithome.com.tw/news/91107)
- [Bash 漏洞已出現攻擊行動，又傳出修補後仍有漏洞！](http://www.ithome.com.tw/news/91148)
- [Bash 漏洞連環爆：第二波修補還未完，第三波漏洞又來襲！](http://www.ithome.com.tw/news/91233)
- [Linux大廠二度釋出Shellshock漏洞的修補程式！](http://www.ithome.com.tw/news/91180)
- https://www.gnu.org/software/bash/manual/html_node/Bash-Variables.html
