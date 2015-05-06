

# Query the repository #

Please note the behaviour of the Alfresco search implementations (solr or lucene) and their implications on the result set.


# Search for all documents containing the word 'alfresco' #
```
$ alfSearch.sh alfresco
workspace://SpacesStore/82c914d3-87d5-4772-8bf3-37263ca3fceb
workspace://SpacesStore/e2af816a-a584-4c98-94f5-9c8ddc258d84
workspace://SpacesStore/9990d269-2b2d-4f94-9caf-3f224ee0c26a
workspace://SpacesStore/b92463ef-49c2-4574-ae1a-49d01e2f4ef1
workspace://SpacesStore/8f322a03-cf10-453d-906a-cb7af92bcc03
workspace://SpacesStore/78809ea0-5b44-43c9-9e85-0e3200f9f444
...
```


# Output the file name of the search results instead of the nodeRef #

The option -p(roperty) selects which property of the search results to show. These are not ordinary Alfresco property qnames with namespaces, but are search specific values. There is also just a subset returend from Alfresco:

**nodeRef(default)** name
**path** type
**displayName** title
**description** modifiedOn,
**modifiedBy** modifiedByUser
**size** mimetype,
**path**

```
$ alfSearch -p name alfresco
alfresco docs.js.sample
emailbody_texthtml_alfresco.ftl
emailbody_texthtml_alfresco_it.ftl
emailbody_texthtml_alfresco_de.ftl
emailbody_texthtml_alfresco_fr.ftl
emailbody_texthtml_alfresco_es.ftl
emailbody_texthtml_alfresco_ja.ftl
emailbody_textplain_alfresco.ftl
emailbody_textplain_alfresco_it.ftl
emailbody_textplain_alfresco_de.ftl
...
```

# Raw JSON search output #

Use the -m(ode) switch to output the raw search results data in json format

```
macx:bin lothar$ ./alfSearch.sh -m json tester
{
	"items":
	[
		{
			"nodeRef": "workspace:\/\/SpacesStore\/9c04feaa-2c1e-41c0-808c-07fde5ced6eb",
			"type": "document",
			"name": "tester.txt",
			"displayName": "tester.txt",
			"description": "",
			"modifiedOn": "2012-09-07T21:04:05.289+02:00",
			"modifiedByUser": "admin",
			"modifiedBy": "Administrator ",
			"size": 11,
			"mimetype": "text\/plain",
			"path": "\/Company Home",
			"tags": []
		}
      ]
}
```

# Delete all documents matching a search term #

```
for nodeRef in `alfSearch.sh tester`; do alfDelete.sh $nodeRef;done
```


# Alfresco search solr vs. lucene #

from the alfSearch.sh -h output:

```
side note about the Alfresco search and the implications of the various implementations

    If Alfresco uses the LUCENE search backend, the result list will not be stable. This is due
    to internal performance optimizations done by Alfresco and depends on cache filling levels and
    system load. As a result the search will return more results on subsequence executions.

    If Alfresco is configured to use the SOLR search backend, the result list will be 'eventual consistent'
    This simple means, the Alfresco content is indexed by a background job in an asynchronous manner and
    and therefore will not contain all content at any point in time.
    However, the result list is stable, taking into account what is indexed so far.
```