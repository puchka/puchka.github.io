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

> To show the available network interfaces, run the the command below:
```
$ ip link show
```

> Note: Because of the process substitution, you cannot run this command with sudo and must use a root shell, see Help:Reading#Regular user or root for more explanations. Just pre-pending sudo will lead to the following error: [1]
```
Successfully initialized wpa_supplicant
Failed to open config file '/dev/fd/63', error: No such file or directory
Failed to read or parse configuration '/dev/fd/63'
```
e.g. You should be able to use su -c under sudo like so: [2]
```
$ sudo su -c 'wpa_supplicant -D nl80211,wext -i wlp4s0 -c \
    <(wpa_passphrase "some ssid" "password")'
```

Then obtain an ip address manually
```
# dhcpcd interface
```

If the router doesn't have DHCP activated, the process of obtaining new IP address, add default route and DNS server has to be done manually. [6]

```bash
ip addr add 192.168.1.1/24 dev em1
ip route add default via 192.168.1.1 dev em1
resolvectl dns em1 8.8.8.8
```

You need to enable `systemd-resolved.service` before using `resolvectl` [7]

Check if it's running and enabled.
```bash
systemctl status systemd-resolved.service
```

Enable and start it.
```bash
systemctl enable systemd-resolved.service
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

[1] https://wiki.archlinux.org/title/Wpa_supplicant#Connecting_with_wpa_passphrase

[2] https://unix.stackexchange.com/questions/279545/failed-to-open-config-file-dev-fd-63-error-no-such-file-or-directory-for-wp

[3] https://wiki.archlinux.org/index.php/Installation_guide#Partition_the_disks

[4] https://wiki.archlinux.org/index.php/GRUB#Installation

[5] https://wiki.archlinux.org/index.php/Wpa_supplicant#Connecting_with_wpa_passphrase

[6] https://access.redhat.com/sites/default/files/attachments/rh_ip_command_cheatsheet_1214_jcs_print.pdf

[7] https://superuser.com/questions/1427311/activation-via-systemd-failed-for-unit-dbus-org-freedesktop-resolve1-service
