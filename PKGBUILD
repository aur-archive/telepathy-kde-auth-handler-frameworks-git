# Maintainer: Antonio Rojas 

pkgname=telepathy-kde-auth-handler-frameworks-git
pkgver=r202.801b286
pkgrel=1
pkgdesc='Provide UI/KWallet Integration For Passwords and SSL Errors on Account Connect'
arch=('i686' 'x86_64')
url='http://community.kde.org/Real-Time_Communication_and_Collaboration'
license=('GPL')
depends=('qca-qt5' 'kdewebkit' 'telepathy-kde-common-internals-frameworks-git' 'libaccounts-qt5' 'signon-qt5')
makedepends=('extra-cmake-modules' 'git')
source=("git://anongit.kde.org/ktp-auth-handler.git#branch=frameworks")
sha256sums=('SKIP')

pkgver() {
  cd ktp-auth-handler
  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

prepare() {
  mkdir -p build
}

build() {
  cd build
  cmake ../ktp-auth-handler \
    -DCMAKE_INSTALL_PREFIX=/opt/kf5 \
    -DCMAKE_BUILD_TYPE=Release \
    -DLIB_INSTALL_DIR=lib \
    -DQT_PLUGIN_INSTALL_DIR=lib/qt/plugins
  make
}

package() {
  cd build
  make DESTDIR="${pkgdir}" install
}
