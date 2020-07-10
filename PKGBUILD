# Maintainer: Ivan Semkin (ivan at semkin dot ru)
# Contributor: kikadf <kikadf.01@gmail.com>

pkgname=mir
pkgver=1.8.0
pkgrel=1
pkgdesc="Canonical's display server"
url='https://mir-server.io'
arch=(x86_64 i686 aarch64)
license=(GPL LGPL)
conflicts=(mir)
provides=(mir)
depends=(gtest boost-libs capnproto google-glog gflags libglvnd  liburcu lttng-ust libepoxy libxml++2.6 nettle libinput libxkbcommon python-pillow freetype2 libevdev protobuf python-dbus python-gobject hicolor-icon-theme libxcursor yaml-cpp)
makedepends=(git glm doxygen cmake boost gcovr gmock lcov valgrind python-dbusmock umockdev wlcs)
optdepends=('qterminal: required for miral demos'
            'ttf-ubuntu-font-family: required for miral demos'
            'qt5-wayland: required for miral demos'
            'xcursor-dmz: opt requirement for miral demos'
            'qtubuntu: opt requirement for miral demos')
source=("https://github.com/MirServer/mir/archive/v${pkgver}.tar.gz")
sha256sums=('88848189d562ce9956b0ad62aa0287c8cdddeb7f14f79727ce67dcdaa63ee443')

BUILD_DIR=build

build() {
  cd ${pkgname}-${pkgver}
  mkdir -p ${BUILD_DIR}
  cd ${BUILD_DIR}
  cmake -DCMAKE_INSTALL_PREFIX:PATH=/usr -DCMAKE_INSTALL_LIBDIR="lib/" ..
  cmake --build ./
}

#check() {
#  cd ${pkgname}-${pkgver}/${BUILD_DIR}
#  GTEST_OUTPUT=xml:./
#  bin/mir_acceptance_tests
#  bin/mir_integration_tests
#  bin/mir_unit_tests
#}

package() {
  cd ${pkgname}-${pkgver}/${BUILD_DIR}
  make DESTDIR="${pkgdir}/" install
}
# vim:set ts=2 sw=2 et:
