# Filter property #

**Project:** [Drop Files Components](DropFilesComponents.md).

**Unit:** _PJDropFiles_.

**Class:** _[TPJDropFiles](TPJDropFiles.md)_

```pascal
property Filter: TPJFileFilter;
```

## Description ##

References a file filter component that is used to filter the names of dropped files.

The referenced component filters the dropped files and stores only those files that pass through the filter. The filter component must descend from the _[TPJFileFilter](TPJFileFilter.md)_ abstract base class. Various _TPJFileFilter_ descendants perform different kinds of filtering. Those supported in this release are:

  * _[TPJExtFileFilter](TPJExtFileFilter.md)_ - filters out all files that do not have one of more specified extensions.
  * _[TPJWildCardFileFilter](TPJWildCardFileFilter.md)_ - filters out file names that do not match a given wildcard.

Any files that pass the filter are then passed to the _[OnFileFilter](TPJDropFilesOnFileFilter.md)_ event, if handled.