# UnlockRegion method

***Project:*** [Stream Extension Classes](../API.md)

***Unit:*** [_PJIStreams_](./PJIStreams.md)

***Classes:*** [_TPJIStreamWrapper_](./TPJIStreamWrapper.md), [_TPJHandleIStreamWrapper_](./TPJHandleIStreamWrapper.md), [_TPJFileIStream_](./TPJFileIStream.md)

```pascal
function UnlockRegion(libOffset: Largeint; cb: Largeint;
  dwLockType: Longint): HResult; virtual; stdcall;
```

## Description

***Does nothing.***

This method may remove the access restriction on a range of bytes previously restricted with [_LockRegion_](TPJIStreamWrapper-LockRegion.md). It is optional whether support is provided for region locking -- this implementation does not do so. A do-nothing stub method is provided that returns the value required by the [Microsoft documentation](http://msdn.microsoft.com/en-us/library/aa380046%28v=VS.85%29.aspx).

***Parameters:***

* _libOffset_ -- Byte offset of the beginning of the restricted range to be unlocked. _Ignored._
* _cb_ -- Length of the restricted range in bytes. _Ignored._
* _dwLockType_ -- Access restrictions previously placed on the range. Valid values are from the [_LOCKTYPE_](http://msdn.microsoft.com/en-us/library/aa380048%28v=vs.85%29.aspx). _Ignored._

***Returns:***

* _STG_E_INVALIDFUNCTION_ in all cases.
