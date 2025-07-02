# Maintainer: littleblack111 <littleblack11111@gmail.com>
pkgname=video-guard
pkgver=r11.06bcc88
pkgrel=1
pkgdesc="Helper that guards and requests user confirmation for /dev/video* access"
arch=('any')
url="https://github.com/littleblack111/video-guard"
license=('GPL-3.0-or-later')
depends=('inotify-tools' 'lsof' 'bash' 'systemd' 'libnotify' 'coreutils' 'gawk')
optdepends=('hyprland-dialog: to use default dialog')
makedepends=('git')
source=("git+https://github.com/littleblack111/video-guard.git")
sha256sums=('SKIP')

pkgver() {
	cd "$pkgname"
	printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short=7 HEAD)"
}

package() {
	cd "$pkgname"
	install -Dm755 videoGuard.sh "$pkgdir/usr/bin/videoGuard"
	install -Dm644 video-guard.service "$pkgdir/etc/systemd/system/video-guard.service"
}

post_install() {
	echo "To enable the service, run systemctl --user enable --now shut-userspace.service"
	echo "Important: for this to work, you need special permissions for lsof(/sys/kernel/debug/tracing)"
	echo "You can set it up by running: sudo setcap cap_sys_admin+ep /usr/bin/lsof"
}
