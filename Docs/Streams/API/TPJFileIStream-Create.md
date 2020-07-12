# Create constructor

***Project:*** [Stream Extension Classes](../API.md)

***Unit:*** [_PJIStreams_](./PJIStreams.md)

***Class:*** [_TPJFileIStream_](./TPJFileIStream.md)

```pascal
constructor Create(const FileName: string; Mode: Word);
```

## Description

Object constructor. Creates a stream onto a given file that supports the _IStream_ interface.

***Parameters:***

* _FileName_ -- Name of file that the stream is to be opened onto.
* _Mode_ -- Bitmask determining how the file is to be opened. Valid values are the same as those used in the _TFileStream_ constructor with the same parameters from Delphi's _Classes_ unit.
