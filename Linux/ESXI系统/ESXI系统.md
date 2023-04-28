# 前言
为了将一台电脑分为多个服务器，我尝试安装esxi，尝试过许多教程，下面是对教程的整理。
# ESXI下载
先提供一个下载地址，但你最好看完后再决定用不用下载。
[虚拟机VMware vSphere ESXi 7.0安装配置详细教程(附下载)](https://www.jb51.net/softjc/717737_all.html)
这里下载的esxi没有网卡驱动因此在安装时会显示No Network Adapters的错误，但你如果只是在VMware虚拟机上体验完全够用了。
如果你是在实体虚拟机上安装，请往下看。
# No Network Adapters问题
果然，我在安装时遇到了这个问题，这是我搜到的教程。
[ESXI安装过程记录及No Network Adapters问题解决](https://blog.csdn.net/sinat_15028281/article/details/121757056)
我尝试了一下这个教程，ennnnn，失败了。但是！
在这篇文章里提供了**吴昊博客**的连接，他给了一个封装好的esxi系统，查看他的网卡驱动正好是我需要的，于是我毫不客气的拿来用了。
接下来的就是制作启动盘装系统了，这个略过不提，傻瓜操作。
# 内存过小，无法安装
在安装过程中我又遇到了这个问题，我的内存是3.9G的，但他需要的内存是4G 的，因此我又找到了一篇文章。
[尝试绕过ESXi最小4GB内存的安装检查](https://www.virtualtips.info/?p=83)
# 如果你的存储太小，那么你有可能遇到新的问题
我当时在虚拟机安装时，只给它分了40G的空间，安装好后完全没有存储空间可用，放心不是系统本身所占空间过大。如果你遇到同样的问题，不论是虚拟机还是实体机，可以参考这篇文章。
[VMware ESXi 7.0 自定义「虚拟闪存」容量拯救小磁盘](https://www.vvave.net/archives/change-the-default-size-of-the-esx-osdata-volume-in-esxi-seven.html)