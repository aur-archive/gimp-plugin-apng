# Contributor: maz-1 <loveayawaka_at_gmail_dot_com>
# Contributor:
# Maintainer: Pablo Lezaeta <prflr88@gmail.com>

pkgname=gimp-plugin-apng
_pkgname=gimp-apng
pkgver=0.1.0
pkgrel=3
pkgdesc="A GIMP plugin to support animated PNG (APNG)."
url="http://sourceforge.net/projects/gimp-apng/"
depends=("gimp>=2.3.0" "libpng")
source=("http://tcpdiag.dl.sourceforge.net/project/${_pkgname}/${_pkgname}-dev/${pkgver}/${_pkgname}-${pkgver}.tar.bz2")
arch=("i686" "x86_64")
license=("GPL")
options=(makeflags)

LDFLAGS=-Wl,-O1,--sort-common,-lm,-z,relro

build() {
  cd "${srcdir}/${_pkgname}-${pkgver}"
  ./configure --prefix=/usr --bindir=/usr/bin --sbindir=/usr/bin \
  --libdir=/usr/lib --libexecdir=/usr/lib/gimp-2.0

  make prefix=/usr bindir=/usr/bin sbindir=/usr/bin libdir=/usr/lib \
  libexecdir=/usr/lib/gimp-2.0 DESTDIR="${pkgdir}"
}

package() {
  cd "${srcdir}/${_pkgname}-${pkgver}"

  make prefix=/usr bindir=/usr/bin sbindir=/usr/bin libdir=/usr/lib \
  libexecdir=/usr/lib/gimp-2.0 DESTDIR="${pkgdir}" install

#Stupid Makefile, not install thisng correctly, help?
  mkdir -p "${pkgdir}/usr/lib/gimp/2.0/plug-ins/"
  mv "${pkgdir}/usr/bin/file-apng" \
  "${pkgdir}/usr/lib/gimp/2.0/plug-ins/"
  rmdir "${pkgdir}/usr/bin/"

  mkdir -p "${pkgdir}/usr/share/gimp/2.0/ui/"
  mv "${pkgdir}/usr/share/gimp-apng/ui/plug-ins/plug-in-file-apng.ui" \
  "${pkgdir}/usr/share/gimp/2.0/ui"
  rm -r "${pkgdir}/usr/share/gimp-apng/ui/"
}

md5sums=("af83f8dfc6cfedc9ce3e898d1eef1768")
