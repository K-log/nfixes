# Operating System 
Fixes and notes relating to a specific OS/Environment


## Early 2011 MacBook Pro


### Manjaro/ArchLinux

**WIP: Setup NeoVim IDE**
This section still needs to be filled out.


### Ubuntu/Debian


**Missing Wifi Drivers**
source: [https://wiki.debian.org/bcm43xx](https://wiki.debian.org/bcm43xx)

```bash
# Debian 9 "stretch"
deb http://deb.debian.org/debian/ stretch main contrib non-free

sudo apt-get update

apt-get install firmware-b43-installer
```


**NeoVim Missing Python Support via Python**
source: [https://github.com/neovim/neovim/wiki/Installing-Neovim](https://github.com/neovim/neovim/wiki/Installing-Neovim)

```bash
# Works most of the time without any tweaking
sudo apt install python-neovim
sudo apt install python3-neovim
```

*Alternatively*

source: [https://neovim.io/doc/user/provider.html](https://neovim.io/doc/user/provider.html)


```bash
# Prerequisits -- Python 3
sudo apt-get update
sudo apt-get install python3-pip python3-setuptools python3-wheel
```

```bash
# Prerequisits -- Python 2
sudo apt-get update
sudo apt-get install python-pip
sudo python2 -m install --upgrade setuptools
```

```bash
# Install the modules
python3 -m pip install --user --upgrade pynvim
python2 -m pip install --user --upgrade pynvim
```
