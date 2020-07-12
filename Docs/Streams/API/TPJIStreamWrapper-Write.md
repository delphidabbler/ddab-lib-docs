# Write method

***Project:*** [Stream Extension Classes](../API.md)

***Unit:*** [_PJIStreams_](./PJIStreams.md)

***Classes:*** [_TPJIStreamWrapper_](./TPJIStreamWrapper.md), [_TPJHandleIStreamWrapper_](./TPJHandleIStreamWrapper.md), [_TPJFileIStream_](./TPJFileIStream.md)

```pascal
function Write(pv: Pointer; cb: Longint; pcbWritten: PLongint): HResult;
  virtual; stdcall;
```

## Description

Writes a specified number of bytes from memory to the wrapped stream starting at the current seek pointer. The seek pointer is incremented by the number of bytes written.

***Parameters:***

* _pv_ -- Pointer to a buffer containing data to be written to the wrapped stream.
* _cb_ -- Number of bytes to be written.
* _pcbWritten_ -- Pointer to value that receives number of bytes actually written. May be nil in which case the parameter is ignored.

***Returns:***

* _S_OK_ on success.
* _STG_E_CANTSAVE_ if the stream can't be written to.
* _STG_E_INVALIDPOINTER_ if _pv_ is nil.

## Remarks

If _pcbWritten^_ is less than _cb_ then not all the data could be written to the wrapped stream.

The buffer pointed to by _pv_ must contain at least _cb_ bytes of data.
