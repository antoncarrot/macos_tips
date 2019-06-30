# macOS (High Sierra) tips

### Install Command Line Tools

```bash
xcode-select --install
```

### Install brew and extras

```bash
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
brew tap buo/cask-upgrade
```

### brew commands

```bash
brew update
brew upgrade
brew cu -a
brew cleanup -s
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
firefox
iterm2
keepassxc
marta
oversight
sublime-text
transmission
virtualbox
vlc
```

### macports commands

https://www.macports.org/ports.php

```bash
sudo vim /opt/local/etc/macports/macports.conf
applications_dir /opt/local/Library/Applications/MacPorts
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
https://design.ubuntu.com/font/
```
