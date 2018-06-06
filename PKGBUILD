
# Maintainer:

pkgname=python-cupy-cudnn-git
_pkgname=cupy
pkgver=v5.0.0b1.r128.g0a87a602e
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
  export CC=gcc-7
  export CXX=g++-7
  export CFLAGS='-march=skylake -mtune=native -O3 -pipe -fstack-protector'
  # export CFLAGS='-march=skylake -mtune=native -O3 -pipe -fstack-protector --param=ssp-buffer-size=4a -I/opt/cuda/include'
  python setup.py build
}

package() {
  cd $_pkgname

  export CUDA_PATH=/opt/cuda
  export CC=gcc-7
  export CXX=g++-7
  python setup.py install --root=${pkgdir} --optimize=1

  install -D -m644 LICENSE ${pkgdir}/usr/share/licenses/python-$_pkgname
}
