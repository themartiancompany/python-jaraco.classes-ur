# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>
# Maintainer: Chih-Hsuan Yen <yan12125@archlinux.org>
# Contributor: Kyle Keen <keenerd@gmail.com>

_py="python"
_pyver="$( \
  "${_py}" \
    -V | \
    awk \
      '{print $2}')"
_pymajver="${_pyver%.*}"
_proj="jaraco"
_pkg="${_proj}.classes"
pkgname="${_py}-${_pkg}"
# https://github.com/jaraco/jaraco.classes/blob/main/NEWS.rst
pkgver=3.4.0
pkgrel=1
pkgdesc='Module for classes manipulation'
arch=(
  'any'
)
_http="https://github.com"
_ns="${_proj}"
url="${_http}/${_ns}/${_pkg}"
license=(
  'MIT'
)
depends=(
  "${_py}>=${_pymajver}"
  "${_py}-more-itertools"
)
makedepends=(
  "${_py}-build"
  "${_py}-installer"
  "${_py}-setuptools-scm"
  "${_py}-wheel"
)
checkdepends=(
  "${_py}-pytest-enabler"
  "${_py}-pytest-mypy"
  "${_py}-pip"
)
conflicts=(
 "${_py}-${_proj}"
)
replaces=(
 "${_py}-${_proj}"
)
source=(
  "${url}/archive/refs/tags/v${pkgver}/${_pkg}-${pkgver}.tar.gz"
)
sha512sums=(
  'dd321db10ffe0e5af0b8d061e2f2cfa42a6f61cc3117a1bdb84e5b403155525f467413279057aecc6fcc2d306dade0f542adb92540d71f525afc19aae717a103'
)

export \
  SETUPTOOLS_SCM_PRETEND_VERSION="${pkgver}"

build() {
  cd \
    "${srcdir}/${_pkg}-${pkgver}"
  "${_py}" \
    -m \
      build \
    --wheel \
    --no-isolation
}

check() {
  cd \
    "${srcdir}/${_pkg}-${pkgver}"
  "${_py}" \
    -m \
      pytest
}

package() {
  cd \
    "${srcdir}/${_pkg}-${pkgver}"
  "${_py}" \
    -m \
      installer \
    --destdir="${pkgdir}" \
    dist/*.whl
  install \
    -Dm644 \
    LICENSE \
    "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}

# vim:set ts=2 sw=2 et:
