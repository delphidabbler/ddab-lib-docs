# Finalize method

***Project:*** [MD5 Message Digest Unit](../API.md)

***Unit:*** _PJMD5_

***Class:*** [_TPJMD5_](./TPJMD5.md)

***Introduced:*** v1.0

```pascal
procedure Finalize;
```

## Description

Finalizes the current MD5 hash and sets the [_Finalized_](./TPJMD5-Finalized.md) property to `True`.

Any attempt to add more data to the hash after calling this method raises an [_EPJMD5_](./EPJMD5.md) exception.

_Finalize_ is called internally when the [_Digest_](./TPJMD5-Digest.md) property is read. This means that there is rarely any need to call _Finalize_ explicitly.

Calling this method more than once has no effect - the digest is finalized only once. This ensures that calling _Finalize_ before reading [_Digest_](./TPJMD5-Digest.md), or reading [_Digest_](./TPJMD5-Digest.md) more than once, is safe.

## Example

```pascal
var
  MD5: TPJMD5;
begin
  MD5 := TPJMD5.Create;
  try
    MD5.Process('Foo', TEncoding.ASCII);
    ShowMessage(BoolToStr(MD5.Finalized, True)); // will display "False"
    MD5.Finalize;
    // Further calls to MD5.Process will raise exception now
    ShowMessage(BoolToStr(MD5.Finalized, True)); // will display "True"
    ShowMessage(MD5.Digest);  // Digest implicitly cast to string
  finally
    MD5.Free;
  end;
end;
```
