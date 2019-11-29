# EFIGEN

Bundle a `linux.efi` which contains cmdline, kernel, initrds and os release.

## Requirements

This package is designed for Arch Linux users with the following configuration:

* `systemd` installed

* `binutils` installed

* Kernel: `linux`

* EFI partition is mounted at `/boot`

## Install

Root privilege is required.

```shell
$ makepkg -cfi
```

## Config

Configuration file (an envfile): `/etc/efigen/efigen.config`

Default values and descriptions are stated in that file. The default config may work for most Arch Linux machines with the following configuration:

* Initrd: `/boot/initramfs-linux.img`, no microcode.

* Kernel: '/boot/vmlinuz-linux'

* OS Release file: `/usr/lib/os-release`

* Kernel cmdline file: `/etc/efigen/cmdline.txt` **IMPORTANT: You need to create this file**

* Temp initrd file: `./temp.img` (TODO: Pacman hooks may not be able to write `/tmp`?)

* and requirements of this package.

If the default configuration does not satisfy your situation, you may need to edit the configuration file yourself.

## How to use

This includes a `pacman` hook, which will be executed after upgrading `linux` or `systemd` package.

# Disclaimer

I'm a total Linux beginner; this script may contain errors which will destory your boot partition. Use it with care, and feedbacks are always welcome.

# License

GPL v2
