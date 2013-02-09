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


Fedora/CentOS/RedHat
____________________

The RPM specification file is reproduced here, in the fedora/ directory,
for convenient reason. However, the master is hosted by Fedora:
http://pkgs.fedoraproject.org/cgit/soci.git/tree/soci.spec

If you want to build the package on Fedora/CentOS/RedHat:
```
shell
sudo yum -y install fedora-packager
sudo yum -y groupinstall development
rpmdev-setuptree
```
Change the ```%packager``` variable in the ```~/.rpmmacros``` configuration file.
```
shell
SOCI_VER=3.2.0
cd ~/rpmbuild/SPECS
wget http://pkgs.fedoraproject.org/cgit/soci.git/tree/soci.spec
pushd ~/rpmbuild/SOURCES
wget http://downloads.sourceforge.net/soci/soci-${SOCI_VER}.zip
popd
rpmbuild -bs soci.spec
rpmbuild -ba soci.spec
```

Note:
-----
On CentOS, you have to enable the EPEL repository, with something like:
```
shell
rpm --import http://dl.fedoraproject.org/pub/epel/RPM-GPG-KEY-EPEL-6
rpm -Uvh http://dl.fedoraproject.org/pub/epel/6/x86_64/epel-release-6-8.noarch.rpm
```
See the [Fedora Wiki](http://fedoraproject.org/wiki/EPEL/FAQ#How_can_I_install_the_packages_from_the_EPEL_software_repository.3F)
for more details.



