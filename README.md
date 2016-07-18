# Docker files for BioPerl

This repository contains Dockerfiles for reproducible builds of
BioPerl.

At this point there are only two Dockerfiles, each in its own
subdirectory. One is for a Docker image with all BioPerl dependencies
pre-built, the other is for main BioPerl distribution itself. The
latter builds on the dependencies image.

At present, the base OS image is Ubuntu 14.04. This may change in the
future, in particular if there is user demand, so please post on the
issue tracker if you'd like to see other base OS images as well.

## bioperl

This is meant to provide a reproducible and complete build of the main
BioPerl distribution, including almost all dependencies. It is based
on the bioperl-deps image (see below), which itself is currently based
on Ubuntu 14.04.

Currently the following tags are available:

* `latest`: Built from the current `master` branch of the bioperl-live
  repository. This image gets automatically rebuilt upon every update
  to the bioperl-live `master` branch that passes the continuous
  integration test on Travis CI.
* `stable`: Built from the latest stable release of BioPerl on
  CPAN. This build may change from one major revision to the next if
  the latest stable release on CPAN changes the major revision. This
  image gets automatically rebuilt whenever a new release-N-N-N tag is
  posted on the bioperl-live repository.
* `release-1-6-924`: Built from the corresponding tag on the
  bioperl-live repository. This is at this time the latest, and last
  planned release for the 1.6.x series.

Other BioPerl release-specific tags will be added as and when they are
released.

## bioperl-deps

This image is meant to provide a well-defined reproducible base image
for BioPerl that has pre-installed all dependencies of at least the
main distribution.

The benefit of this image is to allow anyone to build a version of
BioPerl on top of this image in a reproducible fashion. Since by far
the majority of time when installing BioPerl (or building a BioPerl Docker
image) is spent installing dependencies, using this image as the base
image also significantly cuts down on build (or installation) time (on
Docker Hub from >45 to 5-8 minutes).

The image is available on Docker Hub as [bioperl/bioperl-deps]. At
present there is only one tag, `latest`. The dependencies include all
needed for BioPerl 1.6.x, and we anticipate also for 1.7.x. None of
the dependencies should be incompatible with versions of BioPerl
earlier than the current one, so it should be safe building earlier
versions of BioPerl off of this image, too.

[bioperl/bioperl]: https://hub.docker.com/r/bioperl/bioperl/
[bioperl/bioperl-deps]: https://hub.docker.com/r/bioperl/bioperl-deps/
