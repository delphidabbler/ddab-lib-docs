# Stat method

***Project:*** [Stream Extension Classes](../API.md)

***Unit:*** [_PJIStreams_](./PJIStreams.md)

***Class:*** [_TPJFileIStream_](./TPJFileIStream.md)

```pascal
function Stat(out statstg: TStatStg; grfStatFlag: Longint): HResult;
  virtual; stdcall;
```

## Description

_Stat_ retrieves a [_STATSTG_](http://msdn.microsoft.com/en-us/library/aa380319%28v=VS.85%29.aspx) structure that provides information about the file associated with the stream.

This version of _Stat_ modifies the method inherited from [_TPJHandleIStreamWrapper_](./TPJHandleIStreamWrapper.md) to provide the file name instead of a name based on class names in the _pwcsName_ field of the _TStatStg_ record.

***Parameters:***

* _statstg_ -- Receives the required _TStatStg_ ([_STATSTG_](http://msdn.microsoft.com/en-us/library/aa380319%28v=VS.85%29.aspx)) record.
* _grfStatFlag_ -- Specifies which members of the _TStatStg_ record are not to contain information. Possible values are:
  * _STATFLAG_DEFAULT_: Omits the stream name from the record.
  * _STATFLAG_NORMAL_: Includes the stream name in the record. In this case the name should be freed by the caller using the task allocator.

***Returns:***

* _S_OK_ on success.
* _E_UNEXPECTED_ if an exception occurs
* _STG_E_INVALIDFLAG_ if _grfStatFlag_ is not valid
* _STG_E_INVALIDPOINTER_ if _statstg_ is not a valid pointer.

## Remarks

The following fields of _TStatStg_ are supported:

* _dwType_: Set to _STGTY_STREAM_.
* _cbSize_: Set to the size of the underlying stream.
* _pwcsName_: Set to the name of the file associated with the stream. This field is only set if the _grfStatFlag_ parameter is set to _STATFLAG_NORMAL_. When set, the value must be freed using the task allocator.
* _mtime_: Set to the last modification time of any file whose handle is associated with the wrapped _THandleStream_.
* _ctime_: Set to the creation time of any file whose handle is associated with the wrapped _THandleStream_.
* _atime_: Set to the last access time of any file whose handle is associated with the wrapped _THandleStream_.

Other fields are set to zero.
