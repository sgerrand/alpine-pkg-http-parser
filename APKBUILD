# Contributor: Sasha Gerrand <alpine-pkgs@sgerrand.com>
# Maintainer: Sasha Gerrand <alpine-pkgs@sgerrand.com>
pkgname=http-parser
pkgver=2.7.1
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
source="http-parser-$pkgver.tar.gz::https://github.com/nodejs/http-parser/archive/v$pkgver.tar.gz"

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

sha512sums="c0fe86455db1a563a5c668f118dfa9a27b9a637ee1c0e2f2f18a5b816352436ed90435ea978e3f3d85b037d3c630234e47d609dc3b7086b898286c4e54d9f031  http-parser-2.7.1.tar.gz"
