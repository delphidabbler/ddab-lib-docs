# Read method

***Project:*** [Stream Extension Classes](../API.md)

***Unit:*** [_PJIStreams_](./PJIStreams.md)

***Classes:*** [_TPJIStreamWrapper_](./TPJIStreamWrapper.md), [_TPJHandleIStreamWrapper_](./TPJHandleIStreamWrapper.md), [_TPJFileIStream_](./TPJFileIStream.md)

```pascal
function Read(pv: Pointer; cb: Longint; pcbRead: PLongint): HResult;
  virtual; stdcall;
```

## Description

Reads a specified number of bytes from the wrapped stream into memory starting at the current seek pointer. The seek pointer is incremented by the number of bytes read.

***Parameters:***

* _pv_ -- Pointer to buffer to receive data read from wrapped stream.
* _cb_ -- Number of bytes to be read.
* _pcbRead_ -- Pointer to value that receives number of bytes actually read. May be nil in which case the parameter is ignored.

***Returns:***

* _S_OK_ on success.
* _S_FAIL_ on error reading stream.
* _STG_E_INVALIDPOINTER_ if _pv_ is nil.

## Remarks

If the requested number of bytes are available in the wrapped stream then _pv^_ receives _cb_ bytes and _pcbRead^_ is set equal to _cb_. If there is insufficient data remaining in the wrapped stream to fulfil the request then any remaining bytes are read from the stream into _pv^_ and _pcbRead^_ will be less than _cb_. If the stream is at the end when the request is made then no data is copied into _pv^_ and _pcbRead^_ is set to zero.

The buffer pointed to by _pv_ must have capacity of at least _cb_ bytes.
