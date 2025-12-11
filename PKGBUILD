# Maintainer: imcb <irismessage@protonmail.com>

pkgname='gp2-git'
pkgver=r1077.b34765e
pkgrel=1
pkgdesc=" The rule-based graph programming language GP 2"
arch=('x86_64')
url="https://uoycs-plasma.github.io/GP2/"
license=('GPL3')
depends=('judy')
makedepends=(
    'git'
    # stupid
    'pandoc'
)
checkdepends=()
optdepends=()
provides=("${pkgname%-git}")
conflicts=("${pkgname%-git}")
source=("${pkgname%-git}::git+https://github.com/UoYCS-plasma/GP2.git")
sha256sums=('SKIP')

pkgver() {
    cd "${pkgname}"

    # If there are no tags then use number of revisions since beginning of the history:
    printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short=7 HEAD)"
}

prepare() {
    cd "${pkgname}"
    # patch -p1 -i "$srcdir/${pkgname}-${pkgver}.patch"
}

build() {
    cd "${pkgname}"
    autoreconf -i
    ./configure --prefix=/opt/gp2
    make
}

# check() {
#     cd "${pkgname}"
#     make -k check
# }

package() {
    cd "${pkgname}"
    make DESTDIR="${pkgdir}/" install
}
