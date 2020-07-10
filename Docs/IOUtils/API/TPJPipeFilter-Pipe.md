# Pipe property

***Project:*** [I/O Utility Classes](../API.md)

***Unit:*** [_PJPipeFilters_](./PJPipeFilters.md)

***Classes:*** [_TPJPipeFilter_](./TPJPipeFilter.md), [_TPJUnicodeBMPPipeFilter_](./TPJUnicodeBMPPipeFilter.md), [_TPJAnsiSBCSPipeFilter_](./TPJAnsiSBCSPipeFilter.md)

```pascal
property Pipe: TPJPipe;
```

## Description

This property provides read only access to the [_TPJPipe_](./TPJPipe.md) object that was passed to the [constructor](./TPJPipeFilter-Create.md).

Use this property if you need to access any of the pipe's properties or methods and have not maintained a separate reference to it.

## Remarks

This property was provided so that a reference could be obtained to pipe object that was created on the fly in the filter object's [constructor](./TPJPipeFilter-Create.md).
