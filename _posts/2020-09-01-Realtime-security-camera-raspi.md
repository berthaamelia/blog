---
layout: post
title:  "Setting up mini real-time security camera at your house"
date:   2020-09-01 21:00:00 +0200
categories: [python,raspberrypi]
---

 In the previous post I have explained about how to turn your raspberry pi Zero into a music player through bluetooth. However not long after that I discovered another application that is perfect to complement my pi :smile:
 <br/>The tutorial explained on how to set up a real-time security camera with raspi and stream it through VLC media player, as simple as that! It is such an excellent idea to try because streaming will not consume memory space in my Pi !
 I followed all the guides from a tutorial video in YouTube which i will post it here and I can confirm the system works so well and it is streaming in high quality to your laptop. The small RAM in raspi Zero does not affect the quality and the speed of IP camera transmission. I believe the speed is somehow relative to how fast your internet is.

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
Honestly for me this application works like a charm. I mean OpenCV is awesome but that is more for another level of application. It optimizes a computer to solve vision problems like face recognition or video analysis. Typical cases is to get a license plate number of a car that was speeding, or assigning a robot vision to acknowledge human´s handwriting. As for day-to-day budget surveillance system, I believe my raspi Zero does fantastic job! Check out how I installed it in my apartment :house: :wink: