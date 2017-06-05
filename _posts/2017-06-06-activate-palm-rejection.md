---
layout: post
title: Activating Palm Rejection on XPS-13 Ubuntu 16.04 
tags: [setup,xps13,ubuntu]
comments: true
---

After receiving my brand new XPS-13 with Ubuntu 16.04 the first thing I notice is that the palm rejection feature is not present at all. 

I will try to describe as best as I can the methods I have tried and whether or not they are successful.

* *Method 1:* libinput: It didn't work

I tried was was suggested [here](#https://www.reddit.com/r/Dell/comments/4pgek1/dell_xps_13_touch_pad_palm_detection_on_ubuntu/) adn installed:

```
sudo apt-get install xserver-xorg-input-libinput
```

Then I edited the file */usr/share/X11/xor:g.conf.d/90-libinput.conf* so that it contained this:
```
Section "InputClass"
        Identifier "libinput touchpad catchall"
        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/event*"
        Driver "libinput"
        Option "Tapping" "True"
        Option "PalmDetection" "True"
        Option "TappingDragLock" "True"
EndSection
```
