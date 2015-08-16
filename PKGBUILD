# Maintainer: Ralf Warmuth <schumbi@gmail.com> 
# Contributor: Adria Arrufat <swiftscythe@gmail.com>
pkgname=imapquickcheck
pkgver=1.3
pkgrel=1
pkgdesc="A lightweight systray docking app that checks your IMAP mailboxes for unread messages."
arch=('i686' 'x86_64')
url="http://kde-apps.org/content/show.php/ImapQuickCheck?content=110823"
license=("GPL")
depends=('qt4')
source=("http://kde-apps.org/CONTENT/content-files/110823-$pkgname-$pkgver.tar.bz2"
        "imap_check_sql_final.py.patch")
md5sums=('ba022f1af33ce4caaaefe57cd2b9613a' 'ab15b6273ce32782ad9be20df8ccd61e')
install=$pkgname.install

build() {
  cd ${pkgname}-${pkgver}
  patch -uN python/imap_check_sql_final.py ../imap_check_sql_final.py.patch || return 1
  qmake-qt4 
  make || return 1
}

package() {
  cd ${pkgname}-${pkgver}
  install -D -m755 $pkgname $pkgdir/usr/bin/$pkgname || return 1
  install -Dm644 $pkgname.desktop $pkgdir/usr/share/applications/$pkgname.desktop
}
