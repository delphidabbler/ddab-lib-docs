# OnFileFilter event #

**Project:** [Drop Files Components](DropFilesComponents.md).

**Unit:** _PJDropFiles_.

**Class:** _[TPJCtrlDropFiles](TPJCtrlDropFiles.md)_

```pascal
property OnFileFilter: TPJDroppedFileFilter;
```

## Description ##

This event is triggered for each dropped file and folder handled on behalf of the managed control and has type _[TPJDroppedFileFilter](TPJDroppedFileFilter.md)_. The file or folder can be omitted from the list of dropped files by altering the _Accept_ parameter of the event handler from True to False.

Folders that are filtered out by this event are not added to the _[Files](TPJCtrlDropFilesFiles.md)_ property but are still scanned when the `dfoRecurseFolders` is included in _[Options](TPJCtrlDropFilesOptions.md)_.

Note that the _[Filter](TPJCtrlDropFilesFilter.md)_ property takes precedence and files filtered out by the associated filter component are not processed by this event.