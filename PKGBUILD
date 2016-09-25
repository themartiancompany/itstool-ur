# Maintainer: Jan Alexander Steffens (heftig) <jan.steffens@gmail.com>
# Contributor: Michael Pusterhofer <pusterhofer(at)student(dot)tugraz(dot)at>

pkgname=itstool
pkgver=2.0.2+5+g676f3f7
pkgrel=2
pkgdesc="XML to PO and back again"
arch=(any)
url="http://itstool.org/"
license=(GPL3)
depends=(python2 libxml2)
makedepends=(git)
_commit=676f3f738b21ec4d77f300f83d31d2d0eceaddcc
source=("git+https://github.com/itstool/itstool#commit=$_commit")
sha256sums=('SKIP')

pkgver() {
  cd $pkgname
  git describe --tags | sed 's/-/+/g'
}

prepare() {
  cd $pkgname
  sed -i 's/| python/&2/' configure.ac
  autoreconf -fi
}

build() {
  cd $pkgname
  ./configure --prefix=/usr PYTHON=/usr/bin/python2
  make
}

check() {
  cd $pkgname
  make -k check
}

package() {
  cd $pkgname
  make DESTDIR="$pkgdir" install
}
