# MD5 How-to: How To Get a Digest String

You often see MD5 hashes or digests displayed as strings like this: `c8b029b7698b23a5962e7cc21a75653a`

These strings are always 32 characters long and are made up hexadecimal characters representing the 16 bytes of a MD5 digest.

It's easy to get a MD5 hash string from a [_TPJMD5Digest_](../API/TPJMD5Digest.md) record. You just assign it to a string variable:

```pascal
var
  D: TPJMD5Digest;
  S: string;
begin
  D := TPJMD5.Calculate('Foo');
  S := D;
  ShowMessage(S);
end;
```

This code works because [_TPJMD5Digest_](../API/TPJMD5Digest.md) has an [_Implicit_ cast operator](../API/TPJMD5Digest-Implicit.md#tpjmd5digest-to-string) that automatically creates a string representation of the hash when it is assigned to a string.

This conversion also works when a digest record is used in a string context, such as when passed as a string parameter to a routine or method. For example:

```pascal
var
  D: TPJMD5Digest;
begin
  D := TPJMD5.Calculate('Foo');
  ShowMessage(D);
end;
```

This works because _ShowMessage_ takes a string parameter.

You can also explicitly cast a [_TPJMD5Digest_](../API/TPJMD5Digest.md) record to a string. This is useful when it is passed as a parameter to something like the `array of const` parameter of routines like _Format_ and _ShowMessageFmt_ where the type is not recognised. In this case you do:

```pascal
var
  D: TPJMD5Digest;
begin
  D := TPJMD5.Calculate('Foo');
  ShowMessageFmt('Digest = %s', [string(D)]);
end;
```

You can't pass _D_ directly here because, behind the scenes, the second parameter of _ShowMessageFmt_ is converted to an array of _TVarRec_ records, and no suitable implicit cast is defined in [_TPJMD5Digest_](../API/TPJMD5Digest.md). However, a cast to string works because the compiler knows how to convert strings to _TVarRec_.

Similarly, if you have a console application and want to write a [_TPJMD5Digest_](../API/TPJMD5Digest.md) record as a string to the console you need the string cast otherwise _WriteLn_ and its ilk don't understand the type:

```pascal
var
  D: TPJMD5Digest;
begin
  D := TPJMD5.Calculate('Foo');
  WriteLn('Digest = ', string(D));
end;
```

> You can also assign a string to a [_TPJMD5Digest_](../API/TPJMD5Digest.md) providing the string contains a valid hex representation of a MD5 digest. This uses another [_Implicit_ cast operator](../API/TPJMD5Digest-Implicit.md#string-to-tpjmd5digest)

## See Also

* How-tos:
  * [Get raw digest data](./GetDigestData.md)
  * [Compare two digests](./CompareDigests.md)
* Programmers' Guide:
  * [_TPJMD5Digest_](../API/TPJMD5Digest.md)

## Links

* [How-to Guide Contents](../HowTo.md)
