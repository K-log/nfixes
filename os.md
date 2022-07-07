# Operating System 
Fixes and notes relating to a specific OS/Environment

## Manjaro/ArchLinux

**Setup NeoVim IDE**

Recommended:

```bash
sudo python3 -m pip install --user neovim
```

OR

Install using Snap: https://snapcraft.io/install/nvim/manjaro

THEN

```bash
# Clone the configs to your home directory
cd ~
git clone https://github.com/k-log/configs

# Create the config directory if it does not exist yet
mkdir ~/.config/nvim/

# link them to the config directory
ln ~/config/init.vim ~/.config/nvim/init.vim
```

Now to install [Vim-Plug](https://github.com/junegunn/vim-plug). It is recommended that you read the instructions instead of just simply copy and pasting the code below.

```bash
curl -fLo ~/.local/share/nvim/site/autoload/plug.vim --create-dirs \
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```

Now open NeoVim and install the plugins specified in the config.

```bash
neovim +PlugInstall
```

Once all the plugins are installed it's time to setup syntax checking with [YouCompleteMe](https://github.com/ycm-core/YouCompleteMe). Following the instructions on YouCompleteMe's README.

[YouCompleteMe setup on Linux 64 bit](https://github.com/ycm-core/YouCompleteMe#linux-64-bit)




## Ubuntu/Debian


### Missing Wifi Drivers

**Note: ** Only tested on a 2012 macbook pro running Ubuntu 18.4

source: [https://wiki.debian.org/bcm43xx](https://wiki.debian.org/bcm43xx)

```bash
# Debian 9 "stretch"
deb http://deb.debian.org/debian/ stretch main contrib non-free

sudo apt-get update

apt-get install firmware-b43-installer
```

### Wifi disabled after sleep/lock

**Note: ** Only tested on a 2012 macbook pro running Ubuntu 18.4

source: [wifi-available-networks-not-showing-up-suddenly](https://askubuntu.com/questions/951261/wifi-available-networks-not-showing-up-suddenly/)

Essentially, this systemd script reloads the WiFi kernel module when resuming from suspend.

This script is written for iwlwifi` which is the common Intel driver name. If your's is different change that name below:

```bash
#!/bin/sh

# NAME: /lib/systemd/system-sleep/iwlwifi-reset
# DESC: Resets Intel WiFi which can be flakey after a long suspend.
# DATE: Apr 1, 2017. Modified August 30, 2017.

MYNAME=$0

exit

restart_wifi() {
    /usr/bin/logger $MYNAME 'restart_wifi BEGIN'
    /sbin/modprobe -v -r iwldvm # This removes iwlwifi too
    /sbin/modprobe -v iwlwifi   # This starts iwldvm too
#    systemctl restart NetworkManager.service
    /usr/bin/logger 'systemctl restart NetworkManager.service (SUPPRESSED)'
    /usr/bin/logger $MYNAME 'restart_wifi END'
}

/usr/bin/logger $MYNAME 'case=[' ${1}' ]'
case "${1}/${2}" in
    hibernate|suspend|pre*)
      ;;
    resume|thaw|post*)
      restart_wifi;;
esac
```
NOTE: 

Sometimes simply resetting network manager is all that is needed. In that case un-comment the lines above by removing `#` within the `restart_wifi()` block. 
Then comment out the two lines directly above it by putting `#` at the beginning of those two lines.

You'll need to create this script, called `iwlwifi-reset`, with sudo powers and save it into the directory `/lib/systemd/system-sleep`. Then mark it executable using:

```bash
chmod a+x /lib/systemd/system-sleep/iwlwifi-reset
```

### Unable to screenshare in Wayland on Ubuntu 22.x running gnome 3.x

source: [https://askubuntu.com/questions/1313369/screen-sharing-with-wayland#comment2445442_1398720](https://askubuntu.com/questions/1313369/screen-sharing-with-wayland#comment2445442_1398720)

Simplying install this package fixed the issue.

```bash
sudo apt install xdg-desktop-portal-gnome
```


### NeoVim Missing Python Support via Python

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
