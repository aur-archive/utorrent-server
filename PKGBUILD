# Maintainer: Carl Reinke <mindless2112 gmail com>
pkgname=utorrent-server
pkgver=27079
pkgrel=1
pkgdesc='uTorrent server, BitTorrent client with web UI'
url='http://www.utorrent.com/downloads/linux'
license=('custom')
install="$pkgname.install"
source=("http://download.utorrent.com/linux/utorrent-server-3.0-ubuntu-12.04-${pkgver}.x64.tar.gz"
        'utserver' 'utserver.conf' 'utserver.rc.d' 'utserver.service')
md5sums=('baac6a08d0653eb7d2880e61a92627f8'
         'cc2abac1ce3d0efe475f16b70257bace'
         '3ded0803577a244ff18269412983dc32'
         '574c73e51b81615eb0fc99a5ec6b4454'
         '8ba727ba2d01eb54c30765db87eaf716')
arch=('i686' 'x86_64')
depends=('glibc' 'gcc-libs' 'bash' 'openssl' 'zlib')
conflicts=('utserver')

if [[ "$CARCH" == i686 ]]
then
    source[0]="http://download.utorrent.com/linux/utorrent-server-3.0-ubuntu-10.10-${pkgver}.tar.gz"
    md5sums[0]='145f795dd4a8ec9e1432efdde508d4f3'
    depends=('glibc' 'gcc-libs' 'bash' 'openssl098' 'zlib')
fi

package()
{
    install -dm755 "${pkgdir}"/srv/utserver/{downloads,settings,torrents}
    install -dm755 "${pkgdir}"/usr/share/utserver/webui
    install -dm755 "${pkgdir}"/usr/share/doc/utserver
    
    cd "${srcdir}/utorrent-server-v3_0"
    install -Dm755 utserver "${pkgdir}"/usr/share/utserver/utserver
    install -m644 docs/* "${pkgdir}"/usr/share/doc/utserver/
    bsdtar -xf webui.zip -C "${pkgdir}"/usr/share/utserver/webui/
    
    cd "${srcdir}"
    install -Dm755 utserver "${pkgdir}"/usr/bin/utserver
    install -Dm644 utserver.conf "${pkgdir}"/etc/utserver.conf
    install -Dm755 utserver.rc.d "${pkgdir}"/etc/rc.d/utserver
    install -Dm644 utserver.service "${pkgdir}"/usr/lib/systemd/system/utserver.service
}
