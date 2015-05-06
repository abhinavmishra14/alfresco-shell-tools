Alfresco offers a rich remote API using its WebScripts technology which is based on the REST paradigm. This projects provides a set of scripts that makes it more easy to interact with the repository and its exposed resources.

Create or change users, create sites, manage group membership form the command line instead of the user interface.

Also great for automation: Create some hundreds of users from a table and automatically add to a set of groups? This becomes a one liner with the Alfresco shell tools.

## News ##

  * 2014-01-13: New commands for multi tenancy since Alfresco 4.2: alfCreateTenant.sh, alfListTenants.sh
  * 2014-01-09: Added some small commands: alfRename.sh and alfGetUserHomeFolder.sh
  * 2012-12-11: Uploaded jshon binary for mac os and an Ubuntu package for easier installation
  * 2012-12-09: Richard Esplin of Alfresco joined the project - Welcome Richard!


## Use cases ##

Reported use cases have been:
  * Backup User-Group relationships
  * Provision demo systems
  * Keep avatar pictures in sync with a 3rth party source
  * pregenerate >100k thumbnail images
  * Initial import of users and groups, along with user-group and group-subgroup assignements
  * Create a bunch of tenants for a multi-tenancy enabled Alfresco
  * Do repetitive maintenance tasks for multiple tenants in one go

## How start? ##

  1. check out the scripts or download a release tarball
  1. install required 3-rd party tools for json handling
  1. set environment variables
  1. have fun

See the [Introduction](Introduction.md) for the usage and possibilities of the commands.

Further pages showing the commands:
[GeneralInstructions](GeneralInstructions.md)

[DocumentsAndFolderFun](DocumentsAndFolderFun.md)

[UsersAndGroupsFun](UsersAndGroupsFun.md)

[SearchFun](SearchFun.md)

SitesFun


## Alfresco version compatibility ##
Users reported success with Alfresco 4.0dCE, 4.1.3EE, 4.2bCE, 4.2cCE, 4.2eCE