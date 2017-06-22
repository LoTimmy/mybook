### 安裝 {#installing}

```console
shell> brew install git
shell> brew cask install sourcetree
```

### Set Up Git {#set-up-git}

```console
shell> git config --global user.name "Your Name"
shell> git config --global user.email "your_email@example.com"

shell> git config --global user.email
your_email@example.com

shell> git config --global user.email "username@users.noreply.github.com"

shell> git config --global core.autocrlf true
# Configure Git on Windows to properly handle line endings

shell> git config --global core.autocrlf input
# Configure Git on OS X or Linux to properly handle line endings

shell> git config --global core.editor emacs

shell> git config --global color.ui true

shell> git config --global commit.template ~/.gitmessage.txt
shell> git commit
```

`~/.gitmessage.txt`

`.gitconfig`

```
[user]
	name = Your Name
	email = your_email@example.com
```

```console
shell> git config --global alias.co checkout
shell> git config --global alias.br branch
shell> git config --global alias.ci commit
shell> git config --global alias.st status
shell> git config --global alias.diffc diff --cached
shell> git config --global alias.remotev remote -v
shell> git config --global alias.last 'log -1 HEAD'
```

```console
shell> git config --global diff.tool vimdiff
shell> git config --global difftool.prompt false 
```


```console
shell> git config -l
```

```console
shell> git config --global --unset user.name
shell> git config --global --unset user.email
```

