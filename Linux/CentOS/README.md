# centos镜像源更换

**阿里云镜像**

```bash
yum install wget
rm /etc/yum.repos.d/CentOS-Base.repo
sudo wget -O /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-7.repo 
yum makecache
```

# yum软件管理包

文章参考：[Centos7-软件包的管理与安装Centos7-软件包的管理与安装](https://blog.csdn.net/liang_operations/article/details/83241551?ops_request_misc=&request_id=&biz_id=102&utm_term=centos7%E5%AE%89%E8%A3%85%E5%8C%85%E7%AE%A1%E7%90%86%E5%99%A8&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-83241551.142^v2^article_score_rank,143^v4^register&spm=1018.2226.3001.4187)

**包管理常用命令**

```bash
yum search xxx			#模糊查询软件包
yum install xxx			#安装软件包
yum remove xxx			#删除软件包
```

# mysql安装

```bash
#下载mysql数据包
wget http://dev.mysql.com/get/mysql57-community-release-el7-10.noarch.rpm
#安装mysql
yum -y install mysql57-community-release-el7-10.noarch.rpm
yum -y install mysql-community-server
#如果报错说公钥尚未安装则用如下命令，跳过公钥检查
yum -y install mysql-community-server --nogpgcheck
#启动mysql服务
systemctl start  mysqld
#查看初始密码
grep 'password' /var/log/mysqld.log
#进入数据库
mysql -h (主机ip，可省略) -u root -p 
#修改root密码，xxxx就是新密码，大小写加符号
ALTER USER USER() IDENTIFIED BY 'XXXX';
#退出
exit
```

**mysql连接c++重要包**

```bash
mysql-libs mysql-devel mysql++
```

mysql++参考文章：[centos 6.4下mysql++的安装](https://blog.csdn.net/weixin_33939380/article/details/92123224?ops_request_misc=&request_id=&biz_id=102&utm_term=centos%20mysql%20%E5%AE%89%E8%A3%85%20mysql++&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-4-92123224.142^v5^pc_search_result_control_group,157^v4^new_style&spm=1018.2226.3001.4187)

## mysql远程连接

进入数据库

```bash
use mysql;
update user set user.Host='%' where user.User='root';
flush privileges;
```

# 防火墙firewall的使用

文章参考：[防火墙开放端口](https://blog.csdn.net/leiwuhen92/article/details/104551218?ops_request_misc=&request_id=&biz_id=102&utm_term=%E9%98%B2%E7%81%AB%E5%A2%99%E5%BC%80%E6%94%BE%E7%AB%AF%E5%8F%A3&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-104551218.142^v2^article_score_rank,143^v4^register&spm=1018.2226.3001.4187)

```bash
#开放端口
firewall-cmd --zone=public --add-port=80/tcp --permanent
#重新启动防火墙
firewall-cmd --reload
#查看端口是否开启
firewall-cmd --zone=public --query-port=80/tcp
#删除端口
firewall-cmd --zone=public --remove-port=80/tcp --permanent
#列出开放端口
firewall-cmd --zone=public --list-ports
```

# 网络配置

文章参考：[CentOS7 网络配置超详细ip、网关设置](https://blog.csdn.net/qq_41474121/article/details/108929640?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522164752876816782184640676%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=164752876816782184640676&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-1-108929640.142^v2^article_score_rank,143^v4^register&utm_term=centos7%E7%BD%91%E7%BB%9C%E9%85%8D%E7%BD%AE&spm=1018.2226.3001.4187)

[Centos 7开启网卡打开DHCP自动获取IP关闭防火墙](https://blog.csdn.net/lukaixiao/article/details/53946243?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522164752922416782248553535%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=164752922416782248553535&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~baidu_landing_v2~default-4-53946243.142^v2^article_score_rank,143^v4^register&utm_term=centos7%E7%BD%91%E7%BB%9C%E9%85%8D%E7%BD%AEdhcp&spm=1018.2226.3001.4187)

其他参考：[「Linux」- 通过 NetworkManager 连接 Wi-Fi 热点](https://blog.k4nz.com/949d40228a77b57d0fc0e7cd0ca4cbf1/)

**编辑配置文件**

```bash
ip address 		#查看你的网络信息，网卡名，mac地址，IP地址
cd /etc/sysconfig/network-scripts
vim xxx			#你的网卡名
```

**dhcp自动获取ip**

重要设置：mac地址，dhcp，onboot

```bash
HWADDR=00:0c:29:58:27:57
TYPE=Ethernet
BOOTPROTO=DHCP
DEFROUTE=yes
PEERDNS=yes
PEERROUTES=yes
IPV4_FAILURE_FATAL=no
IPV6INIT=yes
IPV6_AUTOCONF=yes
IPV6_DEFROUTE=yes
IPV6_PEERDNS=yes
IPV6_PEERROUTES=yes
IPV6_FAILURE_FATAL=no
NAME=eno16777736
UUID=71557f7c-446c-4145-8151-1f52f07b8b12
ONBOOT=yes                  
#开启自动启用网络连接

#这里增加了第一行的mac地址，
#最后一行修改成了yes开启网络连接
```

**设置静态ip**

最重要的四个设置，ip、网关、子网掩码、dns

```bash
代码示例:
TYPE=Ethernet
PROXY_METHOD=none
BROWSER_ONLY=no
BOOTPROTO=static  #启动的时候的 IP 取得的协议，这里是固定的，如果是动态主机的话，要改成 dhcp 才行#
DEFROUTE=yes
IPV4_FAILURE_FATAL=no
IPV6INIT=yes
IPV6_AUTOCONF=yes
IPV6_DEFROUTE=yes
IPV6_FAILURE_FATAL=no
IPV6_ADDR_GEN_MODE=stable-privacy
NAME=ens33     #设定网卡的名称，要跟文件名称对应 #
UUID=f5e37a10-3da9-47af-8dbb-370b7bf24509 
DEVICE=ens33   #设定网卡的名称，要跟文件名称对应 #
ONBOOT=yes    #是否在开机的的时候启动网卡# 
IPADDR=192.168.0.7        #IP 地址#   必设置
GATEWAY=192.168.0.2       #网关地址#  必须设置
NETWORK=192.168.0.3　　    #该网段的第一个 IP# 可以不设置
BROADCAST=192.168.0.255　　#最后一个同网段的广播地址#  可以不设置
NETMASK=255.255.255.0     #子网掩码#   必设置
DNS1=192.168.0.1   必设置   跟ip地址一样，只需要把最后末尾改成1即可
#GATEWAYDEV=eth0 推荐阅读： linux网络配置文件(redhat、ubuntu系统) centos基本网络配置-网卡eth0、DNS、Host等
linux主机刚安装好时，ONBOOT属性的缺省值为no，需要修改为yes，BOORPROTO缺省值为dhcp，需要修改为static。
然后，设置IP地址，网络掩码，网关等。
```

# systemctl控制目录

文章参考：[systemctl配置管理文件详解](https://blog.csdn.net/yonghutwo/article/details/115160748?ops_request_misc=&request_id=&biz_id=102&utm_term=systemctl%20enable%20%E6%96%87%E4%BB%B6%E7%9B%AE%E5%BD%95&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-115160748.nonecase&spm=1018.2226.3001.4187)

**文件存放位置：（共三处）**

```bash
/etc/systemd/system/
/usr/lib/systemd/system
/lib/systemd/system
```

# CentOS实现远程桌面

[CentOS7安装xrdp实现Windows桌面远程](https://blog.csdn.net/stony3/article/details/78599246)