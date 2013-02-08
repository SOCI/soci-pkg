soci-pkg
========

SOCI packaging configurations


Debian
______

Just copy the debian/ directory to your soci sources directory and run dpkg-buildpackage -rfakeroot

debian/control is generated from debian/control.in manually, by calling `DEB_AUTO_UPDATE_DEBIAN_CONTROL=yes fakeroot debian/rules clean`.

Packages, required for build:

* patchutils
* cdbs
* debhelper
* dh-buildinfo
* devscripts
* cmake
* libboost-dev
* libmysql15-dev
* libpq-dev
* libsqlite3-dev
* unixodbc-dev
