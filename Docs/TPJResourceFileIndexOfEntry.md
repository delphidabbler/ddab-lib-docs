# IndexOfEntry method #

**Project:** [Resource File Unit](ResFileUnit.md)

**Unit:** _PJResFile_.

**Class:** _[TPJResourceFile](TPJResourceFile.md)_

```pascal
function IndexOfEntry(const Entry: TPJResourceEntry): Integer;
```

Gets the index number of a resource entry in the resource file's _[Entries](TPJResourceFileEntries.md)_ property.

**_Parameter:_**

  * _Entry_: A reference to resource entry to be found.

**_Returns:_**

The index of the resource entry in the _[Entries](TPJResourceFileEntries.md)_ property or `-1` if not found.