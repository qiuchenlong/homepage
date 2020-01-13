# ijkplayer 

#### Before build

- 安装git, yasm
    - Ubuntu 版本
    ```
    sudo apt update
    apt install git
    apt install yasm
    ```
  
- 下载安装ndk(版本需要是android-ndk-r10e)
    - 下载地址: https://developer.android.google.cn/ndk/downloads/older_releases.html#ndk-10c-downloads
  
  
- 配置环境变量
    - sdk, ndk
    ```
    // 1修改环境变量
    sudo vim /etc/profile
      
    export ANDROID_HOEM=/home/cyndi/Android/Sdk
    export PATH=$PATH:$ANDROID_HOEM/tools:$ANDROID_HOEM/platform-tools

    export ANDROID_NDK=/home/cyndi/android-ndk-r10e-linux-x86_64/android-ndk-r10e/
    export PATH=$PATH:$ANDROID_NDK
  
    // 2立即生效,需要重新打开terminator
    source /etc/profile
  
  
    // 
    ```

- 

#### build Android

```
// 下载仓库
git clone https://github.com/Bilibili/ijkplayer.git ijkplayer-android

// 切换到ijkplayer-android目录下
cd ijkplayer-android

// 创建最新版本的分支(k0.8.8)
git checkout -B latest k0.8.8

// 初始化脚本(拉取ffmpeg...)
./init-android.sh

// 切换目录
cd android/contrib

// 编译脚本,清空编译库
./compile-ffmpeg.sh clean

// 编译脚本,生成所有的编译库
./compile-ffmpeg.sh all

// 构建ijk所需要的库文件
cd ..
./compile-ijk.sh all

```