---
title: Working with OLED Displays
date: 2021-03-25 05:57
tags: 
  - OLED
  - Display
  - Adafruit
  - Python
---
I've been working with a Raspberry Pi Zero. I want to set it up to automatically take pictures and will (eventually) set it up where it won't be connected to a keyboard/mouse/monitor. I will still need to know the IP address so I can use VNC to connect to from a different computer. 

So I attached a small 128x64 OLED display [^wiring] and wrote a small Python script to write the IP address to the screen. Okay, I didn't write the script, I learned how to do this from those great folks at [Adafruit](https://learn.adafruit.com/adafruit-pioled-128x32-mini-oled-for-raspberry-pi/usage) who have a nice little [OLED display](https://www.adafruit.com/product/3527) designed to work with the Raspberry Pi Zero. (I ended up buying two of them!)

I had to make some very slight modifications to the original script to work with my OLED display, which you can see here
{% gist 273b1c0559ed3e66f5fe6086cebac882 startup.py %}

## Running automatically at boot
Those nice folks at Adafruit also showed how to automatically run this script at boot. Simply add: 
```
sudo python3 /home/pi/bin/startup.py &
```
to `/etc/rc.local` before the line that says `exit 0`. 

## Turning off display
You don't always want the display on. I'll be running on battery power and the display will consume power and reduce the amount of time I can run my camera. Well, it's pretty simple to turn the display off. 

{% gist 273b1c0559ed3e66f5fe6086cebac882 poweroffDisplay.py %}

When you want to turn off the OLED display, just execute that script
```bash
$ python3 ~/bin/poweroffDisplay.py
```

[^wiring]: Simple wiring diagram can be found here: <https://circuitdigest.com/microcontroller-projects/ssd1306-oled-display-with-raspberry-pi>. Warning: your display board may not have the terminal pins in the same order as what is used on that site.
