############################################################
# Dockerfile to build a BioPerl container image
# Based on Ubuntu
############################################################

# Set the base image to the BioPerl prebuilt prerequisites image
# for building from source
FROM bioperl/bioperl-builddeps as builder

# File Author / Maintainer
LABEL maintainer="Hilmar Lapp <hlapp@drycafe.net>"

# Set the working directory to where we will install bioperl
# in the builder stage
WORKDIR /bioperl

# download BioPerl soure, install authordeps, build BioPerl
RUN \
  curl -L -s -o - \
         https://github.com/bioperl/bioperl-live/archive/master.tar.gz | \
    tar xzf - && \
  cd bioperl-live-master && \
  dzil authordeps | cpanm -n && \
  dzil build --in /bioperl/bioperl-build

# Set the base image to the BioPerl prebuilt prerequisites image
# this time for the final image
FROM bioperl/bioperl-deps as final

# Install modules recommended by BioPerl.
# We can't include Bio::ASN1::EntrezGene here yet, because it declares
# a dependency on BioPerl, thus pulling in BioPerl first.
RUN cpanm -n \
  Bio::Phylo

# -------------------------------------------------------------
# Install BioPerl from GitHub current master branch.
#
# This is the actual installation step of BioPerl itself :-)
# -------------------------------------------------------------
# Copy the files produced in the previous build stage over to the 
# final image
COPY --from=builder /bioperl/bioperl-build /usr/local/src/bioperl-build/

# Install bioperl
RUN cpanm -v /usr/local/src/bioperl-build

# Install modules recommended by BioPerl that depend on BioPerl.
# (Don't ask. See above.)
## Temporarily commented out until this bringing in the last BioPerl
## release from CPAN is fixed.
# RUN cpanm \
#   Bio::ASN1::EntrezGene
