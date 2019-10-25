# mcpelauncher-manifest
The main repository for the Linux and Mac OS Bedrock edition Minecraft launcher with fixed armhf code and 1.12 dedicated server

# Getting started with Raspberry Pi
**You need to own Minecraft Pe on Google Play**,
You need an **arm apk** of Minecraft
# Known issues
- mesa 19.x is unusable for this launcher install mesa 13.0.6 from [source](https://mesa.freedesktop.org/archive/older-versions/13.x/13.0.6/mesa-13.0.6.tar.xz) [building instruction](https://github.com/anholt/mesa/wiki/Building-Mesa-for-VC4)
prepend `LD_LIBRARY_PATH=$HOME/prefix/lib LIBGL_DRIVERS_PATH=$HOME/prefix/lib/dri GBM_DRIVERS_PATH=$HOME/prefix/lib `
- no / bad quality analog audio (unknown hdmi audio quality)
- Currently no Xbox live, **do not press sign-in**

## Raspbian 

### buster
- install mesa 13.0.6 is working, but not the distibution version (Raspberry Pi 2)
- download https://github.com/ChristopherHX/mcpelauncher-manifest/releases/tag/1.12.x.2.armhf.raspbian.buster
- install via `sudo dpkg -i name.deb && sudo apt-get install -f`
- **You must do this for every Terminal Session** `export OPENSSL_armcap=0`
#### Qt Bedrocklauncher
- Currently cannot start the game, needs to define Environment Variables
- Only Download and extracting latest or apk unpacking works
- install https://packages.debian.org/buster/all/debian-archive-keyring/download
- add 'deb http://ftp.debian.org/debian buster main' to /etc/apt/sources.list'
- install
- `sudo apt-get update && sudo apt-get install libssl-dev libcurl4-openssl-dev libuv1-dev libzip-dev libprotobuf-dev protobuf-compiler qtbase5-dev qtwebengine5-dev qtdeclarative5-dev libqt5svg5-dev qml-module-qtquick2 qml-module-qtquick-layouts qml-module-qtquick-controls qml-module-qtquick-controls2 qml-module-qtquick-window2 qml-module-qtquick-dialogs qml-module-qt-labs-settings qml-module-qt-labs-folderlistmodel`
- install mcpelauncher-qt from my github download page and run it


### stretch (only cli client + server)
- Deprecated
- qt is to old for the gui
  - no gui launcher / downloader
  - no Microsoft Account online play
- mesa 13.0.6 preinstalled

#### Prebuild
##### Client
- `sudo apt-get install libpng16-16 libx11-6 libxi6 libcurl3 libudev1 libevdev2 libegl1-mesa libasound2`

- download https://github.com/ChristopherHX/mcpelauncher-manifest/releases/download/1.12.x.0/mcpelauncher-client-46b9621-Linux.deb
- `dpkg -i mcpelauncher-client-46b9621-Linux.deb`

- `sudo raspi-config`
- enable opengl desktop kernel mode in misc and restart

- `export OPENSSL_armcap=0` (Pi2)
- start `mcpelauncher-client` form every where

##### Server
- `sudo apt-get install libcurl3`

- download https://github.com/ChristopherHX/mcpelauncher-manifest/releases/download/1.12.x.1/mcpelauncher-server

- `export OPENSSL_armcap=0` (Pi2)
- start `mcpelauncher-server`

### Building from source 

- `sudo apt-get install cmake libpng-dev libx11-dev libxi-dev libcurl4-openssl-dev libudev-dev libevdev-dev libegl1-mesa-dev libasound2`
- `git clone --recursive https://github.com/ChristopherHX/mcpelauncher-manifest.git -b 1.12.x_armhf`
- `mkdir build && cd build`
- `cmake ..`
- `make` or with swap space `make -j4`

### Failed to run CURL_OPENSSL 3 not found (Raspbian stretch build on archlinuxarm)
- prepend `LDPRELOAD=/usr/lib/libcurl.so.3 ` to the start command
