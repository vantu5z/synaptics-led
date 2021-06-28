# Support for the LED in Synaptics touchpads in Xorg

This is patched kernel module for touchpads with enable/disable LED button in left corner.

Originaly patches comes from Takashi Iwai from SUSE for supporting the LED in Synaptics touchpads.

This [video](https://www.youtube.com/watch?v=fj1Yf4ASag0) show how these touchpads looks like.

## Upstream
Kernel sources are taken from [repo.or.cz](https://repo.or.cz/linux.git) at [linux-rolling-stable](https://repo.or.cz/linux.git/shortlog/refs/heads/linux-rolling-stable) head. Changes will be monitored and applied.
```
git archive --remote="git://repo.or.cz/linux.git" "linux-rolling-stable" drivers/input/mouse | tar -x
```

## Dependencies
This module work with [xf86-input-synaptics-led](https://aur.archlinux.org/packages/xf86-input-synaptics-led/) patched Xorg driver.

## Build
Module can be build from sources and compressed by `xz`:
```
git clone https://github.com/vantu5z/synaptics-led.git
cd synaptics-led
make -C "/usr/lib/modules/$(uname -r)/build" M="$PWD" psmouse.ko
xz psmouse.ko
```

## Install
Module `psmouse.ko.xz` should be installed to directory:<BR>
`/usr/lib/modules/<kernel_version>/extramodules/`

AUR [synaptics-led](https://aur.archlinux.org/packages/synaptics-led/) or [synaptics-led-dkms](https://aur.archlinux.org/packages/synaptics-led-dkms/) packages can be used for Arch Linux users.  
[DKMS](https://wiki.archlinux.org/title/Dynamic_Kernel_Module_Support) version advantage - you don't need to reinstall module manualy after every kernel update.  

## Load
To load or reload module you can use `modprobe`:
```
sudo modprobe -r psmouse
sudo modprobe psmouse
```
or just reboot PC.

## Links
https://github.com/perusio/xorg-synaptics-led-support <BR>
https://github.com/mmonaco/PKGBUILDs/tree/master/synaptics-led
