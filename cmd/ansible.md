<img src="http://i.imgur.com/x3bCOdV.png" alt="ansible" width=58 height=58>

> `Ansible`是近年來知名度不斷上升的`DevOps`自動化軟體。

> 目前`DevOps`自動化軟體知名的工具有`Puppet`、`Chef`、`Ansible`、`SaltStack`及`CFEngine`等。

> `Ansible`之所以易於使用，其一是`Ansible`用以設定自動化部署的`Playbook`，是以易讀易懂的`YAML`程式碼來撰寫，對於`DevOps`撰寫程式碼與維護自動化流程相對容易；再者，`Ansible`無須代理程式，以`SSH`來執行自動化程序，對於企業要採用也比較容易。

> `Ansible`是以`Python`開發的自動化組態管理工具，架構靈活、部署模式不需依賴代理程式，目標是實現`基礎建設即程式碼`（`Infrastructure as Code`），協助開發者部署出一致的運作環境。此外，`Ansible`可以用於部署應用程式以及幫助開發者導入持續整合的作業流程。

> `Ansible`的部署模式不需要依賴`代理程式` (`agent`)，與`Puppet`及`Chef`的拉取（Pull-based）屬性為特色的工具相比，`Ansible`的屬性則為推播式（Push-based）。

> `Ansible`透過`劇本` (`Playbook`) 以及`模組` (`Module`) 對節點進行管理。`Ansible`比喻：「**如果模組是工作室內的工具，那麼劇本就是你的設計規畫。**」

---

### 安裝 {#installing}

```console
shell> apt-get install python
shell> apt-get install ansible
```

```console
shell> brew install ansible
```

---

```console
shell> ansible all -m raw -a 'apt-get install python -y' -b --ask-become-pass
```

```console
shell> ansible all -m ping
shell> ansible all -m ping --ask-pass
shell> ansible all -m ping -u bruce
shell> ansible all -m ping -u bruce --sudo
shell> ansible all -m ping -u bruce --sudo --sudo-user batman

shell> ansible all -m ping -u bruce -b
shell> ansible all -m ping -u bruce -b --become-user batman

shell> ansible all -a "uptime"

shell> ansible foo.example.com -m yum -a "name=httpd state=installed"
shell> ansible foo.example.com -a "/usr/sbin/reboot"

shell> ansible myhost --sudo -m raw -a "yum install -y python2 python-simplejson"
```

```console
shell> echo "127.0.0.1" > ~/ansible_hosts
shell> export ANSIBLE_INVENTORY=~/ansible_hosts
```

```
[defaults]

host_key_checking = False
```

```console
shell> export ANSIBLE_HOST_KEY_CHECKING=False
```

