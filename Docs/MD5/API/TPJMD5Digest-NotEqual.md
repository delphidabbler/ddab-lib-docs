# NotEqual operator overloads

***Project:*** [MD5 Message Digest Unit](../API.md)

***Unit:*** _PJMD5_

***Class:*** [_TPJMD5_](./TPJMD5.md)

***Introduced:*** v1.0

```pascal
class operator NotEqual(const D1, D2: TPJMD5Digest): Boolean;
class operator NotEqual(const D: TPJMD5Digest; const B: TBytes): Boolean;
class operator NotEqual(const B: TBytes; const D: TPJMD5Digest): Boolean;
class operator NotEqual(const D: TPJMD5Digest; const S: string): Boolean;
class operator NotEqual(const S: string; const D: TPJMD5Digest): Boolean;
```

## Description

[_TPJMD5Digest_](./TPJMD5Digest.md) defines five overloads of the `<>` operator that permit [_TPJMD5Digest_](./TPJMD5Digest.md) variables to be tested for inequality with:

* [Other TPJMD5Digest records](#inequality-with-other-tpjmd5digest-records)
* [Unicode strings](#inequality-with-unicode-strings)
* [TBytes byte arrays](#inequality-with-tbytes-byte-arrays)

### Inequality with other TPJMD5Digest records

Two [_TPJMD5Digest_](./TPJMD5Digest.md) records are considered unequal if their _LongWords_ array fields differ in any element.

#### TPJMD5Digest example

```pascal
var
  D1, D2: TPJMD5Digest;
begin
  D1 := TPJMD5.Calculate('foo');
  D2 := TPJMD5.Calculate('bar');
  Assert(D1 <> D2);
  Assert(D2 <> D1);
end;
```

### Inequality with Unicode strings

A [_TPJMD5Digest_](./TPJMD5Digest.md) record is considered unequal to a Unicode string if:

1. The string is not 32 characters long -- ***or***
2. The string contains any characters that are not valid hexadecimal characters (both upper and lower case letters `A` to `F` are permitted) -- ***or***
3. The sequence of bytes represented by the string is different to the bytes of the [_TPJMD5Digest_](./TPJMD5Digest.md) record's _Bytes_ field.

#### Unicode example

```pascal
const
  S1 = '000102030405060708090A0B0C0D0E0F';
  S2 = '*foobarfoobarfoobarfoobarfoobar*'
  S3 = '000102030405060708';
  D: TPJMD5Digest = (
    Bytes: (
      $D1, $74, $AB, $98, $D2, $77, $D9, $F5,
      $A5, $61, $1C, $2C, $9F, $41, $9D, $9F
    )
  );
begin
  Assert(S1 <> D);
  Assert(D <> S1);
  Assert(S2 <> D);
  Assert(D <> S2);
  Assert(S3 <> D);
  Assert(D <> S3);
end;
```

### Inequality with TBytes byte arrays

A [_TPJMD5Digest_](./TPJMD5Digest.md) record is considered unequal to a _TBytes_ array if:

1. The byte array does not have 16 elements -- ***or***
2. The bytes of the byte array differ from those of the [_TPJMD5Digest_](./TPJMD5Digest.md) record's _Bytes_ field.

#### TBytes example

```pascal
const
  D: TPJMD5Digest = (
    Bytes: (
      $D1, $74, $AB, $98, $D2, $77, $D9, $F5,
      $A5, $61, $1C, $2C, $9F, $41, $9D, $9F
    )
  );
var
  A1, A2, A3: TBytes;
begin
  A1 := TBytes.Create(  // 16 elements
    $00, $01, $02, $03, $04, $05, $06, $07,
    $08, $09, $0A, $0B, $0C, $0D, $0E, $0F
  );
  A2 := TBytes.Create(  // 2 elements
    $D1, $74
  );
  A3 := TBytes.Create(  // 18 elements
    $D1, $74, $AB, $98, $D2, $77, $D9, $F5,
    $A5, $61, $1C, $2C, $9F, $41, $9D, $9F,
    $00, $FF
  );
  Assert(A1 <> D);
  Assert(D <> A1);
  Assert(A2 <> D);
  Assert(D <> A2);
  Assert(A3 <> D);
  Assert(D <> A3);
end;
```

#### TBytes note

Although a byte array with more than 16 elements can be assigned to a [_TPJMD5Digest_](./TPJMD5Digest.md), the two items ***do not*** compare equal:

```pascal
var
  D: TPJMD5Digest;
  A: TBytes;
begin
  A := TBytes.Create(  // 18 elements
    $D1, $74, $AB, $98, $D2, $77, $D9, $F5,
    $A5, $61, $1C, $2C, $9F, $41, $9D, $9F,
    $00, $FF
  );
  D := A;
  Assert(D <> A);
end;
```

This is because the "overflow" bytes from the byte array are discarded when assigning to the [_TPJMD5Digest_](./TPJMD5Digest.md) record.

## See Also

* [_Equal_](TPJMD5Digest-Equal.md) operator overloads
