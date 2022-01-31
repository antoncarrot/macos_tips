# macOS tips

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
coreutils
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

### Set bash

```bash
chsh -s /bin/bash
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

### .profile

```bash
HISTCONTROL=ignoreboth
shopt -s histappend

HISTSIZE=1000
HISTFILESIZE=2000

export PS1='\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '

ARCH=$(arch)

export HOMEBREW_NO_ANALYTICS=1

if [ $ARCH == "arm64" ]; then
    eval "$(/opt/homebrew/bin/brew shellenv)"
elif [ $ARCH == "i386" ]; then
    export PS1="\[\033[01;31m\]$ARCH\[\033[00m\] $PS1"
    eval "$(/usr/local/bin/brew shellenv)"

    export PYENV_ROOT="$HOME/.pyenv_x86"
fi

BREW_LIST="$(brew list --formula --full-name -1)"

CFLAGS=""
LDFLAGS=""
BIN_PATH=""

for pkg in $BREW_LIST; do
    PKG_PATH=$(brew --prefix $pkg)

    PKG_H_PATH="$PKG_PATH/include"
    PKG_LIB_PATH="$PKG_PATH/lib"

    PKG_BIN_PATH="$PKG_PATH/bin"

    if [ -d "$PKG_H_PATH" ]; then
        if [ -z "$CFLAGS" ]; then
            CFLAGS="-I$PKG_H_PATH"
        else
            CFLAGS="$CFLAGS -I$PKG_H_PATH"
        fi
    fi

    if [ -d "$PKG_LIB_PATH" ]; then
        if [ -z "$LDFLAGS" ]; then
            LDFLAGS="-L$PKG_LIB_PATH"
        else
            LDFLAGS="$LDFLAGS -L$PKG_LIB_PATH"
        fi
    fi

    if [ -d "$PKG_BIN_PATH" ]; then
        if [ -z "$BIN_PATH" ]; then
            BIN_PATH="$PKG_BIN_PATH"
        else
            BIN_PATH="$BIN_PATH:$PKG_BIN_PATH"
        fi
    fi
done

export LDFLAGS=$LDFLAGS
export CFLAGS=$CFLAGS
export CPPFLAGS=$CFLAGS
export PATH="$PATH:$BIN_PATH"

[[ -r "/opt/homebrew/etc/profile.d/bash_completion.sh" ]] && . "/opt/homebrew/etc/profile.d/bash_completion.sh"

PATH="$PATH:/opt/homebrew/opt/coreutils/libexec/gnubin"

if [ -x $(which dircolors) ]; then
    test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'

    alias grep='grep --color=auto'
    alias fgrep='fgrep --color=auto'
    alias egrep='egrep --color=auto'
fi
```

### Fake uname to avoid unknown arch error

```bash
#!/bin/sh

if [[ "$@" == "-m" ]]; then
    if [ $(arch) == "arm64" ]; then
        echo "aarch64"
    else
        echo "x86_64"
    fi
else
    /usr/bin/uname $@
fi
```

### Arch runner

```bash
#!/bin/sh

if [ -z "$ARCHPREFERENCE" ]; then
   eval $@
else
   /usr/bin/arch $@
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
https://dejavu-fonts.github.io
https://design.ubuntu.com/font/
https://www.jetbrains.com/lp/mono/
```
