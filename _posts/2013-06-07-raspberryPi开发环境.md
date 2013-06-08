---
layout: post
category : 良樵
---
{% include JB/setup %}

在raspberryPi上面开发，先需要了解linux的基本用法，比如更改目录(cd)，下载安装(apt)，解压(tar)，root权限(sudo)等不多的几个命令。

对于配置系统（比如配置网络什么的），可以使用startx进入图形化界面。

raspberryPi自带Python，还可以用QT，ruby。所以理论上，接个显示器，就可以开始开发。我不愿意这么用：
<pre>
	1、需要边写代码边上Google，而以raspberryPi的硬件配置，随便打开个网页都会卡死。
	2、用自己喜欢的编辑器写程序，优秀的IDE也不少。linux上也有很棒编辑器，但在raspberryPi上运行，容易让人崩溃。
</pre>

所以宁愿通过“远程操作”的方法来进行这个过程。

<pre>
	1、部分代码在raspberryPi上调试，比如与GPIO有关的。
       不知有没有GPIO模拟器之类的东西，嘿嘿...
	2、在PC上开发Python程序(用自己喜欢的IDE，一边Google一边Coding)
	3、写好程序后，传到raspberryPi
</pre>

这个过程看起来有点像开发手机程序：）

“远程操作”方法很多，如vnc，putty，我现在用Bitvise SSH Client，它自带ftp，传文件非常方便。
<pre>
	注意：如果您也用远程的方式操作raspberryPi，记得把raspberryPi设置为静态IP。您好总不希望它IP每次都变吧。
</pre>	

![](https://raw.github.com/hackeen/hackeen.github.com/master/img/20130607/raspberryPi.jpg)