############################################################
# Dockerfile for the prerequisites to build and install    #
# BioPerl from source since the switch to Dist::Zilla      #
############################################################

# Set the base image to the various BioPerl dependencies prebuilt
FROM bioperl/bioperl-deps

# File Author / Maintainer
LABEL maintainer="Hilmar Lapp <hlapp@drycafe.net>"

# Prevent error messages from debconf about non-interactive frontend
ARG TERM=linux
ARG DEBIAN_FRONTEND=noninteractive

# Install software needed to build BioPerl (not all are required to run it)
RUN apt-get update --yes && \
    apt-get install --yes git
RUN cpanm -n \
       Dist::Zilla \
       Dist::Zilla::Plugin::Git \
       Dist::Zilla::PluginBundle::BioPerl
