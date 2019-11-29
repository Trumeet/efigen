# Maintainer: YuutaW <i@yuuta.moe>
# Thanks: https://aur.archlinux.org/cgit/aur.git/tree/PKGBUILD?h=systemd-boot-pacman-hook
pkgname=efigen
pkgver=1
pkgrel=1
pkgdesc=""
arch=("any")
url="https://github.com/Trumeet/efigen"
license=('GPL2')
depends=("linux"
        "systemd"
        "binutils")
source=(y-efigen.hook
        efigen
        efigen.config)
md5sums=('d894a704527d7ac407160f8d67837069'
         '36baf021eac6ef4fb40ad1fc3cb292b5'
         '47994b7df6fe434b3c680969189bc171')
backup=('etc/efigen/efigen.config')

package() {
    install -m755 -d "${pkgdir}/etc/pacman.d/hooks/"
    install -m755 -d "${pkgdir}/usr/bin/"
    install -m755 -d "${pkgdir}/etc/efigen/"
    install -m644 "${srcdir}/y-efigen.hook" "${pkgdir}/etc/pacman.d/hooks/"
    install -m755 "${srcdir}/efigen" "${pkgdir}/usr/bin/"
    install -m644 "${srcdir}/efigen.config" "${pkgdir}/etc/efigen"
}
