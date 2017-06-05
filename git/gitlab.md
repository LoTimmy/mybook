
```
sudo apt-get install curl openssh-server ca-certificates postfix
curl -sS https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh | sudo bash
sudo apt-get install gitlab-ce
sudo gitlab-ctl reconfigure
```

```
curl -LJO https://packages.gitlab.com/gitlab/gitlab-ce/packages/ubuntu/xenial/gitlab-ce-XXX.deb/download
dpkg -i gitlab-ce-XXX.deb
```

`root`

#### :books: 參考網站：
- https://about.gitlab.com/installation/#ubuntu
- https://about.gitlab.com/installation/#raspberry-pi-2
- https://packages.gitlab.com/gitlab/gitlab-ee
- https://packages.gitlab.com/gitlab/gitlab-ee/install

