# LoadFromStream method #

**Project:** [Resource File Unit](ResFileUnit.md)

**Unit:** _PJResFile_.

**Class:** _[TPJResourceFile](TPJResourceFile.md)_

```pascal
procedure LoadFromStream(const Stm: TStream);
```

Loads a resource file from a stream. The data is read from the current location in the stream. Loading the data updates the stream position. New _[TPJResourceEntry](TPJResourceEntry.md)_ objects are created for each resource in the data stream.

Any _[TPJResourceEntry](TPJResourceEntry.md)_ objects that existed before calling _LoadFromStream_ are freed. You should be careful not to access any existing references to such objects after calling _LoadFromStream_.

**_Parameter:_**

  * _Stm_: The stream from which the resource file data is loaded.

**_Raises:_**

An exception is raised if the stream does not contain valid resource file data.