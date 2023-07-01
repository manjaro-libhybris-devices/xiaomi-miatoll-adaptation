# Maintainer: Bardia Moshiri <fakeshell@bardia.tech>

pkgname=xiaomi-miatoll-adaptation
provides=(halium10-post-install)
conflicts=(halium10-post-install)
pkgver=1$(date +%y%m%d)
pkgrel=1
pkgdesc="Manjaro libhybris adaptation for xiaomi miatoll"
arch=('any')
url="https://github.com/manjaro-libhybris-devices/xiaomi-miatoll-adaptation"
license=('GPL')
depends=('gzip' 'glibc-locales' 'wget' 'systemd')
makedepends=('git')
source=("xiaomi-miatoll-adaptation::git+https://github.com/manjaro-libhybris-devices/xiaomi-miatoll-adaptation.git")
install=$pkgname.install
md5sums=('SKIP')

package() {
    mv "${srcdir}/xiaomi-miatoll-adaptation/xiaomi-miatoll-adaptation.sh" "${srcdir}/xiaomi-miatoll-adaptation/xiaomi-miatoll-adaptation"

    mkdir -p "${pkgdir}/usr/bin/"
    install -Dm755 "${srcdir}/xiaomi-miatoll-adaptation/xiaomi-miatoll-adaptation" -t "${pkgdir}/usr/bin/"
    install -Dm755 "${srcdir}/xiaomi-miatoll-adaptation/miatoll-postboot.sh" -t "${pkgdir}/usr/bin/"

    mkdir -p "${pkgdir}/usr/lib/systemd/system/"
    install -Dm644 "${srcdir}/xiaomi-miatoll-adaptation/xiaomi-miatoll-adaptation.service" -t "${pkgdir}/usr/lib/systemd/system/"

    mkdir -p "${pkgdir}/usr/lib/sysusers.d/"
    install -Dm644 "${srcdir}/xiaomi-miatoll-adaptation/android.conf" -t "${pkgdir}/usr/lib/sysusers.d/"

    cp -r "${srcdir}/xiaomi-miatoll-adaptation/droid-vendor-overlay" -t "${pkgdir}/usr/lib/"

    mkdir -p ${pkgdir}/etc/phosh/
    install -Dm644 "${srcdir}/xiaomi-miatoll-adaptation/phoc.ini" -t "${pkgdir}/etc/phosh/"

    mkdir -p "${pkgdir}/etc/udev/rules.d/"
    install -Dm644 "${srcdir}/xiaomi-miatoll-adaptation/70-android.rules" -t "${pkgdir}/etc/udev/rules.d/"

    mkdir -p "${pkgdir}/boot/"
    install -Dm644 "${srcdir}/xiaomi-miatoll-adaptation/boot.img" -t "${pkgdir}/boot/"
    install -Dm644 "${srcdir}/xiaomi-miatoll-adaptation/dtbo.img" -t "${pkgdir}/boot/"
    install -Dm644 "${srcdir}/xiaomi-miatoll-adaptation/vbmeta.img" -t "${pkgdir}/boot/"

    mkdir -p "${pkgdir}/usr/lib/systemd/system/"
    install -Dm644 "${srcdir}/xiaomi-miatoll-adaptation/enable-ipa.service" "${pkgdir}/usr/lib/systemd/system/"
    install -Dm644 "${srcdir}/xiaomi-miatoll-adaptation/miatoll-postboot.service" "${pkgdir}/usr/lib/systemd/system/"
}
