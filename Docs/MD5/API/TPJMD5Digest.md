# TPJMD5Digest Record

***Project:*** [MD5 Message Digest Unit](../API.md)

***Unit:*** _PJMD5_

***Introduced:*** v1.0

## Description

_TPJMD5Digest_ is a record that encapsulates a MD5 digest produced by hashing an octet stream using the MD5 message digest algorithm. These digests are produced by the [_TPJMD5_](./TPJMD5.md) class.

The record enables the digest to be cast to and from strings and _TBytes_ byte arrays. It also permits digests to be tested for equality and inequality. In addition the digest data can be accessed either as an array of bytes or as long words.

### Fields

_TPJMD5Digest_ is a variant record which provides three different ways of accessing the digest data:

| Field | Description |
|-------|-------------|
| _Bytes_ | This array provides access to each of the 16 bytes of the digest. It is indexed from 0 to 15. |
| _LongWords_ | This array provides access the each of the 4 long words that make up the digest. It is indexed from 0 to 3. |
| _A_, _B_, _C_ and _D_ | Each of these fields provide an alternate means of accessing the digest data as long words. _A_, _B_, _C_ and _D_ are aliases for the elements of the _LongWords_ array at indexes 0, 1, 2 & 3 respectively. |

### Property

| Property | Description |
|----------|-------------|
| [_Parts_](./TPJMD5Digest-Parts.md) | Default array property that provides an alternate means of access the digest as long words. Enables _TPJMD5Digest_ variables to be directly indexed. |

### Operator Overloads

| Operator | Description |
|----------|-------------|
| [_Implicit_](./TPJMD5Digest-Implicit.md) | Enables _TPJMD5Digest_ records to be cast to and from Unicode strings and _TBytes_ byte arrays. |
| [_Equal_](./TPJMD5Digest-Equal.md) | Enables a _TPJMD5Digest_ record to be compared for equality with another _TPJMD5Digest_, Unicode strings and _TBytes_ byte arrays. |
| [_NotEqual_](./TPJMD5Digest-NotEqual.md) | Enables a _TPJMD5Digest_ record to be compared for inequality with another _TPJMD5Digest_, Unicode strings and _TBytes_ byte arrays. |
