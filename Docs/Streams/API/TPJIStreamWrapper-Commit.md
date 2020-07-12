# Commit method

***Project:*** [Stream Extension Classes](../API.md)

***Unit:*** [_PJIStreams_](./PJIStreams.md)

***Classes:*** [_TPJIStreamWrapper_](./TPJIStreamWrapper.md), [_TPJHandleIStreamWrapper_](./TPJHandleIStreamWrapper.md), [_TPJFileIStream_](./TPJFileIStream.md)

```pascal
function Commit(grfCommitFlags: Longint): HResult; virtual; stdcall;
```

## Description

***Does nothing.***

In theory, this method commits any changes made to a stream opened in transacted mode. In direct mode it should simply flush any memory buffers into the underlying storage object.

Since wrapped streams do not support transacted mode and _TPJIStreamWrapper_ maintains no data buffers, this method does nothing in this implementation.

***Parameters:***

* _grfCommitFlags_ -- Flags from the [_STGC_](http://msdn.microsoft.com/en-us/library/aa380320%28v=vs.85%29.aspx) specify how the changes are committed. ***All flags are ignored in this implementation.***

***Returns:***

* _S_OK_ on all occasions.
