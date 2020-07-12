# SetSize method

***Project:*** [Stream Extension Classes](../API.md)

***Unit:*** [_PJIStreams_](./PJIStreams.md)

***Classes:*** [_TPJIStreamWrapper_](./TPJIStreamWrapper.md), [_TPJHandleIStreamWrapper_](./TPJHandleIStreamWrapper.md), [_TPJFileIStream_](./TPJFileIStream.md)

```pascal
function SetSize(libNewSize: Largeint): HResult; virtual; stdcall;
```

## Description

Changes the size of the wrapped stream.

***Parameters:***

* _libNewSize_ -- New stream size.

***Returns:***

* _S_OK_ on success.
* _E_FAIL_ if we can't set the size or the requested size is too large.
* _E_UNEXPECTED_ if there is an exception.
* **[v3.0]** _STG_E_INVALIDFUNCTION_ if the value of _libNewSize_ is greater than _MaxInt_ or is less than zero. _See Remarks_.

## Remarks

If the requested size of the wrapped stream is too large the stream size may be set to a smaller value than requested and _E_FAIL_ will be returned.

**[v3.0]** Although _libNewSize_ accepts 64 bit values the implementation of _SetSize_ prior to v3.1 is limited to positive 32 bit integer values. Passing a value greater than _MaxInt_ or less than zero in the _libNewSize_ parameter causes the method to return _STG_E_INVALIDFUNCTION_.
