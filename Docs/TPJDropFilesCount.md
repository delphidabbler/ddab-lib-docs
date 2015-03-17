# Count property #

**Project:** [Drop Files Components](DropFilesComponents.md).

**Unit:** _PJDropFiles_.

**Class:** _[TPJDropFiles](TPJDropFiles.md)_

```pascal
property Count: Integer;
```

## Description ##

This read only property returns the number of files dropped on the _TPJDropFiles_ control or its child controls.

The names of the dropped files are stored in the _[Files](TPJDropFilesFiles.md)_ array property and are indexed from 0 to _Count_ - 1.

Files filtered out via the _[Options](TPJDropFilesOptions.md)_ and _[Filter](TPJDropFilesFilter.md)_ properties or the _[OnFileFilter](TPJDropFilesOnFileFilter.md)_ event handler are not included in the _Files_ or _Count_ properties.