# Maintainer: Marius Rejdak <mariuswol at gmail dot com>
# Based on the DCP-J725DW PKGBUILD -> Mariusz Michalak <stricte at gumed dot edu dot pl>
pkgname=brother-dcpj552dw
pkgver=3.0.0_1
pkgrel=3
pkgdesc='Driver for the Brother DCP-J552DW wifi multifuncional printer'
url='http://support.brother.com/g/b/downloadtop.aspx?c=gb&lang=en&prod=dcpj552dw_eu_as'
license=('custom:brother')
depends=('a2ps' 'cups')
depends_x86_64=('lib32-glibc')
arch=('i686' 'x86_64')

md5sums=('1f20ac4b7f379e049bbcacb144977ea9'
         'a0478abfe85516e7b02993f2ed041da1'
         '63842cf3efbf87a25f85f77b841b6dd7')

source=("brother-dcpj552dw.patch"
        "http://download.brother.com/welcome/dlf007009/dcpj552dwlpr-${pkgver/_/-}.i386.rpm"
        "http://download.brother.com/welcome/dlf007011/dcpj552dwcupswrapper-${pkgver/_/-}.i386.rpm")

build() {
    cd "$srcdir"
    patch -Np0 < brother-dcpj552dw.patch
    sh "$srcdir"/opt/brother/Printers/dcpj552dw/cupswrapper/cupswrapperdcpj552dw > "$srcdir"/opt/brother/Printers/dcpj552dw/cupswrapper/brother_lpdwrapper_dcpj552dw
    chmod 755 "$srcdir"/opt/brother/Printers/dcpj552dw/cupswrapper/brother_lpdwrapper_dcpj552dw
}

package() {
    cp -R "$srcdir"/opt "$pkgdir"/opt

    install -d "$pkgdir"/usr/lib/cups/filter
    ln -s /opt/brother/Printers/dcpj552dw/cupswrapper/brother_lpdwrapper_dcpj552dw "$pkgdir"/usr/lib/cups/filter/

    install -d "$pkgdir"/usr/share/cups/model
    ln -s /opt/brother/Printers/dcpj552dw/cupswrapper/brother_dcpj552dw_printer_en.ppd "$pkgdir"/usr/share/cups/model

    install -m755 -D "$srcdir"/usr/bin/brprintconf_dcpj552dw "$pkgdir"/usr/bin/brprintconf_dcpj552dw
}
