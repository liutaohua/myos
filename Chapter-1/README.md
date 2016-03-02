#第一步：环境搭建
##1.windows or linux
其实如果你不是一个熟悉linux系统的推荐还是首选windows的，因为：
> 学习一个东西还是首先直奔主题,操作系统的差异很可能导致你在学习的过程当中失去了继续下去的学习勇气，用你最了解的方式，去学习你未知的领域在我看来是最好的技术探索之路

但如果你懂一些linux的常用操作，了解一些工具的安装，看的懂一些命令行和能使用个文本编辑器，我还是推荐使用linux的，毕竟学习过程中遇到的很多工具更方便的在linux中找到，更方便的搜索到。
至于究竟是使用什么操作系统，使用什么工具，在我看来仁者见仁，而且我是混合使用。Haaaa，因为linux更直接，而windows更方便查阅资料。

##2.环境搭建步骤

###1)安装虚拟机和linux系统
又到了这个选择的时刻，虚拟机种类繁多，qemu、vmware、vbox、etc...
哪个用好了都能达到你想要的效果，我呢暂时使用vbox，在虚拟机中创建一个linux系统然后开始我的操作系统编写之旅。
[Oracle Vbox下载地址](https://www.virtualbox.org/)
[Centos 下载地址](http://mirrors.163.com/centos/7/isos/x86_64/CentOS-7-x86_64-DVD-1511.iso)
[Xshell 下载地址]()
###2)安装linux下的开发工具
* gcc
``` powershell
    yum groupinstall "Development Tools" 
```
* vim
``` powershell
	yum install vim
```

好了基本的就这样，剩下的在实践的过程中一步步的更新。thx