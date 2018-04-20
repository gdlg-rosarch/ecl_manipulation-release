# Script generated with Bloom
pkgdesc="ROS - Deploys various manipulation algorithms, currently just feedforward filters (interpolations)."
url='http://wiki.ros.org/ecl_manipulators'

pkgname='ros-kinetic-ecl-manipulators'
pkgver='0.60.1_2'
pkgrel=1
arch=('any')
license=('BSD'
)

makedepends=('ros-kinetic-catkin'
'ros-kinetic-ecl-build'
'ros-kinetic-ecl-exceptions'
'ros-kinetic-ecl-formatters'
'ros-kinetic-ecl-geometry'
'ros-kinetic-ecl-license'
)

depends=('ros-kinetic-ecl-build'
'ros-kinetic-ecl-exceptions'
'ros-kinetic-ecl-formatters'
'ros-kinetic-ecl-geometry'
'ros-kinetic-ecl-license'
)

conflicts=()
replaces=()

_dir=ecl_manipulators
source=()
md5sums=()

prepare() {
    cp -R $startdir/ecl_manipulators $srcdir/ecl_manipulators
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

