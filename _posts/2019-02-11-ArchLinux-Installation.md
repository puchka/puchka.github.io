---
layout: post
comments: true
---

I was going through the process of installing Archlinux on a laptop
the last 2 days.

The process was much less painful than I expected.

In fact, the documentation is very detailed and straightforward to follow.

Maybe I just was lucky too.

I had some issues that was not trivial to resolve and I will discuss them below.

* For connecting to a WPA protected Wifi network

```
# wpa_supplicant -B -i interface -c <(wpa_passphrase MYSSID passphrase)
```

Then obtain an ip address manually
```
# dhcpcd interface
```

* The swap partition need to be primary if not mkswap will fail [1]

```
# grub-install --target=i386-pc /dev/sdX
```
where /dev/sdX is the disk where GRUB is to be installed (for example, disk /dev/sda and not partition /dev/sda1). [2]

This notes need more digging to find the real cause because I merely
skimmed through the forums to get the installation done without really
searching to understand why it was not working.

A final note is to install the internet tools after arch-chroot
in /mnt because you will not be able to install packages when
booting from the disk if you don't have internet access. [3]

Reference
----------

[1] https://wiki.archlinux.org/index.php/Installation_guide#Partition_the_disks

[2] https://wiki.archlinux.org/index.php/GRUB#Installation

[3] https://wiki.archlinux.org/index.php/Wpa_supplicant#Connecting_with_wpa_passphrase