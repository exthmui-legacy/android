**中文｜[English](https://github.com/exthmui-legacy/android/blob/exthm-12/README_EN.md)**

# exTHmUI

## 什么是 exTHmUI ？

![exthm logo](https://i.niupic.com/images/2020/06/16/8gWB.png)

exTHmUI-legacy 为历史仓库，不再提供任何的安全补丁或者功能更新, 源码*不保证*能够正常编译。请移步 [这里](https://github.com/exTHmUI/android) 来获取 exTHmUI-13 的源码。

## 同步源码

> repo 是一种用于管理多个 Git 仓库的工具

要开始编译 exTHmUI，你需要熟悉 Repo 和 Git

要开始同步源码，请使用这些命令

```shell
repo init -u https://github.com/exthmui-legacy/android.git -b exthm-12
repo sync
```

您也可以使用如下命令来初始化仓库，这样可以节省磁盘空间

```shell
repo init -u https://github.com/exthmui-legacy/android.git -b exthm-12 --depth=1
repo sync
```

### 开始编译

```shell
. build/envsetup.sh
lunch exthm_[您的设备代号]-[构建类型]
make bacon
```
