# Finalized property

***Project:*** [MD5 Message Digest Unit](../API.md)

***Unit:*** _PJMD5_

***Class:*** [_TPJMD5_](./TPJMD5.md)

***Introduced:*** v1.0

```pascal
property Finalized: Boolean;
```

## Description

This read only property indicates if the MD5 hash has been finalized. Once finalized no more data can be added to the hash and attempts to do so cause an [_EPJMD5_](./EPJMD5.md) exception to be raised.

Call [_Reset_](./TPJMD5-Reset.md) to clear the _Finalized_ property.

Reading the [_Digest_](./TPJMD5-Digest.md) property or calling [_Finalize_](./TPJMD5-Finalize.md) finalizes the hash and sets this property to `True`.
