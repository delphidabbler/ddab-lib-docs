# MD5 How-to: How To Get Raw Digest Data

An MD5 digest or hash is an 8 byte value. Most of the time all you need to do with a hash is display it or compare it to another hash. But occasionally you need to access the data itself.

[_TPJMD5Digest_](../API/TPJMD5Digest.md) provides two views of the digest data:

* [As long words](#long-word-access)
* [As bytes](#byte-access
)

## Long word access

This is the most common way to interpret MD5 digest data. For example if you are transmitting the MD5 hash via an HTTP header you encode the data based on the long words.

There are several ways of accessing the hash as long words. The most useful are:

1. By directly indexing a [_TPJMD5Digest_](../API/TPJMD5Digest.md) variable. (This is made possible by the [_TPJMD5Digest.Parts_](../API/TPJMD5Digest-Parts.md) default array property).
2. By accessing the elements of the _LongWords_ array.
3. By accessing named long word variables _A_, _B_, _C_ and _D_.

For a [_TPJMD5Digest_](../API/TPJMD5Digest.md) variable _D_, the following are equivalent:

```pascal
D.A = D[0] = D.LongWords[0]
D.B = D[1] = D.LongWords[1]
D.C = D[2] = D.LongWords[2]
D.D = D[3] = D.LongWords[3]
```

### Long word examples

Use direct indexing like this:

```pascal
var
  D: TPJMD5Digest;
  Idx: Integer;
begin
  D := TPJMD5.Calculate('Foo', TEncoding.ASCII);
  for Idx := 0 to 3 do
    ShowMessageFmt('D[%d] = %.8X', [Idx, D[Idx]]);
end;
```

Iterate the long words of the digest using the _LongWords_ array field like this:

```pascal
var
  D: TPJMD5Digest;
  LW: LongWord;
begin
  D := TPJMD5.Calculate('Foo', TEncoding.ASCII);
  for LW in D.LongWords do
    ShowMessage(IntToHex(LW, 8));
end;
```

Access the long words by name like this:

```pascal
var
  D: TPJMD5Digest;
begin
  D := TPJMD5.Calculate('Foo', TEncoding.ASCII);
  ShowMessageFmt('A=%.8X  B=%.8X  C=%.8X  D=%.8X', [D.A, D.B, D.C, D.D]);
end;
```

## Byte access

It is sometimes convenient to access the digest data as individual bytes. You may want access a byte at a time or you may want a copy of the whole digest. [_TPJMD5Digest_](../API/TPJMD5Digest.md) provides both

Byte by byte access is provided via the _Bytes_ array field. This can be indexed from `0` to `15` or it can be iterated.

Digest data can be copied to a _TBytes_ array by means of an implicit cast: you just assign a [_TPJMD5Digest_](../API/TPJMD5Digest.md) variable to a _TBytes_ variable which receives a copy of the 16 bytes of the digest's data.

### Byte examples

Iterate the _Bytes_ array field like this:

```pascal
var
  D: TPJMD5Digest;
  B: Byte;
  SL: TStrings;
begin
  D := TPJMD5.Calculate('Foo', TEncoding.ASCII);
  SL := TStringList.Create;
  try
    for B in D.Bytes do
      SL.Add(IntToStr(B));
    ShowMessage('D.Bytes = (' + SL.DelimitedText + ')');
  finally
    SL.Free;
  end;
end;
```

Access the _Bytes_ field by index like this:

```pascal
var
  D: TPJMD5Digest;
  Idx: Integer;
  S: string;
begin
  D := TPJMD5.Calculate('Foo', TEncoding.ASCII);
  S := '';
  for Idx := Low(D.Bytes) to High(D.Bytes) do
    S := S + Format('D.Bytes[%d] = %d'#10, [Idx, D.Bytes[Idx]]);
  ShowMessage(S);
end;
```

Copy the data to a _TBytes_ array like this:

```pascal
var
  D: TPJMD5Digest;
  S: string;
  BA: TBytes;
  B: Byte;
begin
  D := TPJMD5.Calculate('Foo', TEncoding.ASCII);
  BA := D; // assignment uses implicit cast of TPJMD5Digest to TBytes
  S := '';
  for B in BA do
    S := S + '  ' + IntToStr(B) + #10;
  ShowMessage('TBytes array contains:'#10 + S);
end;
```

## See Also

* How-tos:
  * [Get a digest string](./GetDigestAsString.md)
  * [Compare two digests](./CompareDigests.md)
* Programmers' Guide:
  * [_TPJMD5Digest_](../API/TPJMD5Digest.md)

## Links

* [How-To Guide Contents](../HowTo.md)
