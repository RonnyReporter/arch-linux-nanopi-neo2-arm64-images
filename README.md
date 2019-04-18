# Arch Linux for NanoPi NEO2 board
The images are made using the great work by @mbouron found [here](https://github.com/mbouron/archlinuxarm-nanopi-neo2).
This is for those who don't or can't download and install crosstool-ng or other dependencies.

This is an unmodified -current arch linux rootfs and written to a 1.5GB image file.
Create sd card with something like Etcher and then resize the partion on your sd card, gparted is great for it.

Download the latest image [here](https://github.com/RonnyReporter/nanopi-neo2-arch/releases).

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
