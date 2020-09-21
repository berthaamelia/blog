---
layout: post
title:  "Statistic 101 with python"
date:   2020-09-23 22:46:00 +0200
categories: [python,machinelearning,statsmodels]
---

I have always loved statistic, it was among my most favorite subject when I did my bachelor and master. Even in my most recent master thesis, I applied pure quantitative approach in order to prove the effect of income inequality in entrepreneurial activities in 70 different countries. 
I simply adore how you can generate such pattern of information solely from a bunch of numbers in table form. The more you dig into, the more you discover the hidden layers of information underneath. There is no right or wrong, it is just a question of which method would you like to associate your argument with. Perhaps that is what makes it very much captivating, the fact that you could not manipulate details inside statistic? It is so pure and honest. 

### Tools:
1. Raspberry pi zero W (512 MB RAM). OS: Linux raspberry Pi OS Lite (32-bit)
2. Camera module. I bought this online from Aliexpress.com for about US$ 8.
Though I have to wait for almost a month to arrive, I am super-satisfied with the features this camera offers. It has 5 MP wide angle fish eyes + night vision surveillance lenses 1080p and you can adjust its focus manually by rotating the lens. It also comes with Pi Zero camera adapter cable so you do not need to worry on finding one because it is quite hard to find. This stuff is worth every second moment I opened my post box with hope. 

![Raspberry pi camera module 5MP Wide Angle](https://raw.githubusercontent.com/berthaamelia/blog/master/images/PiZero_camera.png)

Basic program requirements:
- VLC media player
- Raspivid (it is by default installed already in your computer)

This is the complete video tutorial video on how to setup the pi:

<iframe width="560" height="315" src="https://www.youtube.com/embed/JeFs6Mx08Yo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br/>
### Sidenote:
Basically the idea behind this project is to use the raspi as an IP camera and it will stream the video over network by using RTSP (Real Time Streaming Protocol). Then we will use the raspivid in order to configure the stream setting.
By default it is set to output 1080 video at 30 fps with a bit rate of 2 Mbps. However the setting can be adjusted according to your need, you just need to edit the script `rtsp-stream.sh`.
<br/>Probably the only downside with such system is its limitations to work with captured images, in contrary to OpenCV. The VLC stream only allow you to see real-time images, record videos and few other basic video editing.
Honestly for me this application works like a charm. I mean OpenCV is awesome but that suits to completely another level of application. It optimizes a computer to solve vision problems like face recognition or video analysis. Typical case is to get a license plate number of a car that was speeding, or assigning a robot vision to acknowledge human’s handwriting. As for day-to-day budget surveillance system, I believe my raspi Zero does fantastic job! Check out how I installed it in my apartment :house: :wink: