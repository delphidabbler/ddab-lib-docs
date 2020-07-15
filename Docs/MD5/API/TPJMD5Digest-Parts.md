# Parts property

***Project:*** [MD5 Message Digest Unit](../API.md)

***Unit:*** _PJMD5_

***Class:*** [_TPJMD5_](./TPJMD5.md)

***Introduced:*** v1.0

```pascal
property Parts[Idx: Integer]: LongWord; default;
```

## Description

_Parts_ is the default array property of [_TPJMD5Digest_](./TPJMD5Digest.md), indexed from 0 to 3.

It provides yet another means of accessing the digest data as long words and is functionally equivalent to the _LongWords_ field.

The primary purpose of the property is not to be used as-is but to enable [_TPJMD5Digest_](./TPJMD5Digest.md) variables to be accessed using an array subscript.

***Note:*** If _D_ is a [_TPJMD5Digest_](./TPJMD5Digest.md) variable, the following are all equivalent ways of getting the 2nd long word from a digest:

* `D[1]`
* `D.Parts[1]`
* `D.LongWords[1]`
* `D.B`
