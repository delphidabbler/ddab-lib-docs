# Create constructor

***Project:*** [I/O Utility Classes](../API.md)

***Unit:*** [_PJFileHandle_](./PJFileHandle.md)

***Class:*** [_TPJFileHandle_](./TPJFileHandle.md)

```pascal
constructor Create(const FileName: string; const Mode: LongWord;
  const Inheritable: Boolean = True); overload;

constructor Create(const FileName: string; const Mode: LongWord;
  const Security: PSecurityAttributes); overload;
```

## Description

These two overloaded constructors open or create files and record the file handle in the [_Handle_](./TPJFileHandle-Handle.md) property.

Parameters are:

* _FileName_ - Name of file to be opened or created.

* _Mode_ - File open mode. This is made up of an access mode constant ORd with a share mode constant. Valid access modes are `fmOpenRead`, `fmOpenWrite`, `fmOpenReadWrite` and `fmCreate`. The share mode must be one of `fmShareCompat`, `fmShareExclusive`, `fmShareDenyWrite`, `fmShareDenyRead` or `fmShareDenyNone`.

* _Inheritable_ - Indicates whether the file handle is to be inheritable.

* _Security_ - Points to a _TSecurityAttributes_ record that specifies the required security for the file. If the file handle is to be inheritable set the _bInheritHandle_ field to `True`.

The constructors raise _EFCreateError_ or _EFOpenError_ exceptions if a file cannot be created or opened respectively.
