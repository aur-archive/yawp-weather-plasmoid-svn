# Maintainer: t3ddy  <t3ddy1988 "at" gmail {dot} com>

pkgname=yawp-weather-plasmoid-svn
pkgver=450
pkgrel=1
pkgdesc="Colorful kdeplasma weather plasmoid"
arch=('i686' 'x86_64')
url="http://www.kde-look.org/content/show.php/yaWP+(Yet+Another+Weather+Plasmoid)?content=94106"
depends=('kdebase-workspace>=4.2' 'gettext')
makedepends=('cmake' 'make' 'automoc4')
conflicts=('kde-extragear-plasmoids' 'yawp-weather-plasmoid')
provides=('yawp-weather-plasmoid')
license=('GPL')
 
_svnmod="yawp"
_svntrunk="https://yawp.svn.sourceforge.net/svnroot/yawp/trunk"

build() {
  msg "Starting SVN checkout..."
  
  cd $srcdir
    if [ -d $_svnmod/.svn ]; then
      (cd $_svnmod && svn up -r $pkgver)
    else
      svn co $_svntrunk --config-dir ./ -r $pkgver $_svnmod
    fi
  msg "SVN checkout done or server timeout"

  msg "Starting make..."

  cd $_svnmod
  cmake -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix` . || return 1
  make DESTDIR=${pkgdir} install || return 1
}