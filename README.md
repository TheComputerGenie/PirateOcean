# PirateOcean (pirate-qt) #

Pirate-Qt (PirateOcean) is a world-first Qt native wallet for ARRR ([Pirate](https://pirate.black/)). It's available for three OS platforms - Windows, Linux, MacOS.

**NB!** Earlier (till 23.05.2019) we had three branches:


- [WinOS](../../tree/WinOS) for Windows.
- [Linux](../../tree/Linux) for Linux.
- [MacOS](../../tree/MacOS) for MacOS.

Now we have only one branch [static](../../tree/static) for building static Pirate-Qt binaries, rather than one branch for each OS.

Use the following scripts to build:

- Linux: `build-linux.sh` (native build)
- Windows: `build-win.sh` (cross-compilation for Win)
- MacOS: `build-mac.sh` (native build)

## How to build? ##

#### Linux

```shell
#The following packages are needed:
sudo apt-get install build-essential pkg-config libc6-dev m4 g++-multilib autoconf libtool ncurses-dev unzip git python python-zmq zlib1g-dev wget libcurl4-gnutls-dev bsdmainutils automake curl
```

```shell
git clone https://github.com/PirateNetwork/PirateOcean --branch static --single-branch
cd PirateOcean
./zcutil/fetch-params.sh
# -j8 = using 8 threads for the compilation - replace 8 with number of threads you want to use
./zcutil/build-linux.sh -j8
#This can take some time.
```


#### OSX
Ensure you have [brew](https://brew.sh) and Command Line Tools installed.
```shell
# Install brew
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
# Install Xcode, opens a pop-up window to install CLT without installing the entire Xcode package
xcode-select --install 
# Update brew and install dependencies
brew update
brew upgrade
brew tap discoteq/discoteq; brew install flock
brew install autoconf autogen automake
brew install gcc@6
brew install binutils
brew install protobuf
brew install coreutils
brew install wget
# Clone the Pirate repo
git clone https://github.com/PirateNetwork/PirateOcean --branch static --single-branch
# Change static branch to other branch you wish to compile
cd PirateOcean
./zcutil/fetch-params.sh
# -j8 = using 8 threads for the compilation - replace 8 with number of threads you want to use
./zcutil/build-mac.sh -j8
# This can take some time.
```

#### Windows
Use a debian cross-compilation setup with mingw for windows and run:
```shell
sudo apt-get install build-essential pkg-config libc6-dev m4 g++-multilib autoconf libtool ncurses-dev unzip git python python-zmq zlib1g-dev wget libcurl4-gnutls-dev bsdmainutils automake curl cmake mingw-w64
curl https://sh.rustup.rs -sSf | sh
source $HOME/.cargo/env
rustup target add x86_64-pc-windows-gnu

sudo update-alternatives --config x86_64-w64-mingw32-gcc
# (configure to use POSIX variant)
sudo update-alternatives --config x86_64-w64-mingw32-g++
# (configure to use POSIX variant)

git clone https://github.com/PirateNetwork/PirateOcean --branch static --single-branch
cd PirateOcean
./zcutil/build-win.sh -j8
# -j8 = using 8 threads for the compilation - replace 8 with number of threads you want to use
#This can take some time and you'll need to run zcutil/fetch-params.bat on the Win system.
```
**Pirate QT is experimental and a work-in-progress.** Use at your own risk.



## Developers of Qt wallet ##
- Pirate developer: [@ComputerGenie](https://github.com/TheComputerGenie)
- Main developer: [@Ocean](https://pirate-platform.slack.com/team/U8BRG09EV)
- IT Expert / Sysengineer: [@Decker](https://pirate-platform.slack.com/messages/D5UHJMCJ3)
