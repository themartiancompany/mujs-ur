# Maintainer: Daniel Bermond <dbermond@archlinux.org>

pkgname=mujs
pkgver=1.0.7
pkgrel=1
pkgdesc='An embeddable Javascript interpreter in C'
arch=('x86_64')
url='https://mujs.com/'
license=('ISC')
depends=('readline')
source=("${pkgname}-${pkgver}.tar.gz"::"https://github.com/ccxvii/mujs/archive/${pkgver}.tar.gz"
        '010-mujs-use-arch-flags.patch')
sha256sums=('9081244e070381300acaa5bf306a8b8b6f6231932ef4dca122992d3f6d243446'
            '93ad3ba48675cf9da33a764742c8188a6b32a27ad4d88f2507252f9ddcd13e37')

prepare() {
    patch -d "${pkgname}-${pkgver}" -Np1 -i "${srcdir}/010-mujs-use-arch-flags.patch"
}

build() {
    make -C "${pkgname}-${pkgver}" release
}

package() {
    make -C "${pkgname}-${pkgver}" DESTDIR="$pkgdir" prefix='/usr' install-shared
    install -D -m644 "${pkgname}-${pkgver}/COPYING" "${pkgdir}/usr/share/licenses/mujs/LICENSE"
    install -D -m644 "${pkgname}-${pkgver}/docs/"* -t "${pkgdir}/usr/share/doc/${pkgname}"
}
