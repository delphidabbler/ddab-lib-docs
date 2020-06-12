# Digest property

***Project:*** [MD5 Message Digest Unit](../API.md)

***Unit:*** _PJMD5_

***Class:*** [_TPJMD5_](./TPJMD5.md)

***Introduced:*** v1.0

```pascal
property Digest: TPJMD5Digest;
```

## Description

This read only property provides access to the current MD5 hash as a [_TPJMD5Digest_](./TPJMD5Digest.md) record.

Once you have finished adding data to a hash with the [_Process_](./TPJMD5-Process.md) and [_ProcessFile_](./TPJMD5-ProcessFile.md) methods you should read _Digest_ to get the required MD5 digest of the data.

Reading this property finalizes the hash so that no more data can be added to it. _Digest_ calls [_Finalize_](./TPJMD5-Finalize.md) internally and sets the [_Finalized_](./TPJMD5-Finalized.md) property to `True`.

## Note

The value of _Digest_ can be assigned to another [_TPJMD5Digest_](./TPJMD5Digest.md) record or to a Unicode string or _TBytes_ array. This is because [_TPJMD5Digest_](./TPJMD5Digest.md) overloads the [_Implicit_](./TPJMD5Digest-Implicit.md) operator for the string and _TBytes_ types.

## Example

Here's how to display the combined MD5 hash of two files:

```pascal
var
  MD5: TPJMD5;
begin
  MD5 := TPJMD5.Create;
  try
    MD5.ProcessFile('MyFile1.txt');
    MD5.ProcessFile('MyFile2.txt');
    ShowMessage(MD5.Digest);
  finally
    MD5.Free;
  end;
end;
```

The _ShowMessage_ call relies on the fact that _Digest_ can be implicitly cast to a string.
