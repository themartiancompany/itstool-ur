# Maintainer: Jan Alexander Steffens (heftig) <jan.steffens@gmail.com>
# Contributor: Michael Pusterhofer <pusterhofer(at)student(dot)tugraz(dot)at>

pkgname=itstool
pkgver=2.0.4+1+g9b84c00
pkgrel=2
pkgdesc="XML to PO and back again"
arch=(any)
url="http://itstool.org/"
license=(GPL3)
depends=(python2 libxml2 docbook-xml)
makedepends=(git)
_commit=9b84c007a73e8275ca45762f1bfa3ab7c3a852e2  # master
source=("git+https://github.com/itstool/itstool#commit=$_commit")
sha256sums=('SKIP')

# itstool on python3 segfaults building gnome-getting-started-docs;
# can probably blame that one on the libxml2 bindings

pkgver() {
  cd $pkgname
  git describe --tags | sed 's/-/+/g'
}

prepare() {
  cd $pkgname
  autoreconf -fvi
}

build() {
  cd $pkgname
  ./configure --prefix=/usr PYTHON=/usr/bin/python2
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
