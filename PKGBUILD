pkgname=syncthing
pkgver=0.13.2
pkgrel=1
pkgdesc="An open source continuous file synchronization"
url="http://syncthing.net/"
arch=('x86_64')
license=('MPL2')
category=Network
screenshot=http://i.imgur.com/VWzG7V3.png
source=("https://github.com/syncthing/syncthing/releases/download/v${pkgver}/syncthing-linux-amd64-v${pkgver}.tar.gz")
md5sums=('95fce602b0f840184c66f65be4c64540')
install=syncthing.install

package() {
   cd $pkgname-linux-amd64-v$pkgver
   install -Dm755 $pkgname $pkgdir/usr/bin/$pkgname
   install -Dm644 etc/linux-systemd/system/${pkgname}@.service $pkgdir/usr/lib/systemd/system/$pkgname@.service
}
