# Contributor: Nickolay Stepanenko <nixtrian at gmail dot com>
# Maintainer: tuftedocelot@fastmail.fm

pkgname=mcabber-module-pep-hg
pkgver=41
pkgrel=1
pkgdesc='A pep mcabber module'
url="http://wiki.mcabber.com/index.php/Modules"
license=(GPL)
arch=('i686' 'x86_64')
depends=('mcabber>=0.10.0')
makedepends=("cmake" "mercurial" "mcabber>=0.10.0")
conflicts=("mcabber-module-pep-hg" "mcabber-module-mood-hg" "mcabber-module-geoloc-hg" "mcabber-module-activity-hg" "mcabber-module-tune-hg")
replaces=("mcabber-module-pep-hg" "mcabber-module-mood-hg" "mcabber-module-geoloc-hg" "mcabber-module-activity-hg" "mcabber-module-tune-hg")

_hgroot="http://hg.isbear.org.ua/isbear/"
_hgrepo="mcabber-pep"

md5sums=(SKIP)
source=("hg+http://hg.isbear.org.ua/isbear/${_hgrepo}")

pkgver() {
    cd $_hgrepo
    echo $(hg identify -n)
}

build() {
	cp -rf $srcdir/$_hgrepo $srcdir/$_hgrepo-build
    
    msg "Building $pkgname ..."
	
    cd $srcdir/$_hgrepo-build
	
	cmake -DMCABBER_INCLUDE_DIR=/usr/include/mcabber -DCMAKE_INSTALL_PREFIX=/usr .
	make || return 1
}

package() {
    cd $srcdir/$_hgrepo-build
    DESTDIR=$pkgdir make install
}