#### :books: 參考網站：
- [Git Aliases](https://git-scm.com/book/tr/v2/Git-Basics-Git-Aliases)
- [Setting your username in Git](https://help.github.com/articles/setting-your-username-in-git/)
- [Setting your email in Git](https://help.github.com/articles/setting-your-email-in-git/)
- [Keeping your email address private](https://help.github.com/articles/keeping-your-email-address-private/)
- [Dealing with line endings](https://help.github.com/articles/dealing-with-line-endings/)

### Hello world 範例 {#hello-world}

```console
shell> mkdir helloworld
shell> cd project
shell> git init
Initialized empty Git repository in .git/
shell> edit hello.c
shell> git add hello.c
shell> git status
shell> git commit -m "initial revision"
shell> git log
```

### Git Hooks {#githooks}

```console
shell> mkdir web.git
shell> cd web.git
shell> git init --bare
```

`hooks/post-receive`

```sh
#!/bin/sh
git --work-tree=/var/www/html clean -fd
git --work-tree=/var/www/html checkout --force


jpegoptim /var/www/html/images/*.jpg
optipng -o7 *.png

chown -R www:www /var/www/html
```
```console
shell> chmod -x hooks/post-receive
```
```console
shell> git remote add prd 192.168.8.88:/opt/web.git
shell> git remote add tst 192.168.8.88:/opt/web-tst.git
shell> git add *
shell> git commit -m ''
shell> git push tst master
shell> git push prd master
```
---

`hooks/post-commit`

```sh
#!/bin/sh

git push origin master
```

---

`hooks/pre-commit`

```console
shell> git add .
```

```sh
#!/bin/sh

if `git diff --cached --name-only --diff-filter=ACM | grep '.js'`
then
  jshint --verbose 
fi
exit $?
```
---

`hooks/prepare-commit-msg`

```sh
#!/bin/sh
echo "$(date +%Y%m%d)" >> $1
```

`hooks/commit-msg`
```sh
#!/bin/sh
echo "$(date +%Y%m%d)" >> $1
```

```console
shell> git commit --amend --no-edit
```

#### :books: 參考網站：
- [githooks](https://git-scm.com/docs/githooks)
- [git-checkout](https://git-scm.com/docs/git-checkout)
- [git-clean](https://git-scm.com/docs/git-clean)
- [git](https://git-scm.com/docs/git)
- https://git-scm.com/book/en/v2/Customizing-Git-Git-Hooks

---

### Git Branching {#git-branch}

```console
shell> mkdir git-tutorial
shell> cd git-tutorial 
shell> git init
shell> git add README test.rb LICENSE
shell> git commit -m 'The initial commit of my project'
```

<img src="https://git-scm.com/book/en/v2/images/commit-and-tree.png" width="70%" >
<img src="https://git-scm.com/book/en/v2/images/commits-and-parents.png" width="70%" >
<img src="https://git-scm.com/book/en/v2/images/branch-and-history.png" width="50%" >
<br><br>
<img src="https://git-scm.com/book/en/v2/images/two-branches.png" width="50%" >

`Creating a New Branch`

```console
shell> mkdir git-tutorial
shell> cd git-tutorial 
shell> git init
shell> git add README test.rb LICENSE
shell> git commit -m 'The initial commit of my project'
```

<img src="https://git-scm.com/book/en/v2/images/commit-and-tree.png" width="70%" >
<img src="https://git-scm.com/book/en/v2/images/commits-and-parents.png" width="70%" >
<img src="https://git-scm.com/book/en/v2/images/branch-and-history.png" width="50%" >
<br><br>
<img src="https://git-scm.com/book/en/v2/images/two-branches.png" width="50%" >

`Creating a New Branch`
```console
shell> git branch testing
shell> git branch
* master
  testing

shell> git log --oneline --decorate
f30ab (HEAD -> master, testing) add feature #32 - ability to add new formats to the central interface
34ac2 Fixed bug #1328 - stack overflow under certain conditions
98ca9 The initial commit of my project
```

<img src="https://git-scm.com/book/en/v2/images/head-to-master.png" width="50%" >

`Switching Branches`

```console
shell> git checkout testing
Switched to branch 'testing'

shell> git branch
  master
* testing
```
<img src="https://git-scm.com/book/en/v2/images/head-to-testing.png" width="50%" >

```console
shell> vim test.rb
shell> git commit -a -m 'made a change'
```
<img src="https://git-scm.com/book/en/v2/images/advance-testing.png" width="50%" >

```console
shell> git checkout master
```
<img src="https://git-scm.com/book/en/v2/images/checkout-master.png" width="50%" >

```console
shell> vim test.rb
shell> git commit -a -m 'made other changes'
```
<img src="https://git-scm.com/book/en/v2/images/advance-master.png" width="50%" >

```console
shell> git log --oneline --decorate --graph --all
* c2b9e (HEAD, master) made other changes
| * 87ab2 (testing) made a change
|/
* f30ab add feature #32 - ability to add new formats to the
* 34ac2 fixed bug #1328 - stack overflow under certain conditions
* 98ca9 initial commit of my project
```
---

<img src="https://git-scm.com/book/en/v2/images/basic-branching-1.png" width="50%" >

```console
shell> git checkout -b iss53
Switched to a new branch "iss53"
```
```console
shell> git branch iss53
shell> git checkout iss53
```
<img src="https://git-scm.com/book/en/v2/images/basic-branching-2.png" width="50%" >

```console
shell> vim index.html
shell> git commit -a -m 'added a new footer [issue 53]'
```
<img src="https://git-scm.com/book/en/v2/images/basic-branching-3.png" width="50%" >

```console
shell> git checkout master
Switched to branch 'master'
```

```console
shell> git checkout -b hotfix
Switched to a new branch 'hotfix'
shell> vim index.html
shell> git commit -a -m 'fixed the broken email address'
[hotfix 1fb7853] fixed the broken email address
 1 file changed, 2 insertions(+)
```
<img src="https://git-scm.com/book/en/v2/images/basic-branching-4.png" width="50%" >

```console
shell> git checkout master
shell> git merge hotfix
Updating f42c576..3a0874c
Fast-forward
 index.html | 2 ++
 1 file changed, 2 insertions(+)

```
<img src="https://git-scm.com/book/en/v2/images/basic-branching-5.png" width="50%" >

```console
shell> git branch -d hotfix
Deleted branch hotfix (3a0874c).
```
<img src="https://git-scm.com/book/en/v2/images/basic-branching-5.png" width="50%" >

```console
shell> git checkout iss53
Switched to branch "iss53"
shell> vim index.html
shell> git commit -a -m 'finished the new footer [issue 53]'
[iss53 ad82d7a] finished the new footer [issue 53]
1 file changed, 1 insertion(+)

shell> git branch -d hotfix
Deleted branch hotfix (3a0874c).
```
<img src="https://git-scm.com/book/en/v2/images/basic-branching-6.png" width="60%" >

```console
shell> git checkout iss53
Switched to branch "iss53"
shell> vim index.html
shell> git commit -a -m 'finished the new footer [issue 53]'
[iss53 ad82d7a] finished the new footer [issue 53]
1 file changed, 1 insertion(+)
```
<img src="https://git-scm.com/book/en/v2/images/basic-branching-6.png" width="60%" >

```console
>>>>>>> e1f0afe8af02de269b75f25ff8285fce65bcb2e9
shell> git checkout master
Switched to branch 'master'
shell> git merge iss53
Merge made by the 'recursive' strategy.
index.html |    1 +
1 file changed, 1 insertion(+)
```
<img src="https://git-scm.com/book/en/v2/images/basic-merging-2.png" width="60%" >

```console
shell> git branch -d iss53
```

`Basic Merge Conflicts`

`Merge` `合併` `[mɝdʒ]`

`Conflicts` `衝突` `[ˋkɑnflɪkt]`

```console
shell> git merge iss53
Auto-merging index.html
CONFLICT (content): Merge conflict in index.html
Automatic merge failed; fix conflicts and then commit the result.
```

```console
shell> git status
On branch master
You have unmerged paths.
  (fix conflicts and run "git commit")

Unmerged paths:
  (use "git add <file>..." to mark resolution)

    both modified:      index.html

no changes added to commit (use "git add" and/or "git commit -a")
```

```
<div id="footer">
 please contact us at support@github.com
</div>
```
```console
shell> git mergetool

This message is displayed because 'merge.tool' is not configured.
See 'git mergetool --tool-help' or 'git help config' for more details.
'git mergetool' will now attempt to use one of the following tools:
opendiff kdiff3 tkdiff xxdiff meld tortoisemerge gvimdiff diffuse diffmerge ecmerge p4merge araxis bc3 codecompare vimdiff emerge
Merging:
index.html

Normal merge conflict for 'index.html':
  {local}: modified file
  {remote}: modified file
Hit return to start merge resolution tool (opendiff):
```
```console
shell> git status
On branch master
All conflicts fixed but you are still merging.
  (use "git commit" to conclude merge)

Changes to be committed:

    modified:   index.html
```

```
Merge branch 'iss53'

Conflicts:
    index.html
#
# It looks like you may be committing a merge.
# If this is not correct, please remove the file
#	.git/MERGE_HEAD
# and try again.


# Please enter the commit message for your changes. Lines starting
# with '#' will be ignored, and an empty message aborts the commit.
# On branch master
# All conflicts fixed but you are still merging.
#
# Changes to be committed:
#	modified:   index.html
#
```

---

```console
shell> git branch	     # list all local branches in this repo
shell> git checkout test  # switch working directory to branch "test"
shell> git branch new     # create branch "new" starting at current HEAD
shell> git branch -d new  # delete branch "new"
```

#### :books: 參考網站：
- [git-branch](https://git-scm.com/docs/git-branch)
- [git-checkout](https://git-scm.com/docs/git-checkout)
- [Git-Branching-Branches-in-a-Nutshell](https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell)
- [Git-Branching-Basic-Branching-and-Merging](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging)
- [Git-Branching-Branch-Management](https://git-scm.com/book/en/v2/Git-Branching-Branch-Management)
- [Git-Branching-Remote-Branches](https://git-scm.com/book/en/v2/Git-Branching-Remote-Branches)
- [Git-Branching-Branching-Workflows](https://git-scm.com/book/en/v2/Git-Branching-Branching-Workflows)
- https://git-scm.com/book/en/v2
- https://git-scm.com/docs/user-manual
- [Subversion to Git Migration](https://services.github.com/on-demand/downloads/subversion-migration/)
- [GitHub Git 备忘单](https://services.github.com/on-demand/downloads/zh_CN/github-git-cheat-sheet/)
- https://services.github.com/on-demand/downloads/github-git-cheat-sheet.pdf

`In a nutshell...` `簡單地說…`

---

```console
shell> git log --graph
```

---

### Ignoring files {#ignoring-files}

`.gitignore`

```
*~
.*.swp
.DS_Store
```

#### :books: 參考網站：
- [Ignoring files](https://help.github.com/articles/ignoring-files/)
- [gitignore](https://github.com/github/gitignore)

---

```console
shell> git ls-files
shell> git ls-files --ignored --exclude-standard
```

#### :books: 參考網站：
- [git-ls-files](https://git-scm.com/docs/git-ls-files)
---

```console
shell> git difftool
```

#### :books: 參考網站：
- [git-difftool](https://git-scm.com/docs/git-difftool)
---

```console
shell> git difftool --extcmd icdiff
shell> git icdiff
```

- [icdiff](https://github.com/jeffkaufman/icdiff)
---

`HEAD`
`iss53`
`master`
`iss91`
`iss91v2`
`testing`
`dumbidea`
`experiment`
`.git`
`test`
`v2.6.18`
`.gitignore`
`branchname`
`mywork`
`origin`
`myfile`


```
$ git remote add example git://example.com/project.git
$ git remote			# list remote repositories
example
origin
$ git remote show example	# get details
* remote example
  URL: git://example.com/project.git
  Tracked remote branches
    master
    next
    ...
$ git fetch example		# update branches from example
$ git branch -r			# list all remote branches
```

```
$ echo "Hello World" >hello
$ echo "Silly example" >example
$ echo "It's a new day for git" >>hello
$ git tag my-first-tag
$ mkdir my-git
$ cd my-git
$ git checkout -b mybranch
$ git add file.txt
$ git clone git://git.kernel.org/pub/scm/git/git.git/ my-git
$ cd my-git
$ git checkout
$ git checkout master
$ git branch
$ echo "Work, work, work" >>hello
$ git commit -m "Some work." -i hello
$ git checkout mybranch
$ echo "Play, play, play" >>hello
$ echo "Lots of fun" >>example
$ git commit -m "Some fun." -i hello example
$ git tag -l
$ git checkout -b new v2.6.13

$ mkdir project
$ cd project
$ git init

$ git remote add example git://example.com/proj.git
```
- [Git-Tools-Credential-Storage](https://git-scm.com/book/be/v2/Git-Tools-Credential-Storage)

`Fast Forward` `快轉` `向前快轉`

```
git clean -f
git clean -f -d
```



