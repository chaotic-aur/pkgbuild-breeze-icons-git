# Merged with official ABS breeze-icons PKGBUILD by João, 2021/03/05 (all respective contributors apply herein)
# Maintainer: João Figueiredo <jf.mundox@gmail.com>
# Contributor: Gustavo Alvarez <sl1pkn07@gmail.com>
# Contributor: FadeMind <fademind@gmail.com>

pkgname=breeze-icons-git
pkgver=5.80.0_r1711.gb86e319f
pkgrel=1
pkgdesc='Breeze icon themes'
arch=($CARCH)
url='https://community.kde.org/Frameworks'
license=(LGPL)
groups=(kf5-git)
makedepends=(git extra-cmake-modules-git qt5-base)
conflicts=(${pkgname%-git})
provides=(${pkgname%-git})
source=("git+https://github.com/KDE/${pkgname%-git}.git")
sha256sums=('SKIP')

pkgver() {
  cd ${pkgname%-git}
  _ver="$(grep -m1 'set(KF5\?_VERSION' CMakeLists.txt | cut -d '"' -f2 | tr - .)"
  echo "${_ver}_r$(git rev-list --count HEAD).g$(git rev-parse --short HEAD)"
}

build() {
  cmake -B build -S ${pkgname%-git} \
    -DBINARY_ICONS_RESOURCE=ON \
    -DBUILD_TESTING=OFF
  cmake --build build
}

package() {
  DESTDIR="$pkgdir" cmake --install build
}
