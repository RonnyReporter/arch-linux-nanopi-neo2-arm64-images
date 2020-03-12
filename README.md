# Arch Linux (images) for NanoPi NEO2
These images are made using the great work by @mbouron found [here](https://github.com/mbouron/archlinuxarm-nanopi-neo2) (my [fork](https://github.com/RonnyReporter/archlinuxarm-nanopi-neo2) with some small fixes).
This is for those who don't want or can't download and install crosstool-ng or other dependencies or just want an easy way to try Arch out on the NEO2.

This is an unmodified [-current](http://archlinuxarm.org/os/) Arch Linux arm64 rootfs written to a 1.5GB image file.
Create sd card with something like Etcher. It is (pretty much) required to resize/expand the 1.5GB partition on your sd card, gparted is a great tool for that.

**Download the latest image [here](https://github.com/RonnyReporter/nanopi-neo2-arch/releases).**

Once booted please login with **alarm**/**alarm** then su to root with password **root** and run the follow commands:
```
pacman-key --init
pacman-key --populate archlinuxarm
pacman -Syu
```
Good luck, and have fun!

**Please note:** cpu frequency scaling is missing from the current 5.x kernel/dtb. Hopefully this will be added to the Arch kernel but it may require compiling a NEO2 specific kernel and/or applying correct dtb/overlays. I haven't ran any thermal issues using the stock heatsink. Monitoring temperatures can be done with the latest -rc kernel (see below).

![alt text](https://github.com/RonnyReporter/nanopi-neo2-arch/blob/master/screenie.png?raw=true)

##### Tweaks:
1. To disable (most of) the annoying audit messages on the console run `systemctl mask systemd-journald-audit.socket` as root to silence them.
2. For thermals to work you need to get the latest 5.x kernel install the `linux-aarch64-rc` package.
3. Install *[yay](https://github.com/Jguer/yay)* to easily install AUR packages such as *localepurge*.

Checking temperatures:

cpu=$(</sys/class/thermal/thermal_zone0/temp) && echo "$((cpu/1000)) c"
cpu=$(</sys/class/thermal/thermal_zone1/temp) && echo "$((cpu/1000)) c"

##### Networking:
1. Install dialog and wpa supplicant with `pacman -S dialog wpa_supplicant` to make the **wifi-menu** application work. This allows for an easy configuration of your wireless connection(s).

   Don't forget to *start* and also *enable* your network profile(s) with `netctl enable profile-name`, for more information check out [this](https://wiki.archlinux.org/index.php/Netctl#Configuration) page.
2. Disable systemd networking stuff as it sometimes gets in the way of netctl;

    ```
    systemctl disable systemd-resolved.service
    systemctl disable systemd-networkd.service
    ```
3. Install some additional packages like `iptables` `iproute2` `wavemon` to complete the networking stack.
___
###### Notes/to-do:

This is my first *"project"* on Github, be gentle and please don't look at all the commits, lol.

- Automatically expand filesystem on first boot?
- Try and detect v1.1 boards and make them work at 1.3ghz (kernel/boot-args/dts+dtb)
- Thermals
- CPU scaling
- See how Armbian does it ;-)
