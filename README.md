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







管理宝塔
停止
/etc/init.d/bt stop
启动
/etc/init.d/bt start
重启
/etc/init.d/bt restart
卸载
/etc/init.d/bt stop && chkconfig --del bt && rm -f /etc/init.d/bt && rm -rf /www/server/panel
查看当前面板端口
cat /www/server/panel/data/port.pl
修改面板端口，如要改成8881（centos 6 系统）
echo '8881' > /www/server/panel/data/port.pl && /etc/init.d/bt restart
iptables -I INPUT -p tcp -m state --state NEW -m tcp --dport 8881 -j ACCEPT
service iptables save
service iptables restart
修改面板端口，如要改成8881（centos 7 系统）
echo '8881' > /www/server/panel/data/port.pl && /etc/init.d/bt restart
firewall-cmd --permanent --zone=public --add-port=8881/tcp
firewall-cmd --reload
强制修改MySQL管理(root)密码，如要改成123456
cd /www/server/panel && python tools.py root 123456
修改面板密码，如要改成123456
cd /www/server/panel && python tools.py panel 123456
查看宝塔日志
cat /tmp/panelBoot.pl
查看软件安装日志
cat /tmp/panelExec.log
站点配置文件位置
/www/server/panel/vhost
删除域名绑定面板
rm -f /www/server/panel/data/domain.conf
清理登陆限制
rm -f /www/server/panel/data/*.login
查看面板授权IP
cat /www/server/panel/data/limitip.conf
关闭访问限制
rm -f /www/server/panel/data/limitip.conf
查看许可域名
cat /www/server/panel/data/domain.conf
关闭面板SSL
rm -f /www/server/panel/data/ssl.pl && /etc/init.d/bt restart
查看面板错误日志
cat /tmp/panelBoot
查看数据库错误日志
cat /www/server/data/*.err
站点配置文件目录(nginx)
/www/server/panel/vhost/nginx
站点配置文件目录(apache)
/www/server/panel/vhost/apache
站点默认目录
/www/wwwroot
数据库备份目录
/www/backup/database
站点备份目录
/www/backup/site
站点日志
/www/wwwlogs
Nginx服务管理
nginx安装目录
/www/server/nginx
启动
/etc/init.d/nginx start
停止
/etc/init.d/nginx stop
重启
/etc/init.d/nginx restart
启载
/etc/init.d/nginx reload
nginx配置文件
/www/server/nginx/conf/nginx.conf
Apache服务管理
apache安装目录
/www/server/httpd
启动
/etc/init.d/httpd start
停止
/etc/init.d/httpd stop
重启
/etc/init.d/httpd restart
启载
/etc/init.d/httpd reload
apache配置文件
/www/server/apache/conf/httpd.conf
MySQL服务管理
mysql安装目录
/www/server/mysql
phpmyadmin安装目录
/www/server/phpmyadmin
数据存储目录
/www/server/data
启动
/etc/init.d/mysqld start
停止
/etc/init.d/mysqld stop
重启
/etc/init.d/mysqld restart
启载
/etc/init.d/mysqld reload
mysql配置文件
/etc/my.cnf
FTP服务管理
ftp安装目录
/www/server/pure-ftpd
启动
/etc/init.d/pure-ftpd start
停止
/etc/init.d/pure-ftpd stop
重启
/etc/init.d/pure-ftpd restart
ftp配置文件
/www/server/pure-ftpd/etc/pure-ftpd.conf
PHP服务管理
php安装目录
/www/server/php
启动(请根据安装PHP版本号做更改，例如：/etc/init.d/php-fpm-54 start)
/etc/init.d/php-fpm-{52|53|54|55|56|70|71|72|73|74} start
停止(请根据安装PHP版本号做更改，例如：/etc/init.d/php-fpm-54 stop)
/etc/init.d/php-fpm-{52|53|54|55|56|70|71|72|73|74} stop
重启(请根据安装PHP版本号做更改，例如：/etc/init.d/php-fpm-54 restart)
/etc/init.d/php-fpm-{52|53|54|55|56|70|71|72|73|74} restart
启载(请根据安装PHP版本号做更改，例如：/etc/init.d/php-fpm-54 reload)
/etc/init.d/php-fpm-{52|53|54|55|56|70|71|72|73|74} reload
配置文件(请根据安装PHP版本号做更改，例如：/www/server/php/52/etc/php.ini)
/www/server/php/{52|53|54|55|56|70|71|72|73|74}/etc/php.ini
Redis服务管理
redis安装目录
/www/server/redis
启动
/etc/init.d/redis start
停止
/etc/init.d/redis stop
redis配置文件
/www/server/redis/redis.conf
Memcached服务管理
memcached安装目录
/usr/local/memcached
启动
/etc/init.d/memcached start
停止
/etc/init.d/memcached stop
重启
/etc/init.d/memcached restart
启载
/etc/init.d/memcached reload


