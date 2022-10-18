**[中文](https://github.com/exthmui-legacy/android/blob/exthm-12/README.MD) | English**

# exTHmUI

## What’s exTHmUI?

![exthm logo](https://raw.githubusercontent.com/exthmui-legacy/android/exthm-12/logo.png)

exTHmUI is an open source Android project with Touhou elements, based on [AOSP](https://android.googlesource.com/). 

exTHmUI-12 is already dead. Move to [this page](https://github.com/exthmui/android) to get the newest code.

## Getting started

To get started with exTHmUI, you will need to get familiar with Repo and Version Control with Git.

To initialize your local repository using the exTHmUI trees, use a command like this:

```shell
repo init -u https://github.com/exthmui-legacy/android.git -b exthm-12
repo sync
```

## Start build

To work faster, we introduced a new build script to help you start compiling.

First, go to the root path of your project. We assume that your source is under (/exthm):

```shell
cd /exthm
```

then feel free to use the build script:

```
. build/envsetup.sh && lunch exthm_xxxxx-userdebug && mka bacon
```

The script is interactive so everything else is self-explanatory.
