# 安装和测试ffmpeg过程中使用和测试的代码

## 安装ffmpeg和需要的包

### 安装ffmpeg

* 下载网址： https://ffmpeg.org/download.html

* 下载包版本： ffmpeg-4.3.6.tar.bz2

* 设置配置选项
    
    ./configure --prefix="/usr/local/ffmpeg/" --enable-gpl --enable-nonfree --enable-ffplay --enable-libfdk-aac --enable-libmp3lame --enable-libx264 --enable-libx265 --enable-filter=delogo --enable-debug --disable-optimizations --enable-libspeex --enable-shared --enable-pthreads --enable-version3 --enable-hardcoded-tables --extra-ldflags=-L/usr/local/ffmpeg/lib

* 编译和安装

    make
    make install


### 安装yasm

* 未安装会出现 nasm/yasm not found or too old. Use --disable-x86asm for a crippled build.错误

* 由于后面编程不需要导入头文件和对应的库，所以不需要用源码的方式安装。这里使用自带的方式

* sudo apt-get install yasm 

### 安装fdk-acc

* 未安装会出现 ERROR: libfdk_aac not found 错误

* 下载网址： https://jaist.dl.sourceforge.net/project/opencore-amr/fdk-aac/

* 下载包版本： fdk-aac-2.0.1.tar.gz

* 设置配置选项
    
    ./configure --prefix="/usr/local/ffmpeg/" --enable-shared

* 编译和安装

    make -j8  
    make install

* 如果ffmpeg还是一样的错误,但查看/usr/local/ffmpeg/lib中有库文件，则执行 export PKG_CONFIG_PATH=$PKG_CONFIG_PATH:/usr/local/ffmpeg/lib/pkgconfig/ 将库文件路径导入

### 安装mp3lame

* 未安装会出现 ERROR: libmp3lame >= 3.98.3 not found 错误

* 下载网址： https://sourceforge.net/projects/lame/

* 下载包版本： lame-3.100.tar.gz

* 设置配置选项
    
    ./configure --prefix="/usr/local/ffmpeg/" --enable-shared

* 编译和安装

    make -j8  
    make install

### 安装speex

* 未安装会出现 ERROR: speex not found using pkg-config

* 下载网址： https://sourceforge.net/projects/lame/

* 下载包版本： speex-1.2.0.tar.gz

* 设置配置选项
    
    ./configure --prefix="/usr/local/ffmpeg/"

* 编译和安装

    make -j8  
    make install


### 安装x264

* 未安装会出现 ERROR: libx264 not found

* 下载网址： wget https://code.videolan.org/videolan/x264/-/archive/master/x264-master.tar.bz2

* 设置配置选项
    
    ./configure --prefix="/usr/local/ffmpeg/" --enable-shared --disable-asm

* 编译和安装

    make -j8  
    make install

### 安装x265

* 未安装会出现 ERROR: libx264 not found

* 下载网址： http://ftp.videolan.org/pub/videolan/x265/

* 下载包版本： x265_3.2.tar.gz

* 设置配置选项
    
    cd /x265_3.2/build/linux
    ./make-Makefiles.bash
    
* 编译和安装

    make -j8  
    make install

### 安装ffplay需要的一下依赖库
sudo apt-get install libasound2-dev
sudo apt-get install libpulse-dev
sudo apt-get install libx11-dev
sudo apt-get install xorg-dev

### 安装SDL

* 安装ffmpeg后，会发现bin目录下是没有ffplay等应用程序，需要安装SDL

* 下载网址： https://github.com/libsdl-org/SDL/releases/latest

* 下载包版本： x265_3.2.tar.gz

* 设置配置选项
    
    ./configure --prefix="/usr/local/ffmpeg/" --enable-shared --enable-video-x11 --enable-x11-shared --enable-video-x11-vm
    
* 编译和安装

    make -j8  
    make install

### 增加可执行文件路径，增加连接口文件夹

* 修改 sudo vim /etc/profile 结尾增加 export PATH="/usr/local/ffmpeg/bin:$PATH"

* 修改 sudo vim /etc/ld.so.conf 结尾增加  /usr/local/ffmpeg/lib

* 加载配置 sudo ldconfig



