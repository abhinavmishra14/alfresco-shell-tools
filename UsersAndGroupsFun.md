These commands let you manage users and groups, but also control group membership. With a litte shell automation it becomes a trivial task to create many users and also set their group membership (Compare to Alfrescos ability to import a User-CSV file).



# Create a new user #
The alfCreateUser.sh command is able to create a user and also to assign the user to several exisiting groups.

```
$ alfCreateUser.sh -n lothar -p password -f Lothar -l Märkle -e lothar.maerkle@ecm4u.de -g GroupA -g GroupB -g GroupC
```

# Change user details #
The first, last name and email fields can be also updated using the following command:

```
alfUpdateUser.sh -n lothar -f FirstName -l LastName -e my@email.com
```

# Get user detail properties #

The alfGetUser.sh command dumps some json with extra user details, including groups assignment:
```
$ alfGetUser.sh admin
macx:bin lothar$ ./alfGetUser.sh admin
{
 "emailFeedDisabled": false,
 "companyaddress2": null,
 "sizeCurrent": 0,
 "firstName": "Administrator",
 "companyfax": null,
 "url": "/alfresco/service/api/person/admin",
 "instantmsg": null,
 "companytelephone": null,
 "skype": null,
 "location": null,
 "jobtitle": null,
 "telephone": null,
 "email": "admin@alfresco.com",
 "lastName": "",
 "userStatus": null,
 "organization": null,
 "enabled": true,
 "userName": "admin",
 "companyemail": null,
 "mobile": null,
 "userStatusTime": null,
 "companyaddress1": null,
 "companyaddress3": null,
 "companypostcode": null,
 "googleusername": null,
 "quota": -1,
 "persondescription": null,
 "capabilities": {
  "isMutable": true,
  "isGuest": false,
  "isAdmin": true
 },
 "groups": [
  {
   "itemName": "GROUP_ALFRESCO_ADMINISTRATORS",
   "displayName": "ALFRESCO_ADMINISTRATORS"
  },
  {
   "itemName": "GROUP_EMAIL_CONTRIBUTORS",
   "displayName": "EMAIL_CONTRIBUTORS"
  }
 ],
 "immutability": {}
}
```

# Add a user to a group #
Use the alfAddAuthorityToGroup.sh command to add a user to group:
```
$ alfAddAuthorityToGroup.sh  ParentGroup MyUserId
```

# Subgroup assignment #
Use GROUP_prefix to add subgroup
```
$ alfAddAuthorityToGroup.sh  ParentGroup GROUP_Subgroup
```_

# Delete a user #
Remove the user MyUserId like this:
```
$ alfDeleteUser.sh MyUserId
```

# Add a User to a site (without invitation) #
Ooops - The user hans tried to log out of Alfresco, but instead left the site TestSite by accident? No Problem, add him again to the site:
```
$ alfAddAuthorityToGroup.sh site_testsite_SiteConsumer hans
```


# Add a new group #

Add a group named "newgroupabc" :

```
$ alfCreateGroup.sh newgroupabc
{
 "data": {
  "displayName": "newgroupabc",
  "authorityType": "GROUP",
  "url": "/api/groups/newgroupabc",
  "shortName": "newgroupabc",
  "fullName": "GROUP_newgroupabc"
 }
}
```

# Add a new group as a subgroup #

Same thing: use the -p(arent) option to set a parent group.

```
$ alfCreateGroup.sh -p newgroupabc newsubgroup123
{
	"data":{
		   "authorityType": "GROUP",
		   "shortName": "newsubgroup123",
		   "fullName": "GROUP_newsubgroup123",
		   "displayName": "newsubgroup123",
		   "url": "/api/groups/newsubgroup123"
        }
}
```

# Delete a group #

```
$ alfDeleteGroup.sh GroupA
```

# List group members #

Show all members of an Alfresco group. Use the -g(roup) or -u(ser) switches to list only subgroups or direct members:

```
$ alfListGroupMembers.sh  -u ALFRESCO_ADMINISTRATORS
admin
```

# Remove a user from a group #

```
$ alfDeleteAuthorityFromGroup.sh ParentGroup lothar
```

# Remove a subgroup from a group #

Use the GROUP_prefix to indicate that a subgroup should be removed. Note that the subgroup is not deleted, it is just removed as a subgroup._

```
$ alfDeleteAuthorityFromGroup.sh ParentGroup GROUP_SubParentTestGroup
```

# List all groups #

```
$ alfListGroups.sh 
GROUP_TestGroupA
GROUP_ALFRESCO_ADMINISTRATORS
GROUP_EMAIL_CONTRIBUTORS
GROUP_GroupA
...
```

# List all members of all groups #

A table is required to see which groups contain which users? Wait a second...just combine the groups listing with the member listing:
```
$ for groupName in `./alfListGroups.sh`; do echo "$groupName=`./alfListGroupMembers.sh -u $groupName | paste -s -d ',' -`";done
GROUP_TestGroupA=
GROUP_ALFRESCO_ADMINISTRATORS=admin
GROUP_EMAIL_CONTRIBUTORS=admin
GROUP_GroupA=lothar,lothar4,lothar6,lothar7,t1
GROUP_GroupB=lothar,lothar6,lothar7
...
```


# List all groups of each user #

This other way round from above, can be achieved by feeding the user list to the user details command from which output the user groups are extracted.

```
$ for userName in `./alfListUsers.sh`; do echo "$userName=`./alfGetUser.sh $userName | ./jshon -Q -e groups -a -e itemName -u|paste -s -d , -`";done
admin=GROUP_ALFRESCO_ADMINISTRATORS,GROUP_EMAIL_CONTRIBUTORS
guest=
abeecher=
mjackson=
lothar=GROUP_GroupA,GROUP_GroupB,GROUP_ParentGroup,GROUP_testgroup1
lothar1=GROUP_ParentGroup
lothar7=GROUP_GroupA,GROUP_GroupB
...
```


# Set the avatar of a user #

Set the avatar image of some user, here admin. Can be easily used to update the avatars of a bunch of users in a loop.

```
$ alfSetAvatar.sh localimage.png admin
```

# Reset the avatar of a user #

To restore the Alfresco default placeholder picture do this:

```
$ alfResetAvatar.sh admin
{
  "success": true
}
```