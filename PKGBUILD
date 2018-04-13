pkgname=quartus-lite-cyclone
pkgver=17.1.0.590
pkgrel=1
pkgdesc="Cyclone IV device support for Quartus Prime Lite Edition"
arch=('i686' 'x86_64')
url="http://dl.altera.com/?edition=lite#tabs-2"
license=('custom')

_build_nr=$(echo ${pkgver} | cut -d '.' -f4)
_edition="std"
_alteradir="/opt/altera"

depends=('quartus-lite')

source=("cyclone-${pkgver}.zip::http://download.altera.com/akdlm/software/acdsinst/${pkgver%.*.*}${_edition}/${_build_nr}/ib_installers/cyclone-${pkgver}.qdz" )
md5sums=('09D346E4AE7AC403DF4F36563E6B7BFB')
options=('!strip' '!upx') # No need for device support
PKGEXT=".pkg.tar" # Do not compress

package() {
    cd "${srcdir}"

    # Use mv instead of install/cp to save I/O in case of big device support packages
    install -d -m755 "${pkgdir}/${_alteradir}/"
    mv ${srcdir}/quartus "${pkgdir}/${_alteradir}/"

    # Fix permissions
    cd "${pkgdir}/${_alteradir}"
    chmod -R u+w ./
}
