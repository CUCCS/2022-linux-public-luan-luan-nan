 ## 一、Systemd 入门教程：命令篇
 ### 1 系统管理
 #### 1.1 systemctl
 由于此部分命令大多与系统状态有关，执行时`asciinema rec`因退出导致无法记录，故采用截图形式呈现。
 
 `sudo systemctl reboot` 重启系统
 git  bash 连接时重启系统：
 ![git  bash 连接时重启系统](./image/1%20git%20bash%20%E8%BF%9E%E6%8E%A5%E6%97%B6%E9%87%8D%E5%90%AF%E7%B3%BB%E7%BB%9F.png)
 虚拟机内重启系统 显示上次启动时间及当前时间：
 ![虚拟机内重启系统 显示上次启动时间及当前时间](./image/2%20%E8%99%9A%E6%8B%9F%E6%9C%BA%E5%86%85%E9%87%8D%E5%90%AF%E7%B3%BB%E7%BB%9F%20%E6%98%BE%E7%A4%BA%E4%B8%8A%E6%AC%A1%E5%90%AF%E5%8A%A8%E6%97%B6%E9%97%B4%E5%8F%8A%E5%BD%93%E5%89%8D%E6%97%B6%E9%97%B4.png)

 `sudo systemctl poweroff` 关闭系统，切断电源
 关闭系统 切断电源：
![关闭系统 切断电源](./image/3%20%E5%85%B3%E9%97%AD%E7%B3%BB%E7%BB%9F%20%E5%88%87%E6%96%AD%E7%94%B5%E6%BA%90.png)
因已切断电源 故无法直接再次远程连接：
![因已切断电源 故无法直接再次远程连接](./image/4%20%E5%9B%A0%E5%B7%B2%E5%88%87%E6%96%AD%E7%94%B5%E6%BA%90%20%E6%95%85%E6%97%A0%E6%B3%95%E7%9B%B4%E6%8E%A5%E5%86%8D%E6%AC%A1%E8%BF%9C%E7%A8%8B%E8%BF%9E%E6%8E%A5.png)

 `sudo systemctl halt` CPU停止工作
git bash 连接时CPU停止工作后：
 ![git bash 连接时CPU停止工作后](./image/5%20git%20bash%20%E8%BF%9E%E6%8E%A5%E6%97%B6CPU%E5%81%9C%E6%AD%A2%E5%B7%A5%E4%BD%9C%E5%90%8E.png)
CPU停止工作后 虚拟机内显示：
![CPU停止工作后 虚拟机内显示](./image/6%20CPU%E5%81%9C%E6%AD%A2%E5%B7%A5%E4%BD%9C%E5%90%8E%20%E8%99%9A%E6%8B%9F%E6%9C%BA%E5%86%85%E6%98%BE%E7%A4%BA.png)

 `sudo systemctl suspend` 暂停系统
 虚拟机内暂停系统后：
![虚拟机内暂停系统后](./image/7%20%E8%99%9A%E6%8B%9F%E6%9C%BA%E5%86%85%E6%9A%82%E5%81%9C%E7%B3%BB%E7%BB%9F%E5%90%8E.png)

 `sudo systemctl hibernate` 让系统进入冬眠状态
虚拟机页面直接关闭，无法截图

 `sudo systemctl hybrid-sleep` 让系统进入交互式休眠状态
虚拟机页面直接关闭，无法截图

 `sudo systemctl rescue`启动进入救援状态（单用户状态）
 虚拟机内启用救援状态后：
![虚拟机内启用救援状态后](./image/8%20%E8%99%9A%E6%8B%9F%E6%9C%BA%E5%86%85%E5%90%AF%E7%94%A8%E6%95%91%E6%8F%B4%E7%8A%B6%E6%80%81%E5%90%8E.png)
进入到单root用户状态：
![进入到单root用户状态](./image/9%20%E8%BF%9B%E5%85%A5%E5%88%B0%E5%8D%95root%E7%94%A8%E6%88%B7%E7%8A%B6%E6%80%81.png)

