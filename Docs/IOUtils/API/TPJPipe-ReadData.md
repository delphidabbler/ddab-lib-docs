# ReadData method

***Project:*** [I/O Utility Classes](../API.md)

***Unit:*** [_PJPipe_](./PJPipe.md)

***Class:*** [_TPJPipe_](./TPJPipe.md)

```pascal
function ReadData(out Buf; const BufSize: LongWord; out BytesRead: LongWord):
  Boolean;
```

## Description

This method reads data from the pipe into a buffer. Parameters are:

* _Buf_: Buffer that receives the data from the pipe. _Buf_ must have capacity of at least _BufSize_ bytes.

* _BufSize_: Size of the buffer or the number of bytes requested, which must be less than or equal to the size of the buffer.

* _BytesRead_: Set by the method to the number of bytes actually read.

`True` is returned if some data was read, `False` if nothing was read.

An _EInOutError_ exception is raised if there is an error peeking or reading the pipe.
