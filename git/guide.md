
<img src="http://i.imgur.com/2V2g0Sx.png" width="500">

<img src="http://i.imgur.com/unRQXHr.png" width="500">

<img src="http://i.imgur.com/UAfIe37.png" width="300">

<img src="http://i.imgur.com/pf5uNCz.png" width="300">

<img src="http://i.imgur.com/Z6gnVPv.png" width="300">

<img src="http://i.imgur.com/eBmGfJb.png" width="300">


```console
shell> mkdir helloworld 
shell> git init
shell> edit hello.c
shell> git add hello.c
shell> git status
shell> git commit -m "initial commit" --author "A U Thor <author@example.com>"
shell> git log
shell> git commit --amend -m "Initial commit" --author "A U Thor <author@example.com>"
shell> git log
```

```console
shell> git add .
shell> git commit -m "initial revision"
```

- **`Revision`** `[rɪˋvɪʒən]` `修訂` `re・vi・sion`
- **`Initial`** `[ɪˋnɪʃəl]` `初始` `起始` `i・ni・tial`
- **`Commit`** `[kəˋmɪt]` `認可` `交付` `確認` `com・mit`

#### :books: 參考網站：
- [git-log](https://git-scm.com/docs/git-log)
- [git-init](https://git-scm.com/docs/git-init)
- [git-add](https://git-scm.com/docs/git-add)
- [git-status](https://git-scm.com/docs/git-status)
- [git-commit](https://git-scm.com/docs/git-commit)

---

```console
shell> git config -l
shell> git config --system -l
shell> git config --global -l
shell> git config --local -l

shell> git config --system user.name "Your Name"
shell> git config --system user.email you@example.com

shell> git config --global user.name "Your Name"
shell> git config --global user.email you@example.com
shell> git config --global color.ui true
shell> git config --global push.default simple

shell> git config --local user.name "Your Name"
shell> git config --local user.email you@example.com
shell> git config --local color.ui true

shell> git config --unset user.name

shell> git config --global --edit
shell> git commit --amend --reset-author
```

```console
shell> git config --global user.name "Your Name"
shell> git config --global user.email you@example.com
shell> git config --global color.ui true
```

#### :books: 參考網站：
- [git-config](https://git-scm.com/docs/git-config)

---

```console
shell> mkdir helloworld 
shell> git init
shell> edit hello.c
shell> edit hello.h
shell> git add .
shell> git status

shell> git rm --cached hello.h
shell> git status 
```

#### :books: 參考網站：
- [git-rm](https://git-scm.com/docs/git-rm)

---

```
shell> git show --pretty="" --name-only de05672
shell> git ls-tree --name-only HEAD
```

```console
shell> mkdir helloworld 
shell> git init
shell> edit hello.c
shell> edit hello.h
shell> git add .
shell> git commit -m "initial revision"
shell> git log --pretty=oneline --abbrev-commit

810801f initial revision

shell> git ls-tree --name-only HEAD
shell> git ls-tree --name-only 810801f

shell> git rm --cached hello.h
shell> git commit --amend -C HEAD
shell> git ls-tree --name-only HEAD
```

#### :books: 參考網站：
- [git-reset](https://git-scm.com/docs/git-reset)
- [git-ls-tree](https://git-scm.com/docs/git-ls-tree)

---

```console
shell> git filter-branch --tree-filter 'rm filename' HEAD
```

#### :books: 參考網站：
- [git-filter-branch](https://git-scm.com/docs/git-filter-branch)

---

```console
shell> edit hello.c hello.h
shell> git add hello.c
shell> git status
shell> touch .gitignore
shell> edit .gitignore
shell> git commit -m "My changes"
shell> git log
```

`.gitignore`
```
.gitignore

# This is a comment

# Ignore the file test.md
test.md

# Ignore everything in the directory "bin"
bin/*

*.h
```

#### :books: 參考網站：
- [gitignore](https://git-scm.com/docs/gitignore)
- [ignoring-files](https://help.github.com/articles/ignoring-files/)

---

```console
shell> rm -f hello.c
shell> git checkout hello.c
```

```console
shell> git checkout -- '*.c'
```

```console
shell> git checkout -- *
shell> git checkout -- hello.c
```

```console
shell> edit hello.c
shell> git add hello.c
shell> git commit -m "initial revision"

shell> edit hello.c
shell> git add hello.c
shell> git commit -m "My changes"

shell> edit hello.c
shell> git log --pretty=oneline
53ae079ba38047b2d8709c42e1ef88705e497936 My changes
0a717d53efd86893b1bf47c7c7a43135ea3279d6 initial revision

shell> git checkout 0a71 hello.c
```


#### :books: 參考網站：
- [git-checkout](https://git-scm.com/docs/git-checkout)

---

```console
shell> git add .
```

```
warning: CRLF will be replaced by LF in myfile.txt.
The file will have its original line endings in your working directory.
```

```console
shell> git config --global core.autocrlf
shell> git config --global core.autocrlf input
shell> git config --global core.autocrlf true
shell> git config --global core.autocrlf false
```

```
shell> git config --global core.eol
```

```console
shell> echo "* text=auto" >.gitattributes
```

`.gitattributes`
```
* text=auto

*.txt text
*.vcproj text eol=crlf
*.sh text eol=lf
*.jpg -text
*.jpg -text -diff

*.md text eol=lf
*.markdown text eol=lf

*.c	filter=indent

manual.pdf	-text
weirdchars.txt	text
```

#### :books: 參考網站：
- [gitattributes](https://git-scm.com/docs/gitattributes)

---

```console
shell> edit hello.c
shell> git add hello.c
shell> git rm hello.c
shell> git rm --cached hello.c
shell> git reset HEAD hello.c
```

```
shell> git reset HEAD^
shell> git reset HEAD^ --hard
```

#### :books: 參考網站：
- [git-reset](https://git-scm.com/docs/git-reset)
- [git-rm](https://git-scm.com/docs/git-rm)

---

```console
shell> bfg --no-blob-protection --delete-files YOUR-FILE-WITH-SENSITIVE-DATA
```

```console
shell> bfg --no-blob-protection --delete-files id_{dsa,rsa}  my-repo.git
```

```console
shell> git reflog expire --expire=now --all && git gc --prune=now --aggressive
```


```console
shell> git clone --bare https://github.com/you/HelloWorld.git HelloWorld.git
shell> bfg --no-blob-protection --delete-files id_{dsa,rsa} HelloWorld.git
```


#### :books: 參考網站：
- [remove-sensitive-data](https://help.github.com/articles/remove-sensitive-data/)
- [bfg](https://rtyley.github.io/bfg-repo-cleaner/)

---


```console
shell> git log --pretty=oneline
shell> git log --pretty=oneline --abbrev-commit
shell> git remote add origin YOUR_GIT_CLONE_URL_HERE
shell> git remote add origin https://github.com/you/HelloWorld.git
```

#### :books: 參考網站：
- [changing-a-remote-s-url](https://help.github.com/articles/changing-a-remote-s-url/)

---

```console
shell> git add -A
shell> git add .
shell> git add -u
```

---

```console
shell> mkdir helloworld 
shell> git init
shell> git add .
shell> git commit -m "initial commit"
shell> git remote add azure [URL for remote repository]
shell> git push azure master
```
---

```console
shell> mkdir HelloWorld
shell> cd HelloWorld
shell> git init
shell> echo HelloWorld > testfile.txt
shell> git status

shell> git add . -n
shell> git add .

shell> git status
shell> git commit -a
shell> git log
shell> git commit -a -m "Initial commit"
shell> git commit -m "Demo"
shell> git commit -m "My changes"
shell> git commit -am "disable node_modules cache" --allow-empty
shell> git push heroku master

shell> git add package.json
shell> git commit -m "Added package.json"

shell> git diff HEAD testfile.txt  
shell> git show

shell> git diff 0fcd2baef5b6741412db6eb3bd2c2b559a02b64f fd7f63f055f2e6ecc23be1a9a3b33a438ae68ead

shell> git remote add origin https://username@your-azure-website.scm.azurewebsites.net:443/your-azure-website.git
shell> git push
```


```
shell> git show --pretty="" --name-only HEAD
shell> git show --pretty="" --name-only HEAD~1
shell> git show --pretty="" --name-only HEAD~2
shell> git show HEAD:testfile.txt
shell> git show HEAD:testfile.txt> testfile.txt 
```

```
Aborting commit due to empty commit message.
```
- **`Aborting`** `正在中止`
- **`Empty`** `[ˋɛmptɪ]` `空的` `空` `空白` `emp・ty`


```console
shell> git clone --bare HelloWorld HelloWorld.git
shell> scp -r HelloWorld.git user@git.example.com:/opt/git
shell> git clone user@git.example.com:/opt/git/HelloWorld.git

shell> git remote -v
shell> git push origin master
shell> git remote set-url origin user@git.example.com:/opt/git/HelloWorld.git
shell> git remote show origin
```

```console
shell> git remote add azure https://username@your-azure-website.scm.azurewebsites.net:443/your-azure-website.git
shell> git push azure master
```

---
```console
shell> mkdir HelloWorld.git
shell> cd HelloWorld.git
shell> git init --bare
```

```console
shell> mkdir HelloWorld
shell> cd HelloWorld
shell> git init
shell> echo HelloWorld > testfile.txt
shell> git commit -a -m "Initial commit"
shell> git commit -a -m "My changes"

shell> git remote add origin /opt/git/HelloWorld.git
shell> git push origin master
```

```console
shell> git clone /opt/git/HelloWorld.git
```

```console
shell> git clone user@git.example.com:/opt/git/HelloWorld.git

shell> git remote set-url origin user@git.example.com:/opt/git/HelloWorld.git
shell> git remote -v
shell> git commit -a -m "My changes"
shell> git push origin master
```

```console
shell> git pull origin master
shell> git pull --progress
```

---

```console
shell> git branch
shell> git branch -vv
shell> git branch --remotes
```

```console
shell> git push origin --delete Branch_df65c30a8bb632955646b90f778c0cb5a7c5b28f
```
---

#### :books: 參考網站：
- [gist](https://gist.github.com/)
---

```console
shell> git mv JavaScript javascript
```

#### :books: 參考網站：
- [git-mv](https://git-scm.com/docs/git-mv)
---

#### :books: 參考網站：
- [4.2 伺服器上的 Git - 在伺服器上部署 Git](https://git-scm.com/book/zh-tw/v1/%E4%BC%BA%E6%9C%8D%E5%99%A8%E4%B8%8A%E7%9A%84-Git-%E5%9C%A8%E4%BC%BA%E6%9C%8D%E5%99%A8%E4%B8%8A%E9%83%A8%E7%BD%B2-Git)

---

#### :books: 參考網站：
- [git-remote](http://git-scm.com/docs/git-remote)
- [Customizing-Git-Git-Configuration](http://git-scm.com/book/en/Customizing-Git-Git-Configuration)
- [Git for Windows](https://msysgit.github.io/)
- [程式開發者的社群網路新世界](http://www.ithome.com.tw/node/79439)
- [從集中版本控制到分散式版本控制](http://www.ithome.com.tw/node/77088)
- [持續整合下的版本控管做法](http://www.ithome.com.tw/node/67969)
- [語意明確的版本變更](http://www.ithome.com.tw/voice/85505)
- [軟體開發過程中不能缺少的系統](http://www.ithome.com.tw/node/76548)
- https://www.ibm.com/developerworks/library/d-learn-workings-git/
- https://www.ibm.com/developerworks/library/wa-git/
- https://developer.ibm.com/opentech/2016/02/01/git-with-it/


---

#### :books: 參考網站：
- https://git-scm.com/book/be/v2/Git-Tools-Credential-Storage
- [caching-your-github-password-in-git](https://help.github.com/articles/caching-your-github-password-in-git/)
- [connecting-to-github-with-ssh](https://help.github.com/articles/connecting-to-github-with-ssh/)

---

#### :books: 參考網站：
- [hello-world](https://guides.github.com/activities/hello-world/)

```
WEB_DIR="/var/www/html"
export GIT_DIR="$WEB_DIR/.git"
```