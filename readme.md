# awesome-shell-commands [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

> A curated list of tasks done from the command line


## Contents

- [Hardware specs](#hardware-specs)
- [Misc](#misc)
- [Operating system](#operating-system)
  - [Disk](#disk)


## Hardware specs

Querying the OS to get hardware info.

- Connected usb devices: `lsusb`
- Details on a usb device: `lsusb -d vendorId:productId -v`
- Get graphic controllers: `lspci | grep -i vga`
- Get graphic controllers (detailed): `lshw -C video`

## Misc

KEWL

- Nyancat: `nc -v nyancat.dakko.us 23`

## Operating system

Querying info about the OS

- Architecture: `uname -m`
- Distro: `cat /etc/*release`
- Distro name: `lsb_release -cs`
- Most recent kernel messages: `dmesg | tail`
- Packages installed (debian|ubuntu): `dpkg -l`
- Specific package installed: `dpkg -l nvidia*`

### Disk

- Mounted partitions (in human-friendly units): `df -h`
- Summary of disk space used by directories: `du -hs *`


## Contribute

Contributions welcome! Read the [contribution guidelines](contributing.md) first.


## License

[![CC0](http://mirrors.creativecommons.org/presskit/buttons/88x31/svg/cc-zero.svg)](http://creativecommons.org/publicdomain/zero/1.0)

To the extent possible under law,  has waived all copyright and
related or neighboring rights to this work.
