# Dockerfiles for reproducible builds of BioPerl

This image is meant to provide a well-defined reproducible base image for BioPerl that has pre-installed all dependencies of at least the main distribution.

The benefit of this image is to allow anyone to build a version of BioPerl on top of this image in a reproducible fashion. Since by far the majority of time when installing BioPerl (or building a [BioPerl Docker image]) is spent installing dependencies, using this image as the base image also significantly cuts down on build (or installation) time (on Docker Hub from >45 to 5-8 minutes).

At present there is only one tag, `latest`. The dependencies include all needed for BioPerl 1.6.x, and we anticipate also for 1.7.x. None of the dependencies should be incompatible with versions of BioPerl earlier than the current one, so it should be safe building earlier versions of BioPerl off of this image, too. The base OS image at present is Ubuntu 14.04. This may change in the future, in particular if there is user demand, so please post on the issue tracker if you'd like to see other base OS images as well.


## Acknowledgements

The initial starting point for this work was the [bioperl-1.6.1924 Dockerfile created by @sophielemoine] at Genomic Paris Centre.

[BioPerl Docker image]: https://hub.docker.com/r/bioperl/bioperl/
[bioperl-1.6.1924 Dockerfile created by @sophielemoine]: https://github.com/GenomicParisCentre/dockerfiles/blob/master/bioperl/bioperl-1.6.924/Dockerfile
