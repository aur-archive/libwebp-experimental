# Contributor: spider-mario <spidermario@free.fr>
pkgname=libwebp-experimental
pkgver=2
pkgrel=1
pkgdesc="Tools to convert to & from PNG to the experimental webp-alpha/webp-lossless formats."
arch=('i686' 'x86_64')
url="http://code.google.com/p/webp/"
license=('custom')
depends=('libpng12')

case "$CARCH" in
	i686)
		_tarball=http://webp.googlecode.com/files/$pkgname-linux-x86-32-$pkgver.tar.gz
		_checksum='16f4e0f88cc3f833d38fcfee8fc8faec'
		;;
	x86_64)
		_tarball=http://webp.googlecode.com/files/$pkgname-linux-x86-64-$pkgver.tar.gz
		_checksum='dc521f521a51db48e547b522074439bd'
		;;
esac

source=(http://libwebp.webm.googlecode.com/git/COPYING
        $_tarball)
md5sums=(6e8dee932c26f2dab503abf70c96d8bb
         $_checksum)

build() {
  cd "$srcdir/$pkgname"-*/

  perl -pe 's{(declare -r BINPATH=)\$\(pwd\)}{$1/usr/bin/}' -i png2webp_opt.sh
}

package() {
  cd "$srcdir/$pkgname"-*/

  install --directory "$pkgdir"/usr/share/licenses/$pkgname \
                      "$pkgdir"/usr/bin

  cp "$srcdir"/COPYING "$pkgdir"/usr/share/licenses/$pkgname/
  cp png2webpll png2webp_opt.sh webpll2png "$pkgdir"/usr/bin/
}

# vim:set ts=2 sw=2 et:
