# Maintainer: Noel Maersk <veox at wemakethings dot net>

pkgname=sigrok-gtk-git
_gitname=sigrok-gtk
pkgver=66.1fe3e6c
pkgrel=1
pkgdesc="Client software that supports various hardware logic analyzers, GTK+ client (git version)"
arch=('i686' 'x86_64')
url="http://sigrok.org/wiki/Main_Page"
license=('GPL3')
depends=('glib2' 'libsigrok-git' 'libsigrokdecode-git' 'gtk2')
optdepends=()
makedepends=('git')
provides=('sigrok-gtk')
conflicts=('sigrok-gtk')
source=("git://sigrok.org/${_gitname}")
md5sums=('SKIP')

pkgver() {
  cd "${_gitname}"
  echo $(git rev-list --count master).$(git rev-parse --short master)
}

build() {
  cd "$srcdir/${_gitname}"

  ./autogen.sh
  CPPFLAGS="-I/usr/include/python3.3m" ./configure --prefix=/usr
  make
}

package() {
  cd "$srcdir/${_gitname}"
  make DESTDIR="$pkgdir" PREFIX=/usr install
}
