# TPJDroppedFileFilter #

**Project:** [Drop Files Components](DropFilesComponents.md).

**Unit:** _PJDropFiles_.

```pascal
TPJDroppedFileFilter = procedure(
  Sender: TObject; const FileName: string; const IsFolder: Boolean;
  var Accept: Boolean
) of object;
```

## Description ##

Event handler type for _OnFileFilter_ events, triggered for each file and folder dropped after processing by any filter component. This event can be handled to apply custom filtering to each file and folder.

_FileName_ is the name of the file or folder being filtered. _IsFolder_ is true if _FileName_ denotes a folder. The state of the _Accept_ flag determines if _FileName_ is to be added to the list of dropped files / folders. _Accept_ is true by default - set it to false to omit the file from the list of dropped files and folders.