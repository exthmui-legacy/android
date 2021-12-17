**中文｜[English](https://github.com/exthmui/android/blob/exthm-12/README_EN.md)**

# exTHmUI

## 什么是 exTHmUI ？

![exthm logo](https://i.niupic.com/images/2020/06/16/8gWB.png)

这是一个由国内爱好者自行发起制作，以本地化、流畅还有东方化（？？还没实现呢啊喂）为特色的开源类原生 Android 项目，基于 [AOSP](https://android.googlesource.com/)

> exthm-11 EOL 时间为 2022 年中旬，届时请迁移至 exthm-12 或更新的分支

> 本分支基于 AOSP / Arrow OS Port 开发。

> 作者的一些心里话：从各种意义上来说咱这个**不是同人作品**，它只是我的一种特殊的表达方式（？有点表述不清），但是我至少还是实现了它圆了我当初的梦想。因为我不会绘画，也无钱钱去请画师，目前的UI都还非常AOSP不够东方化（我自裁呜呜呜QAQ），各种美术资源都是在联系作者申明授权后公开使用的。如果有人想提供UI界面美术资源或者提建议，请在本 repo 内提 issue 或者发送邮件至 dingwenxuan4@gmail.com ,非常感谢DA⭐ZE~

> 非常感谢 [Shelling](https://github.com/cjybyjk), [ReallySnow](https://github.com/ReallySnow)，[ArrowOS](https://github.com/ArrowOS)和 [DerpFest团队](https://github.com/DerpFest-11)提供的技术支持！


## 同步源码

> repo 是一种用于管理多个 Git 仓库的工具

要开始编译 exTHmUI，你需要熟悉 Repo 和 Git

要开始同步源码，请使用这些命令

```shell
repo init -u https://github.com/exthmui/android.git -b exthm-12
repo sync
```

您也可以使用如下命令来初始化仓库，这样可以节省磁盘空间

```shell
repo init -u https://github.com/exthmui/android.git -b exthm-12 --depth=1
repo sync
```

### 开始编译

```shell
. build/envsetup.sh
lunch exthm_[您的设备代号]-[构建类型]
make bacon
```

## 向 exTHmUI 贡献提交

我们欢迎开发者通过 [Gerrit](https://www.gerritcodereview.com/) 参与到 exTHmUI 的开发中，请访问 [exTHmUI Code Review](https://review.exthmui.cn/)（目前不可用）

## 查阅 wiki

如果对详细的系统介绍和编译有兴趣，欢迎访问我们的 [Wiki](https://wiki.exthmui.cn/)
