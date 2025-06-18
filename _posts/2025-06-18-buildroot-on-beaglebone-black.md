---
layout: post
title:  "Making a slim linux image for Beaglebone Black using Buildroot"
date:   2025-06-18 17:44:47 +0200
categories: embedded beaglebone buildroot
---

Tested with Buildroot version 2025.02.3, which can be obtained from [here](https://buildroot.org/downloads/buildroot-2025.02.3.tar.xz).

1. Download source code:
```console
wget https://buildroot.org/downloads/buildroot-2025.02.3.tar.xz
```

2. unpack the tarball and change to custom name:
```console
tar xf buildroot-2025.02.3.tar.xz
mv buildroot-2025.02.3 buildroot-2025.02.3-bbb
```

3. generate makefile, then open the interactive menu to cutomize:
```console
make beaglebone_defconfig
make menuconfig
```
Definitely, you want to set the root password at *System configuration*.

4. compile, possibly in parallel:
```console
make -j10
```

5. Go to `output/images` and copy the SD card image:
```console
sudo dd if=output/images/sdcard.img of=/dev/sdf
```
