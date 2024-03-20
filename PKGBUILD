pkgname=mbpfan-git
pkgver=2.4.0.r3.g0cb3c5a6
pkgrel=1
pkgdesc="A simple daemon to control fan speed on all MacBook/MacBook Pros"
arch=('x86_64')
url="https://github.com/linux-on-mac/mbpfan"
license=('GPL3')
depends=('glibc')
makedepends=('git')
provides=('mbpfan')
conflicts=('mbpfan')
source=("$pkgname"::'git+https://github.com/linux-on-mac/mbpfan.git')
md5sums=('SKIP')
backup=('etc/mbpfan.conf')

pkgver(){
    cd "$srcdir/$pkgname"
    git describe --tags --long --abbrev=8 | sed 's/^v//;s/\([^-]*-g\)/r\1/;s/-/./g'
}

build() {
    cd "$srcdir/$pkgname"
    make
}

package() {
    cd "$srcdir/$pkgname"
    DESTDIR="$pkgdir" make install
    install -Dm644 "mbpfan.service" "$pkgdir/usr/lib/systemd/system/mbpfan.service"
}
