pkgname=syncthing
pkgver=0.14.14
pkgrel=1
pkgdesc="An open source continuous file synchronization"
url="http://syncthing.net/"
arch=('x86_64')
license=('MPL2')
category=Network
screenshot=http://i.imgur.com/VWzG7V3.png
source=("https://github.com/syncthing/syncthing/releases/download/v${pkgver}/syncthing-linux-amd64-v${pkgver}.tar.gz"
        "syncthing.install")
sha1sums=('90aa492f5c0f5fe2d046667caf76c23579b83160'
          '5ceacfd6964ebb81be5af3db3a9c3aec613d7605')
install=syncthing.install

package() {
   cd $pkgname-linux-amd64-v$pkgver
   install -Dm755 $pkgname $pkgdir/usr/bin/$pkgname
   install -Dm644 etc/linux-systemd/system/${pkgname}@.service $pkgdir/usr/lib/systemd/system/$pkgname@.service
}
