```
shell> apt-get install mysql-server
shell> apt-get install roundcube roundcube-mysql
```

```
shell> vim /etc/roundcube/apache.conf
```

```
Alias /roundcube/program/js/tiny_mce/ /usr/share/tinymce/www/
Alias /roundcube /var/lib/roundcube
```

```
shell> vim /etc/roundcube/main.inc.php
```
```
$rcmail_config['default_host'] = '127.0.0.1';
$rcmail_config['smtp_server'] = '127.0.0.1';
$rcmail_config['language'] = 'zh_TW';
$rcmail_config['create_default_folders'] = TRUE;
$rcmail_config['default_charset'] = 'UTF-8';
$rcmail_config['htmleditor'] = TRUE;
$rcmail_config['timezone'] = '8';
```