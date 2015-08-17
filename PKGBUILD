# Maintainer: Aleksey Ksenzov aka KsenZ <aksenzov@gmail.com>
pkgname=qxneur-git
pkgver=4eecd79
pkgrel=1
pkgdesc="Qt frontend for xneur"
arch=('i686' 'x86_64')
url="https://github.com/KsenZ/qxneur"
license=('GPLv2')
depends=('qt4' 'xneur')
makedepends=('gcc' 'make' 'cmake' 'git' 'pkgconfig')
source=('qxneur::git+https://github.com/KsenZ/qxneur.git')
_gitname="qxneur"
md5sums=('SKIP')

pkgver() {
  cd $_gitname
  git describe --always | sed 's|-|.|g'
}

build() {
    msg "Building and installing qxneur..."
    cd $_gitname
    cmake -DCMAKE_INSTALL_PREFIX=/usr -DCMAKE_BUILD_TYPE=Release . || return 1
    make || return 1
}

package() {
    cd $_gitname
    install -Dm 755 qxneur $pkgdir/usr/bin/qxneur || return 1
    install -Dm 644 qxneur_ru.qm $pkgdir/usr/share/qxneur/translations/qxneur_ru.qm || return 1
    cp -R images $pkgdir/usr/share/qxneur || return 1
}