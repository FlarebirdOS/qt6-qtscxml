pkgname=qt6-qtscxml
pkgver=6.10.0
pkgrel=2
pkgdesc="Static and runtime integration of SCXML models into Qt6 code"
arch=('x86_64')
url="https://www.qt.io"
license=(
    'GPL-3.0-only'
    'LGPL-3.0-only'
    'LicenseRef-Qt-Commercial'
    'Qt-GPL-exception-1.0'
)
depends=(
    'gcc-libs'
    'glibc'
    'qt6-qtbase'
)
makedepends=(
    'cmake'
    'git'
    'ninja'
    'qt6-qtdeclarative'
)
source=(git+https://code.qt.io/qt/${pkgname#*-}#tag=v${pkgver})
sha256sums=(20eee37aae93c1a4fdaac8ab9b22dd1d3f81a6cef361620d9ab0513b6154f7ae)

build() {
    cd ${pkgname#*-}

    local cmake_args=(
        -B flarebird-build
        -G Ninja
        -D CMAKE_BUILD_TYPE=Release
        -D CMAKE_INSTALL_PREFIX=/usr
        -D INSTALL_LIBDIR=lib64
        -D CMAKE_MESSAGE_LOG_LEVEL=STATUS
    )

    cmake "${cmake_args[@]}"

    cmake --build flarebird-build
}

package() {
    cd ${pkgname#*-}

    DESTDIR=${pkgdir} cmake --install flarebird-build
}

