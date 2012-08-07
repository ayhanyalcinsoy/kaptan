#
# Apps Packages for Chakra, part of chakra-project.org
# 
# Maintainer: george <george[at]chakra-project.org>

pkgname=kapudan
pkgver=20120807
pkgrel=1
pkgdesc="Chakra's desktop greeter, a fork of Pardus's Kaptan."
arch=('i686' 'x86_64')
url='http://gitorious.org/chakra/kapudan/'
screenshot='http://i.imgur.com/71aU5.png'
license=('GPLv2')
conflicts=('kapudan-git')
depends=('python2' 'kde-baseapps-konsole' 'kde-runtime'
         'kdebindings-pykde4' 'pyqt' 'python2-xlib'
         'python2-v4l2capture' 'python-imaging')
makedepends=('python-distribute' 'git')
optdepends=('spun: update notifications'
            'clamav: for the security page')
source=("http://chakra-linux.org/sources/${pkgname}/${pkgname}-${pkgver}.tar.xz")
md5sums=('c9bd8288f6e572c6ca1c64ebf2279921')

mksource() {
    git clone git://gitorious.org/chakra/${pkgname}.git ${pkgname}
    pushd ${pkgname}
    popd
    rm ${pkgname}/PKGBUILD
    tar -cvJf ${pkgname}-${pkgver}.tar.xz ${pkgname}
    md5sum ${pkgname}-${pkgver}.tar.xz
}

package() {
    cd "${srcdir}/${pkgname}"
    python2 setup.py install --root="${pkgdir}" #--prefix="/usr"
    install -Dm755 kapudan-rootactions "${pkgdir}/usr/bin/kapudan-rootactions"
    install -Dm755 kapudan.desktop "${pkgdir}/usr/share/applications/kapudan.desktop"
    install -Dm644 data/kapudan.svgz \
        "${pkgdir}/usr/share/icons/hicolor/scalable/apps/kapudan.svgz"
    install -dm755 \
        "${pkgdir}/usr/share/kde4/apps/kapudan/kapudan/kde-themes/"
    install -Dm644 data/kde-themes/* \
        "${pkgdir}/usr/share/kde4/apps/kapudan/kapudan/kde-themes/"
    install -Dm755 kapudan-autostart.desktop \
        "${pkgdir}/usr/share/kde4/apps/kapudan/kapudan/kapudan-autostart.desktop"
}
