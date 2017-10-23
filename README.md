# LivePusher覆盖现阶段流行的音视频采集技术
整个视频直播开发流程技术如下：

![images](https://github.com/ambitious09/LivePusher/blob/master/live.png)

来认识一下视频编码格式:
代表软编码器------openh264、x264
	
![](https://github.com/ambitious09/LivePusher/blob/master/%E6%A0%BC%E5%BC%8F.png)
Profile     		:      baseline main high
Level          		:	限制了码率上限
Resolution 		:	分辨率
Bitrate        		:	码率,与数据大小成正比
Frame Rate 		:	帧率,每秒多少帧图像，影响流畅度
Frame Interval		:	关键帧间隔
RTMP
Real Time Message Protocol(实时信息传输协议)
基于TCP的应用层协议
视频包
	1、解码信息包(sps与pps)
	2、数据包
音频包
	1、解码信息包
	2、数据包
摄像头采集图像时候格式

# y1   y2     y3    y4   
# y5   y6     y7    y8   
# y9   y10   y11   y12
# y13 y14    y15    y16
# v1   u1     v2    u2
# v3   u3     v4    u4

即:y有4x4=16个字节的长度
v在y数据完后紧跟着y数据，与u数据交替出现。
v、u长度都为 16/4 = 4。
以上基本的定义
