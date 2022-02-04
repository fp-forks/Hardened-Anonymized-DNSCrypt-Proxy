# Maintainer: BL4CKH47H4CK3R <bl4ckh47h4ck3r@archlinux.org>

pkgname=Hardened-Anonymized-DNSCrypt-Proxy
_pkgname=dnscrypt-proxy
pkgver=2.1.1
pkgrel=1
pkgdesc="A flexible DNS proxy, with support for encrypted DNS protocols"
arch=('x86_64')
url="https://github.com/DNSCrypt/dnscrypt-proxy"
license=('ISC')
source=("${_pkgname}.sh"
		"${_pkgname}.toml"
        "${_pkgname}.socket"
		"${_pkgname}.service")
sha512sums=('0c1fa82b0695a7fef6fc5e14316b366e85994b8850311ac79106f1582b14e24f0cf6397eb9b2354fa6d7e08b786aa06aa4de9dab2e4ed872e7d2f96f49c56467'
            '2edcc7b2e201a3a1785bbc1e28fe676b4840fdbb71490a47f79750bcfcc0a02cf13e6a6b713b111b15a585e12babea08a06ca6c64dbab47b4672060fc922faac'
            '17175397a5a35692f300d6caff84eb236b21a6e41a870bca966c5576f0db2bc7556d6a214d2f7e985fe9e0be99ef6e0bb067f29cebd41c2ea374540d6f4bd990'
            '49a9e7ab55e3d5a61017ab2d3a9d8baa503a7737b3b23402d1685f3fda2b59c5e08810bb18be30b2f099da7fa8686ce1bb4052cdd705e9397fd40b663bef3f21')
package() {
  install -Dm755 "${_pkgname}.sh" "$pkgdir/usr/bin/${pkgname}"
  install -Dm644 "${_pkgname}.toml" "$pkgdir/etc/{_pkgname}/${_pkgname}.toml"
  install -Dm644 "${_pkgname}.socket" "$pkgdir/usr/lib/systemd/system/${_pkgname}.socket"
  install -Dm644 "${_pkgname}.service" "$pkgdir/usr/lib/systemd/system/${_pkgname}.service"
}
