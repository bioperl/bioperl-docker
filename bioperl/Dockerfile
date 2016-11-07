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
RUN cpanm -v Bio::Perl

# Install modules recommended by BioPerl that depend on BioPerl.
# (Don't ask. See above.)
RUN cpanm \
  Bio::ASN1::EntrezGene
