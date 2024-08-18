# Maintainer: rodriguezst <git@rodriguezst.es>

pkgname="qbootctl"
pkgdesc="Qualcomm bootctl HAL for Linux"
pkgver=r0.0
pkgrel=1
arch=("aarch64")
url="https://github.com/rodriguezst/qbootctl"
license=("GPL3")
depends=("glibc" "zlib" "gcc-libs")
makedepends=("git" "meson" "gcc")
source=("git+https://github.com/rodriguezst/qbootctl.git")
md5sums=("SKIP")

pkgver() {
	cd "$pkgname"
	printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
	arch-meson "$pkgname" build
	meson compile -C build
}

package() {
	meson install -C build --destdir "$pkgdir"
	install -Dm644 "$pkgname/LICENSE" "$pkgdir"/usr/share/licenses/$pkgname/LICENSE
}
