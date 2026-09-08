# Maintainer: lovedel <lovedel@github.com>
pkgname=gpa-git
pkgver=0.11.2.r0.g2f022c4
pkgrel=1
pkgdesc="A graphical user interface for the GnuPG"
arch=('x86_64')
url="https://www.gnupg.org/related_software/gpa/"
license=('GPL-3.0-or-later')
depends=('gpgme' 'gtk3')
makedepends=('git' 'glib2-devel' 'libgpg-error')
provides=('gpa')
conflicts=('gpa')
source=('gpa-git::git+https://github.com/lovedel/gpa.git')
sha256sums=('SKIP')

pkgver() {
  cd "$pkgname"
  git describe --long | sed 's/^gpa-//;s/\([^-]*-g\)/r\1/;s/-/./g'
}

prepare() {
  cd "$pkgname"
  ./autogen.sh
}

build() {
  cd "$pkgname"
  ./configure --prefix=/usr
  make
}

check() {
  cd "$pkgname"
  make -k check || :
}

package() {
  cd "$pkgname"
  make DESTDIR="$pkgdir/" install
  rm -rf "$pkgdir/src"
}
