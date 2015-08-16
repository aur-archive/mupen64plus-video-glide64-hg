# Contributer: BeholdMyGlory <larvid@gmail.com>
pkgname=mupen64plus-video-glide64-hg
pkgver=93
pkgrel=1
pkgdesc="Port of the Glide64 video plugin to Mupen64Plus v2.0, a Nintendo 64 emulator. Latest hg pull."
url="http://bitbucket.org/wahrhaft/mupen64plus-video-glide64"
license=("GPL")
arch=(i686 x86_64)
groups=(mupen64plus-hg)
depends=(mupen64plus-core-hg boost)
makedepends=(mercurial)
source=("hg+https://bitbucket.org/wahrhaft/mupen64plus-video-glide64")
md5sums=('SKIP')

pkgver() {
	cd $srcdir/${pkgname%-*}
	echo $(hg identify -n)
}

build() {
	cd "${srcdir}/${pkgname%-*}"
	sed -i "s,BOOST_SUFFIX ?= -mt,BOOST_SUFFIX ?= ,g" "projects/unix/Makefile"
	sed -i "s,BOOST_THREAD_SUFFIX ?= -mt,BOOST_THREAD_SUFFIX ?= ,g" "projects/unix/Makefile"
	make -C projects/unix all
}

package() {
	cd "${srcdir}/${pkgname%-*}"
	make -C projects/unix PREFIX=/usr DESTDIR=${pkgdir} install
}
