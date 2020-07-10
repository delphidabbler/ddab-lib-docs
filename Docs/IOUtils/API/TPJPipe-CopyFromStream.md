# CopyFromStream method

***Project:*** [I/O Utility Classes](../API.md)

***Unit:*** [_PJPipe_](./PJPipe.md)

***Class:*** [_TPJPipe_](./TPJPipe.md)

```pascal
procedure CopyFromStream(const Stm: TStream; Count: LongWord = 0);
```

## Description

This method copies data from a stream into the pipe. Parameters are:

* _Stm_: Stream from which to copy data.

* _Count_: Number of bytes to copy. If `0` then all the remaining data from the stream is copied to the pipe.

An _EInOutError_ exception is raised if the pipe's write handle has been closed or if the pipe can't be written to. _EReadError_ is raised if the stream read fails.
