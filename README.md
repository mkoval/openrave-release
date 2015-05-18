# OpenRAVE Gitbuildpackage (GBP) Repository #

This repository packages an upstream OpenRAVE source tree into a buildable debian package.

----
**Import new upstream source:**
```bash
$ curl -L https://api.github.com/repos/personalrobotics/openrave/tarball/master > master.tar.gz
$ git clone https://github.com/mkoval/openrave-release.git
$ cd openrave-release
$ gbp import-orig --pristine-tar --upstream-branch=upstream --debian-branch=debian/trusty ../master.tar.gz
What is the upstream version? [] <enter some version higher than the previous>
```

**Build a debian source (`.dsc`) package:**
```bash
$ git clone https://github.com/mkoval/openrave-release.git
$ cd openrave-release
$ git checkout debian/trusty
$ gbp dch --release --debian-branch=debian/trusty
$ gbp buildpackage --git-debian-branch=debian/trusty --pristine-tar -uc -us
```

**Build a debian binary (`.deb`) package:**
