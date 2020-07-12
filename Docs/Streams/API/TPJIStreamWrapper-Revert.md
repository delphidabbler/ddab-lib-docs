# Revert method

***Project:*** [Stream Extension Classes](../API.md)

***Unit:*** [_PJIStreams_](./PJIStreams.md)

***Classes:*** [_TPJIStreamWrapper_](./TPJIStreamWrapper.md), [_TPJHandleIStreamWrapper_](./TPJHandleIStreamWrapper.md), [_TPJFileIStream_](./TPJFileIStream.md)

```pascal
function Revert: HResult; virtual; stdcall;
```

## Description

Discards all changes that have been made to a transacted stream since the last call to [_Commit_](TPJIStreamWrapper-Commit.md). _Revert_ has no effect on streams opened in direct mode.

Since wrapped streams do not support transacted mode, this method does nothing in this implementation.

***Parameters:***

* This method has no parameters.

***Returns:***

* _STG_E_REVERTED_ on all occasions.
