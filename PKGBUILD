# Script generated with Bloom
pkgdesc="ROS - A friendly library for parsing HTTP request arguments, with built-in support for popular web frameworks, including Flask, Django, Bottle, Tornado, Pyramid, webapp2, Falcon, and aiohttp."


pkgname='ros-kinetic-webargs'
pkgver='1.3.4_0'
pkgrel=1
arch=('any')
license=('BSD'
)

makedepends=('python-tornado>=4.0'
'python-werkzeug>=0.9.4'
'python2-flask>=0.10.1'
'python2-mock'
'python2-pytest'
'python2-webtest>=2.0.18'
'ros-kinetic-catkin-pip>=0.2.0'
'ros-kinetic-catkin>=0.6.18'
'ros-kinetic-marshmallow>=2.0.0'
)

depends=('ros-kinetic-marshmallow>=2.0.0'
)

conflicts=()
replaces=()

_dir=webargs
source=()
md5sums=()

prepare() {
    cp -R $startdir/webargs $srcdir/webargs
}

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/kinetic/setup.bash ] && source /opt/ros/kinetic/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/kinetic \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DPYTHON_BASENAME=-python2.7 \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}

