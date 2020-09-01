---
layout: post
title:  "Face detection program with raspberry pi 4"
date:   2020-07-25 18:30:00 +0200
categories: [python,openCV]
---
I have been experimenting few online tutorials for face detection program and finally i have found the best one that i would like to share with you. Installing OpenCV module in raspberry pi is very labour-intensive (due to limited RAM) and there are too many tutorials out there that you will be confused which one to follow if it is your first time. Hence i would be sharing the link that i used and the equipment needed to launch your very own face detection program!

### Tools:
1. Raspberry pi 4 (4 GB RAM). OS: Linux raspbian buster with desktop.
I purchased it from Kjell og Company shop. I would recommend to use raspberry pi 4 for faster processing, i had used raspi 3b+ before still it took me ~8 hours to install OpenCV and for some reason it was built-in together with python 2.7. So i had to re-do the whole process again because i prefer python 3.7. To avoid the same mistake, I have then switched to raspi 4 which only took me 1 hour in total to install everything.

2. Power cable, screen, HDMI cable, mouse, keyboard, 16 gb SD card
3. Camera module NOIR (No infra red filter for night mode)

Here I am sharing the link on step-by-step to make face detection program using OpenCV. I did not write the guide, so please carefully follow each instruction written there. Make sure you do not skip any dependencies and no typo. The author pretty much explained everything straightforward and in comments section he also explained some issues that may occur while installing.

[Click here for installation guide](https://www.element14.com/community/community/raspberry-pi/blog/2019/02/11/raspberry-pi-face-recognition)

<https://www.element14.com/community/community/raspberry-pi/blog/2019/02/11/raspberry-pi-face-recognition>

It took 1 hour for my raspi 4 to successfully build & install OpenCV. Voila ! If it takes longer duration, check again your free disk space by typing “free -h”, perhaps there is issue with your memory space.

For my next mission, i plan to modify it in order to allow face detection as an input to unlock my DIY-google home assistant. I will post it here in the blog once i am done with the project :)

![Face recognition program](https://raw.githubusercontent.com/berthaamelia/blog/master/images/face_detection.jpg "face recognition program with raspi4")