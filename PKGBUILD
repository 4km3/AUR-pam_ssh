# Maintainer: pancho horrillo <pancho at pancho dot name>
# Contributor: bender02 at archlinux dot us
# Contributor: Troels Kofoed Jacobsen <tkjacobsen at gmail dot com>

pkgname=pam_ssh
pkgver=2.3
pkgrel=2
pkgdesc='PAM module providing single sign-on behavior for SSH.'
arch=('i686' 'x86_64')
url='http://pam-ssh.sourceforge.net/'
license=('custom')
depends=('pam' 'openssl' 'openssh')
options=('!libtool')
install="$pkgname.install"
source=(
  "https://sourceforge.net/projects/pam-ssh/files/pam_ssh/$pkgver/pam_ssh-$pkgver.tar.xz"{,.asc}
)
sha512sums=('e3ddcf851ffd8f6fb831e2dee7269c1b89283ae2f8f6aa3487bf7b1bc71d26ac9bcbd2a01c5a67a983b980bbb5151e991402940f4752741286d057843c817895'
            'SKIP')
validpgpkeys=(
  '501B088D8485568B87BB62BE180F6A5B3EDE742E'	# Wolfgang Rosenauer
)

build () {
  cd "$srcdir/$pkgname-$pkgver"
  CFLAGS="$CFLAGS -fcommon" ./configure --prefix=/usr --with-pam-dir=/usr/lib/security
  make
}

package () {
  cd "$srcdir/$pkgname-$pkgver"
  make DESTDIR="$pkgdir" install
  install -m 644 -D COPYING "$pkgdir/usr/share/licenses/$pkgname/COPYING"
}
