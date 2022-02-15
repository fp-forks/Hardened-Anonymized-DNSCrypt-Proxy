# Maintainer: BL4CKH47H4CK3R <bl4ckh47h4ck3r@archlinux.org>

pkgname=Hardened-Anonymized-DNSCrypt-Proxy
_pkgname=dnscrypt-proxy
pkgver=2.1.1
pkgrel=1
pkgdesc="Wipe Snoopers Out Of Your Networks"
arch=('any')
url="https://github.com/BL4CKH47H4CK3R/Hardened-Anonymized-DNSCrypt-Proxy"
license=('ISC')
depends=('glibc')
makedepends=('git' 'go')
install="${_pkgname}.install"
source=("git+https://github.com/dnscrypt/${_pkgname}#tag=${pkgver}"
        "${_pkgname}.toml"
        "${_pkgname}.service"
        "${_pkgname}.socket")
sha512sums=('SKIP'
            'a87b122ce15c5c786350e74a4ed43fa1eb25b56d3b5ef60848db8d601a0d1a67da4bfe240b8dca02a688d211b74d49a1db35417454f620e16af71e8165f20cdc'
            '49a9e7ab55e3d5a61017ab2d3a9d8baa503a7737b3b23402d1685f3fda2b59c5e08810bb18be30b2f099da7fa8686ce1bb4052cdd705e9397fd40b663bef3f21'
            '17175397a5a35692f300d6caff84eb236b21a6e41a870bca966c5576f0db2bc7556d6a214d2f7e985fe9e0be99ef6e0bb067f29cebd41c2ea374540d6f4bd990')

build() {
  cd "${_pkgname}/${_pkgname}"
  export CGO_CPPFLAGS="${CPPFLAGS}"
  export CGO_CFLAGS="${CFLAGS}"
  export CGO_CXXFLAGS="${CXXFLAGS}"
  export CGO_LDFLAGS="${LDFLAGS}"
  export GOFLAGS="-buildmode=pie -trimpath -ldflags=-linkmode=external -mod=readonly -modcacherw"
  go build
}

package() {
  cd "$srcdir/${_pkgname}/${_pkgname}"
  install -Dm755 "dnscrypt-proxy" "$pkgdir/usr/bin/dnscrypt-proxy"
  install -Dm644 "../../dnscrypt-proxy.toml" "$pkgdir/etc/dnscrypt-proxy/dnscrypt-proxy.toml"
  install -Dm644 "../../dnscrypt-proxy.socket" "$pkgdir/usr/lib/systemd/system/dnscrypt-proxy.socket"
  install -Dm644 "../../dnscrypt-proxy.service" "$pkgdir/usr/lib/systemd/system/dnscrypt-proxy.service"
  install -Dm644 "../LICENSE" "$pkgdir/usr/share/licenses/${_pkgname}/LICENSE"
}
# vim:set ts=2 sw=2 et:
