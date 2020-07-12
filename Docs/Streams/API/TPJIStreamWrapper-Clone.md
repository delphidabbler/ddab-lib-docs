# Clone method

***Project:*** [Stream Extension Classes](../API.md)

***Unit:*** [_PJIStreams_](./PJIStreams.md)

***Classes:*** [_TPJIStreamWrapper_](./TPJIStreamWrapper.md), [_TPJHandleIStreamWrapper_](./TPJHandleIStreamWrapper.md), [_TPJFileIStream_](./TPJFileIStream.md)

```pascal
function Clone(out stm: IStream): HResult; virtual; stdcall;
```

## Description

***Method not supported.***

In theory, this method creates a new stream object that references the same bytes as the original stream but provides a separate seek pointer to those bytes.

But, because _TStream_ does not support multiple position pointers, implementation of this method is non-trivial. In this implementation _Clone_ is simply a do-nothing stub.

***Parameters:***

* _IStream_ -- This parameter is not set in this implementation and its value is undefined.

***Returns:***

* _E_NOTIMPL_.
