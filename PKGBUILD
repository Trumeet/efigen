# Maintainer: YuutaW <i@yuuta.moe>
# Thanks: https://aur.archlinux.org/cgit/aur.git/tree/PKGBUILD?h=systemd-boot-pacman-hook
pkgname=efigen
pkgver=1
pkgrel=1
pkgdesc=""
arch=("any")
url=
license=('GPL')
depends=("linux"
        "systemd")
source=(y-efigen.hook
        efigen
        efigen.config)
md5sums=('322af73ce8599c769d71abd0aabe5990'
         'efbed9869cd119bb4ae4dd477970a7fc'
         '3ed60a34c1aad61324e3f36645232e76')

package() {
    install -m755 -d "${pkgdir}/etc/pacman.d/hooks/"
    install -m755 -d "${pkgdir}/usr/bin/"
    install -m755 -d "${pkgdir}/etc/efigen/"
    install -m644 "${srcdir}/y-efigen.hook" "${pkgdir}/etc/pacman.d/hooks/"
    install -m755 "${srcdir}/efigen" "${pkgdir}/usr/bin/"
    install -m644 "${srcdir}/efigen.config" "${pkgdir}/etc/efigen"
}
