# 实验五 Web服务器
## 实验环境
- 服务器 Ubuntu20.04
- 客户端 Window10
- Nginx
- VeryNginx
- DVWA
- Wordpress4.7

## 实验过程
### 环境搭建
**1.客户端hosts修改**
- `windows`主机`C:\Windows\System32\drivers\etc`目录下找到`hosts`文件，添加如下信息配置本地域名解析
    ```bash
    192.168.56.101  vn.sec.cuc.edu.cn
    192.168.56.101  dvwa.sec.cuc.edu.cn
    192.168.56.101  wp.sec.cuc.edu.cn
    ```
- `windows`客户端可以正确解析

    ![1 客户端可以正确解析域名](./image/1%20%E5%AE%A2%E6%88%B7%E7%AB%AF%E5%8F%AF%E4%BB%A5%E6%AD%A3%E7%A1%AE%E8%A7%A3%E6%9E%90%E5%9F%9F%E5%90%8D.png)

**2.Nginx安装**
- 安装并修改配置
    ```bash
    #安装nginx包
    sudo apt install nginx

    #修改配置文件内容
    sudo vim /etc/nginx/sites-enabled/default
    ```
- 配置内容修改后如下图所示

    ![2 nginx文件配置内容](./image/2%20nginx%E6%96%87%E4%BB%B6%E9%85%8D%E7%BD%AE%E5%86%85%E5%AE%B9.png)

    ```bash
    #为防止verynginx安装时报错，先停止nginx服务
    sudo nginx -s stop
    ```

**3.VeryNginx安装**
- 克隆VeryNginx仓库至虚拟机
  ```bash
  git clone https://github.com/alexazhou/VeryNginx.git
  ```
- 按照VeryNginx官方文档提示安装
    ```bash
    #先安装依赖可以避免报错
    sudo apt-get install zlib1g-dev
    sudo apt-get update
    sudo apt-get install libpcre3 libpcre3-dev
    sudo apt install gcc
    sudo apt install make
    sudo apt install libssl-dev
    sudo python3 install.py install
    ```
- 修改配置文件
    ```bash
    sudo vim /opt/verynginx/openresty/nginx/conf/nginx.conf
    ```
- 修改内容为
    ```bash
    # 用户名
    user  www-data;
    # 监听端口设置为8080
    server {
            listen 192.168.56.101:8080;
            
            #this line shoud be include in every server block
            include /opt/verynginx/verynginx/nginx_conf/in_server_block.conf;

            location = / {
                root   html;
                index  index.html index.htm;
            }
        }
    ```
- 添加进程权限
  ```bash
  sudo chmod -R 777 /opt/verynginx/verynginx/configs
  ```
- 访问8080端口时[遇到了和这个同学一样的问题](遇到了和这个同学一样的问题)，按照老师的解答,确认启动的是`verynginx`下的`nginx`后访问成功
  
    ![3 确认启动为verynginx下nginx](./image/3%20%E7%A1%AE%E8%AE%A4%E5%90%AF%E5%8A%A8%E4%B8%BAverynginx%E4%B8%8Bnginx.png)

    ![4 openresty访问成功](./image/4%20openresty%E8%AE%BF%E9%97%AE%E6%88%90%E5%8A%9F.png)
- 进入`/verynginx/index.html`界面，输入用户名和密码,成功进入verynginx界面
  
    ![5 成功进入verynginx界面](./image/5%20%E6%88%90%E5%8A%9F%E8%BF%9B%E5%85%A5verynginx%E7%95%8C%E9%9D%A2.png)

**4.Wordpress安装**
- 下载并解压`wordpress-4.7.zip`
  ```bash
    sudo wget https://wordpress.org/wordpress-4.7.zip
    7z x wordpress-4.7.zip
  ```
- 创建目录并将wordpress文件夹拷贝过去
  ```bash
  sudo mkdir /var/www/html/wp.sec.cuc.edu.cn
  sudo cp -r wordpress /var/www/html/wp.sec.cuc.edu.cn
    ```
- 安装php
    ```bash
    sudo apt install php-fpm php-mysql php-curl php-gd php-intl php-mbstring php-soap php-xml php-xmlrpc php-zip
    ```
- 下载安装mysql数据库，新建数据库`wordpress`数据库及用户`Anan`
    ```bash
    sudo apt install mysql-server# 登录
    sudo mysql
    CREATE DATABASE wordpress DEFAULT CHARACTER SET utf8 COLLATE utf8_unicode_ci;
    create user 'anan'@'localhost' identified by 'anan911';
    ```
    ![6 新建数据库wordpress及用户anan](./image/6%20%E6%96%B0%E5%BB%BA%E6%95%B0%E6%8D%AE%E5%BA%93wordpress%E5%8F%8A%E7%94%A8%E6%88%B7anan.png)
