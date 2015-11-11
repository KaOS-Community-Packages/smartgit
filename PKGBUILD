pkgname=smartgit
pkgver=7.0.3
pkgrel=1
pkgdesc="Git client with Hg and SVN support."
arch=("x86_64")
url="http://www.syntevo.com/smartgit"
license=('custom')
depends=("java-runtime" "desktop-file-utils" "git" "gtk2")
optdepends=("mercurial" "subversion")
# package version as it appears in the name of tar.gz archive file
_pkgver=${pkgver//\./_}
# folder within tar.gz archive
_pkgfolder=${pkgname}
source=(https://www.syntevo.com/downloads/${pkgname}/${pkgname}-generic-${_pkgver}.tar.gz
        smartgit.desktop)
install="smartgit.install"
md5sums=('a33819ab59229049d5b847d78b72c0c0'
         'c372fb0864ce6010c92f75910acbe8d0')

package() {
    cd "$srcdir"

    #install -D -m644 "${_pkgfolder}"/licenses/* "${pkgdir}/usr/share/licenses/${pkgname}"
    mkdir -p "${pkgdir}"/opt
    mv "${_pkgfolder}" ${pkgdir}/opt/${pkgname} || return 1

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