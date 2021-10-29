---
title: WordPress Notes
menu:
  notes:
    name: WordPress
    identifier: notes-wordpress
    weight: 20
---

<!-- htaccess file notes-->
{{< note title=".htaccess File Notes" >}}
*write code in blocks that are bookended by BEGIN and END like below INCLUDING HASHES*
```
# BEGIN $CODE DESCRIPTION
instructions go here
# END $CODE DESCRIPTION
```

Adding custom PHP values needed for many modern themes
```
## BEGIN Custom PHP values
php_value upload_max_filesize 64M
php_value post_max_size 128M
php_value memory_limit 256M
php_value max_execution_time 300
php_value max_input_time 300
## END Custom PHP values
```
### Adding a password using htpasswd
Install Apache utils package
```
apt-get update
apt-get install apache2-utils
```
create password file and user
```
htpasswd -c /etc/apache2/.htpasswd $USERNAME
```
LEAVE OFF -c for additional users
```
htpasswd /etc/apache2/.htpasswd $USERNAME2
```
update permissions to .htpasswd file
```
chmod 644 /etc/apache2/.htpasswd
```
add following to .htaccess file
```
## BEGIN password
AuthType Basic
AuthName "Authorized Users"
AuthUserFile /etc/apache2/.htpasswd
Require valid-user
## END password
```
Restart apache service
```
systemctl restart apache2
```
{{< /note >}}
