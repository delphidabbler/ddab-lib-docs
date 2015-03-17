# SaveToFile method #

**Project:** [Resource File Unit](ResFileUnit.md)

**Unit:** _PJResFile_.

**Class:** _[TPJResourceFile](TPJResourceFile.md)_

```pascal
procedure SaveToFile(const FileName: TFileName);
```

Creates a 32 bit resource file containing all the resources recorded in the resource file object. If there are no resource entries then a valid empty resource file is created.

**_Parameter:_**

  * _FileName_: The name of the resource file to be created.

**_Raises:_**

An exception is raised if the file cannot be created.