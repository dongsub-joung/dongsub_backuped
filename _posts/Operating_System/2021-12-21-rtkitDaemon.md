---
title: rtkit-daemon
tag: SE
---  

![](https://upload.wikimedia.org/wikipedia/commons/6/6d/Processes_with_D-Bus.svg)

# Zip  
- *RealtimeKit* 

## D-Bus system Overview
- Session Bus && System Bus
- *Inter process communucation //IPC*  
  > SW bus abstraction that gathers all the communications beween a group of processes over a single shared virtual channel.
- *multiple buses*  
- a framework to integrate different components of a user application.  


### etc  
- tool: dbus-monitor  

## Some logs

> tail /var/log/Xorg*log.old  

```
[   788.414] (II) AMDGPU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   788.414] (II) AMDGPU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[   788.414] (II) AMDGPU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   788.414] (II) AMDGPU(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz e)
[   788.414] (II) AMDGPU(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[   788.414] (II) AMDGPU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   788.414] (II) AMDGPU(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[   788.414] (II) AMDGPU(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[   789.178] (II) AMDGPU(0): Allocate new frame buffer 3600x1080
[   789.179] (II) AMDGPU(0):  => pitch 15360 bytes

```

# Ref  
- https://bbs.archlinux.org/viewtopic.php?id=248893  
- https://askubuntu.com/questions/752600/abnormal-logout-debugging  
- https://en.wikipedia.org/wiki/D-Bus  
- https://12bme.tistory.com/282  


## Other Packages Related to rtkit  
- https://packages.debian.org/sid/rtkit  