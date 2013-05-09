ubuntusetup
===========
Just a quick reference to how I have ubuntu set up so I can blow things up and put them back in place relatively quickly.

Partitions
----------
/home
/var/www
/var/lib/mysql

Files to save
-------------


Packages to add
---------------
```
echo "deb http://www.duinsoft.nl/pkg debs all" | sudo tee -a /etc/apt/sources.list
sudo apt-key adv --keyserver keys.gnupg.net --recv-keys 5CB26B26
sudo apt-get update
sudo apt-get install tasksel update-sun-jre gparted git zsh curl dkms build-essential linux-headers-`uname -r` libasound2-plugins:i386

```

References:
[Java sun-jre](http://www.duinsoft.nl/packages.php?t=en)
dkms is needed for virtualbox

Then run these commands:
```
sudo tasksel install lamp-server
sudo adduser {username} www-data
sudo chown -R www-data:www-data /var/www
sudo chmod -R g+rw /var/www
sudo rm /var/www/*
sudo mv /var/lib/mysql /var/lib/mysql-orig
sudo mkdir /var/lib/mysql
sudo chown mysql:mysql /var/lib/mysql
sudo chmod -R u+rw /var/lib/mysql
chsh -s /usr/bin/zsh
```
run `sudo blkbld` to get the UUIDs of the www and mysql partitions
edit /etc/fstab and point those to /var/www and /var/lib/mysql directories (using default in the options)

Restore the files in "Files to Save"


Outside repositories
--------------------
https://www.google.com/intl/en/chrome/browser/beta.html
https://www.dropbox.com/install
https://www.virtualbox.org/wiki/Linux_Downloads
http://www.skype.com/en/ http://askubuntu.com/questions/220636/proper-way-to-install-skype-x86-64-in-ubuntu-12-04-after-recent-skype-upgrade
http://www.sublimetext.com/2 follow [sublime setup instructions](http://www.technoreply.com/how-to-install-sublime-text-2-on-ubuntu-12-04-unity/)
```
sudo tar xvf Sublime\ Text\ 2.0.1\ x64.tar.bz2 -C /opt/sublime
sudo mv /opt/sublime/Sublime\ Text\ 2/sublime_text /opt/sublime
sudo ln -s /opt/sublime/sublime_text /usr/bin/sublime
```

