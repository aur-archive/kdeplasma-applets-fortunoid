# Maintainer: Jeff Sharpe <jeff@impcode.com>
# Adopted package from
# Contributor: Zephyr

pkgname=kdeplasma-applets-fortunoid
pkgver=0.2.1
pkgrel=3
pkgdesc="Plasmoid showing a quote using the Fortune Cookie Program"
url="http://www.kde-look.org/content/show.php/fortunoid?content=98838"
arch=('i686' 'x86_64')
license=('GPL')
depends=('kdebase-workspace' 'fortune-mod')
makedepends=('cmake' 'automoc4')
conflicts=('fortunoid')
replaces=('fortunoid')
source=("http://www.kde-look.org/CONTENT/content-files/98838-fortunoid${pkgver}.tar.gz"
	'find-fortune-bin.patch')
md5sums=('c085801520b275ef2c2a675b68fecc96'
         'db124aae61217b90d182b04cf28459c5')

build() {
  # Fix the fortune binary location problem
  cd fortunoid
  patch -Np0 -i ${srcdir}/find-fortune-bin.patch
  cd ..

  mkdir build
  cd build
  cmake ../fortunoid \
    -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix` \
    -DCMAKE_BUILD_TYPE=Release
  make
}

package() {
  cd build
  make DESTDIR="${pkgdir}" install
}
