## Rainloop Warning

Get rid of of Rainloop Warning-message in admin-page

## AllowOverride

In `/etc/apache2/apache2.conf` file

Make sure that

`AllowOverride None` is `AllowOverride All`

## Solution 

### htaccess in data`folder

Now when `apache2.conf` is set.

`.htaccess`-file in `/var/www/html/rainloop/data/` should look like this:

```
cat /var/www/html/rainloop/data/.htaccess
Require all denied
```

Make sure that premission are owned by `ẁww-data`:

```
sudo chown www-data.www-data /var/www/html/rainloop/data/.htaccess
ls -al /var/www/html/rainloop/data/.htaccess
-rw-r--r-- 1 www-data www-data 19 May 11 10:13 rloop/data/.htaccess
```

## Restart Apache2

Restart Apache2:

```
sudo systemctl restart apache2.service
```

Done
```
