# Maintainer: Chih-Hsuan Yen <yan12125@archlinux.org>
# Contributor: Kyle Keen <keenerd@gmail.com>

pkgname=python-jaraco.classes
pkgver=3.3.1
pkgrel=2
pkgdesc='Module for classes manipulation'
arch=('any')
url='https://github.com/jaraco/jaraco.classes'
license=('MIT')
depends=('python-more-itertools')
makedepends=('python-build' 'python-installer' 'python-setuptools-scm' 'python-wheel')
checkdepends=('python-pytest-enabler' 'python-pytest-mypy' 'python-pip')
conflicts=(python-jaraco)
replaces=(python-jaraco)
source=("https://github.com/jaraco/jaraco.classes/archive/refs/tags/v$pkgver/jaraco.classes-$pkgver.tar.gz")
sha512sums=('dac9511926507ece5a8e2c413e70d8f44fcb3d27f4a74e9745545a3122a74b2752fb92fa58e6c3c166039a8576aee2a9f9e426b49a4aa556b824ddb2899b7645')

export SETUPTOOLS_SCM_PRETEND_VERSION=$pkgver

build() {
  cd "$srcdir/jaraco.classes-$pkgver"
  python -m build --wheel --no-isolation
}

check() {
  cd "$srcdir/jaraco.classes-$pkgver"
  python -m pytest
}

package() {
  cd "$srcdir/jaraco.classes-$pkgver"
  python -m installer --destdir="$pkgdir" dist/*.whl
  install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}

# vim:set ts=2 sw=2 et:
