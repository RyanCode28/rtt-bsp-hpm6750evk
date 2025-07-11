# 简介

本例程演示基于RT-Thread音频驱动框架使用I2S外设和板载codec芯片sgtl5000实现录音和播放功能。

## 硬件设置

- 安装SD卡或者eMMC转TF卡至开发板SD卡卡槽(U11)
- 连接耳机至codec芯片的HP_MIC接口(J14)， 该接口标准为CTIA， 请使用对应标准的耳机
- 使用3.5mm音频数据线连接音频播放源至codec的LINE_IN接口(J17)
- 下载例程并运行，若卡被成功识别，则例程会打印如下所示的容量等信息

```console
 \ | /
- RT -     Thread Operating System
 / | \     5.0.1 build May 15 2023 17:44:01
 2006 - 2022 Copyright by RT-Thread team
msh />found part[0], begin: 32256, size: 28.907GB

msh />sd0 mounted to /

```

## 注意事项

- SD/eMMC卡必须被格式化FAT32格式


## 支持的命令

```console
RT-Thread shell commands:
codec_recordwav  - codec record sound to wav file
codec_playwav    - codec play wav file
reset            - reset the board
clear            - clear the terminal screen
version          - show RT-Thread version information
list             - list objects
help             - RT-Thread shell help.
ps               - List threads in the system.
free             - Show the memory usage in the system.
ls               - List information about the FILEs.
cp               - Copy SOURCE to DEST.
mv               - Rename SOURCE to DEST.
cat              - Concatenate FILE(s)
rm               - Remove(unlink) the FILE(s).
cd               - Change the shell working directory.
pwd              - Print the name of the current working directory.
mkdir            - Create the DIRECTORY.
mkfs             - format disk with file system
mount            - mount <device> <mountpoint> <fstype>
umount           - Unmount the mountpoint
df               - disk free
echo             - echo string to file
tail             - print the last N - lines data of the given file
pin              - pin [option]
date             - get date and time or set (local timezone) [year month day hour min sec]
```

## 运行现象
使用`codec_recordwav /sample.wav`命令, 录制LINE_IN线上的一段音频以wav格式保存在SD卡
```console
msh />codec_recordwav /test.wav
record 10s audio data to wav file:
samplerate: 16000
samplebits: 16
channel number: 1
```
使用`codec_playwav /sample.wav`命令, 播放sd卡中的wav, 通过耳机可听到声音
```console
msh />codec_playwav /test.wav
wav information:
time: 10s
samplerate: 16000
samplebits: 16
channel: 1
```

