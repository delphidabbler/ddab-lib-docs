# Stat method

***Project:*** [Stream Extension Classes](../API.md)

***Unit:*** [_PJIStreams_](./PJIStreams.md)

***Class:*** [_TPJIStreamWrapper_](./TPJIStreamWrapper.md)

```pascal
function Stat(out statstg: TStatStg; grfStatFlag: Longint): HResult;
  virtual; stdcall;
```

## Description

_Stat_ retrieves a [_STATSTG_](http://msdn.microsoft.com/en-us/library/aa380319%28v=VS.85%29.aspx) structure that provides information about the wrapped stream.

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

Only the following fields of _TStatStg_ are supported:

* _dwType_: Set to _STGTY_STREAM_.
* _cbSize_: Set to the size of the underlying stream.
* _pwcsName_: Set to the name of the stream. This is made up of wrapper class name followed by name of wrapped class in parentheses. This field is only set if the _grfStatFlag_ parameter is set to _STATFLAG_NORMAL_. When set, the value must be freed using the task allocator.

Other fields are set to zero.
