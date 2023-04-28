@[TOC](Ubuntu小知识)
# Ubuntu包管理器
Ubuntu包管理器有：apt, apt-cache, apt-get, dpkg
```
apt-get update						#更新包管理器
apt-cache search <你要查找的name> 	#模糊查询软件
apt-get install <你要安装的软件包>	#安装软件
apt-get source <你要下载的源代码包名>	#下载软件源码
apt-get remove packagename			#卸载软件
dpkg -l								#查看已安装的软件包
```
# Ubuntu防火墙
Ubuntu防火墙是ufw
```
ufw status			#防火墙状态
ufw enable			#开启防火墙
ufw disable			#关闭防火墙
ufw version			#查看防火墙版本
ufw default allow	#默认允许外部主机访问
ufw default deny	#默认拒绝外部主机访问
ufw allow ${port}/tcp	#开启${port}端口
ufw deny ${port}/tcp	#关闭${port}端口
ufw status 				#展示已有防火墙规则
```
# Ubuntu卸载MySQL
文章收录：[【Ubuntu】安装和卸载MySQL8.0](https://blog.csdn.net/fangkang7/article/details/105363273?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522165412895316782184649075%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=165412895316782184649075&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-1-105363273-null-null.142^v11^control,157^v12^new_style2&utm_term=ubuntu%E5%8D%B8%E8%BD%BDmysql8.0&spm=1018.2226.3001.4187)
# Ubuntu安装JDK18
文章收录：[Ubuntu 安装JDK18](https://blog.csdn.net/zynaln/article/details/124369473?ops_request_misc=&request_id=&biz_id=102&utm_term=ubuntu%E5%AE%89%E8%A3%85jdk18&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-124369473.142^v11^control,157^v13^new_style1&spm=1018.2226.3001.4187)
# Ubuntu切换到root

```
sudo passwd root
```
