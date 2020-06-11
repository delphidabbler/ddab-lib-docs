# CalculateFile method

***Project:*** [MD5 Message Digest Unit](../API.md)

***Unit:*** _PJMD5_

***Class:*** [_TPJMD5_](./TPJMD5.md)

***Introduced:*** v1.0

```pascal
class function CalculateFile(const FileName: TFileName): TPJMD5Digest;
```

## Description

This class method is very like the [_Calculate_](./TPJMD5-Calculate.md) methods in that it provides a useful shortcut when you want to get the MD5 hash of a single file. Just call this method and pass the path to the required file in the _FileName_ parameter and read the function result to get the required digest.

Like [_Calculate_](./TPJMD5-Calculate.md), there is no need to create an instance of [_TPJMD5_](./TPJMD5.md) to use this method.

The disadvantage of this method over the similar [_ProcessFile_](TPJMD5-ProcessFile.md) method is that there is no way to change the default size of the buffer used to read the file. The buffer size is that given by the [_TPJMD5.DefReadBufferSize_](./TPJMD5-DefReadBufferSize.md) constant.

## Example

Here's how to check if the MD5 hashes of two files are the same:

```pascal
function SameMD5(const FileName1, FileName2: TFileName): Boolean;
var
  D1, D2: TPJMD5Digest;
begin
  D1 := TPJMD5.CalculateFile(FileName1);
  D2 := TPJMD5.CalculateFile(FileName2);
  Result := D1 = D2;
end;
```
