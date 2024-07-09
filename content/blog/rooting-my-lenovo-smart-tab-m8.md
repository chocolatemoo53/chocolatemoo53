+++
title = "Rooting my Lenovo Smart Tab M8"
date = "2024-07-08"
description = "A tutorial and my general experience when rooting my Lenovo Smart Tab M8."
tags = [
    "android",
    "experiments",
]
+++

For my first post, I simply wanted to share an interesting thing I did. Today, I rooted my Android tablet and it wasn't the first time. This Lenovo tablet is quite simple. The processer can be slow and not much works on it beyond watching things. It's pretty good for watching things but it's certainly not the best screen I've ever seen. What some may find interesting is the Dolby Atmos equalizer which is simply an application which changes some EQ, as least that's what it sounds like, to match what you're currently using your tablet for. Like, changing it to dynamic or music mode. I assume it's doing something but maybe it's just a simple way to attract more people to buy it because the assume the speakers will be quality. They're fine in reality. It comes with a stand which charges via micro USB. The few times I do remember using it, it was for simple stuff like playing a game through Parsec or watching a movie. 

It still has a micro SD slot, runs Android 10 and never recieved any other updates beyond last year. The most interesting thing it can do is easily be rooted. I did this exact process a while back but after experimenting with _something_ I ended up bootlooping it and fixing it through the Lenovo Rescue application on Windows, which is actually what can help you get into rooting the device to begin with. 

I remember that I was following the process via a Reddit post but that must be gone now because not much talk is happening on Reddit about this tablet and I can't find the original post, nor did I save it. I'm sure by now many people have returned this thing or recieved a newer tablet but I still kept using it, not to mention that on XDA, it appears people were still using some variant of this device in 2023 so it wouldn't be stretch to say someone other than me is currently still using it. 

Before you begin this process, in case you're following along, back up anything you want to save. The device will become erased once rooted.

It's pretty easy to root it. You simply follow the same steps as you would if you used Magisk on any device, although I have only used it on this device so I'm not sure about that. What I'm talking about really is the steps provided on the [Magisk website](https://topjohnwu.github.io/Magisk/install.html). 

To download the firmware for this tablet and I presume for any other, you can use the [Rescue and Smart Assistant application](https://en-us.support.motorola.com/app/answers/detail/a_id/158726/~/download-rescue-%26-smart-assistant-%28pc-only%29) for Windows only. Then, plug your device in after signing in and setting up the application and install the companion applicaton on the device, go over to the recovery tab and download the .zip firmware that is listed. Hit the Windows Key and R to open the run dialog then go to C:\ProgramData\RSA folder and extract the files from the relevant folders. 

Afterward, you really only need the boot.img and vbmeta.img, although you can keep the entire downloaded archive in case of any problems. Download both files and download [Magisk](https://github.com/topjohnwu/Magisk/releases/latest/) on the device itself. Send your boot file to the tablet through any means, even through ADB, and use Magisk to patch the file by selecting install on the Magisk section then selecting your file. Afterwards, on the device should be a Magisk file that's been patched. Transfer this to your computer. Finally, on your Mac, install adb/android-platform-tools with homebrew or download Platform Tools as a zip and use the individual executables on Windows. 

Now it's time to use Fastboot. Type in the command `adb reboot bootloader` and then `flashboot flashing unlock` which will prompt you on the tablet to push volume up. Afterward, you can use `flashboot flash boot your_file.img` which may simply transfer and flash and proceed to hang. There's nothing to worry about, hard restart and then you can use the vbmeta.img file from the firmware zip and do the exact process for that file except with this command `fastboot flash vbmeta --disable-verity --disable-verification vbmeta.img` which will finally allow the device to be rooted. Once you boot again and set the tablet back up, you'll see Magisk. In my case for some reason, I had to reinstall the app. Normally, I would assume it didn't work but it did just fine. Using `adb shell` and then typing `su` brought up a prompt for root access like as if it was a native app on Android. 

That's it. The device is rooted which can be very useful or not useful at all for you. Whatever you may use root access for, it will probably help you use stuff like [this project](https://github.com/Deeepkk/ubtouch_akita) which is a port of Ubuntu touch. It seems that, even if you use a S variant like me, very little was changed between the versions. The biggest differences being a screen upgrade. So any work done for one variant might work for all variants of this device.
 
---