- `var/www/html/wp.sec.cuc.edu.cn/wordpress`目录下将`wp-config-sample.php`文件名修改为`wp-config.php`并配置文件
    ```bash
    sudo mv wp-config-sample.php wp-config.php
    sudo vim wp-config.php
    ```
- 修改配置文件如下
    ```bash
    // ** MySQL settings - You can get this info from your web host ** //
    /** The name of the database for WordPress */
    define('DB_NAME', 'wordpress');

    /** MySQL database username */
    define('DB_USER', 'anan');

    /** MySQL database password */
    define('DB_PASSWORD', 'anan911');

    /** MySQL hostname */
    define('DB_HOST', 'localhost');

    /** Database Charset to use in creating database tables. */
    define('DB_CHARSET', 'utf8');

    /** The Database Collate type. Don't change this if in doubt. */
    define('DB_COLLATE', '');
    ```
- 配置文件wp
    ```bash
    sudo cp /etc/nginx/sites-available/default /etc/nginx/sites-available/wp
    #编辑配置文件
    sudo vim /etc/nginx/sites-available/wp
    # 修改server_name
    server_name wp.sec.cuc.edu.cn;
    # 添加index.php
    index index.php index.html index.htm index.nginx-debian.html;
    ```
- 检查nginx是否生效
    ```bash
    sudo nginx -t
    ```
- 重启php
  ```bash
  sudo systemctl restart php7.4-fpm
  ``` 
- 实验到此处还是无法访问，通过`sudo systemctl status nginx`发现`nginx`实际处于`inactive`状态
    ```bash
    #启动nginx
    sudo systemctl start nginx
    ``` 
- 访问`wp.sec.cuc.edu.cn/wordpress/wp-admin/install.php`成功，进入wordpress界面
  
    ![8 访问wordpress成功](./image/8%20%E8%AE%BF%E9%97%AEwordpress%E6%88%90%E5%8A%9F.png)
- 此处悄悄放一个我的小声呐喊
  
    ![9 小声呐喊](./image/9%20%E5%B0%8F%E5%A3%B0%E5%91%90%E5%96%8A.png)

**5.DVWA安装**
- 将`DVWA`源码下载到当前`/home/CUC`目录
  ```bash
  sudo git clone https://github.com/ethicalhack3r/DVWA
  ```
- 创建目录，并将DVWA文件夹下的文件拷贝至该目录
  ```bash
  sudo mkdir /var/www/html/dvwa.sec.cuc.edu.cn
  sudo cp -r DVWA/. /var/www/html/dvwa.sec.cuc.edu.cn
  ```
- 配置php
  ```bash
    cd /var/www/html/dvwa.sec.cuc.edu.cn/config/
    sudo cp config.inc.php.dist config.inc.php
    sudo vim /var/www/html/DVWA/config/config.inc.php
  ```
- 修改配置如下图光标所示
  
    ![10 配置php](./image/10%20%E9%85%8D%E7%BD%AEphp.png)
- 重启php
  ```bash
  sudo systemctl restart php7.4-fpm
  ```
- 将所有权分配给www-data用户和组
  ```bash
  sudo chown -R www-data.www-data /var/www/html/dvwa.sec.cuc.edu.cn
  ```
- 进入文件配置
  ```bash
  sudo vim /etc/nginx/sites-available/dvwa.sec.cuc.edu.cn
  ```
- 创建软连接
  ```bash
  sudo ln -s /etc/nginx/sites-available/dvwa.sec.cuc.edu.cn /etc/nginx/sites-enabled/
  ```
- 重启nginx
    ```bash
    sudo systemctl restart nginx.service
    ```
- 访问`dvwa.sec.cuc.edu.cn`成功
    ![11 登录DVWA成功](./image/11%20%E7%99%BB%E5%BD%95DVWA%E6%88%90%E5%8A%9F.png)

### 实验检查点
**1.基本要求**
- 配置`Matcher`和`Proxy Pass` 
    ![12 基本要求matcher](./image/12%20%E5%9F%BA%E6%9C%AC%E8%A6%81%E6%B1%82matcher.png)

    ![13 基本要求proxy pass](./image/13%20%E5%9F%BA%E6%9C%AC%E8%A6%81%E6%B1%82proxy%20pass.png)

**2.安全加固要求**

