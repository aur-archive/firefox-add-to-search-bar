# Maintainer: Pierre Dorbais <pierre at dorbais dot fr>

pkgname=firefox-add-to-search-bar
pkgver=2.2
_addons_file=3682
pkgrel=2
pkgdesc="Add any search engine to the search bar."
arch=('any')
url="https://firefox.maltekraus.de/extensions/add-to-search-bar"
license=('MPL' 'GPL' 'LGPL')
depends=('firefox')
source=("https://addons.cdn.mozilla.net/storage/public-staging/${_addons_file}/add_to_search_bar-${pkgver}-fx.xpi")
md5sums=('327d1b9b48f4d68d118f8ef79bfde122')

package() {
  cd $srcdir
  local emid=$(sed -n '/.*<em:id>\(.*\)<\/em:id>.*/{s//\1/p;q}' install.rdf)
  local dstdir=$pkgdir/usr/lib/firefox/browser/extensions/${emid}
  [ -n ${emid} ] || return 1
  install -d $dstdir
  cp -R * $dstdir
  rm $dstdir/*.xpi
  find $pkgdir -type d -exec chmod 0755 {} \;
  find $pkgdir -type f -exec chmod 0644 {} \;
}
