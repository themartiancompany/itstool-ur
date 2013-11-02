# Maintainer: Jan Alexander Steffens (heftig) <jan.steffens@gmail.com>
# Contributor: Michael Pusterhofer <pusterhofer(at)student(dot)tugraz(dot)at>

pkgname=itstool
pkgver=2.0.0
pkgrel=1
pkgdesc="XML to PO and back again"
arch=(any)
url="http://itstool.org/"
license=(GPL3)
depends=(python2 libxml2)
source=(http://files.itstool.org/itstool/$pkgname-$pkgver.tar.bz2)
sha256sums=('14708111b11b4a70e240e3b404d7a58941e61dbb5caf7e18833294d654c09169')

prepare() {
  cd $pkgname-$pkgver
  sed -i '1s|#!/usr/bin/python|&2|' itstool itstool.in
}

build() {
  cd $pkgname-$pkgver
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
