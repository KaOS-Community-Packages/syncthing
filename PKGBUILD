pkgname=syncthing
pkgver=0.14.21
pkgrel=1
pkgdesc="An open source continuous file synchronization"
url="http://syncthing.net/"
arch=('x86_64')
license=('MPL2')
category=Network
source=("https://github.com/syncthing/syncthing/archive/v${pkgver}.tar.gz")
md5sums=('e41ff22640010bd3b8c3682e70a4d40f')
install=syncthing.install
github_src="src/github.com/syncthing"

prepare() {
  mkdir -p ${github_src}
  mv ${pkgname}-${pkgver} ${github_src}/${pkgname}
}


build() {
    export GOPATH="$srcdir"
    export PATH=$PATH:$GOROOT/bin
        
    cd ${github_src}/${pkgname}
    go run build.go -version v${pkgver} -no-upgrade
}

package(){
    cd ${srcdir}/${github_src}/${pkgname}
    install -Dm755 bin/${pkgname} ${pkgdir}/usr/bin/${pkgname}
    install -Dm644 etc/linux-systemd/system/${pkgname}@.service ${pkgdir}/usr/lib/systemd/system/${pkgname}@.service
    install -Dm644 etc/linux-systemd/user/${pkgname}.service ${pkgdir}/usr/lib/systemd/user/${pkgname}.service
    install -Dm644 LICENSE ${pkgdir}/usr/share/licenses/${pkgname}/LICENSE
    
    cd man
    for file in $(find . -name '*.1' -print); do
        install -Dm644 $file ${pkgdir}/usr/share/man/man1/$file
    done
    for file in $(find . -name '*.5' -print); do
        install -Dm644 $file ${pkgdir}/usr/share/man/man5/$file
    done
    for file in $(find . -name '*.7' -print); do
        install -Dm644 $file ${pkgdir}/usr/share/man/man7/$file
    done
}
