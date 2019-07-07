# macOS (High Sierra) tips

### Install Command Line Tools

```bash
xcode-select --install
```

### brew extras

```bash
?brew tap buo/cask-upgrade
```

### brew commands

```bash
brew update
brew upgrade
brew cleanup -s

brew cask outdated --greedy
brew cask upgrade --greedy
```

### My brew list

```bash
brew list | column -t
```

```
bash-completion
brew-cask-completion
```

### My brew cask list

```bash
brew cask list | column -t
```

```
appcleaner
coconutbattery
dropbox
iterm2
keepassxc
marta
oversight
sublime-text
transmission
virtualbox
visual-studio-code
vlc
```

### macports commands

https://www.macports.org/ports.php

```bash
sudo vim /opt/local/etc/macports/macports.conf
applications_dir /opt/local/Applications/MacPorts
```

```bash
sudo port -v selfupdate
sudo port installed
sudo port outdated
sudo port upgrade outdated
sudo port clean --all installed
sudo port clean --all all
```
```bash
sudo port -f uninstall installed
```


### NFS server config

```
config file - /etc/exports
<dir> - path from root
```

```bash
<dir> -ro -mapall=<uid>:<gid> -network 10.0.3 -mask 255.255.255.0
```

### Disable local snapshots

```bash
sudo tmutil disable localsnapshot
```

### My .bash_profile

```bash
if [ -f $(brew --prefix)/etc/bash_completion ]; then
  source $(brew --prefix)/etc/bash_completion
fi
# for macports
PATH=/opt/local/bin:/opt/local/sbin:$PATH
# for python
PATH=$PATH:~/Library/Python/3.6/bin
```

### Disable bash session files

```bash
touch ~/.bash_sessions_disable
```

### Mount NFS via terminal

```bash
open smb://<ip>/<name>
```

### My fonts

```bash
/Users/Your_Username/Library/Fonts
```
```bash
https://dejavu-fonts.github.io
https://design.ubuntu.com/font/
```

### Python

```bash
/opt/local/bin/python3 -m pip install -U pylint --user
/opt/local/bin/python3 -m pip install -U flake8 --user
/opt/local/bin/python3 -m pip install -U pep8 --user
/opt/local/bin/python3 -m pip install -U autopep8 --user
```
