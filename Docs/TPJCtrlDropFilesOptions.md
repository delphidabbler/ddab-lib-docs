# Options property #

**Project:** [Drop Files Components](DropFilesComponents.md).

**Unit:** _PJDropFiles_.

**Class:** _[TPJCtrlDropFiles](TPJCtrlDropFiles.md)_

```pascal
property Options: TPJDropFilesOptions;
```

## Description ##

This property determines how dropped files are interpreted. The resulting files are made available through the _[Files](TPJCtrlDropFilesFiles.md)_ property. The property can take any one or more of the values from the _[TPJDropFilesOptions](TPJDropFilesOptionsSet.md)_ set.

It makes no sense to omit both the `dfoIncFiles` and `dfoIncFolders` options since no files will pass the filter.