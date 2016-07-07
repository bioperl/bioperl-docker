############################################################
# Dockerfile to build a BioPerl container image
# Based on Ubuntu
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
# In theory, we should just be able to install BioPerl. But for some
# reason that currently picks up the version _prior_ to the last stable
# one rather than the last.
RUN cpanm -v Bio::Root::Root

# Install modules recommended by BioPerl that depend on BioPerl.
# (Don't ask. See above.)
RUN cpanm \
  Bio::ASN1::EntrezGene
