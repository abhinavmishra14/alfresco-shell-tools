# Introduction #

All commands of the Alfresco shell tools share a common set of global options and how the work in general.
First the command name prefixed with alf... followed by the global options followed by the options specific for the used command and finally the command arguments (if any):

```
  alfCOMMAND_NAME.sh <GLOBAL OPTIONS> <COMMAND OPTIONS> <COMMAND ARGUMENTS>
```

The common set of options are usual named in uppercase letters, except for -h(elp) and -v(erbose)
```
    -h   help       shows this help screen
    -v   verbose    displays information while executing

    -E   endpoint   Alfresco endpoint
    -U   user       Alfresco user id used in authentication
    -P   password   password used for authenticaiton

    -C   curl opts  any additional options pass to curl
```

# Help option -h #

-h shows the help screen and explains all options and arguments of a command. For example the -h output of

```
macx:bin lothar$ ./alfUpload.sh -h
usage: ./alfUpload.sh [global options] [command specific options] arguments
  global options:
    -h   help       shows this help screen
    -v   verbose    displays information while executing

    -E   endpoint   Alfresco endpoint
    -U   user       Alfresco user id used in authentication
    -P   password   password used for authenticaiton

    -C   curl opts  any additional options pass to curl

  command options:
    -n NAME        filename to use for Alfresco
    -m MIMETYPE    mime type of the added file
  command arguments:
    LOCAL_FILE      path to a local file, or - to read contents from stdin.
    ALFURL          pointer to an Alfesco document.

  command explanation:
    the alfUpload.sh command adds content to Alfresco. If there is already a document, its contents will be updated.

  usage examples:

  ./alfUpload.sh ./local/file.pdf /some/repo/path/to/space
     --> uploads the local file at ./local/file.pdf to the space /some/repo/path/to/space

  ./alfUpload.sh ./local/file.pdf workspace://SpacesStore/1234-1234-1234-1234
     --> uplodas the local file at ./local/file.pdf to the space given by the nodeRef

  cat sth.pdf | ./alfUpload.sh -n filename.pdf - /some/repo/path/to/space
     --> uploads content read from stdin and saves it to a file at /some/repo/path/to/space/filename.pdf

```