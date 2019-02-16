### Remote Linux HappyPath
**1. Create remote Linux instance**  
Ensure that you have any option to connect with root to the instance. Password 
connection may be already enabled, you can also provide your public key
to initial script (look at second paragraph). SSH key should be used later anyway.

**2. Create SSH keys with OpenSSH**  
Encryption algorithm is rsa by default so we don't have to provide -t option. Length is 2048 by default.
```
ls ~/.ssh   // maybe I already have a key?

ssh-keygen -t rsa -b 4096 -C marcskow
ssh-keygen -C marcskow

cat ~/.ssh/id_rsa.pub
```

**3. Create new sudo user**
```
adduser marcskow
usermod -aG sudo marcskow

As root:
cat ~/.ssh/authorized_keys      // there should be our host
rsync --archive --chown marcskow:marcskow ~/.ssh /home/marcskow
```

**4. Configure firewall if you want**  
UFW - uncomplicated firewall
```kotlin
ufw app list
ufw allow OpenSSH
ufw enable
ufw status
```

**5. Copy files from to instance**
```
scp file root@ip:/remote-path
scp root@ip:/remote-path file
```

**6. Install docker**
```
sudo apt-get install docker
docker version
sudo systemctl start docker     // if needed
```