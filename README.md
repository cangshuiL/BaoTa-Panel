# 前言

bt文件夹里的文件在宝塔安装过程中会自动下载

bt_code文件夹里的文件是宝塔面板的源码也会在安装过程中自动下载。

bt.init 宝塔面板PyWeb配置文件

install.sh Centos/Fedora安装文件 

install-ubuntu.sh Ubuntu/Deepin/Debian安装文件

宝塔安装需要的程序chardet-2.3.0、MySQL-python-1.2.5、psutil-5.2.2、Pillow-3.2.0、setuptools-33.1.1、web.py-0.38

panel是宝塔的面板源码。update.sh面板更新文件。uninstall.sh面板卸载软件
## 安装要求：
Python版本： 2.6/2.7（安装宝塔时会自动安装）
内存：128M以上，推荐512M以上（纯面板约占系统10M内存）
硬盘：100M以上可用硬盘空间（纯面板约占20M磁盘空间）
系统：CentOS 6.x / 7.x (Ubuntu、Debian、Fedora 请点这里)，确保是干净的操作系统，没有安装过其它环境带的Apache/Nginx/php/MySQL


**Centos/Fedora安装命令：**

```
wget https://github.com/cangshuiL/BaoTa-Panel/archive/master.zip && unzip master.zip && cd BaoTa-Panel-master && sh install.sh
```

**Ubuntu/Deepin/Debian安装命令：**

```
wget https://github.com/cangshuiL/BaoTa-Panel/archive/master.zip && unzip master.zip && cd BaoTa-Panel-master && bash install-ubuntu.sh
```

## 更新命令（仅限3.x以上版本使用！不支持2.X面板！）：

```
sh /www/server/panel/update.sh
```

**若点击更新后没生效，请尝试重启面板服务：**

```
service bt restart
```
