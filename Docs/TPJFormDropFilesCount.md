# Count property #

**Project:** [Drop Files Components](DropFilesComponents.md).

**Unit:** _PJDropFiles_.

**Class:** _[TPJFormDropFiles](TPJFormDropFiles.md)_

```pascal
property Count: Integer;
```

## Description ##

This read only property returns the number of files dropped on the form.

The names of the dropped files are stored in the _[Files](TPJFormDropFilesFiles.md)_ array property and are indexed from 0 to _Count_ - 1.

Files filtered out via the _[Options](TPJFormDropFilesOptions.md)_ and _[Filter](TPJFormDropFilesFilter.md)_ properties or the _[OnFileFilter](TPJFormDropFilesOnFileFilter.md)_ event handler are not included in the _Files_ or _Count_ properties.