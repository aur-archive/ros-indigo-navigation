# Script generated with import_catkin_packages.py
# For more information: https://github.com/bchretien/arch-ros-stacks
pkgdesc="ROS - A 2D navigation stack that takes in information from odometry, sensor streams, and a goal pose and outputs safe velocity commands that are sent to a mobile base."
url='http://wiki.ros.org/navigation'

pkgname='ros-indigo-navigation'
pkgver='1.11.11'
_pkgver_patch=0
arch=('any')
pkgrel=1
license=('BSD,LGPL,LGPL (amcl)')

ros_makedepends=(ros-indigo-catkin)
makedepends=('cmake' 'git' 'ros-build-tools'
  ${ros_makedepends[@]})

ros_depends=(ros-indigo-nav-core
  ros-indigo-carrot-planner
  ros-indigo-fake-localization
  ros-indigo-clear-costmap-recovery
  ros-indigo-base-local-planner
  ros-indigo-amcl
  ros-indigo-navfn
  ros-indigo-costmap-2d
  ros-indigo-map-server
  ros-indigo-voxel-grid
  ros-indigo-dwa-local-planner
  ros-indigo-robot-pose-ekf
  ros-indigo-move-base-msgs
  ros-indigo-move-slow-and-clear
  ros-indigo-rotate-recovery
  ros-indigo-move-base)
depends=(${ros_depends[@]})

_tag=release/indigo/navigation/${pkgver}-${_pkgver_patch}
_dir=navigation
source=("${_dir}"::"git+https://github.com/ros-gbp/navigation-release.git"#tag=${_tag})
md5sums=('SKIP')

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/indigo/setup.bash ] && source /opt/ros/indigo/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/indigo \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}
