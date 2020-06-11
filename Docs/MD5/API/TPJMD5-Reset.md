# Reset method

***Project:*** [MD5 Message Digest Unit](../API.md)

***Unit:*** _PJMD5_

***Class:*** [_TPJMD5_](./TPJMD5.md)

***Introduced:*** v1.0

```pascal
procedure Reset;
```

## Description

Resets the [_TPJMD5_](./TPJMD5.md) object and discards the current digest ready to calculate a new hash. Calling this method sets the object to its newly created state.

The method sets the [_Finalized_](./TPJMD5-Finalized.md) property to `False`.

Once the [_Digest_](./TPJMD5-Digest.md) property has been read or the [_Finalize_](./TPJMD5-Finalize.md) method has been called _Reset_ must be called to create a new hash before calling [_Process_](./TPJMD5-Process.md) or [_ProcessFile_](./TPJMD5-ProcessFile.md).

## Example

Suppose you need two get two MD5 hashes using the same [_TPJMD5_](./TPJMD5.md) instance. The following code will do it:

```pascal
var
  MD5: TPJMD5;
begin
  MD5 := TPJMD5.Create;
  try
    MD5.Process('Foo', TEncoding.ASCII);
    ShowMessage(MD5.Digest);  // implicitly casts Digest to string
    MD5.Reset;
    MD5.Process('Bar', TEncoding.ASCII);
    ShowMessage(MD5.Digest);  // implicitly casts Digest to string
  finally
    MD5.Free;
  end;
end;
```
