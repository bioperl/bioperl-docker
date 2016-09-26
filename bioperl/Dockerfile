############################################################
# Dockerfile to build a BioPerl container image
# Based on Ubuntu
#
# This version installs the latest release on CPAN that is
# marked as stable, i.e., not as a developer release.
############################################################

# Set the base image to the BioPerl prebuilt prerequisites image
FROM bioperl/bioperl-deps

# File Author / Maintainer
MAINTAINER Hilmar Lapp <hlapp@drycafe.net>

# Install modules recommended by BioPerl.
# We can't include Bio::ASN1::EntrezGene here yet, because it declares
# a dependency on BioPerl, thus pulling in BioPerl first.
RUN cpanm \
  Bio::Phylo

# -------------------------------------------------------------
# Install BioPerl from the last stable version registered on CPAN.
#
# This is the actual installation step of BioPerl itself :-)
# -------------------------------------------------------------
#
# In theory, we should just be able to install BioPerl. But the indexing
# of releases by CPAN is not currently working in the way it should for
# BioPerl, since BioPerl doesn't have a hard-coded VERSION declared in
# each of its >900 source modules. Until this is worked out, we use
# Bio::Root::Version, which is the place that does hardcode the version.
RUN cpanm -v Bio::Root::Version

# Install modules recommended by BioPerl that depend on BioPerl.
# (Don't ask. See above.)
RUN cpanm \
  Bio::ASN1::EntrezGene
