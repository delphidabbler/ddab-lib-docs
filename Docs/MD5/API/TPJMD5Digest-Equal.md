# Equal operator overloads

***Project:*** [MD5 Message Digest Unit](../API.md)

***Unit:*** _PJMD5_

***Class:*** [_TPJMD5_](./TPJMD5.md)

***Introduced:*** v1.0

```pascal
class operator Equal(const D1, D2: TPJMD5Digest): Boolean;
class operator Equal(const D: TPJMD5Digest; const B: TBytes): Boolean;
class operator Equal(const B: TBytes; const D: TPJMD5Digest): Boolean;
class operator Equal(const D: TPJMD5Digest; const S: string): Boolean;
class operator Equal(const S: string; const D: TPJMD5Digest): Boolean;
```

## Description

[_TPJMD5Digest_](./TPJMD5Digest.md) defines five overloads of the `=` operator that permit [_TPJMD5Digest_](./TPJMD5Digest.md) variables to be tested for equality with:

* [Other TPJMD5Digest records](#equality-with-other-tpjmd5digest-records)
* [Unicode strings](#equality-with-unicode-strings)
* [TBytes byte arrays](#equality-with-tbytes-byte-arrays)

### Equality with other TPJMD5Digest records

Two [_TPJMD5Digest_](./TPJMD5Digest.md) records are considered equal if all elements of their _LongWords_ array fields are the same.

#### Example

```pascal
var
  D1, D2: TPJMD5Digest;
begin
  D1 := TPJMD5.Calculate('Foo');
  D2 := TPJMD5.Calculate('Foo');
  Assert(D1 = D2);
  Assert(D2 = D1);
end;
```

### Equality with Unicode strings

A [_TPJMD5Digest_](./TPJMD5Digest.md) record is considered equal to a Unicode string if:

1. The string is 32 characters long -- ***and***
2. The string contains only valid hexadecimal characters (both upper and lower case letters `A` to `F` are permitted) -- ***and***
3. The sequence of bytes represented by the string is the same as the bytes of the [_TPJMD5Digest_](./TPJMD5Digest.md) record's _Bytes_ field.

#### Unicode example

```pascal
const
  S = 'd174ab98d277d9f5a5611c2c9f419d9f';
  D: TPJMD5Digest = (
    Bytes: (
      $D1, $74, $AB, $98, $D2, $77, $D9, $F5,
      $A5, $61, $1C, $2C, $9F, $41, $9D, $9F
    )
  );
begin
  Assert(S = D);
  Assert(D = S);
end;
```

### Equality with TBytes byte arrays

A [_TPJMD5Digest_](./TPJMD5Digest.md) record is considered equal to a _TBytes_ array if:

1. The byte array has 16 elements -- ***and***
2. The bytes of the byte array are the same as those of the [_TPJMD5Digest_](./TPJMD5Digest.md) record's _Bytes_ field.

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
  A: TBytes;
begin
  A := TBytes.Create(
    $D1, $74, $AB, $98, $D2, $77, $D9, $F5,
    $A5, $61, $1C, $2C, $9F, $41, $9D, $9F
  );
  Assert(A = D);
  Assert(D = A);
end;
```

#### Note

Although a byte array with more than 16 elements can be assigned to a [_TPJMD5Digest_](./TPJMD5Digest.md), the two items ***do not*** compare equal:

```pascal
var
  D: TPJMD5Digest;
  A: TBytes;
begin
  A := TBytes.Create(
    $D1, $74, $AB, $98, $D2, $77, $D9, $F5,
    $A5, $61, $1C, $2C, $9F, $41, $9D, $9F,
    $00, $FF  // 18 elements
  );
  D := A;
  Assert(not(D = A));
end;
```

This is because the "overflow" bytes from the byte array are discarded when assigning to the [_TPJMD5Digest_](./TPJMD5Digest.md) record.

## See Also

* [_NotEqual_](./TPJMD5Digest-NotEqual.md) operator overloads
