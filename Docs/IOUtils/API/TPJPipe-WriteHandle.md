# WriteHandle property

***Project:*** [I/O Utility Classes](../API.md)

***Unit:*** [_PJPipe_](./PJPipe.md)

***Class:*** [_TPJPipe_](./TPJPipe.md)

```pascal
property WriteHandle: THandle;
```

## Description

This read only property provides access to the Windows handle used to write data to the pipe.

This handle can be passed to file writing routines that take a handle as a parameter, such as those provided in Delphi's _SysUtils_ and _Windows_ units. Alternatively, if you want to write to the pipe via a _TStream_ object, create a _THandleStream_ instance for the handle.

## Remarks

Do not pass this handle to any Windows API function that may alter it (e.g. _CloseHandle_).

If you do need to close _WriteHandle_ then use the [_CloseWriteHandle_](./TPJPipe-CloseWriteHandle.md) method. [_CloseWriteHandle_](./TPJPipe-CloseWriteHandle.md) closes the handle and sets it to `0`.

_WriteHandle_ should not be used when it is `0`.
