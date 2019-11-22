#### FFmpeg 命令笔记

###### 1.视频转码（转为h264,码率5000K，帧率30,音频aac） 
```
ffmpeg -i 1.mp4 -vcodec h264 -b:v 5000k -r 30 -acodec aac out.mp4
```
###### 2.视频合并（各个片段视频必须为ts格式）
```
ffmpeg -i concat:"1.ts|2.ts" -c copy out.mp4 //原各个视频不做转码
```
###### 3.从视频中提取帧图片(劫取0.1秒处截图)
```
 ffmpeg -ss 0.1 -i E:\allin_video\ZhiNengWaiHu.mp4 -f image2 -y 1.jpg
```