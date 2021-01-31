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
