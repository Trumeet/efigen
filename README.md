# EFIGEN

Bundle a `linux.efi` which contains cmdline, kernel, initrds and os release.

## Requirements

This package is designed for Arch Linux users with the following configuration:

* `systemd` installed

* `binutils` installed

* EFI partition is mounted at `/boot`

## Install

Root privilege is required.

```shell
$ makepkg -cfi
```

## Config

Considering difference in kernels, we provide a way to adept in kernels. All configuration files (envfiles) are placed in `/etc/efigen/`, ending with `.config`. For example, configuration for kernel `linux` should be `/etc/efigen/linux.config`. Although names do not matter, it is suggested to use the same name as kernel name, because of the default naming method which will be talked later.

The default configuration is `/etc/efigen/linux.config`. It is supposed to work on the following situation:

* Initrd: `/boot/initramfs-linux.img`, no microcode.

* Kernel: `/boot/vmlinuz-linux`

* OS Release file: `/usr/lib/os-release`

* Kernel cmdline file: `/etc/efigen/cmdline.txt` **IMPORTANT: You need to create this file**

* Temp initrd file: `./temp.img` (TODO: Pacman hooks may not be able to write `/tmp`?)

* Output file: `/boot/linux.efi`

* Stub file: `/usr/lib/systemd/boot/efi/linuxx64.efi.stub`

* and requirements of this package.

If the default configuration does not satisfy your situation, you may need to edit the configuration file yourself. If you are using custom kernels, it is suggested to create a new file.

### Default Naming Method

To simplify your work, we provide a default naming method for initrds and kernels. According to names of configuration files (without `.config` extension), kernel and initrd file names are inferred as the following strategy: 

* Kernel: `/boot/vmlinuz-<Config name>`

* Initrd: `/boot/initramfs-<Config name>.img`

* Output file: `/boot/<Config name>.img`

If you are using microcodes, or files are not placed in default locations, you have to define variables yourself.

## How to use

This includes a `pacman` hook, which will be executed following mkinitcpio install, which occurs when `/usr/lib/modules/*/vmlinuz` or `/usr/lib/initcpio/*` is added or modified.

# Next Step

Reinstall kernel to initiate the first generate: `sudo pacman -S linux`.

For secure boot users, sign `/boot/*.efi`.

Get rid of bootloader: `sudo bootctl remove`.

Set boot option: either `efibootmgr` (Sometimes break on my computer, idk why) or BIOS menu

# Disclaimer

I'm a total Linux beginner; this script may contain errors which will destory your boot partition. Use it with care, and feedbacks are always welcome.

# Acknowledgements

* [https://github.com/xdever/arch-efiboot](https://github.com/xdever/arch-efiboot)

# License

GPL v2
