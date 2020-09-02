---
layout: post
title:  "Connect bluetooth speaker to raspberry pi zero W with no desktop environment"
date:   2020-08-20 20:00:00 +0200
categories: [python, raspberrypi]
---
My raspberry pi zero has been sitting idle in my cabinet for some time and my hand felt a little itchy to create something out of it. It was my first ever raspi that I owned so I had tons of sentimental value and is reluctant to dispose it. I first thought of installing *KODI*, some sort of mini Netflix but I discovered my pi zero run too slow on it! Same story with *Calibre*. Thought it will be pretty cool to have an e-book server in my pi but again it was running super slow. Gave up and ended up to reimage everything. So my best bet is to just transform the good ol' pi into a media player where i can at least play music on it. 

It may seems easy in the first glance to connect your bluetooth speaker to raspberry pi. True! That is easy when you have proper raspbian desktop environment. However when you deal with raspberry pi zero with no desktop and you have to control everything from terminal, things can get pretty messy and (honestly) frustating. So i dedicate this topic for people who encounter problem connecting their device to raspberry pi zero just like what i had.

Problems experienced when installing:
- I tried to connect my bluetooth speaker and android phone to raspi. Both are successfully paired, but failed to connect. I had error message `org.bluez.error. Failed` <br/>I unpaired, removed and paired it all over again, reboot it, still no success.
- Tried:
<br/>`$ sudo pactl load-module module-bluetooth-discover`
<br/>Output:
<br/>`Failure: Module initialization failed`


### Tools:
1. Raspberry pi zero W (512 MB RAM). OS: Linux raspberry Pi OS Lite (32-bit). This is the latest pi zero that comes with wifi and bluetooth. The size is super cute!
I purchased the starter kit from Kjell og Company shop for 649 kr. It comes in one complete package together with SD card, HDMI, power and USB adapter. 

2. Andersson Bluetooth speaker that i purchased from NetOnNet for 99 kr.

![Raspberry pi zero W starter kit](https://raw.githubusercontent.com/berthaamelia/blog/master/images/raspi_zeroW.png)

After hours of googling, I finally came across one article on how to properly install it. I run it through ssh from my Mac and it worked flawlessly! Credit to the author! I am so excited for you to try this too. Here is the link:

[Click here for installation guide](https://gist.github.com/actuino/9548329d1bba6663a63886067af5e4cb)

*https://gist.github.com/actuino/9548329d1bba6663a63886067af5e4cb*

### Extra:
1. Whenever you want to you connect your device, always start the command with 
<br/>`pulseaudio --start`. Everytime i launched my bluetoothctl without launching the pulseaudio --start, it will refuse to connect with the speaker eventhough it is successfully paired.

2. Now that you have your bluetooth speaker and your android phone connected to raspberry pi. Try open youtube video from your phone, raspi should be able to recognize it and play it through the speaker. You can also run google home assistant from your phone and let the speaker replies! I personaly believe this way is indeed better than installing home assistant over the pi itself due to limited features that Google provides on particular external API assigned for a non-google device.
If you want to run .mp3, i recommend to install mpg321 instead of vlc player. 
<br/>`$ sudo apt-get install mpg321`
<br/>To run the file
<br/>`$ mpg321 -q /home/usr/Coldplay_Yellow.mp3`
<br/>Use -help for more information of the functions.

### Sidenote:
1. Just in case you still failed to launch your speaker after the attempt. Here is what i thought that could be wrong (which i learned from my experience).
You probably are missing the PulseAudio bluetooth module. So install one with this:
<br/>`$ sudo apt install bluetooth pulseaudio-module-bluetooth`
<br/>When it is successful, you should be able to execute:
<br/>`pactl load-module  module-bluetooth-discover`
<br/>Otherwise, try: 
<br/>`pactl unload-module  module-bluetooth-discover`
<br/>`pactl load-module  module-bluetooth-discover`
<br/>It will return numbers like 22 or 24 or 26... Something like that.. It means it is successfully executed.

2. In some articles stack overflow that i read, one solution suggested to edit the file /etc/pulse/default.pa and comment out (with an #) the following line
<br/>`#load-module module-bluetooth-discover`
<br/>This probably worked for others but it did not work for me, i eventually edited it back to the original.
<br/>`sudo nano /etc/pulse/default.pa`
<br/>`load-module module-bluetooth-discover`
<br/>The user also suggested to edit the file /usr/bin/start-pulseaudio-x11, but again it did not work for me and edited it back to original. I simply followed all the guides in the link above that i mentioned without editing any file and it worked 100%!

Here is the original article that i quoted <https://askubuntu.com/questions/689281/pulseaudio-can-not-load-bluetooth-module/1121417#1121417>
