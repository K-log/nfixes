# Operating System 
Fixes and notes relating to a specific OS/Environment


## Early 2011 MacBook Pro


### Manjaro/ArchLinux

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
