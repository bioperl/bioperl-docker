############################################################
# Dockerfile to build bioperl container images
# Based on Ubuntu
############################################################

# Set the base image to Ubuntu
FROM ubuntu:14.04

# File Author / Maintainer
MAINTAINER Hilmar Lapp <hlapp@drycafe.net>

# Prevent error messages from debconf about non-interactive frontend
ARG TERM=linux
ARG DEBIAN_FRONTEND=noninteractive

# Update the repository sources list
RUN apt-get update

# Install compiler and perl stuff
RUN apt-get install --yes \
  build-essential \
  gcc-multilib \
  perl

# Install libraries that BioPerl dependencies depend on
RUN apt-get install --yes \
  expat \
  libexpat-dev \
  libdb-dev \
  graphviz

##RUN apt-get install --yes \
## libarchive-zip-perl

# Install perl modules 
RUN apt-get install --yes cpanminus

RUN cpanm \
  CPAN::Meta \
  YAML \
  Digest::SHA \
  Module::Build \
  Test::Most \
  Test::Weaken \
  Test::Memory::Cycle \
  Clone

# Install what counts as BioPerl dependencies
RUN cpanm \
  HTML::TableExtract \
  Algorithm::Munkres \
  Array::Compare \
  Convert::Binary::C \
  Error \
  Graph \
  GraphViz \
  PostScript::TextBlock \
  Set::Scalar \
  Sort::Naturally \
  Math::Random \
  Spreadsheet::ParseExcel

# Install XML-dependent packages
RUN apt-get install --yes \
    libxml2-dev

RUN cpanm \
  XML::DOM::XPath \
  XML::Parser \
  XML::Parser::PerlSAX \
  XML::SAX \
  XML::SAX::Writer \
  XML::Simple \
  XML::Twig \
  XML::Writer \
  SVG \
  SVG::Graph

# Install database connectivity packages
RUN apt-get install --yes \
  libdbd-mysql \
  libdbd-mysql-perl \
  libdbd-pgsql

RUN cpanm \
  DBI \
  Data::Stag \
  DB_File \
  DBD::mysql \
  DBD::Pg \
  DBD::SQLite

# Install GD
RUN apt-get install --yes \
 libgd2-xpm-dev

RUN cpanm GD

# Install BioPerl dependancies, mostly from cpan
##RUN apt-get install --yes \
## libpixman-1-0 \
## libpixman-1-dev \
## libxml-parser-perl \
## libsoap-lite-perl 

## RUN apt-get install -y \
## libxml-libxml-perl \
## libxml-dom-xpath-perl \
## libxml-libxml-simple-perl \
## libxml-dom-perl

# Install BioPerl last built
RUN cpanm -v  \
 CJFIELDS/BioPerl-1.6.924.tar.gz 

# Install modules that depend on BioPerl
RUN cpanm \
  Bio::ASN1::EntrezGene \
  Bio::Phylo

