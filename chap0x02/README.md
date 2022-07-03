## 1 Ubuntu 20.04与CentOS操作对比
|     |Ubuntu20.04|CentOS|
|-----|---|---|
|安装`tmux`|`sudo apt install tmux`|`yum install tmux`|
|查看`tmux`安装路径|`dpkg -L tmux`|`find / -name *tmux*`|
|安装`tshark`|`sudo apt install wireshark`<br> `sudo apt install tshark`|`yum install wireshark`|
|查看`tshark`安装路径|`dpkg -L tshark`|``find / -name *wireshark*``|
|卸载`tshark`|`sudo apt remove tshark` <br>`sudo apt remove wireshark`|`yum remove wireshark`|
|寻找文件名中包含666|`sudo find / -name "*666*"`|`find / -name "*666*"`|
|寻找文件内容中包含666|`sudo grep -r "666"./ --exclude=*.cast`|`find.| xargs grep -ri "666" `|
|gzip|` gzip {{file.ext}}`压缩<br>`gzip -d {{file.ext}}.gz`解压缩|` gzip {{file.ext}}`压缩<br>`gzip -d {{file.ext}}.gz`解压缩|
|bzip2|` bzip2 {{path/to/file_to_compress}}`压缩<br>` bzip2 -d {{path/to/compressed_file.bz2}}`解压缩|` bzip2 {{path/to/file_to_compress}}`压缩<br>` bzip2 -d {{path/to/compressed_file.bz2}}`解压缩|
|zip|`zip {{file}}`压缩<br>`unzip {{file.zip}}`解压缩|`zip {{file}}`压缩<br>`unzip {{file.zip}}`解压缩|
|tar|`tar cf {{target.tar}} {{file1}}`压缩<br> ` tar xvf {{source.tar[.gz|.bz2|.xz]}}`解压缩|`tar cf {{target.tar}} {{file1}}`压缩<br> ` tar xvf {{source.tar[.gz|.bz2|.xz]}}`解压缩|
|7z| `7z a {{path/to/archive.7z}}`压缩<br>`7z x {{path/to/archive.7z}}`解压缩|`7za a {{path/to/archive.7z}}`压缩<br>`7za x {{path/to/archive.7z}}`解压缩|
|CPU信息|`cat /proc/cpuinfo`|`cat /proc/cpuinfo`|
|内存大小|`free`|`free`|
|硬盘数量与硬盘容量|`sudo fdisk -l | grep Disk` |`fdisk -l | grep Disk`|


