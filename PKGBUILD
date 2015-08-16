# Maintainer: Edoardo Maria Elidoro <edoardo.elidoro@gmail.com>
# Contributor: Jib <jbc.as (AT) free.fr>
# Last update: 01/27/11

pkgname=gtk-theme-stepintofreedom
_pkgname=step-into-freedom-theme
pkgver=1.7.1
pkgrel=2
pkgdesc="Step-into-freedom theme for Xfce and Mate."
arch=(any)
license=('GPL')
makedepends=('imagemagick')
optdepends=('slim-theme-step-into-freedom: matching theme for slim login manager')
source=(https://launchpad.net/~bisigi/+archive/ppa/+files/step-into-freedom-theme_1.7.1.maverick.ppa2+nmu1.tar.gz
        arch-icon-128.png
        step-into.patch)
url="http://www.bisigi-project.org"
md5sums=('0776a65a1b21f77c20ddd3761894d2d1'
         '5e7318b77e6ddb74b2fdf72788d7c5cc'
         '1866874e8dc5358896a7fcaf3f063016')

package() {
   cd ${srcdir}/${_pkgname}
   # install dirs 
   install -d ${pkgdir}/usr/share/{themes,icons,pixmaps/backgrounds/gnome/other,gnome-background-properties,emerald/themes,doc/bisigi/step-into-freedom}
   tar -xzf Gtk/step-into-freedom.tar.gz -C Gtk/
   #Icons theme
   echo "Unpacking icons..."
   tar -xjf Icons/step-into-freedom.tar.bz2 -C Icons/
   local _w=""
   for _w in {16x16,22x22,24x24,32x32}; do
      convert -resize $_w ${startdir}/arch-icon-128.png Icons/step-into-freedom/$_w/places/distributor-logo.png
      convert -resize $_w ${startdir}/arch-icon-128.png Icons/step-into-freedom/$_w/places/gnome-main-menu.png
      convert -resize $_w ${startdir}/arch-icon-128.png Icons/step-into-freedom/$_w/places/start-here.png
   done
   install -D -m644 ${startdir}/arch-icon-128.png Icons/step-into-freedom/scalable/places/distributor-logo.png
   install -D -m644 ${startdir}/arch-icon-128.png Icons/step-into-freedom/scalable/places/gnome-main-menu.png
   install -D -m644 ${startdir}/arch-icon-128.png Icons/step-into-freedom/scalable/places/start-here.png
   #Emerald theme
   mkdir Emerald/step-into-freedom
   tar -xzf Emerald/step-into-freedom.emerald -C Emerald/step-into-freedom
   # install files
   patch -Np0 <${srcdir}/step-into.patch
   cp -R Gtk/step-into-freedom/ ${pkgdir}/usr/share/themes/
   cp -R Icons/step-into-freedom/ ${pkgdir}/usr/share/icons
   install -D -m644 Wallpaper/gnome-step-into-freedom-16_10.jpg Wallpaper/gnome-step-into-freedom.jpg Wallpaper/gnome-step-into-freedom1-16_10.jpg Wallpaper/gnome-step-into-freedom1.jpg ${pkgdir}/usr/share/pixmaps/backgrounds/gnome/other
   install -D -m644 Wallpaper/step-into-freedom-wallpaper.xml ${pkgdir}/usr/share/gnome-background-properties
   cp -R Emerald/step-into-freedom ${pkgdir}/usr/share/emerald/themes/
   install -D -m644 credits.txt ${pkgdir}/usr/share/doc/bisigi/step-into-freedom/
}
