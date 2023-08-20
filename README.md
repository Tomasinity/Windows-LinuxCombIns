# Windows-LinuxCombIns
记录一下自己在笔记本上下载windows和linux双系统过程。  
  
查阅资料：
+ [win10和linux双系统安装步骤（详细!）](https://blog.csdn.net/weixin_43828196/article/details/103113966)
+ [笔记本装双系统！win10+Linux！所有的坑自己一个个爬过来，纪念一下](https://blog.csdn.net/u012173720/article/details/82729082)
+ [Win10和linux双系统怎么安装？Win10 linux双系统安装教程](https://blog.csdn.net/qq_28424679/article/details/78140378)
+ [安装ubuntu双系统分区教程](https://www.bilibili.com/read/cv20858614)

电脑型号：  
[华硕 天选4](https://item.jd.com/100058848085.html)，原系统win11，bios系统为uefi模式  

> 因为本人懒惰，本文全篇无图片而仅靠语言进行尽量详细的描述，请您做好实操并充分发挥想象力的准备；同时由于个体差别，本人遭遇可能和您的遭遇不同，因此推荐您配合搜索引擎和其他教程使用本文。

## 准备工作
### 制作ubuntu启动u盘
在[这里](https://ubuntu.com/download/desktop)下载ubuntu，我下载的版本是ubuntu 22.04.3 LTS；  
插入U盘，在win32diskimager中用默认设置将下载下来的文件写入U盘即可。注意U盘大小应大于写入所需空间，这里我在写入后查看发现使用空间大概在5G左右。  
注意这个时候U盘内已经是一个新的系统，在windows里不能也不应打开，所以此时出现的要格式化U盘窗口忽略就好。
### 准备磁盘空间
在笔记本磁盘中分出一块空闲区，50G是很充裕的选择，这里我分配了128G。

## 安装
开机时进入bios界面，在启动-【】中选择插入的U盘，保存退出后会进入gnu grub界面。可能是因为版本更新或者是默认集成显卡的原因，我并没有遇到N卡死机的问题，故直接选择第一个选项。稍等片刻就自动进入了安装界面。按自己偏好选择，直到来到安装类型。这里选择其他选项后继续，遂来到分配分区界面。选择自己分出来的空闲区，具体方案如下：  
+ 交换区域(swap area)：大小设置为电脑内存大小，逻辑分区，Use as选择交换区域(若语言选择英文则:swap area)
+ /：根目录，用于存放系统，这里我设置了32G，主分区，Use as默认选择第一个即可(ext4日志文件系统 Ext4 journaling File system)（下同），最下面mount point栏输入"/"
+ /boot：引导分区，这里我设置了1G，逻辑分区或主分区都可。
+ /home:用户存储数据用分区，剩下的内存全部给它即可，逻辑分区。
设置完了之后即可开始安装，之后还会出现使用Active Directory选项框，但本人未勾选。
之后进入mok界面，因为未遇到N卡驱动问题所以直接选择第一个选项。此之后安装基本完成。

## 后续工作
