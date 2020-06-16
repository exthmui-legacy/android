**中文｜[English](https://github.com/exthmui/android/blob/exthm-10/README_EN.md)**
# exTHmUI
## 什么是 exTHmUI ？
![](https://raw.githubusercontent.com/exthmui/android/exthm-10/logo.png)

这是一个由国内东方众自行发起制作的基于 [LineageOS](https://github.com/LineageOS) 的含有东方 Project 的类原生 Android 项目。

## 源码更新日志
<details markdown='1'><summary>展开/收起更新日志</summary>

2020/6/12 
1. Merge 'lineage/lineage-17.1' 远程仓库内的改动于exthm-10分支

2020/5/26 
1. 加入中国本地化 libphonenumber库

2020/5/25
1. prebuilt: init: chown for Smart charging
2. ThemeManager启用了新UI

2020/5/15 
1. 移除了DanmakuNotification仓库
2. 移除了crDroid remote
3. Merge 'lineage/lineage-17.1' 远程仓库内的改动于exthm-10分支
4. 跟进exthm的 lottie repo

2020/5/7
1. 修复了ThemeManager的权限问题

2020/5/6
1. ThemeManager加入了字体支持，强制壁纸居中显示

2020/5/3
1. ThemeManager加入了开机动画支持

2020/4/29
1. 跟进exthm的sepolicy repository
2. 选定了exthm的默认壁纸

目前仅记录到2020/4/29，后续将补齐更新日志，敬请谅解
</details>

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
> [方括号]内为可选参数，可以根据网络情况按需使用。
```shell
# -j参数为下载线程数，不带该参数默认自动分配线程，-l参数用于更新本地存储库，--fail-fast参数可以处理上次repo时由于网络原因导致的同步失败问题，--force-sync参数忽略本地修改，强制同步git仓库的内容。
repo sync [-j8 --fail-fast --force-sync]
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
