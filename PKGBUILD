pkgname=classicos-2000-git
pkgver=d463191
pkgrel=1
pkgdesc="Millenium PC Look for GTK2/3"
arch=('any')
url="https://github.com/ClassicOS-Themes/ClassicOS-2000-Theme"
license=('GPL' 'MIT')
makedepends=('meson' 'sassc')
optdepends=(
  'gtk3: required for CSS/GTK3 theme'
  'gtk-engines: required for GTK2 theme'
)
source=("ClassicOS-2000-Theme::git+https://github.com/ClassicOS-Themes/ClassicOS-2000-Theme.git")
md5sums=('SKIP')

pkgver() {
  cd "ClassicOS-2000-Theme"
	echo "$(git rev-parse --short HEAD)"
}

build() {
  arch-meson "ClassicOS-2000-Theme" build
  meson compile -C build
}

package() {
  meson install -C build --destdir "$pkgdir"

}
