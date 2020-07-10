# AvailableDataSize method

***Project:*** [I/O Utility Classes](../API.md)

***Unit:*** [_PJPipe_](./PJPipe.md)

***Class:*** [_TPJPipe_](./TPJPipe.md)

```pascal
function AvailableDataSize: LongWord;
```

## Description

This method peeks the pipe to get the size of data available for reading from it.

The number of bytes of available data is returned.

An _EInOutError_ exception is raised if there is an error peeking the pipe.
