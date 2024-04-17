# 一些操作命令和概念的记录

## 当前主流的封装格式(百度查的)

* MP4 (MP4是一种较为全面的容器格式，被认为可以嵌入任何形式的数据)

* AVI (简单易懂的开发API)

* FLV (是一种流行的流媒体格式，广泛用于网络视频应用)

* TS (它广泛应用于数字广播系统，例如我们日常使用的数字机顶盒接收到的就是TS流)

* M3U8 (M3U8文件是一种使用UTF-8编码的Unicode版本的M3U文件)

## 提供的工具介绍

* ffmpeg (对多媒体文件封装/复用，编码/解码，转换等)

* ffplay (多媒体播放器，支持超多种格式)

* ffprobe (多媒体的解析工具，用于了解多媒体中的格式等)

### 常用操作

#### ffplay

* ffplay -window_title "ks" house1.flv 播放本地流

* ffplay http://ivi.bupt.edu.cn/hls/cctv1hd.m3u8 播放网络流(测试会连接超时，待定)

* ffplay -f rawvideo -video_size 640x360 ???.yuv 播放视频裸数据(-f等几个参数必须，且高宽需正确)

#### ffprobe

* ffprobe -show_packets -show_data house1.flv 查看某个文件的包和二进制数据

-show_format 查看封装格式
-show_frames 查看视频文件的帧信息
-show_streams 查看视频文件的流信息
-of json -show_format 以json的形式展示

#### ffmpeg

* ffmpeg -h full 查看支持的操作

* ffmpeg -i house_of_ruin.mp4 house1.flv 将某文件的压缩格式修改，保持编码格式不变

##### 分解/复用命令

* ffmpeg -i house1.flv -vcodec copy -acodec copy out.avi 将flv解封装，编码解码不变，然后重新封装为avi。(当音频和视频编解码都不变时可以写成 -c cpoy == -vcodec copy -acodec copy)

* ffmpeg -i house_of_ruin.mp4 -vn -acodec copy out.aac 从flv中解封装获取音频文件，编解码不变，不要视频文件。flv是不能直接获取的aac的。

* ffmpeg -i house_of_ruin.mp4 -an -vcodec copy out.h264
从flv中解封装获取视频文件，编解码不变，不要音频文件

##### 编码/解码命令
##### 裁剪/合并命令
##### 图片/视频互转命令

##### 非经常使用(用的时候百度)
* 录制命令
* 直播命令
* 滤镜处理命令