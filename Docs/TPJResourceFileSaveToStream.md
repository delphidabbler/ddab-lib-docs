# SaveToStream method #

**Project:** [Resource File Unit](ResFileUnit.md)

**Unit:** _PJResFile_.

**Class:** _[TPJResourceFile](TPJResourceFile.md)_

```pascal
procedure SaveToStream(const Stm: TStream);
```

Saves the resource file object's data to a stream. The data written is in the form of a 32 bit resource file containing all the resources recorded in the resource file object. If there are no resource entries then the data of a valid empty resource file is written to the stream.

**_Parameter:_**

  * _Stm_: The stream to which the resource file data is written.

**_Raises:_**

An exception is raised if the stream does not support writing.