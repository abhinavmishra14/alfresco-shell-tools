

# Create a site #

To create a site from the command line, issue the following command.
The sites short name will be calculated from the given name.

```
$ alfCreateSite.sh 'My new Site'
{
  success: true
}
```

# Create a site with all options #

All available options are: -s(hortName) -d(escription) -a(ccess) -p(reset)

```
$ alfCreateSite.sh -s shortname -d 'some description' -a PUBLIC -p 'site-dashboard' NewSiteTitle
```

# Delete a site #

To remove a site the short name as to given as first argument.

```
$ alfDeleteSite.sh my_new_site
```


# Add a user or group to a site (without invitation) #

This is the same as adding a user (or group) to an existing group. Lookup the site groups name and then add the user or group by alfAddAuthorityToGroup.sh.

# Remove a user or group from a site #

See on how to remove a user (or group) from a group.