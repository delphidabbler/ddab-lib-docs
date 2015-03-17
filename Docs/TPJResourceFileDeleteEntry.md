# DeleteEntry method #

**Project:** [Resource File Unit](ResFileUnit.md)

**Unit:** _PJResFile_.

**Class:** _[TPJResourceFile](TPJResourceFile.md)_

```pascal
function DeleteEntry(const Entry: TPJResourceEntry): Boolean;
```

Removes a resource entry from the resource file object. The resource entry object **is not freed** so must be freed explicitly by the user when no longer required.

The recommended way to delete and free a resource entry is to free the _[TPJResourceEntry](TPJResourceEntry.md)_ object while it is still linked into the resource file since this automatically unlinks it from the resource. The _DeleteEntry_ method is provided in case you need to unlink a resource entry from a resource file and work on the entry after unlinking it, or perhaps to move the entry to a different resource file.

If the resource entry is not in the resource file then _DeleteEntry_ does nothing.

**_Parameter:_**

  * _Entry_: Reference to the resource entry object to be deleted.

**_Returns:_**

`True` if the resource entry was in the resource file and was deleted and `False` otherwise.