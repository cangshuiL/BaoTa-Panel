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

## 
管理宝塔
----

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
---------

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
----------

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
---------

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
-------

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
-------

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
---------

redis安装目录

/www/server/redis

启动

/etc/init.d/redis start

停止

/etc/init.d/redis stop

redis配置文件

/www/server/redis/redis.conf

Memcached服务管理
-------------

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
				<h2 class="th2">安装宝塔</h2>
				<div class="btcode">
					<span>Centos安装脚本</span>
					<pre class="installcode">yum install -y wget &amp;&amp; wget -O install.sh http://download.bt.cn/install/install_6.0.sh &amp;&amp; sh install.sh</pre>
					<span>Ubuntu/Deepin安装脚本</span>
					<pre class="installcode">wget -O install.sh http://download.bt.cn/install/install-ubuntu_6.0.sh &amp;&amp; sudo bash install.sh</pre>
					<span>Debian安装脚本</span>
					<pre class="installcode">wget -O install.sh http://download.bt.cn/install/install-ubuntu_6.0.sh &amp;&amp; bash install.sh</pre>
					<span>Fedora安装脚本</span>
					<pre class="installcode">wget -O install.sh http://download.bt.cn/install/install_6.0.sh &amp;&amp; bash install.sh</pre>
				</div>
				<a name="main"></a>
				<h2 class="th2">管理宝塔</h2>
				<div class="btcode">
					
					
					<span>停止</span>
					<pre>/etc/init.d/bt stop</pre>
					<span>启动</span>
					<pre>/etc/init.d/bt start</pre>
					<span>重启</span>
					<pre>/etc/init.d/bt restart</pre>
					<span>卸载</span>
					<pre>/etc/init.d/bt stop &amp;&amp; chkconfig --del bt &amp;&amp; rm -f /etc/init.d/bt &amp;&amp; rm -rf /www/server/panel</pre>
					<span>查看当前面板端口</span>
					<pre>cat /www/server/panel/data/port.pl</pre>
					<span>修改面板端口，如要改成8881（centos 6 系统）</span>
					<pre>echo '8881' &gt; /www/server/panel/data/port.pl &amp;&amp; /etc/init.d/bt restart
iptables -I INPUT -p tcp -m state --state NEW -m tcp --dport 8881 -j ACCEPT
service iptables save
service iptables restart</pre>
					<span>修改面板端口，如要改成8881（centos 7 系统）</span>
					<pre>echo '8881' &gt; /www/server/panel/data/port.pl &amp;&amp; /etc/init.d/bt restart