#### [1.2 systemd-analyze](https://asciinema.org/a/505427)
[![asciicast](https://asciinema.org/a/505427.svg)](https://asciinema.org/a/505427)

#### [1.3 hostnamectl](https://asciinema.org/a/505429)
[![asciicast](https://asciinema.org/a/505429.svg)](https://asciinema.org/a/505429)

#### [1.4 localectl](https://asciinema.org/a/505431)
[![asciicast](https://asciinema.org/a/505431.svg)](https://asciinema.org/a/505431)

#### [1.5 timedatectl](https://asciinema.org/a/505433)
[![asciicast](https://asciinema.org/a/505433.svg)](https://asciinema.org/a/505433)

#### [1.6 loginctl](https://asciinema.org/a/505435)
[![asciicast](https://asciinema.org/a/505435.svg)](https://asciinema.org/a/505435)

### 2 Unit
#### [2.1 systemctl list-units命令](https://asciinema.org/a/505437)
[![asciicast](https://asciinema.org/a/505437.svg)](https://asciinema.org/a/505437)

#### [2.2 systemctl查看unit状态](https://asciinema.org/a/505439)
[![asciicast](https://asciinema.org/a/505439.svg)](https://asciinema.org/a/505439)

#### 2.3 Unit管理
##### [2.3.1 Unit 管理-安装apache2](https://asciinema.org/a/505512)
[![asciicast](https://asciinema.org/a/505512.svg)](https://asciinema.org/a/505512)

##### [2.3.2 Unit管理](https://asciinema.org/a/505513)
[![asciicast](https://asciinema.org/a/505513.svg)](https://asciinema.org/a/505513)

#### [2.4 依赖关系](https://asciinema.org/a/505514)
[![asciicast](https://asciinema.org/a/505514.svg)](https://asciinema.org/a/505514)

### 3 Unit的配置文件
#### [3.1 配置文件状态](https://asciinema.org/a/505515)
[![asciicast](https://asciinema.org/a/505515.svg)](https://asciinema.org/a/505515)

#### [3.2 配置文件的格式](https://asciinema.org/a/505516)
[![asciicast](https://asciinema.org/a/505516.svg)](https://asciinema.org/a/505516)

#### [3.3 Target](https://asciinema.org/a/505517)
[![asciicast](https://asciinema.org/a/505517.svg)](https://asciinema.org/a/505517)

### 4 日志管理
#### [4.1 日志管理](https://asciinema.org/a/505521)
[![asciicast](https://asciinema.org/a/505521.svg)](https://asciinema.org/a/505521)

## 二、Systemd 入门教程：实战篇
### [1 开机启动](https://asciinema.org/a/505524)
[![asciicast](https://asciinema.org/a/505524.svg)](https://asciinema.org/a/505524)

### [2 启动服务](https://asciinema.org/a/505525)
[![asciicast](https://asciinema.org/a/505525.svg)](https://asciinema.org/a/505525)

### [3 停止服务](https://asciinema.org/a/505526)
[![asciicast](https://asciinema.org/a/505526.svg)](https://asciinema.org/a/505526)

### [4 读懂配置文件](https://asciinema.org/a/505527)
[![asciicast](https://asciinema.org/a/505527.svg)](https://asciinema.org/a/505527)

### [5 install区块](https://asciinema.org/a/505529)
[![asciicast](https://asciinema.org/a/505529.svg)](https://asciinema.org/a/505529)

### [6 Target的配置文件](https://asciinema.org/a/505530)
[![asciicast](https://asciinema.org/a/505530.svg)](https://asciinema.org/a/505530)

### [7 修改配置文件后重启动](https://asciinema.org/a/505531)
[![asciicast](https://asciinema.org/a/505531.svg)](https://asciinema.org/a/505531)