#### :books: 參考網站：
- [intro_installation](http://docs.ansible.com/ansible/intro_installation.html)

---

`Inventory`
```
badwolf.example.com:5309
jumper ansible_port=5555 ansible_host=192.168.1.50

mail.example.com

192.168.1.50
aserver.example.org
bserver.example.org

[webservers]
www1.example.com
www2.example.com
foo.example.com
bar.example.com

[dbservers]
db0.example.com
db1.example.com
one.example.com
two.example.com
three.example.com
```

---

```console
shell> ansible all -m setup
shell> ansible all -m setup -a 'filter=ansible_eth[0-2]'

shell> ansible all -m copy -a "src=/srv/myfiles/foo.conf dest=/etc/foo.conf owner=foo group=foo mode=0644"
shell> ansible all -m copy -a "src=/mine/ntp.conf dest=/etc/ntp.conf owner=root group=root mode=644 backup=yes"
shell> ansible all -m copy -a "src=/etc/hosts dest=/tmp/hosts"

```

```console
shell> ansible all -m apt -a 'name=foo update_cache=yes' --sudo
```

```
- apt: update_cache=yes

- apt: name=foo state=present
- apt: name=foo update_cache=yes
```

`filename.yml`

```
- command: echo HelloWorld

- name: add several users
  user: name={{ item }} state=present groups=wheel
  with_items:
     - testuser1
     - testuser2

- user: name=johnd comment="John Doe" uid=1040 group=admin
- user: name=james shell=/bin/bash groups=admins,developers append=yes
- user: name=johnd state=absent remove=yes
- user: name=jsmith generate_ssh_key=yes ssh_key_bits=2048 ssh_key_file=.ssh/id_rsa
- user: name=james18 shell=/bin/zsh groups=developers expires=1422403387

```

```console
shell> ansible-doc -l
```

```
- lineinfile: dest=/etc/hosts regexp='^127\.0\.0\.1' line='127.0.0.1 localhost' owner=root group=root mode=0644
```

#### :books: 參考網站：
- [ping_module](http://docs.ansible.com/ansible/ping_module.html)
- [setup_module](http://docs.ansible.com/ansible/setup_module.html)
- [copy_module](http://docs.ansible.com/ansible/copy_module.html)
- [debconf_module](http://docs.ansible.com/ansible/debconf_module.html)
- [apt_module](http://docs.ansible.com/ansible/apt_module.html)
- [mail_module](http://docs.ansible.com/ansible/mail_module.html)
- [service_module](http://docs.ansible.com/ansible/service_module.html)
- [template_module](http://docs.ansible.com/ansible/template_module.html)
- [command_module](http://docs.ansible.com/ansible/command_module.html)
- [apt_module](http://docs.ansible.com/ansible/apt_module.html)
- [user_module](http://docs.ansible.com/ansible/user_module.html)
- [authorized_key_module](http://docs.ansible.com/ansible/authorized_key_module.html)
- [lineinfile_module](http://docs.ansible.com/ansible/lineinfile_module.html)
- [blockinfile_module](http://docs.ansible.com/ansible/blockinfile_module.html)
- [shell_module](http://docs.ansible.com/ansible/shell_module.html)
- [mysql_db_module](http://docs.ansible.com/ansible/mysql_db_module.html)
- [mysql_user_module](http://docs.ansible.com/ansible/mysql_user_module.html)
- [fetch_module](http://docs.ansible.com/ansible/fetch_module.html)

---

```
---
- hosts: webservers
```

```
ansible-playbook playbook.yml -f 10

ansible-galaxy install

search
```

```
---
- hosts: 172.16.159.129
  tasks:
    - name: test connection
      ping:
    - apt: name=vim-nox update_cache=yes
      become: true

- hostname: name=web01

    - service: name=nginx state=started
      become: yes
      become_method: sudo

    - name: make sure apache is running
      service: name=httpd state=started

  - name: disable selinux
    command: /sbin/setenforce 0

    - apt: name=postfix,mailutils state=present
      when: ansible_os_family == "Debian"
```

```
---
# ...
  tasks:

  - name: recursively copy files from management server to target
    local_action: command rsync -a /path/to/files {{ inventory_hostname }}:/path/to/target/
```

```console
shell> python -c 'import crypt; print crypt.crypt("word", "salt")'
```
---

#### :books: 參考網站：
- [ansible](http://www.ithome.com.tw/news/99354)
- [ansible](http://www.ithome.com.tw/news/99306)
- [become](http://docs.ansible.com/ansible/become.html)
- [intro_getting_started](http://docs.ansible.com/ansible/intro_getting_started.html)
- [intro_configuration](http://docs.ansible.com/ansible/intro_configuration.html)
- [intro_inventory](http://docs.ansible.com/ansible/intro_inventory.html) 
- [playbooks_intro](http://docs.ansible.com/ansible/playbooks_intro.html)
- [playbooks_conditionals](http://docs.ansible.com/ansible/playbooks_conditionals.html)
- [faq](http://docs.ansible.com/ansible/faq.html)
- [galaxy](https://galaxy.ansible.com/)
- [使用 Ansible 高效交付 Docker 容器](https://www.ibm.com/developerworks/cn/cloud/library/cl-provision-docker-containers-ansible/)
- [使用 Ansible 管理 MySQL 复制](https://www.ibm.com/developerworks/cn/linux/1502_lih_ansible/)
- [yum_module](http://docs.ansible.com/ansible/yum_module.html)

