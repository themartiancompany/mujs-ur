# Maintainer: Daniel Bermond <dbermond@archlinux.org>

pkgname=mujs
pkgver=1.3.5
pkgrel=1
pkgdesc='An embeddable Javascript interpreter in C'
arch=('x86_64')
url='https://mujs.com/'
license=('ISC')
depends=('readline')
source=("https://github.com/ccxvii/mujs/archive/${pkgver}/${pkgname}-${pkgver}.tar.gz"
        '010-mujs-use-arch-flags.patch')
sha256sums=('78a311ae4224400774cb09ef5baa2633c26971513f8b931d3224a0eb85b13e0b'
            'f5a2cf4865f00b676f51264ef5a55d4dc953125e209f99c8fb81a76bb76fd42f')

prepare() {
    patch -d "${pkgname}-${pkgver}" -Np1 -i "${srcdir}/010-mujs-use-arch-flags.patch"
}

build() {
    make -C "${pkgname}-${pkgver}" prefix='/usr' release
}

package() {
    make -C "${pkgname}-${pkgver}" DESTDIR="$pkgdir" prefix='/usr' install-shared
    install -d -m755 "${pkgdir}/usr/share/doc"
    install -D -m644 "${pkgname}-${pkgver}/COPYING" "${pkgdir}/usr/share/licenses/mujs/LICENSE"
    cp -dr --no-preserve='ownership' "${pkgname}-${pkgver}/docs" "${pkgdir}/usr/share/doc/${pkgname}"
}
