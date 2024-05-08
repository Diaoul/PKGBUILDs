# Maintainer: Antoine Bertin <antoine.bertin@archlinux.org>

pkgname=gruvbox-plus-icon-theme
pkgver=5.3.1  # renovate: datasource=github-tags depName=SylEleuth/gruvbox-plus-icon-pack
pkgrel=2
pkgdesc="Icon theme based on Gruvbox color scheme"
arch=(any)
url=https://github.com/SylEleuth/gruvbox-plus-icon-pack
license=(GPL3)
depends=('gtk-update-icon-cache')
makedepends=('git' 'fd')
provides=(gruvbox-plus-icon-theme)
conflicts=(gruvbox-plus-icon-theme-git)
options=(!strip !emptydirs)
source=("$pkgname-$pkgver.tar.gz::$url/archive/v$pkgver.tar.gz")
sha256sums=('aa548cab563bc8776f09b92cf8bdf5501ea7a1ffef32bfcf53ffa567ebf49120')

package() {
    cd "gruvbox-plus-icon-pack-$pkgver"
    install -d "$pkgdir/usr/share/icons"
    cp -r ./ "$pkgdir/usr/share/icons/Gruvbox-Plus-Dark"
}
