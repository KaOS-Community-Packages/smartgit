pkgname=smartgit
pkgver=18.1.5
pkgrel=1
pkgdesc="Git client with Hg and SVN support."
arch=("x86_64")
url="http://www.syntevo.com/smartgit"
license=('custom')
depends=("java-runtime" "desktop-file-utils" "git" "gtk2")
optdepends=("mercurial" "subversion")
# package version as it appears in the name of tar.gz archive file
_pkgver=${pkgver//\./_}
source=(https://www.syntevo.com/downloads/${pkgname}/${pkgname}-linux-${_pkgver}.tar.gz
        smartgit.desktop)
install="smartgit.install"
md5sums=('2d817ab3b9faf6305c5f2f09fc42092f'
         'db7de01424b290a41db6e010be11b45c')

package() {
    mkdir -p "${pkgdir}"/opt
    mv "${pkgname}" ${pkgdir}/opt/${pkgname} || return 1

    install -D -m644 smartgit.desktop "${pkgdir}"/usr/share/applications/${pkgname}.desktop

    # link icon files
    mkdir -p ${pkgdir}/usr/share/icons/hicolor/{32x32,48x48,64x64,128x128,256x256}/apps
    cd ${pkgdir}/usr/share/icons/hicolor
    ln -s /opt/${pkgname}/bin/smartgit-32.png 32x32/apps/${pkgname}.png
    ln -s /opt/${pkgname}/bin/smartgit-48.png 48x48/apps/${pkgname}.png
    ln -s /opt/${pkgname}/bin/smartgit-64.png 64x64/apps/${pkgname}.png
    ln -s /opt/${pkgname}/bin/smartgit-128.png 128x128/apps/${pkgname}.png
    ln -s /opt/${pkgname}/bin/smartgit-256.png 256x256/apps/${pkgname}.png

    # create link in /usr/bin
    cd ${pkgdir}
    chmod 755 opt/${pkgname}/bin/smartgit.sh
    mkdir -p usr/bin
    ln -s /opt/${pkgname}/bin/smartgit.sh usr/bin/${pkgname}
}
