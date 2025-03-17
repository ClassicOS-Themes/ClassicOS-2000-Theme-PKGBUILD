# Maintainer: tomatoes <tomatoes@tin-can.mozmail.com> 
_pkgbase=classicos-2000
_pkgbv=1.2
pkgname=$_pkgbase-git
pkgver=1.2.r0.0
pkgrel=2
pkgdesc="Millenium PC Look for GTK2/3"
arch=('any')
url="https://github.com/ClassicOS-Themes/ClassicOS-2000-Theme"
license=('GPL' 'MIT')
makedepends=('meson' 'sassc')
optdepends=(
  'gtk3: required for CSS/GTK3 theme'
)
source=("ClassicOS-2000-Theme::git+https://github.com/ClassicOS-Themes/ClassicOS-2000-Theme.git")
md5sums=('SKIP')

pkgver() {
  cd "ClassicOS-2000-Theme"
  printf "$_pkgbv.r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
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
    meson setup --prefix /usr --buildtype plain --auto-features enabled --wipe -Dcolorscheme="$lighttheme" -Ddark_colorscheme="$darktheme" -Dtheme_name="ClassicOS$name" "ClassicOS-2000-Theme" "build$i"
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
