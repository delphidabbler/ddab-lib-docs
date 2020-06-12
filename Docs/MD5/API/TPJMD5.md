# TPJMD5 class

***Project:*** [MD5 Message Digest Unit](../API.md)

***Unit:*** _PJMD5_

***Introduced:*** v1.0

## Description

This class implements the MD5 message digest algorithm. It produces a message digest (i.e. a 16 byte hash) from a sequence of octets (bytes).

_TPJMD5_ has been designed to make it easy to create MD5 hashes of different types of data. It does this by providing overloaded [_Process_](./TPJMD5-Process.md) and [_Calculate_](./TPJMD5-Calculate.md) methods that can each accept several different data types.

The MD5 hash is exposed as a record of type [_TPJMD5Digest_](./TPJMD5Digest.md) that contains the hash in binary form. The record overloads various operators to make it easy to obtain a string representation of the hash and to access the hash itself either byte by byte or as a sequence of long words.

### Methods

| Method | Description |
|--------|-------------|
| [_Create_](./TPJMD5-Create.md) | Object constructor. |
| [_Calculate_](./TPJMD5-Calculate.md) | There are numerous overloaded versions of [_Calculate_](./TPJMD5-Calculate.md) for several different data types. These are class methods that create an MD5 hash directly from data passed to them. Each method returns the resulting hash as a [_TPJMD5Digest_](./TPJMD5Digest.md) record. |
| [_CalculateFile_](./TPJMD5-CalculateFile.md) | This class method is similar to the [_Calculate_](./TPJMD5-Calculate.md) methods except that it calculates and returns the MD5 hash of the contents of a file. |
| [_Process_](./TPJMD5-Process.md) | Each of the numerous overloaded [_Process_](./TPJMD5-Process.md) methods adds the data passed to it to the current MD5 hash. The method enable data to be added to the hash in chunks rather than all at once as is the case with v. The methods also enable data of different types to be combined in the same hash. |
| [_ProcessFile_](./TPJMD5-ProcessFile.md) | This method is similar to the [_Process_](./TPJMD5-Process.md) method except that it adds the contents of a file to the current MD5 hash. |
| [_Reset_](./TPJMD5-Reset.md)  | Resets the object and discards the current digest ready to calculate a new hash. |
| [_Finalize_](./TPJMD5-Finalize.md) | Finalizes the current MD5 hash. Any attempt to add more data to the hash after calling this method raises an exception. |

### Properties

| Property | Description |
|----------|-------------|
| [_Digest_](./TPJMD5-Digest.md) | Read only property that finalizes and provides access to the MD5 hash as a [_TPJMD5Digest_](./TPJMD5Digest.md) record. |
| [_ReadBufferSize_](./TPJMD5-ReadBufferSize.md) | Gets and sets the size of buffer used when reading data from files and streams. |
| [_Finalized_](./TPJMD5-Finalized.md) | Read only property that indicates if the MD5 hash has been finalized. |

### Events

_TPJMD5_ exposes no events.

### Class Constants

| Constant | Description |
|----------|-------------|
| [_DefReadBufferSize_](TPJMD5-DefReadBufferSize.md) | Default buffer size used when reading streams and files. |
