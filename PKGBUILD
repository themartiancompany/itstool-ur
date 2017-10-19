# Maintainer: Jan Alexander Steffens (heftig) <jan.steffens@gmail.com>
# Contributor: Michael Pusterhofer <pusterhofer(at)student(dot)tugraz(dot)at>

pkgname=itstool
pkgver=2.0.4
pkgrel=3
pkgdesc="XML to PO and back again"
arch=(any)
url="http://itstool.org/"
license=(GPL3)
depends=(python3 libxml2)
makedepends=(git)
_commit=890f35998ba7f86bdc58227142309b8ecc618c10  # tags/2.0.4^0
source=("git+https://github.com/itstool/itstool#commit=$_commit")
sha256sums=('SKIP')

pkgver() {
  cd $pkgname
  git describe --tags | sed 's/-/+/g'
}

prepare() {
  cd $pkgname
  # https://github.com/itstool/itstool/issues/15#issuecomment-337820553
  git revert -n d3adf0264ee2b6fd28b7eff7dec33501d6e75a7c
  autoreconf -fvi
}

build() {
  cd $pkgname
  ./configure --prefix=/usr
  make
}

check() {
  cd $pkgname
  make check
}

package() {
  cd $pkgname
  make DESTDIR="$pkgdir" install
}
