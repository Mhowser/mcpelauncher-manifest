# mcpelauncher-manifest
The main repository for the Linux and Mac OS Bedrock edition Minecraft launcher with fixed armhf code and 1.12 dedicated server

# Getting started with Raspberry Pi2
The latest Raspbian buster won't launch minecraft 1.12.1.1 UI cropped / pure glitch
Raspbian stretch works without sound / unknown if there is a workaround

## This raspbian stretch Release (without updates) is known to run it without many glitches or light issues (no sound)
http://downloads.raspberrypi.org/raspbian/images/raspbian-2018-06-29/2018-06-27-raspbian-stretch.zip
As of now install no updates from getting started ui without risking not beeing able to run it fine

### Download Prebuild Raspbian stretch 2018-06-29+
`sudo apt-get install libpng libx11 libxi libcurl4-openssl libudev libevdev libegl1 libasound2`

download https://github.com/ChristopherHX/mcpelauncher-manifest/releases/download/1.12.x.0/mcpelauncher-client-46b9621-Linux.deb
dpkg -i mcpelauncher-client-46b9621-Linux.deb

#### Client

`sudo raspi-config`
enable opengl desktop kernel mode in misc (you may also to adjust gpu mem to 128 reduce some ui glitchs) and restart

`export OPENSSL_armcap=0` (Pi2)
start `mcpelauncher-client` form every where

#### Server
download this to https://github.com/ChristopherHX/mcpelauncher-manifest/releases/download/1.12.x.0/mcpelauncher-server

run mcpelauncher-server from download location with minecraft game 1.12.0.28 or 1.12.1.1


### Building from source

`sudo apt-get install libpng-dev libx11-dev libxi-dev libcurl4-openssl-dev libudev-dev libevdev-dev libegl1-mesa-dev libasound2`
