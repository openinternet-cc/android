# Android Root

This guide is for building DatOS for your own device. If you would like to use DatOS without building it yourself, try one of our precompiled builds. Otherwise, you may purchase devices preinstalled with DatOS from the [Open Internet store](https://openinternet.cc). This also helps to support future development efforts. 

> Upstream see Lineage OS 17.1 

## Setup

### 1) Install Requirements:

```
apt-get install bc bison build-essential ccache curl flex g++-multilib gcc-multilib git gnupg gperf imagemagick lib32ncurses5-dev lib32readline-dev lib32z1-dev liblz4-tool libncurses5 libncurses5-dev libsdl1.2-dev libssl-dev libxml2 libxml2-utils lzop pngcrush rsync schedtool squashfs-tools xsltproc yasm zip zlib1g-dev -y
```

### 2) Install Repo Tool:

```
curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
chmod a+x ~/bin/repo
```

> Add it to your path if you want - [see here](https://harryyoud.co.uk/lineage-previews/283946/2/devices/marlin/build#put-the-bin-directory-in-your-path-of-execution)


### 3) Inialize Repo

```
mkdir -p ~/android/openinternet
cd ~/android/openinternet
repo init -u git@github.com:openinternet-cc/android.git
repo sync
```

### 4) Get the party started

DatOS is supported on: 

- Le Eco S2 (S2). 

> What device are you building for? You may have some troubles building for others. To start, make sure you get the correct [propreitary blobs](https://gist.github.com/gWOLF3/30c2339442cc9b58e68aa2a1d373238e) before proceeding.

> For help understanding the Android Build System: see [this guide](https://elinux.org/Android_Build_System)

#### Building for Device:
```
source build/envsetup.sh
breakfast s2
brunch s2
```

#### Building for Emulator:
```
source build/envsetup.sh
lunch lineage_<arch>-eng
mka
```
> Options:
> arm (32-bit ARM)
> arm64 (64-bit ARM)
> x86 (32-bit x86)
> x86_64 (64-bit x86)

## Optimizations

### Set and Enable CCache:
```
export USE_CCACHE=1
export CCACHE_EXEC=/usr/bin/ccache
ccache -M 50G
```

