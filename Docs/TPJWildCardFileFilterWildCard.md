# WildCard property #

**Project:** [Drop Files Components](DropFilesComponents.md).

**Unit:** _PJDropFiles_.

**Class:** _[TPJWildCardFileFilter](TPJWildCardFileFilter.md)_

```pascal
property WildCard: string;
```

## Description ##

This property filters files based on a wildcard string.

It stores the wildcard that is used by the component to filter files. The wildcard is applied to the base filename or folder name (not the path) and uses the same special characters as DOS and Windows wildcards. The wildcard is applied to both files and folders.

### Example ###

To filter out all files except those with names beginning with "PJ" and with a `.pas` extension set _WildCard_ to `'PJ*.pas'`.