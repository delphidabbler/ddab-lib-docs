# LoadDataFromFile method #

**Project:** [Resource File Unit](ResFileUnit.md)

**Unit:** _PJResFile_.

**Class:** _[TPJResourceEntry](TPJResourceEntry.md)_

**Introduced:** v1.1

```pascal
procedure LoadDataFromFile(const SrcFileName: TFileName;
  const Append: Boolean);
```

Loads the content of a file into the resource entry's raw data. The file content can either replace existing or be appedned to it.

After the file is loaded the _[Data](TPJResourceEntry.md#properties)_ property's stream pointer is set to `0`.

_**Parameters**_

  * _SrcFileName_: The name of the file whose contents are to be loaded.
  * _Append_: When `True` the file contents are appended to the end of any current resource data. When `False` any existing resource data is replaced by the file contents.
