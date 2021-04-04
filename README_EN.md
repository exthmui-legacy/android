# exTHmUI

## What’s exTHmUI?

![exthm logo](https://raw.githubusercontent.com/exthmui/android/exthm-10/logo.png)

exTHmUI is an open source Android project with Touhou element, based LineageOS. 

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
mkdir -p ~/bin
curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
sudo cp ~/bin/repo /bin/repo
sudo chmod a+x /bin/repo
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

### Initialize the exTHmUI source repository

> repo is a tool to manage multi repositories.

```shell
repo init -u https://github.com/exthmui/android.git -b exthm-10
```

You can also use following command to initialize, it may take up less space

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

# Initialize compiling environment
. build/envsetup.sh

# Initialize compiling device
lunch exthm_[YourDeviceCodename]-userdebug
# You can also use this command to initialize compiling devices.
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

> If you want to add other content, just repeat the steps (don't submit a new commit), but use `git commit --amend` instead of `git commit -m`. Gerrit will recognize it as a new commit set.

> To check the status of you and other commits, please visit [exTHmUI](https://review.exthmui.cn) code review.
