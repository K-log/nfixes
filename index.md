---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

# layout: home
---

# FIXES
All the fixes for all the things.
Entries are sorted by Machine -> OS -> Fix

## Early 2011 MacBook Pro

### Ubuntu/Debian

#### Missing Wifi Drivers
source: https://wiki.debian.org/bcm43xx

```bash
# Debian 9 "stretch"
deb http://deb.debian.org/debian/ stretch main contrib non-free

sudo apt-get update

apt-get install firmware-b43-installer
```

#### NeoVim Missing Python Support via Python
source: https://github.com/neovim/neovim/wiki/Installing-Neovim

```bash
sudo apt install python-neovim
sudo apt install python3-neovim
```

**Alternatively**

source: https://neovim.io/doc/user/provider.html

Prerequisits -- Python 3
```bash
sudo apt-get update
sudo apt-get install python3-pip python3-setuptools python3-wheel
```

Prerequisits -- Python 2
```bash
sudo apt-get update
sudo apt-get install python-pip
sudo python2 -m install --upgrade setuptools
```

Install the modules
```bash
python3 -m pip install --user --upgrade pynvim
python2 -m pip install --user --upgrade pynvim
```
