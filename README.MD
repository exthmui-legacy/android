## EXTHMUI
![](logo.jpg)


#下载源码

安装repo
```
sudo apt install repo
```

安装Git
```
sudo apt install git
```
安装jdk
```
sudo apt install openjdk-8-jdk
```
初始化repo
```
repo init https://github.com/exthmui/android.git -b exthm-9
repo init https://github.com/exthmui/android.git -b exthm-9 --depth=1  //更快的下载速度
```
同步源码
```
repo sync -c -j$(nproc --all) --force-sync --no-clone-bundle --no-tags
```
配置编译环境
```
git clone  https://github.com/akhilnarang/scripts 
cd scripts && bash setup/android_build_env.sh
```
初始化编译
```
. build/envsetup.sh
```
初始化设备
```
lunch lineage_你的设备代号-userdebug
```
编译
```
mka bacon -j8
```
#提交更改
```
cd <项目目录>
git add .
git commit -m “提交内容”
git push -u origin <目标分支>
```