# Maintainer: BL4CKH47H4CK3R <bl4ckh47h4ck3r@archlinux.org>

pkgname=Hardened-Anonymized-DNSCrypt-Proxy
_pkgname=dnscrypt-proxy
pkgver=2.1.1
pkgrel=11
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
  $_pkgname.socket
  $_pkgname.service
)
sha512sums=('SKIP'
            'b17704410ddbc7ad1cc069097bdbdaeae9bddb6c05d18379bf5da41a9dc1f21c1bc1b720272547f472610efaa2a2614adbc82e6a32c2eb8a6c2bdbacee7e16e3'
            '17175397a5a35692f300d6caff84eb236b21a6e41a870bca966c5576f0db2bc7556d6a214d2f7e985fe9e0be99ef6e0bb067f29cebd41c2ea374540d6f4bd990'
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
  install -Dm644 "../LICENSE" "$pkgdir/usr/share/licenses/$_pkgname/LICENSE"
  install -Dm644 "../../dnscrypt-proxy.toml" "$pkgdir/etc/dnscrypt-proxy/dnscrypt-proxy.toml"
  install -Dm644 "../../dnscrypt-proxy.socket" "$pkgdir/usr/lib/systemd/system/dnscrypt-proxy.socket"
  install -Dm644 "../../dnscrypt-proxy.service" "$pkgdir/usr/lib/systemd/system/dnscrypt-proxy.service"
}
# vim:set ts=2 sw=2 et:
