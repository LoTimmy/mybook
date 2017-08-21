
```
shell> sudo apt-get install curl openssh-server ca-certificates postfix
shell> curl -sS https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh | sudo bash
shell> sudo apt-get install gitlab-ce
shell> sudo gitlab-ctl reconfigure
```

`root`

---

`/etc/gitlab/gitlab.rb`
```
## GitLab URL
external_url 'http://ubuntu.unassigned-domain'

### Email Settings
# gitlab_rails['gitlab_email_enabled'] = true
# gitlab_rails['gitlab_email_from'] = 'example@example.com'
# gitlab_rails['gitlab_email_display_name'] = 'Example'
# gitlab_rails['gitlab_email_reply_to'] = 'noreply@example.com'
# gitlab_rails['gitlab_email_subject_suffix'] = ''

### Backup Settings
# gitlab_rails['backup_path'] = "/var/opt/gitlab/backups"

```

```
sudo gitlab-ctl reconfigure
```

---

```
shell> sudo gitlab-ctl restart
shell> sudo gitlab-ctl restart nginx
```

---

`/var/opt/gitlab/backups`
`/var/opt/gitlab/git-data/repositories`


```
shell> sudo gitlab-rake gitlab:backup:create
```

```
Dumping database tables:
- Dumping table events... [DONE]
- Dumping table issues... [DONE]
- Dumping table keys... [DONE]
- Dumping table merge_requests... [DONE]
- Dumping table milestones... [DONE]
- Dumping table namespaces... [DONE]
- Dumping table notes... [DONE]
- Dumping table projects... [DONE]
- Dumping table protected_branches... [DONE]
- Dumping table schema_migrations... [DONE]
- Dumping table services... [DONE]
- Dumping table snippets... [DONE]
- Dumping table taggings... [DONE]
- Dumping table tags... [DONE]
- Dumping table users... [DONE]
- Dumping table users_projects... [DONE]
- Dumping table web_hooks... [DONE]
- Dumping table wikis... [DONE]
Dumping repositories:
- Dumping repository abcd... [DONE]
Creating backup archive: $TIMESTAMP_gitlab_backup.tar [DONE]
Deleting tmp directories...[DONE]
Deleting old backups... [SKIPPING]
```

```
shell> sudo gitlab-ctl stop unicorn
shell> sudo gitlab-ctl stop sidekiq
# Verify
shell> sudo gitlab-ctl status
```

```
shell> sudo gitlab-rake gitlab:backup:restore BACKUP=1493107454_2017_04_25_9.1.0
```

```
shell> sudo gitlab-ctl start
shell> sudo gitlab-rake gitlab:check SANITIZE=true
```


#### :books: 參考網站：
- https://about.gitlab.com/installation/#ubuntu
- https://about.gitlab.com/installation/#raspberry-pi-2
- https://packages.gitlab.com/gitlab/gitlab-ee
- https://packages.gitlab.com/gitlab/gitlab-ee/install
- https://docs.gitlab.com/ce/install/requirements.html
- https://docs.gitlab.com/ee/administration/restart_gitlab.html

