# Implicit operator overloads

***Project:*** [MD5 Message Digest Unit](../API.md)

***Unit:*** _PJMD5_

***Class:*** [_TPJMD5_](./TPJMD5.md)

***Introduced:*** v1.0

```pascal
class operator Implicit(const D: TPJMD5Digest): string;
class operator Implicit(const S: string): TPJMD5Digest;
class operator Implicit(const D: TPJMD5Digest): TBytes;
class operator Implicit(const B: TBytes): TPJMD5Digest;
```

## Description

[_TPJMD5Digest_](./TPJMD5Digest.md) defines four implicit casts:

* [TPJMD5Digest to string](#tpjmd5digest-to-string)
* [string to TPJMD5Digest](#string-to-tpjmd5digest)
* [TPJMD5Digest to TBytes](#tpjmd5digest-to-tbytes)
* [TBytes to TPJMD5Digest](#tbytes-to-tpjmd5digest)

### TPJMD5Digest to string

```pascal
class operator Implicit(const D: TPJMD5Digest): string;
```

This cast creates a string representation of the digest. The string is the well known 32 character hexadecimal representation, for example `d41d8cd98f00b204e9800998ecf8427e` which is the MD5 digest of the empty (ansi) string.

This cast is particularly useful because it enables a [_TPJMD5Digest_](./TPJMD5Digest.md) to be rendered as text. Just reference a [_TPJMD5Digest_](./TPJMD5Digest.md) instance in a string context and the digest is automatically converted to a string.

#### TPJMD5Digest example

```pascal
var
  D: TPJMD5Digest;
begin
  D := TPJMD5.Calculate('foo');
  ShowMessage('MD5 of "foo" is: ' + D);
end;
```

### String to TPJMD5Digest

```pascal
class operator Implicit(const S: string): TPJMD5Digest;
```

This cast enable you to assign a string to a [_TPJMD5Digest_](./TPJMD5Digest.md) variable.

The string must hold a hexadecimal representation of a MD5 digest. It must be exactly 32 characters long and be comprised only of valid hexadecimal characters. Both upper and lower case `A`..`F` are permitted. If the string is invalid a [_EPJMD5_](./EPJMD5.md) exception is raised.

The digest's data is set to the bytes represented by the hex digits.

#### String to TPJMD5Digest example

```pascal
const
  S = 'd174ab98d277d9f5a5611c2c9f419d9f';
  D: TPJMD5Digest = (
    Bytes: (
      $D1, $74, $AB, $98, $D2, $77, $D9, $F5,
      $A5, $61, $1C, $2C, $9F, $41, $9D, $9F
    )
  );
var
  Digest: TPJMD5Digest;
begin
  Digest := S;
  Assert(Digest = D);
end;
```

### TPJMD5Digest to TBytes

```pascal
class operator Implicit(const D: TPJMD5Digest): TBytes;
```

This cast allows a digest's data to be assigned to a _TBytes_ array. The digest's data is copied into a new 16 element _TBytes_ array.

#### TPJMD5Digest to TBytes example

```pascal
const
  D: TPJMD5Digest = (
    Bytes: (
      $D1, $74, $AB, $98, $D2, $77, $D9, $F5,
      $A5, $61, $1C, $2C, $9F, $41, $9D, $9F
    )
  );
var
  A, Arr: TBytes;
begin
  A := TBytes.Create(
    $D1, $74, $AB, $98, $D2, $77, $D9, $F5,
    $A5, $61, $1C, $2C, $9F, $41, $9D, $9F
  );
  Arr := D;
  Assert(ArraysEqual(Arr, A));
end;
```

Note that _ArraysEqual_ is assumed to be some function that tests equality of two byte arrays.

### TBytes to TPJMD5Digest

```pascal
class operator Implicit(const B: TBytes): TPJMD5Digest;
```

This cast allows you to assign a byte array to a variable of type [_TPJMD5Digest_](./TPJMD5Digest.md).

The array of bytes must have at least 16 elements otherwise a [_EPJMD5_](./EPJMD5.md) exception is raised. Bytes are copied directly from the array elements into the digest's data without change. If the length of the byte array is greater than 16, only to first 16 elements are copied.

#### TBytes to TPJMD5Digest example

```pascal
const
  D: TPJMD5Digest = (
    Bytes: (
      $D1, $74, $AB, $98, $D2, $77, $D9, $F5,
      $A5, $61, $1C, $2C, $9F, $41, $9D, $9F
    )
  );
var
  Digest: TPJMD5Digest;
  A: TBytes;
begin
  A := TBytes.Create(
    $D1, $74, $AB, $98, $D2, $77, $D9, $F5,
    $A5, $61, $1C, $2C, $9F, $41, $9D, $9F
  );
  Digest := A;
  Assert(Digest = D);
end;
```

#### TBytes to TPJMD5Digest note

Although a byte array with more than 16 elements can be cast to [_TPJMD5Digest_](./TPJMD5Digest.md), such an array will always test as unequal to the digest.
