# Introduction and rational #

This project contains a collection of shell scripts, that makes interaction with Alfresco a snap. Common administrative tasks and simple integrations will become a one liner.

# Installation #

The scripts require a bash shell and familiar tools like curl. If you are on Linux (and of course you should) or Mac (acceptable) everything will be fine.

  1. Go to /usr/local/share
  1. Download the latest release: `git clone https://code.google.com/p/alfresco-shell-tools/`
  1. Configure your environment:
    1. Add the Alftools scripts to your shells search PATH: `export PATH="$PATH:/usr/local/share/alfresco-shell-tools/bin"`. To make this permanent add this line to your HOME/.profilerc file
    1. Set the target server: `export ALFTOOLS_ENDPOINT=http://localhost:8080/alfresco`
    1. Set the target server for share: `export ALFTOOLS_SHARE_ENDPOINT=http://localhost:8080/share`
    1. Set the user: `export ALFTOOLS_USER=admin`
    1. Set the password: `export ALFTOOLS_PASSWORD=admin`
  1. install required 3rd party tools for json parsing, see the InstallationGuide page for details
    1. jansson: library for parsing json http://www.digip.org/jansson/doc/2.3/gettingstarted.html#compiling-and-installing-jansson
    1. jshon: command line tool to manipulate json http://kmkeen.com/jshon/ - links to the jansson lib

# Usage #

GeneralInstructions

DocumentsAndFolderFun

UsersAndGroupsFun

SearchFun

SitesFun

DevelopmentFun

# Version compatibility #

Tested with 4.0dCE and 4.2aCE from Sep.2012


# About the authors #

## Lothar Märkle ##

Co-founder and CTO of the company ecm4u - http://ecm4u.de - a system integrator for Alfresco and operator of the ecm Market http://www.ecm-market.de.

## Richard Esplin ##

Alfresco Community Technology - http://www.alfresco.com