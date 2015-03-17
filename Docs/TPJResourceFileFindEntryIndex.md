# FindEntryIndex method #

**Project:** [Resource File Unit](ResFileUnit.md)

**Unit:** _PJResFile_.

**Class:** _[TPJResourceFile](TPJResourceFile.md)_

```pascal
function FindEntryIndex(const ResType, ResName: Pchar;
  const LangID: Word = $FFFF): Integer;
```

Finds the index in the _[Entries](TPJResourceFileEntries.md)_ property of a resource entry with the given type, name and language id. The search can ignore the resource name or language id in which case first entry that matches the provided information is accepted.

**_Parameters:_**

  * _ResType_: The type of the resource to be found as either an ordinal or string type.
  * _ResName_: The name of the resource to be found as either an ordinal or string type. If just the first resource of the given type is required then `nil` can be specified here.
  * _LangID_: The language id of the required resource. If only the first matching resource for the given type and name is required this parameter can be left out (or `$FFFF` supplied). To find a language neutral resource specify `0` here.

**_Returns:_**

The index of the found resource in the _[Entries](TPJResourceFileEntries.md)_ property or `-1` if no resource was found.