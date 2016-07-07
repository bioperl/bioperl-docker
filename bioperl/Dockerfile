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
  libdb-dev \
  zlib1g-dev \
  graphviz

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

# Install packages for XML processing
RUN apt-get install --yes \
  expat \
  libexpat-dev \
  libxml2-dev \
  libxslt1-dev \
  libgdbm-dev

RUN cpanm \
  XML::Parser \
  XML::Parser::PerlSAX \
  XML::DOM \
  XML::DOM::XPath \
  XML::SAX \
  XML::SAX::Writer \
  XML::Simple \
  XML::Twig \
  XML::Writer \
  XML::LibXML \
  XML::LibXSLT

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
  Spreadsheet::ParseExcel \
  IO::String \
  JSON \
  Data::Stag

# Install database connectivity packages
RUN apt-get install --yes \
  libdbi-perl \
  libdbd-mysql-perl \
  libdbd-pg-perl \
  libdbd-sqlite3-perl

RUN cpanm \
  DB_File

# Install GD and other graphics dependencies
RUN apt-get install --yes \
 libgd2-xpm-dev

RUN cpanm \
  GD \
  SVG \
  SVG::Graph

# Install BioPerl last built
RUN cpanm -v  \
 CJFIELDS/BioPerl-1.6.924.tar.gz 

# Install modules that depend on BioPerl
RUN cpanm \
  Bio::ASN1::EntrezGene \
  Bio::Phylo

