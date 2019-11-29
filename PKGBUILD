# Maintainer: YuutaW <i@yuuta.moe>
# Thanks: https://aur.archlinux.org/cgit/aur.git/tree/PKGBUILD?h=systemd-boot-pacman-hook
pkgname=efigen
pkgver=1
pkgrel=1
pkgdesc=""
arch=("any")
url="https://github.com/Trumeet/efigen"
license=('GPL2')
depends=("systemd"
        "binutils")
source=(99-efigen.hook
        efigen
        linux.config)
md5sums=('3696655e397201916b0c23fbbc5d3bbd'
         '13805fb5bf05c729a7a9decf4fcf64b8'
         '35b7be991eaffb22e67afe597b72596b')
backup=('etc/efigen/linux.config')

package() {
    install -m755 -d "${pkgdir}/usr/share/libalpm/hooks/"
    install -m755 -d "${pkgdir}/usr/share/libalpm/scripts/"
    install -m755 -d "${pkgdir}/etc/efigen/"
    install -m644 "${srcdir}/99-efigen.hook" "${pkgdir}/usr/share/libalpm/hooks/"
    install -m755 "${srcdir}/efigen" "${pkgdir}/usr/share/libalpm/scripts/"
    install -m644 "${srcdir}/linux.config" "${pkgdir}/etc/efigen"
}
