## 1 调查并记录实验环境的信息
### 1.1 当前Linux发行版基本信息
使用 `lsb_release -a` 查看
![当前发行版信息](./picture/%E5%8F%91%E8%A1%8C%E7%89%88.png)
### 1.2 当前Linux内核版本信息
使用 `uname -a` 查看
![当前内核版本信息](./picture/%E5%86%85%E6%A0%B8%E7%89%88.png)

## 2 使用scp传输文件
### 2.1 虚拟机和宿主机之间
#### 2.1.1 宿主机——>虚拟机
在宿主机gitBash使用 `scp` 传输文件"blender.crash.txt"至虚拟机

最开始用了windows上的目录方式，即目录采用反斜线分割，显示找不到文件，改为linux风格目录，正斜线分割，传输成功

![宿主机至虚拟机](./picture/%E5%AE%BF%E4%B8%BB%E8%87%B3%E8%99%9A%E6%8B%9F.png)
虚拟机查看目录，存在文件"blender.crash.txt"，确认传输成功
![虚拟机确认存在文件](./picture/%E8%99%9A%E6%8B%9F%E6%9C%BA%E4%B8%AD%E7%9C%8B%E5%88%B0%E6%96%87%E4%BB%B6.png)

#### 2.1.2 虚拟机——>宿主机
虚拟机中 `mkdir test` 创建文件夹"test"
![虚拟机创建文件夹](./picture/%E8%99%9A%E6%8B%9F%E6%9C%BA%E5%88%9B%E5%BB%BA%E6%96%87%E4%BB%B6%E5%A4%B9.png)
宿主机gitbash下载虚拟机 `/home/cuc` 中所有文件至 `C:\Users\李楠的世界呀\Desktop` 目录
![下载虚拟机文件](./picture/%E5%AE%BF%E4%B8%BB%E6%9C%BA%E4%B8%8B%E8%BD%BD%E6%96%87%E4%BB%B61.png)
此步操作虽然可以将文件下载到了桌面，但【文件名非常奇怪】，而且多了很多在我的虚拟机`/home/cuc`目录下看不到的文件，能看到的文件只有"test"和我之前上传的"blender.crash.txt"
![宿主机下载后奇怪的文件名](./picture/%E5%A5%87%E6%80%AA%E7%9A%84%E6%96%87%E4%BB%B6%E5%90%8D.png)
突然意识到，是不是又是因为在win上gitbash的目录风格需要和linux是一样的，于是同样的命令，我把反斜线改成了正斜线，成功传送，并且文件名正常
![修改目录斜线](./picture/%E4%BF%AE%E6%94%B9%E6%96%9C%E7%BA%BF%E6%96%B9%E5%90%91.png)
![传输成功且文件名正常](./picture/%E6%96%87%E4%BB%B6%E5%90%8D%E6%AD%A3%E5%B8%B8.png)
### 2.2 本机和阿里云远程linux系统之间
#### 2.2.1 阿里云——>本机
阿里云`mkdir test`创建测试文件夹"test"
![阿里云创建文件夹](./picture/%E9%98%BF%E9%87%8C%E4%BA%91%E5%88%9B%E5%BB%BA%E6%B5%8B%E8%AF%95%E6%96%87%E4%BB%B6%E5%A4%B9.png)
拉取阿里云`/root`目录下文件至本地桌面，成功，其中包含刚刚创建的测试文件夹"test"
![拉取阿里云文件](./picture/%E6%8B%89%E5%8F%96%E9%98%BF%E9%87%8C%E4%BA%91%E6%96%87%E4%BB%B6%E8%87%B3%E6%9C%AC%E5%9C%B0.png)
本地目录查看到阿里云文件
![本地接受到阿里云文件](./picture/%E6%9C%AC%E5%9C%B0%E6%88%90%E5%8A%9F%E6%8E%A5%E5%8F%97%E9%98%BF%E9%87%8C%E4%BA%91%E6%96%87%E4%BB%B6.png)
#### 2.2.1 本机——>阿里云
本地采用scp传输文件"test01.txt"至阿里云成功
![本机上传文件](./picture/%E6%9C%AC%E5%9C%B0%E4%BC%A0%E6%96%87%E4%BB%B6%E8%87%B3%E9%98%BF%E9%87%8C%E4%BA%91.png)
采用`ls`查看当前目录所含文件，阿里云成功接受文件"test01.txt"
![阿里云接受文件](./picture/%E9%98%BF%E9%87%8C%E4%BA%91%E6%88%90%E5%8A%9F%E6%8E%A5%E5%8F%97%E6%96%87%E4%BB%B6.png)

## 3 配置SSH免密登录
宿主机使用`ssh-keygen`创建密钥，显示已经创建成功，应该是我以前写作业的时候尝试创建了密钥，于是不重新创建，直接将公钥文件内容拷贝至虚拟机上，配置免密登录成功
![拷贝公钥](./picture/%E5%B0%86%E5%85%AC%E9%92%A5%E6%8B%B7%E8%B4%9D%E8%87%B3%E9%98%BF%E9%87%8C%E4%BA%91.png)
成功免密登录
![免密登录](./picture/%E6%88%90%E5%8A%9F%E5%AE%9E%E7%8E%B0%E5%85%8D%E5%AF%86%E7%99%BB%E5%BD%95.png)

## 参考文献
[配置SSH免密登录方式](https://blog.csdn.net/weixin_44966641/article/details/123955997)





