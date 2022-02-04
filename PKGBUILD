# Maintainer: BL4CKH47H4CK3R <bl4ckh47h4ck3r@archlinux.org>

pkgname=Hardened-Anonymized-DNSCrypt-Proxy
_pkgname=dnscrypt-proxy
pkgver=2.1.1
pkgrel=1
pkgdesc="Wipe Snoopers Out Of Your Networks"
arch=('any')
url="https://github.com/DNSCrypt/dnscrypt-proxy"
license=('ISC')
depends=('glibc')
makedepends=('git' 'go')
install="${_pkgname}.install"
source=("git+https://github.com/dnscrypt/${_pkgname}#tag=${pkgver}"
        "${_pkgname}.toml"
        "${_pkgname}.service"
        "${_pkgname}.socket")
sha512sums=('SKIP'
            '2edcc7b2e201a3a1785bbc1e28fe676b4840fdbb71490a47f79750bcfcc0a02cf13e6a6b713b111b15a585e12babea08a06ca6c64dbab47b4672060fc922faac'
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
