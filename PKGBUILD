# Maintainer: Robbie Smith <zoqaeski AT gmail DOT com>
# Contributor: Robbie Smith <zoqaeski AT gmail DOT com>
pkgname=netcfg-ppp-mobile-git
pkgver=1.0
pkgrel=2
pkgdesc="PPP (mobile) support for netcfg (Git version). "
url="https://wiki.archlinux.org/index.php/3G_and_GPRS_modems_with_pppd"
arch=(i686 x86_64)
license=('GPL')
depends=('netcfg>=2.5' 'ppp')
#source=(ppp-mobile.tar.xz)
install=$pkgname.install
sha256sums=('15b7b744b9e814e5fef24cc2b0813e2e4ecbff4203342c5e9ae8024b69462bd4')

build() {
	cd "$srcdir"
	msg "Connecting to GIT server..."
	if [ -d $_gitname ] ; then
		cd $_gitname && git pull origin
		msg "The local files are updated."
	else
		git clone --depth=1 $_gitroot $_gitname
	fi
	msg "GIT checkout done or server timeout"
}

package() {
	mkdir -p "${pkgdir}/etc/network.d/examples"
	mkdir -p "${pkgdir}/etc/ppp/chatscripts"
	mkdir -p "${pkgdir}/etc/ppp/peers"
	install -Dm644 "${srcdir}/ppp-mobile" "${pkgdir}/etc/network.d/examples/"
	install -Dm644 "${srcdir}/options-mobile" "${pkgdir}/etc/ppp/"
	install -D "${srcdir}/apn" "${pkgdir}/etc/ppp/chatscripts/"
	install -Dm644 "${srcdir}/apn.iinet" "${pkgdir}/etc/ppp/chatscripts/"
	install -Dm644 "${srcdir}/apn.optus-prepaid" "${pkgdir}/etc/ppp/chatscripts/"
	install -Dm644 "${srcdir}/mobile-modem.chat" "${pkgdir}/etc/ppp/chatscripts/"
	install -D "${srcdir}/mode" "${pkgdir}/etc/ppp/chatscripts/"
	install -Dm644 "${srcdir}/mode.3G-only" "${pkgdir}/etc/ppp/chatscripts/"
	install -Dm644 "${srcdir}/mode.3G-pref" "${pkgdir}/etc/ppp/chatscripts/"
	install -Dm644 "${srcdir}/mode.GPRS-only" "${pkgdir}/etc/ppp/chatscripts/"
	install -Dm644 "${srcdir}/mode.GPRS-pref" "${pkgdir}/etc/ppp/chatscripts/"
	install -Dm644 "${srcdir}/mode.NONE" "${pkgdir}/etc/ppp/chatscripts/"
	install -D "${srcdir}/pin" "${pkgdir}/etc/ppp/chatscripts/"
	install -Dm644 "${srcdir}/pin.NONE" "${pkgdir}/etc/ppp/chatscripts/"
	install -Dm644 "${srcdir}/mobile-noauth" "${pkgdir}/etc/ppp/peers/"
}
