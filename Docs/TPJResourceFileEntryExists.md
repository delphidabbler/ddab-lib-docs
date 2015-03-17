# EntryExists method #

**Project:** [Resource File Unit](ResFileUnit.md)

**Unit:** _PJResFile_.

**Class:** _[TPJResourceFile](TPJResourceFile.md)_

```pascal
function EntryExists(const ResType, ResName: PChar;
  const LangID: Word = $FFFF): Boolean;
```

Checks whether a resource entry with the specified type, name and language id exists. The search can ignore the resource name and or language id in which case the method succeeds if any resource matching the provided information is accepted.

**_Parameters:_**

  * _ResType_: The type of the resource to be found as either an ordinal or string type.
  * _ResName_: The name of the resource to be found as either an ordinal or string type. If just the first resource of the given type is required then `nil` can be specified here.
  * _LangID_: The language id of the required resource. If only the first matching resource for the given type and name is required this parameter can be left out (or `$FFFF` supplied). To find a language neutral resource specify `0` here.

**_Returns:_**

`True` if a resource matching the search criteria exists and `False` if not.