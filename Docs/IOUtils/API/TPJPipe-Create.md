# Create constructors

***Project:*** [I/O Utility Classes](../API.md)

***Unit:*** [_PJPipe_](./PJPipe.md)

***Class:*** [_TPJPipe_](./TPJPipe.md)

```pascal
constructor Create(const Size: LongWord; const Inheritable: Boolean = True);
  overload;

constructor Create(const Inheritable: Boolean = True);
  overload;

constructor Create(const Size: LongWord; const Security: TSecurityAttributes);
  overload;

constructor Create(const Security: TSecurityAttributes);
  overload;
```

## Description

There are four overloaded constructors, each of which creates a pipe with certain characteristics depending on the parameters.

* When a _Size_ parameter is present the pipe is created with the specified size in bytes. If _Size_ is `0` or is not provided then the Windows default pipe size is used.

* If the _Inheritable_ parameter is present it specifies whether [_ReadHandle_](./TPJPipe-ReadHandle.md) and [_WriteHandle_](./TPJPipe-WriteHandle.md) are to be inheritable. Calling _Create_ with a single _Size_ parameter, or with no parameters, is the same as specifying _Inherited_ as `True`.

* _Security_ parameters, where provided, specify the required security for the pipe. If [_ReadHandle_](./TPJPipe-ReadHandle.md) and [_WriteHandle_](./TPJPipe-WriteHandle.md) are to be inheritable the _TSecurityAttributes.bInheritHandle_ field must be set to `True`.

All versions of the constructor raise _EInOutError_ exceptions if the pipe can't be created. The exception message includes the reason for failure that was returned from the operating system.
