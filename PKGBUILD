# Maintainer: Jan "heftig" Steffens <jan.steffens@gmail.com>
# Contributor: Michael Pusterhofer <pusterhofer(at)student(dot)tugraz(dot)at>

pkgname=itstool
pkgver=1.1.0
pkgrel=3
pkgdesc="XML to PO and back again"
arch=(any)
url="http://itstool.org/"
license=(GPL3)
source=(http://files.itstool.org/itstool/$pkgname-$pkgver.tar.bz2)
depends=(python2 libxml2)
md5sums=('088290c44c222abe656ae9366bbfa496')

build() {
  cd "$srcdir/$pkgname-$pkgver"
  sed -i '1s|#!/usr/bin/python|&2|' itstool itstool.in
  ./configure --prefix=/usr
  make
}

check() {
  cd "$srcdir/$pkgname-$pkgver"
  make -k check
}

package() {
  cd "$srcdir/$pkgname-$pkgver"
  make DESTDIR="$pkgdir" install
}
