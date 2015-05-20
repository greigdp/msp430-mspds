# Maintainer: Your Name <youremail@domain.com>
# Taken from https://aur.archlinux.org/packages/mspds
pkgname=mspds
pkgver=3.5.0.1
pkgrel=1
pkgdesc="MSP430 Debug Stack. Contains a dynamic link library as well as embedded firmware that runs on the MSP-FET430UIF or the eZ430 emulators."
arch=('i686' 'x86_64')
url="http://processors.wiki.ti.com/index.php/MSPDS_Open_Source_Package"
license=('custom:TI Open Source')
group=('msp430')
depends=('hidapi' 'boost')
makedepends=('unzip' 'dos2unix')
optdepends=('mspdebug-git')
noextract=('slac460.zip')
source=('http://www-s.ti.com/sc/techzip/slac460.zip'
	'https://raw.githubusercontent.com/greigdp/msp430-mspds/master/v3.5.0.001.patch')

prepare() {
  unzip slac460.zip
  find ./MSPDebugStack_OS_Package/ -type f -exec dos2unix -q '{}' \;
  patch -p1 -d MSPDebugStack_OS_Package < ../v3.5.0.001.patch
}

build() {
	cd "$srcdir/MSPDebugStack_OS_Package"
	make
}

package() {
  install -Dm644 "$srcdir/MSPDebugStack_OS_Package/libmsp430.so" "$pkgdir/usr/lib/libmsp430.so"
}
sha256sums=('5aa34a1ecea324c404dae0e71b1e552b4cd5536678beac4dacaffbad5ea5eae2'
	    '564298885eb4cb13b647e1ef9a35be0369e6243b4f00750304de4c75b1d7a8c2')

