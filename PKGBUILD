# Maintainer: Martynas Mickevičius <self at 2m dot lt>

pkgname=coursier
pkgver=2.1.24
pkgrel=1
pkgdesc="Pure Scala Artifact Fetching"
arch=('any')
url="http://get-coursier.io"
license=('Apache')
depends=('java-runtime-headless>=8' 'bash')

source=("builder-$pkgver::https://github.com/coursier/coursier/releases/download/v${pkgver}/coursier")
sha256sums=('7aa975f12469726d6bb87852107afe0b8d6f3c82b12a49ef43cc6647c4e057ca')
noextract=("builder-$pkgver")

build() {
  cd "${srcdir}"
  mkdir -p cache bin
  export COURSIER_CACHE="${srcdir}/cache"
  sh ./builder-$pkgver bootstrap \
    "io.get-coursier::coursier-cli:${pkgver}" \
    --no-default \
    -r central \
    -r typesafe:ivy-releases \
    -f -o "bin/coursier" \
    --standalone
}

package() {
  install -D -m755 "${srcdir}/bin/coursier" "${pkgdir}/usr/bin/coursier"
}
