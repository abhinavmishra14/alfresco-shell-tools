# Introduction #

The Alfresco shell tools use the jshon tool to parse JSON output from the alfresco REST API. It is very valuable tool to work with JSON on the command line. Compare it to the xmlstarlet tool with xml.

Please see how you can install the jshon tool. The alfresco shell tools project has made precompiled packages available to ease the installation.

# Installation with ready-to-use packages #

On the downloads page a precompiled package of jshon for linux (Ubuntu .deb package) and for Mac OS X (just the executable) is available.

# Manual installation #

How to install this tool is described here in detail.

## 1. Compile and install Jansson library ##

On ubuntu 12.x there is a jansson package: `apt-get install libjansson-dev`

All details are here http://www.digip.org/jansson/doc/2.3/gettingstarted.html#compiling-and-installing-jansson and is a standard autotools based project with configure && make && make install.

## 2. Compile and install jshon program ##

  1. Download tgz from here: wget http://kmkeen.com/jshon/jshon.tar.gz
  1. extract to a directory of your choise: devenv/lib/jshon and cd into that directory
  1. be sure to have the packages libc6-dev and build-essentials
  1. do a 'make' which creates the jshon binary
  1. the jshon binary has to put on your path, e.g. /usr/local/bin or /usr/bin

## Troubleshooting ##

If you get the error "library libjansson" not found you may need a ldconfig run. Maybe the environment variable LD\_LIBRARY\_PATH=/usr/local/lib has to be set, so that the jansson libary can be found while executing jshon