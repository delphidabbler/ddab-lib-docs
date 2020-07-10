# WriteBytes method

***Project:*** [I/O Utility Classes](../API.md)

***Unit:*** [_PJPipe_](./PJPipe.md)

***Class:*** [_TPJPipe_](./TPJPipe.md)

```pascal
procedure WriteBytes(const Bytes: TBytes);
```

## Description

This method writes the whole content of a byte array to the pipe. The parameter is:

* _Bytes_: Array of bytes to write to the pipe.

An _EInOutError_ exception is raised if the pipe's write handle has been closed or the pipe can't be written to.

## Remarks

On versions of Delphi where _TBytes_ is not defined in _SysUtils_, the [_PJPipe_](./PJPipe.md) unit defines it as:

```pascal
type TBytes = array of Byte;
```
