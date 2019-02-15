### Apache2 as service

**1. Setup remote Linux instance**  

**2. Install apache2**  
```
ssh root@ip

sudo apt-get update
sudo apt-get install apache2 apache2-utils

cd /var/www/html
echo "<html><header><title>This is title</title></header><body>Hello world</body></html>" >> /var/www/html/index.html
google-chrome http://localhost
```

**3. Remove apache2**

**4. Setup password for some files**
```
sudo htpasswd -c /etc/apache2/.htpasswd some-username
sudo nano /etc/apache2/sites-enabled/000-default.conf
```

as 000-default.conf add:

```
<Directory "/var/www/html">
        AuthType Basic
        AuthName "Restricted Content"
        AuthUserFile /etc/apache2/.htpasswd
        Require valid-user
</Directory>
```

Replace /var/www/html with the path to the directory you want to restrict access to.

**5. Restart apache2 after changing password settings**
```
sudo service apache2 restart
```

### Starting stopping restarting
**Start stop**
```
sudo systemctl start apache2.service
sudo systemctl stop apache2.service
sudo systemctl restart apache2.service

Status:
journalctl -u apache2
sudo systemctl status apache2.service

Second method:
sudo /etc/init.d/apache2 start
sudo /etc/init.d/apache2 restart
sudo /etc/init.d/apache2 stop
```

**Remove**
```
sudo service apache2 stop
sudo apt-get purge apache2 apache2-utils apache2.2-bin apache2-common
sudo apt-get autoremove
whereis apache2
sudo rm -rf /etc/apache2  
```


### Download file using command line
```
curl -O [url]

wget "http://domain.com/directory/4?action=AttachFile&do=view&target=file.tgz" 
wget  -P /home/omio/Desktop/ "http://thecanadiantestbox.x10.mx/CC.zip"
wget  -O /home/omio/Desktop/NewFileName "http://thecanadiantestbox.x10.mx/CC.zip"
```

### Sources

[Link](https://www.bersling.com/2016/04/29/password-protect-parts-of-your-website/)