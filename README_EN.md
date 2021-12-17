**[中文](https://github.com/exthmui/android/blob/exthm-12/README.MD) | English**

# exTHmUI

## What’s exTHmUI?

![exthm logo](https://raw.githubusercontent.com/exthmui/android/exthm-12/logo.png)

exTHmUI is an open source Android project with Touhou elements, based on [AOSP](https://android.googlesource.com/). 

> exthm-11 EOL time is mid-2022, please migrate to exthm-12 or newer branches at that time.

> Thank you very much for the technical support provided by [Shelling](https://github.com/cjybyjk), [ReallySnow](https://github.com/ReallySnow)，[ArrowOS](https://github.com/ArrowOS) and [DerpFest](https://github.com/DerpFest-11)!

## Getting started

To get started with exTHmUI, you will need to get familiar with Repo and Version Control with Git.

To initialize your local repository using the exTHmUI trees, use a command like this:

```shell
repo init -u https://github.com/exthmui/android.git -b exthm-12
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

## Contributing

We always welcome developers to submit patches via [exTHmUI Code Review](https://review.exthmui.cn/).
