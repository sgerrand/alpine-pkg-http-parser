# Contributor: Sasha Gerrand <alpine-pkgs@sgerrand.com>
# Maintainer: Sasha Gerrand <alpine-pkgs@sgerrand.com>
pkgname=http-parser
pkgver=2.7.0
pkgrel=0
pkgdesc="HTTP request/response parser for C"
url="https://github.com/nodejs/http-parser"
arch="all"
license="MIT"
depends=""
depends_dev=""
makedepends="$depends_dev automake gcc"
install=""
subpackages="$pkgname-dev $pkgname-doc"
source="http-parser-$pkgver.tar.gz::https://github.com/nodejs/http-parser/archive/v$pkgver.tar.gz
		10-remove-unused-test-variable.patch"

_builddir="$srcdir"/http-parser-$pkgver
prepare() {
	local i
	cd "$_builddir"
	for i in $source; do
		case $i in
		*.patch) msg $i; patch -p1 -i "$srcdir"/$i || return 1;;
		esac
	done
}

build() {
	cd "$_builddir"
	make || return 1
}

package() {
	local i
	cd "$_builddir"
	mkdir -p "$pkgdir/usr/share/doc/$pkgname" || return 1
	for i in AUTHORS README.md; do
		install -Dm644 $i "$pkgdir/usr/share/doc/$pkgname/$i"
	done
	mkdir -p "$pkgdir/usr/share/licenses/$pkgname" || return 1
	install -Dm644 LICENSE-MIT "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
	make DESTDIR="$pkgdir" PREFIX="$pkgdir/usr" install || return 1
}

md5sums="335f0a0748684640078474c897d87804  http-parser-2.7.0.tar.gz
0f0cd6446e19612ba906db735580efc4  10-remove-unused-test-variable.patch"
sha256sums="b0c5bf03fe9a57c4e63760d19d5a51d3063e0502cae54b3a8f2f6c6eb6911167  http-parser-2.7.0.tar.gz
3e598cb857119b92733e0399734ab7cc1c02278eb53455f099c175dbf95eb4d5  10-remove-unused-test-variable.patch"
sha512sums="1fe13b5366e9d161dbce2f6ad340890713413e4c5865d2567cb5ccf5601a52bc03682ecc43bc4e2c5ee9c4f152993a658d87fd43373070da67530c58ad577ee1  http-parser-2.7.0.tar.gz
548967e8c0aed6e75524dec24a3bc0c8bf0437f541fb1d807e5e1d77e2e6b39b8e407884530eed068638445f2706e448a769ce8c769eec5ede0d739592eb8999  10-remove-unused-test-variable.patch"
