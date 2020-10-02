# exTHmUI

## What’s exTHmUI?

![](https://raw.githubusercontent.com/exthmui/android/exthm-10/logo.png)

exTHmUI is an open source Android project with Touhou element, based LineageOS. 

## How to build exTHmUI?

> This guide takes Debian for example.

### Install dependencies

```shell
sudo apt-get install bc bison build-essential ccache curl flex g++-multilib gcc-multilib git gnupg gperf imagemagick lib32ncurses5-dev lib32readline-dev lib32z1-dev liblz4-tool libncurses5-dev libsdl1.2-dev libssl-dev libwxgtk3.0-dev libxml2 libxml2-utils lzop pngcrush rsync schedtool squashfs-tools xsltproc zip zlib1g-dev repo
```

### Create the work directories

```shell
mkdir ~/exTHmUI
cd ~/exTHmUI
```

### Initialize the exTHmUI source repository

```shell
repo init -u https://github.com/exthmui/android.git -b exthm-10
```

### Download the source code

```shell
repo sync
```

### Prepare the device-specific code

```shell
. build/envsetup.sh
lunch exthm_[device_code]-userdebug
```

### Start building

```shell
mka bacon
```
