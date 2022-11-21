pkgname=st-xaizone-git
_pkgname=st
pkgver=0.9
pkgrel=1
pkgdesc="xaizone's simple terminal build by suckless.org with xresources and other patches."
url="https://github.com/xaizone/st"
arch=(x86_64)
license=('MIT')
options=()
depends=(libxft)
makedepends=(git)
optdepends=()
source=(git+$url)
sha1sums=('SKIP')
provides=("${_pkgname}")
conflicts=("${_pkgname}")

pkgver() {
	cd "${_pkgname}"
	printf "%s.r%s.%s" "$(awk '/^VERSION =/ {print $3}' config.mk)" \
		"$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

prepare() {
	cd $srcdir/${_pkgname}
	sed -i '/tic /d' Makefile
}

build() {
	cd "${_pkgname}"
	make X11INC=/usr/include/X11 X11LIB=/usr/lib/X11
}

package() {
	cd "${_pkgname}"
	make PREFIX=/usr DESTDIR="${pkgdir}" install
}
