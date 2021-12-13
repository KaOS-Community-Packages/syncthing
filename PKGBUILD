pkgname=syncthing
pkgver=1.18.5
pkgrel=1
pkgdesc="An open source continuous file synchronization"
url="http://syncthing.net/"
arch=('x86_64')
license=('MPL2')
makedepends=('go')
github_src="src/github.com/syncthing"
source=("https://github.com/syncthing/syncthing/archive/v${pkgver}.tar.gz")
md5sums=('a491d31fbc6e0d64e67ea1644c7f781b')
install=syncthing.install

prepare() {
    install -d ${github_src}
    mv ${pkgname}-${pkgver} ${github_src}/${pkgname}
    cd "${srcdir}/src/github.com/syncthing/${pkgbase}"
}

build() {
    export GOPATH=${srcdir}
    export PATH=$PATH:$GOROOT/bin
        
    cd ${github_src}/${pkgname}
    go run build.go -version v${pkgver} -no-upgrade #-with-next-gen-gui
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
        install -Dm644 $file ${pkgdir}/usr/share/man/man1/${file}
    done
    for file1 in $(find . -name '*.5' -print); do
        install -Dm644 $file ${pkgdir}/usr/share/man/man5/${file1}
    done
    for file2 in $(find . -name '*.7' -print); do
        install -Dm644 $file ${pkgdir}/usr/share/man/man7/${file2}
    done
}
