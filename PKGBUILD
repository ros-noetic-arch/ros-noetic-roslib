# Script generated with import_catkin_packages.py.
# For more information: https://github.com/bchretien/arch-ros-stacks.
pkgdesc="ROS - Base dependencies and support libraries for ROS."
url='https://wiki.ros.org/roslib'

pkgname='ros-noetic-roslib'
pkgver='1.15.8'
arch=('i686' 'x86_64' 'aarch64' 'armv7h' 'armv6h')
pkgrel=2
license=('BSD')

ros_makedepends=(
	ros-noetic-rospack
	ros-noetic-catkin
)

makedepends=(
	'cmake'
	'ros-build-tools'
	${ros_makedepends[@]}
	boost
)

ros_depends=(
	ros-noetic-ros-environment
	ros-noetic-rospack
	ros-noetic-catkin
)

depends=(
	${ros_depends[@]}
	python-rospkg
)

_commit="136e18e9dfda748a87b5ed197a36587f612c6e46"
_dir="ros-${_commit}/core/roslib"
source=("${pkgname}-${pkgver}.tar.gz"::"https://github.com/ros/ros/archive/${_commit}.tar.gz")
sha256sums=('1a5214cb8453388a8017ba2cc1eec659a29f61c854c35aa75923cd466a12222d')

build() {
	# Use ROS environment variables.
	source /usr/share/ros-build-tools/clear-ros-env.sh
	[ -f /opt/ros/noetic/setup.bash ] && source /opt/ros/noetic/setup.bash

	# Create the build directory.
	[ -d ${srcdir}/build ] || mkdir ${srcdir}/build
	cd ${srcdir}/build

	# Build the project.
	cmake ${srcdir}/${_dir} \
		-DCATKIN_BUILD_BINARY_PACKAGE=ON \
		-DCMAKE_INSTALL_PREFIX=/opt/ros/noetic \
		-DPYTHON_EXECUTABLE=/usr/bin/python \
		-DSETUPTOOLS_DEB_LAYOUT=OFF
	make
}

package() {
	cd "${srcdir}/build"
	make DESTDIR="${pkgdir}/" install
}
