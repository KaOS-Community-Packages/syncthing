pkgname=syncthing
pkgver=0.14.23
pkgrel=1
pkgdesc="An open source continuous file synchronization"
url="http://syncthing.net/"
arch=('x86_64')
license=('MPL2')
depends=('glibc')
makedepends=('go')
source=("https://github.com/syncthing/syncthing/archive/v${pkgver}.tar.gz")
md5sums=('64a445deecafdeb170177f98b4712811')
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
    
    local file file1 file2
    for file in $(find . -name '*.1' -print); do
        install -Dm644 $file ${pkgdir}/usr/share/man/man1/$file
    done
    for file1 in $(find . -name '*.5' -print); do
        install -Dm644 $file ${pkgdir}/usr/share/man/man5/$file1
    done
    for file2 in $(find . -name '*.7' -print); do
        install -Dm644 $file ${pkgdir}/usr/share/man/man7/$file2
    done
}
