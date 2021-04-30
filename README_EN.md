**[中文](https://github.com/exthmui/android/blob/exthm-11/README.MD) | English**

# exTHmUI

## What’s exTHmUI?

![exthm logo](https://raw.githubusercontent.com/exthmui/android/exthm-11/logo.png)

exTHmUI is an open source Android project with Touhou element, based on LineageOS. 

> Branch exthm-9 now is no longer maintained. Please using branch exthm-10 to compile.

## How to build exTHmUI?

> This guide takes Debian for example.

### Install dependencies

```shell
sudo apt-get install bc bison build-essential ccache curl flex g++-multilib gcc-multilib git gnupg gperf imagemagick lib32ncurses5-dev lib32readline-dev lib32z1-dev liblz4-tool libncurses5 libncurses5-dev libsdl1.2-dev libssl-dev libxml2 libxml2-utils lzop pngcrush rsync schedtool squashfs-tools xsltproc zip zlib1g-dev
```

- Ubuntu lower than 20.04 needs `libwxgtk3.0-dev` also.
- Ubuntu lower than 16.04 needs `libwxgtk2.8-dev` also.

### Install repo

```shell
mkdir -p $HOME/bin
curl https://storage.googleapis.com/git-repo-downloads/repo > $HOME/bin/repo
chmod +x $HOME/bin/repo
echo "if [[ \$PATH != *"\$HOME/bin"* ]]; then PATH=\$HOME/bin:\$PATH ; fi" >> .bashrc
```

### Set up GitHub username and email (replace it to yours)

```shell
git config --global user.email "xxx@xxx.com"
git config --global user.name "xxx"
```

### Create workspace

> This workspace means the path to storage the source code of exTHmUI.

```shell
# Create dictionary to storage the source code of exTHmUI.
# ~/ is HOME path
# User path is /home/username
# The following exTHmUI is just a folder nam, you can custom it by yourself
mkdir ~/exTHmUI
cd ~/exTHmUI
```

### Initialise the exTHmUI source repository

> repo is a tool to manage multiple repositories.

```shell
repo init -u https://github.com/exthmui/android.git -b exthm-10
```

You can also use following command to initialise, it may take up less space.

```shell
# depth=1 means NOT to sync history commits
repo init -u https://github.com/exthmui/android.git -b exthm-10 --depth=1
```

### Sync the source code

> Arguments in [] are optional. You can use it depending on your network status.

```shell
repo sync [-j8 --fail-fast --force-sync]
```

### Start building

```shell
# Make sure that current path is the root path of source code of exTHmUI

# Initialise compiling environment
. build/envsetup.sh

# Initialise compiling device
lunch exthm_[YourDeviceCodename]-userdebug
# You can also use this command to initialise compiling devices.
breakfast [YourDeviceCodename]

# Start building
mka bacon
```

# Submit commit
> We welcome developers to submit commits in Gerrit, you can use the following command to submit commits:
```
     cd <project>
     <make edits>
     git add -A
     git commit -m "commit information"
     git push ssh://<username>@review.exthmui.cn:29418/<project> HEAD:refs/for/exthm-11
```

> Commit can be submitted with one submission. Use the following command to compress multiple commits: `git rebase -i HEAD~<number of commits>`

> If you want to add other contents, just repeat the steps (don't submit a new commit), but use `git commit --amend` instead of `git commit -m`. Gerrit will recognise it as a new commit set.

# How to submit to Gerrit Using SSH
> [Generate local key](https://docs.github.com/articles/generating-an-ssh-key/)
```
     ssh-keygen -t rsa -C <youremail>

```
> Get the key & Copy the printed output
```
     cat ~/.ssh/id_rsa.pub

```
>Upload the key to gerrit
![Gerrit ssh](https://img-blog.csdnimg.cn/20181106150940882.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3pob3Vsd18yNQ==,size_16,color_FFFFFF,t_70)
```
     1. Go to the SSH key panel & paste the output into add SSH public key.
     2. Click Add Button.
     3. Get the reply from gerrit in your mail.
     Enjoy!

```



> To check the status of yours and others commits, please visit [exTHmUI](https://review.exthmui.cn) code review.
