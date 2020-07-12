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
source=("https://github.com/MirServer/mir/archive/v${pkgver}.tar.gz"
        "a701c3c9c1649a6959d4c0b1c7289ee83857633d.patch"
        "68480bc9654191b615b0e7b80c8a87599a417470.patch"
        "b8c2da5871a805602f40fc30abe1a6ac619916e2.patch"
        "0dfb6d76d04031441fb4d4fcb2e986f2874004a0.patch"
        "de9b340d823f4effff4c8d2b14b6c30e1f1c3097.patch")
sha256sums=('88848189d562ce9956b0ad62aa0287c8cdddeb7f14f79727ce67dcdaa63ee443'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP')

BUILD_DIR=build

build() {
  cd ${pkgname}-${pkgver}
  mkdir -p ${BUILD_DIR}
  cd ${BUILD_DIR}
  cmake -DCMAKE_INSTALL_PREFIX:PATH=/usr -DCMAKE_INSTALL_LIBDIR="lib/" ..
  cmake --build ./
}

prepare() {
  cd ${pkgname}-${pkgver}

  patch -Np1 -i "${srcdir}/a701c3c9c1649a6959d4c0b1c7289ee83857633d.patch"
  patch -Np1 -i "${srcdir}/68480bc9654191b615b0e7b80c8a87599a417470.patch"
  patch -Np1 -i "${srcdir}/b8c2da5871a805602f40fc30abe1a6ac619916e2.patch"
  patch -Np1 -i "${srcdir}/0dfb6d76d04031441fb4d4fcb2e986f2874004a0.patch"
  patch -Np1 -i "${srcdir}/de9b340d823f4effff4c8d2b14b6c30e1f1c3097.patch"
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
