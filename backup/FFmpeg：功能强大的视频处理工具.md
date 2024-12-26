### 项目介绍
&emsp;&emsp;FFmpeg是一组用来处理多媒体内容（如音频、视频、字幕和相关元数据）的库和工具集合，能够执行多种视频功能，比如视频格式转换、压缩、拼接、添加水印，甚至可以处理声音、录屏、Gif动图转换等。

### 项目亮点

- 免费且功能齐全
- 命令行工具，体积小巧
- 所有平台均可通用

### 相关链接

- GitHub·：https://github.com/FFmpeg/FFmpeg
- 官网：https://ffmpeg.org/
- 介绍视频-抖音（大神开发）：7.41 12/31 K@W.Zm FuF:/ FFmpeg 最最强大的视频工具 FFmpeg 最最强大的视频工具 (转码/压缩/剪辑/滤镜/水印/录屏/Gif/...)。# 科技 # 计算机 # 编程 # 软件开发 # 学习  https://v.douyin.com/iUvXKxq8/ 复制此链接，打开Dou音搜索，直接观看视频！

### 示例（Ubuntu）

1. 安装软件： `sudo apt update` and `sudo apt install ffmpeg`
2. 验证安装：`ffmpeg -version`
3. 转换视频：`ffmpeg -i input.avi output.mp4`
4. 转换音频：`ffmpeg -i input.wav output.mp3`
5. 压缩视频：`ffmpeg -i input.avi -c:v libx264 -crf 22 output.mp4`，-c:v：编码格式，-crf：视频质量（常用19~28）
6. 缩放旋转：`ffmpeg -i input.avi -c:v libx264 -vf "scale=256:256,transpose=1" output.mp4`，-vf：过滤器，scale：缩放，transpose：旋转，crop：裁剪······等
7. 剪切视频：`ffmpeg -i input.avi -c:v libx264 -ss 00:00:03 -t 00:00:05 output.mp4`，-ss：起始位置，-t：时长，-to：终止位置
8. 合并视频：先将视频以一行行的格式列举在一个文件中，再进行操作>>>`ffmpeg -f concat -i mylist.txt -c copy output.mp4`，-f concat：合并，-c copy：不进行编码保存原来格式（可替换成其他操作，如编码）
9. 音频处理：`ffmpeg -i input.mp4 -af "loudnorm=I=-5:LRA=1" output.mp4`，-af：音频过滤器，loudnorm：统一音量
10. 删除音频：`ffmpeg -i input.mp4 -an output.mp4`
11. 删除视频轨：`ffmpeg -i input.mp4 -vn output.mp4`
12. 删除字幕：`ffmpeg -i input.mp4 -sn output.mp4`
13. 删除数据流：`ffmpeg -i input.mp4 -dn output.mp4`
14. 创建视频缩略图：`ffmpeg -i input.mp4 -vf "fps=1/10,scale=-2:720" thumbnail-%03d.jpg`，-fps指定输出文件的帧率，scale：指定输出图像的大小
15. 添加水印：`ffmpeg -i input.mp4 -i shuiyin.jpg -filter_complex="overlay=100：100" output.mp4`，-filter_complex="overlay"：指定过滤器overlay用水印叠加再原始视频的上面与水印的位置
16. GIF动图转换：`ffmpeg -i input.mp4 -ss 0 -t 3 -filter_complex [0:v]fps=15,scale=-1:256,split[a][b];[a]palettegen[p];[b][p]paletteuse output.gif`
17. 屏幕录制：`ffmpeg -hile_banner -loglevel error -stats -f gdigrab -framerate 60 -offset_x 0 -offset_y 0 -video_size 1920x1080 -draw_mouse 1 -i desktop -c:v libx264 -r 60 -preset ultrafast -pix_fmt yuv420p -y screen_record.mp4`
18. 更多功能请查看官方文档