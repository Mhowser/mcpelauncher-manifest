# mcpelauncher-manifest
The main repository for the Linux and Mac OS Bedrock edition Minecraft launcher with fixed armhf code and 1.12 dedicated server

# Getting started with Raspberry Pi2
# Known issues
- mesa 19.x is unusable for this launcher install mesa 13.0.6 from [source](https://mesa.freedesktop.org/archive/older-versions/13.x/13.0.6/mesa-13.0.6.tar.xz) [building instruction](https://github.com/anholt/mesa/wiki/Building-Mesa-for-VC4)
prepend `LD_LIBRARY_PATH=$HOME/prefix/lib LIBGL_DRIVERS_PATH=$HOME/prefix/lib/dri GBM_DRIVERS_PATH=$HOME/prefix/lib `
- no / bad quality analog audio (unknown hdmi audio quality)
- Stretch qt5 is to old
  - no gui launcher / downloader
  - no Microsoft Account online play

## This raspbian stretch is known to works out of box
- mesa 13.0.6 preinstalled
- download and flash http://downloads.raspberrypi.org/raspbian/images/raspbian-2018-06-29/2018-06-27-raspbian-stretch.zip

### Download Prebuild for Raspbian stretch 2018-06-29+
#### Client
- `sudo apt-get install libpng16-16 libx11-6 libxi6 libcurl3 libudev1 libevdev2 libegl1-mesa libasound2`

- download https://github.com/ChristopherHX/mcpelauncher-manifest/releases/download/1.12.x.0/mcpelauncher-client-46b9621-Linux.deb
- `dpkg -i mcpelauncher-client-46b9621-Linux.deb`

- `sudo raspi-config`
- enable opengl desktop kernel mode in misc and restart

- `export OPENSSL_armcap=0` (Pi2)
- start `mcpelauncher-client` form every where

#### Server
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

### Failed to run CURL_OPENSSL 3 not found
- prepend `LDPRELOAD=/usr/lib/libcurl.so.3 ` to the start command
