# Contributor: Brad Arrington
pkgname=bouncycastle-sharp
pkgver=20120808
pkgrel=4
pkgdesc="A C Sharp Library for Crypto"
url="http://www.bouncycastle.org/csharp/index.html"
option=('')
license="MIT"
arch=('x86_64')
depends=('mono' 'nant')
_cvsroot=":pserver:anonymous@cvs.bouncycastle.org:/home/users/bouncy/cvsroot"
_cvsmod="csharp"

build() {
  cd "$srcdir"
  msg "Connecting to cvs.bouncycastle.org CVS server...."
  if [ -d $_cvsmod/CVS ]; then
    cd $_cvsmod
    cvs -z3 update -d
  else
    cvs -z3 -d $_cvsroot co -D $pkgver -f $_cvsmod
    cd $_cvsmod
  fi

  msg "CVS checkout done or server timeout"
  msg "Starting make..."

  cd $startdir/src/csharp/crypto
  nant
  mkdir -p $pkgdir/usr/lib/mono/gac/bouncycastle-sharp/test/lib
  mkdir -p $pkgdir/usr/lib/mono/bouncycastle-sharp/test/lib
  install -m644 $srcdir/csharp/crypto/api/bin/release/BouncyCastle.Crypto.dll $pkgdir/usr/lib/mono/gac/bouncycastle-sharp/
  install -m644 $srcdir/csharp/crypto/api/bin/release/BouncyCastle.Crypto.dll $pkgdir/usr/lib/mono/bouncycastle-sharp/

  install -m644 $srcdir/csharp/crypto/test/lib/nunit.core.dll $pkgdir/usr/lib/mono/gac/bouncycastle-sharp/test/lib
  install -m644 $srcdir/csharp/crypto/test/lib/nunit.core.dll $pkgdir/usr/lib/mono/bouncycastle-sharp/test/lib

  install -m644 $srcdir/csharp/crypto/test/lib/nunit.core.interfaces.dll $pkgdir/usr/lib/mono/gac/bouncycastle-sharp/test/lib
  install -m644 $srcdir/csharp/crypto/test/lib/nunit.core.interfaces.dll $pkgdir/usr/lib/mono/bouncycastle-sharp/test/lib

  install -m644 $srcdir/csharp/crypto/test/lib/nunit.framework.dll $pkgdir/usr/lib/mono/gac/bouncycastle-sharp/test/lib
  install -m644 $srcdir/csharp/crypto/test/lib/nunit.framework.dll $pkgdir/usr/lib/mono/bouncycastle-sharp/test/lib
}
