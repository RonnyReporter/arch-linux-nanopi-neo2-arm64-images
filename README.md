# Arch Linux (images) for NanoPi NEO2
These images are made using the great work by @mbouron found [here](https://github.com/mbouron/archlinuxarm-nanopi-neo2).
This is for those who don't want or can't download and install crosstool-ng or other dependencies or just want an easy way to try Arch out on the NEO2.

This is an unmodified [-current](http://archlinuxarm.org/os/) Arch Linux arm64 rootfs written to a 1.5GB image file.
Create sd card with something like Etcher and then resize the partion on your sd card, gparted is great for it.

**Download the latest image [here](https://github.com/RonnyReporter/nanopi-neo2-arch/releases).**

Once booted please login with **alarm**/**alarm** then su to root with password **root** and run the follow commands:
```
pacman-key --init
pacman-key --populate archlinuxarm
pacman -Syu
```
Good luck, and have fun!

| Image name | SHA256 | Size |
| ---------- |--------|------|
| arch-arm-current-12042019.img.xz | d354bf017b528b5dba7a502d3879de749a54ea7b94be94e6af4251232a2126fd | 305MB |

**Please note:** Thermals and cpufreqency scaling is still missing from the current 5.1.x kernel. It should be fine but there's way to monitor if the cpu scaling is working or monitor cpu temps.

![alt text](https://github.com/RonnyReporter/nanopi-neo2-arch/blob/master/screenie.png?raw=true)

##### Tweaks:
1. To disable (most of) the annoying audit messages on the console run `systemctl mask systemd-journald-audit.socket` as root to silence them.
2. To get the latest 5.x kernel install the `linux-aarch64-rc` package.
3. Install *[yay](https://github.com/Jguer/yay)* to easily install AUR packages such as *localepurge*.

##### Networking:
1. Install dialog and wpa supplicant with `pacman -S dialog wpa_supplicant` to make the **wifi-menu** application work. This allows for an easy configuration of your wireless connection(s).

   Don't forget to *start* and also *enable* your network profile(s) with `netctl enable profile-name`, for more information check out [this](https://wiki.archlinux.org/index.php/Netctl#Configuration) page.

___
###### Notes/to-do:

This is my first *"project"* on Github, please be gentle.

1. Automatically expand filesystem on first boot?
2. Try and detect v1.1 boards and make them work at 1.3ghz (kernel/boot-args/dts+dtb)
3. ????
4. Profit!
