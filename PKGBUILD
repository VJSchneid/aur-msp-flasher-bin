# Maintainer: Peter Ivanov <ivanovp@gmail.com>

pkgname=msp-flasher
pkgver=1.03.20.00
pkgrel=1
pkgdesc="Flasher for TI MSP430 processor"
arch=('x86_64')
url="http://www.ti.com/tool/msp430-flasher"
license=('GPL')
depends=('elfutils' 'libmpc' 'zlib' 'gcc-libs' 'glibc')
options=(!strip !emptydirs !libtool staticlibs)
PKGEXT=".pkg.tar"
_installer=MSPFlasher-1_03_20_00-linux-x64-installer.zip
_installer_run=MSPFlasher-1.3.20-linux-x64-installer.run
source=("http://software-dl.ti.com/msp430/msp430_public_sw/mcu/msp430/MSP430Flasher/1_03_20_00/exports/$_installer")
sha1sums=('792f88f92bcf8386865367ea5c8f12d177eb3d28')
_install_dir=/opt/ti/$pkgname

build() {
  chmod +x $_installer_run
}

package() {
  msg "Running TI's installer..."
  ${srcdir}/$_installer_run --mode unattended --prefix $pkgdir$_install_dir
  msg "Correcting directory permissions..."
  find $pkgdir$_install_dir -type d -print0|xargs -0 chmod 755

  mkdir -p $pkgdir/usr/lib
  mkdir -p $pkgdir/usr/bin
  ln -s ../../opt/ti/msp-flasher/libmsp430.so $pkgdir/usr/lib/
  ln -s ../../opt/ti/msp-flasher/MSP430Flasher $pkgdir/usr/bin/
}

# vim:set sts=2 ts=2 sw=2 et:
