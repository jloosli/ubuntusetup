ubuntusetup
===========
Just a quick reference to how I have ubuntu set up so I can blow things up and put them back in place relatively quickly.

Partitions
----------
/home
/var/www
/var/lib/mysql

Files/directories to save
-------------
/etc/hosts
~/.homestead/Homestead.yaml
~/.ssh




Repositories to add
-------------------
```
# Node and NPM
curl -sL https://deb.nodesource.com/setup_9.x | sudo -E bash -
# Yarn
curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
```

Packages to add
---------------
```
sudo apt upgrade && sudo apt install -y curl git zsh nodejs yarn vagrant
```

Restore the files in "Files to Save"

Outside repositories
--------------------
* https://www.google.com/chrome/browser/desktop/index.html
* https://www.dropbox.com/install
* https://www.virtualbox.org/wiki/Linux_Downloads
* http://www.skype.com/en/ http://askubuntu.com/questions/220636/proper-way-to-install-skype-x86-64-in-ubuntu-12-04-after-recent-skype-upgrade
* http://www.sublimetext.com/3 follow [sublime setup instructions](https://www.sublimetext.com/docs/3/linux_repositories.html)
* [Oh My Zsh](https://github.com/robbyrussell/oh-my-zsh)

Aditional setup
---------------

### Oh My Zsh
Run following script:
```
# Set Theme
sed -i -r '/^ZSH_THEME/s/"(.*)"/"candy"/' ~/.zshrc

# Set Plugins
sed -i '/^plugins/s/(.*)/(git yarn)/' ~/.zshrc

# Uncomment lines
sed -i '/ENABLE_CORRECTION/s/^#\s*//' ~/.zshrc
sed -i '/COMPLETION_WAITING_DOTS/s/^#\s*//' ~/.zshrc
cat <<EOT >> ~/.zshrc
function homestead() {
  ( cd ~/Homestead && vagrant $* )
}

export PATH=$PATH:~/.npm-global/bin:
EOT
```

### Laravel Homestead
See [Installation Docs](https://laravel.com/docs/5.5/homestead#installation-and-setup)

```
vagrant box add laravel/homestead

cd Homestead

# Clone the desired release...
git checkout v6.5.0
```

### VIM
See https://github.com/amix/vimrc