firewall-cmd --permanent --zone=public --add-port=8881/tcp
firewall-cmd --reload</pre>
					<span>强制修改MySQL管理(root)密码，如要改成123456</span>
					<pre>cd /www/server/panel &amp;&amp; python tools.py root 123456</pre>
					<span>修改面板密码，如要改成123456</span>
					<pre>cd /www/server/panel &amp;&amp; python tools.py panel 123456</pre>
					<span>查看宝塔日志</span>
					<pre>cat /tmp/panelBoot.pl</pre>
					<span>查看软件安装日志</span>
					<pre>cat /tmp/panelExec.log</pre>
					<span>站点配置文件位置</span>
					<pre>/www/server/panel/vhost</pre>
					<span>删除域名绑定面板</span>
					<pre>rm -f /www/server/panel/data/domain.conf</pre>
					<span>清理登陆限制</span>
					<pre>rm -f /www/server/panel/data/*.login</pre>
					<span>查看面板授权IP</span>
					<pre>cat /www/server/panel/data/limitip.conf</pre>
					<span>关闭访问限制</span>
					<pre>rm -f /www/server/panel/data/limitip.conf</pre>
					<span>查看许可域名</span>
					<pre>cat /www/server/panel/data/domain.conf</pre>
					<span>关闭面板SSL</span>
					<pre>rm -f /www/server/panel/data/ssl.pl &amp;&amp; /etc/init.d/bt restart</pre>
					<span>查看面板错误日志</span>
					<pre>cat /tmp/panelBoot</pre>
					<span>查看数据库错误日志</span>
					<pre>cat /www/server/data/*.err</pre>
					<span>站点配置文件目录(nginx)</span>
					<pre>/www/server/panel/vhost/nginx</pre>
					<span>站点配置文件目录(apache)</span>
					<pre>/www/server/panel/vhost/apache</pre>
					<span>站点默认目录</span>
					<pre>/www/wwwroot</pre>
					<span>数据库备份目录</span>
					<pre>/www/backup/database</pre>
					<span>站点备份目录</span>
					<pre>/www/backup/site</pre>
					<span>站点日志</span>
					<pre>/www/wwwlogs</pre>
				</div>
				<a name="nginx"></a>
				<h2 class="th2">Nginx服务管理</h2>
				<div class="btcode">
					<span>nginx安装目录</span>
					<pre>/www/server/nginx</pre>
					<span>启动</span>
					<pre>/etc/init.d/nginx start</pre>
					<span>停止</span>
					<pre>/etc/init.d/nginx stop</pre>
					<span>重启</span>
					<pre>/etc/init.d/nginx restart</pre>
					<span>启载</span>
					<pre>/etc/init.d/nginx reload</pre>
					<span>nginx配置文件</span>
					<pre>/www/server/nginx/conf/nginx.conf</pre>
				</div>
				<a name="apache"></a>
				<h2 class="th2">Apache服务管理</h2>
				<div class="btcode">
					<span>apache安装目录</span>
					<pre>/www/server/httpd</pre>
					<span>启动</span>
					<pre>/etc/init.d/httpd start</pre>
					<span>停止</span>
					<pre>/etc/init.d/httpd stop</pre>
					<span>重启</span>
					<pre>/etc/init.d/httpd restart</pre>
					<span>启载</span>
					<pre>/etc/init.d/httpd reload</pre>
					<span>apache配置文件</span>
					<pre>/www/server/apache/conf/httpd.conf</pre>
				</div>
				<a name="mysql"></a>
				<h2 class="th2">MySQL服务管理</h2>
				<div class="btcode">
					<span>mysql安装目录</span>
					<pre>/www/server/mysql</pre>
					<span>phpmyadmin安装目录</span>
					<pre>/www/server/phpmyadmin</pre>
					<span>数据存储目录</span>
					<pre>/www/server/data</pre>
					<span>启动</span>
					<pre>/etc/init.d/mysqld start</pre>
					<span>停止</span>
					<pre>/etc/init.d/mysqld stop</pre>
					<span>重启</span>
					<pre>/etc/init.d/mysqld restart</pre>
					<span>启载</span>
					<pre>/etc/init.d/mysqld reload</pre>
					<span>mysql配置文件</span>
					<pre>/etc/my.cnf</pre>
				</div>
				<a name="ftp"></a>
				<h2 class="th2">FTP服务管理</h2>
				<div class="btcode">
					<span>ftp安装目录</span>
					<pre>/www/server/pure-ftpd</pre>
					<span>启动</span>
					<pre>/etc/init.d/pure-ftpd start</pre>
					<span>停止</span>
					<pre>/etc/init.d/pure-ftpd stop</pre>
					<span>重启</span>
					<pre>/etc/init.d/pure-ftpd restart</pre>
					<span>ftp配置文件</span>
					<pre>/www/server/pure-ftpd/etc/pure-ftpd.conf</pre>
				</div>
				<a name="php"></a>
				<h2 class="th2">PHP服务管理</h2>
				<div class="btcode">
					<span>php安装目录</span>
					<pre>/www/server/php</pre>
					<span>启动</span><span class="info">(请根据安装PHP版本号做更改，例如：/etc/init.d/php-fpm-54 start)</span>
					<pre>/etc/init.d/php-fpm-{52|53|54|55|56|70|71|72|73|74} start</pre>
					<span>停止</span><span class="info">(请根据安装PHP版本号做更改，例如：/etc/init.d/php-fpm-54 stop)</span>
					<pre>/etc/init.d/php-fpm-{52|53|54|55|56|70|71|72|73|74} stop</pre>
					<span>重启</span><span class="info">(请根据安装PHP版本号做更改，例如：/etc/init.d/php-fpm-54 restart)</span>
					<pre>/etc/init.d/php-fpm-{52|53|54|55|56|70|71|72|73|74} restart</pre>
					<span>启载</span><span class="info">(请根据安装PHP版本号做更改，例如：/etc/init.d/php-fpm-54 reload)</span>
					<pre>/etc/init.d/php-fpm-{52|53|54|55|56|70|71|72|73|74} reload</pre>
					<span>配置文件</span><span class="info">(请根据安装PHP版本号做更改，例如：/www/server/php/52/etc/php.ini)</span>
					<pre>/www/server/php/{52|53|54|55|56|70|71|72|73|74}/etc/php.ini</pre>
				</div>
				<a name="redis"></a>
				<h2 class="th2">Redis服务管理</h2>
				<div class="btcode">
					<span>redis安装目录</span>
					<pre>/www/server/redis</pre>
					<span>启动</span>
					<pre>/etc/init.d/redis start</pre>
					<span>停止</span>
					<pre>/etc/init.d/redis stop</pre>
					<span>redis配置文件</span>
					<pre>/www/server/redis/redis.conf</pre>
				</div>
				<a name="memcached"></a>
				<h2 class="th2">Memcached服务管理</h2>
				<div class="btcode">
					<span>memcached安装目录</span>
					<pre>/usr/local/memcached</pre>
					<span>启动</span>
					<pre>/etc/init.d/memcached start</pre>
					<span>停止</span>
					<pre>/etc/init.d/memcached stop</pre>
					<span>重启</span>
					<pre>/etc/init.d/memcached restart</pre>
					<span>启载</span>
					<pre>/etc/init.d/memcached reload</pre>
				</div>
			</div>
