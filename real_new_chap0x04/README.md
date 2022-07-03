### 1 任务列表
**任务一：用bash编写一个图片批处理脚本，实现以下功能**
- [x]    支持命令行参数方式使用不同功能
- [x]    支持对指定目录下所有支持格式的图片文件进行批处理
- [x]    支持以下常见图片批处理功能的单独使用或组合使用
- [x]    支持对jpeg格式图片进行图片质量压缩
- [ ]    支持对jpeg/png/svg格式图片在保持原始宽高比的前提下压缩分辨率
- [x]    支持对图片批量添加自定义文本水印
- [x]    支持批量重命名（统一添加文件名前缀或后缀，不影响原始文件扩展名）
- [x]    支持将png/svg图片统一转换为jpg格式图片

**任务二：用bash编写一个文本批处理脚本，对以下附件分别进行批量处理完成相应的数据统计任务**
- [x] 统计不同年龄区间范围（20岁以下、[20-30]、30岁以上）的球员数量、百分比
- [x] 统计不同场上位置的球员数量、百分比
- [x] 名字最长的球员是谁？名字最短的球员是谁？
- [x] 年龄最大的球员是谁？年龄最小的球员是谁？

**任务三：用bash编写一个文本批处理脚本，对以下附件分别进行批量处理完成相应的数据统计任务**
- [x] Web服务器访问日志
- [x] 统计访问来源主机TOP 100和分别对应出现的总次数
- [x] 统计访问来源主机TOP 100 IP和分别对应出现的总次数
- [x] 统计最频繁被访问的URL TOP 100
- [x] 统计不同响应状态码的出现次数和对应百分比
- [x] 分别统计不同4XX状态码对应的TOP 10 URL和对应出现的总次数
- [x] 给定URL输出TOP 100访问来源主机

### 2 实验步骤

#### 2.1 任务1
- 安装`imagemagick`
`sudo apt install imagemagick`
- 从宿主机将图片复制至虚拟机工作空间下
![1 从宿主机将图片复制至虚拟机1](./image/1%20%E4%BB%8E%E5%AE%BF%E4%B8%BB%E6%9C%BA%E5%B0%86%E5%9B%BE%E7%89%87%E5%A4%8D%E5%88%B6%E8%87%B3%E8%99%9A%E6%8B%9F%E6%9C%BA1.png)
![2 从宿主机将图片复制至虚拟机2](./image/2%20%E4%BB%8E%E5%AE%BF%E4%B8%BB%E6%9C%BA%E5%B0%86%E5%9B%BE%E7%89%87%E5%A4%8D%E5%88%B6%E8%87%B3%E8%99%9A%E6%8B%9F%E6%9C%BA2.png)
- 写入`task01.sh`脚本文件，逐项执行任务
![3 开始执行任务1脚本](./image/3%20%E5%BC%80%E5%A7%8B%E6%89%A7%E8%A1%8C%E4%BB%BB%E5%8A%A11%E8%84%9A%E6%9C%AC.png)
- 在对svg格式图像实行压缩时出现报错
![4 在对svg格式图像实行压缩时出现报错](./image/4%20%E5%9C%A8%E5%AF%B9svg%E6%A0%BC%E5%BC%8F%E5%9B%BE%E5%83%8F%E5%AE%9E%E8%A1%8C%E5%8E%8B%E7%BC%A9%E6%97%B6%E5%87%BA%E7%8E%B0%E6%8A%A5%E9%94%99.png)
- 查阅资料，显示要修改配置文件`/etc/ImageMagick-6/policy.xml`
- 提权修改policy.xml文件
![5 提权修改policy.xml文件](./image/5%20%E6%8F%90%E6%9D%83%E4%BF%AE%E6%94%B9policy.xml%E6%96%87%E4%BB%B6.png)
- policy.xml修改光标处两行
![6 policy.xml修改光标处两行](./image/6%20policy.xml%E4%BF%AE%E6%94%B9%E5%85%89%E6%A0%87%E5%A4%84%E4%B8%A4%E8%A1%8C.png)
- 修改后仍有报错
![7 修改后仍有报错](./image/7%20%E4%BF%AE%E6%94%B9%E5%90%8E%E4%BB%8D%E6%9C%89%E6%8A%A5%E9%94%99.png)
- 换了一张图片4.svg成功,但发现svg图像只要经过了task01.sh脚本中`function compressResolution`函数的一次压缩后，再次进行其他操作都会有之前的提示错误，猜测是`function compressResolution`函数对于svg的处理可能有问题，但不知道怎样修改
![8 换了一张图片4.svg成功](./image/8%20%E6%8D%A2%E4%BA%86%E4%B8%80%E5%BC%A0%E5%9B%BE%E7%89%874.svg%E6%88%90%E5%8A%9F.png)
- 换了新的5.svg 全部加水印成功
![9 加水印成功](./image/9%20%E5%8A%A0%E6%B0%B4%E5%8D%B0%E6%88%90%E5%8A%9F.png)
其余成功
![10 其余成功](./image/10%20%E5%85%B6%E4%BD%99%E6%88%90%E5%8A%9F.png)
#### 2.2 任务2
- `wget https://c4pr1c3.gitee.io/linuxsysadmin/exp/chap0x04/worldcupplayerinfo.tsv`获取处理数据
- 写入`task02.sh`脚本文件，逐项执行任务
![11 任务2成功](./image/11%20%E4%BB%BB%E5%8A%A12%E6%88%90%E5%8A%9F.png)
#### 2.3 任务3
- `wget https://c4pr1c3.github.io/LinuxSysAdmin/exp/chap0x04/web_log.tsv.7z`获取处理数据
- `7z x web_log.tsv.7z` 解压文件
![12 7z解压](./image/12%207z%E8%A7%A3%E5%8E%8B.png)
- 任务3成功
![13 任务3成功](./image/13%20%E4%BB%BB%E5%8A%A13%E6%88%90%E5%8A%9F.png)
#### 2.4 所有内容传回本地仓库
![14 所有内容传回本地仓库](./image/14%20%E6%89%80%E6%9C%89%E5%86%85%E5%AE%B9%E4%BC%A0%E5%9B%9E%E6%9C%AC%E5%9C%B0%E4%BB%93%E5%BA%93.png)
### 3 参考资料
- [任务压缩出问题时查阅资料](https://blog.csdn.net/lpwmm/article/details/83313459)
- [参考仓库](https://github.com/CUCCS/linux-2020-LyuLumos/blob/ch0x04/ch0x04/%E7%AC%AC%E5%9B%9B%E6%AC%A1%E5%AE%9E%E9%AA%8C%E6%8A%A5%E5%91%8A.md)


