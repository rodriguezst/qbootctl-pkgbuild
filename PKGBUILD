# Maintainer: rodriguezst <git@rodriguezst.es>

pkgname="qbootctl"
pkgdesc="Qualcomm bootctl HAL for Linux"
pkgver=r0.0
pkgrel=2
arch=("aarch64")
url="https://github.com/rodriguezst/qbootctl"
license=("GPL3")
depends=("glibc" "zlib" "gcc-libs")
makedepends=("git" "meson" "gcc")
source=("git+https://github.com/rodriguezst/qbootctl.git"
		"qbootctl.service")
sha256sums=("SKIP"
			"dbb2f86b9bdff8809c475c4888860c2a3b4b10b9d0d3d0c73a151ce51f5cda8b")

pkgver() {
	cd "$pkgname"
	printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
	arch-meson "$pkgname" build
	meson compile -C build
        echo Variable value is"$VARIABLE"
}

package() {
	meson install -C build --destdir "$pkgdir"
	install -Dm644 "$pkgname/LICENSE" "$pkgdir"/usr/share/licenses/$pkgname/LICENSE
	install -Dm644 qbootctl.service "$pkgdir"/usr/lib/systemd/system/qbootctl.service
}
