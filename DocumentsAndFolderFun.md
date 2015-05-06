

# Upload a document #

Uploads a document into a folder and output the nodeRef of the uploaded file. Can also read file content piped from stdin.

## Target folder by path ##
```
alfUpload.sh ./local/file.pdf /repository/folder
workspace://SpacesStore/2c28746c-9181-4c71-83cc-9e7bddd0d305
```

## Target folder by nodeRef ##
```
alfUpload.sh ./local/file.pdf workspace://SpacesStore/1234-1234-1234-1234
workspace://SpacesStore/2c28746c-9181-4c71-83cc-9e7bddd0d305
```

## Piped input, for example a zipped doc ##
The filename has to given with the -n(ame) option in this case. Also use - to indicate that the file contents should be read from stdin

```
gzip -c bigfile.txt | alfUpload.sh -n somefile.gz - /repo/folder
workspace://SpacesStore/2c28746c-9181-4c71-83cc-9e7bddd0d305
```

# Delete a document or folder #

```
alfDelete.sh workspace://SpacesStore/2c28746c-9181-4c71-83cc-9e7bddd0d305
{
   "totalResults": 1,
   "overallSuccess": true,
   "successCount": 1,
   "failureCount": 0,
   "results":
   [
      {
         "action": "deleteFile",
         "id": "tester.txt",
         "nodeRef": "workspace:\/\/SpacesStore\/2c28746c-9181-4c71-83cc-9e7bddd0d305",
         "success": true
      }
   ]
}
```

# Download a file #
The alfGet.sh command downloads document contents. The content ist always printed to stdout for further processing.

```
alfGet.sh tester.txt
contents
of 
the file
tester.txt
```

Grep some stuff out of it
```
alfGet.sh tester.txt |grep of
of
```

Save to file myfile.txt
```
alfGet.sh tester.txt > myfile.txt
```


# Get and generate a thumbnail #

Get a preview rendition of a document. The -t(ype) option tells which type preview to fetch. All preview types that are registered with the ThumbnailRegistry (see thumbnail-services-context.xml) can be specified. If the preview was not yet generated, use the -f(orce) option to let Alfresco generate it on the fly.
```
alfGetThumbnail.sh -f -t webpreview workspace://SpacesStore/u-u-i-d > webpreview.swf 
```


# Rename a document or folder #

Rename the document (or folder) on the command line. It simple sets the cm:name property of the node.

```
alfRename.sh workspace://SpacesStore/u-u-i-d "Some new filename.txt"
```