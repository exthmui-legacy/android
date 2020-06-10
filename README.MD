# exTHmUI

## 什么是 exTHmUI ？
![](https://raw.githubusercontent.com/exthmui/android/exthm-10/logo.png)

这是一个由国内东方众自行发起制作的基于 [LineageOS](https://github.com/LineageOS) 的含有东方 Project 的类原生 Android 项目。

## 如何编译 exTHmUI ？
> 该向导以 Debian 系 Linux 为例
### 安装相关依赖
```shell
sudo apt-get install bc bison build-essential ccache curl flex g++-multilib gcc-multilib git gnupg gperf imagemagick lib32ncurses5-dev lib32readline-dev lib32z1-dev liblz4-tool libncurses5-dev libsdl1.2-dev libssl-dev libwxgtk3.0-dev libxml2 libxml2-utils lzop pngcrush rsync schedtool squashfs-tools xsltproc zip zlib1g-dev repo
```

### 新建工作区
> 这里的工作区指存放 exTHmUI 源码的路径

```shell
# 新建文件夹用来存放 exTHmUI 源码
# ~/指用户目录
# 用户目录指 /home/用户名
# 此处的 exTHmUI 为文件夹名，可自定义
mkdir ~/exTHmUI
cd ~/exTHmUI
```

### 初始化仓库
> repo 是一个用来管理多个仓库的工具

```shell
repo init -u https://github.com/exthmui/android.git -b exthm-10
```
您也可以使用如下命令来初始化仓库，这样可以节省磁盘空间
```shell
# depth=1 表示不同步历史提交
repo init -u https://github.com/exthmui/android.git -b exthm-10 --depth=1
```

### 同步源码
```shell
repo sync
```

### 开始编译
```shell
# 确保当前所在目录为 exTHmUI 源码根目录

# 初始化编译环境
. build/envsetup.sh

# 初始化编译设备
lunch exthm_[您的设备代号]-userdebug
# 您也可以使用该命令初始化编译设备
breakfast [您的设备代号]

# 开始编译
mka bacon
```
