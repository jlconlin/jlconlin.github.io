---
title: VNC Authentication with Raspberry Pi
date: 2021-03-02 06:14
tags: 
  - VNC
  - Authentication
---
I like to use the Screen Sharing app on my Mac to connect to my Raspberry Pi so I don't have to connect a keyboard/mouse/monitor. After it is setup, you can do this. A little more configuration needs to be done in order to make this work seamlessly with Screen Sharing.

1. Click the VNC button in the menu bar and selct "Options..."
2. Select "Security" on the left side
   - Set Encryption to "Prefer Off"
   - Set Authentication to "VNC password"

   This should prompt to create a password. If not proceed to step 3.
3. Select "Users & Permissions"
   - Select "Standard user (user)" and create a password.


Now you can go to your Mac, open Screen Sharing, set the appropriate address and connect to your machine. Alternatively you can use the Finder and select Go > Network and type `vnc://ip.add.re.ss` and it will open Screen Sharing for you.

I discovered this from [StackExchange](https://raspberrypi.stackexchange.com/a/70981/107023), of course.
