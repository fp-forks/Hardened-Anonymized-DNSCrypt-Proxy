# Maintainer: BL4CKH47H4CK3R <bl4ckh47h4ck3r@archlinux.org>

pkgname=Hardened-Anonymized-DNSCrypt-Proxy
_pkgname=dnscrypt-proxy
pkgver=2.1.1
pkgrel=1
pkgdesc="Wipe Snoopers Out Of Your Networks"
arch=(any)
url="https://github.com/BL4CKH47H4CK3R/Hardened-Anonymized-DNSCrypt-Proxy"
license=(ISC)
depends=(glibc)
makedepends=(git go)
install=$_pkgname.install
source=(
  git+https://github.com/dnscrypt/$_pkgname#tag=$pkgver?signed
  $_pkgname.toml
  $_pkgname.service
)
sha512sums=('SKIP'
            '957298bf290d04d1ed137eb648f48fcf52828ee9d1db5274546d1ceb181f3960913249ac4e57378ab73a5edb16f8942b3336f508cbd70b7318836d112edf1583'
            '5589eddf9d5fda86778ebc91c9e20d8acfdcf86bc1f1a5d34279f33c402f32dc73539c0c0ba6bd74b80617e9abcc49c8c68cc06f171f74c66f2ffc92dfeecd75')
validpgpkeys=('54A2B8892CC3D6A597B92B6C210627AABA709FE1') # Frank Denis (Jedi/Sector One) <pgp@pureftpd.org

build() {
  cd $_pkgname/$_pkgname
  export CGO_CPPFLAGS="$CPPFLAGS"
  export CGO_CFLAGS="$CFLAGS"
  export CGO_CXXFLAGS="$CXXFLAGS"
  export CGO_LDFLAGS="$LDFLAGS"
  export GOFLAGS="-buildmode=pie -trimpath -ldflags=-linkmode=external -mod=readonly -modcacherw"
  go build
}

package() {
  cd "$srcdir/$_pkgname/$_pkgname"
  install -Dm755 "dnscrypt-proxy" "$pkgdir/usr/bin/dnscrypt-proxy"
  install -Dm644 "../../dnscrypt-proxy.toml" "$pkgdir/etc/dnscrypt-proxy/dnscrypt-proxy.toml"
  install -Dm644 "../../dnscrypt-proxy.service" "$pkgdir/usr/lib/systemd/system/dnscrypt-proxy.service"
  install -Dm644 "../LICENSE" "$pkgdir/usr/share/licenses/$_pkgname/LICENSE"
}
# vim:set ts=2 sw=2 et:
