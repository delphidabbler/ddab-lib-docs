# AddEntry methods #

**Project:** [Resource File Unit](ResFileUnit.md)

**Unit:** _PJResFile_.

**Class:** _[TPJResourceFile](TPJResourceFile.md)_

There are two overloaded _AddEntry_ methods. They are both used to create a new resource entry within the resource file represented by a _[TPJResourceFile](TPJResourceFile.md)_ object.


---


```pascal
function AddEntry(const ResType, ResName: Pchar;
  const LangID: Word = 0): TPJResourceEntry;
```

Adds a new, empty, resource to the resource file object.

**_Parameters:_**

  * _ResType_: The type of the new resource (ordinal or string).
  * _ResName_: The name of the new resource (ordinal or string).
  * _LangID_: Optional language id of the resource (a language neutral value of `0` is used if this parameter is not provided).

**_Returns:_**

A reference to the new resource entry. This reference should be used to set the resource headers and to store the raw data.

**_Raises:_**

An exception is raised if an entry already exists with same type, name and language id.


---


```pascal
function AddEntry(const Entry: TPJResourceEntry; const ResName: Pchar;
  const LangID: Word = 0): TPJResourceEntry;
```

Adds a copy of an existing resource entry to the resource file object with a new resource name and language id. The new entry has the same resource type as the one being copied.

  * _Entry_: Reference to the resource entry to be copied.
  * _ResName_: Name of the new resource.
  * _LangID_: Optional language id of the resource (a language neutral value of 0 is used if this parameter is not provided).

**_Returns:_**

A reference to the new resource entry that has the same header information and data as the one being copied except for the resource name and language id.

**_Raises:_**

An exception is raised if an entry already exists with same type, name and language id.