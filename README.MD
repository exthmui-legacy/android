**中文｜[English](https://github.com/exthmui/android/blob/exthm-11/README_EN.md)**

# exTHmUI

## 什么是 exTHmUI ？

![exthm logo](https://i.niupic.com/images/2020/06/16/8gWB.png)

这是一个由国内东方众自行发起制作的基于 [LineageOS](https://github.com/LineageOS) 的含有东方 Project 的类原生 Android 项目。

> exthm-10 EOL 时间为2021年底，届时请迁移至本exthm-11分支
> 很抱歉让大家失望了qwq
> 因为一些原因我们未能实现当初的基于AOSP的想法，因此本11分支将继续基于LineageOS
> AOSP基线为android-11.0.0_r29,LineageOS基线为18.1

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
mkdir -p $HOME/bin
curl https://storage.googleapis.com/git-repo-downloads/repo > $HOME/bin/repo
chmod +x $HOME/bin/repo
echo "if [[ \$PATH != *"\$HOME/bin"* ]]; then PATH=\$HOME/bin:\$PATH ; fi" >> .bashrc
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
repo init -u https://github.com/exthmui/android.git -b exthm-11
```

您也可以使用如下命令来初始化仓库，这样可以节省磁盘空间

```shell
# depth=1 表示不同步历史提交
repo init -u https://github.com/exthmui/android.git -b exthm-11 --depth=1
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

### 提交commit
> 我们欢迎开发者在Gerrit提交commit，你可以使用以下命令提交commit：
```
    cd <project>
    <make edits>
    git add -A
    git commit -m "commit信息"
    git push ssh://<username>@review.exthmui.cn:29418/<project> HEAD:refs/for/exthm-11
```
# 如何使用SSH提交到Gerrit
> 首先生成SSH密钥
```
     git config --global user.email "xxx@xxx.com"
     git config --global user.name "xxx"
     ssh-keygen -t rsa
     然后后面的提示一路回车即可

```
> 复制密钥
```
     cat ~/.ssh/id_rsa.pub

```

>配置ssh key
![Gerrit ssh](https://img-blog.csdnimg.cn/20181106150940882.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3pob3Vsd18yNQ==,size_16,color_FFFFFF,t_70)
```
     首先打开exTHmUI代码审查(下面有) -> 点击右上角的Sign in -> 再点击Github OAuth2那一行使用git登录 
     然后点击右上角的设置 (齿轮图标)

     1.找到Email Addresses部分 添加您的邮箱

     2.在您的邮件收件箱找到Gerrit的验证邮件, 点击它通过验证

     3.转到SSH Keys部分将密钥输出内容粘贴到SSH Keys中的New SSH Keys输入框中

     4.点击添加按钮 (即 ADD NEW SSH KEY), 然后点击SAVE CHANGES

     5.稍后您的邮件中收到Gerrit的答复.

     好耶!!

```


>推送提交至审核服务器

所需文件: [commit-msg](https://review.exthmui.cn/tools/hooks/commit-msg)

```
     1. 首先进入到带有您要推送更改提交的源码目录

     2. 添加远程服务器 输入git remote add gerrit <审核服务器地址>/源码目录的仓库名称
         < 例如 git remote add gerrit https://review.exthmui.cn/android >

     3. 设置Change-Id功能
         3-1: 下载commit-msg文件 并将它移动至 <源码目录/.git/hooks> 下
         3-2: 输入 chmod a+x .git/hooks/commit-msg
     
     4. 将您要修改好的文件添加到暂存区, 并写好提交描述
         * 如果先前修改好的提交可以使用 git commit --amend 重新提交

     5. 然后将提交推送到审核服务器
         即 git push ssh://<用户名>@<代码审查服务器地址>:<端口>/<仓库名称> HEAD:refs/for/<分支>
         * 例如 < git push ssh://builder@review.exthmui.cn:29418/android HEAD:refs/for/exthm-11 >

     6. 出现 SUCCESS 即推送完成, 待审查人与审稿人测试无误后即可合并

     好耶!!

```


> 一次提交即可提交commit。使用以下命令压缩多个提交：`git rebase -i HEAD~<提交数量>`

> 如果您要添加其他内容，只需重复步骤（不要提交新的commit），而是使用`git commit --amend`代替`git commit -m`。Gerrit会将其识别为新的commit集。

> 要查看您和其他commit的状态，请访问[exTHmUI](https://review.exthmui.cn)代码审查。
