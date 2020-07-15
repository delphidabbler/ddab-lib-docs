# ProcessFile method

***Project:*** [MD5 Message Digest Unit](../API.md)

***Unit:*** _PJMD5_

***Class:*** [_TPJMD5_](./TPJMD5.md)

***Introduced:*** v1.0

```pascal
procedure ProcessFile(const FileName: TFileName);
```

## Description

This class method is very like the [_Process_](./TPJMD5-Process.md) methods in that it adds data to the current hash. In this case the method reads the file named by the _FileName_ parameter and adds the bytes representing the whole of the file to the current hash.

The file is read into an internal buffer before adding the data to the hash. The buffer's size can be changed by assigning the required size to the [_TPJMD5.ReadBufferSize_](./TPJMD5-ReadBufferSize.md) property. Find the current size of the buffer by reading the property.

## Example

Suppose you want a single MD5 hash of all the files in a directory. If the required file names are stored in a string list then the following function will find the required MD5 hash:

```pascal
function MD5OfFiles(const FileNames: TStrings): TPJMD5Digest;
var
  FileName: string;
  MD5: TPJMD5;
begin
  MD5 := TPJMD5.Create;
  try
    for FileName in FileNames do
      MD5.ProcessFile(FileName);
    Result := MD5.Digest;
  finally
    MD5.Free;
  end;
end;
```
