# LoadFromFile method #

**Project:** [Resource File Unit](ResFileUnit.md)

**Unit:** _PJResFile_.

**Class:** _[TPJResourceFile](TPJResourceFile.md)_

```pascal
procedure LoadFromFile(const FileName: TFileName);
```

Loads a resource file from a named file. New _[TPJResourceEntry](TPJResourceEntry.md)_ objects are created for each resource in the file.

Any _[TPJResourceEntry](TPJResourceEntry.md)_ objects that existed before calling _LoadFromFile_ are freed. You should be careful not to access any existing references to such objects after calling _LoadFromFile_.

**_Parameter:_**

  * _FileName_: The name of the file from which to load the resource data.

**_Raises:_**

Exceptions are raised if the file does not exist or does not contain a valid resource file.