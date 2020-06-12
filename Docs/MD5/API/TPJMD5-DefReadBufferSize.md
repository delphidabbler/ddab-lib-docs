# DefReadBufferSize constant

***Project:*** [MD5 Message Digest Unit](../API.md)

***Unit:*** _PJMD5_

***Class:*** [_TPJMD5_](./TPJMD5.md)

***Introduced:*** v1.0

```pascal
const DefReadBufferSize = 64 * 1024;
```

## Description

This class constant determines the default buffer size used when reading data from streams and files. The constant has two uses:

1. It provides the default value of the [_ReadBufferSize_](./TPJMD5-ReadBufferSize.md) property.
2. It provides the buffer size used by the [_CalculateFile_](./TPJMD5-CalculateFile.md) class method and the _TStream_ variants of the [_Calculate_](./TPJMD5-Calculate.md) class method.

The default buffer size is 64Kb.
