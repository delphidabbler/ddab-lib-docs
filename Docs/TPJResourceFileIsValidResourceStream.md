# IsValidResourceStream class method #

**Project:** [Resource File Unit](ResFileUnit.md)

**Unit:** _PJResFile_.

**Class:** _[TPJResourceFile](TPJResourceFile.md)_

```pascal
class function IsValidResourceStream(const Stm: TStream): Boolean;
```

This class method checks if a stream contains data representing a valid 32 bit resource file starting at the current position in the stream. This method checks that a 32 bit resource file header is present but does not validate the whole of the file. Note that the stream is **not** rewound to the starting position after the check is made.

Use _IsValidResourceStream_ to test a stream for validity before loading it into a _[TPJResourceFile](TPJResourceFile.md)_ object.

**_Parameter:_**

  * _Stm_: The stream containing the date to be checked.

**_Returns:_**

`True` if the stream contains the required header information or `False` if the data is not a valid resource file.

**_Example:_**

```pascal
var
  Stm: TStream;
  SavedPos: Int64;
  RF: TPJResourceFile;
begin
  Stm := TFileStream.Create('C:\MyFile.res', fmOpenRead);
  try
    SavedPos := Stm.Position;
    if TPJResourceFile.IsValidResourceStream(Stm) then
    begin
      RF := TPJResourceFile.Create;
      try
        Stm.Position := SavedPos;
        RF.LoadFromStream(Stm);
        // do something with RF here
      finally
        RF.Free;
      end;
    end
    else
      ShowMessage('Stream does not contain valid resource file data');
  finally
    Stm.Free;
  end;
end;
```
