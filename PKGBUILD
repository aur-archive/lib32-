﻿_pkgbase=ocl-icd
pkgname=lib32-$_pkgbase
pkgver=2.2.3
_pkgver=598
pkgrel=1
pkgdesc="OpenCL ICD Bindings"
arch=('x86_64')
url="https://forge.imag.fr/projects/ocl-icd/"
license=('GPL')
depends=('glibc')
makedepends=('ruby' 'opencl-headers12')
checkdepends=()
provides=('lib32-libcl')
conflicts=('lib32-libcl')
source=(http://forge.imag.fr/frs/download.php/$_pkgver/$pkgname-$pkgver.tar.gz)
md5sums=('6b4733e72c67bb28f4e27272ced6fb3d')

build() {
  export CC="gcc -m32"
  export CXX="g++ -m32"
  export PKG_CONFIG_PATH="/usr/lib32/pkgconfig"

  cd "$srcdir/$_pkgbase-$pkgver"
  ./configure --prefix=/usr --libdir=/usr/lib32
  make
}

check() {
  cd "$srcdir/$_pkgbase-$pkgver"
  make -k check
}

package() {
  cd "$srcdir/$_pkgbase-$pkgver"
  make DESTDIR="$pkgdir/" install
  cd "$pkgdir/usr"
  rm -rf share
  rm -rf include
}

# vim:set ts=2 sw=2 et:
