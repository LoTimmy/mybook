<img src="https://pbs.twimg.com/profile_images/616309728688238592/pBeeJQDQ_200x200.png" width="100">

> `GitHub`服務的定價策略是，**凡是對外公開的專案完全免費使用，不限使用人數或資料量**，只有使用者或企業想要在`GitHub`上建立不公開的封閉專案時才需要按月付費，而且不公開的專案越多，費用越高。

> 比起缺乏具體證明的履歷，親自開發的程式碼更能代表開發者真正的能力，就像設計師需要作品集，**`GitHub`就是開發者的作品集**

> 在`GitHub`上的程式碼作品，即使只是一個小型的開源專案，也都更能凸顯一個人的確具備了自主學習的能力，這甚至比起上班族只能完成被交付工作的工作經驗，還更有價值。因為在`GitHub`跨國團隊工作模式中，「**90%的能力都要靠自己學習而來**。」




---
`GitHub's IP addresses`
`Current IP Addresses`
`192.30.252.0/22`


---

### Using SSH over the HTTPS port {#using-ssh-over-the-https-port}

```console
shell> ssh -T -p 443 git@ssh.github.com
Hi username! You've successfully authenticated, but GitHub does not
provide shell access.
```

`git@ssh.github.com`
```
Host github.com
  Hostname ssh.github.com
  Port 443
```
```console
shell> ssh -T git@github.com
Hi username! You've successfully authenticated, but GitHub does not
provide shell access.
 Contact a human
```

### Switching remote URLs from HTTPS to SSH {#switching-remote-urls-from-https-to-ssh}

```console
shell> git remote -v
origin  https://github.com/USERNAME/REPOSITORY.git (fetch)
origin  https://github.com/USERNAME/REPOSITORY.git (push)
```

```console
shell> git remote set-url origin git@github.com:USERNAME/OTHERREPOSITORY.git
```
```console
shell> git remote -v
# Verify new remote URL
origin  git@github.com:USERNAME/OTHERREPOSITORY.git (fetch)
origin  git@github.com:USERNAME/OTHERREPOSITORY.git (push)
```

---

<img src="https://pages.github.com/images/logo.svg" width="100">

`http://username.github.io`

#### :books: 參考網站：
- [](https://pages.github.com/)

---

美國知名開發論壇`StackOverflow`

---

`RawGit`

<img src="http://cdn.rawgit.com/rgrove/rawgit/cdn-20170108/public/img/sushi.png" width="100">

**RawGit** serves raw files directly from GitHub with proper **Content-Type** headers.



---

#### :books: 參考網站：
- [github](https://github.com/)
- [GitHub's IP addresses](https://help.github.com/articles/github-s-ip-addresses/)
- [Using SSH over the HTTPS port](https://help.github.com/articles/using-ssh-over-the-https-port/)
- https://help.github.com/articles/changing-a-remote-s-url/#switching-remote-urls-from-ssh-to-https
- https://help.github.com/articles/working-with-ssh-key-passphrases/
- https://help.github.com/articles/changing-author-info/
- https://help.github.com/articles/dealing-with-line-endings/
- [GitHub Git 备忘单](https://services.github.com/on-demand/downloads/zh_CN/github-git-cheat-sheet/)
- [Associating text editors with Git](https://help.github.com/articles/associating-text-editors-with-git/)
- [Removing sensitive data from a repository](https://help.github.com/articles/removing-sensitive-data-from-a-repository/)
- http://www.ithome.com.tw/article/95280
- http://www.ithome.com.tw/news/95283
- http://www.ithome.com.tw/news/95284
- [RawGit](http://rawgit.com/)
