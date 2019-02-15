### Add or remove service from Linux startup

There are 3 main init systems for Ubuntu

* Systemd
* Upstart
* SysV

**How to enable and disable services in Systemd init**
```
Starting, stopping, restarting:
systemctl start service-name
systemctl restart service-name
systemctl stop service-name
systemctl is-active service-name

Enabling and disabling on boot up run:
systemctl enable service-name
systemctl disable service-name
systemctl is-enabled service-name

Disable completely:
systemctl stop service-name
systemctl disable service-name
rm /etc/systemd/system/service-name

Reload systemd:
systemctl daemon-reload
systemctl reset-failed
```

Another way:
```
sudo update-rc.d apache2 enable
sudo update-rc.d apache2 disable

Doing this will cause all runlevel folders that are linked to apache2 to be removed.
sudo update-rc.d -f apache2 remove
```

#### Source
[Link](https://linoxide.com/linux-how-to/enable-disable-services-ubuntu-systemd-upstart/)