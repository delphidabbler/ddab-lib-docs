# ReadHandle property

***Project:*** [I/O Utility Classes](../API.md)

***Unit:*** [_PJPipe_](./PJPipe.md)

***Class:*** [_TPJPipe_](./TPJPipe.md)

```pascal
property ReadHandle: THandle;
```

## Description

This read only property provides access to the Windows handle used to read data from the pipe.

This handle can be passed to file reading routines that take a handle as a parameter, such as those provided in Delphi's _SysUtils_ and _Windows_ units. Alternatively, if you want to read from the pipe via a _TStream_ object, create a _THandleStream_ instance for the handle.

## Remarks

Do not pass this handle to any Windows API function that may alter it (e.g. _CloseHandle_).
