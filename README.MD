**中文｜[English](https://github.com/exthmui/android/blob/exthm-10/README_EN.md)**

# exTHmUI

## 什么是 exTHmUI ？

![exthm logo](https://i.niupic.com/images/2020/06/16/8gWB.png)

这是一个由国内东方众自行发起制作的基于 [LineageOS](https://github.com/LineageOS) 的含有东方 Project 的类原生 Android 项目。

> exthm-9 分支已停止维护，请使用 exthm-10 分支进行编译

## 如何编译 exTHmUI ？

### 安装相关依赖

#### Debian系（以Ubuntu为例）

```shell
sudo apt-get install bc bison build-essential ccache curl flex g++-multilib gcc-multilib git gnupg gperf imagemagick lib32ncurses5-dev lib32readline-dev lib32z1-dev liblz4-tool libncurses5 libncurses5-dev libsdl1.2-dev libssl-dev libxml2 libxml2-utils lzop pngcrush rsync schedtool squashfs-tools xsltproc zip zlib1g-dev
```

- 低于 20.04 的 Ubuntu，还需安装：`libwxgtk3.0-dev`
- 低于 16.04 的 Ubuntu，还需安装：`libwxgtk2.8-dev`

##### 安装 repo

```shell
mkdir -p ~/bin
curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
sudo cp ~/bin/repo /bin/repo
sudo chmod a+x /bin/repo
```

#### Arch系（Archlinux/Manjaro等）
```
cd ~/
git clone https://github.com/akhilnarang/scripts
cd scripts
./setup/arch-manjaro.sh
```

### 修改AOSP为国内源（可选）

```
git config --global url.https://mirrors.tuna.tsinghua.edu.cn/git/AOSP/.insteadof https://android.googlesource.com

repo的运行过程中会尝试访问官方的git源更新自己，如果想使用tuna的镜像源进行更新，可以将如下内容复制到你的~/.bashrc里或者是直接运行
export REPO_URL='https://mirrors.tuna.tsinghua.edu.cn/git/git-repo'
```
> 或者是修改.repo/manifests.git/config内的
```
url = https://android.googlesource.com/platform/manifes
改为
url = https://mirrors.tuna.tsinghua.edu.cn/git/AOSP/platform/manifest
```
### 设置 Git 用户名及邮箱（替换成自己的）

```shell
git config --global user.email "xxx@xxx.com"
git config --global user.name "xxx"
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
# -j 参数为下载线程数，不带该参数默认自动分配线程
# -l 参数用于更新本地存储库
# --fail-fast 参数可以处理上次repo时由于网络原因导致的同步失败问题
#--force-sync 参数忽略本地修改，强制同步git仓库的内容。
repo sync [-j8 --fail-fast --force-sync]
参考同步命令
repo sync -j$(nproc --all) -c -j$(nproc --all) --force-sync --no-clone-bundle --no-tags
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
