# CloseWriteHandle method

***Project:*** [I/O Utility Classes](../API.md)

***Unit:*** [_PJPipe_](./PJPipe.md)

***Class:*** [_TPJPipe_](./TPJPipe.md)

```pascal
procedure CloseWriteHandle;
```

## Description

_CloseWriteHandle_ closes the pipe's write handle if it is open.

After calling this method no further data may be written to the pipe and [_WriteHandle_](./TPJPipe-WriteHandle.md) will be zero.
