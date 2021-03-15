# Support for the LED in Synaptics touchpads in Xorg

This is patched kernel module for touchpads with enable/disable LED button in left corner.

Originaly patches comes from Takashi Iwai from SUSE for supporting the LED in Synaptics touchpads.

This [video](https://www.youtube.com/watch?v=fj1Yf4ASag0) show how touchpads looks like.

## Upstream
Kernel sources get from [repo.or.cz](https://repo.or.cz/linux.git) at [linux-5.11.y](https://repo.or.cz/linux.git/shortlog/refs/heads/linux-5.11.y) head.
```
git archive --remote="git://repo.or.cz/linux.git" "linux-5.11.y" drivers/input/mouse | tar -x
```

## Dependencies
This module work with [xf86-input-synaptics-led](https://aur.archlinux.org/packages/xf86-input-synaptics-led/) patched Xorg driver.

## Build
Module can build from sources and compressed by `xz`:
```
make -C "/usr/lib/modules/$(uname -r)/build" M="$PWD" psmouse.ko
xz psmouse.ko
```

## Install
Module `psmouse.ko.xz` should be installed to directory:<BR>
`/usr/lib/modules/<kernel_version>/extramodules/`

AUR [package](https://aur.archlinux.org/packages/synaptics-led/) can be used for Arch Linux users.

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
