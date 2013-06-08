---
layout: post
category : 良樵
---
{% include JB/setup %}

开发环境准备好了，要做我们想要的东西：控制电路。一查，需要GPIO，这就讲讲，咋用raspberryPi控制LED。

控制LED，算得上是开源硬件里的"Hello World"。我做的第一个Arduino也是LED，哈哈。

先查技术参数，确保raspberryPi能驱动LED。
<pre>
	1、raspberryPi官网上，可以查到，raspberryPi最大输出50ma电流，每个引脚最大15ma
	2、GPIO上说得清楚，提供3.3V输出电压
</pre>	
而led，包装上写得清楚：5V   <20mA。对比raspberryPi,不够？非也，led标注的最大值。3.3v，10mA足以点亮led。

算算电阻
<pre>
3.3v/10mA = 330欧。额，偶莫有330的电阻，220差不多，输出电流15mA，小于20mA就烧不了。
初中学的欧姆定律又用上啦。
</pre>

我们需要元件
<pre>
	一个raspberryPi
	一个led
	一个面包板
    一个220欧的电阻
    两根公头对母头线
</pre>

接下来，我们要接线了。***注意，不要热拔插。***

先看GPIO图，具体可以Google一下。

方向这样罢：
![](https://raw.github.com/hackeen/hackeen.github.com/master/img/20130607/RASPBERRYPIGPIO.JPG)
上图右上角的针脚，就是GPIO接口。序号示意图如下：
![](https://raw.github.com/hackeen/hackeen.github.com/master/img/20130607/GPIO.png)

***注意，写程序时，引角序号按圆圈内标注的为准。***

线路简单，直接照片：
![](https://raw.github.com/hackeen/hackeen.github.com/master/img/20130607/LINK.JPG)
照片不太清楚，文字说明一下：
<pre>
   参照序号示意图
   红线，从Pi的11号GPIO口，通过220欧电阻，连接到LED长脚（正级），注：GPIO口绿色的都可以接。
   咖啡色线，接地（Pi上的接地：ground）连接到LED的短脚(负)
</pre>	

接线完毕。接下来，开机，安装python的GPIO模块。
<pre>
sudo apt-get install python-setuptools
sudo easy_install -U distributesudo 
apt-get install python-dev
sudo easy_install RPi.GPIO
</pre>

Python程序：test.py
<pre>
import RPi.GPIO as GPIO
from time import sleep
GPIO.setmode(GPIO.BOARD)
GPIO.setwarnings(False)
GPIO.setup(11,GPIO.OUT)
while True:	
	GPIO.output(11,GPIO.HIGH)
	sleep(1)
	GPIO.output(11,GPIO.LOW)
	sleep(1)
</pre>	

下一步，执行:sudo python test.py

可以看到LED灯一闪一闪的。

注意：
<pre>
	操作GPIO，需要root
	sleep的参数，不是秒。
</pre>	
