# Maintainer: Martynas Mickevičius <self at 2m dot lt>
_version=2.1.10

pkgname=coursier
pkgver="${_version//-/_}"
pkgrel=1
pkgdesc="Pure Scala Artifact Fetching"
arch=('any')
url="http://get-coursier.io"
license=('Apache')
depends=('java-runtime-headless>=8' 'bash')

source=("builder-$pkgver::https://github.com/coursier/coursier/releases/download/v${_version}/coursier")
sha256sums=('7e26709830ee69a7c16d841d3b13e94eb95e30b3926a40ad7a2ce92b07064ad9')
noextract=("builder-$pkgver")

build() {
  cd "${srcdir}"
  mkdir -p cache bin
  export COURSIER_CACHE="${srcdir}/cache"
  sh ./builder-$pkgver bootstrap \
    "io.get-coursier::coursier-cli:${_version}" \
    --no-default \
    -r central \
    -r typesafe:ivy-releases \
    -f -o "bin/coursier" \
    --standalone
}

package() {
  install -D -m755 "${srcdir}/bin/coursier" "${pkgdir}/usr/bin/coursier"
}