## 2 asciinema分段录屏记录
### 2.1 Ubuntu 20.04录屏
#### 2.1.1 软件包管理
[Ubuntu 20.04 【软件包管理】操作](https://asciinema.org/a/501079)
[![asciicast](https://asciinema.org/a/501079.svg)](https://asciinema.org/a/501079)
#### 2.1.2 文件管理
[Ubuntu 20.04 【文件管理】操作：构造测试数据集](https://asciinema.org/a/504932)
[![asciicast](https://asciinema.org/a/504932.svg)](https://asciinema.org/a/504932)
[Ubuntu 20.04 【文件管理】操作：查找“666”](https://asciinema.org/a/504935)
[![asciicast](https://asciinema.org/a/504935.svg)](https://asciinema.org/a/504935)
#### 2.1.3 文件压缩与解压缩
[Ubuntu 20.04 【文件压缩与解压缩】操作：tar](https://asciinema.org/a/505293)
[![asciicast](https://asciinema.org/a/505293.svg)](https://asciinema.org/a/505293)
[Ubuntu 20.04 【文件压缩与解压缩】操作：gzip](https://asciinema.org/a/505294)
[![asciicast](https://asciinema.org/a/505294.svg)](https://asciinema.org/a/505294)
[Ubuntu 20.04 【文件压缩与解压缩】操作：bzip2](https://asciinema.org/a/505336)
[![asciicast](https://asciinema.org/a/505336.svg)](https://asciinema.org/a/505336)
[Ubuntu 20.04 【文件压缩与解压缩】操作：7z](https://asciinema.org/a/505339)
[![asciicast](https://asciinema.org/a/505339.svg)](https://asciinema.org/a/505339)
[Ubuntu 20.04 【文件压缩与解压缩】操作：zip与unzip](https://asciinema.org/a/504950)
[![asciicast](https://asciinema.org/a/504950.svg)](https://asciinema.org/a/504950)
#### 2.1.4 子进程管理实验
子进程管理跟练录制了两遍，但最后exit时都是显示没有记录，猜测可能中间杀死进程时误杀了，所以把跟练过程截图如下：
[!图片1](./image/%E5%9B%BE%E7%89%871.png)
[!图片2](./image/%E5%9B%BE%E7%89%872.png)
[!图片3](./image/%E5%9B%BE%E7%89%873.png)
[!图片4](./image/%E5%9B%BE%E7%89%874.png)
[!图片5](./image/%E5%9B%BE%E7%89%875.png)
[!图片6](./image/%E5%9B%BE%E7%89%876.png)
#### 2.1.5 硬件信息获取
[Ubuntu 20.04 【硬件信息获取】操作：CPU信息](https://asciinema.org/a/505356)
[![asciicast](https://asciinema.org/a/505356.svg)](https://asciinema.org/a/505356)
[Ubuntu 20.04 【硬件信息获取】操作：内存大小、硬盘数量与硬盘容量](https://asciinema.org/a/505357)
[![asciicast](https://asciinema.org/a/505357.svg)](https://asciinema.org/a/505357)

### 2.2 CentOS录屏
#### 2.2.1 软件包管理
[CentOS 【软件包管理】操作：安装tmux，查看tmux安装路径](https://asciinema.org/a/505372)
[![asciicast](https://asciinema.org/a/505372.svg)](https://asciinema.org/a/505372)
[CentOS 【软件包管理】操作：安装tshark](https://asciinema.org/a/505374)
[![asciicast](https://asciinema.org/a/505374.svg)](https://asciinema.org/a/505374)
[CentOS 【软件包管理】操作：查找tshark安装路径，卸载tshark](https://asciinema.org/a/505378)
[![asciicast](https://asciinema.org/a/505378.svg)](https://asciinema.org/a/505378)
#### 2.2.2 文件管理
[CentOS【文件管理】操作：构造测试数据集](https://asciinema.org/a/505380)
[![asciicast](https://asciinema.org/a/505380.svg)](https://asciinema.org/a/505380)
[CentOS 【文件管理】操作：查找“666”](https://asciinema.org/a/505383)
[![asciicast](https://asciinema.org/a/505383.svg)](https://asciinema.org/a/505383)
#### 2.2.3 文件压缩与解压缩
[CentOS【文件压缩与解压缩】操作：zip与unzip](https://asciinema.org/a/505384)
[![asciicast](https://asciinema.org/a/505384.svg)](https://asciinema.org/a/505384)
[CentOS【文件压缩与解压缩】操作：tar](https://asciinema.org/a/505385)
[![asciicast](https://asciinema.org/a/505385.svg)](https://asciinema.org/a/505385)
[CentOS 【文件压缩与解压缩】操作：gzip](https://asciinema.org/a/505386)
[![asciicast](https://asciinema.org/a/505386.svg)](https://asciinema.org/a/505386)
[CentOS【文件压缩与解压缩】操作：bzip2](https://asciinema.org/a/505387)
[![asciicast](https://asciinema.org/a/505387.svg)](https://asciinema.org/a/505387)
[CentOS【文件压缩与解压缩】操作：7z](https://asciinema.org/a/505389)
[![asciicast](https://asciinema.org/a/505389.svg)](https://asciinema.org/a/505389)
#### 2.2.4 硬件信息获取
[CentOS 【硬件信息获取】操作：CPU信息](https://asciinema.org/a/505390)
[![asciicast](https://asciinema.org/a/505390.svg)](https://asciinema.org/a/505390)
[CentOS 【硬件信息获取】操作：内存大小、硬盘数量与硬盘容量](https://asciinema.org/a/505392)
[![asciicast](https://asciinema.org/a/505392.svg)](https://asciinema.org/a/505392)