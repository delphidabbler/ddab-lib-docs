# TPJVersionNumber record

***Project:*** [Version Information Component](../API.md)

***Unit:*** _PJVersionInfo_

```pascal
TPJVersionNumber = record
  V1: Word;   // Major version number
  V2: Word;   // Minor version number
  V3: Word;   // Revision version number
  V4: Word;   // Build number
end;
```

## Description

_V1_ represents the most significant version number and _V4_ represents the least significant number. For example a version number written as `2.5.8.3` would be stored in a variable of type _TPJVersionNumber_ with `V1=2`, `V2=5`, `V3=8` and `V4=3`.

Common uses for these fields are shown in the comments in the record definition above.

### Enhanced Functionality [v3.3]

When compiled with Delphi 2006 and later _TPJVersionNumber_ has some additional functionality. This functionality depends on the availability of advanced records, which were introduced with Delphi 2006.

#### String Assignment

A _TPJVersionNumber_ record can be assigned to a string variable. The version number is stored in the string as a dotted quad.

If the following code is executed the string variable _S_ will have the value `'2.5.8.3'`.

```pascal
var
  S: string;
  VN: TPJVersionNumber;
begin
  VN.V1 := 2;
  VN.V2 := 5;
  VN.V3 := 8;
  VN.V4 := 3;
  S := VN;
  // ...
end;
```

You cannot reverse this assignment - a string cannot be assigned to a _TPJVersionNumber_ record.

Users of Delphi 2005 and earlier can use the [_VerNumToStr_](./Routines.md#vernumtostr) routine to convert a _TPJVersionNumber_ to a string.

#### Operator Overloads

_TPJVersionNumber_ records can be compared with each other using all the usual equality operators, i.e. `=`, `<>`, `<`, `<=`, `>` and `>=`. This is particularly useful when checking the version numbers of two copies of an executable file to find which one is the latest version.

For example:

```pascal
var
  VI1, VI2: TPJVersionInfo;
begin
  VI1 := nil;
  VI2 := nil;
  try
    VI1 := TPJVersionInfo.Create(nil);
    VI2 := TPJVersionInfo.Create(nil);
    VI1.FileName := 'C:\Path\To\Program1.exe';
    VI2.FileName := 'C:\Path\To\Program2.exe';
    if not VI1.HaveInfo or not VI2.HaveInfo then
      Exit;  // no version info available
    if VI1.FileVersionNumber > VI2.FileVersionNumber then
    begin
      // Program1.exe has later version than Program2.exe
    end;
  finally
    VI1.Free;
    VI2.Free;
  end;
end;
```

Users of Delphi 2005 and earlier can use the [_CompareVerNums_](./Routines.md#comparevernums) routine to compare two version numbers.
