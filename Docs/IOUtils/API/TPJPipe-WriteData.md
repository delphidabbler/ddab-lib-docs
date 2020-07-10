# WriteData method

***Project:*** [I/O Utility Classes](../API.md)

***Unit:*** [_PJPipe_](./PJPipe.md)

***Class:*** [_TPJPipe_](./TPJPipe.md)

```pascal
function WriteData(const Buf; const BufSize: LongWord): LongWord;
```

## Description

This method writes data from a buffer to the pipe. Parameters are:

* _Buf_: Buffer containing the data to be written. _Buf_ must have capacity of at least _BufSize_ bytes.

* _BufSize_: Number of bytes to write from the buffer to the pipe.

The number of bytes actually written is returned by the method.

An _EInOutError_ exception is raised if the pipe's write handle has been closed or if the pipe can't be written to.
