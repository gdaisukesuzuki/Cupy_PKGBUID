
# Maintainer: 

pkgname=python-cupy-cudnn-git
_pkgname=cupy
pkgver=v4.0.0b3.r4.g914494815
pkgrel=1
pkgdesc='NumPy-like API accelerated with CUDA'
arch=('any')
url='https://github.com/cupy/cupy'
license=('custom')
depends=('python-numpy' 'python-six' 'cuda' 'cudnn' 'python-fastrlock')
makedepends=('git' 'python-setuptools')
conflicts=('python-cupy')
provides=('python-cupy')
source=('git://github.com/cupy/cupy.git')
md5sums=('SKIP' )

pkgver() {
  cd $_pkgname
  git describe --long --tags | sed 's/\([^-]*-g\)/r\1/;s/-/./g'
}


build() {
  cd $_pkgname
  export CUDA_PATH=/opt/cuda
#  export CC=gcc-6
#  export CXX=g++-6
  sudo python setup.py build
}

package() {
  cd $_pkgname

  export CUDA_PATH=/opt/cuda
#  export CC=gcc-6
#  export CXX=g++-6
  sudo python setup.py install --root=${pkgdir} --optimize=1

  sudo install -D -m644 LICENSE ${pkgdir}/usr/share/licenses/python-$_pkgname
}
