# mcpelauncher-manifest
The main repository for the Linux and Mac OS Bedrock edition Minecraft launcher with fixed armhf code and 1.12 dedicated server

# Getting started with Raspberry Pi2
- Problems with latest Raspbian buster / arch linux arm 2019 and other linux distros with mesa 1.19.*
  - won't launch minecraft 1.12.1.1 UI cropped / pure glitch (when build with buster using mesa 1.19.*)
  - starts with mesa 1.19.* but a lot of in game glitches and black area around the player (not really playable)
  - working client launcher gui raspbian (with qt packages from debian buster)
- Raspbian stretch works (mesa 1.13.x) without sound (unknown if there is a workaround)

## This raspbian stretch Release (without updates) is known to run it without many glitches or light issues (no sound)
http://downloads.raspberrypi.org/raspbian/images/raspbian-2018-06-29/2018-06-27-raspbian-stretch.zip
As of now install no updates from getting started ui without risking not beeing able to run it fine

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
