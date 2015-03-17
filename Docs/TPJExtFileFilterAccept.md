# Accept method #

**Project:** [Drop Files Components](DropFilesComponents.md).

**Unit:** _PJDropFiles_.

**Class:** _[TPJExtFileFilter](TPJExtFileFilter.md)_

```pascal
function Accept(
  const FilePath: string; const IsFolder: Boolean
): Boolean; override;
```

## Description ##

Checks whether a given file or folder passes though the filter.

This method is called by the filter's owning drop files component whenever files are dropped. It is called once for each dropped file or folder and returns true if the file or folder passes through the filter and false if not. _FilePath_ is the fully qualified path of the file or folder concerned, while _IsFolder_ indicates whether _FilePath_ is a file or folder.

For a file to pass through the filter it must either be of a type that is not being filtered (per the _[Style](TPJExtFileFilterStyle.md)_ property) or it must have an extension that matches one of those listed in the _[Extensions](TPJExtFileFilterExtensions.md)_ property.

This method is used internally by the drop files components. There is no reason to call the method from program code unless to discover whether a file or folder will pass the filter.