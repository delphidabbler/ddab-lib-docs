# ReadBytes method

***Project:*** [I/O Utility Classes](../API.md)

***Unit:*** [_PJPipe_](./PJPipe.md)

***Class:*** [_TPJPipe_](./TPJPipe.md)

```pascal
function ReadBytes(const Count: LongWord = 0): TBytes;
```

## Description

This method reads data from the pipe into a byte array. The parameter is:

* _Count_: Number of bytes to read from the pipe. If _Count_ is `0` or greater than the number of available bytes then all the data from the pipe is read.

The required byte array is returned.

An _EInOutError_ exception is raised if there is an error peeking or reading the pipe.

## Remarks

On versions of Delphi where _TBytes_ is not defined in _SysUtils_, the [_PJPipe_](PJPipe.md) unit defines it as:

```pascal
type TBytes = array of Byte;
```
