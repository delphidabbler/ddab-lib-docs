# CopyToStream method

***Project:*** [I/O Utility Classes](../API.md)

***Unit:*** [_PJPipe_](./PJPipe.md)

***Class:*** [_TPJPipe_](./TPJPipe.md)

```pascal
procedure CopyToStream(const Stm: TStream; Count: LongWord = 0);
```

## Description

This method copies data from the pipe to a stream. Parameters are:

* _Stm_: Stream that receives the data.

* _Count_: Number of bytes to copy. If `0` then all the remaining data in the pipe is copied to the stream.

An _EInOutError_ exception is raised if there is an error peeking or reading the pipe. _EWriteError_ is raised if the stream write fails.