- 使⽤IP地址方式均无法访问上述任意站点，并向访客展示⾃定义的友好错误提示信息页面 `Permssion denied!Have a good day:)`
    - 添加 `matcher`
    ![14 ip无法访问matcher](./image/14%20ip%E6%97%A0%E6%B3%95%E8%AE%BF%E9%97%AEmatcher.png)
    - 添加 `response`
    ![15 ip无法访问reponse](./image/15%20ip%E6%97%A0%E6%B3%95%E8%AE%BF%E9%97%AEreponse.png)
    - 添加 `filter`
    ![16 ip无法访问filter](./image/16%20ip%E6%97%A0%E6%B3%95%E8%AE%BF%E9%97%AEfilter.png)
    - `ip` 无法访问，返回友好错误提示
    ![17 ip无法访问结果](./image/17%20ip%E6%97%A0%E6%B3%95%E8%AE%BF%E9%97%AE%E7%BB%93%E6%9E%9C.png)
    - `url` 可以访问结果
    ![18 url可以访问结果](./image/18%20url%E5%8F%AF%E4%BB%A5%E8%AE%BF%E9%97%AE%E7%BB%93%E6%9E%9C.png)
- `Damn Vulnerable Web Application (DVWA)` 只允许白名单上的访客来源IP，其他来源的IP访问均向访客展示自定义的友好错误提示信息页面
    - 添加 `matcher`
    ![19 dvwa白名单matcher](./image/19%20dvwa%E7%99%BD%E5%90%8D%E5%8D%95matcher.png)
    - 添加 `response`
    ![20 dvwa_response](./image/20%20dvwa_response.png)
    - 添加 `filter`
    ![21 dvwa_white_list_filter](./image/21%20dvwa_white_list_filter.png)
    - 设置成功，主机访问被拒，返回友好错误提示
    ![21-2 设置成功，主机访问被拒](./image/21-2%20%E8%AE%BE%E7%BD%AE%E6%88%90%E5%8A%9F%EF%BC%8C%E4%B8%BB%E6%9C%BA%E8%AE%BF%E9%97%AE%E8%A2%AB%E6%8B%92.png)
    
- 在不升级 `Wordpress` 版本的情况下，通过定制 `VeryNginx` 的访问控制策略规则，热修复[WordPress < 4.7.1 - Username Enumeration](https://www.exploit-db.com/exploits/41497/)
    - 添加 `matcher`
    ![22 热修复matcher](./image/22%20%E7%83%AD%E4%BF%AE%E5%A4%8Dmatcher.png)
    - 添加 `filter`
    ![23 热修复filter](./image/23%20%E7%83%AD%E4%BF%AE%E5%A4%8Dfilter.png)

**3.VeryNginx配置要求**
- `VeryNginx` 的 `Web` 管理页面仅允许⽩名单上的访客来源IP，其他来源的IP访问均向访客展示自定义的友好错误提示信息页面
    - 添加 `matcher`
    ![24 ip_white_list_matcher](./image/24%20ip_white_list_matcher.png)
    - 添加 `response`
    ![25 ip_white_list_response](./image/25%20ip_white_list_response.png)
    - 添加 `filter`
    ![26 ip_white_list_filter](./image/26%20ip_white_list_filter.png)
- 通过定制 `VeryNginx` 的访问控制策略规则实现：限制 `DVWA` 站点的单 `IP` 访问速率为每秒请求数 < 50;限制Wordpress站点的单IP访问速率为每秒请求数 < 20
    - 添加`matcher`
    ![27 request_limit](./image/27%20request_limit.png)
    - 添加 `Frequency Limit`
    ![28 frequency limit](./image/28%20frequency%20limit.png)
    - 添加 `matcher`
    ![29 curl_matcher](./image/29%20curl_matcher.png)
- 禁止curl访问
    - 添加 `response`
    ![30 curl_response](./image/30%20curl_response.png)
    - 添加 `filter`
    ![31 curl_filter](./image/31%20curl_filter.png)

## 参考资料
- [How To Install WordPress with LEMP on Ubuntu 18.04](https://www.digitalocean.com/community/tutorials/how-to-install-wordpress-with-lemp-on-ubuntu-18-04)
- [VeryNginx 文档](https://github.com/alexazhou/VeryNginx/blob/master/readme_zh.md)
- [Trouble Shooting](https://github.com/alexazhou/VeryNginx/wiki/Trouble-Shooting)
- [Systemd 命令](https://www.ruanyifeng.com/blog/2016/03/systemd-tutorial-commands.html)