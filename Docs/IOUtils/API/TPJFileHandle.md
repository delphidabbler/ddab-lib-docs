# TPJFileHandle class

***Project:*** [I/O Utility Classes](../API.md)

***Unit:*** [_PJFileHandle_](./PJFileHandle.md)

## Description

This helper class can create or open files in various access and sharing modes with specified security and provide access to the file handle.

The class was designed with the sole purpose of making it easier to obtain inheritable file handles for use elsewhere. As a result the class provides no methods of its own for _accessing_ the file.

If there is a need to read or write the file you can either create a _THandleStream_ using the handle or you can use pass the handle to suitable handle file access routines from Delphi's _SysUtils_ and _Windows_ units.

### Methods

| Method | Description |
|--------|-------------|
| [_Create_](./TPJFileHandle-Create.md) | Overloaded constructors. Each opens or creates a file and records its handle. |

### Properties

| Property | Description |
|----------|-------------|
| [_Handle_](./TPJFileHandle-Handle.md) | Handle used to access file. |

### Events

_TPJFileHandle_ exposes no events.

## Links

* [Classes List](./Classes.md)
