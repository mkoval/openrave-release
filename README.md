# OpenRAVE Gitbuildpackage (GBP) Repository #

This repository packages an upstream OpenRAVE source tree into a buildable debian package.

----
**Import new upstream source:**
```bash
$ curl -L https://github.com/personalrobotics/openrave/tarball/master.tar.gz
$ git clone https://github.com/mkoval/openrave-release.git
$ cd openrave-release
$ gbp import-orig --pristine-tar --upstream-branch=upstream --debian-branch=debian/trusty /path/to/master.tar.gz
```

**Build a debian source (`.dsc`) package:**
```bash
$ git clone https://github.com/mkoval/openrave-release.git
$ cd openrave-release
$ gbp buildpackage --git-debian-branch=debian/trusty --pristine-tar -uc -us
```

**Build a debian binary (`.deb`) package:**
