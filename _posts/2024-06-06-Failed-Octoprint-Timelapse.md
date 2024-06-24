---
title: Failed Octoprint Timelapse
date: 2024-06-06
tags:
  - 3D printing
  - timelapse
  - Octoprint
---
I know it's been a few years since I wrote anything for this blog. I'm now writing to make note of what I did to fix the problem so when I face it again, I know what to do.

I've been doing some 3D printing and have installed [Octoprint](https://octoprint.org). What a great little utility. I had a little bit of trouble getting the timelapse to work. It seemed to fail every time with error code `-9`. A little bit of searching online let me to realize the problem was the size of the swap file on the Raspberry Pi. I'm not sure why this isn't bigger[^swap].

The solution is pretty simple, just increase the swap file as shown below.

[^swap]: I don't really understand the swap file on Linux.

https://github.com/OctoPrint/OctoPrint/issues/4447#issuecomment-1604272892
```shell
sudo dphys-swapfile swapoff
sudo nano /etc/dphys-swapfile
# Modify CONF_SWAPSIZE to 512
# (Save file.)
sudo dphys-swapfile setup
sudo dphys-swapfile swapon
```

