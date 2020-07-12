# LockRegion method

***Project:*** [Stream Extension Classes](../API.md)

***Unit:*** [_PJIStreams_](./PJIStreams.md)

***Classes:*** [_TPJIStreamWrapper_](./TPJIStreamWrapper.md), [_TPJHandleIStreamWrapper_](./TPJHandleIStreamWrapper.md), [_TPJFileIStream_](./TPJFileIStream.md)

```pascal
function LockRegion(libOffset: Largeint; cb: Largeint;
  dwLockType: Longint): HResult; virtual; stdcall;
```

## Description

***Method not supported.***

This method may restrict access to a specified range of bytes in the stream. It is optional whether support is provided for this method -- this implementation does not do so. A stub is provided in accordance with the [Microsoft documentation](http://msdn.microsoft.com/en-us/library/aa380039%28v=vs.85%29.aspx).

***Parameters:***

* _libOffset_ -- Byte offset of the beginning of the range to be restricted. _Ignored._
* _cb_ -- Length of the range to be restricted in bytes. _Ignored._
* _dwLockType_ -- Restrictions being requested on accessing the range. Valid values are from the [_LOCKTYPE_](http://msdn.microsoft.com/en-us/library/aa380048%28v=vs.85%29.aspx). _Ignored._

***Returns:***

* _STG_E_INVALIDFUNCTION_ in all cases.
