# Maintainer: Jan Alexander Steffens (heftig) <jan.steffens@gmail.com>
# Contributor: Michael Pusterhofer <pusterhofer(at)student(dot)tugraz(dot)at>

pkgname=itstool
pkgver=1.2.0
pkgrel=1
pkgdesc="XML to PO and back again"
arch=(any)
url="http://itstool.org/"
license=(GPL3)
source=(http://files.itstool.org/itstool/$pkgname-$pkgver.tar.bz2)
depends=(python2 libxml2)
sha256sums=('46fed63fb89c72dbfc03097b4477084ff05ad6f171212d8f1f1546ea543978aa')

build() {
  cd $pkgname-$pkgver
  sed -i '1s|#!/usr/bin/python|&2|' itstool itstool.in
  ./configure --prefix=/usr
  make
}

check() {
  cd $pkgname-$pkgver
  make -k check
}

package() {
  cd $pkgname-$pkgver
  make DESTDIR="$pkgdir" install
}
