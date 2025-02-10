# SPDX-License-Identifier: AGPL-3.0

#    ----------------------------------------------------------------------
#    Copyright © 2025  Pellegrino Prevete
#
#    All rights reserved
#    ----------------------------------------------------------------------
#
#    This program is free software: you can redistribute it and/or modify
#    it under the terms of the GNU Affero General Public License as published by
#    the Free Software Foundation, either version 3 of the License, or
#    (at your option) any later version.
#
#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU Affero General Public License for more details.
#
#    You should have received a copy of the GNU Affero General Public License
#    along with this program.  If not, see <https://www.gnu.org/licenses/>.

# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Truocolo <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
# Maintainer: Pellegrino Prevete (dvorak) <pellegrinoprevete@gmail.com>
# Maintainer: Pellegrino Prevete (dvorak) <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>

# Maintainer: Jan Alexander Steffens (heftig) <jan.steffens@gmail.com>
# Contributor: Michael Pusterhofer <pusterhofer(at)student(dot)tugraz(dot)at>

_py="python"
_pkg=itstool
pkgname="${_pkg}"
pkgver=2.0.7
pkgrel=2
epoch=1
pkgdesc="XML to PO and back again"
url="http://${_pkg}.org/"
arch=(
  'any')
license=(
  'GPL-3.0-only'
)
depends=(
  'docbook-xml'
  'libxml2'
  "${_py}"
)
makedepends=(
  "git"
)
_http="https://github.com"
_ns="${_pkg}"
_url="${_http}/${_ns}/${_pkg}"
source=(
  "git+${_url}?signed#tag=${pkgver}"
  "0001-Fix-the-crash-from-912099.patch"
  "0002-Fix-insufficiently-quoted-regular-expressions.patch"
)
b2sums=(
  '316a27ad8c76d789e773298a656d9d2516277f65be968e583e953c886f94d0e2a2af49fedc79c0652571affac7851e5dd1b671dfb92b0db3537b9495c1a95616'
  '42e496c4d0aa3c5561d259c970cb9f43835e50c94b273bc01b4e388d1d6d16f05dc00cfded631cd8fdf2c1bf28f6ec64c1e626b5bdc50c15abfa7020d398673a'
  'da79a18dee20e10c9b9e49824a09a00cab4b22abab83f3cb00d0d899216d0cf8b9d56b79f46714360312e87ec04501f6fedb3e2b8e2dcabca18c8777361f6490'
)
validpgpkeys=(
  # Shaun McCance <shaunm@redhat.com>
  "4E03CB89E1C8ED8E049367ABE5D9AD24CC3ADF80"
)

prepare() {
  cd \
    "${pkgname}"
  # https://src.fedoraproject.org/rpms/itstool/blob/rawhide/f/itstool-2.0.5-fix-crash-wrong-encoding.patch
  git \
    apply \
    -3 \
    "../0001-Fix-the-crash-from-912099.patch"
  # Fix insufficiently quoted regular expressions / Python 3.12
  ## https://github.com/itstool/itstool/pull/51
  git \
    apply \
    -3 \
    "../0002-Fix-insufficiently-quoted-regular-expressions.patch"
  autoreconf \
    -fvi
}

build() {
  cd \
    "${pkgname}"
  ./configure \
    --prefix="/usr"
  make
}

check() {
  cd \
    "${pkgname}"
  make \
    check
}

package() {
  cd \
    "${pkgname}"
  make \
    DESTDIR="${pkgdir}" \
    install
}
