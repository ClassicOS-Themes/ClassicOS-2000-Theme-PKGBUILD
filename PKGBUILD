pkgname=classicos-2000-git
pkgver=1.0_git_cdf4c9e
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
	echo "1.0_git_$(git rev-parse --short HEAD)"
}

build() {
  source './ClassicOS-2000-Theme/schemes'
  i=0
  while [ "$i" -lt "${#schemes[@]}" ]; do
    lighttheme="${schemes[i]}"
    i=$((i+1))
    darktheme="${schemes[i]}"
    i=$((i+1))
    name="${schemes[i]}"
    i=$((i+1))
    arch-meson -Dcolorscheme="$lighttheme" -Ddark_colorscheme="$darktheme" -Dtheme_name="ClassicOS$name" "ClassicOS-2000-Theme" "build$i"
    meson compile -C "build$i"
  done
}
package() {

  source './ClassicOS-2000-Theme/schemes'
  i=0
  while [ "$i" -lt "${#schemes[@]}" ]; do
    lighttheme="${schemes[i]}"
    i=$((i+1))
    darktheme="${schemes[i]}"
    i=$((i+1))
    name="${schemes[i]}"
    i=$((i+1))
    meson install -C "build$i" --destdir "$pkgdir"
  done
}
