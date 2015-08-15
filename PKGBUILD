# Maintainer:  Felix Berkenkamp      <felix1012 at gmx.de>

pkgname=creeper-world
pkgver=0632
pkgrel=1
pkgdesc="Imagine an enemy that is everywhere and moves like a giant, organic mass across the map."
arch=('i686' 'x86_64')
url="http://knucklecracker.com/creeperworld/cw.php"
license=('custom')
depends=('adobe-air-sdk')
makedepends=('unzip')
source=(http://knucklecracker.com/creeperworld/dd_webb/CreeperWorld-${pkgver}.exe
	    creeperworld.desktop)
noextract=(CreeperWorld-${pkgver}.exe)

package() {
  cd "${srcdir}"

  unzip CreeperWorld-${pkgver}.exe
  unzip CreeperWorld-${pkgver}.air

  mkdir -p "${pkgdir}"/usr/share/{cw1,applications}
  mkdir -p "${pkgdir}/usr/bin"

  cp -r icons  Main.swf META-INF  mimetype "${pkgdir}/usr/share/cw1/"

  cp -p creeperworld.desktop "${pkgdir}/usr/share/applications/"
  cat <<EOF >> "${pkgdir}/usr/bin/cw1"
#!/bin/sh
/opt/adobe-air-sdk/bin/adl -nodebug /usr/share/cw1/META-INF/AIR/application.xml /usr/share/cw1 &
EOF

  chmod +x "${pkgdir}/usr/bin/cw1"
}

md5sums=('ac53814d4a0de51d8d5e095695e76f64'
         '658a07246f96f018e67fb1e74d523353')
