# Maintainer: Aris Synodinos <arissynod-gmail-com>
pkgname='python2-rosinstall-git'
pkgdesc='Tool to download/boostrap the ROS stack'
url='http://wiki.ros.org/rosinstall'
pkgver='0.0.1'
pkgrel='2'
arch=('i686' 'x86_64')
license=('BSD')
depends=('python2' 'cmake' 'wget' 'vcstools-git' 'git' 'python2-distribute' 'python2-yaml' 'python2-dateutil')
provides=('python2-rosinstall')
conflicts=('python2-rosinstall')
md5sums=() #generate with 'makepkg -g'

_gitroot=("https://github.com/vcstools/rosinstall.git")
_gitname=("rosinstall")

build() {
  cd ${srcdir}
  msg "Connecting to Git server..."

  # Git checkout
  if [ -d ${srcdir}/${_gitname} ] ; then
    msg "Git checkout:  Updating existing tree"
    cd ${_gitname} && git pull origin
    msg "Git checkout:  Tree has been updated"
  else
    msg "Git checkout:  Retrieving sources"
    git clone ${_gitroot}
  fi
  msg "Checkout completed"
}

#build() {
#  cd "${srcdir}/rosinstall-${pkgver}"
#  sed -i 's/env python /env python2 /' src/rosinstall/setupfiles.py
#}

package() {
  msg "Starting Build..."
  cd ${srcdir}/${_gitname}
  python2 setup.py install --root=$pkgdir --optimize=1
}
