---
layout: post
title: "Journey To Manjaro Linux - Part.1"
date: "2019-10-21 14:15:53 -0400"
published: false
categories: [linux]
---

This would be a long and painful series of logs of what did to install & configure Manjaro Linux on my Macbook.

## Settings
* Macbook: MacBook Pro (15-inch, 2016), Retina, Touchbar.
* Manjaro: Manjaro i3 (18.1.0)

<!--more-->

## Step.1 Setting up USB Bootable Disk

Like most of the installation process, we need a USB disk with Manjaro on it.  I use balenaEtcher to achieve this on Mac.  

This step surprisingly caused some trouble:

* Once the startup usb is ready, Mac would pop out a warning saying it cannot recognize this device.  **Ignore this message since it's normal that OSX cannot identify it.**
* One of the USB-C to USB Hub doesn't make the bootable partition show up during startup.

## Step.2 Booting into Manjaro Live Environment

Once booted into Manjaro (Live), the real pain starts.

**Problem 1:** In the initial menu where we select driver and timezone, the built-in keyboard works.  But once booted into live environment, built-in keyboard and touchpad does not work.

**Solution:** Use an external mouse and keyboard. Yep. Later we will fix this.  I originally thought I can get away without a mouse, but in the partition selection step it's simply impossible to select the partition.

## Step.3 Installing Keyboard/Mouse Driver

Once we installed it on the disk, now it's time to fix the keyboard and touchpad.  I mainly followed the instruction on [Keyboard and Mouse do not work in Live USB Manjaro i3 on MacBook]([https://forum.manjaro.org/t/keyboard-and-mouse-do-not-work-in-live-usb-manjaro-i3-on-macbook/83964](https://forum.manjaro.org/t/keyboard-and-mouse-do-not-work-in-live-usb-manjaro-i3-on-macbook/83964)), the basic idea is:

1. Install dkms
2. Install the Kernel header
3. Clone the driver into `/usr/src/` 

BUT, for some unknown reason, my Kernel was `5.2.11` and when I install the header, it installed `5.2.21` header, and the Driver couldn't fint the right kernel header for `5.2.11`.

In the end I gave up on `5.2.11` and rolled back to a `4.9` kernel.  Keep in mind that things in `/usr/src/` would get picked up and installed when you install new kernel.

Also, to change which Kernel you boot to, make some changes to your GRUB config `/etc/default/grub/` such that the GRUB menu would always show and we can select the kernel and we can select the kernel:

```

```


