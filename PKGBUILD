# Maintainer: Antoine Bertin <antoine.bertin@archlinux.org>

pkgname=gruvbox-plus-icon-theme
pkgver=5.3.1
pkgrel=1
pkgdesc="Icon theme based on Gruvbox color scheme"
arch=(any)
url=https://github.com/SylEleuth/gruvbox-plus-icon-pack
license=(GPL3)
depends=('gtk-update-icon-cache')
makedepends=('git' 'fd')
provides=(gruvbox-plus-icon-theme)
conflicts=()
options=(!strip !emptydirs)
source=("$pkgname-$pkgver.tar.gz::$url/archive/v$pkgver.tar.gz")
sha256sums=('aa548cab563bc8776f09b92cf8bdf5501ea7a1ffef32bfcf53ffa567ebf49120')

package() {
    cd "$pkgname/Gruvbox-Plus-Dark"
    # remove files with whitespaces as it messes up gtk-update-icon-cache
    fd '.*\s[^/]*' -X rm {}
    # remove cache as it will be generated again
    rm icon-theme.cache
    install -d "$pkgdir/usr/share/icons"
    cp -r ./ "$pkgdir/usr/share/icons/Gruvbox-Plus-Dark"
}
