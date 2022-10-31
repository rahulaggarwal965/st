# Maintainer: Rahul Aggarwal

_pkgname=st
pkgname=st-git
pkgver=0.9.0
pkgrel=1
pkgdesc="Rahul's fork of st"
arch=("i686" "x86_64")
url="https://github.com/rahulaggarwal965/st"
license=("MIT")
depends=('libxft')
makedepends=('ncurses' 'libxext' 'git')
provides=("st")
conflicts=("st")
source=("git+https://github.com/rahulaggarwal965/st.git")
sha1sums=('SKIP')


pkgver() {
	cd "${_pkgname}"
	printf "%s.r%s.%s" "$(awk '/^VERSION =/ {print $3}' config.mk)" \
		"$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
	cd "${_pkgname}"
	make X11INC=/usr/include/X11 X11LIB=/usr/lib/X11 CFLAGS=-O2
}

package() {
	cd "${_pkgname}"
	make PREFIX=/usr DESTDIR="${pkgdir}" install
	install -Dm644 LICENSE "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
	install -Dm644 README "${pkgdir}/usr/share/doc/${pkgname}/README"
}
