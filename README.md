# Hardware-Sync-of-Robosense-and-Xsense-MTI-300
Robosense雷达和Xsense MTI-300的硬件时间同步方案

本项目主要工作是进行了Robosense雷达和Xsense MTI-300的硬件时间同步

准备工作：
1. MTI-300的硬件接口和时间同步方法



官网说明了MTI-300的硬件时间同步方法
https://base.xsens.com/hc/en-us/sections/201296842-Algorithms-Data

2. 
![Robosense GPS同步接口](https://github.com/YangTiankai/Hardware-Sync-of-Robosense-and-Xsense-MTI-300/blob/master/readmefile/LidarGPS.PNG)

系统工作流程如下：
1. MTI-300的时钟输出
MTI-300的硬件时间同步方法在官网有说明

https://base.xsens.com/hc/en-us/articles/211592185

在上位机配置SyncIn引脚为StartSample功能，在上电后3秒后，使用stm32的PA6引脚向MTI-300的SyncIn引脚输入一个上升沿脉冲，此时MTI-300将向外输出数据
在上位机配置MTI-300的SyncOut引脚为脉冲输出功能，将其配置为能够输出频率1Hz，脉宽200ms的矩形波

3. 将MTI-300的SyncOut引脚接到Robosense雷达的GPS接口的PPS引脚上

4. 将MTI-300的SyncOut引脚接入stm32单片机的PC4引脚，每检测到一个上升沿脉冲，向Robosense雷达的GPS接口的串口接收RXD引脚发送一个串口包，该串口包是模拟GPS设备的GPRMC规范








