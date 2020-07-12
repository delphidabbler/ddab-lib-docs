# CopyTo method

***Project:*** [Stream Extension Classes](../API.md)

***Unit:*** [_PJIStreams_](./PJIStreams.md)

***Classes:*** [_TPJIStreamWrapper_](./TPJIStreamWrapper.md), [_TPJHandleIStreamWrapper_](./TPJHandleIStreamWrapper.md), [_TPJFileIStream_](./TPJFileIStream.md)

```pascal
function CopyTo(stm: IStream; cb: Largeint; out cbRead: Largeint;
  out cbWritten: Largeint): HResult; virtual; stdcall;
```

## Description

Copies a specified number of bytes from the current seek pointer in the wrapped stream to the current seek pointer in another stream. If the wrapped stream has less than the requested number of bytes available then all remaining bytes in the wrapped stream are copied.

***Parameters:***

* _stm_ -- Stream to receive copied data, referenced by its _IStream_ interface.
* _cb_ -- Number of bytes to be copied.
* _cbRead_ -- Set to number of bytes actually read from wrapped stream.
* _cbWritten_ -- Set to number of bytes actually written to destination stream.

***Returns:***

* *S_OK_* on success.
* *E_UNEXPECTED* if there is an exception during copying.
* *STG_E_INVALIDPOINTER* if _stm_ is nil.
* *STG_E_CANTSAVE* if the data can't be written to the destination stream.
* **[v3.0]** *E_FAIL* if the number of bytes requested in _cb_ is greater than _MaxInt_ or is negative. _See Remarks_.
* **[≥v3.1]** *STG_E_MEDIUMFULL* if less than the requested amount of data can be written to the destination stream.

## Remarks

* **[v3.0]** Although you can request more than 2Gb of data to be copied, the implementation of _CopyFrom_ does not support this and will fail with an *E_FAIL* return value. This happens regardless of the size of the wrapped stream.

* **[≥v3.1]** Requests of more than 2Gb of data to be copied are supported.
