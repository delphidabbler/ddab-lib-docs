# TPJPipe class

***Project:*** [I/O Utility Classes](../API.md)

***Unit:*** [_PJPipe_](./PJPipe.md)

## Description

This class provides a wrapper round a Windows un-named pipe.

Pipes can be created with the desired security attributes. Pipes can also have inheritable handles to make them suitable for passing to child processes [†](#note).

_TPJPipe_ provides methods to check the number of bytes in a readable pipe, read bytes from a pipe into either a buffer or a stream and write bytes to a pipe from buffers and streams.

### Note 

† Inheritable handles have a particular use in the [Console Application Runner Classes](../../ConsoleApp/API.md) for piping the output or input of console applications to and from the host application.

### Methods

| Method | Description |
|--------|-------------|
| [_AvailableDataSize_](./TPJPipe-AvailableDataSize.md) | Peeks the pipe to get the size of data available for reading. |
| [_CloseWriteHandle_](./TPJPipe-CloseWriteHandle.md) | Closes the pipe's write handle if it is open. |
| [_CopyFromStream_](./TPJPipe-CopyFromStream.md) | Copies data from a stream into the pipe. |
| [_CopyToStream_](./TPJPipe-CopyToStream.md) | Copies data from the pipe to a stream. |
| [_Create_](./TPJPipe-Create.md) | Various overloaded constructors. |
| [_ReadBytes_](./TPJPipe-ReadBytes.md) | Reads data from the pipe into a byte array. |
| [_ReadData_](./TPJPipe-ReadData.md) | Reads data from the pipe into a buffer. |
| [_WriteBytes_](./TPJPipe-WriteBytes.md) | Writes the content of a byte array to the pipe. |
| [_WriteData_](./TPJPipe-WriteData.md) | Writes data from a buffer to the pipe. |

### Properties

| Property | Description |
|----------|-------------|
| [_ReadHandle_](./TPJPipe-ReadHandle.md) | Windows handle used to read data from the pipe. |
| [_WriteHandle_](./TPJPipe-WriteHandle.md) | Windows handle used to write data to the pipe. |

### Events

_TPJPipe_ exposes no events.

## Links

* [Classes List](./Classes.md)
