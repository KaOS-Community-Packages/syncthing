pkgname=syncthing
pkgver=0.14.12
pkgrel=1
pkgdesc="An open source continuous file synchronization"
url="http://syncthing.net/"
arch=('x86_64')
license=('MPL2')
category=Network
screenshot=http://i.imgur.com/VWzG7V3.png
source=("https://github.com/syncthing/syncthing/releases/download/v${pkgver}/syncthing-linux-amd64-v${pkgver}.tar.gz")
md5sums=('da1115f78b78895e1cbbcf5d98c5ba4d')
install=syncthing.install

package() {
   cd $pkgname-linux-amd64-v$pkgver
   install -Dm755 $pkgname $pkgdir/usr/bin/$pkgname
   install -Dm644 etc/linux-systemd/system/${pkgname}@.service $pkgdir/usr/lib/systemd/system/$pkgname@.service
}
