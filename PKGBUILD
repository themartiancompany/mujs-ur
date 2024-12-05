# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>
# Maintainer: Daniel Bermond <dbermond@archlinux.org>

_pkg=mujs
pkgname="${_pkg}"
pkgver=1.3.5
pkgrel=1
pkgdesc='An embeddable Javascript interpreter in C'
arch=(
  'x86_64'
  'arm'
  'aarch64'
  'armv7l'
  'armv6l'
  'mips'
  'powerpc'
  'i686'
  'pentium4'
)
url="https://${_pkg}.com"
license=(
  'ISC'
)
depends=(
  'readline'
)
_http="https://github.com"
_ns="ccxvii"
_url="${_http}/${_ns}/${_pkg}"
source=(
  "${_url}/archive/${pkgver}/${_pkg}-${pkgver}.tar.gz"
  "010-${_pkg}-use-arch-flags.patch"
)
sha256sums=(
  '78a311ae4224400774cb09ef5baa2633c26971513f8b931d3224a0eb85b13e0b'
  'f5a2cf4865f00b676f51264ef5a55d4dc953125e209f99c8fb81a76bb76fd42f'
)

prepare() {
  patch \
    -d \
      "${_pkg}-${pkgver}" \
    -Np1 \
    -i \
      "${srcdir}/010-${_pkg}-use-arch-flags.patch"
}

build() {
  make \
    -C \
      "${_pkg}-${pkgver}" \
    prefix='/usr' \
    release
}

package() {
  make \
    -C \
      "${_pkg}-${pkgver}" \
      DESTDIR="${pkgdir}" \
      prefix='/usr' \
      install-shared
  install \
    -dm755 \
    "${pkgdir}/usr/share/doc"
  install \
    -Dm644 \
    "${_pkg}-${pkgver}/COPYING" \
    "${pkgdir}/usr/share/licenses/${_pkg}/LICENSE"
  cp \
    -dr \
    --no-preserve='ownership' \
    "${_pkg}-${pkgver}/docs" \
    "${pkgdir}/usr/share/doc/${_pkg}"
}

