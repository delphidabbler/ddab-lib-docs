# Handle property

***Project:*** [I/O Utility Classes](../API.md)

***Unit:*** [_PJFileHandle_](./PJFileHandle.md)

***Class:*** [_TPJFileHandle_](./TPJFileHandle.md)

```pascal
property Handle: THandle;
```

## Description

Handle used to access the file.

This handle is set when one of the [constructors](./TPJFileHandle-Create.md) opens or creates a file successfully. The handle will have value _INVALID_HANDLE_VALUE_ if there was an error opening the file.

Handles, and hence the related files, are closed when the [_TPJFileHandle_](./TPJFileHandle.md) instance is freed.
