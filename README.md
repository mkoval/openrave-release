# OpenRAVE Gitbuildpackage (GBP) Repository #

This repository packages an upstream OpenRAVE source tree into a buildable debian package. All of this documentatoin is written using `trusty` as an example. If you are building this package for a different version of Ubuntu, then you should replace `trusty` with the appropriate codename. You can get the codename of your current distribution by running `lsb_release -sc`.

----
**Initialize cowbuilder:**
```
$ sudo apt-get install cowbuilder
$ DIST=trusty sudo cowbuilder --create --distribution ${DIST} --components "main universe"
```
To update existing:
```
$ sudo cowbuilder --update
```

**Import new upstream source:**
```bash
$ curl -L https://api.github.com/repos/personalrobotics/openrave/tarball/master > master.tar.gz
$ git clone https://github.com/mkoval/openrave-release.git
$ cd openrave-release
$ gbp import-orig --pristine-tar --upstream-branch=upstream --debian-branch=debian/trusty ../master.tar.gz
What is the upstream version? [] <enter version higher than the previous>
```

**Build debian source (`.dsc`) and binary (`.deb`) packages:**
```bash
$ git clone https://github.com/mkoval/openrave-release.git
$ cd openrave-release
$ git checkout debian/trusty
$ gbp dch --release --debian-branch=debian/trusty
$ git commit -m "Updated changelog for version <your version>."
$ gbp buildpackage --git-debian-branch=debian/trusty --git-pbuilder -uc -us
```
