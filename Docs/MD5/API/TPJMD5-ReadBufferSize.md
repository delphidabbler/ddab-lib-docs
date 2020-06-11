# ReadBufferSize property

***Project:*** [MD5 Message Digest Unit](../API.md)

***Unit:*** _PJMD5_

***Class:*** [_TPJMD5_](./TPJMD5.md)

***Introduced:*** v1.0

```pascal
property ReadBufferSize: Cardinal;
```

## Description

[_TPJMD5_](./TPJMD5.md) buffers data read from streams and files. The size of the buffer is customisable. Read this property to find the buffer size in bytes. Set the property to change the buffer size.

The default buffer size is specified by the [_DefReadBufferSize_](./TPJMD5-DefReadBufferSize.md) class constant.

## Example

The following code reads data from a file in 1Kb chunks:

```pascal
var
  MD5: TPJMD5;
begin
  MD5 := TPJMD5.Create;
  try
    MD5.ReadBufferSize := 1024;
    MD5.ProcessFile('MyFile1.txt');
    ShowMessage(MD5.Digest); // Digest implicitly cast to string
  finally
    MD5.Free;
  end;
end;
```
